---
title: "my desktop folder are gone"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by MPX11 on 2009-01-31
after running several programs my desktop froze, I rebooted and my desktop was black, everything else seemed to be working fine, I went to pref>appearnc>visual effects and toggle between the different settings and my background came back but my desktop folders are gone, when I try to open them from >places>desktop  I get this error:
 Could not open location 'file:///home/bet/Desktop'..
 No application is registered as handling this file.
and when I try to open one of the video files I get this error:
  Could not open folder "Webcam"
  The nautilus file manager is not running.
is there a fix to this or do I have to reinstall? please help

---

### Post by gettinoriginal on 2009-02-01
First, try this:
Reboot > during grub splash, hit escape > Recovery mode > Enter (let finish)
Repair Broken Packages > Enter (if it asks about updates hit N) (let finish)
Try to fix X server > Enter (Let finish)
Resume normal Boot > Enter

---

### Post by MPX11 on 2009-02-01
> **gettinoriginal said:**
> First, try this:
Reboot > during grub splash, hit escape > Recovery mode > Enter (let finish)
Repair Broken Packages > Enter (if it asks about updates hit N) (let finish)
Try to fix X server > Enter (Let finish)
Resume normal Boot > Enter

thanks a lot GETTINORIGINAL this has fixed the problem, all my folders are back.

---

