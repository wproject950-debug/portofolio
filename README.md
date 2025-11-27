<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Win Project | Portfolio</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        /* CSS Variables */
        :root {
            --primary-color: #2c3e50;
            --secondary-color: #3498db;
            --accent-color: #e74c3c;
            --light-color: #ecf0f1;
            --dark-color: #2c3e50;
            --text-color: #333;
            --text-light: #777;
            --shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            --transition: all 0.3s ease;
            --bg-color: #f9f9f9;
            --card-bg: white;
            --header-bg: white;
        }

        /* Dark Mode Variables */
        .dark-mode {
            --primary-color: #ecf0f1;
            --secondary-color: #3498db;
            --accent-color: #e74c3c;
            --light-color: #2c3e50;
            --dark-color: #ecf0f1;
            --text-color: #ecf0f1;
            --text-light: #bdc3c7;
            --shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
            --bg-color: #121212;
            --card-bg: #1e1e1e;
            --header-bg: #1e1e1e;
        }

        /* Base Styles */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: var(--text-color);
            background-color: var(--bg-color);
            transition: background-color 0.5s ease, color 0.5s ease;
            overflow-x: hidden;
        }

        a {
            text-decoration: none;
            color: inherit;
        }

        ul {
            list-style: none;
        }

        .container {
            width: 90%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 15px;
        }

        .section {
            padding: 80px 0;
        }

        .section-title {
            text-align: center;
            margin-bottom: 50px;
            position: relative;
        }

        .section-title h2 {
            font-size: 2.5rem;
            color: var(--primary-color);
            margin-bottom: 15px;
        }

        .section-title::after {
            content: '';
            position: absolute;
            width: 80px;
            height: 4px;
            background: var(--secondary-color);
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
        }

        .btn {
            display: inline-block;
            padding: 12px 28px;
            background: var(--secondary-color);
            color: white;
            border-radius: 5px;
            font-weight: 600;
            transition: var(--transition);
            border: none;
            cursor: pointer;
        }

        .btn:hover {
            background: #2980b9;
            transform: translateY(-3px);
            box-shadow: var(--shadow);
        }

        /* Intro Animation */
        .intro {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100vh;
            background: var(--bg-color);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            overflow: hidden;
        }

        .intro.hidden {
            opacity: 0;
            pointer-events: none;
            transition: opacity 0.8s ease;
        }

        .intro-content {
            text-align: center;
        }

        .intro-logo {
            font-size: 4rem;
            font-weight: 700;
            color: var(--secondary-color);
            margin-bottom: 20px;
            opacity: 0;
            transform: translateY(30px);
        }

        .intro-text {
            font-size: 1.2rem;
            color: var(--text-color);
            opacity: 0;
            transform: translateY(30px);
        }

        .loading-bar {
            width: 200px;
            height: 4px;
            background: rgba(0, 0, 0, 0.1);
            margin: 30px auto 0;
            border-radius: 2px;
            overflow: hidden;
        }

        .loading-progress {
            height: 100%;
            width: 0%;
            background: var(--secondary-color);
            border-radius: 2px;
            transition: width 2s ease;
        }

        /* Header & Navigation */
        header {
            background: var(--header-bg);
            box-shadow: var(--shadow);
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            transition: background-color 0.5s ease;
        }

        .navbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 0;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: 700;
            color: var(--primary-color);
        }

        .logo span {
            color: var(--secondary-color);
        }

        .nav-links {
            display: flex;
            align-items: center;
        }

        .nav-links li {
            margin-left: 30px;
        }

        .nav-links a {
            font-weight: 600;
            transition: var(--transition);
            position: relative;
        }

        .nav-links a:hover {
            color: var(--secondary-color);
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            background: var(--secondary-color);
            bottom: -5px;
            left: 0;
            transition: var(--transition);
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        .theme-toggle {
            background: none;
            border: none;
            color: var(--primary-color);
            font-size: 1.2rem;
            cursor: pointer;
            transition: var(--transition);
            margin-left: 20px;
            width: 40px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 50%;
            background: var(--light-color);
        }

        .theme-toggle:hover {
            color: var(--secondary-color);
            transform: rotate(30deg);
        }

        .menu-toggle {
            display: none;
            font-size: 1.5rem;
            cursor: pointer;
            color: var(--primary-color);
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            background: linear-gradient(rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.7)), url('https://images.unsplash.com/photo-1517077304055-6e89abbf09b0?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2069&q=80') center/cover no-repeat;
            color: white;
            display: flex;
            align-items: center;
            text-align: center;
        }

        .hero-content {
            max-width: 800px;
            margin: 0 auto;
            opacity: 0;
            transform: translateY(30px);
            transition: opacity 1s ease, transform 1s ease;
        }

        .hero.animate .hero-content {
            opacity: 1;
            transform: translateY(0);
        }

        .hero h1 {
            font-size: 3.5rem;
            margin-bottom: 20px;
        }

        .hero p {
            font-size: 1.2rem;
            margin-bottom: 30px;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
        }

        .hero-btns {
            display: flex;
            justify-content: center;
            gap: 20px;
        }

        .btn-outline {
            background: transparent;
            border: 2px solid white;
        }

        .btn-outline:hover {
            background: white;
            color: var(--primary-color);
        }

        /* About Section */
        .about-content {
            display: grid;
            grid-template-columns: 1fr 2fr;
            gap: 50px;
            align-items: center;
        }

        .about-img {
            border-radius: 10px;
            overflow: hidden;
            box-shadow: var(--shadow);
        }

        .about-img img {
            width: 100%;
            height: auto;
            display: block;
            transition: var(--transition);
        }

        .about-img:hover img {
            transform: scale(1.05);
        }

        .about-text h3 {
            font-size: 1.8rem;
            margin-bottom: 20px;
            color: var(--primary-color);
        }

        .about-text p {
            margin-bottom: 20px;
            color: var(--text-light);
        }

        .skills {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin-top: 20px;
        }

        .skill {
            background: var(--light-color);
            padding: 8px 15px;
            border-radius: 30px;
            font-size: 0.9rem;
            font-weight: 600;
            color: var(--text-color);
            transition: var(--transition);
        }

        /* Projects Section */
        .projects {
            background: var(--light-color);
            transition: background-color 0.5s ease;
        }

        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 30px;
        }

        .project-card {
            background: var(--card-bg);
            border-radius: 10px;
            overflow: hidden;
            box-shadow: var(--shadow);
            transition: var(--transition);
        }

        .project-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.15);
        }

        .project-img {
            height: 200px;
            overflow: hidden;
        }

        .project-img img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: var(--transition);
        }

        .project-card:hover .project-img img {
            transform: scale(1.1);
        }

        .project-info {
            padding: 20px;
        }

        .project-info h3 {
            margin-bottom: 10px;
            color: var(--primary-color);
        }

        .project-info p {
            color: var(--text-light);
            margin-bottom: 15px;
            font-size: 0.95rem;
        }

        .project-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin-bottom: 15px;
        }

        .project-tag {
            background: var(--light-color);
            padding: 5px 10px;
            border-radius: 5px;
            font-size: 0.8rem;
            color: var(--text-light);
        }

        .project-links {
            display: flex;
            gap: 15px;
        }

        .project-link {
            font-size: 0.9rem;
            font-weight: 600;
            color: var(--secondary-color);
            display: flex;
            align-items: center;
            gap: 5px;
            transition: var(--transition);
        }

        .project-link:hover {
            color: var(--primary-color);
        }

        /* Contact Section */
        .contact-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 50px;
        }

        .contact-info h3 {
            font-size: 1.8rem;
            margin-bottom: 20px;
            color: var(--primary-color);
        }

        .contact-info p {
            margin-bottom: 30px;
            color: var(--text-light);
        }

        .contact-details {
            margin-bottom: 30px;
        }

        .contact-item {
            display: flex;
            align-items: center;
            margin-bottom: 15px;
        }

        .contact-item i {
            width: 40px;
            height: 40px;
            background: var(--light-color);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-right: 15px;
            color: var(--secondary-color);
        }

        .social-links {
            display: flex;
            gap: 15px;
        }

        .social-link {
            width: 40px;
            height: 40px;
            background: var(--light-color);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: var(--transition);
        }

        .social-link:hover {
            background: var(--secondary-color);
            color: white;
            transform: translateY(-5px);
        }

        .contact-form .form-group {
            margin-bottom: 20px;
        }

        .contact-form input,
        .contact-form textarea {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-family: inherit;
            font-size: 1rem;
            transition: var(--transition);
            background: var(--card-bg);
            color: var(--text-color);
        }

        .contact-form input:focus,
        .contact-form textarea:focus {
            border-color: var(--secondary-color);
            outline: none;
        }

        .contact-form textarea {
            height: 150px;
            resize: vertical;
        }

        /* Footer */
        footer {
            background: var(--dark-color);
            color: white;
            padding: 40px 0;
            text-align: center;
            transition: background-color 0.5s ease;
        }

        .footer-content {
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .footer-logo {
            font-size: 1.8rem;
            font-weight: 700;
            margin-bottom: 20px;
        }

        .footer-links {
            display: flex;
            gap: 20px;
            margin-bottom: 20px;
        }

        .footer-links a {
            transition: var(--transition);
        }

        .footer-links a:hover {
            color: var(--secondary-color);
        }

        .copyright {
            color: #aaa;
            font-size: 0.9rem;
        }

        /* Animation Classes */
        .fade-in {
            opacity: 0;
            transform: translateY(30px);
            transition: opacity 0.8s ease, transform 0.8s ease;
        }

        .fade-in.visible {
            opacity: 1;
            transform: translateY(0);
        }

        /* Responsive Design */
        @media (max-width: 992px) {
            .about-content,
            .contact-content {
                grid-template-columns: 1fr;
            }

            .about-img {
                max-width: 400px;
                margin: 0 auto;
            }
        }

        @media (max-width: 768px) {
            .navbar {
                padding: 15px 0;
            }

            .nav-links {
                position: fixed;
                top: 70px;
                left: -100%;
                width: 100%;
                background: var(--header-bg);
                flex-direction: column;
                align-items: center;
                padding: 20px 0;
                box-shadow: var(--shadow);
                transition: var(--transition);
                z-index: 999;
            }

            .nav-links.active {
                left: 0;
            }

            .nav-links li {
                margin: 15px 0;
            }

            .menu-toggle {
                display: block;
            }

            .hero h1 {
                font-size: 2.5rem;
            }

            .hero-btns {
                flex-direction: column;
                align-items: center;
            }

            .btn {
                width: 200px;
                text-align: center;
            }

            .theme-toggle {
                margin-left: 0;
            }
        }
    </style>
</head>
<body>
    <!-- Intro Animation -->
    <div class="intro" id="intro">
        <div class="intro-content">
            <div class="intro-logo">Win Project<span>.</span></div>
            <div class="intro-text">Front End Developer & UI/UX Designer</div>
            <div class="loading-bar">
                <div class="loading-progress"></div>
            </div>
        </div>
    </div>

    <!-- Header & Navigation -->
    <header>
        <div class="container">
            <nav class="navbar">
                <a href="#" class="logo">Win Project<span>.</span></a>
                <ul class="nav-links">
                    <li><a href="#home">Home</a></li>
                    <li><a href="#about">About</a></li>
                    <li><a href="#projects">Projects</a></li>
                    <li><a href="#contact">Contact</a></li>
                    <li>
                        <button class="theme-toggle" id="themeToggle">
                            <i class="fas fa-moon"></i>
                        </button>
                    </li>
                </ul>
                <div class="menu-toggle">
                    <i class="fas fa-bars"></i>
                </div>
            </nav>
        </div>
    </header>

    <!-- Hero Section -->
    <section id="home" class="hero">
        <div class="container">
            <div class="hero-content">
                <h1>Win Project</h1>
                <p>Front End Developer & UI/UX Designer passionate about creating beautiful, functional web experiences.</p>
                <div class="hero-btns">
                    <a href="#projects" class="btn">View My Work</a>
                    <a href="#contact" class="btn btn-outline">Get In Touch</a>
                </div>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section id="about" class="section">
        <div class="container">
            <div class="section-title fade-in">
                <h2>About Me</h2>
            </div>
            <div class="about-content">
                <div class="about-img fade-in">
                    <img src="https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=774&q=80" alt="Alex Morgan">
                </div>
                <div class="about-text fade-in">
                    <h3>Hello! I'm Win Project</h3>
                    <p>I'm a passionate front end developer with 1 years of experience building web applications. I specialize in creating responsive, user-friendly interfaces and robust backend systems.</p>
                    <p>My journey in web development started during my computer science degree, and I've been hooked ever since. I love solving complex problems and turning ideas into reality through code.</p>
                    <p>When I'm not coding, you can find me hiking, reading tech blogs, or experimenting with new frameworks and tools.</p>
                    <div class="skills">
                        <span class="skill">HTML/CSS</span>
                        <span class="skill">JavaScript</span>
                        <span class="skill">React</span>
                        <span class="skill">Node.js</span>
                        <span class="skill">Python</span>
                        <span class="skill">UI/UX Design</span>
                        <span class="skill">Responsive Design</span>
                        <span class="skill">Git</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Projects Section -->
    <section id="projects" class="section projects">
        <div class="container">
            <div class="section-title fade-in">
                <h2>My Projects</h2>
            </div>
            <div class="projects-grid">
                <!-- Project 1 -->
                <div class="project-card fade-in">
                    <div class="project-img">
                        <img src="https://images.unsplash.com/photo-1551650975-87deedd944c3?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1674&q=80" alt="E-commerce Website">
                    </div>
                    <div class="project-info">
                        <h3>E-commerce Platform</h3>
                        <p>A full-featured online store with product catalog, shopping cart, and secure checkout.</p>
                        <div class="project-tags">
                            <span class="project-tag">React</span>
                            <span class="project-tag">Node.js</span>
                            <span class="project-tag">MongoDB</span>
                        </div>
                        <div class="project-links">
                            <a href="#" class="project-link"><i class="fas fa-external-link-alt"></i> Live Demo</a>
                            <a href="#" class="project-link"><i class="fab fa-github"></i> Source Code</a>
                        </div>
                    </div>
                </div>

                <!-- Project 2 -->
                <div class="project-card fade-in">
                    <div class="project-img">
                        <img src="https://images.unsplash.com/photo-1551288049-bebda4e38f71?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1770&q=80" alt="Task Management App">
                    </div>
                    <div class="project-info">
                        <h3>Task Management App</h3>
                        <p>A productivity application for managing tasks, projects, and team collaboration.</p>
                        <div class="project-tags">
                            <span class="project-tag">Vue.js</span>
                            <span class="project-tag">Firebase</span>
                            <span class="project-tag">SCSS</span>
                        </div>
                        <div class="project-links">
                            <a href="#" class="project-link"><i class="fas fa-external-link-alt"></i> Live Demo</a>
                            <a href="#" class="project-link"><i class="fab fa-github"></i> Source Code</a>
                        </div>
                    </div>
                </div>

                <!-- Project 3 -->
                <div class="project-card fade-in">
                    <div class="project-img">
                        <img src="https://images.unsplash.com/photo-1552664730-d307ca884978?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1770&q=80" alt="Weather Dashboard">
                    </div>
                    <div class="project-info">
                        <h3>Weather Dashboard</h3>
                        <p>A responsive weather application with forecasts, maps, and location-based services.</p>
                        <div class="project-tags">
                            <span class="project-tag">JavaScript</span>
                            <span class="project-tag">API Integration</span>
                            <span class="project-tag">Bootstrap</span>
                        </div>
                        <div class="project-links">
                            <a href="#" class="project-link"><i class="fas fa-external-link-alt"></i> Live Demo</a>
                            <a href="#" class="project-link"><i class="fab fa-github"></i> Source Code</a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="section">
        <div class="container">
            <div class="section-title fade-in">
                <h2>Get In Touch</h2>
            </div>
            <div class="contact-content">
                <div class="contact-info fade-in">
                    <h3>Let's Work Together</h3>
                    <p>I'm currently available for freelance work. Feel free to reach out if you have a project in mind or just want to connect!</p>
                    <div class="contact-details">
                        <div class="contact-item">
                            <i class="fas fa-envelope"></i>
                            <span>Win Project</span>
                        </div>
                        <div class="contact-item">
                            <i class="fas fa-phone"></i>
                            <span>+62 814 6030 8354</span>
                        </div>
                        <div class="contact-item">
                            <i class="fas fa-map-marker-alt"></i>
                            <span>Surakarta, IDN</span>
                        </div>
                    </div>
                    <div class="social-links">
                        <a href="#" class="social-link"><i class="fab fa-github"></i></a>
                        <a href="#" class="social-link"><i class="fab fa-linkedin-in"></i></a>
                        <a href="#" class="social-link"><i class="fab fa-twitter"></i></a>
                        <a href="#" class="social-link"><i class="fab fa-dribbble"></i></a>
                    </div>
                </div>
                <form class="contact-form fade-in">
                    <div class="form-group">
                        <input type="text" placeholder="Your Name" required>
                    </div>
                    <div class="form-group">
                        <input type="email" placeholder="Your Email" required>
                    </div>
                    <div class="form-group">
                        <input type="text" placeholder="Subject">
                    </div>
                    <div class="form-group">
                        <textarea placeholder="Your Message" required></textarea>
                    </div>
                    <button type="submit" class="btn">Send Message</button>
                </form>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-content">
                <a href="#" class="footer-logo">Win Project<span>.</span></a>
                <div class="footer-links">
                    <a href="#home">Home</a>
                    <a href="#about">About</a>
                    <a href="#projects">Projects</a>
                    <a href="#contact">Contact</a>
                </div>
                <p class="copyright">&copy; 2025 Win Project. All rights reserved.</p>
            </div>
        </div>
    </footer>

    <script>
        // Intro Animation
        document.addEventListener('DOMContentLoaded', function() {
            const intro = document.getElementById('intro');
            const introLogo = document.querySelector('.intro-logo');
            const introText = document.querySelector('.intro-text');
            const loadingProgress = document.querySelector('.loading-progress');
            const hero = document.querySelector('.hero');
            
            // Animate intro elements
            setTimeout(() => {
                introLogo.style.opacity = '1';
                introLogo.style.transform = 'translateY(0)';
            }, 500);
            
            setTimeout(() => {
                introText.style.opacity = '1';
                introText.style.transform = 'translateY(0)';
            }, 1000);
            
            // Animate loading bar
            setTimeout(() => {
                loadingProgress.style.width = '100%';
            }, 1500);
            
            // Hide intro and show main content
            setTimeout(() => {
                intro.classList.add('hidden');
                hero.classList.add('animate');
                
                // Animate sections on scroll
                animateSections();
                
                // Remove intro from DOM after transition completes
                setTimeout(() => {
                    intro.style.display = 'none';
                }, 800);
            }, 3500);
        });

        // Dark/Light Mode Toggle
        const themeToggle = document.getElementById('themeToggle');
        const themeIcon = themeToggle.querySelector('i');
        
        // Check for saved theme preference or default to light
        const currentTheme = localStorage.getItem('theme') || 'light';
        
        if (currentTheme === 'dark') {
            document.body.classList.add('dark-mode');
            themeIcon.classList.remove('fa-moon');
            themeIcon.classList.add('fa-sun');
        }
        
        themeToggle.addEventListener('click', function() {
            document.body.classList.toggle('dark-mode');
            
            if (document.body.classList.contains('dark-mode')) {
                themeIcon.classList.remove('fa-moon');
                themeIcon.classList.add('fa-sun');
                localStorage.setItem('theme', 'dark');
            } else {
                themeIcon.classList.remove('fa-sun');
                themeIcon.classList.add('fa-moon');
                localStorage.setItem('theme', 'light');
            }
        });

        // Mobile menu toggle
        document.querySelector('.menu-toggle').addEventListener('click', function() {
            document.querySelector('.nav-links').classList.toggle('active');
            
            // Toggle menu icon
            const icon = this.querySelector('i');
            if (icon.classList.contains('fa-bars')) {
                icon.classList.remove('fa-bars');
                icon.classList.add('fa-times');
            } else {
                icon.classList.remove('fa-times');
                icon.classList.add('fa-bars');
            }
        });

        // Close mobile menu when clicking on a link
        document.querySelectorAll('.nav-links a').forEach(link => {
            link.addEventListener('click', () => {
                document.querySelector('.nav-links').classList.remove('active');
                // Reset menu icon
                const menuToggleIcon = document.querySelector('.menu-toggle i');
                menuToggleIcon.classList.remove('fa-times');
                menuToggleIcon.classList.add('fa-bars');
            });
        });

        // Form submission (prevent default for demo)
        document.querySelector('.contact-form').addEventListener('submit', function(e) {
            e.preventDefault();
            alert('Thank you for your message! I\'ll get back to you soon.');
            this.reset();
        });

        // Animate sections on scroll
        function animateSections() {
            const fadeElements = document.querySelectorAll('.fade-in');
            
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.classList.add('visible');
                    }
                });
            }, { threshold: 0.1 });
            
            fadeElements.forEach(element => {
                observer.observe(element);
            });
        }

        // Smooth scroll for navigation links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                
                const targetId = this.getAttribute('href');
                if (targetId === '#') return;
                
                const targetElement = document.querySelector(targetId);
                if (targetElement) {
                    window.scrollTo({
                        top: targetElement.offsetTop - 80,
                        behavior: 'smooth'
                    });
                }
            });
        });
    </script>
</body>
</html>
