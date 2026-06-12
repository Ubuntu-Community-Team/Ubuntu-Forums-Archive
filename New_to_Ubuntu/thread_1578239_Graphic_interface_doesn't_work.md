---
title: "Graphic interface doesn't work"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by eithantlv on 2010-09-20
I've installed Ubuntu 10.04, all were working properly.
After the latest updates were installed and computer was restarted, the system does not boot in graphic interface. 
What could be a problem?

---

### Post by jtarin on 2010-09-20
From the Grub boot menu choose "kernel (recovery mode)"see if you can boot with the lowest kernel number.

---

### Post by eithantlv on 2010-09-20
Yes, I boot in recovery mode, but still I only can boot in text mode

---

### Post by jtarin on 2010-09-20
> **eithantlv said:**
> Yes, I boot in recovery mode, but still I only can boot in text mode
What do you see on the screen when you are in "text mode"?

---

### Post by eithantlv on 2010-09-20
normal terminal
all Unix commands are working, I can operate with files and system

---

### Post by jtarin on 2010-09-20
Then try the command ```
startx
``` this should get you a login screen. Anything different post the output here.

---

### Post by eithantlv on 2010-09-20
I'm getting this messag

No such file or direcroty(errorno 2): Unable to connect server
No such process(errorno 3): Server error

---

### Post by jtarin on 2010-09-20
tyr the command ```
su startx
```

---

### Post by jtarin on 2010-09-20
What version of Ubuntu are you using?

---

### Post by eithantlv on 2010-09-20
10.04

---

### Post by jtarin on 2010-09-20
If you have an internet connection and are using Gnome desktop.....from the command line try ```
sudo dpkg-reconfigure gdm
```

---

### Post by eithantlv on 2010-09-20
I see no visual effect when I enter this, but my computer dalays for few seconds.
However when I enter
```
startx
```
after that, still I'm getting the same results

---

### Post by jtarin on 2010-09-20
Did you reboot and try?

---

### Post by jtarin on 2010-09-20
Ok as a last resort....```
sudo apt-get install ubuntu-desktop
```

EDIT:to change command

---

### Post by jtarin on 2010-09-20
See above post

---

