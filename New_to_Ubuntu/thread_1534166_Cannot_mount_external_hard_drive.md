---
title: "Cannot mount external hard drive"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by Fifthmarch on 2010-07-19
When I try to mount my external hard drive, I'm getting this error message:

Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

Has anyone faced something like this? Why does it say it needs a Windows system, and is there a workaround to solve the problem using only Ubuntu?

Thanks

---

### Post by Gone fishing on 2010-07-19
Had similar but not quite the same (I assume you arn't using a software raid?). The ntfs fixing tools in Linux are limited hence asking you to use Windows and chkdisk.

I think you can force a mount - however, it would probably be better to fix in Windows if you don't have Windows borrow someonce Windows CD and fix the problem in the console. 

But if you don;t have Windows why use ntfs?

---

### Post by Fifthmarch on 2010-07-20
> **Gone fishing said:**
> 

But if you don;t have Windows why use ntfs?

I bought the drive before I switched to Linux :(

Is there a way to use a Windows CD to check the drive without installing Windows? (I think not...Just checking)

---

### Post by CharlesA on 2010-07-20
I think it depends. I know you can use a XP CD to boot into the recovery console and run chkdsk from there, but I don't know if it will work without installing Windows.

As for the newer versions of Windows, you can select "repair" after booting off the DVD and run it from there.

---

### Post by Gone fishing on 2010-07-20
Yes you can use an XP disk to fix this without installing. As its an external disk you could just plug into someones XP PC and run chkdsk

---

### Post by Fifthmarch on 2010-08-10
It works after I ran chkdsk from a Virtualbox XP installation. Thanks!

---

