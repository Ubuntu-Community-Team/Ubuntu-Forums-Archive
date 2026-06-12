---
title: "Help needed,.... used xkill on the desktop screen.."
date: 2010-04-10
forum: New to Ubuntu
---

### Post by vivek40 on 2010-04-10
Hii! Looks like i have done a big goof up this time.I used the xkill operation and clicked on the panel,and then everything disappeared.The screen got blacked out and then after a long time when it did not come  back I thought maybe a reboot would help,so I rebooted, which took me again to the login screen and there I could not enter my password to login again,even the mouse was not moving.So i tried entering the recovery mode by pressing escape while the system was booting up,and there i was prompted for my username and pwd ,which i gave in but then i understand that it would only be the console commands that would help me there and nothing else.. and i dont know any..so can someone please help.. ...
(i have only Kubuntu running on my system and nothing else)
regards
Vivek

---

### Post by MooPi on 2010-04-10
Try another reboot to see if things are corrected already. I can't imagine xkill destroying config files for your desktop.

---

### Post by vivek40 on 2010-04-10
Have already rebooted 4 times Moobi!

---

### Post by vivek40 on 2010-04-10
Hii ! These are tough times.. and any sort of help which could be provided in an expedited manner would be deeply and truly appreciated...

---

### Post by MooPi on 2010-04-10
Your first reboot from the unresponsive desktop may have borked the mess.
A possible solution is an un-install of the desktop environment and then a subsequent reinstall.
From the recovery mode:
```
apt-get purge kubuntu-desktop
```That should remove config files as well.
```
apt-get install kubuntu-desktop
```I would suggest that you do further research on this subject before undertaking my suggestion. Other possible solutions may involve using the Live CD to alter your desktop config files.
Try this first if you haven't already done something. This is from recovery mode as well
> sudo dpkg-reconfigure xserver-xorg

---

### Post by vivek40 on 2010-04-10
just used the command "startx" and it worked.. thanks Moopi by the way!

---

### Post by HermanAB on 2010-04-10
I would first try to make a new user account and see if that fixes it (for the new user). It probably will.  Then delete the hidden desktop configuration files in your home directory (.local and .config).  If you log in again, KDE will recreate them.

---

### Post by MooPi on 2010-04-10
That was way to simple. It seems I was making a mole hill a mountain. Glad it worked out:)

---

