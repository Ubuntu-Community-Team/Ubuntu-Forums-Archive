---
title: "Won't install on my AMD PC (no live filesystem)"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by MdX MaxX on 2010-10-15
Okay, my original problem was resolved by me using a CD instead of a USB drive, but now I have a new problem; my PS/2 mouse won't work.  It worked in XP, so I'm thinking it's a software issue.  Are there any PS/2 drivers I can get?  My PS/2 keyboard works, so I don't get why the mouse doesn't.

Original issue:
> Hi everyone, I'm new to Linux, it's my first time getting familiar with anything other than Windows.

I used Wubi to dual-boot Windows 7 and ubuntu 10.10 on my hp Core 2 Quad desktop, and it works very well.  I've had no problems with either OS.

Now, I want to install ubuntu on my old Athlon 64 X2 PC.  I want to wipe the entire drive and install ubuntu.

I set up a bootable USB flashdrive according to the instructions on the download page, and stuck it in my old pc.  I booted from the USB drive and was able to get to the ubuntu splash screen with the flashing orange/white dots.  After that, however, I get a 'BusyBox' screen that says '(initramfs) Unable to find a medium containing a live file system'

I've searched and others have had this problem, but there seems to be no solution.  Is there anyway to solve this?  I re-downloaded the iso and replaced it on the flashdrive, and the issue persists.  Is there some mount command I can try?  Is there any other way to wipe XP and install ubuntu?

---

### Post by RedRat on 2010-10-15
> **MdX MaxX said:**
> Hi everyone, I'm new to Linux, it's my first time getting familiar with anything other than Windows.

I used Wubi to dual-boot Windows 7 and ubuntu 10.10 on my hp Core 2 Quad desktop, and it works very well.  I've had no problems with either OS.

Now, I want to install ubuntu on my old Athlon 64 X2 PC.  I want to wipe the entire drive and install ubuntu.

I set up a bootable USB flashdrive according to the instructions on the download page, and stuck it in my old pc.  I booted from the USB drive and was able to get to the ubuntu splash screen with the flashing orange/white dots.  After that, however, I get a 'BusyBox' screen that says '(initramfs) Unable to find a medium containing a live file system'

I've searched and others have had this problem, but there seems to be no solution.  Is there anyway to solve this?  I re-downloaded the iso and replaced it on the flashdrive, and the issue persists.  Is there some mount command I can try?  Is there any other way to wipe XP and install ubuntu?
Sounds as if your USB stick installation is not well. Why not just boot from the CD? Of course do you have sufficient memory, I believe that you need 2 GB for 10.x versions.

---

### Post by MdX MaxX on 2010-10-15
Okay, I'll try it.  Hopefully it works.

If I recall, others had this problem with CDs as well, so it may not work...

---

### Post by cariboo on 2010-10-15
How did you create your usb boot drive? There have been many people having problems creating them in Windows or older versions. I've been using Maverick since the toolchain upload and haven't had any problems with usb boot disks created in Maverick.

---

### Post by MdX MaxX on 2010-10-15
Ah, the CD worked!  It was slower, but oh well.

I used ubuntu to make the USB boot drive the first time, and used Win7 and Universal USB installer to make it the second time.  I re-downloaded the iso each time.  I wonder why it didn't work.  I was going to assume a problem with IDE HDDs/Optical Drives, but the CD worked...

Anyway, I have a new problem.  My PS/2 mouse won't work.  It worked when I had XP installed on the same PC, so I'm guessing it's a linux problem (the mouse doesn't work when I boot gParted off a LiveCD either).  Is there some driver I can download?

---

