---
title: "reinstall grub menu"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by patchido on 2011-08-17
i installed windows 7 in my laptop, and now i cant get ubuntu to load.
 im in the liveUSB

this is my fdisk```
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3922    31503433+   7  HPFS/NTFS
/dev/sda2            3923        7958    32419139+   5  Extended
/dev/sda3            7959       12037    32764567+  83  Linux
/dev/sda4           12038       60801   391696830    7  HPFS/NTFS
/dev/sda5            3923        7691    30274461   83  Linux
/dev/sda6            7692        7958     2144646   82  Linux swap / Solaris

```


sda1 is windows 7
sda3 ubuntu
sda4 my DATA
sda5 openSUSE
sda6 swap

---

### Post by dave01945 on 2011-08-17
try this see if it helps

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by patchido on 2011-08-17
i have unetboot, so i dont get that grub screen :s

---

### Post by dave01945 on 2011-08-17
it should just be a case of loading the live cd/usb opening a terminal and enter

```
grub-install /dev/sda
```


hope it helps

if that doesn't work here is another guide

[http://www.lancelhoff.com/restore-grub2-after-installing-windows/](http://www.lancelhoff.com/restore-grub2-after-installing-windows/)

---

### Post by Rex Bouwense on 2011-08-17
Try this site:
[http://ubuntulinuxhowtos.blogspot.com/2010/01/how-to-reinstall-grub-2-after.html](http://ubuntulinuxhowtos.blogspot.com/2010/01/how-to-reinstall-grub-2-after.html)

---

