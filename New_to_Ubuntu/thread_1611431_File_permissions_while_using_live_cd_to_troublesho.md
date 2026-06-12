---
title: "File permissions while using live cd to troubleshoot"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by druid001 on 2010-11-01
I was trying to figure out how to get my video in 10.04 to be widescreen. I obviously messed something up because now it will only boot to the purple(ish) screen with the word Ubuntu and the row of dots below it. I tried hitting the escape key on bootup, but that does nothing. So...I tried using the live cd. I can boot into the desktop, I can see the mounted drive and the files on it, I even know where to find the xorg.conf file. BUT I have no permissions to edit or rename the file. What do I do in order to have these permissions? I want to rename the conf file to old and use the backup one to boot with. This is of course assuming that the reason it wont boot is because of a corrupt or mis-configured conf file! It wont boot far enough into the grub to give me the boot options list.

---

### Post by trikster_x on 2010-11-02
```
gksudo gedit /path/to/xorg.conf
```
This will open a ROOT gedit window that will allow you to change the conf file.  If you need to be able to move in and out of directories, then:
```
gksudo nautilus
```
This will open a root nautilus window.

---

