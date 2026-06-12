---
title: "Help with grub"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by tacodestroyer on 2009-07-20
Hi everyone.  I'm new here and to ubuntu.  Put it on my laptop and it rocks so I got a cheap desktop and running it on my LCD TV.  Have XP on it and I wanted to dual boot on it.  One hangup, the grub window never loaded so it only boots to ubuntu.  
I tried to reinstall ubuntu but ended up making two ubuntu partions.  I just need to load windows and then I can delete the Ubuntu partion and reinstall it clean.  Any thoughts on how to boot to windows from Ubuntu or add the grub?  
I have tried the commands to through the terminal (the get grub) but doesn't seem to work. I tried downloading one of the 3rd party grub files magicboot or something and wouldn't install.

Thanks for the help,

J

---

### Post by jeppewinther on 2009-07-20
Well, assuming you do have Grub installed as a boot loader right now, you can fix it by telling Grub you have a windows partition you would like to boot.

You will need some information to do that though, which can be found by opening a terminal and typing```
sudo fdisk -l
```

That should give you a list of your partitions, identifiable as either a Linux partition, or an NTFS one, which is your Windows partition.

You're looking for something like this:
```
/dev/sda2   *       13996       14593     4803435    7  HPFS/NTFS

```

The important bit is the sd**A2**.

This is what we need to tell Grub where to look. A means the first Harddrive,  2 means the second partition. Grub starts counting at 0, So for me that'd be **hd0,1**.

We tell Grub where to look in the menu.lst, which can be reached here:
```

gksudo gedit /boot/grub/menu.lst

```

Right down the very bottom, you can copy paste the following, and replace hd0,1 with what fits on your harddrive.
```

 title Windows XP
 root (hd0,1)
 makeactive
 chainloader +1

```

If that didn't make any sense, just post the results of 
```
sudo fdisk -l
```
and I'll help you from there. And if it was all bloody useless, I do appologize ;)

---

### Post by mthalis on 2009-07-21
Protect your grub after install windows read this
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

