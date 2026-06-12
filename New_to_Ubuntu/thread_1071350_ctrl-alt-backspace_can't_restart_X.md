---
title: "ctrl-alt-backspace: can't restart X"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by Knacker on 2009-02-16
Hi, 
I'm sure this has been answered somewhere, but i can't find a thread through google or ubuntuforum search that applies (or at least not one that "works"). 

just upgraded to intrepid with clean install. i've been migrating stuff from my backup and removing/installing packages...

when i try to restart X-server with ctrl-alt-backspace, some sort of loop seems to start (mostly black-screen) which (usually) eventually pops up a warning telling me that x-server has got to start in low-graphics mode. 

i found an old thread that recommended appending a section to the end of my xorg.conf file, but that made no difference. 
lines that it recommended appending were:
Section	"ServerFlags"
Option	"DontZap"	"yes"
EndSection

sorry to bother everyone with a simple (no-doubt silly) mistake, but i don't know where else to look. 

thanks!

---

### Post by utnubuuser on 2009-02-16
Suppose you've already tried:> sudo dpkg --configure -a

---

### Post by chronographer on 2009-02-16
I suggest to first backup existing xorg ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BACKUP
``` and then remove the current one (which you backed up ```
rm /etc/X11/xorg.conf
```).

restart X or even better reboot the computer and hope for the best!

If this fails, try manually installing nvidia/ati drivers and doing the same (above) if things get *worse* then copy your old xorg back. (You can do this if you can't get to X by using virtual terminal ctrl-alt-F1 and gdm is usually still at ctrl-alt-F7.)

Good luck!

oh and the above post is good too, either that or: ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Knacker on 2009-02-18
hi, 
thanks for your suggestions guys. after messing around with this for a while, i've discovered that the problem lies in a known problem with nvidia driver (177.*) and my T61's NVS 140m graphics card. just thought i'd append this to the thread in case other people with the same problem came across this. 

FYI: 
[http://www.nvnews.net/vbulletin/showthread.php?t=125286](http://www.nvnews.net/vbulletin/showthread.php?t=125286)
[http://www.nvnews.net/vbulletin/showthread.php?t=120626](http://www.nvnews.net/vbulletin/showthread.php?t=120626)
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/258357](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/258357)
[https://bugzilla.novell.com/show_bug.cgi?id=461262](https://bugzilla.novell.com/show_bug.cgi?id=461262) 

anyway, thanks again!

---

### Post by Mister.Vash on 2009-02-18
As an alternative that may work for you since the ctrl-alt-backspace doesn't:

Go to the command line by pressing ctrl-alt-f1
at the prompt, login with your normal name and password

Type in the following:
```
sudo /etc/init.d/gdm restart
```

Give it a try next time you need to do it and see if it works for your

---

