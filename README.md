<!DOCTYPE html>
<html lang="ml">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
    <title>KHATA PRO PREMIUM</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
    
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,600;14..32,700;14..32,800;14..32,900&family=Manjari:wght@400;700&display=swap');
        
        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Inter', 'Manjari', sans-serif; -webkit-tap-highlight-color: transparent; }
        
        html, body { overflow: hidden; width: 100%; height: 100%; position: fixed; background: #f0fdf4; transition: all 0.3s ease; }
        
        /* ===== THEME COLORS ===== */
        .theme-green { background: linear-gradient(145deg, #f0fdf4 0%, #dcfce7 100%); color: #1b5e20; }
        .theme-blue { background: linear-gradient(145deg, #eff6ff 0%, #bfdbfe 100%); color: #1e3a8a; }
        .theme-purple { background: linear-gradient(145deg, #faf5ff 0%, #e9d5ff 100%); color: #4c1d95; }
        .theme-rose { background: linear-gradient(145deg, #fff1f2 0%, #fecdd3 100%); color: #9f1239; }
        .theme-amber { background: linear-gradient(145deg, #fffbeb 0%, #fde68a 100%); color: #92400e; }
        .theme-cyan { background: linear-gradient(145deg, #ecfeff 0%, #a5f3fc 100%); color: #0e7490; }
        .theme-gray { background: linear-gradient(145deg, #f9fafb 0%, #e5e7eb 100%); color: #1f2937; }
        
        body.dark-mode.theme-green { background: #0b2b22; color: #e2e8f0; }
        body.dark-mode.theme-blue { background: #0a1a3a; color: #e2e8f0; }
        body.dark-mode.theme-purple { background: #1a0a2e; color: #e2e8f0; }
        body.dark-mode.theme-rose { background: #2e0a0f; color: #e2e8f0; }
        body.dark-mode.theme-amber { background: #2e1a0a; color: #e2e8f0; }
        body.dark-mode.theme-cyan { background: #0a1a1e; color: #e2e8f0; }
        body.dark-mode.theme-gray { background: #1a1a1a; color: #e2e8f0; }
        
        .premium-card {
            background: rgba(255,255,255,0.95);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(46, 125, 50, 0.15);
            border-radius: 24px;
            box-shadow: 0 8px 30px rgba(0,100,0,0.08);
            padding: 16px;
            transition: all 0.3s ease;
        }
        body.dark-mode .premium-card {
            background: rgba(30, 41, 59, 0.95);
            border-color: #334155;
            box-shadow: 0 8px 30px rgba(0,0,0,0.3);
        }
        
        .header-premium {
            border-bottom: 3px solid #facc15;
            color: white;
            padding: 12px 16px;
            border-radius: 0 0 24px 24px;
            box-shadow: 0 4px 20px rgba(0,50,0,0.2);
            transition: all 0.3s ease;
        }
        body.dark-mode .header-premium { border-bottom-color: #facc15; }
        
        .fab {
            position: fixed;
            bottom: 24px;
            right: 24px;
            width: 64px;
            height: 64px;
            background: linear-gradient(135deg, #facc15, #f59e0b);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 28px;
            color: #1b5e20;
            box-shadow: 0 8px 30px rgba(250, 204, 21, 0.4);
            z-index: 100;
            transition: all 0.3s ease;
            cursor: pointer;
            border: none;
        }
        .fab:active { transform: scale(0.9); }
        body.dark-mode .fab { background: linear-gradient(135deg, #facc15, #d97706); color: #0f172a; }
        
        .input-premium {
            background: rgba(255,255,255,0.9);
            border: 2px solid #c8e6c9;
            border-radius: 16px;
            padding: 14px 16px;
            font-weight: 700;
            transition: all 0.2s;
        }
        .input-premium:focus {
            border-color: #2e7d32;
            box-shadow: 0 0 0 4px rgba(46, 125, 50, 0.1);
            outline: none;
        }
        body.dark-mode .input-premium {
            background: #1e293b;
            border-color: #475569;
            color: #f1f5f9;
        }
        body.dark-mode .input-premium:focus {
            border-color: #facc15;
            box-shadow: 0 0 0 4px rgba(250, 204, 21, 0.1);
        }
        
        .dashboard-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 12px; padding: 4px; }
        .dashboard-item {
            background: rgba(255,255,255,0.8);
            border-radius: 20px;
            padding: 14px;
            text-align: center;
            border: 1px solid rgba(46, 125, 50, 0.1);
            transition: all 0.2s;
        }
        body.dark-mode .dashboard-item {
            background: rgba(30, 41, 59, 0.8);
            border-color: #334155;
        }
        .dashboard-item .icon { font-size: 24px; margin-bottom: 4px; }
        .dashboard-item .value { font-size: 20px; font-weight: 900; }
        .dashboard-item .label { font-size: 10px; font-weight: 800; opacity: 0.7; }
        
        .client-item {
            display: flex;
            align-items: center;
            padding: 12px 16px;
            background: rgba(255,255,255,0.9);
            border-radius: 18px;
            margin-bottom: 8px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.04);
            border: 1px solid rgba(46, 125, 50, 0.05);
            transition: all 0.2s;
            cursor: pointer;
        }
        .client-item:active { transform: scale(0.98); }
        body.dark-mode .client-item {
            background: rgba(30, 41, 59, 0.9);
            border-color: #334155;
        }
        .client-avatar {
            width: 44px;
            height: 44px;
            background: linear-gradient(135deg, #4ade80, #22c55e);
            border-radius: 14px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 900;
            font-size: 18px;
            color: white;
            flex-shrink: 0;
        }
        
        ::-webkit-scrollbar { width: 4px; }
        ::-webkit-scrollbar-track { background: transparent; }
        ::-webkit-scrollbar-thumb { background: #4ade80; border-radius: 10px; }
        body.dark-mode ::-webkit-scrollbar-thumb { background: #facc15; }
        
        .modal-premium {
            background: rgba(255,255,255,0.98);
            backdrop-filter: blur(20px);
            border-radius: 32px;
            padding: 24px;
            max-width: 420px;
            width: 100%;
            box-shadow: 0 20px 60px rgba(0,0,0,0.15);
        }
        body.dark-mode .modal-premium {
            background: rgba(30, 41, 59, 0.98);
            box-shadow: 0 20px 60px rgba(0,0,0,0.4);
        }
        
        .lock-premium {
            background: linear-gradient(145deg, #0a0f1c 0%, #071c14 100%);
            border: 1px solid rgba(250, 204, 21, 0.1);
        }
        .lock-dot {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            border: 2px solid rgba(250, 204, 21, 0.4);
            transition: all 0.3s;
        }
        .lock-dot.active {
            background: #facc15;
            border-color: #facc15;
            box-shadow: 0 0 20px rgba(250, 204, 21, 0.4);
        }
        
        .btn-premium {
            background: linear-gradient(135deg, #2e7d32, #1b5e20);
            color: white;
            border: none;
            border-radius: 16px;
            padding: 14px 20px;
            font-weight: 900;
            font-size: 14px;
            transition: all 0.2s;
            cursor: pointer;
            box-shadow: 0 4px 15px rgba(46, 125, 50, 0.2);
        }
        .btn-premium:active { transform: scale(0.96); }
        body.dark-mode .btn-premium { background: linear-gradient(135deg, #facc15, #f59e0b); color: #0f172a; }
        
        .color-option {
            width: 32px;
            height: 32px;
            border-radius: 50%;
            cursor: pointer;
            border: 3px solid transparent;
            transition: all 0.2s;
        }
        .color-option.active {
            border-color: #facc15;
            transform: scale(1.15);
        }
        .color-option:hover { transform: scale(1.1); }
        
        @media (max-width: 400px) {
            .dashboard-grid { grid-template-columns: repeat(2, 1fr); gap: 8px; }
            .dashboard-item { padding: 10px; }
            .dashboard-item .value { font-size: 16px; }
            .client-item { padding: 10px 12px; }
            .client-avatar { width: 36px; height: 36px; font-size: 14px; }
        }
        
        .font-bold { font-weight: 700 !important; }
        .font-black { font-weight: 900 !important; }
        .text-xs { font-size: 0.75rem; font-weight: 600; }
        .text-sm { font-size: 0.875rem; font-weight: 700; }
        .text-base { font-size: 1rem; font-weight: 700; }
        .text-lg { font-size: 1.125rem; font-weight: 800; }
        .text-xl { font-size: 1.25rem; font-weight: 900; }
        .text-2xl { font-size: 1.5rem; font-weight: 900; }
        .text-3xl { font-size: 1.875rem; font-weight: 900; }
        h1, h2, h3, h4, h5, h6, p, span, div, button, input, textarea, select, label {
            font-weight: 700;
        }
        .premium-card p, .premium-card span, .premium-card div {
            font-weight: 700;
        }
        .dashboard-item .value { font-weight: 900; }
        .dashboard-item .label { font-weight: 800; }
    </style>
</head>
<body class="theme-green h-full w-full overflow-hidden">

    <!-- Lock Screen -->
    <div id="lockScreen" class="fixed inset-0 lock-premium z-[9999] flex flex-col items-center justify-between py-10 px-6 select-none">
        <div class="text-center mt-8">
            <div class="w-20 h-20 bg-gradient-to-br from-amber-500 to-amber-700 rounded-3xl mx-auto mb-4 flex items-center justify-center shadow-2xl">
                <i class="fa-solid fa-shield-halved text-4xl text-black"></i>
            </div>
            <h2 class="text-2xl font-black text-white">KHATA PRO</h2>
            <p id="lockScreenSubtitle" class="text-xs text-amber-300 font-bold mt-2">🔐 Enter Secure PIN</p>
        </div>
        <div class="flex gap-4 my-5 bg-black/40 px-6 py-3 rounded-full">
            <div id="dot-0" class="lock-dot"></div>
            <div id="dot-1" class="lock-dot"></div>
            <div id="dot-2" class="lock-dot"></div>
            <div id="dot-3" class="lock-dot"></div>
        </div>
        <div class="w-full max-w-[280px] grid grid-cols-3 gap-3 mb-4">
            <button class="aspect-square rounded-2xl bg-white/10 backdrop-blur border border-amber-500/30 text-2xl font-black text-white hover:bg-amber-500/20 active:scale-95 transition" onclick="pressKey('1')">1</button>
            <button class="aspect-square rounded-2xl bg-white/10 backdrop-blur border border-amber-500/30 text-2xl font-black text-white hover:bg-amber-500/20 active:scale-95 transition" onclick="pressKey('2')">2</button>
            <button class="aspect-square rounded-2xl bg-white/10 backdrop-blur border border-amber-500/30 text-2xl font-black text-white hover:bg-amber-500/20 active:scale-95 transition" onclick="pressKey('3')">3</button>
            <button class="aspect-square rounded-2xl bg-white/10 backdrop-blur border border-amber-500/30 text-2xl font-black text-white hover:bg-amber-500/20 active:scale-95 transition" onclick="pressKey('4')">4</button>
            <button class="aspect-square rounded-2xl bg-white/10 backdrop-blur border border-amber-500/30 text-2xl font-black text-white hover:bg-amber-500/20 active:scale-95 transition" onclick="pressKey('5')">5</button>
            <button class="aspect-square rounded-2xl bg-white/10 backdrop-blur border border-amber-500/30 text-2xl font-black text-white hover:bg-amber-500/20 active:scale-95 transition" onclick="pressKey('6')">6</button>
            <button class="aspect-square rounded-2xl bg-white/10 backdrop-blur border border-amber-500/30 text-2xl font-black text-white hover:bg-amber-500/20 active:scale-95 transition" onclick="pressKey('7')">7</button>
            <button class="aspect-square rounded-2xl bg-white/10 backdrop-blur border border-amber-500/30 text-2xl font-black text-white hover:bg-amber-500/20 active:scale-95 transition" onclick="pressKey('8')">8</button>
            <button class="aspect-square rounded-2xl bg-white/10 backdrop-blur border border-amber-500/30 text-2xl font-black text-white hover:bg-amber-500/20 active:scale-95 transition" onclick="pressKey('9')">9</button>
            <button class="rounded-2xl bg-red-500/20 backdrop-blur border border-red-500/30 text-xs font-bold text-red-400 py-3 hover:bg-red-500/30 active:scale-95 transition" onclick="clearCurrentPin()">⌫ CLR</button>
            <button class="aspect-square rounded-2xl bg-white/10 backdrop-blur border border-amber-500/30 text-2xl font-black text-white hover:bg-amber-500/20 active:scale-95 transition" onclick="pressKey('0')">0</button>
            <button class="rounded-2xl bg-red-500/20 backdrop-blur border border-red-500/30 text-xs font-bold text-red-400 py-3 hover:bg-red-500/30 active:scale-95 transition" onclick="fullResetApp()">⚠️ RESET</button>
        </div>
        <div class="text-[8px] text-slate-400">KHATA PREMIUM v7.3</div>
    </div>

    <!-- Main App -->
    <div id="mainApp" style="display:none;" class="h-full w-full flex flex-col overflow-hidden">
        
        <!-- Header -->
        <header id="mainHeader" class="header-premium shrink-0 relative z-30" style="background: linear-gradient(135deg, #2e7d32 0%, #1b5e20 100%);">
            <div class="flex items-center justify-between">
                <div class="flex items-center gap-2">
                    <button id="backBtn" onclick="goHome()" class="hidden text-lg text-amber-400 hover:scale-110 transition"><i class="fa-solid fa-arrow-left"></i></button>
                    <button id="memoBackBtn" onclick="closeMemoPage()" class="hidden text-lg text-amber-400 hover:scale-110 transition"><i class="fa-solid fa-arrow-left"></i></button>
                    <button id="vehicleBackBtn" onclick="closeVehiclePage()" class="hidden text-lg text-amber-400 hover:scale-110 transition"><i class="fa-solid fa-arrow-left"></i></button>
                    <button id="incomeBackBtn" onclick="closeIncomeExpensePage()" class="hidden text-lg text-amber-400 hover:scale-110 transition"><i class="fa-solid fa-arrow-left"></i></button>
                    <h1 id="pageTitle" class="text-sm font-black uppercase tracking-wide">KHATA PRO</h1>
                </div>
                <div class="flex gap-1">
                    <button onclick="openIncomeExpensePage('income')" class="w-9 h-9 rounded-xl bg-white/20 flex items-center justify-center text-amber-400 hover:bg-white/30 transition"><i class="fa-solid fa-circle-dollar-to-slot"></i></button>
                    <button onclick="openIncomeExpensePage('expense')" class="w-9 h-9 rounded-xl bg-white/20 flex items-center justify-center text-amber-400 hover:bg-white/30 transition"><i class="fa-solid fa-cart-shopping"></i></button>
                    <button onclick="openMemoPage()" class="w-9 h-9 rounded-xl bg-white/20 flex items-center justify-center text-amber-400 hover:bg-white/30 transition"><i class="fa-regular fa-sticky-note"></i></button>
                    <button onclick="openVehiclePage()" class="w-9 h-9 rounded-xl bg-white/20 flex items-center justify-center text-amber-400 hover:bg-white/30 transition"><i class="fa-solid fa-car"></i></button>
                    <button id="custActionsMenuBtn" onclick="openActionsHubModal()" class="hidden w-9 h-9 rounded-xl bg-white/20 flex items-center justify-center text-amber-400 hover:bg-white/30 transition"><i class="fa-solid fa-bolt"></i></button>
                    <button id="custEditBtn" onclick="openCustModal(activeCid)" class="hidden w-9 h-9 rounded-xl bg-white/20 flex items-center justify-center text-amber-400 hover:bg-white/30 transition"><i class="fa-solid fa-user-pen"></i></button>
                    <button onclick="toggleTheme()" class="w-9 h-9 rounded-xl bg-white/20 flex items-center justify-center text-amber-400 hover:bg-white/30 transition"><i id="themeIcon" class="fa-solid fa-moon"></i></button>
                    <button onclick="openColorSettings()" class="w-9 h-9 rounded-xl bg-white/20 flex items-center justify-center text-amber-400 hover:bg-white/30 transition"><i class="fa-solid fa-palette"></i></button>
                    <button onclick="lockApp()" class="w-9 h-9 rounded-xl bg-white/20 flex items-center justify-center text-amber-400 hover:bg-white/30 transition"><i class="fa-solid fa-lock"></i></button>
                    <button onclick="openSettings()" class="w-9 h-9 rounded-xl bg-white/20 flex items-center justify-center text-amber-400 hover:bg-white/30 transition"><i class="fa-solid fa-gear"></i></button>
                </div>
            </div>
        </header>

        <!-- Main Content -->
        <div class="flex-1 overflow-hidden px-3 py-2">
            
            <!-- Home View -->
            <div id="homeWorkspaceView" class="flex flex-col h-full overflow-hidden">
                <div class="premium-card mb-3 shrink-0">
                    <div class="dashboard-grid">
                        <div class="dashboard-item">
                            <div class="icon text-green-600"><i class="fa-solid fa-wallet"></i></div>
                            <div class="value text-green-800" id="dashTotalBalance">₹0</div>
                            <div class="label text-green-700">Total Balance</div>
                        </div>
                        <div class="dashboard-item">
                            <div class="icon text-amber-600"><i class="fa-solid fa-hand-holding-dollar"></i></div>
                            <div class="value text-amber-800" id="dashPromises">0</div>
                            <div class="label text-amber-700">Promises</div>
                        </div>
                        <div class="dashboard-item">
                            <div class="icon text-blue-600"><i class="fa-solid fa-building-columns"></i></div>
                            <div class="value text-blue-800" id="dashIncome">₹0</div>
                            <div class="label text-blue-700">Income (Month)</div>
                        </div>
                        <div class="dashboard-item">
                            <div class="icon text-red-600"><i class="fa-solid fa-cart-shopping"></i></div>
                            <div class="value text-red-800" id="dashExpense">₹0</div>
                            <div class="label text-red-700">Expense (Month)</div>
                        </div>
                    </div>
                </div>
                <div class="mb-2 shrink-0">
                    <div class="relative">
                        <input type="text" id="searchInput" oninput="searchQuery=this.value;renderClientListFeed()" placeholder="🔍 Search clients..." class="input-premium w-full pl-10 pr-4">
                        <i class="fa-solid fa-magnifying-glass absolute left-3 top-1/2 -translate-y-1/2 opacity-50 text-sm"></i>
                    </div>
                </div>
                <div id="mainClientListContainer" class="flex-1 overflow-y-auto custom-scroll pb-20"></div>
            </div>

            <!-- Ledger View -->
            <div id="ledgerWorkspaceView" class="hidden flex-col h-full overflow-hidden">
                <div id="topArea" class="shrink-0 mb-2"></div>
                <div class="flex items-center gap-2 mb-2 shrink-0 flex-wrap">
                    <div class="flex gap-1 text-[10px] font-black">
                        <button id="typeFilterAll" onclick="setLedgerTypeFilter('ALL')" class="px-3 py-1.5 rounded-xl bg-white shadow text-green-800">All</button>
                        <button id="typeFilterGave" onclick="setLedgerTypeFilter('GAVE')" class="px-3 py-1.5 rounded-xl text-green-700">Gave</button>
                        <button id="typeFilterGot" onclick="setLedgerTypeFilter('GOT')" class="px-3 py-1.5 rounded-xl text-green-700">Got</button>
                    </div>
                    <div class="flex-1 min-w-[80px]">
                        <input type="text" id="ledgerSearchInput" oninput="renderDetails()" placeholder="Filter..." class="w-full rounded-xl py-1.5 px-3 text-xs font-bold border border-green-200 bg-white dark:bg-slate-800 dark:border-slate-600">
                    </div>
                    <button onclick="toggleDateFilterDrawer()" class="w-8 h-8 rounded-xl bg-amber-500/30 flex items-center justify-center text-xs"><i class="fa-solid fa-calendar-alt"></i></button>
                </div>
                <div id="dateFilterDrawer" class="hidden mb-2 p-2 premium-card">
                    <div class="flex items-center justify-between gap-2 flex-wrap">
                        <div class="flex items-center gap-1">
                            <input type="date" id="filterStartDate" onchange="renderDetails()" class="p-1.5 rounded-lg text-[10px] font-bold border border-green-200 dark:border-slate-600 bg-white dark:bg-slate-800">
                            <span class="font-black text-green-700 text-xs">➡</span>
                            <input type="date" id="filterEndDate" onchange="renderDetails()" class="p-1.5 rounded-lg text-[10px] font-bold border border-green-200 dark:border-slate-600 bg-white dark:bg-slate-800">
                        </div>
                        <button onclick="clearDateRangeFilters()" class="text-[9px] font-extrabold bg-red-500/20 px-3 py-1 rounded-lg text-red-600">✖ CLEAR</button>
                    </div>
                </div>
                <div id="dailyRow" class="grid grid-cols-2 gap-2 mb-2 shrink-0"></div>
                <div class="flex-1 overflow-y-auto custom-scroll">
                    <table class="w-full border-collapse">
                        <thead class="sticky top-0 bg-white/90 backdrop-blur dark:bg-slate-800/90">
                            <tr class="text-green-700 dark:text-amber-400 text-[10px] font-black">
                                <th class="p-1 text-left w-[32%]">Date & Note</th>
                                <th class="p-1 text-left w-[22%]">Gave</th>
                                <th class="p-1 text-left w-[22%]">Got</th>
                                <th class="p-1 text-left w-[24%]">Balance</th>
                            </tr>
                        </thead>
                        <tbody id="ledgerItemsRowsContainer"></tbody>
                    </table>
                </div>
            </div>

            <!-- Income / Expense View -->
            <div id="incomeExpenseWorkspaceView" class="hidden flex-col h-full overflow-hidden">
                <div class="flex gap-2 mb-2 shrink-0">
                    <button id="incomeTabBtn" onclick="switchIETab('income')" class="flex-1 py-2.5 rounded-xl font-black text-sm bg-green-600 text-white shadow-md"><i class="fa-solid fa-circle-dollar-to-slot"></i> INCOME</button>
                    <button id="expenseTabBtn" onclick="switchIETab('expense')" class="flex-1 py-2.5 rounded-xl font-black text-sm bg-gray-200 dark:bg-slate-700 text-gray-700 dark:text-gray-300"><i class="fa-solid fa-cart-shopping"></i> EXPENSE</button>
                </div>
                <div id="ieSummaryCard" class="premium-card mb-2 shrink-0">
                    <div class="flex justify-between items-center">
                        <div class="text-center flex-1">
                            <p class="text-[9px] font-bold opacity-70">TOTAL INCOME</p>
                            <h3 id="totalIncomeAmt" class="text-lg font-black text-green-600">₹0</h3>
                        </div>
                        <div class="text-center flex-1 border-x border-green-200 dark:border-slate-600">
                            <p class="text-[9px] font-bold opacity-70">TOTAL EXPENSE</p>
                            <h3 id="totalExpenseAmt" class="text-lg font-black text-red-600">₹0</h3>
                        </div>
                        <div class="text-center flex-1">
                            <p class="text-[9px] font-bold opacity-70">BALANCE</p>
                            <h3 id="totalBalanceAmt" class="text-lg font-black text-blue-600">₹0</h3>
                        </div>
                    </div>
                </div>
                <div class="premium-card mb-2 shrink-0">
                    <div class="flex gap-2 items-center flex-wrap">
                        <div class="flex-1 min-w-[80px]">
                            <input type="date" id="ieFilterDate" class="w-full p-1.5 rounded-lg border text-xs font-bold dark:bg-slate-800 dark:border-slate-600" value="" onchange="renderIncomeExpenseList()">
                        </div>
                        <div class="flex-1 min-w-[80px]">
                            <select id="ieFilterMonth" class="w-full p-1.5 rounded-lg border text-xs font-bold dark:bg-slate-800 dark:border-slate-600" onchange="renderIncomeExpenseList()">
                                <option value="">All Months</option>
                                <option value="2025-01">Jan 2025</option>
                                <option value="2025-02">Feb 2025</option>
                                <option value="2025-03">Mar 2025</option>
                                <option value="2025-04">Apr 2025</option>
                                <option value="2025-05">May 2025</option>
                                <option value="2025-06">Jun 2025</option>
                                <option value="2025-07">Jul 2025</option>
                                <option value="2025-08">Aug 2025</option>
                                <option value="2025-09">Sep 2025</option>
                                <option value="2025-10">Oct 2025</option>
                                <option value="2025-11">Nov 2025</option>
                                <option value="2025-12">Dec 2025</option>
                            </select>
                        </div>
                        <div class="flex-1">
                            <input type="text" id="ieSearchInput" placeholder="Search..." class="w-full p-1.5 rounded-lg border text-xs font-bold dark:bg-slate-800 dark:border-slate-600" oninput="renderIncomeExpenseList()">
                        </div>
                        <button onclick="clearIEFilters()" class="bg-red-500 text-white px-3 py-1.5 rounded-lg text-xs font-bold">✖</button>
                    </div>
                </div>
                <div id="categorySummaryContainer" class="flex flex-wrap gap-1 mb-2 shrink-0 max-h-16 overflow-y-auto"></div>
                <div class="shrink-0 mb-2">
                    <button id="addIeBtn" onclick="openAddIncomeModal()" class="w-full py-2.5 btn-premium"><i class="fa-solid fa-plus"></i> ADD INCOME</button>
                </div>
                <div id="ieListContainer" class="flex-1 overflow-y-auto custom-scroll pb-2 space-y-2"></div>
            </div>

            <!-- Memo View -->
            <div id="memoWorkspaceView" class="hidden flex-col h-full overflow-hidden">
                <div class="flex justify-between items-center mb-3 px-1 shrink-0">
                    <h2 class="text-lg font-black text-green-800 dark:text-amber-400"><i class="fa-regular fa-sticky-note text-purple-500"></i> My Reminders</h2>
                    <button onclick="openAddReminderModal()" class="bg-purple-600 text-white px-4 py-2 rounded-xl shadow-lg action-btn text-sm font-bold">+ Add</button>
                </div>
                <div id="remindersListContainer" class="flex-1 overflow-y-auto custom-scroll pb-2 space-y-2"></div>
            </div>

            <!-- Vehicle View -->
            <div id="vehicleWorkspaceView" class="hidden flex-col h-full overflow-hidden">
                <div class="flex justify-between items-center mb-3 px-1 shrink-0">
                    <h2 class="text-lg font-black text-green-800 dark:text-amber-400"><i class="fa-solid fa-car text-blue-500"></i> Vehicle Expenses</h2>
                    <button onclick="openAddVehicleExpenseModal()" class="bg-blue-600 text-white px-4 py-2 rounded-xl shadow-lg action-btn text-sm font-bold">+ Add</button>
                </div>
                <div class="premium-card mb-2 shrink-0">
                    <p class="text-[10px] font-bold opacity-70">TOTAL EXPENSES</p>
                    <h2 class="text-xl font-black" id="totalVehicleExpense">₹0</h2>
                </div>
                <div id="vehicleExpensesList" class="flex-1 overflow-y-auto custom-scroll pb-2 space-y-2"></div>
            </div>

        </div>

        <!-- Floating Action Button -->
        <button class="fab" onclick="openQuickAddMenu()">
            <i class="fa-solid fa-plus"></i>
        </button>

    </div>

    <!-- Modal Overlay -->
    <div id="modalOverlay" class="fixed inset-0 bg-black/60 backdrop-blur-sm hidden z-[1000] items-center justify-center p-4" onclick="closeModal()">
        <div id="modalBox" class="modal-premium" onclick="event.stopPropagation()"></div>
    </div>

    <script>
        // ==================== DATA LAYER ====================
        const STORAGE_ID = 'KHATA_PRO_PREMIUM_V7';
        let db = JSON.parse(localStorage.getItem(STORAGE_ID)) || { 
            customers: [], trans: [], promises: [], reminders: [], vehicleExpenses: [],
            incomes: [], expenses: [],
            pin: '', upi: '', darkMode: false, theme: 'green' 
        };
        let activeCid = null, currentPinInput = "", searchQuery = "", currentLedgerTypeFilter = "ALL", tempFirstSetupPin = "";
        let currentCalculatorInput = "0";
        let currentIETab = "income";
        let currentQRAmount = 0;
        let reminderCheckInterval = null;

        const saveDB = () => { 
            try {
                localStorage.setItem(STORAGE_ID, JSON.stringify(db)); 
                console.log('Data saved successfully');
                // Removed render() call to prevent infinite loop
                // Only update necessary UI components
                if(document.getElementById('homeWorkspaceView') && !document.getElementById('homeWorkspaceView').classList.contains('hidden')) {
                    renderDashboard();
                    renderClientListFeed();
                }
                if(document.getElementById('memoWorkspaceView') && document.getElementById('memoWorkspaceView').classList.contains('flex')) renderReminders();
                if(document.getElementById('vehicleWorkspaceView') && document.getElementById('vehicleWorkspaceView').classList.contains('flex')) renderVehicleExpenses();
                if(document.getElementById('incomeExpenseWorkspaceView') && document.getElementById('incomeExpenseWorkspaceView').classList.contains('flex')) renderIncomeExpenseList();
                if(activeCid) renderDetails();
            } catch(e) {
                console.error('Save error:', e);
                alert('Data save failed: ' + e.message);
            }
        };
        const getToday = () => new Date().toISOString().split('T')[0];
        const fmtDate = (d) => d ? d.split('-').reverse().join('/') : '';

        // ==================== THEME SYSTEM ====================
        const themeColors = {
            green: { bg: 'linear-gradient(135deg, #2e7d32 0%, #1b5e20 100%)', body: 'theme-green' },
            blue: { bg: 'linear-gradient(135deg, #1e40af 0%, #1e3a8a 100%)', body: 'theme-blue' },
            purple: { bg: 'linear-gradient(135deg, #7c3aed 0%, #6d28d9 100%)', body: 'theme-purple' },
            rose: { bg: 'linear-gradient(135deg, #e11d48 0%, #be123c 100%)', body: 'theme-rose' },
            amber: { bg: 'linear-gradient(135deg, #d97706 0%, #b45309 100%)', body: 'theme-amber' },
            cyan: { bg: 'linear-gradient(135deg, #0891b2 0%, #0e7490 100%)', body: 'theme-cyan' },
            gray: { bg: 'linear-gradient(135deg, #4b5563 0%, #374151 100%)', body: 'theme-gray' }
        };

        function applyTheme(themeName) {
            db.theme = themeName;
            const theme = themeColors[themeName];
            if(!theme) return;
            document.body.className = document.body.className.split(' ').filter(cls => !cls.startsWith('theme-')).join(' ');
            document.body.classList.add(theme.body);
            if(db.darkMode) document.body.classList.add('dark-mode');
            const header = document.getElementById('mainHeader');
            if(header) header.style.background = theme.bg;
            saveDB();
        }

        function toggleTheme() { 
            db.darkMode = !db.darkMode; 
            if(db.darkMode) {
                document.body.classList.add('dark-mode');
                document.getElementById('themeIcon').className = 'fa-solid fa-sun';
            } else {
                document.body.classList.remove('dark-mode');
                document.getElementById('themeIcon').className = 'fa-solid fa-moon';
            }
            saveDB(); 
        }

        function openColorSettings() {
            let html = `<h2 class="font-black text-center text-lg mb-3">🎨 COLOR THEMES</h2><div class="flex flex-wrap gap-3 justify-center mb-4">`;
            for(const [key, value] of Object.entries(themeColors)) {
                const active = db.theme === key ? 'active' : '';
                html += `<div class="color-option ${active}" style="background: ${value.bg};" onclick="selectTheme('${key}')" title="${key.charAt(0).toUpperCase() + key.slice(1)}"></div>`;
            }
            html += `</div><button class="w-full p-2 bg-gray-600 text-white rounded-lg font-bold action-btn text-sm" onclick="closeModal()">Close</button>`;
            openModal(html);
        }

        function selectTheme(theme) {
            applyTheme(theme);
            closeModal();
        }

        // ==================== LOCK SCREEN ====================
        function pressKey(n) { if(currentPinInput.length < 4) { currentPinInput += n; updateDots(); if(currentPinInput.length === 4) setTimeout(checkPin, 150); } }
        function clearCurrentPin() { currentPinInput = ""; updateDots(); }
        function updateDots() { for(let i=0;i<4;i++){ const el=document.getElementById(`dot-${i}`); if(el) { if(i<currentPinInput.length){ el.className = 'lock-dot.active'; } else { el.className = 'lock-dot'; } } } }
        function checkPin() {
            if(!db.pin || db.pin === '') {
                if(!tempFirstSetupPin) { 
                    tempFirstSetupPin = currentPinInput; 
                    currentPinInput = ""; 
                    updateDots(); 
                    document.getElementById('lockScreenSubtitle').innerText = "✅ Confirm new PIN"; 
                    return; 
                } else { 
                    if(currentPinInput === tempFirstSetupPin) { 
                        db.pin = currentPinInput; 
                        tempFirstSetupPin = ""; 
                        saveDB(); 
                        alert("✅ Secure PIN Activated"); 
                        document.getElementById('lockScreen').style.display = 'none'; 
                        document.getElementById('mainApp').style.display = 'flex'; 
                        requestNotificationPermission(); 
                        startReminderChecker(); 
                        renderAll(); 
                    } else { 
                        alert("❌ PIN mismatch"); 
                        tempFirstSetupPin = ""; 
                        currentPinInput = ""; 
                        updateDots(); 
                        document.getElementById('lockScreenSubtitle').innerText = "Create 4-digit PIN"; 
                    } 
                    return; 
                }
            }
            if(currentPinInput === db.pin) { 
                document.getElementById('lockScreen').style.display = 'none'; 
                document.getElementById('mainApp').style.display = 'flex'; 
                requestNotificationPermission(); 
                startReminderChecker(); 
                renderAll(); 
            } else { 
                alert("⛔ Invalid PIN"); 
                currentPinInput = ""; 
                updateDots(); 
            }
        }
        function lockApp() { 
            currentPinInput = ""; 
            updateDots(); 
            document.getElementById('lockScreen').style.display = 'flex'; 
            document.getElementById('mainApp').style.display = 'none'; 
            const sub = document.getElementById('lockScreenSubtitle'); 
            if(!db.pin || db.pin === '') sub.innerText = "✨ Create 4-digit Master PIN"; 
            else sub.innerText = "🔒 Enter PIN to unlock"; 
        }
        function fullResetApp() { 
            if(confirm("⚠️ PERMANENT DELETE all data?")) { 
                localStorage.removeItem(STORAGE_ID); 
                location.reload(); 
            } 
        }

        // ==================== NOTIFICATIONS ====================
        function requestNotificationPermission() { if ('Notification' in window && Notification.permission !== 'granted' && Notification.permission !== 'denied') Notification.requestPermission(); }
        function checkReminderAlerts() {
            if (!db.reminders) return;
            const today = new Date(); today.setHours(0,0,0,0);
            db.reminders.forEach(rem => {
                if (rem.alertSent) return;
                const dueDate = new Date(rem.dueDate); dueDate.setHours(0,0,0,0);
                const daysLeft = Math.ceil((dueDate - today) / (1000*60*60*24));
                if (daysLeft <= rem.reminderDays && daysLeft >= 0) {
                    if ('Notification' in window && Notification.permission === 'granted') new Notification('🔔 KHATA PRO Reminder', { body: `${rem.title}\nDue in ${daysLeft} days!` });
                    rem.alertSent = true;
                    saveDB();
                }
            });
        }
        function startReminderChecker() { if (reminderCheckInterval) clearInterval(reminderCheckInterval); reminderCheckInterval = setInterval(() => { if (document.getElementById('mainApp').style.display === 'flex') checkReminderAlerts(); }, 60000); }

        // ==================== QUICK ADD FAB ====================
        function openQuickAddMenu() {
            openModal(`
                <h2 class="font-black text-center text-lg mb-4">⚡ Quick Add</h2>
                <div class="grid grid-cols-2 gap-3">
                    <button onclick="closeModal();openCustModal()" class="btn-premium py-3 text-sm"><i class="fa-solid fa-user-plus"></i> Client</button>
                    <button onclick="closeModal();openAdd('GAVE')" class="btn-premium py-3 text-sm bg-rose-600"><i class="fa-solid fa-hand-holding-dollar"></i> Gave</button>
                    <button onclick="closeModal();openAdd('GOT')" class="btn-premium py-3 text-sm bg-emerald-600"><i class="fa-solid fa-receipt"></i> Got</button>
                    <button onclick="closeModal();openAddIncomeModal()" class="btn-premium py-3 text-sm bg-green-600"><i class="fa-solid fa-circle-dollar-to-slot"></i> Income</button>
                    <button onclick="closeModal();openAddExpenseModal()" class="btn-premium py-3 text-sm bg-red-600"><i class="fa-solid fa-cart-shopping"></i> Expense</button>
                    <button onclick="closeModal();openAddReminderModal()" class="btn-premium py-3 text-sm bg-purple-600"><i class="fa-regular fa-sticky-note"></i> Reminder</button>
                </div>
                <button class="w-full mt-3 text-slate-500 text-sm" onclick="closeModal()">Cancel</button>
            `);
        }

        // ==================== MODAL ====================
        function openModal(html) { document.getElementById('modalBox').innerHTML = html; document.getElementById('modalOverlay').style.display = 'flex'; }
        function closeModal() { document.getElementById('modalOverlay').style.display = 'none'; }

        // ==================== NAVIGATION ====================
        function goHome() { activeCid=null; document.getElementById('backBtn').classList.add('hidden'); document.getElementById('custEditBtn').classList.add('hidden'); document.getElementById('custActionsMenuBtn').classList.add('hidden'); document.getElementById('pageTitle').innerText="KHATA PRO"; document.getElementById('ledgerWorkspaceView').classList.add('hidden'); document.getElementById('homeWorkspaceView').classList.remove('hidden'); renderClientListFeed(); }
        function openCustomer(id) { activeCid=id; currentLedgerTypeFilter="ALL"; document.getElementById('homeWorkspaceView').classList.add('hidden'); document.getElementById('ledgerWorkspaceView').classList.remove('hidden'); document.getElementById('ledgerWorkspaceView').classList.add('flex'); renderDetails(); renderDashboard(); }

        // ==================== DASHBOARD ====================
        function renderDashboard() {
            let totalBal = 0;
            db.trans.forEach(t => totalBal += (t.type === 'GAVE' ? t.amt : -t.amt));
            document.getElementById('dashTotalBalance').innerText = '₹' + Math.abs(totalBal).toFixed(0);
            document.getElementById('dashPromises').innerText = db.promises.length;
            const now = new Date();
            const month = now.getMonth();
            const year = now.getFullYear();
            let monthIncome = 0, monthExpense = 0;
            (db.incomes || []).forEach(i => {
                const d = new Date(i.date);
                if(d.getMonth() === month && d.getFullYear() === year) monthIncome += i.amount;
            });
            (db.expenses || []).forEach(e => {
                const d = new Date(e.date);
                if(d.getMonth() === month && d.getFullYear() === year) monthExpense += e.amount;
            });
            document.getElementById('dashIncome').innerText = '₹' + monthIncome.toFixed(0);
            document.getElementById('dashExpense').innerText = '₹' + monthExpense.toFixed(0);
        }

        // ==================== CORE RENDER ====================
        function renderAll() { 
            if(db.theme) applyTheme(db.theme);
            if(db.darkMode) document.body.classList.add('dark-mode');
            else document.body.classList.remove('dark-mode');
            document.getElementById('themeIcon').className = db.darkMode ? 'fa-solid fa-sun' : 'fa-solid fa-moon'; 
            renderDashboard();
            renderClientListFeed(); 
            if(activeCid) renderDetails(); 
        }

        // ==================== CLIENT LIST ====================
        function renderClientListFeed() { 
            let filtered = db.customers.filter(c => c.name.toLowerCase().includes(searchQuery.toLowerCase()) || (c.phone && c.phone.includes(searchQuery))).sort((a,b) => a.name.localeCompare(b.name)); 
            let html = ""; 
            filtered.forEach(c => { 
                let bal = 0; 
                db.trans.filter(t => t.cid === c.id).forEach(t => bal += (t.type === 'GAVE' ? t.amt : -t.amt)); 
                html += `
                    <div class="client-item" onclick="openCustomer(${c.id})">
                        <div class="client-avatar">${c.name[0].toUpperCase()}</div>
                        <div class="flex-1 ml-3">
                            <p class="font-black text-sm">${c.name}</p>
                            <p class="text-[10px] font-bold text-green-600 dark:text-amber-400">${c.phone || '—'}</p>
                        </div>
                        <div class="text-right">
                            <p class="font-black text-sm ${bal >= 0 ? 'text-rose-600' : 'text-emerald-600'}">₹${Math.abs(bal).toFixed(0)}</p>
                            <span class="text-[8px] font-black uppercase ${bal >= 0 ? 'text-rose-500' : 'text-emerald-500'}">${bal >= 0 ? 'Gave' : 'Got'}</span>
                        </div>
                    </div>
                `; 
            }); 
            document.getElementById('mainClientListContainer').innerHTML = html || `<div class="text-center text-green-500 dark:text-amber-400 py-8 text-sm font-bold">🤝 No clients yet.</div>`; 
        }

        // ==================== LEDGER DETAILS ====================
        function renderDetails() { 
            const cust = db.customers.find(c => c.id === activeCid); 
            if(!cust){ goHome(); return; } 
            document.getElementById('backBtn').classList.remove('hidden'); 
            document.getElementById('custEditBtn').classList.remove('hidden'); 
            document.getElementById('custActionsMenuBtn').classList.remove('hidden'); 
            document.getElementById('pageTitle').innerText = cust.name; 
            let rb = 0, cashToday = 0, upiToday = 0, mGave = 0, mGot = 0; 
            const today = getToday(); 
            const now = new Date(); 
            const currentMonth = now.getMonth(); 
            const currentYear = now.getFullYear(); 
            let trans = db.trans.filter(t => t.cid === activeCid).sort((a,b) => new Date(a.date) - new Date(b.date)); 
            let cumulative = 0; 
            trans.forEach(t => { cumulative += (t.type === 'GAVE' ? t.amt : -t.amt); rb = cumulative; }); 
            trans.forEach(t => { 
                const tDate = new Date(t.date); 
                if (tDate.getMonth() === currentMonth && tDate.getFullYear() === currentYear) { 
                    if (t.type === 'GAVE') mGave += t.amt; else mGot += t.amt; 
                } 
                if (t.date === today && t.type === 'GOT') { 
                    if (t.mode === 'CASH') cashToday += t.amt; 
                    if (t.mode === 'UPI') upiToday += t.amt; 
                } 
            }); 
            const mNet = mGave - mGot; 
            const ledSearch = document.getElementById('ledgerSearchInput')?.value.toLowerCase() || ""; 
            const sDate = document.getElementById('filterStartDate')?.value || ""; 
            const eDate = document.getElementById('filterEndDate')?.value || ""; 
            let filteredTrans = trans.filter(t => { 
                if(currentLedgerTypeFilter !== 'ALL' && t.type !== currentLedgerTypeFilter) return false; 
                if(sDate && t.date < sDate) return false; 
                if(eDate && t.date > eDate) return false; 
                if(ledSearch && !t.rem.toLowerCase().includes(ledSearch) && !t.amt.toString().includes(ledSearch)) return false; 
                return true; 
            }); 
            let running = 0, rowsArray = []; 
            filteredTrans.forEach(t => { 
                running += (t.type === 'GAVE' ? t.amt : -t.amt); 
                const row = `
                    <tr class="border-b border-green-100 dark:border-slate-700 hover:bg-green-50 dark:hover:bg-slate-800 cursor-pointer" onclick="openEditTrans(${t.id})">
                        <td class="p-1 text-[11px] font-bold">
                            <div>
                                <div class="flex items-center">
                                    <span class="font-black text-green-800 dark:text-amber-400">${fmtDate(t.date)}</span>
                                    <span class="ml-1 px-1 py-0.5 rounded-full text-[8px] font-black ${t.mode === 'UPI' ? 'bg-blue-100 dark:bg-blue-900 text-blue-700 dark:text-blue-300' : 'bg-emerald-100 dark:bg-emerald-900 text-emerald-700 dark:text-emerald-300'}">${t.mode || 'CASH'}</span>
                                </div>
                                ${t.time ? `<span class="text-[9px] font-bold text-gray-500 dark:text-gray-400">${t.time}</span>` : ''}
                                <span class="text-green-600 dark:text-amber-400 text-[9px] font-bold block mt-0.5">${t.rem || '—'}</span>
                            </div>
                        </td>
                        <td class="p-1 text-rose-600 dark:text-rose-400 font-black text-sm">${t.type === 'GAVE' ? '₹'+t.amt.toFixed(0) : '-'}</td>
                        <td class="p-1 text-emerald-600 dark:text-emerald-400 font-black text-sm">${t.type === 'GOT' ? '₹'+t.amt.toFixed(0) : '-'}</td>
                        <td class="p-1 ${running >= 0 ? 'text-rose-600 dark:text-rose-400' : 'text-emerald-600 dark:text-emerald-400'} font-black text-sm">₹${Math.abs(running).toFixed(0)}</td>
                    </tr>
                `; 
                rowsArray.unshift(row); 
            }); 
            document.getElementById('topArea').innerHTML = `
                <div class="premium-card text-center">
                    <p class="text-[8px] font-black opacity-70 uppercase">${rb >= 0 ? "📌 OUTSTANDING" : "⚡ ADVANCE"}</p>
                    <h2 class="text-xl font-black mt-0.5">₹${Math.abs(rb).toFixed(2)}</h2>
                    <div class="grid grid-cols-3 gap-2 mt-2">
                        <div class="bg-green-100 dark:bg-green-900/30 rounded-lg p-1">
                            <div class="text-[8px] font-black text-green-700 dark:text-green-300">MONTH GAVE</div>
                            <div class="text-sm font-black text-rose-700 dark:text-rose-400">₹${mGave.toFixed(0)}</div>
                        </div>
                        <div class="bg-green-100 dark:bg-green-900/30 rounded-lg p-1">
                            <div class="text-[8px] font-black text-green-700 dark:text-green-300">MONTH GOT</div>
                            <div class="text-sm font-black text-emerald-700 dark:text-emerald-400">₹${mGot.toFixed(0)}</div>
                        </div>
                        <div class="bg-green-100 dark:bg-green-900/30 rounded-lg p-1">
                            <div class="text-[8px] font-black text-green-700 dark:text-green-300">NET</div>
                            <div class="text-sm font-black ${mNet >= 0 ? 'text-rose-700 dark:text-rose-400' : 'text-emerald-700 dark:text-emerald-400'}">₹${Math.abs(mNet).toFixed(0)}</div>
                        </div>
                    </div>
                </div>
            `; 
            document.getElementById('dailyRow').innerHTML = `
                <div class="premium-card text-center">
                    <div class="text-[9px] font-black text-green-700 dark:text-amber-400"><i class="fa-solid fa-money-bill-wave"></i> CASH TODAY</div>
                    <div class="text-xl font-black text-green-800 dark:text-amber-400">₹${cashToday.toFixed(0)}</div>
                </div>
                <div class="premium-card text-center">
                    <div class="text-[9px] font-black text-green-700 dark:text-amber-400"><i class="fa-solid fa-mobile-alt"></i> UPI TODAY</div>
                    <div class="text-xl font-black text-green-800 dark:text-amber-400">₹${upiToday.toFixed(0)}</div>
                </div>
            `; 
            document.getElementById('ledgerItemsRowsContainer').innerHTML = rowsArray.length ? rowsArray.join('') : `<tr><td colspan="4" class="text-center py-8 opacity-50 text-green-500 dark:text-amber-400 text-xs font-black">📭 No records</td></tr>`; 
        }

        // ==================== TRANSACTIONS ====================
        function openAdd(type) { 
            const timeStr = new Date().toLocaleTimeString([],{hour:'2-digit',minute:'2-digit',hour12:true}); 
            openModal(`
                <h2 class="font-black text-center text-lg mb-3">${type === 'GAVE' ? '📤 GAVE MONEY' : '📥 GOT MONEY'}</h2>
                <div class="space-y-3">
                    <div class="relative">
                        <input id="ta" type="number" step="0.01" class="w-full p-4 text-2xl text-center font-black rounded-xl border input-premium" placeholder="₹ 0" autofocus>
                        <button onclick="openCalculator()" class="absolute right-2 top-1/2 transform -translate-y-1/2 bg-amber-500 text-black p-2 rounded-xl shadow-lg"><i class="fa-solid fa-calculator text-base"></i></button>
                    </div>
                    <div class="flex gap-2">
                        <button id="mCash" onclick="setM('CASH')" class="flex-1 py-2 rounded-lg border font-black text-green-700 dark:text-amber-400 text-sm">💵 CASH</button>
                        <button id="mUpi" onclick="setM('UPI')" class="flex-1 py-2 rounded-lg border font-black text-green-700 dark:text-amber-400 text-sm">📲 UPI</button>
                    </div>
                    <input id="tr" class="w-full p-2 rounded-lg border input-premium text-sm" placeholder="Remarks / Notes">
                    <div class="grid grid-cols-2 gap-2">
                        <input id="td" type="date" class="p-2 rounded-lg border input-premium text-sm" value="${getToday()}">
                        <input id="tt" type="text" class="p-2 rounded-lg border input-premium text-sm" value="${timeStr}">
                    </div>
                    <input type="hidden" id="tm" value="CASH">
                    <button class="w-full py-3 bg-blue-600 text-white font-black rounded-xl text-base shadow-lg action-btn" onclick="saveTrans('${type}')">✅ SAVE</button>
                    <button class="w-full py-2 text-green-500 font-bold text-sm" onclick="closeModal()">Cancel</button>
                </div>
            `); 
            setM('CASH'); 
        }
        function setM(m) { 
            document.getElementById('tm').value = m; 
            const cashBtn = document.getElementById('mCash'), upiBtn = document.getElementById('mUpi'); 
            if(m === 'CASH') { 
                if(cashBtn) cashBtn.className = 'flex-1 py-2 rounded-lg bg-amber-400 text-black font-black shadow-md text-sm'; 
                if(upiBtn) upiBtn.className = 'flex-1 py-2 rounded-lg bg-gray-200 dark:bg-slate-700 text-slate-700 dark:text-slate-300 font-bold text-sm'; 
            } else { 
                if(cashBtn) cashBtn.className = 'flex-1 py-2 rounded-lg bg-gray-200 dark:bg-slate-700 text-slate-700 dark:text-slate-300 font-bold text-sm'; 
                if(upiBtn) upiBtn.className = 'flex-1 py-2 rounded-lg bg-blue-600 text-white font-black shadow-md text-sm'; 
            } 
        }
        function saveTrans(type) { 
            let a = parseFloat(document.getElementById('ta').value); 
            if(isNaN(a) || a <= 0) return alert("Please enter valid amount"); 
            let d = document.getElementById('td').value, r = document.getElementById('tr').value.trim(), m = document.getElementById('tm').value, t = document.getElementById('tt').value; 
            if(a && d) { 
                db.trans.push({id:Date.now(), cid:activeCid, type, amt:a, date:d, time:t, rem:r, mode:m}); 
                saveDB(); 
                closeModal(); 
            } 
        }
        function openEditTrans(tid) { 
            const t = db.trans.find(x => x.id === tid); 
            openModal(`
                <h2 class="font-black text-center text-lg">✏️ EDIT ENTRY</h2>
                <div class="space-y-3">
                    <input id="eta" type="number" step="0.01" class="w-full p-4 text-2xl text-center font-black rounded-xl border input-premium" value="${t.amt}">
                    <input id="etr" class="w-full mt-2 p-2 rounded-lg border input-premium text-sm" value="${t.rem || ''}" placeholder="Remarks">
                    <div class="grid grid-cols-2 gap-2 mt-2">
                        <input value="${t.date}" disabled class="p-2 bg-gray-100 dark:bg-slate-700 rounded-lg text-sm">
                        <input value="${t.time || ''}" disabled class="p-2 bg-gray-100 dark:bg-slate-700 rounded-lg text-sm">
                    </div>
                    <button class="w-full mt-2 p-2 bg-blue-600 text-white font-black rounded-lg action-btn text-sm" onclick="updateTrans(${tid})">UPDATE</button>
                    <button class="w-full mt-2 p-2 bg-red-600 text-white rounded-lg action-btn text-sm" onclick="deleteTrans(${tid})">DELETE</button>
                    <button class="w-full mt-1 text-slate-400 text-xs" onclick="closeModal()">Cancel</button>
                </div>
            `); 
        }
        function updateTrans(tid) { 
            let t = db.trans.find(x => x.id === tid); 
            t.amt = Number(document.getElementById('eta').value); 
            t.rem = document.getElementById('etr').value.trim(); 
            saveDB(); 
            closeModal(); 
        }
        function deleteTrans(tid) { 
            if(confirm("Delete entry?")) { 
                db.trans = db.trans.filter(x => x.id !== tid); 
                saveDB(); 
                closeModal(); 
            } 
        }
        function setLedgerTypeFilter(f) { 
            currentLedgerTypeFilter = f; 
            ['ALL','GAVE','GOT'].forEach(lbl => { 
                const btn = document.getElementById(`typeFilter${lbl}`); 
                if(btn) btn.className = lbl === f ? 'px-3 py-1.5 rounded-xl bg-white shadow text-green-800 dark:bg-slate-700 dark:text-amber-400 text-[10px] font-black' : 'px-3 py-1.5 rounded-xl text-green-700 dark:text-slate-400 text-[10px] font-black'; 
            }); 
            renderDetails(); 
        }
        function toggleDateFilterDrawer() { document.getElementById('dateFilterDrawer').classList.toggle('hidden'); }
        function clearDateRangeFilters() { document.getElementById('filterStartDate').value = ''; document.getElementById('filterEndDate').value = ''; renderDetails(); }

        // ==================== CLIENT CRUD ====================
        function openCustModal(cid=null) { 
            const c = cid ? db.customers.find(x => x.id === cid) : {name:'', phone:''}; 
            openModal(`
                <h2 class="text-lg font-black mb-3 text-center">${cid ? '✏️ EDIT CLIENT' : '🌟 ADD CLIENT'}</h2>
                <div class="space-y-3">
                    <input id="cn" class="w-full p-3 rounded-xl font-bold border input-premium text-sm" placeholder="Full Name" value="${c.name}">
                    <input id="cp" type="tel" class="w-full p-3 rounded-xl font-bold border input-premium text-sm" placeholder="Phone Number" value="${c.phone || ''}">
                    <button class="w-full p-3 bg-emerald-600 text-white font-black rounded-xl action-btn text-sm" onclick="saveCust(${cid})">💾 SAVE PROFILE</button>
                    <button class="w-full text-xs opacity-70 text-green-600 dark:text-amber-400" onclick="closeModal()">Cancel</button>
                    ${cid ? `<div class="pt-1"><button class="w-full p-2 bg-rose-600/20 text-rose-600 dark:text-rose-400 rounded-lg font-bold text-sm" onclick="deleteFullCust(${cid})">🗑️ DELETE CLIENT</button></div>` : ''}
                </div>
            `); 
        }
        function saveCust(cid) { 
            let n = document.getElementById('cn').value.trim(), p = document.getElementById('cp').value.trim(); 
            if(!n) return alert("Name required"); 
            if(cid) { 
                let c = db.customers.find(x => x.id === cid); 
                c.name = n; 
                c.phone = p; 
            } else { 
                const newId = Date.now(); 
                db.customers.push({id:newId, name:n, phone:p}); 
                activeCid = newId; 
            } 
            saveDB(); 
            closeModal(); 
            openCustomer(activeCid); 
        }
        function deleteFullCust(cid) { 
            if(confirm("DELETE all data of this client?")) { 
                db.customers = db.customers.filter(x => x.id !== cid); 
                db.trans = db.trans.filter(x => x.cid !== cid); 
                db.promises = db.promises.filter(x => x.cid !== cid); 
                activeCid = null; 
                saveDB(); 
                closeModal(); 
                goHome(); 
            } 
        }

        // ==================== PROMISES ====================
        function openPromiseModal() { 
            openModal(`
                <h2 class="font-black text-center text-base">📅 Promise to Pay</h2>
                <div class="space-y-3 mt-2">
                    <input id="pa" type="number" class="w-full p-3 rounded-lg border input-premium text-xl text-center font-black" placeholder="Amount">
                    <input id="pd" type="date" class="w-full p-2 rounded-lg border input-premium text-sm" value="${getToday()}">
                    <button class="w-full p-2 bg-indigo-600 text-white font-black rounded-lg action-btn text-sm" onclick="savePromise()">Set Promise</button>
                    <button class="w-full text-green-500 dark:text-amber-400 text-sm" onclick="closeModal()">Cancel</button>
                </div>
            `); 
        }
        function savePromise() { 
            let a = document.getElementById('pa').value, d = document.getElementById('pd').value; 
            if(a && d) { 
                db.promises.push({id:Date.now(), cid:activeCid, amt:a, date:d}); 
                saveDB(); 
                closeModal(); 
            } 
        }
        function settlePromise(id) { 
            const p = db.promises.find(x => x.id === id); 
            const timeStr = new Date().toLocaleTimeString(); 
            db.trans.push({id:Date.now(), cid:p.cid, type:'GOT', amt:Number(p.amt), date:getToday(), time:timeStr, mode:'CASH', rem:'Promise settled'}); 
            db.promises = db.promises.filter(x => x.id !== id); 
            saveDB(); 
        }
        function deletePromise(id) { 
            if(confirm("Delete promise?")) { 
                db.promises = db.promises.filter(x => x.id !== id); 
                saveDB(); 
            } 
        }

        // ==================== INCOME & EXPENSE ====================
        function openIncomeExpensePage(tab) { 
            currentIETab = tab; 
            document.getElementById('homeWorkspaceView').classList.add('hidden'); 
            document.getElementById('ledgerWorkspaceView').classList.add('hidden'); 
            document.getElementById('memoWorkspaceView').classList.add('hidden'); 
            document.getElementById('vehicleWorkspaceView').classList.add('hidden'); 
            document.getElementById('incomeExpenseWorkspaceView').classList.remove('hidden'); 
            document.getElementById('incomeExpenseWorkspaceView').classList.add('flex'); 
            document.getElementById('backBtn').classList.add('hidden'); 
            document.getElementById('custEditBtn').classList.add('hidden'); 
            document.getElementById('custActionsMenuBtn').classList.add('hidden'); 
            document.getElementById('memoBackBtn').classList.add('hidden'); 
            document.getElementById('vehicleBackBtn').classList.add('hidden'); 
            document.getElementById('incomeBackBtn').classList.remove('hidden'); 
            document.getElementById('pageTitle').innerText = tab === 'income' ? "💰 INCOME" : "💸 EXPENSE"; 
            document.getElementById('ieFilterDate').value = getToday(); 
            switchIETab(tab); 
            renderIncomeExpenseList(); 
        }
        function closeIncomeExpensePage() { 
            document.getElementById('incomeExpenseWorkspaceView').classList.add('hidden'); 
            document.getElementById('homeWorkspaceView').classList.remove('hidden'); 
            document.getElementById('incomeBackBtn').classList.add('hidden'); 
            document.getElementById('pageTitle').innerText = "KHATA PRO"; 
            renderClientListFeed(); 
        }
        function switchIETab(tab) { 
            currentIETab = tab; 
            const incomeBtn = document.getElementById('incomeTabBtn'), expenseBtn = document.getElementById('expenseTabBtn'), addBtn = document.getElementById('addIeBtn'); 
            if(tab === 'income') { 
                incomeBtn.className = "flex-1 py-2.5 rounded-xl font-black text-sm bg-green-600 text-white shadow-md"; 
                expenseBtn.className = "flex-1 py-2.5 rounded-xl font-black text-sm bg-gray-200 dark:bg-slate-700 text-gray-700 dark:text-gray-300"; 
                addBtn.innerHTML = '<i class="fa-solid fa-plus"></i> ADD INCOME'; 
                addBtn.onclick = () => openAddIncomeModal(); 
                document.getElementById('pageTitle').innerText = "💰 INCOME"; 
            } else { 
                incomeBtn.className = "flex-1 py-2.5 rounded-xl font-black text-sm bg-gray-200 dark:bg-slate-700 text-gray-700 dark:text-gray-300"; 
                expenseBtn.className = "flex-1 py-2.5 rounded-xl font-black text-sm bg-red-600 text-white shadow-md"; 
                addBtn.innerHTML = '<i class="fa-solid fa-plus"></i> ADD EXPENSE'; 
                addBtn.onclick = () => openAddExpenseModal(); 
                document.getElementById('pageTitle').innerText = "💸 EXPENSE"; 
            } 
            renderIncomeExpenseList(); 
        }
        function getFilteredIEEntries() { 
            const selectedDate = document.getElementById('ieFilterDate')?.value || "", selectedMonth = document.getElementById('ieFilterMonth')?.value || "", searchText = document.getElementById('ieSearchInput')?.value.toLowerCase() || ""; 
            let incomes = [...(db.incomes || [])], expenses = [...(db.expenses || [])]; 
            if(selectedDate) { incomes = incomes.filter(i => i.date === selectedDate); expenses = expenses.filter(e => e.date === selectedDate); } 
            if(selectedMonth) { incomes = incomes.filter(i => i.date.startsWith(selectedMonth)); expenses = expenses.filter(e => e.date.startsWith(selectedMonth)); } 
            if(searchText) { incomes = incomes.filter(i => i.category.toLowerCase().includes(searchText) || (i.notes || "").toLowerCase().includes(searchText)); expenses = expenses.filter(e => e.category.toLowerCase().includes(searchText) || (e.notes || "").toLowerCase().includes(searchText)); } 
            return { incomes, expenses }; 
        }
        function renderIncomeExpenseList() { 
            const { incomes, expenses } = getFilteredIEEntries(); 
            const totalIncome = incomes.reduce((s,i) => s + i.amount, 0); 
            const totalExpense = expenses.reduce((s,e) => s + e.amount, 0); 
            const balance = totalIncome - totalExpense; 
            document.getElementById('totalIncomeAmt').innerHTML = `₹${totalIncome.toFixed(2)}`; 
            document.getElementById('totalExpenseAmt').innerHTML = `₹${totalExpense.toFixed(2)}`; 
            document.getElementById('totalBalanceAmt').innerHTML = `₹${Math.abs(balance).toFixed(2)}`; 
            const categoryMap = new Map(); 
            if(currentIETab === 'income') incomes.forEach(inc => categoryMap.set(inc.category, (categoryMap.get(inc.category)||0) + inc.amount)); 
            else expenses.forEach(exp => categoryMap.set(exp.category, (categoryMap.get(exp.category)||0) + exp.amount)); 
            let categoryHtml = ''; 
            categoryMap.forEach((amt, cat) => categoryHtml += `<span class="inline-block px-2 py-0.5 rounded-full text-[9px] font-bold bg-green-100 dark:bg-slate-700 text-green-700 dark:text-amber-400">${cat}: ₹${amt.toFixed(0)}</span>`); 
            document.getElementById('categorySummaryContainer').innerHTML = categoryHtml || `<span class="text-[10px] text-gray-400 dark:text-gray-500 font-bold">No categories</span>`; 
            let html = ''; 
            if(currentIETab === 'income') { 
                [...incomes].sort((a,b) => new Date(b.date) - new Date(a.date)).forEach(inc => { 
                    html += `
                        <div class="premium-card flex justify-between items-start cursor-pointer" onclick="openEditIncomeModal(${inc.id})">
                            <div class="flex-1">
                                <div class="flex items-center gap-2 mb-1">
                                    <span class="text-base text-green-600"><i class="fa-solid ${inc.icon || 'fa-circle-dollar-to-slot'}"></i></span>
                                    <span class="font-black text-green-800 dark:text-amber-400 text-sm">${inc.category}</span>
                                </div>
                                <p class="text-xs font-bold text-gray-600 dark:text-gray-400">${inc.notes || '—'}</p>
                                <div class="flex gap-2 mt-1 text-[10px] font-bold text-gray-400 dark:text-gray-500">
                                    <span><i class="fa-regular fa-calendar"></i> ${fmtDate(inc.date)}</span>
                                </div>
                            </div>
                            <div class="text-right">
                                <p class="font-black text-base text-green-600">+ ₹${inc.amount.toFixed(2)}</p>
                                <button onclick="event.stopPropagation();deleteIncomeEntry(${inc.id})" class="mt-1 text-gray-400 hover:text-red-500 dark:hover:text-red-400 text-xs"><i class="fa-solid fa-trash"></i></button>
                            </div>
                        </div>
                    `; 
                }); 
            } else { 
                [...expenses].sort((a,b) => new Date(b.date) - new Date(a.date)).forEach(exp => { 
                    html += `
                        <div class="premium-card flex justify-between items-start cursor-pointer" onclick="openEditExpenseModal(${exp.id})">
                            <div class="flex-1">
                                <div class="flex items-center gap-2 mb-1">
                                    <span class="text-base text-red-600"><i class="fa-solid ${exp.icon || 'fa-cart-shopping'}"></i></span>
                                    <span class="font-black text-red-800 dark:text-red-400 text-sm">${exp.category}</span>
                                </div>
                                <p class="text-xs font-bold text-gray-600 dark:text-gray-400">${exp.notes || '—'}</p>
                                <div class="flex gap-2 mt-1 text-[10px] font-bold text-gray-400 dark:text-gray-500">
                                    <span><i class="fa-regular fa-calendar"></i> ${fmtDate(exp.date)}</span>
                                </div>
                            </div>
                            <div class="text-right">
                                <p class="font-black text-base text-red-600">- ₹${exp.amount.toFixed(2)}</p>
                                <button onclick="event.stopPropagation();deleteExpenseEntry(${exp.id})" class="mt-1 text-gray-400 hover:text-red-500 dark:hover:text-red-400 text-xs"><i class="fa-solid fa-trash"></i></button>
                            </div>
                        </div>
                    `; 
                }); 
            } 
            document.getElementById('ieListContainer').innerHTML = html || `<div class="text-center text-gray-400 dark:text-gray-500 py-8 text-sm font-bold"><i class="fa-solid fa-${currentIETab === 'income' ? 'circle-dollar-to-slot' : 'cart-shopping'} text-3xl mb-2"></i><p>No ${currentIETab} records.<br>Click ADD!</p></div>`; 
        }
        function clearIEFilters() { document.getElementById('ieFilterDate').value = ''; document.getElementById('ieFilterMonth').value = ''; document.getElementById('ieSearchInput').value = ''; renderIncomeExpenseList(); }
        function openAddIncomeModal() { openModal(`<h2 class="font-black text-center text-lg mb-3"><i class="fa-solid fa-circle-dollar-to-slot text-green-500"></i> Add Income</h2><div class="space-y-3"><div><label class="text-xs font-bold">Amount</label><input id="ieAmount" type="number" step="0.01" class="w-full p-3 text-xl text-center font-black rounded-xl border input-premium" placeholder="₹ 0"></div><div><label class="text-xs font-bold">Category</label><select id="ieCategory" class="w-full p-2 rounded-xl border input-premium text-sm"><option value="Salary">💰 Salary</option><option value="Business">🏪 Business</option><option value="Rent">🏠 Rent</option><option value="Investment">📈 Investment</option><option value="Gift">🎁 Gift</option><option value="Other">📌 Other</option></select></div><div><label class="text-xs font-bold">Date</label><input id="ieDate" type="date" class="w-full p-2 rounded-xl border input-premium text-sm" value="${getToday()}"></div><div><label class="text-xs font-bold">Notes</label><textarea id="ieNotes" class="w-full p-2 rounded-xl border input-premium text-sm" rows="2" placeholder="Additional details..."></textarea></div><button class="w-full p-2.5 bg-green-600 text-white font-black rounded-xl action-btn text-sm" onclick="saveIncomeEntry()">💾 SAVE INCOME</button><button class="w-full text-green-500 dark:text-amber-400 text-xs" onclick="closeModal()">Cancel</button></div>`); }
        function openAddExpenseModal() { openModal(`<h2 class="font-black text-center text-lg mb-3"><i class="fa-solid fa-cart-shopping text-red-500"></i> Add Expense</h2><div class="space-y-3"><div><label class="text-xs font-bold">Amount</label><input id="ieAmount" type="number" step="0.01" class="w-full p-3 text-xl text-center font-black rounded-xl border input-premium" placeholder="₹ 0"></div><div><label class="text-xs font-bold">Category</label><select id="ieCategory" class="w-full p-2 rounded-xl border input-premium text-sm"><option value="Food">🍔 Food</option><option value="Travel">✈️ Travel</option><option value="Bills">💡 Bills</option><option value="Shopping">🛍️ Shopping</option><option value="Medical">🏥 Medical</option><option value="Other">📌 Other</option></select></div><div><label class="text-xs font-bold">Date</label><input id="ieDate" type="date" class="w-full p-2 rounded-xl border input-premium text-sm" value="${getToday()}"></div><div><label class="text-xs font-bold">Notes</label><textarea id="ieNotes" class="w-full p-2 rounded-xl border input-premium text-sm" rows="2" placeholder="Additional details..."></textarea></div><button class="w-full p-2.5 bg-red-600 text-white font-black rounded-xl action-btn text-sm" onclick="saveExpenseEntry()">💾 SAVE EXPENSE</button><button class="w-full text-green-500 dark:text-amber-400 text-xs" onclick="closeModal()">Cancel</button></div>`); }
        function saveIncomeEntry() { const amount = parseFloat(document.getElementById('ieAmount').value); if(isNaN(amount)||amount<=0) return alert("Please enter valid amount"); const category = document.getElementById('ieCategory').value; const date = document.getElementById('ieDate').value; const notes = document.getElementById('ieNotes').value.trim(); let icon = 'fa-circle-dollar-to-slot'; if(category === 'Salary') icon = 'fa-money-bill-wave'; else if(category === 'Business') icon = 'fa-store'; else if(category === 'Rent') icon = 'fa-building'; else if(category === 'Investment') icon = 'fa-chart-line'; else if(category === 'Gift') icon = 'fa-gift'; db.incomes.push({ id: Date.now(), amount, category, date, notes, icon }); saveDB(); closeModal(); renderIncomeExpenseList(); }
        function saveExpenseEntry() { const amount = parseFloat(document.getElementById('ieAmount').value); if(isNaN(amount)||amount<=0) return alert("Please enter valid amount"); const category = document.getElementById('ieCategory').value; const date = document.getElementById('ieDate').value; const notes = document.getElementById('ieNotes').value.trim(); let icon = 'fa-cart-shopping'; if(category === 'Food') icon = 'fa-utensils'; else if(category === 'Travel') icon = 'fa-plane'; else if(category === 'Bills') icon = 'fa-file-invoice-dollar'; else if(category === 'Shopping') icon = 'fa-bag-shopping'; else if(category === 'Medical') icon = 'fa-hospital'; db.expenses.push({ id: Date.now(), amount, category, date, notes, icon }); saveDB(); closeModal(); renderIncomeExpenseList(); }
        function openEditIncomeModal(id) { const inc = db.incomes.find(i => i.id === id); if(!inc) return; openModal(`<h2 class="font-black text-center text-lg mb-3"><i class="fa-solid fa-pen"></i> Edit Income</h2><div class="space-y-3"><div><label class="text-xs font-bold">Amount</label><input id="ieAmount" type="number" step="0.01" class="w-full p-3 text-xl text-center font-black rounded-xl border input-premium" value="${inc.amount}"></div><div><label class="text-xs font-bold">Category</label><select id="ieCategory" class="w-full p-2 rounded-xl border input-premium text-sm"><option value="Salary" ${inc.category==='Salary'?'selected':''}>💰 Salary</option><option value="Business" ${inc.category==='Business'?'selected':''}>🏪 Business</option><option value="Rent" ${inc.category==='Rent'?'selected':''}>🏠 Rent</option><option value="Investment" ${inc.category==='Investment'?'selected':''}>📈 Investment</option><option value="Gift" ${inc.category==='Gift'?'selected':''}>🎁 Gift</option><option value="Other" ${inc.category==='Other'?'selected':''}>📌 Other</option></select></div><div><label class="text-xs font-bold">Date</label><input id="ieDate" type="date" class="w-full p-2 rounded-xl border input-premium text-sm" value="${inc.date}"></div><div><label class="text-xs font-bold">Notes</label><textarea id="ieNotes" class="w-full p-2 rounded-xl border input-premium text-sm" rows="2">${inc.notes || ''}</textarea></div><button class="w-full p-2.5 bg-green-600 text-white font-black rounded-xl action-btn text-sm" onclick="updateIncomeEntry(${id})">💾 UPDATE</button><button class="w-full text-green-500 dark:text-amber-400 text-xs" onclick="closeModal()">Cancel</button></div>`); }
        function openEditExpenseModal(id) { const exp = db.expenses.find(e => e.id === id); if(!exp) return; openModal(`<h2 class="font-black text-center text-lg mb-3"><i class="fa-solid fa-pen"></i> Edit Expense</h2><div class="space-y-3"><div><label class="text-xs font-bold">Amount</label><input id="ieAmount" type="number" step="0.01" class="w-full p-3 text-xl text-center font-black rounded-xl border input-premium" value="${exp.amount}"></div><div><label class="text-xs font-bold">Category</label><select id="ieCategory" class="w-full p-2 rounded-xl border input-premium text-sm"><option value="Food" ${exp.category==='Food'?'selected':''}>🍔 Food</option><option value="Travel" ${exp.category==='Travel'?'selected':''}>✈️ Travel</option><option value="Bills" ${exp.category==='Bills'?'selected':''}>💡 Bills</option><option value="Shopping" ${exp.category==='Shopping'?'selected':''}>🛍️ Shopping</option><option value="Medical" ${exp.category==='Medical'?'selected':''}>🏥 Medical</option><option value="Other" ${exp.category==='Other'?'selected':''}>📌 Other</option></select></div><div><label class="text-xs font-bold">Date</label><input id="ieDate" type="date" class="w-full p-2 rounded-xl border input-premium text-sm" value="${exp.date}"></div><div><label class="text-xs font-bold">Notes</label><textarea id="ieNotes" class="w-full p-2 rounded-xl border input-premium text-sm" rows="2">${exp.notes || ''}</textarea></div><button class="w-full p-2.5 bg-red-600 text-white font-black rounded-xl action-btn text-sm" onclick="updateExpenseEntry(${id})">💾 UPDATE</button><button class="w-full text-green-500 dark:text-amber-400 text-xs" onclick="closeModal()">Cancel</button></div>`); }
        function updateIncomeEntry(id) { const inc = db.incomes.find(i => i.id === id); if(inc) { inc.amount = parseFloat(document.getElementById('ieAmount').value); inc.category = document.getElementById('ieCategory').value; inc.date = document.getElementById('ieDate').value; inc.notes = document.getElementById('ieNotes').value.trim(); saveDB(); closeModal(); renderIncomeExpenseList(); } }
        function updateExpenseEntry(id) { const exp = db.expenses.find(e => e.id === id); if(exp) { exp.amount = parseFloat(document.getElementById('ieAmount').value); exp.category = document.getElementById('ieCategory').value; exp.date = document.getElementById('ieDate').value; exp.notes = document.getElementById('ieNotes').value.trim(); saveDB(); closeModal(); renderIncomeExpenseList(); } }
        function deleteIncomeEntry(id) { if(confirm("Delete this income entry?")) { db.incomes = db.incomes.filter(i => i.id !== id); saveDB(); renderIncomeExpenseList(); } }
        function deleteExpenseEntry(id) { if(confirm("Delete this expense entry?")) { db.expenses = db.expenses.filter(e => e.id !== id); saveDB(); renderIncomeExpenseList(); } }

        // ==================== VEHICLE ====================
        function openVehiclePage() { document.getElementById('homeWorkspaceView').classList.add('hidden'); document.getElementById('ledgerWorkspaceView').classList.add('hidden'); document.getElementById('memoWorkspaceView').classList.add('hidden'); document.getElementById('incomeExpenseWorkspaceView').classList.add('hidden'); document.getElementById('vehicleWorkspaceView').classList.remove('hidden'); document.getElementById('vehicleWorkspaceView').classList.add('flex'); document.getElementById('backBtn').classList.add('hidden'); document.getElementById('custEditBtn').classList.add('hidden'); document.getElementById('custActionsMenuBtn').classList.add('hidden'); document.getElementById('memoBackBtn').classList.add('hidden'); document.getElementById('incomeBackBtn').classList.add('hidden'); document.getElementById('vehicleBackBtn').classList.remove('hidden'); document.getElementById('pageTitle').innerText = "🚗 VEHICLE"; renderVehicleExpenses(); }
        function closeVehiclePage() { document.getElementById('vehicleWorkspaceView').classList.add('hidden'); document.getElementById('homeWorkspaceView').classList.remove('hidden'); document.getElementById('vehicleBackBtn').classList.add('hidden'); document.getElementById('pageTitle').innerText = "KHATA PRO"; renderClientListFeed(); }
        function renderVehicleExpenses() { if (!db.vehicleExpenses) db.vehicleExpenses = []; const sorted = [...db.vehicleExpenses].sort((a,b)=>new Date(b.date)-new Date(a.date)); let total = 0, html = ''; sorted.forEach(exp => { total += exp.amount; html += `
                <div class="premium-card flex justify-between items-start cursor-pointer" onclick="openEditVehicleExpenseModal(${exp.id})">
                    <div class="flex-1">
                        <div class="flex items-center gap-2 mb-1">
                            <span class="text-base text-blue-600"><i class="fa-solid fa-${exp.icon || 'car'}"></i></span>
                            <span class="font-black text-green-800 dark:text-amber-400 text-sm">${exp.vehicleName}</span>
                            <span class="text-[10px] px-1.5 py-0.5 bg-blue-100 dark:bg-blue-900 text-blue-700 dark:text-blue-300 rounded-full font-bold">${exp.expenseType}</span>
                        </div>
                        <p class="text-xs font-bold text-gray-600 dark:text-gray-400">${exp.remarks || '—'}</p>
                        <div class="flex gap-2 mt-1 text-[10px] font-bold text-gray-400 dark:text-gray-500">
                            <span><i class="fa-regular fa-calendar"></i> ${fmtDate(exp.date)}</span>
                        </div>
                    </div>
                    <div class="text-right">
                        <p class="font-black text-base text-rose-600 dark:text-rose-400">₹${exp.amount.toFixed(2)}</p>
                        <button onclick="event.stopPropagation();deleteVehicleExpense(${exp.id})" class="mt-1 text-gray-400 hover:text-red-500 dark:hover:text-red-400 text-xs"><i class="fa-solid fa-trash"></i></button>
                    </div>
                </div>
            `; }); document.getElementById('totalVehicleExpense').innerHTML = `₹${total.toFixed(2)}`; document.getElementById('vehicleExpensesList').innerHTML = html || `<div class="text-center text-gray-400 dark:text-gray-500 py-8 text-sm font-bold"><i class="fa-solid fa-car text-3xl mb-2"></i><p>No vehicle expenses yet.<br>Click ADD to record!</p></div>`; }
        function openAddVehicleExpenseModal() { openModal(`<h2 class="font-black text-center text-lg mb-3"><i class="fa-solid fa-plus-circle text-blue-500"></i> Add Vehicle Expense</h2><div class="space-y-3"><div><label class="text-xs font-bold">Vehicle Name</label><input id="vehName" class="w-full p-2 rounded-xl border input-premium text-sm" placeholder="E.g: Car, Bike"></div><div><label class="text-xs font-bold">Expense Type</label><select id="vehType" class="w-full p-2 rounded-xl border input-premium text-sm"><option value="Fuel">⛽ Fuel</option><option value="Repair">🔧 Repair</option><option value="Insurance">📄 Insurance</option><option value="Service">🛠️ Service</option><option value="EMI">🏦 EMI</option><option value="Others">📌 Others</option></select></div><div><label class="text-xs font-bold">Amount</label><input id="vehAmount" type="number" step="0.01" class="w-full p-2 rounded-xl border input-premium text-base font-black" placeholder="₹ 0"></div><div><label class="text-xs font-bold">Date</label><input id="vehDate" type="date" class="w-full p-2 rounded-xl border input-premium text-sm" value="${getToday()}"></div><div><label class="text-xs font-bold">Remarks</label><textarea id="vehRemarks" class="w-full p-2 rounded-xl border input-premium text-sm" rows="2" placeholder="Optional notes..."></textarea></div><button class="w-full p-3 bg-blue-600 text-white font-black rounded-xl action-btn text-sm" onclick="saveVehicleExpense()">💾 SAVE EXPENSE</button><button class="w-full text-green-500 dark:text-amber-400 text-xs" onclick="closeModal()">Cancel</button></div>`); }
        function saveVehicleExpense() { const vehicleName = document.getElementById('vehName').value.trim(); if(!vehicleName) return alert("Please enter vehicle name"); const expenseType = document.getElementById('vehType').value; const amount = parseFloat(document.getElementById('vehAmount').value); if(isNaN(amount)||amount<=0) return alert("Please enter valid amount"); const date = document.getElementById('vehDate').value; const remarks = document.getElementById('vehRemarks').value.trim(); let icon = 'car'; if(expenseType === 'Fuel') icon = 'gas-pump'; else if(expenseType === 'Repair') icon = 'wrench'; else if(expenseType === 'Insurance') icon = 'file-shield'; else if(expenseType === 'Service') icon = 'oil-can'; else if(expenseType === 'EMI') icon = 'building-columns'; db.vehicleExpenses.push({ id: Date.now(), vehicleName, expenseType, amount, date, remarks, icon }); saveDB(); closeModal(); renderVehicleExpenses(); }
        function openEditVehicleExpenseModal(id) { const exp = db.vehicleExpenses.find(e => e.id === id); if(!exp) return; openModal(`<h2 class="font-black text-center text-lg mb-3"><i class="fa-solid fa-pen text-blue-500"></i> Edit Expense</h2><div class="space-y-3"><div><label class="text-xs font-bold">Vehicle Name</label><input id="vehName" class="w-full p-2 rounded-xl border input-premium" value="${exp.vehicleName}"></div><div><label class="text-xs font-bold">Expense Type</label><select id="vehType" class="w-full p-2 rounded-xl border input-premium text-sm"><option value="Fuel" ${exp.expenseType==='Fuel'?'selected':''}>⛽ Fuel</option><option value="Repair" ${exp.expenseType==='Repair'?'selected':''}>🔧 Repair</option><option value="Insurance" ${exp.expenseType==='Insurance'?'selected':''}>📄 Insurance</option><option value="Service" ${exp.expenseType==='Service'?'selected':''}>🛠️ Service</option><option value="EMI" ${exp.expenseType==='EMI'?'selected':''}>🏦 EMI</option><option value="Others" ${exp.expenseType==='Others'?'selected':''}>📌 Others</option></select></div><div><label class="text-xs font-bold">Amount</label><input id="vehAmount" type="number" step="0.01" class="w-full p-2 rounded-xl border input-premium text-base font-black" value="${exp.amount}"></div><div><label class="text-xs font-bold">Date</label><input id="vehDate" type="date" class="w-full p-2 rounded-xl border input-premium text-sm" value="${exp.date}"></div><div><label class="text-xs font-bold">Remarks</label><textarea id="vehRemarks" class="w-full p-2 rounded-xl border input-premium text-sm" rows="2">${exp.remarks || ''}</textarea></div><button class="w-full p-3 bg-blue-600 text-white font-black rounded-xl action-btn text-sm" onclick="updateVehicleExpense(${id})">💾 UPDATE</button><button class="w-full text-green-500 dark:text-amber-400 text-xs" onclick="closeModal()">Cancel</button></div>`); }
        function updateVehicleExpense(id) { const exp = db.vehicleExpenses.find(e => e.id === id); if(exp) { exp.vehicleName = document.getElementById('vehName').value.trim(); exp.expenseType = document.getElementById('vehType').value; exp.amount = parseFloat(document.getElementById('vehAmount').value); exp.date = document.getElementById('vehDate').value; exp.remarks = document.getElementById('vehRemarks').value.trim(); saveDB(); closeModal(); renderVehicleExpenses(); } }
        function deleteVehicleExpense(id) { if(confirm("Delete this expense?")) { db.vehicleExpenses = db.vehicleExpenses.filter(e => e.id !== id); saveDB(); renderVehicleExpenses(); } }

        // ==================== MEMO / REMINDERS ====================
        function openMemoPage() { document.getElementById('homeWorkspaceView').classList.add('hidden'); document.getElementById('ledgerWorkspaceView').classList.add('hidden'); document.getElementById('vehicleWorkspaceView').classList.add('hidden'); document.getElementById('incomeExpenseWorkspaceView').classList.add('hidden'); document.getElementById('memoWorkspaceView').classList.remove('hidden'); document.getElementById('memoWorkspaceView').classList.add('flex'); document.getElementById('backBtn').classList.add('hidden'); document.getElementById('custEditBtn').classList.add('hidden'); document.getElementById('custActionsMenuBtn').classList.add('hidden'); document.getElementById('vehicleBackBtn').classList.add('hidden'); document.getElementById('incomeBackBtn').classList.add('hidden'); document.getElementById('memoBackBtn').classList.remove('hidden'); document.getElementById('pageTitle').innerText = "📝 MEMO"; renderReminders(); }
        function closeMemoPage() { document.getElementById('memoWorkspaceView').classList.add('hidden'); document.getElementById('homeWorkspaceView').classList.remove('hidden'); document.getElementById('memoBackBtn').classList.add('hidden'); document.getElementById('pageTitle').innerText = "KHATA PRO"; renderClientListFeed(); }
        function renderReminders() { if (!db.reminders) db.reminders = []; const today = new Date(); today.setHours(0,0,0,0); const sorted = [...db.reminders].sort((a,b)=>new Date(a.dueDate)-new Date(b.dueDate)); let html = ''; sorted.forEach(rem => { const dueDate = new Date(rem.dueDate); dueDate.setHours(0,0,0,0); const daysLeft = Math.ceil((dueDate - today) / (1000*60*60*24)); let statusClass = '', statusText = ''; if (daysLeft < 0) { statusClass = 'bg-red-800 text-white'; statusText = '⚠️ OVERDUE'; } else if (daysLeft <= 3) { statusClass = 'bg-red-600 text-white'; statusText = '🔴 URGENT - ' + daysLeft + 'd'; } else if (daysLeft <= 7) { statusClass = 'bg-orange-500 text-white'; statusText = '🟡 SOON - ' + daysLeft + 'd'; } else { statusClass = 'bg-green-600 text-white'; statusText = '🟢 ' + daysLeft + 'd left'; } html += `
                <div class="rounded-xl p-3 ${statusClass} shadow-lg mb-2 cursor-pointer" onclick="openEditReminderModal(${rem.id})">
                    <div class="flex justify-between items-start">
                        <div class="flex-1">
                            <h3 class="font-black text-sm"><i class="fa-${rem.icon || 'fa-bell'} mr-1"></i> ${rem.title}</h3>
                            <p class="text-xs font-bold opacity-90 mt-0.5">${rem.description || '—'}</p>
                            <div class="flex gap-2 mt-1 text-[10px] font-bold">
                                <span><i class="fa-regular fa-calendar"></i> ${fmtDate(rem.dueDate)}</span>
                                <span><i class="fa-regular fa-bell"></i> ${rem.reminderDays}d before</span>
                            </div>
                        </div>
                        <div class="text-right">
                            <div class="text-[9px] font-black px-2 py-0.5 bg-black/30 rounded-full">${statusText}</div>
                            <button onclick="event.stopPropagation();deleteReminder(${rem.id})" class="mt-1 text-white/70 hover:text-white"><i class="fa-solid fa-trash text-xs"></i></button>
                        </div>
                    </div>
                </div>
            `; }); document.getElementById('remindersListContainer').innerHTML = html || `<div class="text-center text-green-500 dark:text-amber-400 py-8 text-sm font-bold"><i class="fa-regular fa-sticky-note text-3xl mb-2"></i><p>No reminders yet.<br>Click ADD to create!</p></div>`; }
        function openAddReminderModal() { openModal(`<h2 class="font-black text-center text-lg mb-3"><i class="fa-solid fa-plus-circle text-purple-500"></i> Add Reminder</h2><div class="space-y-3"><div><label class="text-xs font-bold">Title</label><input id="remTitle" class="w-full p-2 rounded-lg border input-premium text-sm" placeholder="E.g: Vehicle Insurance Due"></div><div><label class="text-xs font-bold">Description</label><textarea id="remDesc" class="w-full p-2 rounded-lg border input-premium text-sm" rows="2" placeholder="More details..."></textarea></div><div><label class="text-xs font-bold">Due Date</label><input id="remDate" type="date" class="w-full p-2 rounded-lg border input-premium text-sm" value="${getToday()}"></div><div><label class="text-xs font-bold">Remind me before</label><select id="remDays" class="w-full p-2 rounded-lg border input-premium text-sm"><option value="1">1 day before</option><option value="3" selected>3 days before</option><option value="7">7 days before</option><option value="14">14 days before</option></select></div><div><label class="text-xs font-bold">Icon</label><div class="grid grid-cols-6 gap-1"><button type="button" onclick="selectRemIcon('fa-car')" class="p-1.5 rounded-lg border hover:bg-green-100 dark:hover:bg-slate-700"><i class="fa-solid fa-car text-sm"></i></button><button type="button" onclick="selectRemIcon('fa-building-columns')" class="p-1.5 rounded-lg border hover:bg-green-100 dark:hover:bg-slate-700"><i class="fa-solid fa-building-columns text-sm"></i></button><button type="button" onclick="selectRemIcon('fa-file-lines')" class="p-1.5 rounded-lg border hover:bg-green-100 dark:hover:bg-slate-700"><i class="fa-solid fa-file-lines text-sm"></i></button><button type="button" onclick="selectRemIcon('fa-calendar-check')" class="p-1.5 rounded-lg border hover:bg-green-100 dark:hover:bg-slate-700"><i class="fa-solid fa-calendar-check text-sm"></i></button><button type="button" onclick="selectRemIcon('fa-bell')" class="p-1.5 rounded-lg border hover:bg-green-100 dark:hover:bg-slate-700"><i class="fa-solid fa-bell text-sm"></i></button><button type="button" onclick="selectRemIcon('fa-credit-card')" class="p-1.5 rounded-lg border hover:bg-green-100 dark:hover:bg-slate-700"><i class="fa-solid fa-credit-card text-sm"></i></button></div></div><input type="hidden" id="remIcon" value="fa-bell"><button class="w-full p-2.5 bg-purple-600 text-white font-black rounded-lg action-btn text-sm" onclick="saveReminder()">💾 SAVE</button><button class="w-full text-green-500 dark:text-amber-400 text-sm" onclick="closeModal()">Cancel</button></div>`); }
        function selectRemIcon(icon) { document.getElementById('remIcon').value = icon; }
        function saveReminder() { const title = document.getElementById('remTitle').value.trim(); if(!title) return alert("Enter title"); const description = document.getElementById('remDesc').value.trim(); const dueDate = document.getElementById('remDate').value; const reminderDays = parseInt(document.getElementById('remDays').value); const icon = document.getElementById('remIcon').value; if(!dueDate) return alert("Select due date"); db.reminders.push({ id: Date.now(), title, description, dueDate, reminderDays, icon, alertSent: false }); saveDB(); closeModal(); renderReminders(); }
        function openEditReminderModal(id) { const rem = db.reminders.find(r => r.id === id); if(!rem) return; openModal(`<h2 class="font-black text-center text-lg mb-3"><i class="fa-solid fa-pen"></i> Edit Reminder</h2><div class="space-y-3"><div><label class="text-xs font-bold">Title</label><input id="remTitle" class="w-full p-2 rounded-lg border input-premium text-sm" value="${rem.title}"></div><div><label class="text-xs font-bold">Description</label><textarea id="remDesc" class="w-full p-2 rounded-lg border input-premium text-sm" rows="2">${rem.description || ''}</textarea></div><div><label class="text-xs font-bold">Due Date</label><input id="remDate" type="date" class="w-full p-2 rounded-lg border input-premium text-sm" value="${rem.dueDate}"></div><div><label class="text-xs font-bold">Remind before</label><select id="remDays" class="w-full p-2 rounded-lg border input-premium text-sm"><option value="1" ${rem.reminderDays===1?'selected':''}>1 day before</option><option value="3" ${rem.reminderDays===3?'selected':''}>3 days before</option><option value="7" ${rem.reminderDays===7?'selected':''}>7 days before</option><option value="14" ${rem.reminderDays===14?'selected':''}>14 days before</option></select></div><button class="w-full p-2.5 bg-purple-600 text-white font-black rounded-lg action-btn text-sm" onclick="updateReminder(${id})">💾 UPDATE</button><button class="w-full text-green-500 dark:text-amber-400 text-xs" onclick="closeModal()">Cancel</button></div>`); }
        function updateReminder(id) { const rem = db.reminders.find(r => r.id === id); if(rem) { rem.title = document.getElementById('remTitle').value.trim(); rem.description = document.getElementById('remDesc').value.trim(); rem.dueDate = document.getElementById('remDate').value; rem.reminderDays = parseInt(document.getElementById('remDays').value); rem.alertSent = false; saveDB(); closeModal(); renderReminders(); } }
        function deleteReminder(id) { if(confirm("Delete this reminder?")) { db.reminders = db.reminders.filter(r => r.id !== id); saveDB(); renderReminders(); } }

        // ==================== SETTINGS ====================
        function openSettings() { openModal(`<h2 class="font-black text-center text-lg mb-3">⚙️ SECURE SETTINGS</h2><div class="space-y-3"><div><label class="text-[10px] font-bold uppercase">UPI ID</label><input id="upiI" class="w-full p-2 rounded-lg border input-premium text-sm" value="${db.upi || ''}" placeholder="example@okhdfcbank"></div><div><label class="text-[10px] font-bold uppercase">4-DIGIT PIN</label><input id="pinI" type="password" maxlength="4" class="w-full p-2 rounded-lg border input-premium text-sm" value="${db.pin || ''}" placeholder="****"></div><button class="w-full p-2 bg-blue-600 text-white font-black rounded-lg action-btn text-sm" onclick="saveSettings()">💾 SAVE CHANGES</button><div class="grid grid-cols-2 gap-2"><button class="p-2 bg-emerald-700 text-white rounded-lg font-bold action-btn text-xs" onclick="exportData()">📁 BACKUP</button><button class="p-2 bg-purple-700 text-white rounded-lg font-bold action-btn text-xs" onclick="document.getElementById('imp').click()">🔄 RESTORE</button></div><button class="w-full p-2 bg-rose-700 text-white rounded-lg font-bold action-btn text-sm" onclick="fullResetApp()">⚠️ DELETE ALL DATA</button><button class="w-full py-2 text-green-500 dark:text-amber-400 font-bold text-sm" onclick="closeModal()">Close</button><input type="file" id="imp" class="hidden" onchange="importData(event)"></div>`); }
        function saveSettings() { const newUpi = document.getElementById('upiI').value.trim(); const newPin = document.getElementById('pinI').value; if(newPin && newPin.length !== 4 && newPin.length !== 0) { alert("PIN must be exactly 4 digits"); return; } db.upi = newUpi; if(newPin && newPin.length === 4) db.pin = newPin; saveDB(); alert("✅ Settings saved!"); closeModal(); }
        function exportData() { const blob = new Blob([JSON.stringify(db)], {type:'application/json'}); const a = document.createElement('a'); a.href = URL.createObjectURL(blob); a.download = `khata_backup_${getToday()}.json`; a.click(); }
        function importData(e) { 
            const reader = new FileReader(); 
            reader.onload = ev => { 
                try { 
                    const imported = JSON.parse(ev.target.result); 
                    if(!imported.customers || !imported.trans) {
                        alert("❌ Invalid backup file format");
                        return;
                    }
                    db = imported; 
                    saveDB(); 
                    alert("✅ Restore successful! Reloading..."); 
                    location.reload(); 
                } catch(err) { 
                    alert("❌ Invalid backup file: " + err.message); 
                } 
            }; 
            reader.readAsText(e.target.files[0]); 
        }

        // ==================== QR & SHARE ====================
        function openQR(amt) { if(!db.upi) return alert("Set UPI ID in settings"); currentQRAmount = amt; openModal(`<div class="text-center"><div id="qr-container" class="bg-white p-3 rounded-xl inline-block shadow-md"></div><p class="font-black text-xl mt-2 text-green-800 dark:text-amber-400">₹${amt}</p><p class="text-[10px] font-bold text-green-600 dark:text-amber-400">${db.upi}</p><div class="grid grid-cols-2 gap-2 mt-3"><button onclick="shareQRToWhatsApp()" class="bg-green-600 text-white p-2 rounded-lg font-bold action-btn text-sm"><i class="fab fa-whatsapp mr-1"></i> WhatsApp</button><button onclick="closeModal()" class="bg-gray-300 dark:bg-slate-700 text-gray-800 dark:text-white p-2 rounded-lg font-bold action-btn text-sm">Close</button></div></div>`); setTimeout(() => { const qc = document.getElementById("qr-container"); if(qc) { qc.innerHTML = ""; new QRCode(qc, { text: `upi://pay?pa=${db.upi}&am=${amt}&cu=INR`, width: 160, height: 160, colorDark: "#000000", colorLight: "#ffffff" }); } }, 100); }
        function shareQRToWhatsApp() { const qrElement = document.getElementById("qr-container"); if(!qrElement) return; html2canvas(qrElement, { backgroundColor: '#ffffff', scale: 2 }).then(canvas => { canvas.toBlob(blob => { const file = new File([blob], 'qr_code.png', { type: 'image/png' }); if (navigator.share) { navigator.share({ title: 'Payment QR Code', text: `Payment Request: ₹${currentQRAmount}`, files: [file] }).catch(() => fallbackWhatsAppShare()); } else { fallbackWhatsAppShare(); } }); }).catch(() => fallbackWhatsAppShare()); function fallbackWhatsAppShare() { const cust = db.customers.find(c => c.id === activeCid); const phone = cust?.phone; let waUrl = ''; if(phone && phone !== '-') { let cleanPhone = phone.replace(/\D/g, ''); if(cleanPhone.length === 10) cleanPhone = '91' + cleanPhone; waUrl = `https://wa.me/${cleanPhone}?text=${encodeURIComponent(`💰 Payment Request\nAmount: ₹${currentQRAmount}\nUPI: ${db.upi}`)}`; } else { waUrl = `https://wa.me/?text=${encodeURIComponent(`💰 Payment Request\nAmount: ₹${currentQRAmount}\nUPI: ${db.upi}`)}`; } window.open(waUrl, '_blank'); } closeModal(); }
        function shareWA(p,b) { if(!p || p === '-') return alert("Phone missing"); const msg = `KHATA PRO SECURE\nClient Balance: ₹${Math.abs(b).toFixed(2)}\nThank you!`; window.open(`https://wa.me/91${p}?text=${encodeURIComponent(msg)}`); }

        // ==================== PRINT / PDF ====================
        function openPrintModal() { const cust = db.customers.find(c => c.id === activeCid); if(!cust) return; openModal(`<div><h2 class="font-black text-center text-green-800 dark:text-amber-400 text-base">🖨️ PRINT LEDGER</h2><div class="grid grid-cols-2 gap-2 my-2"><input id="ps" type="date" class="p-2 border border-green-200 dark:border-slate-600 rounded-lg text-sm dark:bg-slate-800" value="2025-01-01"><input id="pe" type="date" class="p-2 border border-green-200 dark:border-slate-600 rounded-lg text-sm dark:bg-slate-800" value="${getToday()}"></div><button class="w-full p-2 bg-indigo-600 text-white rounded-lg font-black action-btn text-sm" onclick="generatePrintA4()">📄 GENERATE</button><button class="w-full mt-2 p-2 text-green-500 dark:text-amber-400 text-sm" onclick="closeModal()">Cancel</button></div>`); }
        function generatePrintA4() { const s = document.getElementById('ps').value, e = document.getElementById('pe').value, cust = db.customers.find(c => c.id === activeCid); const filtered = db.trans.filter(t => t.cid === activeCid && t.date >= s && t.date <= e).sort((a,b) => new Date(a.date) - new Date(b.date)); let rt = 0; let rows = filtered.map(t => { rt += (t.type === 'GAVE' ? t.amt : -t.amt); return `<tr><td style="padding:6px;font-size:12px">${fmtDate(t.date)}<br><small>${t.rem || ''}</small></td><td style="text-align:right">${t.type === 'GAVE' ? '₹'+t.amt.toFixed(2) : '-'}</td><td style="text-align:right">${t.type === 'GOT' ? '₹'+t.amt.toFixed(2) : '-'}</td><td style="text-align:right">₹${Math.abs(rt).toFixed(2)}</td></tr>`; }).join(''); const win = window.open('','_blank'); win.document.write(`<!DOCTYPE html><html><head><title>${cust.name} Statement</title><style>body{font-family:sans-serif;padding:15px}table{width:100%;border-collapse:collapse}th,td{border-bottom:1px solid #ccc;padding:6px;font-size:12px}th{background:#2e7d32;color:white}.text-right{text-align:right}@media print{body{padding:0}}@page{size:A4;margin:8mm}</style></head><body><h2 style="text-align:center;font-size:18px">KHATA PRO LEDGER</h2><p><strong>${cust.name}</strong> | ${cust.phone || ''}</p><p>Period: ${fmtDate(s)} - ${fmtDate(e)}</p><table class="w-full"><thead><tr><th>Date & Notes</th><th class="text-right">Gave</th><th class="text-right">Got</th><th class="text-right">Balance</th></tr></thead><tbody>${rows}</tbody></table><h3 style="text-align:right">Closing: ₹${Math.abs(rt).toFixed(2)}</h3><div style="text-align:center;margin-top:15px"><button onclick="window.print()">Print</button> <button onclick="window.close()">Close</button></div></body></html>`); win.document.close(); closeModal(); }
        function openPDFModal() { openModal(`<div><h2 class="font-black text-center text-green-800 dark:text-amber-400 text-base">📄 PDF Statement</h2><div class="grid grid-cols-2 gap-2 my-2"><input id="ps" type="date" class="p-2 border border-green-200 dark:border-slate-600 rounded-lg text-sm dark:bg-slate-800" value="2025-01-01"><input id="pe" type="date" class="p-2 border border-green-200 dark:border-slate-600 rounded-lg text-sm dark:bg-slate-800" value="${getToday()}"></div><button class="w-full p-2 bg-blue-600 text-white rounded-lg font-black action-btn text-sm" onclick="generatePDF()">CREATE PDF</button><button class="w-full mt-2 p-2 text-green-500 dark:text-amber-400 text-sm" onclick="closeModal()">Cancel</button></div>`); }
        function generatePDF() { const s = document.getElementById('ps').value, e = document.getElementById('pe').value, cust = db.customers.find(c => c.id === activeCid); const filtered = db.trans.filter(t => t.cid === activeCid && t.date >= s && t.date <= e).sort((a,b) => new Date(a.date) - new Date(b.date)); const el = document.createElement('div'); el.style.padding = '15px'; el.style.background = '#fff'; let rt = 0; let rows = filtered.map(t => { rt += (t.type === 'GAVE' ? t.amt : -t.amt); return `<tr><td style="border:1px solid #ccc;padding:5px;font-size:11px">${fmtDate(t.date)} ${t.time || ''}</td><td style="border:1px solid #ccc">${t.type === 'GAVE' ? '₹'+t.amt.toFixed(2) : '-'}</td><td style="border:1px solid #ccc">${t.type === 'GOT' ? '₹'+t.amt.toFixed(2) : '-'}</td><td style="border:1px solid #ccc">₹${rt.toFixed(2)}</td></tr>`; }).join(''); el.innerHTML = `<h2 style="text-align:center;font-size:16px">KHATA PRO LEDGER</h2><p><strong>${cust.name}</strong> | ${cust.phone || ''}</p><p>Period: ${fmtDate(s)} - ${fmtDate(e)}</p><table style="width:100%;border-collapse:collapse">${rows}</table><h3 style="margin-top:10px">Closing: ₹${Math.abs(rt).toFixed(2)}</h3>`; html2pdf().set({margin:0.5,filename:`${cust.name}_statement.pdf`}).from(el).save(); }

        // ==================== ACTIONS HUB ====================
        function openActionsHubModal() { const cust = db.customers.find(c => c.id === activeCid); if(!cust) return; let rb = 0; db.trans.filter(t => t.cid === activeCid).forEach(t => rb += (t.type === 'GAVE' ? t.amt : -t.amt)); openModal(`<h2 class="font-black text-center mb-3 text-base"><i class="fa-solid fa-bolt text-amber-500"></i> QUICK ACTIONS</h2><div class="grid grid-cols-3 gap-2 mb-3"><button onclick="closeModal();shareWA('${cust.phone}',${rb.toFixed(2)})" class="btn-premium text-xs py-2"><i class="fab fa-whatsapp text-lg"></i><span>WA</span></button><button onclick="closeModal();openQR(${Math.abs(rb).toFixed(2)})" class="btn-premium text-xs py-2"><i class="fas fa-qrcode text-lg"></i><span>QR</span></button><button onclick="closeModal();openPDFModal()" class="btn-premium text-xs py-2"><i class="fas fa-file-pdf text-lg"></i><span>PDF</span></button><button onclick="closeModal();openPrintModal()" class="btn-premium text-xs py-2"><i class="fas fa-print text-lg"></i><span>PRINT</span></button><button onclick="closeModal();toggleDateFilterDrawer()" class="btn-premium text-xs py-2"><i class="fas fa-calendar-alt text-lg"></i><span>Filter</span></button><button onclick="closeModal();openPromiseModal()" class="btn-premium text-xs py-2"><i class="fas fa-clock text-lg"></i><span>Promise</span></button></div><button class="w-full mt-1 p-2 text-green-500 dark:text-amber-400 text-xs" onclick="closeModal()">Close</button>`); }

        // ==================== CALCULATOR ====================
        function openCalculator() { openModal(`<div class="p-1"><div id="calcDisplay" class="text-right text-2xl font-black p-3 bg-gray-100 dark:bg-slate-800 rounded-xl mb-3">0</div><div class="grid grid-cols-4 gap-2"><button class="calc-btn text-xl py-2 rounded-xl bg-gray-200 dark:bg-slate-700 font-black" onclick="calcInput('7')">7</button><button class="calc-btn text-xl py-2 rounded-xl bg-gray-200 dark:bg-slate-700 font-black" onclick="calcInput('8')">8</button><button class="calc-btn text-xl py-2 rounded-xl bg-gray-200 dark:bg-slate-700 font-black" onclick="calcInput('9')">9</button><button class="calc-btn text-xl py-2 rounded-xl bg-amber-500 font-black" onclick="calcInput('/')">÷</button><button class="calc-btn text-xl py-2 rounded-xl bg-gray-200 dark:bg-slate-700 font-black" onclick="calcInput('4')">4</button><button class="calc-btn text-xl py-2 rounded-xl bg-gray-200 dark:bg-slate-700 font-black" onclick="calcInput('5')">5</button><button class="calc-btn text-xl py-2 rounded-xl bg-gray-200 dark:bg-slate-700 font-black" onclick="calcInput('6')">6</button><button class="calc-btn text-xl py-2 rounded-xl bg-amber-500 font-black" onclick="calcInput('*')">×</button><button class="calc-btn text-xl py-2 rounded-xl bg-gray-200 dark:bg-slate-700 font-black" onclick="calcInput('1')">1</button><button class="calc-btn text-xl py-2 rounded-xl bg-gray-200 dark:bg-slate-700 font-black" onclick="calcInput('2')">2</button><button class="calc-btn text-xl py-2 rounded-xl bg-gray-200 dark:bg-slate-700 font-black" onclick="calcInput('3')">3</button><button class="calc-btn text-xl py-2 rounded-xl bg-amber-500 font-black" onclick="calcInput('-')">-</button><button class="calc-btn text-xl py-2 rounded-xl bg-gray-200 dark:bg-slate-700 font-black" onclick="calcInput('0')">0</button><button class="calc-btn text-xl py-2 rounded-xl bg-gray-200 dark:bg-slate-700 font-black" onclick="calcInput('00')">00</button><button class="calc-btn text-xl py-2 rounded-xl bg-gray-200 dark:bg-slate-700 font-black" onclick="calcInput('.')">.</button><button class="calc-btn text-xl py-2 rounded-xl bg-amber-500 font-black" onclick="calcInput('+')">+</button><button class="calc-btn col-span-2 bg-red-500 text-white text-sm py-2 rounded-xl font-black" onclick="calcClear()">AC</button><button class="calc-btn text-xl py-2 rounded-xl bg-gray-200 dark:bg-slate-700 font-black" onclick="calcDelete()">⌫</button><button class="calc-btn text-xl py-2 rounded-xl bg-blue-600 text-white font-black" onclick="calcEvaluate()">=</button></div><button class="w-full mt-3 p-2 bg-green-600 text-white rounded-lg font-bold action-btn text-sm" onclick="useCalcResultInAdd()">✓ USE THIS AMOUNT</button><button class="w-full mt-1 p-1 text-slate-500 dark:text-slate-400 text-xs" onclick="closeModal()">Cancel</button></div>`); currentCalculatorInput = "0"; updateCalcDisplay(); }
        function calcInput(val) { if (currentCalculatorInput === "0" && val !== "." && !isNaN(val)) currentCalculatorInput = val; else currentCalculatorInput += val; updateCalcDisplay(); }
        function calcClear() { currentCalculatorInput = "0"; updateCalcDisplay(); }
        function calcDelete() { currentCalculatorInput = currentCalculatorInput.slice(0, -1); if (currentCalculatorInput === "") currentCalculatorInput = "0"; updateCalcDisplay(); }
        function updateCalcDisplay() { const el = document.getElementById("calcDisplay"); if(el) el.innerText = currentCalculatorInput; }
        function calcEvaluate() { try { let expr = currentCalculatorInput.replace(/×/g, '*').replace(/÷/g, '/'); let result = eval(expr); if (isNaN(result) || !isFinite(result)) throw new Error(); currentCalculatorInput = result.toString(); updateCalcDisplay(); } catch(e) { alert("Invalid calculation"); calcClear(); } }
        function useCalcResultInAdd() { let val = parseFloat(currentCalculatorInput); if (isNaN(val)) val = 0; const amtInput = document.getElementById('ta'); if (amtInput) amtInput.value = val.toFixed(2); closeModal(); }

        // ==================== INIT ====================
        window.onload = () => { 
            if(db.theme) applyTheme(db.theme);
            if(db.darkMode) document.body.classList.add('dark-mode');
            lockApp(); 
        };
    </script>
</body>
</html>
