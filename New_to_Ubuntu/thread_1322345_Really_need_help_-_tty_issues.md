---
title: "Really need help - tty issues"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by colin30 on 2009-11-10
Hello everyone, 
 
A coworker of mine said to try this site.  I'm really new to Ubuntu and am having a rough start.  I have the new 9.10 version of Ubuntu, but I'm stuck in a permanent terminal setting.  I was told it was someting to do with pressing ctrl+alt+F3, but I don't remember doing that.  I have tried crtl+alt+F7 to get out of it an that has no effect at all.  I have also tried sudo /etc/init.d/gdm restart and I got this message:
 
Since the script you are attempting to to invoke has been coverted to an upstart job, you may also use the restart(eight) utility e.g.restart gdm
gdm start/running, process 2680
 
I don't know what that even means.  I received a message saying gdm might not even be running.  Is there a terminal code I can enter to get back to the 'regular' desktop? 
 
If I have to totally start over, how would I go about doing that from where I am - I have a 9.10 version saved on a flash-drive.
 
Thanks

---

### Post by doas777 on 2009-11-10
try:
```
sudo service gdm start
```if it is already running replace start with stop, adn then start it.

and if that fails try:
startx

now, just to clarify, does x load after a reboot?

ctrl + alt + f7 should take you back to your desktop, but when you invoke x from a tty, it usually runs within that tty. not sure about the "service start" variant. it's new.

---

### Post by doas777 on 2009-11-10
also, is this teh first time trying to get it up on that hardware? if so, perhaps a reinstallation is in order.

---

### Post by super kim on 2009-11-10
> **doas777 said:**
> also, is this teh first time trying to get it up on that hardware? if so, perhaps a reinstallation is in order.


i'm not knowledgeable enough to help you here but... did ubuntu work ok off the cd? i always check it all works before i start the install. If it runs fine from the cd then i would just reinstall, it takes what? 20 minutes at the most? if you have a blank hard drive then you really have nothing to loose and everything to gain from a reinstall.

---

### Post by colin30 on 2009-11-10
Thanks for replying.
 
No, it does not connect to X server.  It says unable to connect to X server.  No such process.  Server error.
 
How do I totally reinstall Ubuntu from a flash-drive with my computer in this state?

---

### Post by doas777 on 2009-11-10
> **colin30 said:**
> Thanks for replying.
 
No, it does not connect to X server.  It says unable to connect to X server.  No such process.  Server error.
 
How do I totally reinstall Ubuntu from a flash-drive with my computer in this state?

well, pretty much the same way you installed it last time, right? boot off the usb, and perform the install. or am I missing somthing?

if you have an burner you can download a new copy of the disk and burn it off, boot from it and install.

---

### Post by colin30 on 2009-11-10
OK, so here's a stupid question: How do I boot off the disc?

---

### Post by doas777 on 2009-11-10
> **colin30 said:**
> OK, so here's a stupid question: How do I boot off the disc?

put it in, and reboot your PC. 
if it does not boot of the disk, then reboot again, and enter your BIOS. look for the boot order, and move your cd/dvd drive to the top of the list. then save and exit.

---

### Post by Buuntu on 2009-11-10
You'll have to change your boot priority when your computer just starts up.  
It will usually tell you something along the lines of "Press <Key> to Enter Setup" when you first boot up.  Press that key and navigate over to boot priority.  From there you need to make sure CD/DVD is listed above your hard disk.  Make sure to save and exit after you're done.
Then just insert the disk and it should boot from it.

***Sorry - I was replying at the same time as the person above did***

---

### Post by colin30 on 2009-11-10
Thank you one, thank you all, I am reinstalling right now.  I appreciate all of the help and if I have anyother questions I am going to use this forum for sure.  If I haven't been too much of a pain in the ***.
 
Thanks again.
 
Colin.

---

### Post by dillandriskell on 2009-11-10
In addition to what Buuntu said, I believe it's either F12 or F2 that you press as the computers booting up to get into the "boot priority" menu.  

Also, what model/make of computer are you using?  I had some initially issues with Ubuntu 9.10 at first as well because of hardware incompatibility.  If it doesn't work after this reinistillation I would recommend downgrading to Ubuntu 9.04 (it's still quite a good operating system) and wait like a month for a patch to be made for your computer.

You can find the 9.04 release here: [http://releases.ubuntu.com/jaunty/](http://releases.ubuntu.com/jaunty/)

EDIT: If you go with 9.04 I would recommend just getting rid of the files of 9.10 on your flash drive, and replacing them with 9.04.  You can always upgrade straight to 9.10 from 9.04 whenever you'd want to try it again.

---

