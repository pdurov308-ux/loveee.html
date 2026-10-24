<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>Женечка...</title>
<style>
    * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
    }

    body, html {
        background-color: #050505;
        color: #fff;
        height: 100%;
        width: 100%;
        overflow: hidden;
        font-family: 'Georgia', 'Times New Roman', serif;
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    /* Блок для сердечек */
    .canvas-container {
        width: 100%;
        height: 45vh; /* Верхняя часть экрана */
        position: relative;
        display: flex;
        justify-content: center;
        align-items: center;
        margin-top: 5vh;
    }

    canvas {
        display: block;
        width: 100%;
        height: 100%;
    }

    /* Блок для текста */
    .text-section {
        width: 100%;
        height: 50vh; /* Нижняя часть экрана */
        display: flex;
        flex-direction: column;
        justify-content: flex-start;
        align-items: center;
        padding: 10px 20px;
        opacity: 0;
        transition: opacity 1.5s ease;
        z-index: 10;
    }

    .text-section.show {
        opacity: 1;
    }

    .line {
        font-size: 16px;
        line-height: 1.4;
        margin-bottom: 8px;
        color: #cccccc;
        text-align: center;
        min-height: 22px;
        width: 100%;
        text-shadow: 0 0 10px rgba(255, 255, 255, 0.1);
    }

    .line.highlight {
        color: #ffffff;
        font-weight: bold;
        font-size: 18px;
        text-shadow: 0 0 15px rgba(255, 255, 255, 0.4);
    }

    .cursor {
        display: inline-block;
        width: 2px;
        height: 16px;
        background: #fff;
        vertical-align: middle;
        margin-left: 3px;
        animation: blink 1s infinite;
        box-shadow: 0 0 5px #fff;
    }

    @keyframes blink {
        0%, 100% { opacity: 1; }
        50% { opacity: 0; }
    }

    /* Адаптив для компа */
    @media (min-width: 901px) {
        .canvas-container { height: 50vh; margin-top: 0; }
        .text-section { height: 50vh; justify-content: center; }
        .line { font-size: 22px; min-height: 30px; margin-bottom: 12px; }
        .line.highlight { font-size: 24px; }
        .cursor { height: 22px; width: 3px; }
    }
</style>
</head>
<body>

    <div class="canvas-container">
        <canvas id="heartCanvas"></canvas>
    </div>

    <div class="text-section" id="textSection">
        <div class="line" id="l1"></div>
        <div class="line" id="l2"></div>
        <div class="line highlight" id="l3"></div>
        <div class="line" id="l4"></div>
        <div class="line" id="l5"></div>
        <div class="line highlight" id="l6"></div>
        <div class="line" id="l7"></div>
        <div class="line" id="l8"></div>
        <div class="line" id="l9"></div>
        <div class="line highlight" id="l10"></div>
        <div class="line" id="l11"></div>
    </div>

    <script>
        const canvas = document.getElementById('heartCanvas');
        const ctx = canvas.getContext('2d');
        const textSection = document.getElementById('textSection');
        let width, height;

        function resize() {
            const rect = canvas.parentElement.getBoundingClientRect();
            width = canvas.width = rect.width;
            height = canvas.height = rect.height;
        }
        window.addEventListener('resize', resize);
        resize();

        const colors = ['#ffffff', '#d4d4d4', '#a3a3a3', '#e8e8e8', '#8c8c8c'];
        const particleCount = 1000; // Много точек чтобы не было дырок
        let particles = [];
        let progress = 0; 
        let startTime = Date.now();
        
        // Жесткий масштаб чтобы все влезло
        let scaleFactor = Math.min(width, height) / 40;

        // Функция плотного заполнения сердечка (без дырки)
        function getSolidHeartPoint() {
            // Берем случайный угол и случайный радиус (от 0 до 1)
            let t = Math.random() * Math.PI * 2;
            let r = Math.sqrt(Math.random()); // sqrt делает распределение равномерным
            
            // Классическая формула сердца
            let x = 16 * Math.pow(Math.sin(t), 3);
            let y = -(13 * Math.cos(t) - 5 * Math.cos(2 * t) - 2 * Math.cos(3 * t) - Math.cos(4 * t));
            
            // Умножаем на радиус, чтобы заполнить внутренность, а не просто контур
            return {
                x: x * scaleFactor * r,
                y: y * scaleFactor * r
            };
        }

        class Particle {
            constructor() {
                let target = getSolidHeartPoint();
                this.targetX = target.x;
                this.targetY = target.y;

                // Начинают разлетаться с центра (или снизу)
                this.startX = (Math.random() - 0.5) * width;
                this.startY = height + 50;

                this.color = colors[Math.floor(Math.random() * colors.length)];
                this.size = Math.random() * 2 + 1;
                this.delay = Math.random() * 0.3; 
                this.pulseOffset = Math.random() * Math.PI * 2;
                
                this.currentX = this.startX;
                this.currentY = this.startY;
            }

            update(time) {
                if (progress < this.delay) return;

                let localProgress = (progress - this.delay) / (1 - this.delay);
                localProgress = Math.min(localProgress, 1);
                
                // Плавное замедление
                let ease = 1 - Math.pow(1 - localProgress, 4); 

                this.currentX = this.startX + (this.targetX - this.startX) * ease;
                this.currentY = this.startY + (this.targetY - this.startY) * ease;

                // Пульсация когда собрались
                if (localProgress === 1) {
                    let pulse = Math.sin(time * 0.003 + this.pulseOffset) * 2;
                    this.currentX += pulse * 0.5;
                    this.currentY += pulse;
                }
            }

            draw(ctx, offsetX, offsetY) {
                if (progress < this.delay) return;
                
                ctx.beginPath();
                ctx.arc(offsetX + this.currentX, offsetY + this.currentY, this.size, 0, Math.PI * 2);
                ctx.fillStyle = this.color;
                ctx.shadowBlur = 8;
                ctx.shadowColor = '#ffffff'; 
                ctx.fill();
                ctx.shadowBlur = 0;
            }
        }

        // Инициализация
        for (let i = 0; i < particleCount; i++) {
            particles.push(new Particle());
        }

        function animate() {
            ctx.clearRect(0, 0, width, height);
            
            let now = Date.now();
            let elapsed = (now - startTime) / 1000; 

            let offsetX = width / 2;
            let offsetY = height / 2;

            // Запускаем прогресс анимации с 0.5 сек
            if (elapsed > 0.5) {
                progress = Math.min((elapsed - 0.5) / 2.5, 1); 
            }

            // Рисуем точки
            particles.forEach(p => {
                p.update(now);
                p.draw(ctx, offsetX, offsetY);
            });

            // Когда сердце собралось
            if (progress >= 1 && !textSection.classList.contains('show')) {
                textSection.classList.add('show');
                startTyping();
            }

            requestAnimationFrame(animate);
        }

        // --- Текст ---
        const textLines = [
            { id: 'l1', text: 'Женечка...' },
            { id: 'l2', text: 'Я знаю, что сделал тебе больно.' },
            { id: 'l3', text: 'И мне правда очень жаль.' },
            { id: 'l4', text: 'Прости меня за то, что мало пишу.' },
            { id: 'l5', text: 'Это не потому, что ты безразлична.' },
            { id: 'l6', text: 'Наоборот. Ты очень важна.' },
            { id: 'l7', text: 'Я был глупым и не думал о тебе.' },
            { id: 'l8', text: 'Я хочу всё исправить.' },
            { id: 'l9', text: 'Не хочу тебя терять.' },
            { id: 'l10', text: 'Пожалуйста, дай мне шанс.' },
            { id: 'l11', text: 'Прости меня ❤' }
        ];

        function typeText(element, text, speed, callback) {
            let i = 0;
            element.innerHTML = '<span class="cursor"></span>';
            let cursor = element.querySelector('.cursor');

            function type() {
                if (i < text.length) {
                    cursor.insertAdjacentText('beforebegin', text.charAt(i));
                    i++;
                    setTimeout(type, speed);
                } else {
                    if (callback) callback();
                }
            }
            type();
        }

        function startTyping() {
            let lineIndex = 0;
            function typeNextLine() {
                if (lineIndex >= textLines.length) return;
                const lineData = textLines[lineIndex];
                const el = document.getElementById(lineData.id);
                const isLast = lineIndex === textLines.length - 1;
                
                typeText(el, lineData.text, 35, () => {
                    if (!isLast) {
                        const cur = el.querySelector('.cursor');
                        if (cur) cur.remove();
                    }
                    lineIndex++;
                    setTimeout(typeNextLine, 400); 
                });
            }
            typeNextLine();
        }

        // Запуск
        animate();
    </script>
</body>
</html>
