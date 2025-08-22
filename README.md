<!DOCTYPE html>
<html lang="uk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Інтерактивне Осіннє Меню 2018</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <!-- Chosen Palette: Calm Harmony -->
    <!-- Application Structure Plan: A tab-based single-page application is chosen for optimal user experience. The content is divided into three logical sections: "План Харчування" (Meal Plan), "Правила та Поради" (Rules & Tips), and "Відстеження Прогресу" (Progress Tracker). This structure prevents overwhelming the user with a long scrollable page. The meal plan itself is further broken down by weeks, selectable via buttons, allowing users to quickly access the information they need. This non-linear, task-oriented design is more intuitive and engaging than the original document's linear format. -->
    <!-- Visualization & Content Choices: 
        - Report Info: 28-day meal plan -> Goal: Organize/Inform -> Viz/Method: Interactive weekly tabs with daily meal cards (HTML/CSS/JS) -> Interaction: Click buttons to display a specific week's plan -> Justification: Prevents scrolling, allows focused viewing.
        - Report Info: Rules, recommendations, activity guidelines -> Goal: Inform -> Viz/Method: Structured text with headings, lists, and icons (HTML/CSS) -> Interaction: None needed -> Justification: Enhances readability and scannability of important rules.
        - Report Info: Progress tracking (measurements) -> Goal: Engage/Inform -> Viz/Method: Explanatory text + a Chart.js bar chart with sample data -> Interaction: Visual representation of data -> Justification: Makes the concept of tracking more tangible and visually appealing.
    -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <style>
        body {
            font-family: 'Inter', sans-serif;
        }
        .tab-active {
            border-color: #0d9488;
            color: #0d9488;
            font-weight: 600;
        }
        .week-btn-active {
            background-color: #0d9488;
            color: white;
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
            height: 300px;
            max-height: 400px;
        }
        @media (min-width: 768px) {
            .chart-container {
                height: 400px;
            }
        }
    </style>
</head>
<body class="bg-amber-50 text-gray-800">

    <div class="container mx-auto p-4 md:p-8 max-w-5xl">
        
        <header class="text-center mb-8">
            <h1 class="text-3xl md:text-4xl font-bold text-teal-800">Осіннє меню 2018</h1>
            <p class="text-lg text-gray-600 mt-2">Казанцева Олена | <a href="#" class="text-teal-600 hover:underline">www.okay.fit</a></p>
        </header>

        <nav class="flex justify-center border-b-2 border-amber-200 mb-8 space-x-4 md:space-x-8">
            <button data-tab="plan" class="tab-btn py-3 px-2 md:px-4 text-sm md:text-base border-b-4 tab-active">📋 План Харчування</button>
            <button data-tab="rules" class="tab-btn py-3 px-2 md:px-4 text-sm md:text-base border-b-4 border-transparent">💡 Правила та Поради</button>
            <button data-tab="tracker" class="tab-btn py-3 px-2 md:px-4 text-sm md:text-base border-b-4 border-transparent">📊 Відстеження Прогресу</button>
        </nav>

        <main>
            <section id="plan" class="tab-content">
                <div class="bg-white p-6 rounded-xl shadow-md">
                    <h2 class="text-2xl font-bold text-teal-700 mb-4">Щотижневий План Харчування</h2>
                    <p class="text-gray-600 mb-6">Оберіть тиждень, щоб переглянути детальне меню на кожен день. План розроблено для збалансованого харчування протягом місяця.</p>
                    <div id="week-buttons" class="flex flex-wrap justify-center gap-2 mb-6">
                        <button data-week="1" class="week-btn px-4 py-2 rounded-full bg-amber-100 text-amber-800 hover:bg-teal-600 hover:text-white transition week-btn-active">Тиждень 1 (Дні 1-8)</button>
                        <button data-week="2" class="week-btn px-4 py-2 rounded-full bg-amber-100 text-amber-800 hover:bg-teal-600 hover:text-white transition">Тиждень 2 (Дні 9-16)</button>
                        <button data-week="3" class="week-btn px-4 py-2 rounded-full bg-amber-100 text-amber-800 hover:bg-teal-600 hover:text-white transition">Тиждень 3 (Дні 17-24)</button>
                        <button data-week="4" class="week-btn px-4 py-2 rounded-full bg-amber-100 text-amber-800 hover:bg-teal-600 hover:text-white transition">Тиждень 4 (Дні 25-28)</button>
                    </div>

                    <div id="menu-content" class="space-y-6">
                        <!-- Week 1 Content -->
                        <div class="week-content" data-week-content="1">
                            <div class="grid md:grid-cols-2 gap-6">
                                <!-- Days 1-4 -->
                                <div class="border border-amber-200 p-4 rounded-lg">
                                    <h3 class="font-bold text-lg mb-2 text-teal-700">Дні 1-4</h3>
                                    <ul class="space-y-2 text-sm">
                                        <li><strong>7:30:</strong> Склянка теплої негазованої води (250-500 мл).</li>
                                        <li><strong>Сніданок:</strong> Вівсянка довгої варки (50г), кефір сушений (20г), вершкове масло (10г), вершки (50г).</li>
                                        <li><strong>Обід:</strong> Макарони твердих сортів (60г), креветки (100г), овочі (100-150г).</li>
                                        <li><strong>Полуденок:</strong> Яблуко зелене (400г).</li>
                                        <li><strong>Вечеря:</strong> Квасоля з овочами (80г), баклажани (150г), моцарелла (50г), зелень, йогурт (10г) з оливковою олією.</li>
                                    </ul>
                                </div>
                                <!-- Days 5-8 -->
                                <div class="border border-amber-200 p-4 rounded-lg">
                                    <h3 class="font-bold text-lg mb-2 text-teal-700">Дні 5-8</h3>
                                    <ul class="space-y-2 text-sm">
                                        <li><strong>7:30:</strong> Склянка теплої негазованої води (250-500 мл).</li>
                                        <li><strong>Сніданок:</strong> Пшоно (50г), вершкове масло (10г), ізюм (5г), творог 5% (50г), курага/ізюм (40г).</li>
                                        <li><strong>Обід:</strong> Салат мікс, кіноа (60г), гарбузове насіння (20г), шпинат/салат (60г).</li>
                                        <li><strong>Полуденок:</strong> Салат з кус-кусом (50г), зеленню, фруктами та овочами (250-300г).</li>
                                        <li><strong>Вечеря:</strong> Рис (280-300г), тост з авокадо (хліб 100г, авокадо 50г).</li>
                                    </ul>
                                </div>
                            </div>
                        </div>
                        <!-- Week 2 Content -->
                        <div class="week-content hidden" data-week-content="2">
                           <div class="grid md:grid-cols-2 gap-6">
                                <!-- Days 9-12 -->
                                <div class="border border-amber-200 p-4 rounded-lg">
                                    <h3 class="font-bold text-lg mb-2 text-teal-700">Дні 9-12</h3>
                                    <ul class="space-y-2 text-sm">
                                        <li><strong>7:30:</strong> Склянка теплої негазованої води (250-500 мл).</li>
                                        <li><strong>Сніданок:</strong> Омлет з 2-х яєць, броколі (150г), зелень, хліб гречаний (100г).</li>
                                        <li><strong>Обід:</strong> Булгур (60г), пармезан (20г), овочева суміш (100г).</li>
                                        <li><strong>Полуденок:</strong> Булгур (200г), тост з авокадо (100г хліб, 50г авокадо).</li>
                                        <li><strong>Вечеря:</strong> Макарони (50г), салат з відвареною грудкою, моцарелою (250-300г).</li>
                                    </ul>
                                </div>
                                <!-- Days 13-16 -->
                                <div class="border border-amber-200 p-4 rounded-lg">
                                    <h3 class="font-bold text-lg mb-2 text-teal-700">Дні 13-16</h3>
                                    <ul class="space-y-2 text-sm">
                                        <li><strong>7:30:</strong> Склянка теплої негазованої води (250-500 мл).</li>
                                        <li><strong>Сніданок:</strong> Вівсянка (50г), вершки (50г), ягоди/банан (150г), мигдаль (20г).</li>
                                        <li><strong>Обід:</strong> Гречка (100г), сир фета (40г), кольорова капуста (100г).</li>
                                        <li><strong>Полуденок:</strong> Кефір/йогурт (200г), 2 фініка, кавун (300г).</li>
                                        <li><strong>Вечеря:</strong> Рис нешліфований (80г), відварене м'ясо/гриби/кукурудза (200г), оливкова олія.</li>
                                    </ul>
                                </div>
                            </div>
                        </div>
                        <!-- Week 3 Content -->
                        <div class="week-content hidden" data-week-content="3">
                            <div class="grid md:grid-cols-2 gap-6">
                                <!-- Days 17-20 -->
                                <div class="border border-amber-200 p-4 rounded-lg">
                                    <h3 class="font-bold text-lg mb-2 text-teal-700">Дні 17-20</h3>
                                    <ul class="space-y-2 text-sm">
                                        <li><strong>7:30:</strong> Склянка теплої негазованої води (250-500 мл).</li>
                                        <li><strong>Сніданок:</strong> Гречка (50г), варене яйце (1шт), броколі на пару (150-200г).</li>
                                        <li><strong>Обід:</strong> Картопля запечена (250г), кабачки запечені (100г), моцарелла (50г).</li>
                                        <li><strong>Полуденок:</strong> Смузі (яблуко 200г, банан 200г, зелень 20-30г).</li>
                                        <li><strong>Вечеря:</strong> Кус-кус (50г).</li>
                                    </ul>
                                </div>
                                <!-- Days 21-24 -->
                                <div class="border border-amber-200 p-4 rounded-lg">
                                    <h3 class="font-bold text-lg mb-2 text-teal-700">Дні 21-24</h3>
                                    <ul class="space-y-2 text-sm">
                                        <li><strong>7:30:</strong> Склянка теплої негазованої води (250-500 мл).</li>
                                        <li><strong>Сніданок:</strong> Кіноа (50г), мигдаль (30г), сухофрукти (40г), банан (100г).</li>
                                        <li><strong>Обід:</strong> Рис (50г) з креветками (200г), салат з овочів та авокадо (250г).</li>
                                        <li><strong>Полуденок:</strong> Смузі (банан 200г, малина 200г, насіння льону 15г).</li>
                                        <li><strong>Вечеря:</strong> Булгур (60г), індичка (50г), овочевий суп (100-150г).</li>
                                    </ul>
                                </div>
                            </div>
                        </div>
                        <!-- Week 4 Content -->
                        <div class="week-content hidden" data-week-content="4">
                            <div class="grid md:grid-cols-2 gap-6">
                                <!-- Days 25-28 -->
                                <div class="border border-amber-200 p-4 rounded-lg">
                                    <h3 class="font-bold text-lg mb-2 text-teal-700">Дні 25-28</h3>
                                    <ul class="space-y-2 text-sm">
                                        <li><strong>7:30:</strong> Склянка теплої негазованої води (250-500 мл).</li>
                                        <li><strong>Сніданок:</strong> Гречка (50г), пшоно (60г), сливи (50г), мак (20г), банан/яблуко (150г).</li>
                                        <li><strong>Обід:</strong> Кефір/мигдаль (100г).</li>
                                        <li><strong>Вечеря:</strong> Макарони (60г), салат з індичкою (200г) та пармезаном (20г).</li>
                                    </ul>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </section>
            
            <section id="rules" class="tab-content hidden">
                <div class="bg-white p-6 rounded-xl shadow-md space-y-6">
                    <div>
                        <h2 class="text-2xl font-bold text-teal-700 mb-4">Як використовувати меню?</h2>
                        <ul class="list-disc list-inside space-y-2 text-gray-700">
                            <li>Їсти потрібно тільки те, що є в меню. Воно збалансоване по БЖВ.</li>
                            <li>Готувати можна на тефлоновій сковороді без олії. Нічого не смажити!</li>
                            <li>Можна міняти місцями прийоми їжі (обід та вечерю).</li>
                            <li>Продукти вказані у сирому вигляді, зважуйте їх перед приготуванням.</li>
                            <li>Горіхи, бобові, крупи та сухофрукти бажано розмочувати перед вживанням.</li>
                            <li>Каву можна пити 1-2 рази на день з молоком (100 мл) і без цукру.</li>
                        </ul>
                    </div>
                    <div>
                        <h2 class="text-2xl font-bold text-teal-700 mb-4">Ключові поради</h2>
                        <div class="grid md:grid-cols-2 gap-6">
                            <div class="border-l-4 border-teal-500 pl-4">
                                <h3 class="font-semibold">🕒 Час прийому їжі</h3>
                                <p class="text-gray-600">Дотримуйтесь інтервалів між прийомами їжі. Вечеряйте не пізніше, ніж за 3 години до сну.</p>
                            </div>
                            <div class="border-l-4 border-teal-500 pl-4">
                                <h3 class="font-semibold">💧 Питний режим</h3>
                                <p class="text-gray-600">Пийте не менше 1л чистої води в день, влітку – до 2.5л. Вода очищує організм та виводить токсини.</p>
                            </div>
                            <div class="border-l-4 border-teal-500 pl-4">
                                <h3 class="font-semibold">🏃 Активність</h3>
                                <p class="text-gray-600">Обов'язкова норма – 10,000 кроків (або 7 км) на день. Це впливає на швидкість схуднення та загальний стан здоров'я.</p>
                            </div>
                        </div>
                    </div>
                </div>
            </section>

            <section id="tracker" class="tab-content hidden">
                <div class="bg-white p-6 rounded-xl shadow-md">
                    <h2 class="text-2xl font-bold text-teal-700 mb-4">Відстеження прогресу</h2>
                    <p class="text-gray-600 mb-6">Регулярні заміри допоможуть вам бачити результати та залишатися мотивованими. Ось як правильно це робити:</p>
                    <ul class="list-disc list-inside space-y-3 text-gray-700 mb-8">
                        <li>
                            <strong>Зважування:</strong> Зважуйтесь вранці натщесерце. Перший місяць – раз на тиждень, далі – раз на місяць.
                        </li>
                        <li>
                            <strong>Заміри тіла:</strong> Робіть заміри обхвату грудей, талії та стегон раз на місяць в одному й тому ж місці.
                        </li>
                        <li>
                            <strong>Фото:</strong> Зробіть фото "до" (спереду, в профіль, ззаду) для себе, щоб візуально оцінити зміни.
                        </li>
                    </ul>
                    <h3 class="text-xl font-bold text-teal-700 mb-4 text-center">Приклад візуалізації прогресу</h3>
                    <div class="chart-container">
                        <canvas id="progressChart"></canvas>
                    </div>
                </div>
            </section>
        </main>
        
        <footer class="text-center mt-12 text-gray-500 text-sm">
            <p>Вся інформація є інтелектуальною власністю. Будь ласка, використовуйте її лише в особистих цілях.</p>
            <p>Дякую за розуміння та повагу до праці. &copy; 2018</p>
        </footer>

    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const tabs = document.querySelectorAll('.tab-btn');
            const tabContents = document.querySelectorAll('.tab-content');
            const weekButtons = document.querySelectorAll('.week-btn');
            const weekContents = document.querySelectorAll('.week-content');

            tabs.forEach(tab => {
                tab.addEventListener('click', () => {
                    const target = tab.dataset.tab;
                    
                    tabs.forEach(t => t.classList.remove('tab-active'));
                    tab.classList.add('tab-active');
                    
                    tabContents.forEach(content => {
                        if (content.id === target) {
                            content.classList.remove('hidden');
                        } else {
                            content.classList.add('hidden');
                        }
                    });
                });
            });

            weekButtons.forEach(button => {
                button.addEventListener('click', () => {
                    const targetWeek = button.dataset.week;
                    
                    weekButtons.forEach(btn => btn.classList.remove('week-btn-active'));
                    button.classList.add('week-btn-active');
                    
                    weekContents.forEach(content => {
                        if (content.dataset.weekContent === targetWeek) {
                            content.classList.remove('hidden');
                        } else {
                            content.classList.add('hidden');
                        }
                    });
                });
            });

            const ctx = document.getElementById('progressChart').getContext('2d');
            new Chart(ctx, {
                type: 'bar',
                data: {
                    labels: ['Тиждень 1', 'Тиждень 2', 'Тиждень 3', 'Тиждень 4'],
                    datasets: [{
                        label: 'Вага, кг (приклад)',
                        data: [70, 69, 68.5, 67.5],
                        backgroundColor: 'rgba(13, 148, 136, 0.6)',
                        borderColor: 'rgba(13, 148, 136, 1)',
                        borderWidth: 1
                    }, {
                        label: 'Талія, см (приклад)',
                        data: [75, 73, 72, 70],
                        backgroundColor: 'rgba(251, 191, 36, 0.6)',
                        borderColor: 'rgba(251, 191, 36, 1)',
                        borderWidth: 1
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        y: {
                            beginAtZero: false
                        }
                    },
                    plugins: {
                        title: {
                            display: true,
                            text: 'Моніторинг ваги та об\'ємів'
                        },
                        tooltip: {
                            callbacks: {
                                label: function(context) {
                                    let label = context.dataset.label || '';
                                    if (label) {
                                        label += ': ';
                                    }
                                    if (context.parsed.y !== null) {
                                        label += context.parsed.y + (context.datasetIndex === 0 ? ' кг' : ' см');
                                    }
                                    return label;
                                }
                            }
                        }
                    }
                }
            });
        });
    </script>

</body>
</html>
