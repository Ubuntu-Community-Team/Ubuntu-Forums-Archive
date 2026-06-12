---
title: "rdesktop and port redirection"
date: 2008-01-24
forum: Networking &amp; Wireless
---

### Post by rmishler on 2008-01-24
I have a number of clients that connect to Windows servers from Linux clients. All users connect using the Terminal Server Client available in Ubuntu. All Ubuntu installs are 7.10 or later. The problem we have been having is connecting printers and drives from the local client to the Windows desktop. The Terminal Server Client does not have a way to gracefully set port redirection through the GUI.  
I offer this post as an assistance to others that may be experiencing the same challenges. I'm sure there is a way to do this more gracefully. I look forward to you experts filling in the blanks. 

The command you need for port redirecting in rdesktop is: 
rdesktop <IP address of server:server port #(if required)> -r disk:v=/ -r printer:<name of printer installed on client> -f

-r redirects the device
-f runs the application in full screen mode
This command will create a mountable drive called drive V that you will see from the Windows File Explorer. 

I was not able to figure out how to change the underlying config file for the Linux Terminal Server Client so I created the rdesktop command in a separate file using gedit. I saved the file in /username/home/bin/rdesktop. I then went to the Linux desktop and created an icon for the user. The icon was created by right clicking on the mouse button and selecting "Create Launcher". This then let me select the command I wanted to run. 
Before you try to run the rdesktop command run chmod 755 <file name> on your rdesktop file. I found that things didn't work correctly until after I ran the chmod command.

---

