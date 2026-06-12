---
title: "Just installed 8.10 ALT; get a busy-box prompt on first boot from HD"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by diablo75 on 2009-01-14
I'm trying to install Ubuntu on an HP Pavilion 8754c.  I used the Ubuntu Alternate CD because the Live CD almost instantly threw me to a Busybox prompt for some reason.  The Alternate CD installed the OS with no errors... I think.

After the first reboot, the grub menu began to load... and took a very long time at that.  Then I got the busybox prompt (see the attached picture).

I have no idea what to make out of this or what to do next.  Perhaps someone knows what it means?

---

### Post by taurus on 2009-01-14
Did you install intrepid on it own partition (ext3 filesystem) or did you use wubi?

---

### Post by Titan8990 on 2009-01-14
From the grub menu:

Highlight the Ubuntu entry that use to boot.


Hit "e" to edit the enty.


Highlight the kernel= line and hit "e" to edit it.


add:


acpi=off


to the end of that line and press enter


now hit "b" to boot ubuntu

---

### Post by Bölvaður on 2009-01-14
The error message on the photo is very unexpected. Did you double check if grub is booting to correct device?
You could also try and not use uuid

---

### Post by diablo75 on 2009-01-14
The install used the entire hard drive on it's own partition (Guided: Whole Disc).

---

### Post by Titan8990 on 2009-01-14
Sorry, should have read that bit further. 

Still add the acpi=off line like I instructed in my first post.


Also change the /dev/disk/by-uuid/xxxx to /dev/sda1 and see if that resolved the issue

---

### Post by diablo75 on 2009-01-14
> **Titan8990 said:**
> Sorry, should have read that bit further. 

Still add the acpi=off line like I instructed in my first post.


Also change the /dev/disk/by-uuid/xxxx to /dev/sda1 and see if that resolved the issue

I'm about to head to the place where this PC is and give these a shot.

If it works, will I have to have them do these things every time they turn the computer on, or will these settings hold/stick after I add them?

---

### Post by Titan8990 on 2009-01-14
No, edits from the grub menu will not stay. If it works you will have to manually make the change in /boot/grub/menu.lst

---

### Post by Bölvaður on 2009-01-14
> **diablo75 said:**
> I'm about to head to the place where this PC is and give these a shot.

If it works, will I have to have them do these things every time they turn the computer on, or will these settings hold/stick after I add them?

if you change a text file it will stick. so if you change fstab or menu.lst it will stick but editing parameters on the boot menu will not stick, if you catch my drift.

---

### Post by avtolle on 2009-01-14
Take a look at [https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Permanently%20On%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Permanently%20On%20An%20Existing%20Installation) for assistance and information.

---

### Post by diablo75 on 2009-01-14
Turns out the problem was a bad CD-ROM drive.  I don't know what the issue is with it, but with the power attached, it won't eject.  I remember seeing something about "ata2" just before installing, but since it didn't fail to load the installer, I ignored it.  Detaching the drive solved the problem and I'm typing this on the old system right now.

---

