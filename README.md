<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sazid | Front-End Web Developer</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;800&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg-color: #0a0a0f;
            --glass-bg: rgba(255, 255, 255, 0.05);
            --glass-border: rgba(255, 255, 255, 0.1);
            --text-primary: #ffffff;
            --text-secondary: #a0a0b0;
            --accent: #00d2ff;
            --accent-2: #7a28ff;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }
        body {
            font-family: 'Inter', sans-serif;
            background: var(--bg-color);
            color: var(--text-primary);
            overflow-x: hidden;
            line-height: 1.6;
        }

        /* 3D Background Canvas */
        #bg-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
        }

        /* Navigation */
        nav {
            position: fixed;
            top: 0;
            width: 100%;
            padding: 20px 10%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            z-index: 100;
            backdrop-filter: blur(10px);
            background: rgba(10, 10, 15, 0.7);
            border-bottom: 1px solid var(--glass-border);
        }
        .logo { font-size: 1.5rem; font-weight: 800; background: linear-gradient(90deg, var(--accent), var(--accent-2)); -webkit-background-clip: text; -webkit-text-fill-color: transparent; }
        .nav-links a { color: var(--text-secondary); text-decoration: none; margin-left: 30px; font-weight: 400; transition: 0.3s; }
        .nav-links a:hover { color: var(--accent); }

        /* Sections */
        section {
            min-height: 100vh;
            padding: 120px 10% 80px;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }

        /* Hero Section */
        #hero h1 { font-size: 4.5rem; font-weight: 800; line-height: 1.1; margin-bottom: 20px; }
        #hero h1 span { background: linear-gradient(90deg, var(--accent), var(--accent-2)); -webkit-background-clip: text; -webkit-text-fill-color: transparent; }
        #hero p { font-size: 1.25rem; color: var(--text-secondary); max-width: 600px; margin-bottom: 30px; }
        .btn {
            display: inline-block;
            padding: 12px 30px;
            background: linear-gradient(90deg, var(--accent), var(--accent-2));
            color: #fff;
            text-decoration: none;
            border-radius: 50px;
            font-weight: 600;
            transition: transform 0.3s, box-shadow 0.3s;
        }
        .btn:hover { transform: translateY(-3px); box-shadow: 0 10px 20px rgba(0, 210, 255, 0.3); }

        /* Section Titles */
        .section-title { font-size: 2.5rem; margin-bottom: 50px; text-align: center; }
        .section-title span { color: var(--accent); }

        /* 3D Glass Cards */
        .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 30px; }
        .card-3d {
            perspective: 1000px;
        }
        .card-inner {
            background: var(--glass-bg);
            border: 1px solid var(--glass-border);
            border-radius: 20px;
            padding: 30px;
            backdrop-filter: blur(10px);
            transition: transform 0.1s ease-out, box-shadow 0.3s;
            transform-style: preserve-3d;
            height: 100%;
        }
        .card-inner:hover {
            box-shadow: 0 20px 40px rgba(0, 210, 255, 0.15);
            border-color: var(--accent);
        }
        .card-inner h3 { margin-bottom: 10px; color: var(--accent); transform: translateZ(20px); }
        .card-inner .role { font-weight: 600; margin-bottom: 5px; transform: translateZ(15px); }
        .card-inner .date { color: var(--text-secondary); font-size: 0.9rem; margin-bottom: 15px; transform: translateZ(10px); }
        .card-inner p, .card-inner ul { color: var(--text-secondary); transform: translateZ(5px); }
        .card-inner ul { padding-left: 20px; }
        .card-inner li { margin-bottom: 8px; }

        /* Skills */
        .skills-grid { display: flex; flex-wrap: wrap; gap: 15px; justify-content: center; }
        .skill-tag {
            padding: 10px 25px;
            background: var(--glass-bg);
            border: 1px solid var(--glass-border);
            border-radius: 50px;
            font-weight: 600;
            transition: 0.3s;
        }
        .skill-tag:hover { background: var(--accent); color: #000; border-color: var(--accent); transform: scale(1.05); }

        /* Contact */
        #contact { text-align: center; }
        .contact-info { display: flex; gap: 40px; justify-content: center; margin-top: 30px; flex-wrap: wrap; }
        .contact-item { font-size: 1.1rem; color: var(--text-secondary); }
        .contact-item strong { color: var(--text-primary); display: block; margin-bottom: 5px; }

        footer { text-align: center; padding: 30px; color: var(--text-secondary); border-top: 1px solid var(--glass-border); }

        @media (max-width: 768px) {
            #hero h1 { font-size: 2.5rem; }
            nav { padding: 15px 5%; }
            .nav-links a { margin-left: 15px; font-size: 0.9rem; }
            section { padding: 100px 5% 60px; }
        }
    </style>
</head>
<body>

    <canvas id="bg-canvas"></canvas>

    <nav>
        <div class="logo">SAZID.</div>
        <div class="nav-links">
            <a href="#about">About</a>
            <a href="#experience">Experience</a>
            <a href="#projects">Projects</a>
            <a href="#contact">Contact</a>
        </div>
    </nav>

    <section id="hero">
        <h1>Hi, I'm <span>Sazid</span>.<br>I build responsive web experiences.</h1>
        <p>A detail-oriented BCA graduate and Web Developer with 2 years of professional experience crafting user-focused digital solutions. Currently expanding my expertise in modern CSS and JavaScript.</p>
        <a href="#projects" class="btn">View My Work</a>
    </section>

    <section id="about">
        <h2 class="section-title">About <span>Me</span></h2>
        <div class="card-3d">
            <div class="card-inner">
                <p style="font-size: 1.1rem; max-width: 800px; margin: 0 auto; text-align: center;">
                    I am passionate about transitioning into full-time web development. With a strong foundation in HTML and growing expertise in CSS and JavaScript, I focus on building responsive, accessible, and highly optimized web layouts. My diverse background in customer support and backend operations has equipped me with unique problem-solving skills, allowing me to approach development with a strong user-centric and operational mindset.
                </p>
            </div>
        </div>
    </section>

    <section id="experience">
        <h2 class="section-title">Work <span>Experience</span></h2>
        <div class="grid">
            <div class="card-3d">
                <div class="card-inner">
                    <h3>Haircoaction</h3>
                    <div class="role">Web Developer</div>
                    <div class="date">2 Years</div>
                    <ul>
                        <li>Built and maintained responsive web layouts using modern front-end technologies.</li>
                        <li>Collaborated with design teams to ensure seamless UX and UI functionality.</li>
                        <li>Optimized website performance and ensured cross-browser compatibility.</li>
                        <li>Troubleshot and debugged code to enhance site stability.</li>
                    </ul>
                </div>
            </div>
            <div class="card-3d">
                <div class="card-inner">
                    <h3>Cogent E-Service</h3>
                    <div class="role">Customer Support Executive</div>
                    <div class="date">1 Year</div>
                    <ul>
                        <li>Handled inbound queries via voice/chat and managed CRM systems.</li>
                        <li>Resolved complaints efficiently, maintaining high CSAT levels.</li>
                        <li>Developed strong multitasking skills in a fast-paced environment.</li>
                    </ul>
                </div>
            </div>
            <div class="card-3d">
                <div class="card-inner">
                    <h3>Digitech</h3>
                    <div class="role">Process Associate</div>
                    <div class="date">6 Months</div>
                    <ul>
                        <li>Assisted in backend operations, ensuring documentation accuracy.</li>
                        <li>Coordinated with teams to maintain smooth workflow processes.</li>
                        <li>Supported operational efficiency through high attention to detail.</li>
                    </ul>
                </div>
            </div>
        </div>
    </section>

    <section id="projects">
        <h2 class="section-title">Featured <span>Projects</span></h2>
        <div class="grid">
            <!-- Project 1 -->
            <div class="card-3d">
                <div class="card-inner">
                    <h3>E-Commerce Responsive Storefront</h3>
                    <p><strong>Tech:</strong> HTML5, CSS3 (Flexbox/Grid)</p>
                    <p style="margin-top:10px;">Developed a fully responsive e-commerce product layout inspired by my work at Haircoaction. Focused on mobile-first design, ensuring seamless navigation across devices. Implemented CSS Grid for complex product galleries and optimized image loading for faster page render times.</p>
                </div>
            </div>
            <!-- Project 2 -->
            <div class="card-3d">
                <div class="card-inner">
                    <h3>Interactive Analytics Dashboard</h3>
                    <p><strong>Tech:</strong> HTML, CSS Variables, JavaScript</p>
                    <p style="margin-top:10px;">Built a clean, data-focused dashboard UI. Used JavaScript for DOM manipulation to create interactive data tables and dynamic filtering. Utilized CSS variables to implement a seamless dark/light mode toggle, enhancing user accessibility and interface customization.</p>
                </div>
            </div>
            <!-- Project 3 -->
            <div class="card-3d">
                <div class="card-inner">
                    <h3>CRM Ticketing Portal</h3>
                    <p><strong>Tech:</strong> HTML5, CSS3, JavaScript (Form Validation)</p>
                    <p style="margin-top:10px;">Drawing from my customer support experience at Cogent, I designed a frontend for a customer ticketing system. Created intuitive forms with real-time JavaScript validation to reduce user errors, ensuring a smooth, frustration-free experience for support agents and customers.</p>
                </div>
            </div>
            <!-- Project 4 -->
            <div class="card-3d">
                <div class="card-inner">
                    <h3>3D CSS Product Showcase</h3>
                    <p><strong>Tech:</strong> Advanced CSS3 (3D Transforms, Animations)</p>
                    <p style="margin-top:10px;">An experimental project to master CSS 3D transforms. Created an interactive product card that flips and rotates in 3D space on hover using `perspective` and `transform-style: preserve-3d`. Showcases my dedication to pushing the boundaries of modern CSS animations.</p>
                </div>
            </div>
        </div>
    </section>

    <section id="skills">
        <h2 class="section-title">Technical <span>Skills</span></h2>
        <div class="skills-grid">
            <div class="skill-tag">HTML5</div>
            <div class="skill-tag">CSS3</div>
            <div class="skill-tag">JavaScript</div>
            <div class="skill-tag">Responsive Design</div>
            <div class="skill-tag">Cross-Browser Compatibility</div>
            <div class="skill-tag">UI/UX Principles</div>
            <div class="skill-tag">MS Excel / Word</div>
            <div class="skill-tag">Problem Solving</div>
        </div>
    </section>

    <section id="contact">
        <h2 class="section-title">Get In <span>Touch</span></h2>
        <p style="color: var(--text-secondary); max-width: 600px; margin: 0 auto;">I am currently looking for full-time Web Development opportunities. If you have a role that fits my skills, let's connect!</p>
        <div class="contact-info">
            <div class="contact-item">
                <strong>Email</strong>
                ch.sajidali2344@gmail.com
            </div>
            <div class="contact-item">
                <strong>Phone</strong>
                +91 8448634192
            </div>
            <div class="contact-item">
                <strong>Location</strong>
                Noida, India
            </div>
        </div>
    </section>

    <footer>
        <p>&copy; 2026 Sazid. Crafted with HTML, CSS, JS & Three.js.</p>
    </footer>

    <!-- Three.js for 3D Background -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <script>
        // --- 3D Particle Background ---
        const canvas = document.getElementById('bg-canvas');
        const scene = new THREE.Scene();
        const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
        const renderer = new THREE.WebGLRenderer({ canvas: canvas, alpha: true, antialias: true });
        renderer.setSize(window.innerWidth, window.innerHeight);

        const particlesGeometry = new THREE.BufferGeometry();
        const particlesCount = 1500;
        const posArray = new Float32Array(particlesCount * 3);

        for(let i = 0; i < particlesCount * 3; i++) {
            posArray[i] = (Math.random() - 0.5) * 10;
        }
        particlesGeometry.setAttribute('position', new THREE.BufferAttribute(posArray, 3));
        
        const particlesMaterial = new THREE.PointsMaterial({
            size: 0.005,
            color: 0x00d2ff,
            transparent: true,
            opacity: 0.8
        });
        const particlesMesh = new THREE.Points(particlesGeometry, particlesMaterial);
        scene.add(particlesMesh);
        camera.position.z = 3;

        let mouseX = 0, mouseY = 0;
        document.addEventListener('mousemove', (event) => {
            mouseX = (event.clientX / window.innerWidth) * 2 - 1;
            mouseY = -(event.clientY / window.innerHeight) * 2 + 1;
        });

        function animateThree() {
            requestAnimationFrame(animateThree);
            particlesMesh.rotation.y += 0.0005;
            particlesMesh.rotation.x += 0.0005;
            
            // React to mouse
            particlesMesh.rotation.y += mouseX * 0.0005;
            particlesMesh.rotation.x += mouseY * 0.0005;
            
            renderer.render(scene, camera);
        }
        animateThree();

        window.addEventListener('resize', () => {
            camera.aspect = window.innerWidth / window.innerHeight;
            camera.updateProjectionMatrix();
            renderer.setSize(window.innerWidth, window.innerHeight);
        });

        // --- CSS 3D Tilt Effect for Cards ---
        const cards = document.querySelectorAll('.card-3d');
        cards.forEach(card => {
            const inner = card.querySelector('.card-inner');
            card.addEventListener('mousemove', (e) => {
                const rect = card.getBoundingClientRect();
                const x = e.clientX - rect.left;
                const y = e.clientY - rect.top;
                const centerX = rect.width / 2;
                const centerY = rect.height / 2;
                
                // Calculate rotation (max 15 degrees)
                const rotateX = ((y - centerY) / centerY) * -10;
                const rotateY = ((x - centerX) / centerX) * 10;
                
                inner.style.transform = `rotateX(${rotateX}deg) rotateY(${rotateY}deg) scale3d(1.02, 1.02, 1.02)`;
            });
            
            card.addEventListener('mouseleave', () => {
                inner.style.transform = 'rotateX(0) rotateY(0) scale3d(1, 1, 1)';
            });
        });

        // --- Smooth Scrolling ---
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                document.querySelector(this.getAttribute('href')).scrollIntoView({
                    behavior: 'smooth'
                });
            });
        });
    </script>
</body>
</html>
