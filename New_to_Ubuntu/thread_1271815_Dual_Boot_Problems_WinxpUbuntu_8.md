---
title: "Dual Boot Problems Winxp/Ubuntu 8"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by adventure man on 2009-09-21
Hey guys, I've had my hard drive setup as a dual boot system for a while now.  I first installed Ubuntu 8 and then installed Windows xP afterwards.  Ubuntu is the first OS to start up by default, which has been ok up until now.  I would like to change the default OS that starts up to the Windows Partition.
 
I hit escape when the pc starts up and get the OS menu.  With Ubuntu, Ubuntu (recovery) and Windows Xp as choices.  I go to edit Winxp and this comes up:
 

title windows xp (Loader)
root (hd0,1)
savedefault
makeactive
chainloader +1
 
How do I go about editing this so that windows xp starts up instead of Ubuntu?  I tried to make changes to that little passage there but it won't save, how do I do this?
 
Thanks so much for your help guys:)
 
A.M

---

### Post by swoody on 2009-09-21
In Ubuntu, open a terminal (Applications>Accessories>Terminal) and type in:
```
gksu gedit /boot/grub/menu.lst
```

Near the top of that file, you will find an entry named:
```
default         0
```

You need to change this to the entry you want to boot as default. So if your XP option is your 3rd option on the boot menu, you would chage it to:
```
default         2
```
If it is 4th, you would use "default  3", and so on.

This is also the file you need to edit if you want to make permanent changes to your boot menu. Remember to save the file when you are done editing it, and reboot your computer to try it out.

Let us know if this works for you, or if you encounter any issues :)

---

### Post by Sidewinder1 on 2009-09-21
You may wish to make a back-up of menu.lst prior to amending; just in case...

---

### Post by mikechant on 2009-09-21
Or you can install the startup-manager package and make this (and other grub related changes) via a gui, if you prefer.

---

### Post by swoody on 2009-09-21
Ah, this is true. If you do want to make a backup, in the terminal enter:
```
sudo cp /boot/grub/menu.lst /boot/grub/backup-menu.lst
```
This will copy your current menu.lst file to 'backup-menu.lst' in the same folder. If something happens where you ever need to restore your original grub menu to how it was before you edited it, you can use:
```
sudo cp /boot/grub/backup-menu.lst /boot/grub/menu.lst
```

---

### Post by oldfred on 2009-09-21
You can also move the windows stanzas above the automagic line and leave the default to 0. In your menu.lst find these lines:
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
[COLOR=Red]Put windows stanzas here[/COLOR]
### BEGIN AUTOMAGIC KERNELS LIST

If you update to a new kernel the number of windows stanza at the end will change and your default will change.

You can also modify the howmany line so when it adds new kernels it will only add/show so many. Add a new line without the comment(#).
howmany=2

---

### Post by adventure man on 2009-09-25
Thanks guys, I followed Swoody's walkthrough and it worked like a charm :)

---

