---
title: "NVIDIA X Server Settings help needed"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by toyoracer on 2010-03-28
I know this has been asked a thousand times. I have read and tried many solutions to no avail. My tv settings keep getting errors and if able to get connected both screens turn white. When I first tried I got movie on tv but rez was wrong and only half of screen was used. I think I changed something because now nothing seems to work.

I am using Jaunty,Geforce4 mx420, s-video cable, crt tv.

Would like to play movies and Youtube on tv. Right now I am forced to switch to XP to watch which is not acceptable. So I am asking for help thank you

---

### Post by toyoracer on 2010-03-28
When setting tv to separate x screen and save to x configuration file get failed to parse existing x config file '/etc/X11/xorg.conf' press ok only option and window closes.
When setting tv to separate x screen and Apply get cannot apply items have changed need to save to (file above) apply what is possible -- nothing happens
Also get "require x restart" how do I restart -- reboot seems wrong

---

### Post by NightwishFan on 2010-03-28
Perhaps run nvidia-xconfig as root? Also, you can kill xserver by pressing alt+prntsrcn+k

---

### Post by toyoracer on 2010-03-28
Okay that seem to work that I got twinview. What about separate screens which is what I would like.

---

### Post by toyoracer on 2010-03-28
Result of running as root
craig@craig-desktop:~$ sudo /nvidia-xconfig
[sudo] password for craig: 
sudo: /nvidia-xconfig: command not found
craig@craig-desktop:~$

---

### Post by NightwishFan on 2010-03-28
```
sudo nvidia-xconfig
```

---

### Post by toyoracer on 2010-03-28
craig@craig-desktop:~$ sudo /nvidia-xconfig
[sudo] password for craig: 
sudo: /nvidia-xconfig: command not found
craig@craig-desktop:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Undefined Device "(null)" referenced by Screen "Default
                  Screen".

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

craig@craig-desktop:~$

---

### Post by NightwishFan on 2010-03-28
Not sure, I never messed with screens myself, but see if that works for you.

---

### Post by toyoracer on 2010-03-28
When try to sve to configuration file get error unable to remove x config backup file '/etc/X11/xorg.conf.backup' in separate x screen.

In twinview both are solid white and if I accept screen change I will lose x server setting window and have nothing

---

### Post by lidex on 2010-03-29
[Twinview]("http://www.google.com/search?q=nvidia+twinview&sitesearch=ubuntuforums.org")

[Xinerama]("http://www.google.com/search?hl=en&newwindow=1&safe=off&sitesearch=ubuntuforums.org&q=ubuntu+xinerama+nvidia&aq=3m&aqi=g2g-m2&aql=&oq=xinerama+n&gs_rfai=")

---

