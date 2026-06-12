---
title: "Help! New External Hard Drive Broke Mid-transfer"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by westyonfire on 2009-04-10
Hi everyone,
I just bought a brand new external hard drive a few weeks ago (1TB Maxtor Basics model). It's been working fine ,until yesterday, when I was transferring music from my comp to the ehhd and it stopped mid-transfer. Kubuntu detects it when I plug it in but it can't mount the drive. All my college work is on it so I need to fix this ASAP. When I try access it through Dolphin I get this error message:

"An error occured while accessing 'Volume (ntfs)', the system responded: org.freedesktop.Hal.Device.Volume.UnknownFailure: $MFTMirr does not match $MFT (record 0). Failed to mount '/dev/sdb1': Input/output error NTFS is either inconsistent, or you have hardware faults, or you have a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into Windows TWICE. The usage of the /f parameter is very important! If you have SoftRAID/FakeRAID then first you must activate it and mount a differnt device under the /dev/mapper/ directory, (e.g. /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for the details."

...Would anyone help please?

(edit: the drive sounds like its working fine; no weird noises or anything.)

---

### Post by unutbu on 2009-04-10
I believe the symptoms you are experiencing come from the NTFS filesystem not being cleanly unmounted. This might have happened if, when the transfer froze, you powered down the machine before the partition was unmounted.

Whatever the case, below is the usual (Ubuntu) way of fixing the problem:
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdb1
```

If that does not work, you may have to find a Windows machine into which you can plug your external HD. Then run "chkdsk /f" on the drive. Reboot Windows twice. Once you get Windows to recognize the drive, make sure you click the icon or buttons to make the drive "safe to remove". At that point, you should be able to recognize the drive in Ubuntu again.

---

### Post by westyonfire on 2009-04-10
It worked! Thank you SO much. I thought I'd lost everything for a while.
Thanks again.

---

