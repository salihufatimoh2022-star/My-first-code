<!DOCTYPE html>
<html>
<head>
    <title>Quiz Game</title>
    <style>
        body {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            font-family: Arial;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
        }
        .container {
            background: white;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.3);
            max-width: 500px;
        }
        h1 {
            color: #333;
            text-align: center;
        }
        .question {
            font-size: 18px;
            margin: 20px 0;
            font-weight: bold;
        }
        .option {
            background: #f0f0f0;
            padding: 10px;
            margin: 10px 0;
            border-radius: 5px;
            cursor: pointer;
            border: 2px solid #ddd;
        }
        .option:hover {
            background: #e0e0ff;
        }
        button {
            background: #667eea;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            width: 100%;
            margin-top: 20px;
            font-size: 16px;
        }
        button:hover {
            background: #764ba2;
        }
        .score {
            text-align: center;
            font-size: 18px;
            margin: 20px 0;
            color: #667eea;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>🧠 Quiz Game</h1>
        <div class="score">Score: <span id="score">0</span>/3</div>
        <div id="quiz"></div>
        <button onclick="nextQuestion()">Next Question</button>
    </div>

    <script>
        const questions = [
            {
                q: "What is the capital of France?",
                options: ["London", "Paris", "Berlin", "Madrid"],
                correct: 1
            },
            {
                q: "Which planet is Red?",
                options: ["Venus", "Mars", "Jupiter", "Saturn"],
                correct: 1
            },
            {
                q: "What is 2 + 2?",
                options: ["3", "4", "5", "6"],
                correct: 1
            }
        ];

        let current = 0;
        let score = 0;
        let answered = false;

        function showQuestion() {
            const q = questions[current];
            let html = `<div class="question">${q.q}</div>`;
            q.options.forEach((opt, i) => {
                html += `<div class="option" onclick="checkAnswer(${i})">${opt}</div>`;
            });
            document.getElementById('quiz').innerHTML = html;
        }

        function checkAnswer(i) {
            if (answered) return;
            answered = true;
            if (i === questions[current].correct) {
                score++;
                document.getElementById('score').textContent = score;
            }
        }

        function nextQuestion() {
            current++;
            answered = false;
            if (current < questions.length) {
                showQuestion();
            } else {
                document.getElementById('quiz').innerHTML = `<h2 style="text-align:center;">Quiz Complete! Your Score: ${score}/${questions.length}</h2>`;
            }
        }

        showQuestion();
    </script>
</body>
</html>