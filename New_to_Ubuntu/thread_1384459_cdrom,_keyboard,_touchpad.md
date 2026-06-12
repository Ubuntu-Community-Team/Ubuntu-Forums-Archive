---
title: "cdrom, keyboard, touchpad"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by 1ststallion on 2010-01-18
Hi, I'm new here. I need help. I can't mount my cdrom. Whenever I try:
mount /cdrom, it says:
special device /dev/scd0 does not exist. It never happened before. But if the CD already in the cdrom when I boot, it can be mounted like usual.
The main problem came last morning, it suddenly can't be mounted at all, even if I switch to Windows XP (I have 2 OSes in the laptop).
Then I tried some ways to get it back (I've tried the things with noaipc, MAKEDEV, and others I've found with Google but all failed). I tried something to get it back, but failed, then I set it to default. I tried another way, failed again, I set to default again. Again and again. Always failed. Until I realize that the screen resolution has changed, then the Keyboard and the touchpad has stop working! woah! I forgot what the last thing I did that made those problem! I thought I've set things to default whenever I failed, but likely I've missed something important, and I don't know what it was. The keyboard and the touchpad can't work, but work on recovery mode and XP. So the only hope is through the recovery mode and its terminal...

I don't know what to do, I can only think to backup my files and reinstall my system, but I need my cdrom works to do that.

Please help me!!


*sorry for the bad english, I just a student from a not english-speaking country

---

### Post by J V on 2010-01-18
Sounds like the hardware is fried, you probably need a new computer...

---

### Post by warfacegod on 2010-01-18
I agree that it looks like the CD-ROM is most likely broken Trying it in two OS's and getting the same result is an excellent clue that your CD-ROM is fragged.

I seriously doubt, however, that you need an entirely new computer. If you have a laptop it's possible but fairly unlikely that you can replace the drive. If you can't, you can always buy an external CD and or DVD-ROM. If you have a desktop, it is usually very easy to change a CD-ROM drive. You can find directions online.

FYI. If yours is a desktop and you decide to change the drive, you might want to take the time to clean your computers parts while it's open.

---

### Post by 1ststallion on 2010-01-18
> **warfacegod said:**
> I agree that it looks like the CD-ROM is most likely broken Trying it in two OS's and getting the same result is an excellent clue that your CD-ROM is fragged.

I seriously doubt, however, that you need an entirely new computer. If you have a laptop it's possible but fairly unlikely that you can replace the drive. If you can't, you can always buy an external CD and or DVD-ROM. If you have a desktop, it is usually very easy to change a CD-ROM drive. You can find directions online.

FYI. If yours is a desktop and you decide to change the drive, you might want to take the time to clean your computers parts while it's open.


Thanks for the reply. I need new cdrom then. But how about the keyboard and touchpad? They can't work on normal session but work properly on the recovery mode and XP...
I believe this is not about the hardware again

---

### Post by warfacegod on 2010-01-18
When GRUB loads and gives you a list of OS's to choose from, have you tried using one of the older kernels for Linux?

For example:

Your newest would say 2.6.31-16 but you may also have one that says 2.6.31-*15*

If an older one is there try it and see if your keyboard and mouse still behave the same way.

---

### Post by 1ststallion on 2010-01-18
> **warfacegod said:**
> When GRUB loads and gives you a list of OS's to choose from, have you tried using one of the older kernels for Linux?

For example:

Your newest would say 2.6.31-16 but you may also have one that says 2.6.31-*15*

If an older one is there try it and see if your keyboard and mouse still behave the same way.

There are no older kernel when grub loads. I have:

Ubuntu 9.04, kernel 2.6.28.11-generic;
Ubuntu 9.04, kernel 2.6.28.11-generic (recovery mode);
Ubuntu 9.04, memtest86+;
and
Microsoft Windows XP Professional

the keyboard can't work on the first one

---

### Post by warfacegod on 2010-01-18
I think you will have to use the command line to remove the app that runs your keyboard and mouse. I can't remember what it's called at the moment. Try searching the forums for reinstalling keyboard drivers.

---

### Post by 1ststallion on 2010-01-19
man, I'm confused

---

### Post by warfacegod on 2010-01-19
Okay. Simple solution. Save all of your files to somewhere safe (not on the partition that xubuntu is on) and reinstall xubuntu.

---

### Post by 1ststallion on 2010-01-19
> **warfacegod said:**
> Okay. Simple solution. Save all of your files to somewhere safe (not on the partition that xubuntu is on) and reinstall xubuntu.


Sure, I'm already working on it. Thanks a lot! :)

---

### Post by warfacegod on 2010-01-19
Post back if you get stuck.

---

