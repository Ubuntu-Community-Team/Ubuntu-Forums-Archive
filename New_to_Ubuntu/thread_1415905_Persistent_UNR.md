---
title: "Persistent UNR"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by Ryasaurus on 2010-02-25
So I downloaded the .iso on this 8GB flash drive. I created myself and such, but I'd rather not have to sign out of the live user account to get to mine. Basically, I wanna make it persistent. How can I put it onto my USB drive rather than my main SSD? (It doesn't have that much space left, due to Windows 7) I don't see that option in the installer.

Thanks in advance!

---

### Post by linuxuser21 on 2010-02-25
Have you tried the Ubuntu USB Creator?  Find it by going to System-->Administration-->Create a USB startup disk.  If you need some information on it [here]("https://help.ubuntu.com/community/Installation/FromUSBStick") is some documentation.  This will put it on your thumb drive and you can boot into it like you would with a Live CD.  Only, unlike the Live CD, you can set aside space on the thumb drive where it will save all your documents, setting and such.

---

### Post by Ryasaurus on 2010-02-25
Would that make it persistent? Because the help page says Create A Live CD. I want a complete installation as if it was on a hard disk, but on my pendrive. The same one that I have the Live CD one on. Would that be possible? Or do I have to install it to a different USB drive and to install it on this one?

---

### Post by linuxuser21 on 2010-02-25
If installed this way, it treats your flash drive as if it was a hard drive.  You can boot into it, save files right on it, it keeps all your settings and can even run updates.  I think it does treat it as a Live session; however, it's hardly noticable because it does have all the functionality of a full install.  You can also use the flash like you normally would when not running ubuntu from it.

---

### Post by Ryasaurus on 2010-02-25
That's exactly what I don't want. I tried to delete the live account, but it says I can't. 

Is there a reason that when I try to use Install Netbook-Remix 9.10, that I can't install it to this flashdrive? I even tried doing it from another flashdrive.

---

### Post by linuxuser21 on 2010-02-25
Okay, I found a thread that explains how what to do for this [here]("http://ubuntuforums.org/showthread.php?t=1014968").  You basically do a full install onto the flash drive and just set up GRUB to boot from your flash drive.  This thread also suggests that you should remove the Tracker program when you do this.
Why won't it allow you to install it to a flash drive?  When the format section of the install, it should actually show up as a hard drive.  Depending on how many hard drives and partitions you have on your computer, it should be like /sdb1 or /sdc1.  You'll know if it's your flash drive because of the size.  If none of this works, you could try backing up all data on your flash dive and formatting it to ext4 or ext3.

---

### Post by Ryasaurus on 2010-02-26
I got it to work! I just had to clear everything off of the flash drive so that there was space to put UNR. Thanks!

---

### Post by linuxuser21 on 2010-02-26
:) No problem!

---

