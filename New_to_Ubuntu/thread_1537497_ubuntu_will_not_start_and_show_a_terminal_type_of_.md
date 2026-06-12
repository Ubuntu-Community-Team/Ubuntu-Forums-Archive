---
title: "ubuntu will not start and show a terminal type of window"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by cheekymonky2010 on 2010-07-23
PLEASE help!  I tried install the dvd creator and remove Brassero, also removing the Brassero-common file from the synaptic package manager!
After restarting my PC, hearing the drums and entering my password, the computer screen froze and a terminal style box appered in the top left corner asking for the main-user login and then the password!  after trying what I thought it might be and just getting failiure messages, I am absolutely stuck and can not get to my desk top screen or anything!
I tried going through the recovery mode and fixing broken packages but I really have no idea what I am doing!  PLEASE help!

---

### Post by matrixblue on 2010-07-23
If you are connected to the internet via ethernet log in to the terminal and type

**sudo apt-get install ubuntu-desktop**

If that doesn't work then try

**sudo dpkg-reconfigure -a**

---

### Post by linux18 on 2010-07-23
these steps will boot any non-bricked ubuntu:

-choose recovery mode at grub
-drop to a root prompt
-type telinit 3 and login
-then type xinit 
-when xinit starts type: metacity &  - for ubuntu OR compiz &  - if you have it OR flux/openbox &  - if you have it OR fvwm & - for xubuntu
-then type gnome panel & -for ubuntu OR xfce4-panel & -for xubuntu
-lastly type nm-applet & -for networking

once in the familiar interface open a terminal and type: ```
 sudo apt-get check 
```    to check for broken dependencies, if there are any follow this guide:
[http://ubuntuforums.org/showthread.php?t=186672](http://ubuntuforums.org/showthread.php?t=186672)

good luck

---

### Post by cheekymonky2010 on 2010-07-23
Thanks Linux 18 this has worked and I am now back in Linux :D  no idea how though because I ended up in all sorts of reconfiguration screens and just pressed enter on anything!  surprised the text is,nt in urdu! but surely somthting will be different because I had absolutely no idea what i was agreeing to!   just hope it has,nt affected my security    Thank you

---

### Post by linux18 on 2010-07-23
> **cheekymonky2010 said:**
> Thanks Linux 18 this has worked and I am now back in Linux :D  no idea how though because I ended up in all sorts of reconfiguration screens and just pressed enter on anything!  surprised the text is,nt in urdu! but surely somthting will be different because I had absolutely no idea what i was agreeing to!   just hope it has,nt affected my security    Thank you
essentially, the commands I posted are the one's that linux uses to start the desktop environment in the first place minus things like pulseaudio ( which will start if you try to play any sound ) your security is not comprised.just sudo apt-get install ubuntu-desktop and reboot to see if everything works and mark the thread as solved.

---

