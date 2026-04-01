# 🚀 Render + Vercel Deployment Guide

## 📋 Overview
- **Backend**: Render (Node.js)
- **Frontend**: Vercel (React)
- **Database**: MongoDB Atlas
- **Email**: Gmail SMTP

## 🎯 Step-by-Step Deployment

### **Step 1: Prepare Local Environment**

1. **Create production environment files:**
```bash
# Backend environment (create this file manually)
# backend/config.env
NODE_ENV=production
PORT=5000
MONGODB_URI=mongodb+srv://satputesahil8186_db_user:2MSaBOA2RVtmkB0s@cluster0.wbvxrek.mongodb.net/queue_system?retryWrites=true&w=majority
JWT_SECRET=queue_system_production_jwt_secret_key_minimum_32_characters_long_secure_2024
JWT_EXPIRES_IN=7d
OTP_EXPIRY_MINUTES=10
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=satputesahil8186@gmail.com
SMTP_PASS=vlec ipqm cmdd mcnv
SMTP_FROM=Queue System <noreply@queuesystem.dev]
FRONTEND_URL=https://queue-system-frontend.vercel.app

# Frontend environment (already created)
# frontend/vite-project/.env.production
VITE_API_URL=https://queue-system-api.onrender.com
VITE_APP_NAME=Queue System
```

### **Step 2: Deploy Backend on Render**

1. **Go to [https://render.com](https://render.com)**
2. **Sign up** and **connect GitHub**
3. **Create New Web Service:**
   - **Repository**: queue-system
   - **Name**: queue-system-api
   - **Root Directory**: backend
   - **Runtime**: Node
   - **Build Command**: npm install
   - **Start Command**: node server.js
   - **Plan**: Free

4. **Add Environment Variables** (in Render Dashboard):
```
NODE_ENV=production
MONGODB_URI=mongodb+srv://satputesahil8186_db_user:2MSaBOA2RVtmkB0s@cluster0.wbvxrek.mongodb.net/queue_system?retryWrites=true&w=majority
JWT_SECRET=queue_system_production_jwt_secret_key_minimum_32_characters_long_secure_2024
JWT_EXPIRES_IN=7d
OTP_EXPIRY_MINUTES=10
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=satputesahil8186@gmail.com
SMTP_PASS=vlec ipqm cmdd mcnv
SMTP_FROM=Queue System <noreply@queuesystem.dev]
FRONTEND_URL=https://queue-system-frontend.vercel.app
```

5. **Click "Create Web Service"**
6. **Wait for deployment** and note the URL: `https://queue-system-api.onrender.com`

### **Step 3: Deploy Frontend on Vercel**

1. **Go to [https://vercel.com](https://vercel.com)**
2. **Sign up** and **connect GitHub**
3. **Import Project:**
   - **Repository**: queue-system
   - **Framework Preset**: Vite
   - **Root Directory**: frontend/vite-project
   - **Build Command**: npm run build
   - **Output Directory**: dist

4. **Add Environment Variables** (in Vercel Dashboard):
```
VITE_API_URL=https://queue-system-api.onrender.com
VITE_APP_NAME=Queue System
```

5. **Deploy** and note the URL: `https://queue-system-frontend.vercel.app`

### **Step 4: Update CORS Configuration**

1. **Go back to Render Dashboard**
2. **Edit your queue-system-api service**
3. **Environment tab**
4. **Update FRONTEND_URL** to your actual Vercel URL:
```
FRONTEND_URL=https://queue-system-frontend.vercel.app
```

5. **Save and redeploy**

### **Step 5: Test Everything**

1. **Backend Health Check:**
```bash
curl https://queue-system-api.onrender.com/health
```

2. **Frontend Access:**
   - Open `https://queue-system-frontend.vercel.app`
   - Test user registration with OTP
   - Test login functionality
   - Test password reset

3. **Test Email OTP:**
   - Register new user
   - Check email for OTP
   - Verify OTP works

## 🎯 Expected URLs

- **Backend API**: https://queue-system-api.onrender.com
- **Frontend App**: https://queue-system-frontend.vercel.app
- **Health Check**: https://queue-system-api.onrender.com/health

## 🔧 Troubleshooting

### **Common Issues:**

#### **Backend Issues:**
- **MongoDB Connection**: Check MONGODB_URI format
- **Email Not Sending**: Verify Gmail app password
- **CORS Errors**: Ensure FRONTEND_URL matches Vercel URL

#### **Frontend Issues:**
- **API Connection**: Check VITE_API_URL in Vercel env
- **Build Failures**: Check package.json scripts
- **404 Errors**: Check Vercel routing configuration

#### **Cross-Origin Issues:**
1. Update FRONTEND_URL in Render
2. Update VITE_API_URL in Vercel
3. Redeploy both services

## 📁 Files for Deployment

✅ **Backend Ready:**
- `render.yaml` - Render configuration
- `backend/config.env.example` - Environment template
- `backend/server.js` - Production ready
- `backend/package.json` - Updated metadata

✅ **Frontend Ready:**
- `vercel.json` - Vercel configuration
- `frontend/vite-project/.env.production` - Production env
- `frontend/vite-project/package.json` - Updated for Vercel

✅ **Git Ready:**
- `.gitignore` - Properly configured
- All sensitive files excluded
- Production files included

## 🎉 Success Checklist

- [ ] Backend deployed on Render
- [ ] Frontend deployed on Vercel
- [ ] Environment variables configured
- [ ] CORS properly set up
- [ ] Health endpoint working
- [ ] User registration with OTP works
- [ ] Login functionality works
- [ ] Password reset works
- [ ] Email OTP sending works
- [ ] No console errors in browser

## 🚀 Next Steps

1. **Monitor performance** on both platforms
2. **Set up custom domains** (optional)
3. **Configure analytics** (optional)
4. **Scale up resources** if needed
5. **Set up monitoring alerts**

Your Queue System is now live on Render + Vercel! 🎉
