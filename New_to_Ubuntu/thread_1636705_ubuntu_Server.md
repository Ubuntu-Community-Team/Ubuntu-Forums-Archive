---
title: "ubuntu Server"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by vrao123 on 2010-12-03
Hello:
 
I have downloaded and installed ubuntu server (64 bit) ver 10.10 and installed it on my VMWare virtual machine. I also have GNOME 2.32.0 version installed. When I select from the menu Applications-->Programming-->Root, I am seeing the following error message:
 
**Could not launch 'ROOT'**
**Failed to execute child process**
**'xterm' (No such file or directory)**
 
BTW, I am quite new to Linux and wants to access the command line window. I am assuming by accessing Root from above said menu, I will be able to see the command line window or shell window and I can type Linux commands.
 
Thoughts on the above please.
 
Also, I was looking at the Gnome interface and when I click on a folder, select Properties, I see that, I am not the owner of the concerned folder. I thought, when I installed the ubuntu, I was the administrator or the root user and could change anything? Thoughts on this question as well please.
 
Will appreciate your early response as I need to work on an urgent project. Thanks!
 
Sincerely,
 
Victor

---

### Post by Zzl1xndd on 2010-12-03
To access the Terminal it should be Applications > Accessories > Terminal. From here you should be able to enter commands. 

In Ubuntu the Root user is not enabled. Enter "sudo" before any command and it will prompt you for your password and give you root access temporarily.

---

### Post by drdos2006 on 2010-12-03
When you start your server you should see a terminal with the user name entered at setup time. After boot the screen should ask you to login with that username and the password for that username in order to continue.  Once the username and password are entered the server should be running with any software you may have installed during the setup proces. eg Apache, MySql Php etc. Once you have your server running, install Webmin and control your server from your browser.

regards

---

