---
title: "Unable to access anything"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by shivkumars on 2009-03-29
MY ubuntu installation gone kaput. please help me.

I tried to take snapshot of while using some compiz eye candy. Suddenly i got a message that "/home/******/Desktop folder is not present" and the system logged off from GUI. after logging in again I found that only wallpaper is coming and nothing else is present: no icons, no menu bar absolutely nothing. Even right click is not working. 
no key combination or hot key including Ctrl + Alt + Backspace is working. I can't use anything at all in ubuntu. Not even able to go to console mode. 

Please help me recover the system

---

### Post by Temposs on 2009-03-29
When you're booting up and you see the countdown, press Escape. Choose to boot in recovery mode(usually the second choice). Once it boots to the command prompt all the way, type:

```
cd /home
ls -la
```

Verify that you have a directory there that is the same as your username. It has to be **exactly** the same as your username. What I'm thinking is that you accidentally deleted or renamed your home directory, which can cause havoc to ensue on your system.

If you don't have a directory that is the same as your username, rename the existing directory you renamed, or if there's no directory there at all, create one:

```
mkdir yourusername
```

---

### Post by shivkumars on 2009-03-29
The home directory exists... I don't know what to do.  Please help

---

### Post by hovzio on 2009-03-29
When you are in recovery mode; is your home directory still intact, are all of your files still present?

---

### Post by Temposs on 2009-03-29
OK, you said you could get into the login screen. So, get to there and click the "Options" button in the bottom left, then click "Select Session". Then you want to choose Failsafe GNOME or Failsafe Terminal. That should get you logged into your user at least.

---

### Post by Temposs on 2009-03-29
As per this thread:
[http://guide.ubuntuforums.org/showthread.php?p=6792084](http://guide.ubuntuforums.org/showthread.php?p=6792084)

Type in a terminal once you're logged into one of those failsafe modes:
```
gconftool -s /desktop/gnome/applications/window_manager/default -t string "/usr/bin/metacity"
```

Then logout and select GNOME as your session(that's the normal Ubuntu mode). That should get you into your full desktop without compiz loading up. If compiz is the problem, it should load up just fine.

---

### Post by linuxisevolution on 2009-03-29
Sounds like hard drive failure...


See this post:

[http://ubuntuforums.org/showthread.php?p=6977444#post6977444](http://ubuntuforums.org/showthread.php?p=6977444#post6977444)

---

### Post by Temposs on 2009-03-29
> **linuxisevolution said:**
> Sounds like hard drive failure...


See this post:

[http://ubuntuforums.org/showthread.php?p=6977444#post6977444](http://ubuntuforums.org/showthread.php?p=6977444#post6977444)

Could be, but I'm not convinced the OP didn't just unknowingly bork a setting somewhere. I'm trying to see if compiz is the trouble, presently.

---

### Post by shivkumars on 2009-03-29
> **hovzio said:**
> When you are in recovery mode; is your home directory still intact, are all of your files still present?
Yes, I think all the files are present

> **Temposs said:**
> OK, you said you could get into the login screen. So, get to there and click the "Options" button in the bottom left, then click "Select Session". Then you want to choose Failsafe GNOME or Failsafe Terminal. That should get you logged into your user at least.
I have enabled autologin so actually I don't have to enter the username and password at login screen.
This idea of Failsafe mode struck my mind but couldn't do anything becos i am CLI challenged.  Any way to disable autologin 
 > **Temposs said:**
> As per this thread:
[http://guide.ubuntuforums.org/showthread.php?p=6792084](http://guide.ubuntuforums.org/showthread.php?p=6792084)

Type in a terminal once you're logged into one of those failsafe modes:
```
gconftool -s /desktop/gnome/applications/window_manager/default -t string "/usr/bin/metacity"
```

Then logout and select GNOME as your session(that's the normal Ubuntu mode). That should get you into your full desktop without compiz loading up. If compiz is the problem, it should load up just fine.

I also feel that something may be broken in compiz. Any method is there to correct the issue using Recovery Mode.

UPDATE: I was somehow able to run quoted command and when I logged into GDM (Ctrl + Alt + F7) I was able to see the menu all the shortcut icons and toolbar but they were non responsive. Cold Restarted the machine and condition return to that of original.

---

### Post by shivkumars on 2009-03-29
Please help me guys

---

### Post by Temposs on 2009-03-29
In recovery mode, try:

```
apt-get remove ubuntu-desktop
```

restart and that may disable autologin

```
apt-get remove compiz
```

that should uninstall compiz, and if compiz is causing the issue, it shouldn't exist anymore.

---

