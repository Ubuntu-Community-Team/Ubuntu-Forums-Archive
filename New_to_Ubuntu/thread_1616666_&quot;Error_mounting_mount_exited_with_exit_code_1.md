---
title: "&quot;Error mounting: mount exited with exit code 13&quot;"
date: 2010-11-08
forum: New to Ubuntu
---

### Post by thewhiteraven on 2010-11-08
I'm on Ubuntu 10.10 and whenever I try to mount one particular partition, I get the following error message:

> Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

I've looked around the forums for solutions but all of them involve booting into Windows and running chkdsk. I have a dual boot with Windows, but due to some unrelated problem, I'm not able to log into Windows. Is there a way to resolve this issue without chkdsk? Thanks

---

### Post by lkjoel on 2010-11-08
> **thewhiteraven said:**
> I'm on Ubuntu 10.10 and whenever I try to mount one particular partition, I get the following error message:



I've looked around the forums for solutions but all of them involve booting into Windows and running chkdsk. I have a dual boot with Windows, but due to some unrelated problem, I'm not able to log into Windows. Is there a way to resolve this issue without chkdsk? Thanks
What is the problem with using chkdsk?

---

### Post by marshmallow1304 on 2010-11-08
Do you have a Windows CD/DVD?

Here are instructions for running chkdsk from a [Windows XP]("http://kb.wisc.edu/helpdesk/page.php?id=5097") CD and from a [Vista/7]("http://kb.wisc.edu/page.php?id=6565") CD/DVD.  Remember to use the /f switch.

---

