---
title: "Cannot reinstall after removing Ubuntu with WUBI"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by garywayneyoung on 2011-02-07
Hello,

I am new to Ubuntu.  I used WUBI with the defaults and was able to successfully install Ubuntu.  I decided I wanted to create a larger Ubuntu install so I uninstalled Ubuntu (Windows 7 uninstall program). Everything worked fine and Ubuntu was no longer a boot option.

When I tried to run WUBI again, I got a message box saying "There is no disk in the drive. Please insert a disk into drive \Device\Harddisk\DR1.  I could go further than this and had to reboot my computer to get rid of the message box.

Any ideas?

Many thanks in advance.

---

### Post by philinux on 2011-02-07
> **garywayneyoung said:**
> Hello,

I am new to Ubuntu.  I used WUBI with the defaults and was able to successfully install Ubuntu.  I decided I wanted to create a larger Ubuntu install so I uninstalled Ubuntu (Windows 7 uninstall program). Everything worked fine and Ubuntu was no longer a boot option.

When I tried to run WUBI again, I got a message box saying "There is no disk in the drive. Please insert a disk into drive \Device\Harddisk\DR1.  I could go further than this and had to reboot my computer to get rid of the message box.

Any ideas?

Many thanks in advance.

WUBI was never meant to be a permanent install. Just another method of trialling ubuntu. Now you've tried it I would recommend a dual boot or liveusb stick with persistence.

In order to **not mess** with your hard drive, for a liveusb see this. [http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

---

### Post by Rubi1200 on 2011-02-07
> **garywayneyoung said:**
> Hello,

I am new to Ubuntu.  I used WUBI with the defaults and was able to successfully install Ubuntu.  I decided I wanted to create a larger Ubuntu install so I uninstalled Ubuntu (Windows 7 uninstall program). Everything worked fine and Ubuntu was no longer a boot option.

When I tried to run WUBI again, I got a message box saying "There is no disk in the drive. Please insert a disk into drive \Device\Harddisk\DR1.  I could go further than this and had to reboot my computer to get rid of the message box.

Any ideas?

Many thanks in advance.
Hi and welcome to the forums :-)

It sounds as if Wubi was not completely removed.

Look here for more information:
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20uninstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20uninstall%20Wubi?)

Read also the section on manual removal and removal of the registry keys.

---

### Post by bcbc on 2011-02-07
> **garywayneyoung said:**
> Hello,

I am new to Ubuntu.  I used WUBI with the defaults and was able to successfully install Ubuntu.  I decided I wanted to create a larger Ubuntu install so I uninstalled Ubuntu (Windows 7 uninstall program). Everything worked fine and Ubuntu was no longer a boot option.

When I tried to run WUBI again, I got a message box saying "There is no disk in the drive. Please insert a disk into drive \Device\Harddisk\DR1.  I could go further than this and had to reboot my computer to get rid of the message box.

Any ideas?

Many thanks in advance.

this message is due to the presence of an assigned drive letter on an empty drive - e.g. a card reader. remove the card reader and it goes away. You don't need to reboot your computer to get rid of it - ctrl-alt-dlte, run task manager, and kill pyrun.exe. You can also click through it (if you are a patient person) as it seems like it's a loop but it's not. (Wubi just likes to check drives a lot).

---

