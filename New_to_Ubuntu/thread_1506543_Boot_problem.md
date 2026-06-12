---
title: "Boot problem?"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by crossnt0 on 2010-06-10
I'm very new to Ubuntu, and I'm attempting to boot it from my system. I've tried many CD's, thinking I made them wrong. However I tried them on a friend's computer and the CD will work just fine. The problem is when I boot the machine it'll boot, the purple welcome screen will pop up, and then the computer goes black, and from there I can hear the machine still working, but the screen is blank. I have a Toshiba with an i5 processor and (here's where I think the problem is) an NVidia graphics card (512 MB) I don't think Ubuntu supports NVidia graphics does it? Thanks in advance for any help!

---

### Post by limestone on 2010-06-10
try this...
[http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)

---

### Post by crossnt0 on 2010-06-10
Umm on the explanation, I ran it in nomodeset and got it installed like solution 2 said. However when I try to start it back up without the boot CD it won't work. I choose my OS and then the screen goes blank again. Any suggestions?

---

### Post by bcbc on 2010-06-10
Hold down shift at startup (if you don't already see the grub menu). Press 'e' on the first menu item and add the nomodeset option again after 'quiet splash'. Then CTRL-X to boot.

After booting go into /etc/default/grub ```
gksudo gedit /etc/default/grub
``` and change the line 
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

then run ```
sudo update-grub
``` to refresh the grub menu. From then on, it will be in grub. If you need to remove nomodeset, perhaps after getting a proper nvidia driver, then just do the reverse.

---

### Post by crossnt0 on 2010-06-10
I know what you're saying and how to do it (I did it with the boot CD in), but I can't get past the first startup. I'm supposed to start it without the disk and hold shift down right? That didn't bring up the menu that was supposed to come up.

---

### Post by crossnt0 on 2010-06-10
Nevermind!!! Got it! Thanks you very much!! :)

---

### Post by crossnt0 on 2010-06-10
Well, one last thing. I'm getting a permission error for some reason. I'm an administrator on the account though?

---

### Post by bcbc on 2010-06-10
You're welcome. Follow that link pont provided. That seems like the correct long term solution. Sorry should have checked that out first #-o

Don't forget to remove 'nomodeset' from /etc/default/grub and rerun sudo update-grub if you do find the correct driver.

---

### Post by bcbc on 2010-06-10
> **crossnt0 said:**
> Well, one last thing. I'm getting a permission error for some reason. I'm an administrator on the account though?

You have the 'ability to elevate your privileges to root', through use of sudo or gksudo.

---

### Post by crossnt0 on 2010-06-10
Thanks to everyone who helped me! It's solved!

---

