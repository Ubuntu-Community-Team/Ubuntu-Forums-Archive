---
title: "Problem in installing windows software from removable drive"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by ravi_buz on 2009-08-13
I am using ubuntu 9.04 and wine 1.1.24 .I am unable to install any windows software from removable drives like cd drive or pendrive.But i am able to install those software if i transfer them to my system . When i tried through terminal i got this error [PHP]ravi@ravi-desktop:~$ cd /media/disk/aom1
ravi@ravi-desktop:/media/disk/aom1$ wine SETUP.exe
Warning: could not find DOS drive for current working directory '/media/disk/aom1', starting in the Windows directory.
wine: could not load L"C:\\windows\\system32\\SETUP.exe": Module not found
ravi@ravi-desktop:/media/disk/aom1$ fixme:menubuilder:SaveIconResAsXPM Unsupported color depth 32-bit
fixme:menubuilder:SaveIconResAsXPM Unsupported color depth 32-bit
fixme:menubuilder:SaveIconResAsXPM Unsupported color depth 32-bit
fixme:menubuilder:SaveIconResAsXPM Unsupported color depth 32-bit
fixme:menubuilder:SaveIconResAsXPM Unsupported color depth 32-bit
fixme:menubuilder:SaveIconResAsXPM Unsupported color depth 32-bit
fixme:menubuilder:SaveIconResAsXPM Unsupported color depth 32-bit
[/PHP]

---

### Post by fennec_fox on 2009-08-13
As I recall wine doesn't work with windows kernel level drivers so it has problems with some usb devices and such. If it really was ever an issue you could try this but, I'm not sure it would necessarily work for everything.

[http://wiki.winehq.org/USB](http://wiki.winehq.org/USB)

---

### Post by ravi_buz on 2009-08-13
So is there any way to install games like age of mythology which requir two cd to install it.I cant install it by mountiing or from my HDD

---

### Post by 3rdalbum on 2009-08-13
Create symbolic links from /media/cdrom to ~/.wine/dosdevices/D:, which solves the error message.

---

### Post by Hospadar on 2009-08-13
if you arn't sure how to do the above:
let's say your cd mounts to /media/cdrom
```
ln -s /media/cdrom ~/.wine/dosdevices/D:
```
the syntax is ln -s(for symbolic link as opposed to hard link) <link target> <link name>

---

