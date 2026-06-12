---
title: "Please help!  I installed ubuntu and now I can't get into windows"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by ctothebizza on 2009-02-16
So I installed ubuntu, and now my computer boots directly into ubuntu.  I know that Windows is still there, as I can access the files from inside ubuntu.  But windows is not an option in grub.

---

### Post by Crafty Kisses on 2009-02-16
Hey there! Let's see if we can't add Windows back. I'm just guessing your using Windows XP. So try the following, open up the GRUB configuration file, by running the following:
```

sudo gedit /boot/grub/menu.lst
```
Once you're in the file, open up a Terminal and run the following command:
```
sudo fdisk -lu
```
From there you can see what partition XP is installed on, so then after you know what partition XP is installed on, you can add the following to the GRUB configuration file:
```

title Windows XP
root (hd?,?) {Where ?,? the drive and partition XP is installed to)
makeactive
chainloader +1
```

---

