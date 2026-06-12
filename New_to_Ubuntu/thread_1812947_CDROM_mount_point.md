---
title: "CDROM mount point"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by Foobarz on 2011-07-27
Ok, this is a simple question which I (the novice) does not know the answer to? How do I mount my cd drive. There is no cdrom entry in fstab, and no mount point in /media, /cdrom, or /dev. What do I do?


PS: I'm trying to install XP on Virtualbox, and Virtualbox doesn't detect a CDROM drive, just this virtual drive that doesn't work.

---

### Post by 2F4U on 2011-07-27
Usually, the CD should be automatically mounted for you. Is this not working, or is it just not working for the Windows XP CD?

---

### Post by amjjawad on 2011-07-27
> **Foobarz said:**
> Ok, this is a simple question which I (the novice) does not know the answer to? How do I mount my cd drive. There is no cdrom entry in fstab, and no mount point in /media, /cdrom, or /dev. What do I do?


What version/release of Ubuntu do you have?


> PS: I'm trying to install XP on Virtualbox, and Virtualbox doesn't detect a CDROM drive, just this virtual drive that doesn't work.

When you insert any CD to your drive, what will happen? your CD should be mounted automatically once you insert it.

Are you using this one: [http://www.virtualbox.org/](http://www.virtualbox.org/) ??

---

### Post by Foobarz on 2011-07-27
Ok, how do I add my CD to virtualbox? I see tutorials explaining to add it during the first run wizard, but Virtualbox only detects a virtual drive (which it cannot boot from, since it is not my real CD drive.)

---

### Post by amjjawad on 2011-07-28
> **Foobarz said:**
> Ok, how do I add my CD to virtualbox? I see tutorials explaining to add it during the first run wizard, but Virtualbox only detects a virtual drive (which it cannot boot from, since it is not my real CD drive.)

I'm online from my cell. I'll post a screen shot once I'll login to my PC ;)

---

### Post by Foobarz on 2011-07-28
I also tried this: Use brasero to burn my XP disc to an image file, but brasero doesn't detect anything in my CD drive. It seems I have mostly a problem with the XP installation disc, since I can play music from audio CD's.

---

### Post by gdonwallace on 2011-07-28
First thing to understand is that the CD Drive will not show up in FSTAB or under any mount points until a CD is in the drive.  This is because the CD drive does not have an active OS installed.  FSTAB (File System Table) only shows a partition if it has an active File System.

As to installing XP in Virtualbox.  The way I do it is to create the virtual Hard Drive first.  Set it to be able to expand as needed.  Once created, go to the storage tab, click on the CD Drive and make sure that the option for the CD is set to the CD Drive physically listed there and make sure that pass through is activated.  Next create a new virtual machine for Win XP.  Insert your XP CD and then launch the new machine.  It will read from your CD at that point and you will be able to install XP.

---

### Post by amjjawad on 2011-07-28
> **amjjawad said:**
> I'm online from my cell. I'll post a screen shot once I'll login to my PC ;)

There you go:

---

### Post by Foobarz on 2011-07-28
Thank you all for your help. I seem to understand the concept of mounting a hard drive. My main question now is why nothing shows up in the cd drive when I put my XP installation disc in. I can explore the disc in my Windows, so it's definitely not corrupted. And my Windows is on the same computer as my Ubuntu, just a different partition, so my CD drive is definitely not broken. Any suggestions on viewing my CD?

---

### Post by amjjawad on 2011-07-28
> **Foobarz said:**
> Thank you all for your help. I seem to understand the concept of mounting a hard drive. My main question now is why nothing shows up in the cd drive when I put my XP installation disc in. I can explore the disc in my Windows, so it's definitely not corrupted. And my Windows is on the same computer as my Ubuntu, just a different partition, so my CD drive is definitely not broken. Any suggestions on viewing my CD?

I'm confused here so please explain whether you want your Windows Disc to be mounted in the VirtualBox or in Ubuntu or both?

As in VirtualBox, I already uploaded a Screenshot for you.

As for Ubuntu, try to insert different CD/Disc and see what will happen?!
If the CD/Disc works in Windows, it doesn't mean to necessarily work in Ubuntu too, specially if there is something wrong!

---

### Post by Foobarz on 2011-07-28
Other CD's do work, but the thing is that though I can view my other audio CD's, they never appear in the /media or /mnt directory, or even the directory of the same name, /cdrom. I attributed my inability to view the contents of my XP installation disc to this, since CD's also contain a filesystem, ISO9660, and therefore should appear in /media or /mnt. When I mount my windows partition, it appears in the /mnt folder. Why should CD's be any different. Is there something wrong with my fstab or mstab???

Update: Never mind, other CD's no longer work. Tried putting an audio cd in and it gives me this error: 
Unable to mount Audio Disc
DBus error org.freedesktop.DBus.Error.InvalidArgs: Mountpoint Already registered

---

### Post by amjjawad on 2011-07-28
> **Foobarz said:**
> Other CD's do work, but the thing is that though I can view my other audio CD's, they never appear in the /media or /mnt directory, or even the directory of the same name, /cdrom. I attributed my inability to view the contents of my XP installation disc to this, since CD's also contain a filesystem, ISO9660, and therefore should appear in /media or /mnt. When I mount my windows partition, it appears in the /mnt folder. Why should CD's be any different. Is there something wrong with my fstab or mstab???

Update: Never mind, other CD's no longer work. Tried putting an audio cd in and it gives me this error: 
Unable to mount Audio Disc
DBus error org.freedesktop.DBus.Error.InvalidArgs: Mountpoint Already registered

Are you sure on the same PC, same CD Drive, all CDs work fine while you are logging in to Windows? and they don't ever work while you are logging in to Ubuntu? just to confirm.

---

### Post by Foobarz on 2011-07-28
Other CD's do work, but the thing is that though I can view my other audio CD's, they never appear in the /media or /mnt directory, or even the directory of the same name, /cdrom. I attributed my inability to view the contents of my XP installation disc to this, since CD's also contain a filesystem, ISO9660, and therefore should appear in /media or /mnt. When I mount my windows partition, it appears in the /mnt folder. Why should CD's be any different. Is there something wrong with my fstab or mstab???

---

### Post by Foobarz on 2011-07-28
That's BS! I put the installation disc in, and miraculously an icon appears on my desktop. Huh. . . Well, thanks anyway to everybody here.

---

### Post by amjjawad on 2011-07-28
> **Foobarz said:**
> Other CD's do work, but the thing is that though I can view my other audio CD's, they never appear in the /media or /mnt directory, or even the directory of the same name, /cdrom. I attributed my inability to view the contents of my XP installation disc to this, since CD's also contain a filesystem, ISO9660, and therefore should appear in /media or /mnt. When I mount my windows partition, it appears in the /mnt folder. Why should CD's be any different. Is there something wrong with my fstab or mstab???

:)

I expected YES or NO, not the same previous post :)

We need to make sure first it's not a hardware issue.

---

### Post by amjjawad on 2011-07-28
> **Foobarz said:**
> That's BS! I put the installation disc in, and miraculously an icon appears on my desktop. Huh. . . Well, thanks anyway to everybody here.

Magic maybe? :D

Enjoy!

---

### Post by Foobarz on 2011-07-28
No still not magic. After installing XP in virtualbox, I tried putting the disc in FIVE MORE TIMES and all it would do is jitter around (you hear this clicking noise inside the disc tray.) But the weird things is that audio CD's work fine and there are no weird noises when I'm opening those. ???

---

