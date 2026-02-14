# valentines-website
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Valentine's Day Sweetheart</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Playfair+Display:ital,wght@0,400;1,400&display=swap');

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Playfair Display', serif;
            background-color: #ffe6eb; /* Soft Premium Pink Base */
            overflow-x: hidden;
            color: #880e4f; /* Deep Pink Text */
        }

        /* Container for Scrolling Layers */
        .container {
            height: 100vh;
            overflow-y: scroll;
            scroll-snap-type: y mandatory;
            scroll-behavior: smooth;
            position: relative;
            z-index: 2;
        }

        /* Individual Layers */
        .layer {
            height: 100vh;
            width: 100%;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            scroll-snap-align: start;
            padding: 20px;
            position: relative;
            transition: background 0.5s ease;
        }

        /* Layer Background Variations for Depth */
        .layer:nth-child(1) { background: linear-gradient(135deg, #fff0f6 0%, #ffc2d4 100%); }
        .layer:nth-child(2) { background: linear-gradient(135deg, #ffc2d4 0%, #f8bbd0 100%); }
        .layer:nth-child(3) { background: linear-gradient(135deg, #f8bbd0 0%, #f48fb1 100%); }
        .layer:nth-child(4) { background: linear-gradient(135deg, #f48fb1 0%, #ec407a 100%); color: white; }

        /* Typography */
        h1 {
            font-family: 'Dancing Script', cursive;
            font-size: 4rem;
            margin-bottom: 20px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.1);
        }

        p.quote {
            font-size: 1.5rem;
            font-style: italic;
            max-width: 600px;
            line-height: 1.6;
            margin-top: 20px;
            border-top: 2px solid rgba(255,255,255,0.5);
            border-bottom: 2px solid rgba(255,255,255,0.5);
            padding: 20px;
            background: rgba(255, 255, 255, 0.2);
            border-radius: 10px;
            backdrop-filter: blur(5px);
            animation: fadeIn 2s ease;
        }

        .scroll-indicator {
            position: absolute;
            bottom: 30px;
            font-size: 1rem;
            animation: bounce 2s infinite;
            opacity: 0.7;
        }

        /* Floating Hearts Animation Background */
        .hearts-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
            overflow: hidden;
        }

        .heart {
            position: absolute;
            bottom: -10vh;
            font-size: 2rem;
            opacity: 0;
            animation: floatUp 10s linear infinite;
        }

        @keyframes floatUp {
            0% { transform: translateY(0) rotate(0deg); opacity: 0; }
            10% { opacity: 0.8; }
            100% { transform: translateY(-110vh) rotate(360deg); opacity: 0; }
        }

        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
            40% { transform: translateY(-10px); }
            60% { transform: translateY(-5px); }
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

    </style>
</head>
<body>

    <div class="hearts-container" id="hearts-container"></div>

    <div class="container">
        
        <section class="layer">
            <h1>Happy Valentine's Day</h1>
            <div style="font-size: 3rem;">💖</div>
            <p class="quote">"My Sweetheart, you are the reason my life is so full of beautiful colors and love."</p>
            <div class="scroll-indicator">Scroll Down ↓</div>
        </section>

        <section class="layer">
            <h1>You & Me</h1>
            <div style="font-size: 3rem;">🌹</div>
            <p class="quote">"In all the world, there is no heart for me like yours. In all the world, there is no love for you like mine."</p>
        </section>

        <section class="layer">
            <h1>Forever</h1>
            <div style="font-size: 3rem;">✨</div>
            <p class="quote">"I love you not only for what you are, but for what I am when I am with you."</p>
        </section>

        <section class="layer">
            <h1>My Promise</h1>
            <div style="font-size: 3rem;">💍</div>
            <p class="quote">"I choose you. And I'll choose you over and over and over. Without pause, without a doubt, in a heartbeat. I'll keep choosing you."</p>
            <br>
            <h3>Love You Always ❤️</h3>
        </section>

    </div>

    <script>
        // Floating Hearts Logic
        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            
            // Random Emoji Selection
            const emojis = ['❤️', '💖', '💕', '💞', '💓', '💗'];
            heart.innerText = emojis[Math.floor(Math.random() * emojis.length)];
            
            // Random Positioning and Size
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = (Math.random() * 5 + 5) + 's'; // 5s to 10s
            heart.style.fontSize = (Math.random() * 20 + 20) + 'px';
            
            document.getElementById('hearts-container').appendChild(heart);
            
            // Remove heart after animation ends to save memory
            setTimeout(() => {
                heart.remove();
            }, 10000);
        }

        // Generate hearts every 300ms
        setInterval(createHeart, 300);
    </script>
</body>
</html>
