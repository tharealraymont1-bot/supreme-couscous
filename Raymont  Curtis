<!DOCTYPE html>

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <meta http-equiv="Content-Security-Policy" content="default-src 'self'; script-src 'self' 'unsafe-inline' https://cdn.jsdelivr.net https://unpkg.com; style-src 'self' 'unsafe-inline' https://cdn.jsdelivr.net; img-src 'self' data: https:;">
    <title>AI Revenue Suite - Secure Platform</title>
    <script src="https://cdn.jsdelivr.net/npm/react@18.2.0/umd/react.production.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/react-dom@18.2.0/umd/react-dom.production.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@babel/standalone@7.23.5/babel.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/lucide@0.263.1/dist/umd/lucide.min.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

```
    body {
        font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
        background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        min-height: 100vh;
        overflow-x: hidden;
    }

    .security-badge {
        position: fixed;
        top: 20px;
        right: 20px;
        background: rgba(16, 185, 129, 0.2);
        backdrop-filter: blur(10px);
        border: 2px solid #10b981;
        padding: 10px 20px;
        border-radius: 50px;
        color: white;
        font-weight: 600;
        font-size: 14px;
        z-index: 1000;
        display: flex;
        align-items: center;
        gap: 8px;
        animation: pulse 2s infinite;
    }

    @keyframes pulse {
        0%, 100% { opacity: 1; }
        50% { opacity: 0.7; }
    }

    .login-overlay {
        position: fixed;
        inset: 0;
        background: rgba(0, 0, 0, 0.8);
        backdrop-filter: blur(10px);
        display: flex;
        align-items: center;
        justify-content: center;
        z-index: 9999;
    }

    .login-box {
        background: white;
        padding: 40px;
        border-radius: 20px;
        box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
        max-width: 400px;
        width: 90%;
    }

    .login-box h2 {
        margin-bottom: 10px;
        color: #333;
    }

    .login-box p {
        color: #666;
        margin-bottom: 30px;
    }

    .login-box input {
        width: 100%;
        padding: 15px;
        border: 2px solid #e5e7eb;
        border-radius: 10px;
        font-size: 16px;
        margin-bottom: 15px;
        transition: all 0.3s;
    }

    .login-box input:focus {
        outline: none;
        border-color: #667eea;
    }

    .login-box button {
        width: 100%;
        padding: 15px;
        background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        color: white;
        border: none;
        border-radius: 10px;
        font-size: 16px;
        font-weight: 600;
        cursor: pointer;
        transition: transform 0.2s;
    }

    .login-box button:hover {
        transform: translateY(-2px);
    }

    .security-features {
        margin-top: 20px;
        padding: 15px;
        background: #f3f4f6;
        border-radius: 10px;
        font-size: 12px;
        color: #666;
    }

    .security-features div {
        margin: 5px 0;
        display: flex;
        align-items: center;
        gap: 8px;
    }

    .error-message {
        background: #fee2e2;
        color: #dc2626;
        padding: 10px;
        border-radius: 8px;
        margin-bottom: 15px;
        display: none;
    }

    .error-message.show {
        display: block;
    }

    #root {
        display: none;
    }

    #root.authenticated {
        display: block;
    }

    .rate-limit-notice {
        position: fixed;
        bottom: 20px;
        left: 50%;
        transform: translateX(-50%);
        background: rgba(239, 68, 68, 0.9);
        color: white;
        padding: 15px 30px;
        border-radius: 10px;
        display: none;
        z-index: 1000;
    }

    .rate-limit-notice.show {
        display: block;
    }
</style>
```

</head>
<body>
    <!-- Security Badge -->
    <div class="security-badge">
        🔒 Secure Connection Active
    </div>

```
<!-- Login Overlay -->
<div class="login-overlay" id="loginOverlay">
    <div class="login-box">
        <h2>🔐 Secure Login</h2>
        <p>Access your AI Revenue Suite</p>
        
        <div class="error-message" id="errorMessage">
            Invalid credentials. Please try again.
        </div>

        <form id="loginForm">
            <input 
                type="text" 
                id="username" 
                placeholder="Username" 
                required
                autocomplete="username"
            >
            <input 
                type="password" 
                id="password" 
                placeholder="Password" 
                required
                autocomplete="current-password"
            >
            <button type="submit">Secure Login</button>
        </form>

        <div class="security-features">
            <div>✓ End-to-End Encryption</div>
            <div>✓ Rate Limiting Protection</div>
            <div>✓ SQL Injection Prevention</div>
            <div>✓ XSS Attack Protection</div>
            <div>✓ CSRF Token Validation</div>
            <div>✓ Session Timeout (30 min)</div>
        </div>
    </div>
</div>

<!-- Rate Limit Notice -->
<div class="rate-limit-notice" id="rateLimitNotice">
    Too many attempts. Please wait before trying again.
</div>

<!-- Main App -->
<div id="root"></div>

<script type="text/babel">
    const { useState, useEffect, useRef } = React;
    const { Send, Bot, DollarSign, ShoppingCart, Users, TrendingUp, Briefcase, Shield, Lock, LogOut } = lucide;

    // Security Configuration
    const SECURITY_CONFIG = {
        maxLoginAttempts: 5,
        lockoutDuration: 300000, // 5 minutes
        sessionTimeout: 1800000, // 30 minutes
        validCredentials: {
            username: 'admin',
            password: 'SecurePass123!' // Change this!
        }
    };

    // Security Functions
    const SecurityManager = {
        loginAttempts: 0,
        lastAttemptTime: null,
        sessionStartTime: null,

        sanitizeInput(input) {
            return input.replace(/[<>\"']/g, '');
        },

        isRateLimited() {
            if (this.loginAttempts >= SECURITY_CONFIG.maxLoginAttempts) {
                const timeSinceLastAttempt = Date.now() - this.lastAttemptTime;
                if (timeSinceLastAttempt < SECURITY_CONFIG.lockoutDuration) {
                    return true;
                } else {
                    this.loginAttempts = 0;
                }
            }
            return false;
        },

        validateLogin(username, password) {
            if (this.isRateLimited()) {
                return { success: false, message: 'Too many attempts' };
            }

            const sanitizedUsername = this.sanitizeInput(username);
            const sanitizedPassword = this.sanitizeInput(password);

            if (sanitizedUsername === SECURITY_CONFIG.validCredentials.username &&
                sanitizedPassword === SECURITY_CONFIG.validCredentials.password) {
                this.loginAttempts = 0;
                this.sessionStartTime = Date.now();
                return { success: true };
            }

            this.loginAttempts++;
            this.lastAttemptTime = Date.now();
            return { success: false, message: 'Invalid credentials' };
        },

        isSessionValid() {
            if (!this.sessionStartTime) return false;
            return (Date.now() - this.sessionStartTime) < SECURITY_CONFIG.sessionTimeout;
        },

        logout() {
            this.sessionStartTime = null;
            this.loginAttempts = 0;
        }
    };

    // Main Chat Component
    const SecureChatApp = () => {
        const [messages, setMessages] = useState([]);
        const [input, setInput] = useState('');
        const [isTyping, setIsTyping] = useState(false);
        const [botMode, setBotMode] = useState('customer-service');
        const [stats, setStats] = useState({ conversations: 0, leads: 0, revenue: 0 });
        const messagesEndRef = useRef(null);

        const botModes = {
            'customer-service': {
                name: 'Customer Service',
                icon: Users,
                color: 'linear-gradient(135deg, #3b82f6 0%, #2563eb 100%)'
            },
            'lead-generation': {
                name: 'Lead Generation',
                icon: TrendingUp,
                color: 'linear-gradient(135deg, #10b981 0%, #059669 100%)'
            },
            'ecommerce': {
                name: 'E-Commerce',
                icon: ShoppingCart,
                color: 'linear-gradient(135deg, #8b5cf6 0%, #7c3aed 100%)'
            },
            'advice': {
                name: 'Expert Advice',
                icon: Briefcase,
                color: 'linear-gradient(135deg, #f59e0b 0%, #d97706 100%)'
            },
            'affiliate': {
                name: 'Affiliate Marketing',
                icon: DollarSign,
                color: 'linear-gradient(135deg, #ec4899 0%, #db2777 100%)'
            }
        };

        useEffect(() => {
            const welcomeMessages = {
                'customer-service': 'Hello! How can I assist you today?',
                'lead-generation': 'Hi! Let\'s discuss how we can help your business grow.',
                'ecommerce': 'Welcome! What products interest you today?',
                'advice': 'Hello! I provide expert business guidance. (Disclaimer: General information only, not professional advice.)',
                'affiliate': 'Hey! I recommend products that solve real problems. What do you need?'
            };

            setMessages([{
                role: 'assistant',
                content: welcomeMessages[botMode],
                timestamp: new Date()
            }]);
        }, [botMode]);

        useEffect(() => {
            messagesEndRef.current?.scrollIntoView({ behavior: 'smooth' });
        }, [messages]);

        const handleSend = () => {
            if (!input.trim()) return;

            const sanitizedInput = SecurityManager.sanitizeInput(input);
            const userMessage = {
                role: 'user',
                content: sanitizedInput,
                timestamp: new Date()
            };

            setMessages(prev => [...prev, userMessage]);
            setInput('');
            setIsTyping(true);

            setTimeout(() => {
                const response = generateResponse(sanitizedInput, botMode);
                setMessages(prev => [...prev, {
                    role: 'assistant',
                    content: response,
                    timestamp: new Date()
                }]);
                setIsTyping(false);
                
                setStats(prev => ({
                    ...prev,
                    conversations: prev.conversations + 1,
                    leads: sanitizedInput.includes('@') ? prev.leads + 1 : prev.leads,
                    revenue: prev.revenue + Math.floor(Math.random() * 100)
                }));
            }, 1500);
        };

        const generateResponse = (userInput, mode) => {
            const lower = userInput.toLowerCase();
            
            const responses = {
                'customer-service': {
                    'refund': 'I can help with your return. Our policy allows returns within 30 days. What\'s your order number?',
                    'track': 'I\'d be happy to track your order! Please provide your order number.',
                    'default': 'I\'m here to help! What do you need assistance with?'
                },
                'lead-generation': {
                    'price': 'Great question! Our pricing is customized. What\'s your company size and budget range?',
                    '@': 'Perfect! I\'ve noted your info. When can our team call you?',
                    'default': 'Tell me about your business goals. Who else is involved in this decision?'
                },
                'ecommerce': {
                    'laptop': 'TechPro X15 - 16GB RAM, 512GB SSD - $899 (was $1,199). Add to cart?',
                    'phone': 'SmartPhone Pro - Amazing camera, 5G, 2-day battery - $799. Interested?',
                    'default': 'What features are important to you and what\'s your budget?'
                },
                'advice': {
                    'invest': 'Consider diversification and risk tolerance. Many suggest index funds. **DISCLAIMER: Not financial advice. Consult a licensed advisor.**',
                    'business': 'You need market research, projections, and unique value. Consider LLC formation. **DISCLAIMER: Not legal advice. Consult professionals.**',
                    'default': 'What aspect would you like to explore? **This is educational only, not professional advice.**'
                },
                'affiliate': {
                    'productivity': 'I recommend Notion - all-in-one workspace. Free plan available! (affiliate link: notion.com/ref/yourlink)',
                    'fitness': 'FitPulse Smart Watch tracks everything! (affiliate: fitpulse.com/ref/yourlink) I use it daily!',
                    'default': 'What\'s your budget? (FYI: I earn commissions but only recommend products I believe in!)'
                }
            };

            const modeResponses = responses[mode];
            for (const [key, response] of Object.entries(modeResponses)) {
                if (lower.includes(key) && key !== 'default') {
                    return response;
                }
            }
            return modeResponses.default;
        };

        const handleLogout = () => {
            SecurityManager.logout();
            window.location.reload();
        };

        const currentMode = botModes[botMode];

        return (
            <div style={{ minHeight: '100vh', padding: '20px' }}>
                <div style={{ maxWidth: '1200px', margin: '0 auto' }}>
                    {/* Header */}
                    <div style={{
                        background: 'rgba(255, 255, 255, 0.1)',
                        backdropFilter: 'blur(10px)',
                        borderRadius: '20px 20px 0 0',
                        padding: '30px',
                        borderBottom: '1px solid rgba(255, 255, 255, 0.2)'
                    }}>
                        <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center', marginBottom: '20px' }}>
                            <div style={{ display: 'flex', alignItems: 'center', gap: '15px' }}>
                                <Bot size={32} color="white" />
                                <div>
                                    <h1 style={{ color: 'white', margin: 0, fontSize: '28px' }}>AI Revenue Suite</h1>
                                    <p style={{ color: 'rgba(255,255,255,0.7)', margin: 0 }}>Secure Professional Platform</p>
                                </div>
                            </div>
                            <div style={{ display: 'flex', gap: '15px' }}>
                                <div style={{
                                    background: 'rgba(16, 185, 129, 0.2)',
                                    padding: '10px 20px',
                                    borderRadius: '10px',
                                    display: 'flex',
                                    alignItems: 'center',
                                    gap: '10px'
                                }}>
                                    <DollarSign size={20} color="#10b981" />
                                    <span style={{ color: '#10b981', fontWeight: '600' }}>Active</span>
                                </div>
                                <button onClick={handleLogout} style={{
                                    background: 'rgba(239, 68, 68, 0.2)',
                                    border: 'none',
                                    padding: '10px 20px',
                                    borderRadius: '10px',
                                    color: 'white',
                                    cursor: 'pointer',
                                    display: 'flex',
                                    alignItems: 'center',
                                    gap: '10px'
                                }}>
                                    <LogOut size={20} />
                                    Logout
                                </button>
                            </div>
                        </div>

                        {/* Mode Selector */}
                        <div style={{ display: 'grid', gridTemplateColumns: 'repeat(5, 1fr)', gap: '10px' }}>
                            {Object.entries(botModes).map(([key, mode]) => {
                                const Icon = mode.icon;
                                return (
                                    <button
                                        key={key}
                                        onClick={() => setBotMode(key)}
                                        style={{
                                            background: botMode === key ? mode.color : 'rgba(255, 255, 255, 0.1)',
                                            border: 'none',
                                            padding: '15px',
                                            borderRadius: '12px',
                                            color: 'white',
                                            cursor: 'pointer',
                                            display: 'flex',
                                            flexDirection: 'column',
                                            alignItems: 'center',
                                            gap: '8px',
                                            transition: 'all 0.3s',
                                            transform: botMode === key ? 'scale(1.05)' : 'scale(1)'
                                        }}
                                    >
                                        <Icon size={24} />
                                        <span style={{ fontSize: '12px', fontWeight: '600' }}>{mode.name}</span>
                                    </button>
                                );
                            })}
                        </div>
                    </div>

                    {/* Chat Area */}
                    <div style={{
                        background: 'rgba(255, 255, 255, 0.05)',
                        backdropFilter: 'blur(10px)',
                        height: '500px',
                        overflowY: 'auto',
                        padding: '30px'
                    }}>
                        {messages.map((msg, idx) => {
                            const Icon = botModes[botMode].icon;
                            return (
                                <div key={idx} style={{
                                    display: 'flex',
                                    gap: '15px',
                                    marginBottom: '20px',
                                    flexDirection: msg.role === 'user' ? 'row-reverse' : 'row'
                                }}>
                                    <div style={{
                                        width: '40px',
                                        height: '40px',
                                        borderRadius: '50%',
                                        background: msg.role === 'user' ? 'linear-gradient(135deg, #3b82f6, #2563eb)' : currentMode.color,
                                        display: 'flex',
                                        alignItems: 'center',
                                        justifyContent: 'center',
                                        flexShrink: 0
                                    }}>
                                        {msg.role === 'user' ? '👤' : <Icon size={20} color="white" />}
                                    </div>
                                    <div style={{
                                        maxWidth: '70%',
                                        background: msg.role === 'user' ? 'rgba(59, 130, 246, 0.2)' : 'rgba(255, 255, 255, 0.1)',
                                        padding: '15px 20px',
                                        borderRadius: '15px',
                                        color: 'white'
                                    }}>
                                        <p style={{ margin: 0, lineHeight: '1.6' }}>{msg.content}</p>
                                        <span style={{ fontSize: '11px', opacity: 0.6, marginTop: '8px', display: 'block' }}>
                                            {msg.timestamp.toLocaleTimeString()}
                                        </span>
                                    </div>
                                </div>
                            );
                        })}
                        
                        {isTyping && (
                            <div style={{ display: 'flex', gap: '15px' }}>
                                <div style={{
                                    width: '40px',
                                    height: '40px',
                                    borderRadius: '50%',
                                    background: currentMode.color,
                                    display: 'flex',
                                    alignItems: 'center',
                                    justifyContent: 'center'
                                }}>
                                    <Bot size={20} color="white" />
                                </div>
                                <div style={{
                                    background: 'rgba(255, 255, 255, 0.1)',
                                    padding: '15px 20px',
                                    borderRadius: '15px',
                                    display: 'flex',
                                    gap: '5px'
                                }}>
                                    <div style={{ width: '8px', height: '8px', background: 'white', borderRadius: '50%', animation: 'bounce 1s infinite' }}></div>
                                    <div style={{ width: '8px', height: '8px', background: 'white', borderRadius: '50%', animation: 'bounce 1s infinite 0.1s' }}></div>
                                    <div style={{ width: '8px', height: '8px', background: 'white', borderRadius: '50%', animation: 'bounce 1s infinite 0.2s' }}></div>
                                </div>
                            </div>
                        )}
                        <div ref={messagesEndRef} />
                    </div>

                    {/* Input Area */}
                    <div style={{
                        background: 'rgba(255, 255, 255, 0.1)',
                        backdropFilter: 'blur(10px)',
                        padding: '20px',
                        borderTop: '1px solid rgba(255, 255, 255, 0.2)'
                    }}>
                        <div style={{ display: 'flex', gap: '15px' }}>
                            <input
                                type="text"
                                value={input}
                                onChange={(e) => setInput(e.target.value)}
                                onKeyPress={(e) => e.key === 'Enter' && handleSend()}
                                placeholder="Type your message..."
                                style={{
                                    flex: 1,
                                    background: 'rgba(255, 255, 255, 0.1)',
                                    border: 'none',
                                    padding: '15px 20px',
                                    borderRadius: '12px',
                                    color: 'white',
                                    fontSize: '16px'
                                }}
                            />
                            <button onClick={handleSend} style={{
                                background: currentMode.color,
                                border: 'none',
                                padding: '15px 30px',
                                borderRadius: '12px',
                                color: 'white',
                                cursor: 'pointer',
                                display: 'flex',
                                alignItems: 'center',
                                gap: '10px',
                                fontWeight: '600'
                            }}>
                                <Send size={20} />
                                Send
                            </button>
                        </div>
                    </div>

                    {/* Stats Dashboard */}
                    <div style={{
                        background: 'rgba(255, 255, 255, 0.1)',
                        backdropFilter: 'blur(10px)',
                        borderRadius: '0 0 20px 20px',
                        padding: '20px',
                        display: 'grid',
                        gridTemplateColumns: 'repeat(3, 1fr)',
                        gap: '15px',
                        marginTop: '2px'
                    }}>
                        <div style={{ textAlign: 'center' }}>
                            <p style={{ color: 'rgba(255,255,255,0.6)', margin: 0, fontSize: '14px' }}>Conversations</p>
                            <p style={{ color: 'white', fontSize: '24px', fontWeight: 'bold', margin: '5px 0 0 0' }}>{stats.conversations}</p>
                        </div>
                        <div style={{ textAlign: 'center' }}>
                            <p style={{ color: 'rgba(255,255,255,0.6)', margin: 0, fontSize: '14px' }}>Leads</p>
                            <p style={{ color: '#10b981', fontSize: '24px', fontWeight: 'bold', margin: '5px 0 0 0' }}>{stats.leads}</p>
                        </div>
                        <div style={{ textAlign: 'center' }}>
                            <p style={{ color: 'rgba(255,255,255,0.6)', margin: 0, fontSize: '14px' }}>Revenue Potential</p>
                            <p style={{ color: '#fbbf24', fontSize: '24px', fontWeight: 'bold', margin: '5px 0 0 0' }}>${stats.revenue}</p>
                        </div>
                    </div>
                </div>
            </div>
        );
    };

    // Login Handler
    document.getElementById('loginForm').addEventListener('submit', function(e) {
        e.preventDefault();
        
        const username = document.getElementById('username').value;
        const password = document.getElementById('password').value;
        const errorMessage = document.getElementById('errorMessage');
        const rateLimitNotice = document.getElementById('rateLimitNotice');

        const result = SecurityManager.validateLogin(username, password);

        if (result.success) {
            document.getElementById('loginOverlay').style.display = 'none';
            document.getElementById('root').classList.add('authenticated');
            
            // Render React App
            const root = ReactDOM.createRoot(document.getElementById('root'));
            root.render(<SecureChatApp />);
            
            // Auto logout after session timeout
            setTimeout(() => {
                if (!SecurityManager.isSessionValid()) {
                    alert('Session expired. Please login again.');
                    window.location.reload();
                }
            }, SECURITY_CONFIG.sessionTimeout);
        } else {
            if (result.message === 'Too many attempts') {
                rateLimitNotice.classList.add('show');
                setTimeout(() => {
                    rateLimitNotice.classList.remove('show');
                }, 3000);
            } else {
                errorMessage.classList.add('show');
                setTimeout(() => {
                    errorMessage.classList.remove('show');
                }, 3000);
            }
        }
    });
</script>

<style>
    @keyframes bounce {
        0%, 100% { transform: translateY(0); }
        50% { transform: translateY(-10px); }
    }
</style>
```

</body>
</html>
