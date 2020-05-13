**DevOps Project 2 :**

Step - 1: I have created a container image that has Jenkins installed using Dockerfile.

The commands in Dockerfile are as follows--



I have used Centos latest version. We need to install sudo & wget because they will be furthur needed in the installation of Jenkins. Then we have installed Jenkins & the suitable jdk version. 
Since systemctl doesn't work in Centos, so we would require to use _**sudo service jenkins start**_ command. But service command isn't avvailable in Centos latest image. So, we have installed _**/sbin/service**_
We have also installed git because we'll need it later. The third last line is to give powers to jenkins to perform operations inside the container.
The, we have started the Jenkins by _**sudo service jenkins start**_ but we also need to start _**/bin/bash**_ otherwise the container will close as soon as jenkins starts because there will be no tasks left. Hence, we also start the bash in same coomand.

**Note : The bash has to be started in the same command because if there are more than one commands in the Dockerfile, then only the last command runs.**

After that, we have exposed Port 8080 because Jenkins runs on port 8080.


![](/j2/df.png)



Step - 2: Now, we move on to our Jenkins tasks.

**TASK 1 : Production**
  In this task, the code will be auto downloaded from Github. For this, I have used trigger method. 
  
  ![](/j2/prod1.png)
  
  
  ![](/j2/prod2.png)
  
  The trigger would work and I have provided the link along with the authentication token to my local git. As soon as any code is    pushed, Git hook would work & run this task automatically.
  In the execute shell section, The webpages are being downloaded to this folder inside the container.
  
  ![](/j2/prod3.png)
  
  **TASK 2 : Transfer**
   In this task, the web pages downloaded inside the container are being transferred to the base Redhat using scp. I have already   authorized a ssh key from my container to Redhat.
   
   ![](/j2/transfer.png)













