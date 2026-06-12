---
title: "Fail to install"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by Martin.G on 2010-07-25
I am new to linux and I really want to use ubuntu
I recently installed a PPC version on my ibook G4 and it works well.

But I have problem installing it on my pc and I think it is a display problem. I have a ATI HD3200 onboard display.

I tried both booting from CD and using wubi.exe, but it will still restart after the loading screen. The wallpaper comes up, load for awhile then reboot, I tried to tick all the boxes of noacpi nomodeset, etc.

I think it is a display problem coz if I use wubi and load it in recovery mode, it will come up with a message that starts with (EE) and says something about modeset refuse to load of something.


please help ....... I can only use the console login and command line coz I can't even go to the desktop... and is a nightmare for  a beginner

---

### Post by collinp on 2010-07-25
While you're at a terminal, execute the following commands in order:

```
sudo apt-get update
sudo apt-get install fglrx fglrx-amdcccle xorg-driver-fglrx
sudo modprobe fglrx
sudo aticonfig -initial
sudo /etc/init.d/gdm restart
```If it's a graphics issue, that should get everything working fine. Note that, if you're not running off a permanent installation, the changes made by those commands will be lost after reboot.

---

### Post by Martin.G on 2010-07-25
thank you very much for help
although I am not very sure what is a permanent install, I have to say I can only reach the command line interface by installing through wubi... otherwise it will only keep rebooting

I will try it now and tell you how it goes .... be back soon !!

---

### Post by collinp on 2010-07-25
> **Martin.G said:**
> thank you very much for help
although I am not very sure what is a permanent install, I have to say I can only reach the command line interface by installing through wubi... otherwise it will only keep rebooting

I will try it now and tell you how it goes .... be back soon !!

A permanent installation is one that's been installed to the hard drive.

Note that I added another command to the end of that list.

---

### Post by Martin.G on 2010-07-25
thank you....
I am making some progress, I saw the login screen in a split second and then it restarts
however, the command "sudo fglrxconfig -initial" does not work
it says "sudo: fglrxconfig: command not found"

---

### Post by collinp on 2010-07-25
Ah, my mistake. "fglrxconfig" should be "aticonfig". I'll update the instructions with that.

---

### Post by Martin.G on 2010-07-25
it seems better now
but it still says "warning: could not find configuration file Please copy configuration file template to /etc/X11"

any idea ? 10000000 thanks

---

### Post by Martin.G on 2010-07-25
I have done it !!!! Thanks so much !!! 
Just make a note here for other users who have a similar problem
the command is "sudo aticonfig --initial --input=/etc/X11/xorg.conf"


Thanks for you help !!!! hope everything will be fine from now

---

### Post by Martin.G on 2010-07-25
and how to make this topic as solved ?

---

