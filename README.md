# CodeReview AI - AI-Powered Code Analysis & Rewrite Agent

An intelligent web application that uses **Gemini AI** to analyze source code and provide comprehensive reviews including bug detection, performance optimization, security audits, and best practice recommendations with AI-powered code rewrites.

## 🎯 Overview

**CodeReview AI** is a full-stack web application built with modern technologies to help developers identify issues in their code and receive AI-generated optimizations. The application analyzes code for:

- 🐛 **Bug Detection** - Find logic errors, null references, race conditions, edge cases
- ⚡ **Performance Issues** - Identify inefficient algorithms, memory leaks, N+1 queries
- 🔒 **Security Vulnerabilities** - Detect security flaws and unsafe practices
- 📚 **Best Practice Violations** - Ensure code follows industry standards
- ✨ **Code Rewrite** - Get AI-optimized version of your code

## 🏗️ Architecture

### Tech Stack

**Frontend:**
- **Next.js 16** - React framework with App Router
- **TypeScript** - Type-safe development
- **Tailwind CSS 4** - Utility-first CSS framework
- **shadcn/ui** - High-quality React components
- **Framer Motion** - Smooth animations and transitions
- **Zustand** - Lightweight state management
- **React Hook Form** - Efficient form handling
- **MDXEditor** - Rich code editing

**Backend:**
- **Next.js API Routes** - Serverless API endpoints
- **NextAuth.js** - Authentication and authorization
- **Prisma** - ORM for database operations
- **SQLite** - Lightweight database
- **Gemini AI SDK** - AI-powered code analysis

**Authentication:**
- Email/Password authentication
- Session-based auth with NextAuth.js
- Secure password hashing with bcryptjs

**Additional Tools:**
- **TanStack React Table** - Data table management
- **TanStack React Query** - Server state management
- **Recharts** - Data visualization
- **Sonner** - Toast notifications
- **React Markdown** - Markdown rendering
- **DND Kit** - Drag and drop functionality

## 📁 Project Structure

```
.
├── src/
│   ├── app/
│   │   ├── api/
│   │   │   ├── auth/              # NextAuth authentication endpoints
│   │   │   ├── review/            # Code review API endpoint
│   │   │   └── reviews/           # Review history endpoint
│   │   ├── layout.tsx             # Root layout with providers
│   │   ├── page.tsx               # Main application page
│   │   └── globals.css            # Global styles
│   ├── components/
│   │   ├── ui/                    # shadcn/ui components
│   │   ├── code-review/           # Feature components
│   │   │   ├── code-editor.tsx    # Code input component
│   │   │   ├── review-options.tsx # Analysis options selector
│   │   │   ├── results-panel.tsx  # Results display
│   │   │   └── review-history.tsx # Historical reviews
│   │   └── ...
│   ├── hooks/                     # Custom React hooks
│   ├── lib/
│   │   ├── auth.ts                # NextAuth configuration
│   │   ├── db.ts                  # Database client
│   │   └── utils.ts               # Utility functions
│   └── store/
│       └── code-review.ts         # Zustand store for state management
├── prisma/
│   └── schema.prisma              # Database schema
├── public/                        # Static assets
├── package.json                   # Dependencies
├── tsconfig.json                  # TypeScript configuration
├── tailwind.config.ts             # Tailwind CSS configuration
└── next.config.ts                 # Next.js configuration
```

## 🗄️ Database Schema

### User Model
- `id` - Unique user identifier (CUID)
- `name` - User's full name
- `email` - Unique email address
- `password` - Hashed password
- `createdAt` - Account creation timestamp
- `updatedAt` - Last update timestamp
- `reviews` - Relation to code reviews

### CodeReview Model
- `id` - Unique review identifier
- `title` - Review title
- `language` - Programming language
- `code` - Original source code
- `findings` - JSON array of findings
- `rewrite` - AI-generated optimized code
- `summary` - Review summary
- `bugCount` - Number of bugs found
- `performanceCount` - Performance issues count
- `securityCount` - Security vulnerabilities count
- `bestPracticeCount` - Best practice violations count
- `userId` - Foreign key to User
- `createdAt` / `updatedAt` - Timestamps

## 🚀 Key Features

### 1. **Code Analysis Engine**
- Comprehensive code review using Gemini AI
- Multi-aspect analysis (bugs, performance, security, best practices)
- Detailed findings with line numbers and recommendations
- Categorized issues with severity levels

### 2. **Authentication & Security**
- Secure user registration and login
- Session-based authentication with NextAuth.js
- Password hashing with bcryptjs
- Protected API endpoints

### 3. **User Dashboard**
- Review history with metadata
- Quick access to previous analyses
- Statistics and insights display
- Dark/Light theme support

### 4. **Code Editor**
- Syntax-highlighted code input
- File upload support
- Sample code for quick testing
- Language detection and selection

### 5. **Results Display**
- Categorized findings presentation
- AI-generated code rewrites
- Summary and recommendations
- Export capabilities

### 6. **Responsive Design**
- Mobile-first approach
- Desktop and tablet optimized
- Touch-friendly interface
- Progressive enhancement

## 🔑 Key Components

### `CodeEditor`
Manages code input with:
- Syntax highlighting
- File upload
- Language selection
- Sample code loading

### `ReviewOptions`
Allows users to select analysis aspects:
- Bug detection
- Performance analysis
- Security audit
- Best practice review

### `ResultsPanel`
Displays analysis results with:
- Finding categorization
- Code rewrite preview
- Statistics overview
- Action buttons

### `ReviewHistory`
Shows past reviews with:
- Chronological listing
- Quick reload functionality
- Summary information
- Click-to-load results

## 📡 API Endpoints

### Authentication
- `POST /api/auth/...` - NextAuth.js auth routes

### Code Review
- `POST /api/review` - Submit code for analysis
  - **Body**: `{ code: string, language: string, options: string[] }`
  - **Response**: `{ findings: Finding[], rewrite: string, summary: string, stats: Stats }`

### Review History
- `GET /api/reviews` - Fetch user's review history
  - **Response**: `CodeReview[]`

## 🔐 Authentication Flow

1. User signs up with email and password
2. Password is hashed with bcryptjs
3. User credentials stored in database
4. NextAuth.js manages session creation
5. Session token validated for protected routes
6. Token attached to API requests

## 🤖 AI Analysis Process

### System Prompt
The application builds dynamic system prompts that:
1. Enable/disable specific checks based on user selection
2. Provide detailed instructions for bug detection
3. Guide performance analysis with specific criteria
4. Define security vulnerability patterns
5. Establish best practice standards

### Analysis Steps
1. Code received and validated
2. System prompt constructed based on options
3. Gemini AI analyzes code with structured prompt
4. Findings parsed and categorized
5. Code rewrite generated
6. Results stored in database
7. Response returned to frontend

## 🎨 UI/UX Features

### Theme Support
- Light mode (default)
- Dark mode
- System preference detection
- Persistent theme selection

### Animations
- Smooth page transitions with Framer Motion
- Loading states with spinners
- Toast notifications for feedback
- Card animations

### Responsive Layouts
- Grid system adapts to screen size
- Mobile-optimized navigation
- Sticky headers and sidebars
- Flexible spacing

## 🛠️ Development

### Setup

```bash
# Install dependencies
npm install
# or
bun install

# Set up environment variables
cp .env.example .env.local

# Initialize database
npx prisma db push

# Run development server
npm run dev
```

### Environment Variables

```env
DATABASE_URL=file:./db/dev.db
NEXTAUTH_URL=http://localhost:3000
NEXTAUTH_SECRET=your-secret-key
GEMINI_API_KEY=your-gemini-api-key
```

### Database Commands

```bash
# Push schema to database
npm run db:push

# Generate Prisma client
npm run db:generate

# Create migration
npm run db:migrate

# Reset database
npm run db:reset
```

### Build & Deploy

```bash
# Build for production
npm run build

# Start production server
npm run start

# Lint code
npm run lint
```

## 📊 Finding Categories

### Bug
- Logic errors
- Null/undefined references
- Race conditions
- Type mismatches
- Unhandled edge cases
- Missing error handling

### Performance
- Inefficient algorithms
- Memory leaks
- N+1 query patterns
- Missing caching
- Unnecessary computations

### Security
- Input validation gaps
- SQL injection risks
- XSS vulnerabilities
- Authentication flaws
- Data exposure risks

### Best Practice
- Code organization
- Naming conventions
- Documentation gaps
- Error handling patterns
- API usage correctness

## 🎯 Workflow

1. **User Authentication** → Sign in or register
2. **Code Input** → Paste code, upload file, or use sample
3. **Select Options** → Choose analysis aspects
4. **Submit Review** → Trigger AI analysis
5. **View Results** → Examine findings and rewrite
6. **Save History** → Automatically stored for future reference
7. **Export/Share** → Download or share results

## 🔍 Code Quality Metrics

The application provides comprehensive metrics:
- **Bug Count** - Total logic and runtime errors found
- **Performance Count** - Optimization opportunities identified
- **Security Count** - Vulnerabilities and risks detected
- **Best Practice Count** - Standards violations noted

## 📱 Responsive Breakpoints

- **Mobile** - < 640px (full-width layout)
- **Tablet** - 640px - 1024px (optimized layout)
- **Desktop** - > 1024px (two-column layout)

## 🔒 Security Features

- ✅ Password hashing with bcryptjs
- ✅ Session-based authentication
- ✅ Protected API endpoints
- ✅ CORS configuration
- ✅ Input validation and sanitization
- ✅ Environment variable protection

## 📈 Performance Optimizations

- Server-side rendering with Next.js
- Code splitting and lazy loading
- Image optimization
- CSS-in-JS with Tailwind
- React Query for caching
- Database query optimization with Prisma

## 🌐 Deployment Considerations

- **Database**: Use SQLite for development, PostgreSQL for production
- **Environment**: Configure NextAuth secrets
- **API Keys**: Store Gemini API key securely
- **Build**: Optimize for serverless or traditional servers
- **Monitoring**: Implement error tracking and analytics

## 🐛 Known Limitations

- SQLite suitable for single-server deployments
- Gemini API rate limits apply
- Session storage in-memory (configure for production)
- Code file size limits apply

## 🚀 Future Enhancements

- Multi-language support
- Team collaboration features
- Batch code analysis
- Integration with GitHub/GitLab
- Custom analysis templates
- Advanced filtering and search
- Export to PDF/CSV
- API rate limiting dashboard
- Webhooks for automation

## 📄 License

This project is part of a development workspace.

## 👨‍💻 Technologies Summary

| Layer | Technologies |
|-------|--------------|
| **Frontend Framework** | Next.js 16, React 19, TypeScript |
| **Styling** | Tailwind CSS 4, shadcn/ui |
| **State Management** | Zustand, React Query |
| **Forms** | React Hook Form, Zod validation |
| **UI/UX** | Framer Motion, Lucide Icons |
| **Backend** | Next.js API Routes, Prisma ORM |
| **Authentication** | NextAuth.js, bcryptjs |
| **Database** | SQLite (Prisma) |
| **AI/ML** | Gemini AI SDK |
| **Tables** | TanStack React Table |
| **Notifications** | Sonner Toast |
| **Version Control** | Git |
| **Package Manager** | Bun/npm |

## 📞 Support

For issues or questions, refer to the application's error messages and logs:
- Check browser console for client-side errors
- Review server logs in `dev.log` or `server.log`
- Validate database connection in `.env.local`

---

**Last Updated**: July 2026  
**Version**: 0.2.1  
**Status**: Active Development
