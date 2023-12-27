Step 1: Create the Workflow File
Navigate to Your Repository: Go to your GitHub repository.

Create a Workflow Directory: Inside your repository, create a .github/workflows directory if it doesn't exist.

Create a Workflow File: Inside the workflows directory, create a YAML file (e.g., ci.yml) for your workflow.

Step 2: Define the Workflow in YAML
Inside the YAML file, define the workflow to execute on each push event to your repository. Here's an example configuration:

yaml
Copy code
name: CI

on:
  push:
    branches: [ main ] # Define the branch to trigger the workflow on push events

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout Repository
      uses: actions/checkout@v2

    - name: Setup Node.js
      uses: actions/setup-node@v2
      with:
        node-version: '14' # Specify the Node.js version

    - name: Install Dependencies
      run: npm install # Install Node.js dependencies

    - name: Run Tests
      run: npm test # Execute tests
Step 3: Commit and Push the Workflow File
Save Changes: Save the YAML file in the .github/workflows directory within your repository.

Commit Changes: Commit this new file to your repository. You can do this via the GitHub web interface or using Git commands:

bash
Copy code
git add .github/workflows/ci.yml
git commit -m "Add CI workflow"
git push origin main
Step 4: Check GitHub Actions Tab
After pushing the changes, go to the "Actions" tab in your GitHub repository. You should see your workflow listed and executing or waiting for triggers based on the defined events.

Step 5: Monitor Workflow Execution
Whenever a commit is pushed to the main branch, the GitHub Actions workflow will trigger. It will perform a checkout of the repository, set up the Node.js environment, install dependencies, and execute tests defined in your project.

You can monitor the workflow's progress, view logs, and check for any errors or failures in the "Actions" tab. This basic workflow ensures that tests are run automatically upon each commit to maintain code quality and catch issues early in the development process.






