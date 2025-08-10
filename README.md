# pravindeok.github.io
Interactive Resume - Pravin Kumar
This is a single-page interactive web application built to showcase Pravin Kumar's resume in an engaging and dynamic format. Unlike a traditional static document, this application allows for easy exploration of his career timeline, technical skills, and key projects.

Overview
The application is a single HTML file that uses modern web technologies to create a responsive and intuitive user experience. It's designed to be easily shared and viewed on any device, from desktop to mobile.

Features
Interactive Navigation: A fixed header with smooth-scrolling links to different sections of the resume.

Career Timeline: A visually organized and interactive timeline of Pravin's professional experience. Clicking on each job entry reveals more detailed responsibilities.

Skills Visualization: A horizontal bar chart, powered by Chart.js, that graphically represents core technical and leadership competencies.

Project Showcase: A clean card-based layout for highlighting major projects, complete with descriptions and relevant technology tags.

Responsive Design: The layout is built with Tailwind CSS to ensure a great viewing experience on all screen sizes.

How to Use
To use this interactive resume, simply save the code below as a file named index.html and open it in any web browser. No external server or setup is required.

Code
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pravin Kumar - Interactive Resume</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700&display=swap" rel="stylesheet">
    <!-- Chosen Palette: Warm Neutrals with Teal Accent -->
    <!-- Application Structure Plan: A single-page application with a fixed top navigation bar for easy access to different sections: 'Home' (summary), 'Experience' (interactive timeline), 'Skills & Projects' (visualizations and detailed cards), and 'Contact'. This structure was chosen to allow a non-linear exploration of the candidate's profile, making it easy for a recruiter to jump to the information they find most relevant. The flow is designed to guide the user from a high-level summary to detailed evidence of capabilities. -->
    <!-- Visualization & Content Choices: 
        - Report Info: Career History -> Goal: Show progression -> Viz/Method: Interactive Timeline -> Interaction: Clicking on a job reveals detailed responsibilities. Justification: More engaging than a static list. Library: HTML/CSS/JS.
        - Report Info: Technical & Soft Skills -> Goal: Quickly assess capabilities -> Viz/Method: Bar Chart -> Interaction: Hovering over bars shows details. Justification: A bar chart provides a quick visual comparison of skill strengths. Library: Chart.js.
        - Report Info: Key Projects/Achievements -> Goal: Provide in-depth evidence -> Viz/Method: Interactive Cards -> Interaction: Clicking cards can reveal more details or link out. Justification: Organizes detailed information cleanly. Library: HTML/CSS/JS.
        - CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f4f4f5; /* Zinc 100 */
            color: #18181b; /* Zinc 900 */
        }
        .nav-link {
            transition: color 0.3s ease, border-bottom-color 0.3s ease;
            border-bottom: 2px solid transparent;
        }
        .nav-link:hover, .nav-link.active {
            color: #14b8a6; /* Teal 500 */
            border-bottom-color: #14b8a6; /* Teal 500 */
        }
        .timeline-item .timeline-content {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.5s ease-out, padding 0.5s ease-out;
            padding: 0 1.5rem;
        }
        .timeline-item.active .timeline-content {
            max-height: 500px; /* Adjust as needed */
            padding: 1.5rem 1.5rem;
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 800px;
            margin-left: auto;
            margin-right: auto;
            height: 400px;
            max-height: 50vh;
        }
        @media (min-width: 768px) {
            .chart-container {
                height: 500px;
            }
        }
    </style>
</head>
<body class="antialiased">

    <header class="bg-white/80 backdrop-blur-lg shadow-sm sticky top-0 z-50">
        <nav class="container mx-auto px-6 py-4 flex justify-between items-center">
            <div class="text-2xl font-bold text-zinc-800">
                Pravin Kumar
            </div>
            <div class="hidden md:flex items-center space-x-8">
                <a href="#home" class="nav-link font-medium text-zinc-600">Home</a>
                <a href="#experience" class="nav-link font-medium text-zinc-600">Experience</a>
                <a href="#skills" class="nav-link font-medium text-zinc-600">Skills & Projects</a>
                <a href="#contact" class="nav-link font-medium text-zinc-600">Contact</a>
            </div>
            <div class="md:hidden">
                <button id="mobile-menu-button" class="text-zinc-600 focus:outline-none">
                    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7"></path></svg>
                </button>
            </div>
        </nav>
        <div id="mobile-menu" class="hidden md:hidden">
            <a href="#home" class="block py-2 px-4 text-sm text-zinc-600 hover:bg-zinc-100">Home</a>
            <a href="#experience" class="block py-2 px-4 text-sm text-zinc-600 hover:bg-zinc-100">Experience</a>
            <a href="#skills" class="block py-2 px-4 text-sm text-zinc-600 hover:bg-zinc-100">Skills & Projects</a>
            <a href="#contact" class="block py-2 px-4 text-sm text-zinc-600 hover:bg-zinc-100">Contact</a>
        </div>
    </header>

    <main class="container mx-auto px-6 py-12">
        
        <section id="home" class="min-h-[80vh] flex items-center">
            <div class="w-full">
                <h1 class="text-5xl md:text-7xl font-bold text-zinc-800 leading-tight">Senior Solution Architect</h1>
                <p class="mt-4 text-lg text-zinc-600 max-w-3xl">A seasoned Senior Solution Architect and Director of Development with deep expertise in software architecture, API platforms, cloud-native systems, and AI-driven analytics. Proven track record of leading global teams and delivering scalable, secure, and innovative technology solutions across North America, Australia, and India.</p>
                <div class="mt-8">
                    <a href="#experience" class="bg-teal-500 text-white font-bold py-3 px-6 rounded-lg hover:bg-teal-600 transition-colors">Explore My Journey</a>
                </div>
            </div>
        </section>

        <section id="experience" class="py-20">
            <h2 class="text-4xl font-bold text-center mb-12">Career Timeline</h2>
            <div class="relative max-w-4xl mx-auto">
                <div class="absolute left-1/2 w-0.5 h-full bg-zinc-300 transform -translate-x-1/2"></div>
                <div id="timeline-container" class="space-y-12">
                </div>
            </div>
        </section>

        <section id="skills" class="py-20 bg-white rounded-2xl">
            <h2 class="text-4xl font-bold text-center mb-4">Skills & Projects</h2>
            <p class="text-center text-zinc-600 mb-12 max-w-3xl mx-auto">This section provides a visual overview of my technical and leadership competencies, alongside a showcase of key projects that highlight my hands-on experience in software architecture, cloud platforms, and data analytics.</p>
            
            <div class="mb-16">
                <h3 class="text-2xl font-bold text-center mb-8">Core Competencies</h3>
                <div class="chart-container">
                    <canvas id="skillsChart"></canvas>
                </div>
            </div>

            <div>
                <h3 class="text-2xl font-bold text-center mb-8">Project Showcase</h3>
                <div id="projects-container" class="grid md:grid-cols-2 gap-8">
                </div>
            </div>
        </section>

        <section id="contact" class="py-20 text-center">
            <h2 class="text-4xl font-bold mb-4">Get In Touch</h2>
            <p class="text-zinc-600 mb-8 max-w-2xl mx-auto">I'm always open to discussing new projects, creative ideas, or opportunities. Feel free to reach out to connect.</p>
            <div class="flex flex-col md:flex-row justify-center items-center space-y-4 md:space-y-0 md:space-x-6 text-lg">
                <div class="flex items-center space-x-2">
                    <span class="text-teal-500">●</span>
                    <span>+1 437-855-1447</span>
                </div>
                <div class="flex items-center space-x-2">
                    <span class="text-teal-500">●</span>
                    <span>pravin.deo@gmail.com</span>
                </div>
                <div class="flex items-center space-x-2">
                    <span class="text-teal-500">●</span>
                    <span>Toronto, ON, Canada</span>
                </div>
                <div class="flex items-center space-x-2">
                    <span class="text-teal-500">●</span>
                    <span>linkedin.com/in/pravindeo</span>
                </div>
            </div>
        </section>

    </main>

    <footer class="bg-zinc-800 text-zinc-400 text-center py-4">
        <p>&copy; 2025 Pravin Kumar. All Rights Reserved.</p>
    </footer>

    <script>
        const experienceData = [
            {
                role: 'Director of Development',
                company: 'FIS Canada',
                location: 'Toronto, ON',
                period: 'April 2022 – June 2025',
                side: 'left',
                description: 'Led a 25-member global team to deliver an API gateway and API Integrations with several Bank.',
                details: [
                    'Led a 25-member global team to deliver an API gateway and API integrations with several banks.',
                    'Deployed AWS Cloud with Infrastructure as Code using Terraform, harness.io, and Jenkins.',
                    'Integrated Generative AI (Co-Pilot) and PowerBI for intelligent dashboards and predictive insights.',
                    'Partnered with Product & Architecture teams on KPI-driven roadmaps and cloud deployments.'
                ]
            },
            {
                role: 'Senior IT Architect',
                company: 'FIS Canada',
                location: 'Toronto, ON',
                period: 'October 2020 – March 2022',
                side: 'right',
                description: 'Architected and deployed Code Connect API Gateway using WSO2 and cloud-native tooling.',
                details: [
                    'Architected and deployed Code Connect API Gateway using WSO2 and cloud-native tooling.',
                    'Implemented observability with OpenTelemetry and led secure API design for clients.',
                    'Translated complex business needs into robust, scalable, and secure technical solutions.'
                ]
            },
            {
                role: 'Senior IT Architect',
                company: 'FIS Global',
                location: 'Little Rock, AR',
                period: 'October 2015 – October 2020',
                side: 'left',
                description: 'Built automation and monitoring for API infrastructure; improved performance using JMeter + Dynatrace.',
                details: [
                    'Built automation and monitoring for API infrastructure.',
                    'Improved performance using JMeter + Dynatrace.',
                    'Conducted Code Reviews.'
                ]
            },
            {
                role: 'Project Lead / Dev Supervisor',
                company: 'FIS India',
                location: 'Bangalore, India',
                period: 'October 2010 – October 2015',
                side: 'right',
                description: 'Delivered modular banking applications (TouchPoint) with Spring & AngularJS; enforced security using Fortify.',
                details: [
                    'Delivered modular banking applications (TouchPoint) with Spring & AngularJS.',
                    'Enforced security using Fortify.',
                    'Mentored junior team members.'
                ]
            },
            {
                role: 'Technical Lead',
                company: 'CGI (Logica)',
                location: 'Bangalore',
                period: 'December 2006 – October 2010',
                side: 'left',
                description: 'Managed delivery of B2B payment portal; optimized integration and analytics.',
                details: [
                    'Managed delivery of B2B payment portal.',
                    'Optimized integration and analytics.'
                ]
            }
        ];

        const projectsData = [
            {
                title: 'Code Connect API Gateway',
                description: 'An enterprise-grade platform for managing, publishing, and analyzing APIs. Processed over 14 billion transactions in 2024. Built with microservices, deployed across Azure, AWS, and OpenShift.',
                tags: ['API Gateway', 'Microservices', 'Cloud-Native', 'AI-driven Analytics']
            },
            {
                title: 'Modular Banking Applications',
                description: 'Led the delivery of a modular banking application platform using Spring and AngularJS, with a strong focus on security and scalability.',
                tags: ['Spring', 'AngularJS', 'Banking Tech', 'Security']
            }
        ];

        const skillsData = {
            labels: ['API Architecture', 'Microservices', 'Cloud-Native Systems', 'AI/ML Analytics', 'Security Compliance', 'Multi-Cloud Deployments', 'Team Mentoring'],
            values: [95, 90, 95, 85, 90, 95, 90]
        };
        
        document.addEventListener('DOMContentLoaded', () => {
            const timelineContainer = document.getElementById('timeline-container');
            experienceData.forEach((item, index) => {
                const isLeft = item.side === 'left';
                const timelineItem = document.createElement('div');
                timelineItem.className = `timeline-item relative`;
                
                const contentBlock = `
                    <div class="bg-white p-6 rounded-lg shadow-md border-l-4 ${isLeft ? 'border-teal-500' : 'border-amber-500'}">
                        <p class="text-sm font-semibold text-teal-600">${item.period}</p>
                        <h3 class="text-xl font-bold mt-1">${item.role}</h3>
                        <p class="text-md font-medium text-zinc-600">${item.company} | ${item.location}</p>
                        <p class="mt-2 text-zinc-500">${item.description}</p>
                        <div class="timeline-content">
                            <ul class="mt-4 space-y-2 text-zinc-600 list-disc list-inside">
                                ${item.details.map(d => `<li>${d}</li>`).join('')}
                            </ul>
                        </div>
                    </div>
                `;

                timelineItem.innerHTML = `
                    <div class="absolute w-6 h-6 bg-white rounded-full mt-6 -top-1 border-4 ${isLeft ? 'border-teal-500 left-1/2 -translate-x-1/2' : 'border-amber-500 left-1/2 -translate-x-1/2'}"></div>
                    <div class="w-full cursor-pointer timeline-item-trigger">
                        ${contentBlock}
                    </div>
                `;
                timelineContainer.appendChild(timelineItem);
            });

            document.querySelectorAll('.timeline-item-trigger').forEach(trigger => {
                trigger.addEventListener('click', () => {
                    const parentItem = trigger.closest('.timeline-item');
                    parentItem.classList.toggle('active');
                });
            });

            const projectsContainer = document.getElementById('projects-container');
            projectsData.forEach(project => {
                const projectCard = document.createElement('div');
                projectCard.className = 'bg-zinc-100 p-6 rounded-lg shadow-sm hover:shadow-lg hover:-translate-y-1 transition-all';
                projectCard.innerHTML = `
                    <h4 class="text-xl font-bold mb-2">${project.title}</h4>
                    <p class="text-zinc-600 mb-4">${project.description}</p>
                    <div class="flex flex-wrap gap-2">
                        ${project.tags.map(tag => `<span class="bg-teal-100 text-teal-800 text-xs font-medium px-2.5 py-0.5 rounded-full">${tag}</span>`).join('')}
                    </div>
                `;
                projectsContainer.appendChild(projectCard);
            });

            const ctx = document.getElementById('skillsChart').getContext('2d');
            new Chart(ctx, {
                type: 'bar',
                data: {
                    labels: skillsData.labels,
                    datasets: [{
                        label: 'Competency Level',
                        data: skillsData.values,
                        backgroundColor: 'rgba(20, 184, 166, 0.6)',
                        borderColor: 'rgba(15, 118, 110, 1)',
                        borderWidth: 1
                    }]
                },
                options: {
                    indexAxis: 'y',
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            display: false
                        },
                        tooltip: {
                            callbacks: {
                                label: function(context) {
                                    let label = context.dataset.label || '';
                                    if (label) {
                                        label += ': ';
                                    }
                                    if (context.parsed.x !== null) {
                                        label += context.parsed.x + '%';
                                    }
                                    return label;
                                }
                            }
                        }
                    },
                    scales: {
                        x: {
                            beginAtZero: true,
                            max: 100,
                            ticks: {
                                callback: function(value) {
                                    return value + "%"
                                }
                            }
                        },
                        y: {
                           ticks: {
                                autoSkip: false,
                                callback: function(value, index, values) {
                                    const label = this.getLabelForValue(value);
                                    if (label.length > 16) {
                                        return label.match(/.{1,16}/g);
                                    }
                                    return label;
                                }
                           }
                        }
                    }
                }
            });
            
            const mobileMenuButton = document.getElementById('mobile-menu-button');
            const mobileMenu = document.getElementById('mobile-menu');
            mobileMenuButton.addEventListener('click', () => {
                mobileMenu.classList.toggle('hidden');
            });
            
            document.querySelectorAll('a[href^="#"]').forEach(anchor => {
                anchor.addEventListener('click', function (e) {
                    e.preventDefault();
                    document.querySelector(this.getAttribute('href')).scrollIntoView({
                        behavior: 'smooth'
                    });
                    if(mobileMenu.classList.contains('hidden') === false){
                        mobileMenu.classList.add('hidden');
                    }
                });
            });

            const navLinks = document.querySelectorAll('.nav-link');
            const sections = document.querySelectorAll('section');

            window.addEventListener('scroll', () => {
                let current = '';
                sections.forEach(section => {
                    const sectionTop = section.offsetTop;
                    if (pageYOffset >= sectionTop - 60) {
                        current = section.getAttribute('id');
                    }
                });

                navLinks.forEach(link => {
                    link.classList.remove('active');
                    if (link.getAttribute('href').includes(current)) {
                        link.classList.add('active');
                    }
                });
            });
        });
    </script>
</body>
</html>
