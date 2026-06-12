---
title: "Partition Issue - Can't Mount..."
date: 2010-11-08
forum: New to Ubuntu
---

### Post by demonboy on 2010-11-08
Just when I thought I was getting my head around the actual OS I went ahead and did a hard install, dual boot with XP.

However it seems I'm still not understanding the partition business correctly. I've installed Ubuntu 10.10 on the same partition as XP, giving them each 38Gb. That left the other partition (d: in Windows) but when I try and access it in Ubuntu I get this:

> 
Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 1).
Failed to mount '/dev/sda3': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.


I don't actually need anything in that partition so is there a simple way of freeing up this space so that I can use it for data storage for both XP and Ubuntu?

---

### Post by Txsfld on 2010-11-08
I'm getting basically the same error, and it manifests as being unable to boot my XP partition now, although Ubuntu 10.10 boots and runs fine. And I can't run CHKDSK/F on Windows because I can not boot that partition up - even in safe mode!

Help?!!!!

---

### Post by demonboy on 2010-11-09
Just an update - mine worked fine after THREE Windows reboots. First one was a chkdsk, second one ran as normal and then I set up another chkdsk. Appears to have worked.

Anyone know how I reset this thread to 'solved'?

---

### Post by Verbeck on 2010-11-09
under thread tools at the top

---

### Post by demonboy on 2010-11-09
Ta

---

