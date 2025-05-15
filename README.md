# Deploying FB Share Tool to Render

Follow these steps to deploy your Facebook Share Tool to Render:

## Step 1: Set Up Render Account

1. Go to [render.com](https://render.com) and sign up or log in
2. Connect your GitHub account to Render

## Step 2: Create a New Repository

1. Create a new repository on GitHub containing these files:
   - `app.py` (your main application file)
   - `render-requirements.txt` (dependencies)
   - `render.yaml` (Render configuration)
   - `.streamlit/config-render.toml` (Streamlit configuration for Render)

## Step 3: Deploy on Render

### Option 1: Deploy via Dashboard

1. Go to the Render dashboard
2. Click "New +" and select "Web Service"
3. Connect your GitHub repository
4. Configure as follows:
   - **Name**: fb-share-tool
   - **Runtime**: Python
   - **Build Command**: `pip install -r render-requirements.txt`
   - **Start Command**: `streamlit run app.py --server.port $PORT --server.address 0.0.0.0`
5. Click "Create Web Service"

### Option 2: Deploy via Blueprint (render.yaml)

1. Go to the Render dashboard
2. Click "New +" and select "Blueprint"
3. Connect to your repository containing the render.yaml file
4. Render will automatically detect and set up services based on render.yaml

## Step 4: Environment Variables (Optional)

If your app requires any environment secrets, add them in the Render dashboard under your service:
1. Go to your web service
2. Click "Environment" tab
3. Add the required environment variables

## Troubleshooting

If you encounter any issues:
1. Check the Render logs for error messages
2. Ensure your requirements.txt includes all dependencies
3. Make sure your app listens on the port provided by Render's $PORT environment variable

## Notes

- The app will be accessible at `https://fb-share-tool.onrender.com` (or similar URL assigned by Render)
- The free plan may have cold starts (first load might be slow)
- Render free tier has limitations on compute resources and usage time