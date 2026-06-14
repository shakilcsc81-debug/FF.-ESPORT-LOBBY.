
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FF ESPORTS LOBBY - Play & Earn</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700;800&display=swap"
        rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Hind+Siliguri:wght@300;400;500;600;700&display=swap"
        rel="stylesheet">

    <style>
        /* ================= CSS STYLES ================= */
        :root {
            --primary: #FF5500;
            --primary-dark: #d64000;
            --bg-color: #f8f9fa;
            --text-dark: #222;
            --text-light: #666;
            --white: #ffffff;
            --card-bg: #ffffff;
            --border-color: #ddd;
            --input-bg: #fff;
            --sidebar-width: 280px;
        }

        body.dark-theme {
            --bg-color: #121212;
            --white: #1e1e1e;
            --card-bg: #1e1e1e;
            --text-dark: #e0e0e0;
            --text-light: #a0a0a0;
            --border-color: #333;
            --input-bg: #2d2d2d;
        }

        body,
        .match-card,
        .game-card,
        .panel,
        .modal-content,
        .auth-page,
        .sidebar,
        .sidebar-header,
        .tab-btn {
            transition: background-color 0.3s, color 0.3s, border-color 0.3s;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', 'Hind Siliguri', sans-serif;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            background-color: var(--bg-color);
            padding-bottom: 80px;
            overflow-x: hidden;
            min-height: 100vh;
        }

        a {
            text-decoration: none;
            color: inherit;
        }

        /* --- HEADER --- */
        header {
            background: var(--white);
            padding: 12px 15px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.05);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 10px;
            cursor: pointer;
        }

        .logo img {
            height: 45px;
            object-fit: contain;
        }

        .logo-text {
            font-weight: 800;
            font-size: 22px;
            color: var(--primary);
            letter-spacing: -0.5px;
        }

        .header-right {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .theme-btn {
            background: rgba(0, 0, 0, 0.05);
            border: none;
            width: 32px;
            height: 32px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            color: var(--text-dark);
            font-size: 16px;
            transition: 0.3s;
        }

        body.dark-theme .theme-btn {
            background: rgba(255, 255, 255, 0.1);
        }

        .auth-buttons {
            display: flex;
            gap: 10px;
        }

        .btn-login-nav {
            background: transparent;
            color: var(--text-dark);
            border: 1px solid var(--border-color);
            padding: 6px 15px;
            border-radius: 5px;
            font-weight: 600;
            font-size: 13px;
            cursor: pointer;
        }

        .btn-reg-nav {
            background: var(--primary);
            color: white;
            border: none;
            padding: 6px 15px;
            border-radius: 5px;
            font-weight: 600;
            font-size: 13px;
            cursor: pointer;
        }

        .user-nav {
            display: none;
            align-items: center;
            gap: 15px;
        }

        .balance-pill {
            background: #fff0f0;
            border: 1px solid #ffcccc;
            color: var(--primary);
            padding: 6px 16px;
            border-radius: 50px;
            font-size: 14px;
            font-weight: 700;
            display: flex;
            align-items: center;
            gap: 8px;
            cursor: pointer;
            transition: 0.3s;
        }

        .icon-btn {
            font-size: 22px;
            color: #333;
            cursor: pointer;
            position: relative;
        }

        .notif-badge {
            position: absolute;
            top: -5px;
            right: -5px;
            background: red;
            color: white;
            font-size: 10px;
            width: 16px;
            height: 16px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            display: none;
        }

        /* --- AUTH PAGES (FULL SCREEN) --- */
        .auth-page {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: white;
            z-index: 2000;
            overflow-y: auto;
            display: none;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }

        .auth-page.active {
            display: flex;
            animation: fadeIn 0.3s;
        }

        .auth-container {
            width: 100%;
            max-width: 400px;
            text-align: center;
        }

        .auth-title {
            font-size: 24px;
            font-weight: 700;
            margin-bottom: 5px;
            color: var(--text-dark);
        }

        .auth-sub {
            font-size: 14px;
            color: var(--text-light);
            margin-bottom: 30px;
        }

        /* --- SIDEBAR MENU --- */
        .sidebar-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.6);
            z-index: 998;
            display: none;
            opacity: 0;
            transition: opacity 0.3s;
            backdrop-filter: blur(2px);
        }

        .sidebar-overlay.active {
            display: block;
            opacity: 1;
        }

        .sidebar {
            position: fixed;
            top: 0;
            right: -320px;
            width: var(--sidebar-width);
            height: 100%;
            background: white;
            z-index: 999;
            transition: right 0.3s cubic-bezier(0.77, 0, 0.175, 1);
            box-shadow: -5px 0 15px rgba(0, 0, 0, 0.1);
            display: flex;
            flex-direction: column;
        }

        .sidebar.active {
            right: 0;
        }

        .notif-sidebar {
            position: fixed;
            top: 0;
            right: -320px;
            width: var(--sidebar-width);
            height: 100%;
            background: white;
            z-index: 999;
            transition: right 0.3s cubic-bezier(0.77, 0, 0.175, 1);
            box-shadow: -5px 0 15px rgba(0, 0, 0, 0.1);
            display: flex;
            flex-direction: column;
        }

        .notif-sidebar.active {
            right: 0;
        }

        .sidebar-header {
            padding: 30px 20px;
            border-bottom: 1px solid #f0f0f0;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 10px;
            background: #fff;
            position: relative;
        }

        .sidebar-close {
            position: absolute;
            top: 15px;
            right: 20px;
            font-size: 24px;
            color: #999;
            cursor: pointer;
        }

        .sidebar-avatar {
            width: 70px;
            height: 70px;
            border-radius: 50%;
            background: #eee;
            object-fit: cover;
            border: 3px solid var(--primary);
            padding: 2px;
        }

        .user-info {
            text-align: center;
        }

        .sidebar-menu {
            list-style: none;
            padding: 15px 0;
            overflow-y: auto;
            flex: 1;
        }

        .sidebar-menu li {
            padding: 14px 25px;
            cursor: pointer;
            font-size: 15px;
            color: #444;
            display: flex;
            align-items: center;
            gap: 15px;
            transition: background 0.2s;
            font-weight: 500;
            border-left: 4px solid transparent;
        }

        .sidebar-menu li:hover {
            background: #fff5f5;
            color: var(--primary);
            border-left-color: var(--primary);
        }

        .sidebar-menu li i {
            width: 25px;
            text-align: center;
            font-size: 18px;
            color: #888;
        }

        .sidebar-menu li:hover i {
            color: var(--primary);
        }

        .notif-item {
            padding: 15px;
            border-bottom: 1px solid #eee;
            display: flex;
            gap: 10px;
            align-items: flex-start;
        }

        .notif-icon {
            width: 35px;
            height: 35px;
            background: #fff0f0;
            color: var(--primary);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-shrink: 0;
        }

        .notif-content h5 {
            font-size: 13px;
            font-weight: 700;
            margin-bottom: 3px;
        }

        .notif-content p {
            font-size: 11px;
            color: #666;
            line-height: 1.4;
        }

        /* --- MAIN SECTIONS --- */
        .app-section {
            display: none;
            padding: 15px;
            animation: slideUp 0.3s ease-out;
        }

        .app-section.active {
            display: block;
        }

        @keyframes slideUp {
            from {
                opacity: 0;
                transform: translateY(10px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* HERO & SLIDER */
        .hero-banner {
            margin-bottom: 20px;
            border-radius: 12px;
            overflow: hidden;
            position: relative;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        }

        .alert-box {
            background: #222;
            color: white;
            padding: 8px;
            font-size: 13px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .slider-container {
            width: 100%;
            height: 180px;
            position: relative;
            overflow: hidden;
        }

        .slider-wrapper {
            display: flex;
            transition: transform 0.5s ease-in-out;
            height: 100%;
        }

        .slide {
            min-width: 100%;
            height: 100%;
            position: relative;
        }

        .slide img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .slide-caption {
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            background: rgba(0, 0, 0, 0.5);
            color: white;
            padding: 5px 10px;
            font-size: 12px;
        }

        .section-title {
            font-weight: 800;
            font-size: 18px;
            margin: 15px 0;
            color: var(--text-dark);
            border-left: 4px solid var(--primary);
            padding-left: 10px;
        }

        /* --- GRID SYSTEM --- */
        .category-list,
        #matches-container {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        @media (min-width: 768px) {
            .category-list,
            #matches-container {
                display: grid;
                grid-template-columns: repeat(2, 1fr);
                gap: 20px;
            }
        }

        @media (min-width: 1200px) {
            #matches-container {
                display: grid;
                grid-template-columns: repeat(4, 1fr);
                gap: 20px;
            }
            .category-list {
                display: grid;
                grid-template-columns: repeat(2, 1fr);
                gap: 20px;
            }
        }

        .game-card {
            height: 120px;
            border-radius: 12px;
            overflow: hidden;
            position: relative;
            cursor: pointer;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);
            display: flex;
            align-items: center;
            padding: 0 20px;
            transition: transform 0.2s;
            background-color: #000;
        }

        .game-card-bg {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-size: cover;
            background-position: center;
            opacity: 0.6;
            z-index: 1;
            transition: opacity 0.3s;
        }

        .game-card:hover .game-card-bg {
            opacity: 0.4;
        }

        .game-card-content {
            position: relative;
            z-index: 2;
            display: flex;
            align-items: center;
            gap: 15px;
            width: 100%;
        }

        .game-avatar {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            border: 3px solid #fff;
            object-fit: cover;
            background: #fff;
        }

        .game-info {
            flex: 1;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }

        .game-title {
            color: #fff;
            font-size: 20px;
            font-weight: 800;
            text-transform: uppercase;
            text-shadow: 0 2px 4px rgba(0, 0, 0, 0.8);
        }

        .match-count {
            color: #fff;
            font-size: 13px;
            font-weight: 500;
            margin-top: 4px;
            display: flex;
            align-items: center;
            gap: 5px;
        }

        .match-count::before {
            content: '';
            display: inline-block;
            width: 6px;
            height: 6px;
            background: #00ff00;
            border-radius: 50%;
        }

        /* --- MATCH VIEW --- */
        .how-to-join-btn {
            background: #f1f1f1;
            color: #333;
            font-size: 12px;
            font-weight: 600;
            padding: 10px;
            border-radius: 8px;
            text-align: center;
            margin-bottom: 15px;
            cursor: pointer;
            border: 1px solid #ddd;
        }

        .tab-container {
            display: flex;
            background: white;
            border-radius: 8px;
            overflow: hidden;
            margin-bottom: 20px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);
            border: 1px solid #eee;
        }

        .tab-btn {
            flex: 1;
            padding: 12px;
            text-align: center;
            font-size: 14px;
            font-weight: 600;
            cursor: pointer;
            transition: 0.3s;
            background: var(--card-bg);
            color: var(--text-light);
        }

        .tab-btn.active {
            background: #fff0f0;
            color: var(--primary);
            border-bottom: 2px solid var(--primary);
        }

        .match-card {
            background: var(--card-bg);
            border: 2px solid var(--primary);
            border-radius: 8px;
            padding: 15px;
            margin-bottom: 0;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.05);
            position: relative;
            display: flex;
            flex-direction: column;
        }

        .m-header {
            display: flex;
            gap: 12px;
            margin-bottom: 12px;
            align-items: flex-start;
        }

        .m-img {
            width: 50px;
            height: 50px;
            border-radius: 8px;
            object-fit: cover;
        }

        .m-title-box {
            flex: 1;
        }

        .m-title {
            font-size: 14px;
            font-weight: 700;
            color: #000;
            line-height: 1.3;
            margin-bottom: 4px;
            display: -webkit-box;
            -webkit-line-clamp: 2;
            -webkit-box-orient: vertical;
            overflow: hidden;
        }

        .m-time {
            font-size: 10px;
            color: var(--primary);
            font-weight: 600;
        }

        .m-stats-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 5px;
            margin-bottom: 15px;
            text-align: center;
        }

        .m-stat-box {
            display: flex;
            flex-direction: column;
        }

        .stat-label {
            font-size: 9px;
            color: #777;
            text-transform: uppercase;
            font-weight: 600;
            letter-spacing: 0.5px;
        }

        .stat-value {
            font-size: 11px;
            font-weight: 800;
            color: #000;
        }

        .progress-bar {
            height: 8px;
            background: #eee;
            border-radius: 10px;
            overflow: hidden;
            margin-bottom: 5px;
        }

        .progress-fill {
            height: 100%;
            background: var(--primary);
            border-radius: 10px;
        }

        .m-status-row {
            display: flex;
            justify-content: space-between;
            font-size: 10px;
            color: #666;
            margin-bottom: 15px;
            font-weight: 500;
        }

        .btn-join-outline {
            border: 1px solid var(--primary);
            color: white;
            background: var(--primary);
            padding: 8px 0;
            border-radius: 4px;
            font-size: 12px;
            font-weight: 700;
            cursor: pointer;
            transition: 0.2s;
            width: 48%;
            text-align: center;
        }

        .btn-join-outline:hover {
            opacity: 0.9;
        }

        .btn-view-participants {
            border: 1px solid #333;
            color: #333;
            background: transparent;
            padding: 8px 0;
            border-radius: 4px;
            font-size: 12px;
            font-weight: 700;
            cursor: pointer;
            transition: 0.2s;
            width: 48%;
            text-align: center;
        }

        .btn-view-participants:hover {
            background: #eee;
        }

        .btn-view-result {
            border: 1px solid #ccc;
            color: #333;
            background: #f9f9f9;
            padding: 4px 20px;
            border-radius: 4px;
            font-size: 12px;
            font-weight: 700;
            cursor: pointer;
            min-width: 80px;
            text-align: center;
            transition: 0.2s;
        }

        .btn-view-result:hover {
            background: #eee;
        }

        .btn-full-outline {
            border: 1px solid var(--primary);
            color: var(--primary);
            background: #fff;
            cursor: not-allowed;
            padding: 4px 20px;
            border-radius: 4px;
            font-size: 12px;
            font-weight: 700;
            min-width: 80px;
            text-align: center;
        }

        .m-btn-row {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
        }

        .btn-prize {
            background: #333;
            color: white;
            border: none;
            padding: 6px 15px;
            border-radius: 4px;
            font-size: 10px;
            font-weight: 600;
            cursor: pointer;
        }

        .btn-room {
            background: linear-gradient(45deg, #FF5500, #ff8800);
            color: white;
            border: none;
            padding: 6px 15px;
            border-radius: 4px;
            font-size: 10px;
            font-weight: 600;
            cursor: pointer;
        }

        .timer-display {
            text-align: center;
            font-size: 12px;
            font-weight: 600;
            color: #d64000;
            padding-top: 5px;
            border-top: 1px solid #f0f0f0;
            margin-top: auto;
            background: #fff5f5;
            border-radius: 4px;
            padding: 5px;
        }

        /* RESULT VIEW PAGE */
        .result-view-header {
            background: var(--card-bg);
            padding: 15px;
            border-radius: 8px;
            border: 1px solid var(--border-color);
            margin-bottom: 20px;
        }

        .result-view-title {
            font-size: 16px;
            font-weight: 700;
            color: var(--text-dark);
            margin-bottom: 10px;
        }

        .result-table {
            width: 100%;
            border-collapse: collapse;
            font-size: 13px;
            margin-bottom: 15px;
        }

        .result-table th {
            background: #f8f9fa;
            text-align: left;
            padding: 10px;
            font-weight: 700;
            color: #444;
            border-bottom: 2px solid #eee;
        }

        .result-table td {
            padding: 10px;
            border-bottom: 1px solid #eee;
            color: #333;
        }

        .winner-row {
            background: #f0fff4;
        }

        /* GENERAL UI ELEMENTS */
        .card-panel {
            background: var(--card-bg);
            padding: 25px;
            border-radius: 12px;
            box-shadow: 0 2px 15px rgba(0, 0, 0, 0.05);
            margin-bottom: 15px;
        }

        .card-panel h3 {
            font-size: 18px;
            margin-bottom: 20px;
            color: var(--text-dark);
            font-weight: 700;
            border-bottom: 2px solid var(--border-color);
            padding-bottom: 10px;
        }

        .form-group {
            margin-bottom: 18px;
            text-align: left;
        }

        .form-group label {
            display: block;
            font-size: 13px;
            color: #555;
            margin-bottom: 8px;
            font-weight: 500;
        }

        .input-field {
            width: 100%;
            padding: 14px;
            border: 1px solid var(--border-color);
            border-radius: 8px;
            outline: none;
            transition: 0.3s;
            font-size: 14px;
            background: var(--input-bg);
            color: var(--text-dark);
        }

        .input-field:focus {
            border-color: var(--primary);
            background: var(--input-bg);
            box-shadow: 0 0 0 3px rgba(255, 85, 0, 0.1);
        }

        .primary-btn {
            background: var(--primary);
            color: white;
            border: none;
            padding: 16px;
            border-radius: 8px;
            width: 100%;
            font-weight: 700;
            cursor: pointer;
            font-size: 16px;
            margin-top: 10px;
            box-shadow: 0 5px 15px rgba(255, 85, 0, 0.2);
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .primary-btn:disabled {
            background: #999;
            box-shadow: none;
            cursor: not-allowed;
        }

        .btn-cancel {
            background: #f1f1f1;
            color: #555;
            border: 1px solid #ddd;
            padding: 16px;
            border-radius: 8px;
            width: 100%;
            font-weight: 700;
            cursor: pointer;
            font-size: 16px;
            margin-top: 10px;
            text-align: center;
            display: block;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .btn-cancel:hover {
            background: #e9e9e9;
            border-color: #ccc;
        }

        .google-btn {
            background: #fff;
            color: #333;
            border: 1px solid #ddd;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);
            transition: 0.2s;
        }

        .google-btn:hover {
            background: #f9f9f9;
            border-color: #ccc;
        }

        /* MODALS */
        .modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.6);
            z-index: 3000;
            padding: 20px;
            display: none;
            align-items: center;
            justify-content: center;
            backdrop-filter: blur(3px);
        }

        .modal.active {
            display: flex;
            animation: fadeIn 0.2s;
        }

        .modal-box {
            background: var(--card-bg);
            width: 100%;
            max-width: 400px;
            padding: 25px;
            border-radius: 12px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
            text-align: center;
            position: relative;
            max-height: 90vh;
            overflow-y: auto;
        }

        .step-container {
            display: none;
            animation: slideInRight 0.3s ease;
        }

        .step-container.active-step {
            display: block;
        }

        @keyframes slideInRight {
            from {
                transform: translateX(20px);
                opacity: 0;
            }

            to {
                transform: translateX(0);
                opacity: 1;
            }
        }

        .method-btn {
            display: flex;
            align-items: center;
            gap: 15px;
            width: 100%;
            padding: 15px;
            border: 1px solid #eee;
            border-radius: 10px;
            cursor: pointer;
            margin-bottom: 15px;
            background: #fff;
            transition: 0.2s;
        }

        .method-btn:hover {
            border-color: var(--primary);
            background: #fff5f5;
        }

        .method-btn img {
            height: 35px;
            object-fit: contain;
        }
        
        .method-btn.selected {
             border-color: var(--primary);
             background: #fff5f5;
             box-shadow: 0 0 5px rgba(255, 85, 0, 0.3);
        }

        .back-nav {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 20px;
            cursor: pointer;
            color: var(--text-light);
            font-weight: 600;
        }

        .hidden {
            display: none !important;
        }

        /* --- BOTTOM NAV --- */
        .bottom-nav {
            position: fixed;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 65px;
            background: var(--white);
            display: flex;
            align-items: center;
            justify-content: space-around;
            box-shadow: 0 -3px 20px rgba(0,0,0,0.1);
            z-index: 500;
            border-top: 1px solid var(--border-color);
        }

        .bn-item {
            flex: 1;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            gap: 3px;
            cursor: pointer;
            padding: 8px 0;
            position: relative;
            transition: 0.2s;
            -webkit-tap-highlight-color: transparent;
        }

        .bn-item i {
            font-size: 19px;
            color: #bbb;
            transition: 0.2s;
        }

        .bn-item span {
            font-size: 10px;
            font-weight: 600;
            color: #bbb;
            transition: 0.2s;
        }

        .bn-item.bn-active i,
        .bn-item.bn-active span {
            color: var(--primary);
        }

        .bn-item.bn-active::after {
            content: '';
            position: absolute;
            top: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 36px;
            height: 3px;
            background: var(--primary);
            border-radius: 0 0 4px 4px;
        }

        .bn-center-wrap {
            flex: 1;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            -webkit-tap-highlight-color: transparent;
        }

        .bn-center-btn {
            width: 50px;
            height: 50px;
            background: linear-gradient(135deg, #FF5500, #ff8800);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-top: -22px;
            box-shadow: 0 4px 15px rgba(255,85,0,0.45);
            border: 3px solid var(--bg-color);
            transition: transform 0.2s;
        }

        .bn-center-btn i {
            font-size: 20px;
            color: white;
        }

        .bn-center-wrap span {
            font-size: 10px;
            font-weight: 600;
            color: #bbb;
            margin-top: 2px;
        }

        .bn-center-wrap:active .bn-center-btn {
            transform: scale(0.92);
        }

        /* ================= SLOT SYSTEM CSS ================= */
        #slot-selection-container {
            margin-bottom: 20px;
        }
        #join-slot-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 8px;
            max-height: 250px;
            overflow-y: auto;
            padding-right: 5px;
        }
        @media (max-width: 400px) {
            #join-slot-grid {
                grid-template-columns: repeat(3, 1fr);
            }
        }
        .slot-box {
            border: 1.5px solid var(--border-color);
            border-radius: 8px;
            padding: 10px 5px;
            text-align: center;
            font-size: 13px;
            font-weight: 700;
            cursor: pointer;
            background: var(--input-bg);
            color: var(--text-dark);
            transition: 0.2s;
            min-height: 50px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }
        .slot-box:hover:not(.taken) {
            border-color: var(--primary);
            background: #fff5f0;
        }
        .slot-box.taken {
            background: #f1f1f1;
            color: #888;
            cursor: not-allowed;
            border-color: #ddd;
        }
        .slot-box.selected {
            background: var(--primary);
            color: white;
            border-color: var(--primary);
        }
        .slot-players {
            font-size: 9px;
            font-weight: 500;
            color: inherit;
            margin-top: 4px;
            line-height: 1.2;
            word-break: break-all;
        }

        /* VIEW JOINED SLOTS CSS */
        .joined-slots-grid {
            display: grid;
            grid-template-columns: 1fr;
            gap: 12px;
        }
        @media (min-width: 768px) {
            .joined-slots-grid {
                grid-template-columns: repeat(2, 1fr);
            }
        }
        .j-slot-box {
            border: 1px solid var(--border-color);
            border-radius: 8px;
            background: var(--card-bg);
            overflow: hidden;
        }
        .j-slot-header {
            background: #f8f9fa;
            padding: 8px 12px;
            font-size: 13px;
            font-weight: 700;
            border-bottom: 1px solid var(--border-color);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        .j-slot-body {
            padding: 10px 12px;
        }
        .j-player-row {
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-size: 12px;
            font-weight: 600;
            padding: 4px 0;
            border-bottom: 1px dashed #eee;
        }
        .j-player-row:last-child {
            border-bottom: none;
        }
        .j-taken {
            border-color: #ddd;
        }
        .j-empty {
            opacity: 0.7;
        }
        .j-me {
            border-color: var(--primary);
            box-shadow: 0 2px 8px rgba(255,85,0,0.15);
        }
        .j-me .j-slot-header {
            background: #fff5f0;
            color: var(--primary);
            border-bottom-color: #ffdacc;
        }
        .j-badge {
            background: var(--primary);
            color: white;
            font-size: 9px;
            padding: 2px 6px;
            border-radius: 20px;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }
        
        /* RULES TAB SYSTEM CSS */
        .rule-tab {
            padding: 8px 16px;
            background: #f1f1f1;
            border-radius: 50px;
            font-size: 12px;
            font-weight: 700;
            white-space: nowrap;
            cursor: pointer;
            transition: 0.2s;
            color: #555;
            border: 1px solid #ddd;
        }
        .rule-tab.active {
            background: var(--primary);
            color: #fff;
            border-color: var(--primary);
            box-shadow: 0 4px 10px rgba(255,85,0,0.2);
        }
        #rules-category-tabs::-webkit-scrollbar {
            display: none;
        }
    </style>
</head>

<body>

    <header>
        <div class="logo" onclick="navigate('home')">
            <img id="header-app-icon"
                src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg2v5v5v5v5v5v5/s1600/rrr-esports-logo.png"
                alt="Logo" onerror="this.style.display='none';">
            <span id="header-app-name" class="logo-text">FF ESPORTS LOBBY </span>
        </div>

        <div class="header-right">
            <button class="theme-btn" onclick="toggleUserTheme()" id="header-theme-btn" style="margin-right:10px;">
                <i class="fas fa-moon"></i>
            </button>
            <div id="auth-nav" class="auth-buttons" style="display: none;">
                <button class="btn-login-nav" onclick="showAuthPage('login')">Login</button>
                <button class="btn-reg-nav" onclick="showAuthPage('register')">Register</button>
            </div>

            <div id="user-nav" class="user-nav">
                <div class="balance-pill" onclick="navigate('profile')">
                    <i class="fas fa-wallet"></i> <span id="header-balance">0</span> ৳
                </div>
                <div class="icon-btn" onclick="toggleNotification()">
                    <i class="fas fa-bell"></i>
                    <div id="header-notif-badge" class="notif-badge">0</div>
                </div>
                <div class="icon-btn" onclick="toggleSidebar()" style="margin-left: 5px;">
                    <img id="header-avatar" src="https://cdn-icons-png.flaticon.com/512/149/149071.png"
                        style="width:30px; height:30px; border-radius:50%; object-fit:cover;">
                </div>
            </div>
        </div>
    </header>

    <div class="sidebar-overlay" onclick="closeAllSidebars()"></div>

    <div class="sidebar" id="sidebar">
        <div class="sidebar-close" onclick="toggleSidebar()">×</div>
        <div class="sidebar-header">
            <img src="https://cdn-icons-png.flaticon.com/512/149/149071.png" class="sidebar-avatar" id="sidebar-avatar">
            <div class="user-info">
                <h4 id="sidebar-name">Guest User</h4>
                <p id="sidebar-email">Please login</p>
            </div>
        </div>
        <ul class="sidebar-menu">
            <li onclick="navigate('home')"><i class="fas fa-home"></i> Home</li>
            <li onclick="navigate('profile')"><i class="fas fa-user"></i> My Account</li>
            <li onclick="navigate('add-money')"><i class="fas fa-plus-circle"></i> Add Money</li>
            <li onclick="navigate('withdraw')"><i class="fas fa-minus-circle"></i> Withdraw</li>
            <li onclick="navigate('match-history')"><i class="fas fa-gamepad"></i> Match History</li>
            <li onclick="navigate('history')"><i class="fas fa-history"></i> Transaction History</li>
            <li onclick="navigate('contact')"><i class="fas fa-headset"></i> Support</li>
            <li id="menu-logout" class="logout-item hidden" onclick="handleLogout()"
                style="color:red; border-top:1px solid #eee; margin-top:10px;"><i class="fas fa-sign-out-alt"></i>
                Logout</li>
        </ul>
        <div id="sidebar-auth-btn" style="padding:15px; display: none;">
            <button class="primary-btn" onclick="showAuthPage('login')">Login / Register</button>
        </div>
    </div>

    <div class="notif-sidebar" id="notif-sidebar">
        <div class="sidebar-close" onclick="toggleNotification()">×</div>
        <div class="sidebar-header" style="align-items: flex-start;">
            <h4 style="font-size: 18px; font-weight: 700;">Notifications</h4>
            <p style="font-size:12px; color:#666;">Recent updates</p>
        </div>
        <div id="notif-list-container" style="overflow-y:auto; flex:1;">
            <div style="padding:20px; text-align:center; color:#999;">No notifications</div>
        </div>
    </div>

    <div id="login-page" class="auth-page">
        <div class="auth-container">
            <div style="margin-bottom:20px;">
                <img id="login-app-icon"
                    src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg2v5v5v5v5v5v5/s1600/rrr-esports-logo.png"
                    style="height:60px;">
            </div>
            <h2 class="auth-title">Login</h2>
            <p class="auth-sub">Login to your account to continue</p>

            <div class="form-group">
                <label>Email Address</label>
                <input type="email" id="login-email" class="input-field" placeholder="Enter your email">
            </div>
            <div class="form-group">
                <label>Password</label>
                <input type="password" id="login-pass" class="input-field" placeholder="Enter password">
            </div>

            <button class="primary-btn" onclick="emailLogin()">Sign In</button>
            <div style="margin:15px 0; color:#888;">or</div>

            <button class="primary-btn google-btn" type="button" onclick="googleLogin()">
                <i class="fab fa-google" style="color:#DB4437; font-size: 18px;"></i> Sign in with Google
            </button>

            <p style="margin-top:20px; font-size:14px; color:#666;">
                Don't have an account? <span onclick="showAuthPage('register')"
                    style="color:var(--primary); font-weight:700; cursor:pointer;">Register Now</span>
            </p>
            <button class="btn-cancel" onclick="closeAuthPage()">Cancel</button>
        </div>
    </div>

    <div id="register-page" class="auth-page">
        <div class="auth-container">
            <div style="margin-bottom:20px;">
                <img id="reg-app-icon"
                    src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg2v5v5v5v5v5v5/s1600/rrr-esports-logo.png"
                    style="height:60px;">
            </div>
            <h2 class="auth-title">Sign Up</h2>
            <p class="auth-sub">Enter your information to create an account</p>

            <div class="form-group">
                <label>Full Name</label>
                <input type="text" id="reg-username" class="input-field" placeholder="Your Name">
            </div>
            <div class="form-group">
                <label>Phone Number</label>
                <input type="number" id="reg-phone" class="input-field" placeholder="017xxxxxxxx">
            </div>
            <div class="form-group">
                <label>Email Address</label>
                <input type="email" id="reg-email" class="input-field" placeholder="Your Email">
            </div>
            <div class="form-group">
                <label>Password</label>
                <input type="password" id="reg-pass" class="input-field" placeholder="Password">
            </div>

            <button class="primary-btn" onclick="emailRegister()">Sign Up</button>

            <div style="margin:15px 0; color:#888;">or</div>
            <button class="primary-btn google-btn" type="button" onclick="googleLogin()">
                <i class="fab fa-google" style="color:#DB4437; font-size: 18px;"></i> Sign up with Google
            </button>

            <p style="margin-top:20px; font-size:14px; color:#666;">
                Already have an account? <span onclick="showAuthPage('login')"
                    style="color:var(--primary); font-weight:700; cursor:pointer;">Login Now</span>
            </p>
            <button class="btn-cancel" onclick="closeAuthPage()">Cancel</button>
        </div>
    </div>

    <main id="main-content">

        <section id="home" class="app-section active">
            <div class="hero-banner">
                <div class="alert-box">
                    <marquee id="dynamic-notice">Welcome to RRR Esports! Play daily matches and earn rewards.</marquee>
                </div>
                <div class="slider-container">
                    <div id="banner-slider-wrapper" class="slider-wrapper">
                    </div>
                </div>
            </div>

            <div class="section-title">Select Game Category</div>

            <div id="dynamic-category-list" class="category-list">
                <div style="text-align:center; width:100%; padding:20px; color:#999;">Loading Categories...</div>
            </div>
        </section>

        <section id="matches-view" class="app-section">
            <div class="back-nav" onclick="navigate('home')">
                <i class="fas fa-arrow-left"></i> Back to Categories
            </div>

            <div class="how-to-join-btn">
                টুর্নামেন্ট খেলার জন্য কিভাবে যোগদান করবেন ?
            </div>

            <div class="tab-container">
                <div class="tab-btn active" id="tab-play" onclick="switchMatchTab('play')">Play</div>
                <div class="tab-btn" id="tab-result" onclick="switchMatchTab('result')">Result</div>
            </div>

            <div id="matches-container">
            </div>

            <!-- DYNAMIC RULES SECTION (Category specific) -->
            <div id="home-rules-section" style="margin-top:20px; display:none;">
                <div class="section-title" id="home-rules-title">নিয়ম ও শর্তাবলী</div>
                <div id="home-rules-container"></div>
            </div>

            <!-- DEFAULT/FALLBACK RULES BOX -->
            <div class="rules-box" id="default-rules-box">
                <h4 class="rules-title">Rules & Conditions</h4>
                <ul class="rules-list">
                    <li><i class="fas fa-fire"></i> সকল ধরনের গাড়ি ব্যবহার করে কিল করতে পারবেন ❤️</li>
                    <li><i class="fas fa-fire"></i> AWM and যেকোনো স্নাইপার ব্যবহার করা যাবে মাতৃ ❤️</li>
                    <li><i class="fas fa-skull"></i> গেম ওপেন করার পর থেকে Screen Recording চালু করতে হবে (আবশ্যক) Plane
                        এ ওঠার পর অফ করে দিবেন!</li>
                    <li><i class="fas fa-ban"></i> ৩০০ টাকার বেশি কেউ withdraw দিবেন না।</li>
                </ul>
            </div>
        </section>

        <section id="view-joined-members" class="app-section">
            <div class="back-nav" onclick="navigate('matches-view')">
                <i class="fas fa-arrow-left"></i> Back to Matches
            </div>
            <div class="card-panel">
                <h3 id="view-joined-title" style="font-size:18px; margin-bottom:5px;">Match Participants</h3>
                <p style="font-size:12px; color:#666; margin-bottom:20px;">List of slots and players who have successfully joined this match.</p>
                <div id="joined-members-list-container">
                </div>
            </div>
        </section>

        <section id="match-result" class="app-section">
            <div class="back-nav" onclick="navigate('matches-view')">
                <i class="fas fa-arrow-left"></i> Back to Matches
            </div>
            <div id="result-details-container">
            </div>
        </section>

        <section id="profile" class="app-section">
            <div class="card-panel" style="text-align:center;">
                <img id="profile-page-avatar" src="https://cdn-icons-png.flaticon.com/512/149/149071.png"
                    style="width:90px; border-radius:50%; margin-bottom:15px; border:3px solid var(--primary); padding:2px;">
                <h2 id="profile-page-name">User</h2>
                <p id="profile-page-email">Loading...</p>
                <p id="profile-page-phone" style="color:#777; font-size:14px; margin-top:5px; font-weight:600;">--</p>

                <div
                    style="display:flex; justify-content:space-between; margin-top:25px; border-top:1px solid #eee; padding-top:20px;">
                    <div style="text-align:center; flex:1; border-right:1px solid #eee;">
                        <span style="font-size:12px; color:#888; text-transform:uppercase;">Deposit Balance</span>
                        <h3 style="color:#333; font-size:24px;" id="profile-page-deposit">0 ৳</h3>
                    </div>
                    <div style="text-align:center; flex:1;">
                        <span style="font-size:12px; color:#888; text-transform:uppercase;">Winning Balance</span>
                        <h3 style="color:var(--primary); font-size:24px;" id="profile-page-winning">0 ৳</h3>
                    </div>
                </div>
            </div>

            <!-- PROFILE BUTTONS UPDATED -->
            <div class="category-grid" style="display:flex; flex-direction:column; gap:10px;">
                <button class="primary-btn" style="margin:0; background:#333;"
                    onclick="navigate('match-history')">My Matches</button>
                <button class="primary-btn" style="margin:0; background:#444;"
                    onclick="navigate('rules-view')">Game Rules</button>
                <button class="primary-btn" style="margin:0; background:#666;"
                    onclick="navigate('history')">Transaction History</button>
                <button class="primary-btn" style="margin:0;" onclick="navigate('add-money')">Add Money</button>
            </div>
        </section>
        
        <!-- NEW ALL GAME RULES SECTION -->
        <section id="rules-view" class="app-section">
            <div class="back-nav" onclick="navigate('profile')">
                <i class="fas fa-arrow-left"></i> Back to Profile
            </div>
            <div class="card-panel">
                <h3 style="margin-bottom:15px;">Game Rules</h3>
                <!-- TABS CONTAINER -->
                <div id="rules-category-tabs" style="display:flex; overflow-x:auto; gap:10px; margin-bottom:15px; padding-bottom:5px; scrollbar-width: none;"></div>
                
                <!-- CONTENT CONTAINER -->
                <div id="all-rules-container">
                    <div style="text-align:center; padding:30px; color:#999;"><i class="fas fa-spinner fa-spin"></i> Loading Rules...</div>
                </div>
            </div>
        </section>

        <!-- NEW MATCH HISTORY SECTION -->
        <section id="match-history" class="app-section">
            <div class="back-nav" onclick="navigate('profile')">
                <i class="fas fa-arrow-left"></i> Back to Profile
            </div>
            <div class="card-panel">
                <h3>My Match History</h3>
                <div id="match-history-list">
                    <div style="text-align:center; padding:30px; color:#999;">Loading matches...</div>
                </div>
            </div>
        </section>

        <section id="add-money" class="app-section">
            <!-- Wallet Tabs -->
            <div style="display:flex; gap:0; margin-bottom:15px; border-radius:10px; overflow:hidden; border:1px solid var(--border-color);">
                <button id="wallet-tab-deposit" onclick="switchWalletTab('deposit')" style="flex:1; padding:12px; font-size:14px; font-weight:700; border:none; cursor:pointer; background:var(--primary); color:white; transition:0.3s;">
                    <i class="fas fa-plus-circle"></i> Deposit
                </button>
                <button id="wallet-tab-withdraw" onclick="switchWalletTab('withdraw')" style="flex:1; padding:12px; font-size:14px; font-weight:700; border:none; cursor:pointer; background:var(--card-bg); color:var(--text-dark); transition:0.3s;">
                    <i class="fas fa-minus-circle"></i> Withdraw
                </button>
            </div>

            <!-- ===== DEPOSIT PANEL ===== -->
            <div id="wallet-deposit-panel">
            <div class="card-panel">
                <h3>Add Money to Wallet</h3>

                <!-- DEP STEP 1: Amount -->
                <div id="dep-step-1" class="step-container active-step">
                    <div class="form-group">
                        <label>Enter Amount (BDT)</label>
                        <input type="number" id="add-amount-input" class="input-field" placeholder="Minimum 20 BDT">
                    </div>
                    <button class="primary-btn" onclick="depGoToMethod()">NEXT <i class="fas fa-arrow-right"></i></button>
                </div>

                <!-- DEP STEP 2: Method Select -->
                <div id="dep-step-2" class="step-container">
                    <div class="back-nav" onclick="showDepStep(1)">
                        <i class="fas fa-arrow-left"></i> Change Amount
                    </div>
                    <p style="margin-bottom:15px; font-size:14px; color:#666;">You are adding: <strong id="dep-display-amount" style="color:var(--primary);">0 ৳</strong></p>
                    <label style="display:block; margin-bottom:12px; font-weight:600; font-size:14px;">Select Payment Method:</label>
                    <div class="method-btn" onclick="depSelectMethod('Bkash')">
                        <img src="https://freelogopng.com/images/all_img/1656234745bkash-app-logo-png.png" alt="Bkash" style="height:35px; object-fit:contain;">
                        <span style="font-weight:600;">Pay with Bkash</span>
                        <i class="fas fa-chevron-right" style="margin-left:auto; color:#ccc;"></i>
                    </div>
                    <div class="method-btn" onclick="depSelectMethod('Nagad')">
                        <img src="https://freepnglogo.com/images/all_img/1679248787Nagad-Logo.png" alt="Nagad" style="height:35px; object-fit:contain;">
                        <span style="font-weight:600;">Pay with Nagad</span>
                        <i class="fas fa-chevron-right" style="margin-left:auto; color:#ccc;"></i>
                    </div>
                </div>

                <!-- DEP STEP 3: Payment Details -->
                <div id="dep-step-3" class="step-container">
                    <div class="back-nav" onclick="showDepStep(2)">
                        <i class="fas fa-arrow-left"></i> Back
                    </div>
                    <!-- Colored Header -->
                    <div id="dep-method-header" style="border-radius:14px; padding:25px 20px; text-align:center; margin-bottom:18px; color:white;">
                        <img id="dep-method-logo" src="" style="height:55px; background:white; padding:6px; border-radius:50%; box-shadow:0 4px 10px rgba(0,0,0,0.2); margin-bottom:10px;">
                        <h2 style="font-size:28px; font-weight:800;">৳ <span id="dep-final-amount">0</span></h2>
                        <p style="font-size:13px; opacity:0.9;">Send Money to Personal</p>
                    </div>
                    <!-- Number Copy -->
                    <div class="form-group">
                        <label id="dep-num-label" style="font-weight:600; font-size:13px;">Copy Number:</label>
                        <div style="display:flex; gap:10px; margin-top:6px;">
                            <input type="text" id="dep-display-num" readonly class="input-field" style="font-weight:bold;">
                            <button id="dep-copy-btn" class="primary-btn" style="width:auto; margin:0; padding:0 18px; font-size:13px;" onclick="copyToClipboard(document.getElementById('dep-display-num').value)">
                                <i class="fas fa-copy"></i>
                            </button>
                        </div>
                    </div>
                    <!-- Pink Instruction Box -->
                    <div id="dep-instruction-box" style="border-radius:14px; padding:18px; margin:16px 0; color:white; font-size:13px; line-height:2; font-family:'Hind Siliguri',sans-serif;">
                        <ul style="list-style:none; padding:0;">
                            <li>● *247# ডায়াল করে আপনার <span id="dep-method-name" style="font-weight:700;"></span> মোবাইল মেনুতে যান অথবা App এ যান।</li>
                            <li style="color:#FFD700; font-weight:600;">● Send Money/Make Payment - এ ক্লিক করুন।</li>
                            <li>● প্রাপক নম্বর হিসেবে উপরের নম্বরটি লিখুন।</li>
                            <li>● নিশ্চিত করতে আপনার মোবাইল মেনু পিন লিখুন।</li>
                            <li>● এখন নিচে আপনার TrxID এবং Amount দিন আর VERIFY করুন।</li>
                        </ul>
                    </div>
                    <!-- TrxID input -->
                    <div class="form-group">
                        <label>Transaction ID (TrxID)</label>
                        <input type="text" id="dep-trxid" class="input-field" placeholder="TrxID দিন...">
                    </div>
                    
                    <button id="dep-verify-btn" class="primary-btn" onclick="depVerifyPayment()" style="font-size:15px; font-weight:800; letter-spacing:1px;">Verify SMS</button>
                </div>
            </div>
            </div>

            <!-- ===== WITHDRAW PANEL ===== -->
            <div id="wallet-withdraw-panel" style="display:none;">
            <div class="card-panel">
                <h3>Withdraw Winning Funds</h3>
                <div style="background:#f0fff4; padding:12px; border:1px solid #c6f6d5; border-radius:8px; margin-bottom:18px; text-align:center;">
                    <span style="font-size:12px; color:#2f855a;">Available Winning Balance</span>
                    <h2 style="color:#2f855a;" id="withdraw-available-display">0 ৳</h2>
                </div>

                <!-- WD STEP 1: Amount -->
                <div id="wd-step-1" class="step-container active-step">
                    <p style="font-size:12px; color:#e53e3e; margin-bottom:12px;">* Only winning balance can be withdrawn.</p>
                    <div class="form-group">
                        <label>Enter Amount (BDT)</label>
                        <input type="number" id="withdraw-amount" class="input-field" placeholder="Minimum 100 BDT">
                    </div>
                    <button class="primary-btn" onclick="wdGoToMethod()">NEXT <i class="fas fa-arrow-right"></i></button>
                </div>

                <!-- WD STEP 2: Method Select -->
                <div id="wd-step-2" class="step-container">
                    <div class="back-nav" onclick="showWdStep(1)">
                        <i class="fas fa-arrow-left"></i> Change Amount
                    </div>
                    <p style="margin-bottom:15px; font-size:14px; color:#666;">Withdrawing: <strong id="wd-display-amount" style="color:#2f855a;">0 ৳</strong></p>
                    <label style="display:block; margin-bottom:12px; font-weight:600; font-size:14px;">Select Method:</label>
                    <div class="method-btn" onclick="wdSelectMethod('Bkash')">
                        <img src="https://freelogopng.com/images/all_img/1656234745bkash-app-logo-png.png" alt="Bkash" style="height:35px; object-fit:contain;">
                        <span style="font-weight:600;">Withdraw via Bkash</span>
                        <i class="fas fa-chevron-right" style="margin-left:auto; color:#ccc;"></i>
                    </div>
                    <div class="method-btn" onclick="wdSelectMethod('Nagad')">
                        <img src="https://freepnglogo.com/images/all_img/1679248787Nagad-Logo.png" alt="Nagad" style="height:35px; object-fit:contain;">
                        <span style="font-weight:600;">Withdraw via Nagad</span>
                        <i class="fas fa-chevron-right" style="margin-left:auto; color:#ccc;"></i>
                    </div>
                </div>

                <!-- WD STEP 3: Account Number -->
                <div id="wd-step-3" class="step-container">
                    <div class="back-nav" onclick="showWdStep(2)">
                        <i class="fas fa-arrow-left"></i> Back
                    </div>
                    <div id="wd-method-header" style="border-radius:14px; padding:18px; text-align:center; margin-bottom:18px; color:white;">
                        <img id="wd-method-logo" src="" style="height:45px; background:white; padding:5px; border-radius:50%; margin-bottom:8px;">
                        <div style="font-size:16px; font-weight:700;" id="wd-method-title">Bkash Withdraw</div>
                        <div style="font-size:13px; opacity:0.9;">Amount: <strong id="wd-confirm-amount">0</strong> ৳</div>
                    </div>
                    <div class="form-group">
                        <label id="wd-num-label">Bkash Account Number</label>
                        <input type="text" id="withdraw-number" class="input-field" placeholder="017xxxxxxxx">
                    </div>
                    <button class="primary-btn" onclick="submitWithdraw()" id="wd-submit-btn">Submit Request</button>
                </div>
            </div>
            </div>
        </section>

        <section id="withdraw" class="app-section" style="display:none!important;"></section>

        <section id="history" class="app-section">
            <div class="card-panel">
                <h3>Transaction History</h3>
                <div id="history-list">
                    <div style="text-align:center; padding:30px; color:#999;">Loading...</div>
                </div>
            </div>
        </section>

        <section id="contact" class="app-section">
            <div class="card-panel">
                <h3>Contact Support</h3>
                <div id="support-cards-container">
                    <div onclick="openSupport()"
                        style="background:#f4faff; border:1px solid #ddecff; padding:15px; border-radius:10px; margin-bottom:10px; display:flex; align-items:center; gap:15px; cursor:pointer;">
                        <i class="fab fa-telegram" style="color:#0088cc; font-size:32px;"></i>
                        <div>
                            <strong style="color:#0088cc;">Telegram Support</strong>
                            <p style="font-size:12px; color:#666;">Get instant help 24/7 regarding payment or match issues.
                            </p>
                        </div>
                        <i class="fas fa-chevron-right" style="margin-left:auto; color:#ccc;"></i>
                    </div>
                </div>
            </div>
        </section>

    </main>

    <!-- PRIZE LIST MODAL -->
    <div id="prize-modal" class="modal">
        <div class="modal-box" style="text-align:left;">
            <h3 id="prize-modal-title" style="font-size:16px; font-weight:700; text-align:center; margin-bottom:5px;"></h3>
            <p style="text-align:center; font-size:12px; color:#999; margin-bottom:15px;">পুরস্কার তালিকা</p>
            <div id="prize-modal-body"></div>
            <button class="btn-cancel" onclick="closePrizeModal()" style="margin-top:15px;">বন্ধ করুন</button>
        </div>
    </div>

    <!-- JOIN MODAL WITH SLOT SYSTEM -->
    <div id="join-modal" class="modal">
        <div class="modal-box" style="text-align:left;">
            <div style="text-align:center; margin-bottom:15px;">
                <h3 id="join-modal-title" style="font-size:16px; font-weight:700;">MATCH TITLE</h3>
                <p style="font-size:12px; color:#666;">Available Balance: <span id="join-modal-balance"
                        style="font-weight:700; color:var(--primary);">0</span> ৳</p>
                <p style="font-size:12px; color:#666;">Match Entry Fee: <span id="join-modal-fee"
                        style="font-weight:700;">0</span> ৳</p>
            </div>

            <div id="slot-selection-container">
                <!-- Slots will be injected here dynamically -->
            </div>

            <div id="join-inputs-container" style="display:none;">
                <!-- Inputs will be injected here -->
            </div>

            <button class="primary-btn" id="confirm-join-btn" onclick="confirmJoin()" style="margin-top:20px; display:none;">Join Match</button>
            <button class="btn-cancel" onclick="closeJoinModal()">Cancel</button>
        </div>
    </div>

    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/10.12.0/firebase-app.js";
        import { getDatabase, ref, set, onValue, push, update, get, query, orderByChild, equalTo, serverTimestamp } from "https://www.gstatic.com/firebasejs/10.12.0/firebase-database.js";
        import { getAuth, GoogleAuthProvider, signInWithPopup, signInWithEmailAndPassword, createUserWithEmailAndPassword, signOut, onAuthStateChanged, updateProfile } from "https://www.gstatic.com/firebasejs/10.12.0/firebase-auth.js";

        // CONFIG
       const firebaseConfig = {
  apiKey: "AIzaSyBcJfJLVsu0u3TTIQtVgAiB3sT36_6pqD8",
  authDomain: "ff-esports--lobby.firebaseapp.com",
  projectId: "ff-esports--lobby",
  storageBucket: "ff-esports--lobby.firebasestorage.app",
  messagingSenderId: "67236288952",
  appId: "1:67236288952:web:c25a8401a7560036dbd74d",
  measurementId: "G-QS3HRZSM9X"
};

        const app = initializeApp(firebaseConfig);
        const db = getDatabase(app);

        // --- GLOBAL DATA HOLDERS ---
        const auth = getAuth(app);
        const provider = new GoogleAuthProvider();
        let currentUser = null;

        let depositBal = 0;
        let winningBal = 0;
        let currentJoinMatchId = null; 
        let currentJoinFee = 0;
        let currentJoinPlayersPerSlot = 1;
        let currentJoinTotalSlots = 48;
        let currentActiveCategory = null;
        let currentSupportLink = "https://t.me/rrresports";
        window.selectedSlot = null;

        let rawMatches = [];
        let activeCategories = {};
        let timerInterval = null;
        let appSettings = {}; 

        // Helper function for XSS Protection
        const escapeHTML = (str) => {
            return String(str).replace(/[&<>'"]/g, 
                tag => ({
                    '&': '&amp;',
                    '<': '&lt;',
                    '>': '&gt;',
                    "'": '&#39;',
                    '"': '&quot;'
                }[tag] || tag)
            );
        };

        // --- THEME LOGIC ---
        window.toggleUserTheme = () => {
            document.body.classList.toggle('dark-theme');
            const isDark = document.body.classList.contains('dark-theme');
            localStorage.setItem('userTheme', isDark ? 'dark' : 'light');
            updateUserThemeIcon(isDark);
        }

        function updateUserThemeIcon(isDark) {
            const btn = document.getElementById('header-theme-btn');
            if (btn) btn.innerHTML = isDark ? '<i class="fas fa-sun"></i>' : '<i class="fas fa-moon"></i>';
        }

        const savedUserTheme = localStorage.getItem('userTheme');
        if (savedUserTheme === 'dark') {
            document.body.classList.add('dark-theme');
            updateUserThemeIcon(true);
        } else {
            updateUserThemeIcon(false);
        }

        /* --- INITIALIZATION --- */
        window.onload = function () {
            initAppSettings();
            initCategories();
            initMatchesListener();
            initNotifications();
            initBanners();
            loadSupportCards();
        }

        function initAppSettings() {
            const settingsRef = ref(db, 'app_settings');
            onValue(settingsRef, (snap) => {
                const data = snap.val();
                if (data) {
                    appSettings = data;
                    if (data.support_link) currentSupportLink = data.support_link;
                    if (data.min_deposit) document.getElementById('add-amount-input').placeholder = `Minimum ${data.min_deposit} BDT`;
                    if (data.notice) document.getElementById('dynamic-notice').innerText = data.notice;
                    if (data.bkash_number) appSettings.bkash_number = data.bkash_number;
                    if (data.nagad_number) appSettings.nagad_number = data.nagad_number;
                    if (data.app_name) document.getElementById('header-app-name').innerText = data.app_name;
                    if (data.app_icon) {
                        const icons = [document.getElementById('header-app-icon'), document.getElementById('login-app-icon'), document.getElementById('reg-app-icon')];
                        icons.forEach(i => i.src = data.app_icon);
                        document.getElementById('header-app-icon').style.display = 'block';
                    }
                }
            });
        }

        window.openSupport = () => window.open(currentSupportLink, '_blank');

        function initBanners() {
            const bannerRef = ref(db, 'banners');
            const wrapper = document.getElementById('banner-slider-wrapper');
            let bannerLoaded = false;
            const bannerTimeout = setTimeout(() => {
                if (!bannerLoaded) {
                    wrapper.innerHTML = `<div class="slide"><img src="https://placehold.co/600x200/FF5500/white?text=RRR+Esports"></div>`;
                }
            }, 6000);

            onValue(bannerRef, (snap) => {
                bannerLoaded = true;
                clearTimeout(bannerTimeout);
                wrapper.innerHTML = "";
                const data = snap.val();
                if (data) {
                    const slides = Object.values(data);
                    if (slides.length > 0) {
                        slides.forEach(slide => {
                            const div = document.createElement('div');
                            div.className = 'slide';
                            div.onclick = () => window.open(slide.link, '_blank');
                            
                            // Fix: Matching admin panel's key "url"
                            let imageUrl = slide.url || slide.img || "";
                            
                            div.innerHTML = `
                                <img src="${imageUrl}" onerror="this.src='https://placehold.co/600x200/FF5500/white?text=Image+Error'">
                                ${slide.title ? `<div class="slide-caption">${escapeHTML(slide.title)}</div>` : ''}
                            `;
                            wrapper.appendChild(div);
                        });
                        startSlider(slides.length);
                    } else {
                        wrapper.innerHTML = `<div class="slide"><img src="https://placehold.co/600x200/FF5500/white?text=RRR+Esports"></div>`;
                    }
                } else {
                    wrapper.innerHTML = `<div class="slide"><img src="https://placehold.co/600x200/FF5500/white?text=RRR+Esports"></div>`;
                }
            });
        }

        let sliderInterval;

        function loadSupportCards() {
            const container = document.getElementById('support-cards-container');
            if (!container) return;
            onValue(ref(db, 'support_cards'), (snap) => {
                const data = snap.val();
                if (data && Object.keys(data).length > 0) {
                    container.innerHTML = "";
                    Object.values(data).forEach(card => {
                        const iconHtml = (card.icon === 'custom' && card.img)
                            ? `<img src="${card.img}" style="width:32px; height:32px; object-fit:contain;">`
                            : `<i class="${card.icon || 'fas fa-headset'}" style="color:${card.color || '#0088cc'}; font-size:32px;"></i>`;
                        const div = document.createElement('div');
                        div.style = "background:#f4faff; border:1px solid #ddecff; padding:15px; border-radius:10px; margin-bottom:10px; display:flex; align-items:center; gap:15px; cursor:pointer;";
                        div.onclick = () => window.open(card.link, '_blank');
                        div.innerHTML = `
                            ${iconHtml}
                            <div>
                                <strong style="color:${card.color || '#0088cc'};">${escapeHTML(card.title || 'Support')}</strong>
                                <p style="font-size:12px; color:#666;">${escapeHTML(card.desc || '')}</p>
                            </div>
                            <i class="fas fa-chevron-right" style="margin-left:auto; color:#ccc;"></i>
                        `;
                        container.appendChild(div);
                    });
                }
            });
        }

        function startSlider(count) {
            if (sliderInterval) clearInterval(sliderInterval);
            let index = 0;
            const wrapper = document.getElementById('banner-slider-wrapper');
            sliderInterval = setInterval(() => {
                index++;
                if (index >= count) index = 0;
                wrapper.style.transform = `translateX(-${index * 100}%)`;
            }, 3000); 
        }

        function initCategories() {
            const catRef = ref(db, 'categories');
            const list = document.getElementById('dynamic-category-list');
            let dataLoaded = false;
            const loadTimeout = setTimeout(() => {
                if (!dataLoaded) {
                    list.innerHTML = `<div style='padding:20px; text-align:center; color:#999;'><i class='fas fa-wifi' style='font-size:30px; margin-bottom:10px; display:block; color:#ccc;'></i>সংযোগ সমস্যা! পেজ Reload করুন।</div>`;
                }
            }, 6000);

            onValue(catRef, (snap) => {
                dataLoaded = true;
                clearTimeout(loadTimeout);
                list.innerHTML = "";
                const data = snap.val();
                if (data) {
                    activeCategories = data;
                    Object.entries(data).forEach(([key, val]) => {
                        const html = `
                        <div class="game-card" onclick="openCategory('${key}')">
                            <div class="game-card-bg" style="background-image: url('${val.img}');"></div>
                            <div class="game-card-content">
                                <img src="${val.img}" class="game-avatar">
                                <div class="game-info">
                                    <div class="game-title">${escapeHTML(val.name)}</div>
                                    <div class="match-count" id="count-${key}">Loading...</div>
                                </div>
                            </div>
                        </div>`;
                        list.innerHTML += html;
                    });
                    updateMatchCounts();
                } else {
                    list.innerHTML = "<div style='padding:20px; text-align:center; color:#999;'>কোনো Category পাওয়া যায়নি।</div>";
                }
            });
        }

        function initMatchesListener() {
            const matchesRef = ref(db, 'matches');
            onValue(matchesRef, (snap) => {
                rawMatches = [];
                const data = snap.val();
                if (data) {
                    Object.entries(data).forEach(([key, val]) => {
                        rawMatches.push({ dbKey: key, ...val });
                    });
                }
                updateMatchCounts();
                if (document.getElementById('matches-view').classList.contains('active')) {
                    const activeTab = document.querySelector('.tab-btn.active');
                    if (activeTab) switchMatchTab(activeTab.id.replace('tab-', ''));
                }
            });
        }

        function updateMatchCounts() {
            Object.keys(activeCategories).forEach(catKey => {
                const count = rawMatches.filter(m => m.categoryId === catKey && m.status !== 'Finished' && (parseInt(m.total || 0) > parseInt(m.joined || 0))).length;
                const el = document.getElementById(`count-${catKey}`);
                if (el) el.innerText = `${count} Matches Available`;
            });
        }

        function loadHomeRules(catId) {
            const rulesRef = ref(db, 'rules/' + catId);
            const section = document.getElementById('home-rules-section');
            const container = document.getElementById('home-rules-container');
            const titleEl = document.getElementById('home-rules-title');
            const defaultBox = document.getElementById('default-rules-box');

            onValue(rulesRef, (snap) => {
                const data = snap.val();
                if (data && data.rules && data.rules.length > 0) {
                    section.style.display = 'block';
                    if (defaultBox) defaultBox.style.display = 'none';
                    titleEl.innerText = (data.title || 'নিয়ম ও শর্তাবলী');
                    let html = '<div class="rules-box"><ul class="rules-list">';
                    data.rules.forEach(rule => {
                        html += '<li><i class="fas fa-fire"></i> ' + escapeHTML(rule) + '</li>';
                    });
                    html += '</ul></div>';
                    container.innerHTML = html;
                } else {
                    section.style.display = 'none';
                    container.innerHTML = '';
                    if (defaultBox) defaultBox.style.display = 'block';
                }
            });
        }

        function initNotifications() {
            const notifRef = ref(db, 'notifications');
            const container = document.getElementById('notif-list-container');
            const badge = document.getElementById('header-notif-badge');

            onValue(notifRef, (snap) => {
                container.innerHTML = "";
                const data = snap.val();
                if (data) {
                    const keys = Object.keys(data).reverse();
                    badge.style.display = 'flex';
                    badge.innerText = keys.length;
                    keys.forEach(key => {
                        const n = data[key];
                        container.innerHTML += `
                        <div class="notif-item">
                            <div class="notif-icon"><i class="fas fa-bell"></i></div>
                            <div class="notif-content">
                                <h5>${escapeHTML(n.title)}</h5>
                                <p>${escapeHTML(n.body)}</p>
                                <span style="font-size:9px; color:#999;">${escapeHTML(n.date)}</span>
                            </div>
                        </div>`;
                    });
                } else {
                    badge.style.display = 'none';
                    container.innerHTML = '<div style="padding:20px; text-align:center; color:#999;">No notifications</div>';
                }
            });
        }

        /* --- AUTH LOGIC --- */
        window.isAppActiveAuth = false;

        function startAuthSession() {
            window.isAppActiveAuth = true;
            // 5 second fallback to clear the flag in case something fails silently
            setTimeout(() => { window.isAppActiveAuth = false; }, 5000);
        }

        window.googleLogin = () => {
            startAuthSession();
            signInWithPopup(auth, provider).then((result) => {
                closeAuthPage();
                saveUserToDB(result.user, result.user.displayName, null);
            }).catch((error) => {
                window.isAppActiveAuth = false;
                alert("Google Sign-In Error: " + error.message);
            });
        };

        window.emailLogin = () => {
            const email = document.getElementById('login-email').value;
            const pass = document.getElementById('login-pass').value;
            if (!email || !pass) return alert("Please fill all fields");
            
            startAuthSession();
            signInWithEmailAndPassword(auth, email, pass).then(() => {
                closeAuthPage();
            }).catch(e => {
                window.isAppActiveAuth = false;
                alert(e.message);
            });
        };

        window.emailRegister = async () => {
            const name = document.getElementById('reg-username').value.trim();
            const phone = document.getElementById('reg-phone').value.trim();
            const email = document.getElementById('reg-email').value.trim();
            const pass = document.getElementById('reg-pass').value;
            if (!name || !phone || !email || !pass) return alert("Please fill all fields");

            startAuthSession();
            try {
                const userCredential = await createUserWithEmailAndPassword(auth, email, pass);
                const user = userCredential.user;
                await updateProfile(user, { displayName: name });
                await saveUserToDB(user, name, phone);
                closeAuthPage();
            } catch(e) {
                window.isAppActiveAuth = false;
                alert(e.message);
            }
        };

        async function saveUserToDB(user, name, phone) {
            const userRef = ref(db, 'users/' + user.uid);
            const snapshot = await get(userRef);
            if (!snapshot.exists()) {
                await set(userRef, {
                    username: name || "User",
                    email: user.email,
                    phone: phone || "N/A",
                    deposit: 0,
                    winning: 0,
                    joined: new Date().toLocaleDateString()
                });
            }
        }

        onAuthStateChanged(auth, (user) => {
            if (user) {
                updateUIForLogin(user);
            } else {
                currentUser = null;
                depositBal = 0;
                winningBal = 0;
                updateUIForLogout();
            }
        });

        window.handleLogout = () => {
            signOut(auth).then(() => {
                toggleSidebar();
                navigate('home');
            });
        };

        function updateUIForLogin(user) {
            document.getElementById('auth-nav').style.display = 'none';
            document.getElementById('user-nav').style.display = 'flex';
            document.getElementById('sidebar-auth-btn').style.display = 'none';
            document.getElementById('menu-logout').classList.remove('hidden');

            document.getElementById('sidebar-name').innerText = user.displayName || "User";
            document.getElementById('sidebar-email').innerText = user.email || "";
            document.getElementById('profile-page-name').innerText = user.displayName || "User";
            document.getElementById('profile-page-email').innerText = user.email || "";

            if (user.photoURL) {
                document.getElementById('sidebar-avatar').src = user.photoURL;
                document.getElementById('header-avatar').src = user.photoURL;
                document.getElementById('profile-page-avatar').src = user.photoURL;
            }

            const userRef = ref(db, 'users/' + user.uid);
            onValue(userRef, (snapshot) => {
                const data = snapshot.val();
                
                if (!data) {
                    // THE PERMANENT FIX FOR ADMIN / GHOST IDS
                    // If there is no user data, and they didn't just explicitly press login/register: Kick them out!
                    if (!window.isAppActiveAuth) {
                        signOut(auth).then(() => {
                            navigate('home');
                            updateUIForLogout();
                        });
                    }
                    return;
                }

                // Normal user loaded properly, clear flag
                window.isAppActiveAuth = false;

                if (data.role === 'admin' || data.role === 'Admin' || data.isAdmin) {
                    alert("Admin accounts are not allowed to access the User Site.");
                    signOut(auth).then(() => {
                        navigate('home');
                        updateUIForLogout();
                    });
                    return;
                }

                if (data.banned) {
                    alert("Your account has been banned by Admin.");
                    signOut(auth).then(() => {
                        navigate('home');
                        updateUIForLogout();
                    });
                    return;
                }
                
                currentUser = user;
                depositBal = parseFloat(data.deposit) || 0;
                winningBal = parseFloat(data.winning) || 0;
                const totalBal = depositBal + winningBal;

                document.getElementById('header-balance').innerText = totalBal;
                document.getElementById('profile-page-deposit').innerText = depositBal + " ৳";
                document.getElementById('profile-page-winning').innerText = winningBal + " ৳";
                document.getElementById('withdraw-available-display').innerText = winningBal + " ৳";
                document.getElementById('profile-page-phone').innerText = data.phone || "N/A";
                document.getElementById('profile-page-name').innerText = data.username || user.displayName || "User";
                document.getElementById('profile-page-email').innerText = data.email || user.email;
                
                loadHistory(); // Load their transactions
            });
        }

        function updateUIForLogout() {
            document.getElementById('auth-nav').style.display = 'flex';
            document.getElementById('user-nav').style.display = 'none';
            document.getElementById('sidebar-auth-btn').style.display = 'block';
            document.getElementById('menu-logout').classList.add('hidden');
            
            document.getElementById('sidebar-name').innerText = "Guest User";
            document.getElementById('sidebar-email').innerText = "Please login";
            document.getElementById('sidebar-avatar').src = "https://cdn-icons-png.flaticon.com/512/149/149071.png";
            
            document.getElementById('profile-page-name').innerText = "User";
            document.getElementById('profile-page-email').innerText = "Not logged in";
            document.getElementById('profile-page-phone').innerText = "--";
            document.getElementById('profile-page-deposit').innerText = "0 ৳";
            document.getElementById('profile-page-winning').innerText = "0 ৳";
            document.getElementById('profile-page-avatar').src = "https://cdn-icons-png.flaticon.com/512/149/149071.png";
            document.getElementById('header-avatar').src = "https://cdn-icons-png.flaticon.com/512/149/149071.png";
        }

        /* --- VIEW LOGIC & TIMER --- */
        window.openCategory = (catId) => {
            currentActiveCategory = catId;
            switchMatchTab('play');
            loadHomeRules(catId);
            navigate('matches-view');
        };

        window.switchMatchTab = (tab) => {
            document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
            document.getElementById(`tab-${tab}`).classList.add('active');

            const container = document.getElementById('matches-container');
            container.innerHTML = "";

            if (timerInterval) clearInterval(timerInterval);

            let dataToRender = [];
            if (tab === 'play') {
                dataToRender = rawMatches.filter(m => m.categoryId === currentActiveCategory && m.status !== 'Finished');
            } else {
                dataToRender = rawMatches.filter(m => m.categoryId === currentActiveCategory && m.status === 'Finished');
            }

            if (dataToRender.length === 0) {
                container.innerHTML = "<div style='text-align:center; padding:30px; color:#666;'>No matches found in this category.</div>";
                return;
            }

            dataToRender.forEach(m => {
                const joinedPlayers = parseInt(m.joined || 0);
                const totalPlayers = parseInt(m.total || 48);
                const progressPercent = (joinedPlayers / totalPlayers) * 100;
                const isFull = joinedPlayers >= totalPlayers;
                const categoryImg = activeCategories[currentActiveCategory]?.img || "https://placehold.co/50";

                let actionArea = '';

                if (tab === 'result') {
                    actionArea = `<div style="text-align:center; margin-top:10px;">
                        <button class="btn-view-result" onclick="openMatchResult('${m.dbKey}')">View Result</button>
                    </div>`;
                } else {
                    if (isFull) {
                        actionArea = `
                        <div style="display:flex; justify-content:space-between; margin-top:10px;">
                            <button class="btn-view-participants" onclick="openJoinedView('${m.dbKey}')">View Joined</button>
                            <button class="btn-full-outline" style="width:48%;">Full</button>
                        </div>`;
                    } else {
                        actionArea = `
                        <div style="display:flex; justify-content:space-between; margin-top:10px;">
                            <button class="btn-view-participants" onclick="openJoinedView('${m.dbKey}')">View Joined</button>
                            <button class="btn-join-outline" onclick="openJoinModal('${m.dbKey}')">Join</button>
                        </div>`;
                    }
                }

                const html = `
                <div class="match-card">
                    <div class="m-header">
                        <img src="${categoryImg}" class="m-img" alt="Game">
                        <div class="m-title-box">
                            <h3 class="m-title">${escapeHTML(m.title)}</h3>
                            <div class="m-time">${escapeHTML(m.time)}</div>
                        </div>
                    </div>

                    <div class="m-stats-grid">
                        <div class="m-stat-box">
                            <span class="stat-label">TOTAL PRIZE</span>
                            <span class="stat-value">৳ ${m.total_prize}</span>
                        </div>
                        <div class="m-stat-box">
                            <span class="stat-label">PER KILL</span>
                            <span class="stat-value">৳ ${m.per_kill}</span>
                        </div>
                        <div class="m-stat-box">
                            <span class="stat-label">ENTRY FEE</span>
                            <span class="stat-value">৳ ${m.entry}</span>
                        </div>
                        
                        <div class="m-stat-box">
                            <span class="stat-label">TYPE</span>
                            <span class="stat-value">${escapeHTML(m.type || 'Solo')}</span>
                        </div>
                        <div class="m-stat-box">
                            <span class="stat-label">GAME MODE</span>
                            <span class="stat-value">${escapeHTML(m.gameModeName || 'Classic')}</span>
                        </div>
                        <div class="m-stat-box">
                            <span class="stat-label">MAP</span>
                            <span class="stat-value">${escapeHTML(m.map)}</span>
                        </div>
                    </div>

                    <div class="progress-bar">
                        <div class="progress-fill" style="width: ${progressPercent}%;"></div>
                    </div>

                    <div class="m-status-row">
                        <span>${joinedPlayers} Joined</span>
                        <span>${Math.max(0, totalPlayers - joinedPlayers)} Available</span>
                    </div>

                    ${actionArea}

                    <div class="m-btn-row" style="margin-top:15px;">
                        <button class="btn-prize" onclick="openPrizeModal('${m.dbKey}', '${escapeHTML(m.title.replace(/'/g, "\\'"))}')">Prize List</button>
                        <button class="btn-room" onclick="checkRoomDetails('${m.room_id}', '${m.room_pass}')">ROOM ID</button>
                    </div>

                    <div class="timer-display match-countdown" data-time="${m.timestamp}">
                        Loading Timer...
                    </div>
                </div>`;
                container.innerHTML += html;
            });

            if (tab === 'play') startTimers();
        };

        window.checkRoomDetails = (id, pass) => {
            if (!id || id === 'undefined' || id.length < 3) {
                alert("Room details not available yet. Please wait for the match start time.");
            } else {
                alert(`ROOM ID: ${id}\nPASSWORD: ${pass}`);
            }
        };

        function startTimers() {
            function update() {
                const timers = document.querySelectorAll('.match-countdown');
                const now = new Date().getTime();

                timers.forEach(timer => {
                    const target = parseInt(timer.getAttribute('data-time'));
                    if(isNaN(target)) {
                        timer.innerText = "Time TBD";
                        return;
                    }
                    const distance = target - now;

                    if (distance < 0) {
                        timer.innerText = "MATCH STARTED / ENDED";
                        timer.style.color = "red";
                    } else {
                        const days = Math.floor(distance / (1000 * 60 * 60 * 24));
                        const hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
                        const minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
                        const seconds = Math.floor((distance % (1000 * 60)) / 1000);

                        timer.innerHTML = `
                            ${days} <span style="font-size:10px;">Days</span> : 
                            ${hours} <span style="font-size:10px;">Hours</span> : 
                            ${minutes} <span style="font-size:10px;">Min</span> : 
                            ${seconds} <span style="font-size:10px;">Sec</span>
                        `;
                    }
                });
            }
            update();
            timerInterval = setInterval(update, 1000);
        }

        /* --- NEW SLOT SYSTEM: OPEN JOIN MODAL --- */
        window.openJoinModal = async (dbKey) => {
            if (!currentUser) {
                showAuthPage('login');
                return;
            }
            
            const match = rawMatches.find(m => m.dbKey === dbKey);
            if (!match) return alert("Match not found");
            
            let type = match.type || 'Solo';
            let playersPerSlot = 1;
            let typeLow = type.toLowerCase();
            if (typeLow.includes('duo')) playersPerSlot = 2;
            if (typeLow.includes('squad')) playersPerSlot = 4;
            
            let totalPlayers = parseInt(match.total) || 48;
            let totalSlotsNum = Math.floor(totalPlayers / playersPerSlot);
            
            currentJoinMatchId = match.dbKey;
            currentJoinFee = parseInt(match.entry) || 0;
            currentJoinPlayersPerSlot = playersPerSlot;
            currentJoinTotalSlots = totalSlotsNum;
            window.selectedSlot = null;
            
            const totalBal = depositBal + winningBal;
            
            document.getElementById('join-modal-title').innerText = match.title;
            document.getElementById('join-modal-balance').innerText = totalBal;
            document.getElementById('join-modal-fee').innerText = currentJoinFee;
            
            document.getElementById('slot-selection-container').innerHTML = "<div style='text-align:center; padding:20px;'><i class='fas fa-spinner fa-spin'></i> Loading Slots...</div>";
            document.getElementById('slot-selection-container').style.display = 'block';
            document.getElementById('join-inputs-container').style.display = 'none';
            document.getElementById('join-inputs-container').innerHTML = '';
            
            const confirmBtn = document.getElementById('confirm-join-btn');
            confirmBtn.style.display = 'none';
            confirmBtn.dataset.matchKey = dbKey;
            confirmBtn.disabled = false;
            confirmBtn.innerText = "Join Match";
            
            document.getElementById('join-modal').classList.add('active');
            
            try {
                const participantsRef = ref(db, 'match_participants/' + match.dbKey);
                const snap = await get(participantsRef);
                let takenSlots = {};
                let userAlreadyJoined = false;
                
                if (snap.exists()) {
                    const data = snap.val();
                    Object.keys(data).forEach(key => {
                        let slotData = null;
                        if (data[key].slot) {
                            slotData = data[key];
                            takenSlots[data[key].slot] = data[key];
                        } else if (!isNaN(Number(key)) && Number(key) > 0) {
                            slotData = data[key];
                            takenSlots[key] = data[key];
                        }
                        if (slotData && slotData.joinedBy === currentUser.uid) {
                            userAlreadyJoined = true;
                        }
                    });
                }

                if (userAlreadyJoined) {
                    document.getElementById('join-modal').classList.remove('active');
                    return alert("আপনি ইতিমধ্যে এই ম্যাচে একটি স্লট নিয়েছেন! একটি ম্যাচে কেবল একটি স্লট নেওয়া যাবে। তবে অন্য যেকোনো ম্যাচে আপনি জয়েন করতে পারবেন।");
                }
                
                let gridHtml = '<h5 style="font-size:13px; font-weight:700; margin-bottom:10px; color:#333;">Select Your Slot</h5>';
                gridHtml += '<div class="slot-grid" id="join-slot-grid">';
                for (let i = 1; i <= totalSlotsNum; i++) {
                    let isTaken = !!takenSlots[i];
                    let extraClass = isTaken ? 'taken' : '';
                    let content = `Slot ${i}`;
                    
                    if (isTaken) {
                        let names = '';
                        if (takenSlots[i].players) {
                            names = takenSlots[i].players.map(p => escapeHTML(p.ign)).join(', ');
                        } else if (takenSlots[i].ign) {
                             names = escapeHTML(takenSlots[i].ign); 
                        }
                        if (names.length > 18) names = names.substring(0, 16) + '..';
                        content += `<div class="slot-players">${names}</div>`;
                        gridHtml += `<div class="slot-box ${extraClass}">${content}</div>`;
                    } else {
                        gridHtml += `<div class="slot-box" onclick="selectSlot(${i}, this)">${content}</div>`;
                    }
                }
                gridHtml += '</div>';
                
                document.getElementById('slot-selection-container').innerHTML = gridHtml;
                
            } catch(e) {
                document.getElementById('slot-selection-container').innerHTML = "<div style='color:red; text-align:center;'>Error loading slots.</div>";
            }
        };

        window.closeJoinModal = () => {
            document.getElementById('join-modal').classList.remove('active');
            window.selectedSlot = null;
        };

        window.selectSlot = (slotNum, el) => {
            const totalBal = depositBal + winningBal;
            if (totalBal < currentJoinFee) {
                if (confirm(`Insufficient Balance! You need ${currentJoinFee}৳ but you have ${totalBal}৳.\n\nGo to Add Money?`)) {
                    closeJoinModal();
                    navigate('add-money');
                }
                return;
            }
            
            document.querySelectorAll('.slot-box').forEach(b => b.classList.remove('selected'));
            el.classList.add('selected');
            window.selectedSlot = slotNum;
            
            let container = document.getElementById('join-inputs-container');
            container.innerHTML = `
                <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:10px; background:#fff5f0; padding:10px; border-radius:8px; border:1px solid #ffdacc;">
                    <div>
                       <h4 style="color:var(--primary); font-weight:700; margin:0; font-size:14px;">Selected: Slot ${slotNum}</h4>
                       <span style="font-size:11px; color:#666;">Entry Fee: ${currentJoinFee}৳</span>
                    </div>
                    <button class="btn-cancel" style="width:auto; padding:5px 12px; margin:0; font-size:11px; border-radius:4px;" onclick="cancelSlotSelection()">Change</button>
                </div>
            `;
            
            for (let i = 1; i <= currentJoinPlayersPerSlot; i++) {
                container.innerHTML += `
                    <div style="margin-bottom:15px; padding:10px; border:1px solid #eee; border-radius:8px; background:#fafafa;">
                        <h5 style="font-size:12px; margin-bottom:5px; color:#666; font-weight:600;">Player ${i} Details</h5>
                        <div class="form-group" style="margin-bottom:8px;">
                            <input type="text" class="input-field player-name-input" placeholder="In-Game Name">
                        </div>
                        <div class="form-group" style="margin-bottom:0;">
                            <input type="number" class="input-field player-uid-input" placeholder="Free Fire UID (Game ID)">
                        </div>
                    </div>
                `;
            }
            
            document.getElementById('slot-selection-container').style.display = 'none';
            container.style.display = 'block';
            document.getElementById('confirm-join-btn').style.display = 'block';
        };

        window.cancelSlotSelection = () => {
            document.getElementById('slot-selection-container').style.display = 'block';
            document.getElementById('join-inputs-container').style.display = 'none';
            document.getElementById('confirm-join-btn').style.display = 'none';
            document.querySelectorAll('.slot-box').forEach(b => b.classList.remove('selected'));
            window.selectedSlot = null;
        };

        window.confirmJoin = async () => {
            if (!window.selectedSlot) return alert("Please select a slot first.");
            
            const nameInputs = document.querySelectorAll('.player-name-input');
            const uidInputs = document.querySelectorAll('.player-uid-input');
            const matchDbKey = document.getElementById('confirm-join-btn').dataset.matchKey;

            let valid = true;
            let playersData = [];

            for (let i = 0; i < nameInputs.length; i++) {
                if (!nameInputs[i].value.trim() || !uidInputs[i].value.trim()) {
                    valid = false;
                    break;
                }
                playersData.push({
                    ign: nameInputs[i].value.trim(),
                    uid: uidInputs[i].value.trim()
                });
            }

            if (!valid) return alert("Please fill Name and UID for all players.");
            
            const btn = document.getElementById('confirm-join-btn');
            btn.disabled = true;
            btn.innerText = "Joining...";

            try {
                const totalBal = depositBal + winningBal;
                if (totalBal < currentJoinFee) {
                    btn.disabled = false;
                    btn.innerText = "Join Match";
                    return alert("Insufficient balance.");
                }

                const slotRef = ref(db, `match_participants/${currentJoinMatchId}/${window.selectedSlot}`);
                const slotSnap = await get(slotRef);
                if (slotSnap.exists()) {
                     btn.disabled = false;
                     btn.innerText = "Join Match";
                     return alert("Sorry, this slot was just taken by someone else! Please select another slot.");
                }

                // Balance deduction logic
                let newDeposit = depositBal;
                let newWinning = winningBal;
                let remainingFee = currentJoinFee;

                if (newDeposit >= remainingFee) {
                    newDeposit -= remainingFee;
                } else {
                    remainingFee -= newDeposit;
                    newDeposit = 0;
                    newWinning -= remainingFee;
                }

                await update(ref(db, 'users/' + currentUser.uid), { deposit: newDeposit, winning: newWinning });

                await set(slotRef, {
                    joinedBy: currentUser.uid,
                    timestamp: serverTimestamp(),
                    players: playersData
                });

                const matchRef = ref(db, 'matches/' + matchDbKey);
                const matchSnap = await get(matchRef);
                if (matchSnap.exists()) {
                    const currentJoined = parseInt(matchSnap.val().joined || 0);
                    await update(matchRef, { joined: currentJoined + currentJoinPlayersPerSlot });
                }

                alert("Successfully Joined! Check 'View Joined' to see your slot.");
                
                btn.disabled = false;
                btn.innerText = "Join Match";
                closeJoinModal();

            } catch(e) {
                alert(e.message);
                btn.disabled = false;
                btn.innerText = "Join Match";
            }
        };

        /* --- VIEW JOINED MEMBERS WITH SLOTS GRID --- */
        window.openJoinedView = (dbKey) => {
            const match = rawMatches.find(m => m.dbKey === dbKey);
            if (!match) return;
            
            document.getElementById('view-joined-title').innerText = escapeHTML(match.title);
            const container = document.getElementById('joined-members-list-container');
            container.innerHTML = "<div style='text-align:center; padding:20px; color:#999;'><i class='fas fa-spinner fa-spin'></i> Loading participants...</div>";
            navigate('view-joined-members');

            let playersPerSlot = 1;
            let typeLow = (match.type || '').toLowerCase();
            if (typeLow.includes('duo')) playersPerSlot = 2;
            if (typeLow.includes('squad')) playersPerSlot = 4;
            
            let totalPlayers = parseInt(match.total) || 48;
            let totalSlotsNum = Math.floor(totalPlayers / playersPerSlot);

            const matchRef = ref(db, 'match_participants/' + match.dbKey);
            onValue(matchRef, (snapshot) => {
                const data = snapshot.val() || {};
                
                let html = '<div class="joined-slots-grid">';
                
                for (let i = 1; i <= totalSlotsNum; i++) {
                     let slotData = data[i];
                     
                     if (slotData) {
                          let isMe = (currentUser && slotData.joinedBy === currentUser.uid);
                          let boxClass = isMe ? 'j-slot-box j-me' : 'j-slot-box j-taken';
                          let badge = isMe ? '<div class="j-badge">Your Slot</div>' : '';
                          
                          let playersHtml = '';
                          if (slotData.players) {
                               playersHtml = slotData.players.map((p) => `
                                   <div class="j-player-row">
                                       <span><i class="fas fa-user" style="font-size:10px; margin-right:4px;"></i>${escapeHTML(p.ign)}</span>
                                       <span style="font-size:10px; color:#666;">UID: ${escapeHTML(p.uid)}</span>
                                   </div>
                               `).join('');
                          } else if (slotData.ign) {
                               playersHtml = `
                                   <div class="j-player-row">
                                       <span><i class="fas fa-user" style="font-size:10px; margin-right:4px;"></i>${escapeHTML(slotData.ign)}</span>
                                       <span style="font-size:10px; color:#666;">UID: ${escapeHTML(slotData.uid)}</span>
                                   </div>
                               `;
                          }
                          
                          html += `
                              <div class="${boxClass}">
                                  <div class="j-slot-header">Slot ${i} ${badge}</div>
                                  <div class="j-slot-body">
                                       ${playersHtml}
                                  </div>
                              </div>
                          `;
                     } else {
                          html += `
                              <div class="j-slot-box j-empty">
                                  <div class="j-slot-header">Slot ${i}</div>
                                  <div class="j-slot-body" style="text-align:center; color:#999; padding:10px 0;">
                                      Available
                                  </div>
                              </div>
                          `;
                     }
                }
                
                html += '</div>';
                container.innerHTML = html;
            });
        };

        window.openMatchResult = (dbKey) => {
            const match = rawMatches.find(m => m.dbKey === dbKey);
            if (!match || !match.results) return alert("Results not available yet.");

            const container = document.getElementById('result-details-container');

            let rows = match.results.map(r => `
                <tr class="${r.win > 0 ? 'winner-row' : ''}">
                    <td>${escapeHTML(r.name)}</td>
                    <td>${escapeHTML(r.kill)}</td>
                    <td>${escapeHTML(r.win)}</td>
                </tr>
            `).join('');

            container.innerHTML = `
                <div class="result-view-header">
                    <div class="result-view-title">${escapeHTML(match.title)}</div>
                    <table class="result-table">
                        <thead>
                            <tr>
                                <th>Game Name</th>
                                <th>Kill</th>
                                <th>Win</th>
                            </tr>
                        </thead>
                        <tbody>${rows}</tbody>
                    </table>
                </div>

                <div class="rules-box">
                    <h4 class="rules-title">Information</h4>
                    <ul class="rules-list">
                        <li><i class="fas fa-check"></i> Match finished at ${escapeHTML(match.time)}</li>
                        <li><i class="fas fa-check"></i> Winnings have been added to wallets.</li>
                    </ul>
                </div>
            `;
            navigate('match-result');
        };

        window.openPrizeModal = (dbKey, title) => {
            const match = rawMatches.find(m => m.dbKey === dbKey);
            document.getElementById('prize-modal-title').innerText = title;
            const body = document.getElementById('prize-modal-body');

            if (!match || !match.prize_list || match.prize_list.length === 0) {
                body.innerHTML = "<div style='text-align:center; padding:20px; color:#999;'>এই match এর prize list এখনো add করা হয়নি।</div>";
            } else {
                let html = '<table style="width:100%; border-collapse:collapse;">';
                html += '<thead><tr style="background:var(--primary); color:white;">';
                html += '<th style="padding:8px; text-align:left; font-size:13px;">অবস্থান</th>';
                html += '<th style="padding:8px; text-align:right; font-size:13px;">পুরস্কার</th>';
                html += '</tr></thead><tbody>';

                match.prize_list.forEach((item, i) => {
                    const bg = i % 2 === 0 ? '#fff' : '#fafafa';
                    html += '<tr style="background:' + bg + '; border-bottom:1px solid #eee;">';
                    html += '<td style="padding:10px 8px; font-size:13px; font-weight:600;">' + escapeHTML(item.rank) + '</td>';
                    html += '<td style="padding:10px 8px; font-size:13px; font-weight:700; color:var(--primary); text-align:right;">৳ ' + escapeHTML(item.prize) + '</td>';
                    html += '</tr>';
                });

                html += '</tbody></table>';
                if (match.per_kill && match.per_kill > 0) {
                    html += '<div style="margin-top:12px; padding:10px; background:#fff5f0; border-radius:8px; border-left:3px solid var(--primary);">';
                    html += '<span style="font-size:13px; font-weight:600;">প্রতি Kill: <strong style="color:var(--primary);">৳ ' + match.per_kill + '</strong></span>';
                    html += '</div>';
                }
                body.innerHTML = html;
            }
            document.getElementById('prize-modal').classList.add('active');
        };

        window.closePrizeModal = () => {
            document.getElementById('prize-modal').classList.remove('active');
        };

        /* --- NAVIGATION & UI --- */
        window.showAuthPage = (type) => {
            closeAllSidebars();
            if (type === 'login') {
                document.getElementById('login-page').classList.add('active');
                document.getElementById('register-page').classList.remove('active');
            } else {
                document.getElementById('register-page').classList.add('active');
                document.getElementById('login-page').classList.remove('active');
            }
        };

        window.closeAuthPage = () => {
            document.querySelectorAll('.auth-page').forEach(el => el.classList.remove('active'));
        };

        window.closeAllSidebars = () => {
            document.getElementById('sidebar').classList.remove('active');
            document.getElementById('notif-sidebar').classList.remove('active');
            document.querySelector('.sidebar-overlay').classList.remove('active');
        }

        window.toggleSidebar = () => {
            const sidebar = document.getElementById('sidebar');
            const overlay = document.querySelector('.sidebar-overlay');
            if (sidebar.classList.contains('active')) {
                closeAllSidebars();
            } else {
                closeAllSidebars();
                sidebar.classList.add('active');
                overlay.classList.add('active');
            }
        };

        window.toggleNotification = () => {
            const sidebar = document.getElementById('notif-sidebar');
            const overlay = document.querySelector('.sidebar-overlay');
            if (sidebar.classList.contains('active')) {
                closeAllSidebars();
            } else {
                closeAllSidebars();
                sidebar.classList.add('active');
                overlay.classList.add('active');
            }
        }

        window.navigate = (sectionId) => {
            if ((sectionId === 'profile' || sectionId === 'add-money' || sectionId === 'withdraw' || sectionId === 'history' || sectionId === 'match-history' || sectionId === 'rules-view') && !currentUser) {
                showAuthPage('login');
                return;
            }

            document.querySelectorAll('.app-section').forEach(el => el.classList.remove('active'));
            const target = document.getElementById(sectionId);
            if (target) target.classList.add('active');
            if (sectionId === 'add-money') {
                showDepStep(1);
                showWdStep(1);
                wdMethod = null; depMethod = null;
            }
            
            if (sectionId === 'match-history') {
                loadMatchHistory();
            }
            if (sectionId === 'rules-view') {
                loadAllRules();
            }

            closeAllSidebars();
            window.scrollTo(0, 0);

            const bnMap = {
                'home': 'bn-home',
                'matches-view': 'bn-matches',
                'view-joined-members': 'bn-matches',
                'match-result': 'bn-matches',
                'add-money': null,
                'withdraw': null,
                'contact': 'bn-support',
                'profile': 'bn-profile',
                'history': 'bn-profile',
                'match-history': 'bn-profile',
                'rules-view': 'bn-profile'
            };
            document.querySelectorAll('.bn-item').forEach(el => el.classList.remove('bn-active'));
            const activeId = bnMap[sectionId];
            if (activeId) document.getElementById(activeId)?.classList.add('bn-active');
        };

        window.bottomNav = (page) => {
            if (page === 'matches-view') {
                if (!currentActiveCategory) {
                    const keys = Object.keys(activeCategories);
                    if (keys.length > 0) {
                        openCategory(keys[0]);
                        return;
                    } else {
                        navigate('home');
                        return;
                    }
                } else {
                    openCategory(currentActiveCategory);
                    return;
                }
            }
            navigate(page);
        };

        window.switchWalletTab = (tab) => {
            const depositPanel = document.getElementById('wallet-deposit-panel');
            const withdrawPanel = document.getElementById('wallet-withdraw-panel');
            const depositBtn = document.getElementById('wallet-tab-deposit');
            const withdrawBtn = document.getElementById('wallet-tab-withdraw');
            if (tab === 'deposit') {
                depositPanel.style.display = 'block';
                withdrawPanel.style.display = 'none';
                depositBtn.style.background = 'var(--primary)';
                depositBtn.style.color = 'white';
                withdrawBtn.style.background = 'var(--card-bg)';
                withdrawBtn.style.color = 'var(--text-dark)';
            } else {
                depositPanel.style.display = 'none';
                withdrawPanel.style.display = 'block';
                withdrawBtn.style.background = 'var(--primary)';
                withdrawBtn.style.color = 'white';
                depositBtn.style.background = 'var(--card-bg)';
                depositBtn.style.color = 'var(--text-dark)';
            }
        };

        window.copyToClipboard = (text) => {
            navigator.clipboard.writeText(text);
            alert("Copied: " + text);
        };

        /* --- NEW GAME RULES LOGIC --- */
        window.currentRulesData = {};
        window.currentCatData = {};

        async function loadAllRules() {
            const tabsContainer = document.getElementById('rules-category-tabs');
            const container = document.getElementById('all-rules-container');
            
            tabsContainer.innerHTML = "";
            container.innerHTML = "<div style='text-align:center; padding:30px; color:#999;'><i class='fas fa-spinner fa-spin'></i> Loading rules...</div>";
            
            try {
                const rulesSnap = await get(ref(db, 'rules'));
                const catSnap = await get(ref(db, 'categories'));
                
                if (!rulesSnap.exists()) {
                    container.innerHTML = document.getElementById('default-rules-box').outerHTML;
                    return;
                }
                
                window.currentRulesData = rulesSnap.val();
                window.currentCatData = catSnap.exists() ? catSnap.val() : {};
                
                let tabsHtml = "";
                let firstCatId = null;
                
                Object.keys(window.currentRulesData).forEach(catId => {
                    const rData = window.currentRulesData[catId];
                    if (rData && rData.rules && rData.rules.length > 0) {
                        if (!firstCatId) firstCatId = catId;
                        const catName = window.currentCatData[catId] ? window.currentCatData[catId].name : "Category";
                        tabsHtml += `<div class="rule-tab" id="rtab-${catId}" onclick="showRulesForCat('${catId}')">${escapeHTML(catName)}</div>`;
                    }
                });
                
                if (!firstCatId) {
                    container.innerHTML = document.getElementById('default-rules-box').outerHTML;
                    return;
                }
                
                tabsContainer.innerHTML = tabsHtml;
                window.showRulesForCat(firstCatId); // Show the first category's rules automatically
                
            } catch(e) {
                container.innerHTML = "<div style='text-align:center; padding:30px; color:red;'>Error loading rules.</div>";
            }
        }

        window.showRulesForCat = (catId) => {
            document.querySelectorAll('.rule-tab').forEach(el => el.classList.remove('active'));
            const activeTab = document.getElementById(`rtab-${catId}`);
            if (activeTab) activeTab.classList.add('active');
            
            const rData = window.currentRulesData[catId];
            const container = document.getElementById('all-rules-container');
            
            if (rData && rData.rules && rData.rules.length > 0) {
                const catName = window.currentCatData[catId] ? window.currentCatData[catId].name : "Rules";
                const title = rData.title || `${catName} - Rules`;
                
                let html = `<div class="rules-box" style="border:1px solid #eee; padding:15px; border-radius:8px; background:#fafafa;">
                    <h4 style="font-size:15px; font-weight:700; color:var(--primary); border-bottom:1px solid #ddd; padding-bottom:8px; margin-bottom:10px;">${escapeHTML(title)}</h4>
                    <ul class="rules-list" style="list-style:none; padding:0; margin:0;">`;
                
                rData.rules.forEach(rule => {
                    html += `<li style="font-size:13px; color:#555; margin-bottom:8px; display:flex; gap:8px;"><i class="fas fa-check-circle" style="color:var(--primary); margin-top:3px;"></i> <span>${escapeHTML(rule)}</span></li>`;
                });
                
                html += `</ul></div>`;
                container.innerHTML = html;
            } else {
                container.innerHTML = "<div style='text-align:center; padding:30px; color:#999;'>No rules found for this category.</div>";
            }
        };

        /* --- MATCH HISTORY LOGIC --- */
        async function loadMatchHistory() {
            if (!currentUser) return;
            const container = document.getElementById('match-history-list');
            container.innerHTML = "<div style='text-align:center; padding:30px; color:#999;'><i class='fas fa-spinner fa-spin'></i> Loading your matches...</div>";
            
            try {
                const snap = await get(ref(db, 'match_participants'));
                if (!snap.exists()) {
                    container.innerHTML = "<div style='text-align:center; padding:30px; color:#999;'>You haven't joined any matches yet.</div>";
                    return;
                }
                
                const allData = snap.val();
                let myMatches = [];
                
                Object.keys(allData).forEach(matchId => {
                    const slots = allData[matchId];
                    let joinedSlot = null;
                    let playersArr = [];
                    
                    Object.keys(slots).forEach(slotKey => {
                        if (slots[slotKey].joinedBy === currentUser.uid) {
                            joinedSlot = slotKey;
                            playersArr = slots[slotKey].players || [];
                        }
                    });
                    
                    if (joinedSlot) {
                        const matchDetails = rawMatches.find(m => m.dbKey === matchId);
                        if (matchDetails) {
                            myMatches.push({
                                matchId: matchId,
                                slot: joinedSlot,
                                players: playersArr,
                                matchData: matchDetails
                            });
                        }
                    }
                });
                
                if (myMatches.length === 0) {
                    container.innerHTML = "<div style='text-align:center; padding:30px; color:#999;'>You haven't joined any matches yet.</div>";
                    return;
                }
                
                myMatches.sort((a, b) => b.matchData.timestamp - a.matchData.timestamp);
                
                container.innerHTML = "";
                myMatches.forEach(item => {
                    const m = item.matchData;
                    const statusText = m.status === 'Finished' ? '<span style="color:red; font-weight:bold;">Finished</span>' : '<span style="color:green; font-weight:bold;">Upcoming</span>';
                    
                    let playerNames = item.players.map(p => escapeHTML(p.ign)).join(', ');
                    if(!playerNames) playerNames = "Self";

                    let html = `
                    <div style="padding:15px; border:1px solid #eee; border-radius:8px; margin-bottom:15px; background:#fafafa;">
                        <div style="display:flex; justify-content:space-between; margin-bottom:8px;">
                            <h4 style="font-size:14px; font-weight:700; color:var(--primary); margin:0;">${escapeHTML(m.title)}</h4>
                            <span style="font-size:12px;">${statusText}</span>
                        </div>
                        <div style="font-size:12px; color:#555; margin-bottom:5px;">
                            <i class="fas fa-clock" style="margin-right:5px;"></i> Time: ${escapeHTML(m.time)}
                        </div>
                        <div style="font-size:12px; color:#555; margin-bottom:8px;">
                            <i class="fas fa-ticket-alt" style="margin-right:5px;"></i> Your Slot: <strong>${item.slot}</strong>
                        </div>
                        <div style="font-size:11px; background:#fff; border:1px dashed #ccc; padding:8px; border-radius:6px;">
                            <span style="color:#777; font-weight:600; display:block; margin-bottom:3px;">Registered Players:</span>
                            <span style="color:#000;">${playerNames}</span>
                        </div>
                        <div style="display:flex; justify-content:space-between; align-items:center; margin-top:10px;">
                            <button class="btn-room" style="padding:6px 12px; margin:0;" onclick="checkRoomDetails('${m.room_id}', '${m.room_pass}')">ROOM ID</button>
                            ${m.status === 'Finished' ? `<button class="btn-view-result" style="padding:6px 12px; margin:0;" onclick="openMatchResult('${m.dbKey}')">View Result</button>` : ''}
                        </div>
                    </div>`;
                    container.innerHTML += html;
                });
                
            } catch(e) {
                container.innerHTML = "<div style='text-align:center; padding:30px; color:red;'>Error loading matches.</div>";
            }
        }

        /* --- WALLET FLOW (DEPOSIT + WITHDRAW) --- */
        let depAmount = 0;
        let depMethod = null;
        let wdMethod = null;

        window.showDepStep = (step) => {
            document.querySelectorAll('#wallet-deposit-panel .step-container').forEach(el => el.classList.remove('active-step'));
            document.getElementById('dep-step-' + step).classList.add('active-step');
        };

        window.depGoToMethod = () => {
            const val = parseFloat(document.getElementById('add-amount-input').value);
            const minDep = parseFloat(appSettings.min_deposit) || 20;
            if (!val || val < minDep) return alert('Minimum deposit: ' + minDep + ' BDT');
            depAmount = val;
            document.getElementById('dep-display-amount').innerText = val + ' ৳';
            showDepStep(2);
        };

        window.depSelectMethod = (method) => {
            depMethod = method;
            const isBkash = method === 'Bkash';
            const color = isBkash ? '#e2136e' : '#ec1c24';
            const logo = isBkash
                ? 'https://freelogopng.com/images/all_img/1656234745bkash-app-logo-png.png'
                : 'https://freepnglogo.com/images/all_img/1679248787Nagad-Logo.png';
            const num = isBkash ? (appSettings.bkash_number || '...') : (appSettings.nagad_number || '...');

            const header = document.getElementById('dep-method-header');
            header.style.background = color;
            document.getElementById('dep-method-logo').src = logo;
            document.getElementById('dep-final-amount').innerText = depAmount;
            document.getElementById('dep-display-num').value = num;
            document.getElementById('dep-display-num').style.color = color;
            document.getElementById('dep-display-num').style.borderColor = color;
            document.getElementById('dep-display-num').style.background = isBkash ? '#fff0f5' : '#fff5f5';
            document.getElementById('dep-copy-btn').style.background = color;
            document.getElementById('dep-num-label').innerText = method + ' Number (Copy করুন):';
            document.getElementById('dep-method-name').innerText = method.toUpperCase();
            document.getElementById('dep-instruction-box').style.background = color;
            document.getElementById('dep-verify-btn').style.background = color;
            document.getElementById('dep-trxid').value = '';
            showDepStep(3);
        };

        let _smsResolve = null;
        let _smsTimeoutId = null;
        window.smsVerificationResult = (result) => {
            if (_smsTimeoutId) { clearTimeout(_smsTimeoutId); _smsTimeoutId = null; }
            if (_smsResolve) {
                const cb = _smsResolve;
                _smsResolve = null;
                cb(result);
            }
        };

        function requestSmsVerification(trxId, amount, method) {
            if (_smsResolve) {
                const old = _smsResolve;
                _smsResolve = null;
                old({ found: false, amountMatch: false, cancelled: true });
            }
            if (_smsTimeoutId) { clearTimeout(_smsTimeoutId); _smsTimeoutId = null; }

            return new Promise((resolve) => {
                if (window.SmsReader && window.SmsReader.verify) {
                    _smsResolve = resolve;
                    window.SmsReader.verify(trxId, String(amount), method);
                } else if (window.Android && window.Android.verifySms) {
                    _smsResolve = resolve;
                    window.Android.verifySms(trxId, String(amount), method);
                } else {
                    resolve({ found: false, amountMatch: false, noReader: true });
                    return;
                }
                // Backup timeout just in case native code fails to respond
                _smsTimeoutId = setTimeout(() => {
                    if (_smsResolve) {
                        const cb = _smsResolve;
                        _smsResolve = null;
                        _smsTimeoutId = null;
                        cb({ found: false, amountMatch: false, timeout: true });
                    }
                }, 15000);
            });
        }

        window.depVerifyPayment = async () => {
            if (!currentUser) return showAuthPage('login');

            const trxId = document.getElementById('dep-trxid').value.trim().toUpperCase();
            if (!trxId) return alert('Transaction ID দিন।');
            if (trxId.length < 6) return alert('সঠিক TrxID দিন।');
            if (!depAmount || depAmount < 20) return alert('Amount সঠিক নয়। পিছনে গিয়ে আবার দিন।');
            if (!depMethod) return alert('Method select করুন।');

            const btn = document.getElementById('dep-verify-btn');
            
            if (btn.disabled) return;
            
            btn.disabled = true;
            let seconds = 1;
            btn.innerText = `Verifying... ${seconds}s`;

            // লাইভ কাউন্টডাউন ১ থেকে ১৫ সেকেন্ড চলবে
            const timerInterval = setInterval(() => {
                seconds++;
                if (seconds <= 15) {
                    btn.innerText = `Verifying... ${seconds}s`;
                }
            }, 1000);

            try {
                // BUG FIX: Promise.all দিয়ে আমরা ঠিক ১৫ সেকেন্ড ওয়েট করাচ্ছি।
                // এতে করে ডাটাবেস চেক বা রিকোয়েস্ট অ্যাডমিনের কাছে কখনোই ১৫ সেকেন্ডের আগে যাবে্বা না।
                const [smsResult] = await Promise.all([
                    requestSmsVerification(trxId, depAmount, depMethod),
                    new Promise(resolve => setTimeout(resolve, 15000))
                ]);

                // ১৫ সেকেন্ড শেষ হওয়ার পর কাউন্টডাউন বন্ধ করবো
                clearInterval(timerInterval);

                const usedSnap = await get(ref(db, 'used_trx/' + trxId));
                if (usedSnap.exists()) {
                    btn.disabled = false;
                    btn.innerText = 'Verify SMS';
                    return alert('❌ এই TrxID আগে ব্যবহার হয়েছে অথবা Request পেন্ডিং আছে।');
                }

                if (smsResult.noReader || smsResult.timeout) {
                    const note = smsResult.noReader ? 'SMS Reader connected নেই' : 'SMS Reader timeout';
                    await saveDepositRequest(trxId, 'Pending', note);
                    alert('\u2705 Request জমা হয়েছে!\n\nAdmin verify করার পরে balance add হবে।');
                    resetDepositForm();
                    navigate('history');

                } else if (smsResult.found && smsResult.amountMatch) {
                    await update(ref(db, 'users/' + currentUser.uid), { deposit: depositBal + depAmount });
                    await saveDepositRequest(trxId, 'Completed', 'Auto verified via SMS');
                    alert('\u2705 সফল! ' + depAmount + ' BDT আপনার account এ যোগ হয়েছে।');
                    resetDepositForm();
                    navigate('history');

                } else if (smsResult.found && !smsResult.amountMatch) {
                    await saveDepositRequest(trxId, 'Failed', 'Amount mismatch — SMS: ' + smsResult.smsAmount + ', Claimed: ' + depAmount);
                    alert('\u274c Amount মিলছে না!\n\nআপনি দিয়েছেন: ' + depAmount + ' BDT\nSMS এ পাওয়া গেছে: ' + smsResult.smsAmount + ' BDT\n\nRequest admin এর কাছে পাঠানো হয়েছে।');
                    resetDepositForm();
                    navigate('history');

                } else {
                    await saveDepositRequest(trxId, 'Failed', 'TrxID SMS এ match হয়নি');
                    alert('\u274c TrxID verify হয়নি!\n\nএই TrxID দিয়ে কোনো ' + depMethod + ' transaction পাওয়া যায়নি।\n\nRequest admin এর কাছে পাঠানো হয়েছে।');
                    resetDepositForm();
                    navigate('history');
                }

            } catch(e) {
                clearInterval(timerInterval);
                alert('Error: ' + e.message);
                btn.disabled = false;
                btn.innerText = 'Verify SMS';
            }
        };

        async function saveDepositRequest(trxId, status, note = '') {
            const amt = depAmount;
            const mth = depMethod;
            const uid = currentUser.uid;
            const email = currentUser.email || '';
            const displayName = currentUser.displayName || '';
            const dateStr = new Date().toLocaleString();

            await push(ref(db, 'deposit_requests'), {
                uid: uid,
                email: email,
                displayName: displayName,
                amount: amt,
                method: mth,
                trxId: trxId,
                status: status,
                note: note,
                date: dateStr,
                timestamp: serverTimestamp()
            });

            await push(ref(db, 'transactions/' + uid), {
                type: 'Deposit',
                method: mth,
                amount: amt,
                trxId: trxId,
                status: status,
                note: note,
                date: dateStr
            });

            if (!status.includes('Failed')) {
                await set(ref(db, 'used_trx/' + trxId), {
                    uid: uid,
                    amount: amt,
                    method: mth,
                    status: status,
                    timestamp: serverTimestamp()
                });
            }
        }

        function resetDepositForm() {
            document.getElementById('add-amount-input').value = '';
            document.getElementById('dep-trxid').value = '';
            depAmount = 0;
            depMethod = null;
            showDepStep(1);
        }

        window.showWdStep = (step) => {
            document.querySelectorAll('#wallet-withdraw-panel .step-container').forEach(el => el.classList.remove('active-step'));
            document.getElementById('wd-step-' + step).classList.add('active-step');
        };

        window.wdGoToMethod = () => {
            const val = parseFloat(document.getElementById('withdraw-amount').value);
            if (!val || val < 100) return alert('Minimum withdraw: 100 BDT');
            if (val > winningBal) return alert('Insufficient winning balance. Available: ' + winningBal + ' ৳');
            document.getElementById('wd-display-amount').innerText = val + ' ৳';
            showWdStep(2);
        };

        window.wdSelectMethod = (method) => {
            wdMethod = method;
            const isBkash = method === 'Bkash';
            const color = isBkash ? '#e2136e' : '#ec1c24';
            const logo = isBkash
                ? 'https://freelogopng.com/images/all_img/1656234745bkash-app-logo-png.png'
                : 'https://freepnglogo.com/images/all_img/1679248787Nagad-Logo.png';
            const amount = document.getElementById('withdraw-amount').value;

            document.getElementById('wd-method-header').style.background = color;
            document.getElementById('wd-method-logo').src = logo;
            document.getElementById('wd-method-title').innerText = method + ' Withdraw';
            document.getElementById('wd-confirm-amount').innerText = amount;
            document.getElementById('wd-num-label').innerText = method + ' Account Number';
            document.getElementById('wd-submit-btn').style.background = color;
            document.getElementById('withdraw-number').value = '';
            showWdStep(3);
        };

        window.submitWithdraw = async () => {
            if (!currentUser) return showAuthPage('login');
            const amount = parseFloat(document.getElementById('withdraw-amount').value);
            const number = document.getElementById('withdraw-number').value.trim();
            const method = wdMethod;

            if (!amount || amount < 100) return alert('Minimum withdraw: 100 BDT');
            if (!method) return alert('Method select করুন।');
            if (!number) return alert('Account number দিন।');
            if (amount > winningBal) return alert('Insufficient winning balance: ' + winningBal + ' ৳');

            const btn = document.getElementById('wd-submit-btn');
            if (btn.disabled) return;
            btn.disabled = true;
            btn.innerText = 'Processing...';

            try {
                await update(ref(db, 'users/' + currentUser.uid), { winning: winningBal - amount });

                await push(ref(db, 'transactions/' + currentUser.uid), {
                    type: 'Withdraw',
                    method: method,
                    amount: amount,
                    number: number,
                    status: 'Pending',
                    date: new Date().toLocaleString()
                });

                await push(ref(db, 'withdraw_requests'), {
                    uid: currentUser.uid,
                    email: currentUser.email,
                    amount: amount,
                    method: method,
                    number: number,
                    status: 'Pending',
                    date: new Date().toLocaleString(),
                    timestamp: serverTimestamp()
                });

                alert('Withdraw request submitted! ' + amount + ' ৳ via ' + method + ' to ' + number + '. Admin approval pending.');
                document.getElementById('withdraw-amount').value = '';
                document.getElementById('withdraw-number').value = '';
                wdMethod = null;
                showWdStep(1);
                navigate('history');
            } catch(e) { 
                alert('Error: ' + e.message); 
            } finally {
                btn.disabled = false;
                btn.innerText = 'Submit Request';
            }
        };

        function loadHistory() {
            if (!currentUser) return;
            const historyList = document.getElementById('history-list');
            const trxRef = ref(db, 'transactions/' + currentUser.uid);
            
            onValue(trxRef, (snapshot) => {
                historyList.innerHTML = "";
                const data = snapshot.val();
                
                if (data) {
                    const entries = Object.values(data).reverse();
                    entries.forEach(trx => {
                        const isWithdraw = trx.type === 'Withdraw';
                        const color = isWithdraw ? 'red' : 'green';
                        const sign = isWithdraw ? '-' : '+';
                        
                        let badgeStyle = 'background:#eee; color:#666;';
                        if (trx.status) {
                            if (trx.status.includes('Approved') || trx.status.includes('Paid') || trx.status.includes('Completed') || trx.status.includes('Success') || trx.status.includes('Won')) {
                                badgeStyle = 'background:#d4edda; color:#155724; border: 1px solid #c3e6cb;';
                            } else if (trx.status.includes('Rejected') || trx.status.includes('Failed') || trx.status.includes('Cancelled')) {
                                badgeStyle = 'background:#f8d7da; color:#721c24; border: 1px solid #f5c6cb;';
                            } else if (trx.status.includes('Pending')) {
                                badgeStyle = 'background:#fff3cd; color:#856404; border: 1px solid #ffeeba;';
                            }
                        }

                        const html = `
                         <div style="display:flex; justify-content:space-between; padding:15px; border-bottom:1px solid #eee;">
                            <div>
                                <h4 style="font-size:14px; color:#333; font-weight:700;">${escapeHTML(trx.type)} (${escapeHTML(trx.method)})</h4>
                                <p style="font-size:11px; color:#888;">${escapeHTML(trx.date)}</p>
                            </div>
                            <div style="text-align:right;">
                                <div style="font-weight:800; color:${color}; margin-bottom:6px; font-size:15px;">${sign}${escapeHTML(trx.amount)} ৳</div>
                                <span style="font-size:10px; padding:3px 10px; border-radius:12px; font-weight:700; ${badgeStyle}">${escapeHTML(trx.status)}</span>
                            </div>
                        </div>`;
                        historyList.innerHTML += html;
                    });
                } else {
                    historyList.innerHTML = "<div style='text-align:center; padding:30px; color:#999;'>No transactions found.</div>";
                }
            });
        }
    </script>
    
    <!-- BOTTOM NAVIGATION -->
    <nav class="bottom-nav">
        <div class="bn-item bn-active" id="bn-home" onclick="bottomNav('home')">
            <i class="fas fa-home"></i>
            <span>Home</span>
        </div>
        <div class="bn-item" id="bn-matches" onclick="bottomNav('matches-view')">
            <i class="fas fa-gamepad"></i>
            <span>Matches</span>
        </div>
        <div class="bn-center-wrap" onclick="bottomNav('add-money')">
            <div class="bn-center-btn">
                <i class="fas fa-wallet"></i>
            </div>
            <span>Wallet</span>
        </div>
        <div class="bn-item" id="bn-support" onclick="bottomNav('contact')">
            <i class="fas fa-headset"></i>
            <span>Support</span>
        </div>
        <div class="bn-item" id="bn-profile" onclick="bottomNav('profile')">
            <i class="fas fa-user"></i>
            <span>Profile</span>
        </div>
    </nav>

</body>
</html>.
