---
title: "I installed Ubuntu, but I have a problem with Windows"
date: 2011-07-29
forum: New to Ubuntu
---

### Post by bobalooba on 2011-07-29
I installed Ubuntu from Windows XP, but when i startup i have to choose between XP and Ubuntu. How do i get rid of XP? Also, when I use ubuntu, i never stopped using the Try it With Windows. The instructions said an icon would show up for installing it fully, but i can't find it. Please help. I  installed 11.04. Also, when I startup ubuntu, it says Synaptic Package Manager found a new package, but when i use it to open the Package, it gives me an error

---

### Post by lmarmisa on 2011-07-29
Did you install Ubuntu using Wubi?.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Wim Sturkenboom on 2011-07-30
I guess he/she did. Not familiar with Wubi.

Make a bootable CD with Ubuntu on it. Boot from it and install. Allow it to use the whole disk and your windows will be gone. Better option might be to do a manual partitioning and make three partitions; one for /, one for swap and one for /home. The latter allows you to do a re-install if necessary without loosing your documents.

Before you do so, I would run it in live mode first (try ubuntu without installing). Verify that your internet connectivity is working.

PS
Never say that something gives an error. Always state the error message as accurate as possible so we know what the program is complaining about.

---

### Post by beew on 2011-07-30
> **bobalooba said:**
> I installed Ubuntu from Windows XP, but when i startup i have to choose between XP and Ubuntu. How do i get rid of XP? Also, when I use ubuntu, i never stopped using the Try it With Windows. The instructions said an icon would show up for installing it fully, but i can't find it. Please help. I  installed 11.04. Also, when I startup ubuntu, it says Synaptic Package Manager found a new package, but when i use it to open the Package, it gives me an error
 
You can't get rid of XP if you installed "Ubuntu" with WUBI. WUBI is a Windows program and it is not a real Ubuntu install. If you want to install Ubuntu fully and get rid of XP, get the Ubuntu ISO (not WUBI!) , make a live CD or live usb and install it on your whole hard drive, that will automatically wipe out XP. Make sure you back up your important files first.

---

### Post by bobalooba on 2011-07-30
I did use wubi and followed the instructions. I want to fully install it, and to do that The instructions said that an icon would appear on the desktop of ubuntu. There is no icon.

---

### Post by robgraves on 2011-07-30
> **bobalooba said:**
> I did use wubi and followed the instructions. I want to fully install it, and to do that The instructions said that an icon would appear on the desktop of ubuntu. There is no icon.

you would not be able to do a full proper ubuntu install from within windows, i would advise that you go into the start menu (in windows) go to control panel, add/remove programs, you should see the ubuntu (wubi) listed as an application like all your other windows programs, remove it/totally uninstall it, then reboot the computer with the ubuntu CD/USB in to do an install or just try ubuntu, but before installing you will have to do disk partitioning to make room for the ubuntu install.

---

### Post by Mark Phelps on 2011-07-30
> **bobalooba said:**
> I did use wubi and followed the instructions. I want to fully install it, and to do that The instructions said that an icon would appear on the desktop of ubuntu. There is no icon.

There is no icon -- because it is already installed!

As others have told you, if you want to have a separate install, you need to remove the Wubi install.

---

### Post by dFlyer on 2011-07-30
If you don't want to dual boot, just burn a desktop cd and when you install, use whole drive. My advice before doing so would be to make a complete backup of you windows system, (a clone), otherwise it may take you several day for a windows reinstall should you ever change your mind and want to dump linux. I can't think of any reason why someone would dump linux it's best to be safe than sorry later on.

---

### Post by bobalooba on 2011-07-31
> **dFlyer said:**
>  My advice before doing so would be to make a complete backup of you windows system, (a clone), otherwise it may take you several day for a windows reinstall should you ever change your mind and want to dump linux. I can't think of any reason why someone would dump linux it's best to be safe than sorry later on. 

How would I make a clone of windows xp? And thank you for your help

---

### Post by Mark Phelps on 2011-08-01
> **bobalooba said:**
> How would I make a clone of windows xp? And thank you for your help

Most folks around here will probably tell you to use Clonezilla -- but my experience has been that Windows Utilities work best with Windows installs.

So, I would do the following:
1) Download and install the FREE version of Macrium Reflect (MS Windows product)
2) Use the option to create and burn the Linux Restore CD
3) Use MR to image off the XP install -- this is the cloning operation.

---

