---
title: "Turn terminal commands into a program"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by kibitzor on 2008-12-26
I've managed to install ndiswrapper on my mother's laptop, but I still need to enter the following code for the linksys card to turn on: ```
laura@john-laptop:~$ su
Password: 
root@john-laptop:/home/laura# ifconfig wlan0 up
root@john-laptop:/home/laura# 


```
This bit of code is too much for my mother, and I'd like to know if there's a way to turn that code into a program and then bind that program to firefox ( when firefox is clicked, the program will turn the card on, then open firefox). I'm up for any suggestions, thanks!

---

### Post by moredhel on 2008-12-26
What you could do is make a bash script that does it, then make that bash script autostart. (Need any help with that?)

---

### Post by albinootje on 2008-12-26
> **kibitzor said:**
> I've managed to install ndiswrapper on my mother's laptop, but I still need to enter the following code for the linksys card to turn on: ```
laura@john-laptop:~$ su
Password: 
root@john-laptop:/home/laura# ifconfig wlan0 up
root@john-laptop:/home/laura# 


```
This bit of code is too much for my mother, and I'd like to know if there's a way to turn that code into a program and then bind that program to firefox ( when firefox is clicked, the program will turn the card on, then open firefox). I'm up for any suggestions, thanks!

You can put it in /etc/rc.local before the "exit 0" line.
Make sure you test whether that works with a reboot.

---

### Post by kibitzor on 2009-01-12
> **moredhel said:**
> What you could do is make a bash script that does it, then make that bash script autostart. (Need any help with that?)

I know how to make a new file, then type```
#! /bin/bash
``` but I do not know what code to put in after that to have it automatically turn on the linksys card.

*Edit*
The card automatically turns on now without having changed anything, must have been an Ubuntu update. Thanks for the help everyone!

---

### Post by ugm6hr on 2009-01-12
Binding it to Firefox will be a bit tricky, since ifup requires sudo privileges.  Therefore, at Desktop level, you'd have to enter your password each time to get connected, which would be a bit annoying.

Is there any reason you couldn't do it at startup?

If it must be done within the GUI, consider using Wicd as your Network Manager, since it has the facility to include a pre-connection (and disconnection) script.  I have never really experimented with the script facility in Wicd before, but I have no reason to suspect it wouldn't work.

---

### Post by bodhi.zazen on 2009-01-12
> **kibitzor said:**
> I know how to make a new file, then type```
#! /bin/bash
``` but I do not know what code to put in after that to have it automatically turn on the linksys card.

When you make a bash script uses the same commands as you would type them in a terminal ...

[http://linuxcommand.org/](http://linuxcommand.org/)

General comments ...

1. First Ubuntu uses sudo , so there is no need to set a root password.

2. You will need to run the script as root. Since it is not really a script, it is a single command, the suggestion of placing it in /etc/rc.local is a good one. rc.local is run (as root) as the final step in the boot process.

3. If you make a script you will need to run it with sudo. You can configure your script to run with no password if you wish.

---

