# How to create your flagship environment
## Please follow the steps to set up the environment.
### **Make sure your vpn is on before proceeding.**
  1. Generate public SSH key
  2. Create a role for your AWS
  3. Create a Development Environment
  
## Generate public SSH key
  1. Open your Terminal on your laptop and generate your SSH key by entering this command.
 ```bash
 ssh-keygen -t ed25519 -C "YOUR NAME HERE"
```
  2. Next it will ask you to provide a path to save the key. Copy the path shown in the brackets. 
 <br /> For example, /Users/firstname.lastname/.ssh/id_ed25519, and paste that path in and press enter.
 
  3. It will ask for to enter a password. In this step you do not need to enter one, so press enter to have no password.
 
  4. When all this completed, to confirm that your key has been saved to the correct path enter this command in Terminal.
  ```bash
  vim ~/.ssh/id_ed25519.pub
  ```
  
  ### **Note: If you do not see your key, it means you did not save it to the correct path, so begin from step 1 again and make sure the path to save is correct.**
  
  5. You should be able to see your public key on the top which starts with "ssh-ed25519". Copy this entire key and go to [authorized keys](https://github.com/Bynder/env-provisioning-scripts/blob/master/user_access/authorized_keys)
  
  6. Edit the file and paste your key on the bottom, and make sure 'Create a new brach for this commit and start a pull request' is picked, then press Propose changes.
  
  7. Once the pull request has been created, do not proceed to the other steps until the pull request has been approved and merged. To check the status press on Pull requests and check if your pull request exists, if it does not that means it has been approved and merged. If you still see it after 10 mins, enter the channel #b-help-dev-env on slack and ask for your pull request to be approved and merged.
  
## Create a role for your AWS

  1. Once the above has all been completed, go to your [Okta](https://bynder.okta.com/app/UserHome) and press on AWS in my apps.
  
  2. Then when you are logged on in AWS go to [Roles](https://signin.aws.amazon.com/switchrole?roleName=tf-development-cross-account-iam-developer&account=bynder-development) and enter a Display Name for your role e.g. dev, then press switch roles.
  
  3. After that, go back to your AWS and on the top right, switch the region to Frankfurt, and switch the role by press the down arrow next to your default role "tf-production-okta-idp-developer/firstname.lastname@bynder.com @ bynder" and on the bottom it will show your role history which you just created in step 2, press it to be that role.

## Create a Development Environment

  1. Then when all steps have been successfully completed, go to [Jenkins Provisional Environment](https://jenkins.shared.eu-west-1.bynder.cloud/job/bynder-github/job/env-provisioning-scripts/job/master/)
  
  2. Once there, press on Build now.
  
  3. When the build is in Run ansible script phase, hover over it and input your name and press ok. It will then take up to 30-40 mins to create the build.
  
  4. When all the boxes are green and it is successful, open your terminal 
