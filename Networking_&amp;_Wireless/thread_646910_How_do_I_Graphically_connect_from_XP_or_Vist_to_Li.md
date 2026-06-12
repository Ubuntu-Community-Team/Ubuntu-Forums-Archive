---
title: "How do I Graphically connect from XP or Vist to Linux"
date: 2007-12-21
forum: Networking &amp; Wireless
---

### Post by tuproxy on 2007-12-21
I am running 7.10 on my host linux box.  What do I need to install on it to host a graphical remote desktop  session?

What client do I need to install on my XP and Vista machines?

Thanks

---

### Post by heatpumpcontrol on 2007-12-21
ubuntu comes with a Terminal Server Client installed. Just use that to connect to your Windows machines. Then to log into Ubuntu from Windows you have to:

System -->Preferences -->Remote Desktop. Enter your data and use a password if desired...recommended! 

Now install VNC (google it) and run the VNC viewer to view the Ubuntu machine.

Oh, make sure you have Windows Remote Desktop management enabled too so that you can log into the Windows machines.

---

### Post by tuproxy on 2007-12-22
I tried using the RDC from both Vista and XP, and get the same message, that it can not connect.  I've entered the username and password but still doesn't work.  

I've installed VNC viewer and when I tried to run it it locked up my host machine (my ubuntu box)

This is frustrating

---

### Post by heatpumpcontrol on 2007-12-22
> **tuproxy said:**
> I tried using the RDC from both Vista and XP, and get the same message, that it can not connect.  I've entered the username and password but still doesn't work.  

I've installed VNC viewer and when I tried to run it it locked up my host machine (my ubuntu box)

This is frustrating

OK. One step at a time here...
1- Go to each Windows machine that you want to connect to and 
right click on 'My Computer' --> Properties --> Remote --> check box 'Allow others to connect remotely to this computer
2- Click on 'Select Remote Users' and make sure you add your name or the account that it going to have access to the particular machine.
3- click start-->run--> and type cmd
4- enter ipconfig and jot down the machine's IP Address. Type exit

Now you are done with Window's settings.
5- Go to Ubuntu and open Applications --> Internet --> Terminal Server Client
6- Under Computer type in the IP Address from step 4
7- Enter the user used from step 2
8- Enter password for user in step 2 --- leave rest blank
9- Connect to machine

Now to connect from Windows to Ubuntu
1- install VNC 
2- Open up VNC viewer
3- On Ubuntu machine right click on the two little computer icons on the top bar next to the speaker icon or next to the Date -->Connection Information --jot down the machine's IP Address
4- Now go to Preferences --> Remote Desktop --> check next to:
   4 A- Allow others to view your desktop
   4 B- Allow others to cont.......
    C- Select a password for security
5- Now on Windows machine use VNC viewer. (I don't have it installed but it's pretty simple to follow) Enter the IP from step 3


Now my friend you should be able to connect back and forth

If your Ubuntu locks up, deactivate the eye candy (compiz fusion) and try it again

---

### Post by tuproxy on 2007-12-23
> **heatpumpcontrol said:**
> OK. One step at a time here...
1- Go to each Windows machine that you want to connect to and 
right click on 'My Computer' --> Properties --> Remote --> check box 'Allow others to connect remotely to this computer
2- Click on 'Select Remote Users' and make sure you add your name or the account that it going to have access to the particular machine.
3- click start-->run--> and type cmd
4- enter ipconfig and jot down the machine's IP Address. Type exit

Now you are done with Window's settings.
5- Go to Ubuntu and open Applications --> Internet --> Terminal Server Client
6- Under Computer type in the IP Address from step 4
7- Enter the user used from step 2
8- Enter password for user in step 2 --- leave rest blank
9- Connect to machine

Now to connect from Windows to Ubuntu
1- install VNC 
2- Open up VNC viewer
3- On Ubuntu machine right click on the two little computer icons on the top bar next to the speaker icon or next to the Date -->Connection Information --jot down the machine's IP Address
4- Now go to Preferences --> Remote Desktop --> check next to:
   4 A- Allow others to view your desktop
   4 B- Allow others to cont.......
    C- Select a password for security
5- Now on Windows machine use VNC viewer. (I don't have it installed but it's pretty simple to follow) Enter the IP from step 3


Now my friend you should be able to connect back and forth

If your Ubuntu locks up, deactivate the eye candy (compiz fusion) and try it again

Thank you for your step by step instructions!  I needed this to make sure that I wasn't making a major mistake.  I had done all of this before with no luck.  When I am in Vista, I am using UltraVNC Viewer and when I go to connect, it prompts for a password and accepts my input, and then hangs at "Please wait - initial screen loading..." and just hangs there.

What can I do?

---

