---
title: "Install Problem-GRUB not installed"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by soaklord on 2010-02-21
I have a Lenovo W700 that I am trying to install Ubuntu on and am running in to difficulties.  The install works fine until I get to the Installing GRUB portion of the install, where I get a failure every time.  The failure states (paraphrasing) Failed to install GRUB, without GRUB, Ubuntu will not load.  The machine is running in a RAID (2x200GB for 400GB total).  Windows 7 still works fine after each failure and I can see the swap partition and the partition I set for / but when I go to install again, it is never formatted as a EXT4, it shows as a "do not use" partition that I again format, choose at Root.  I am guessing the issue is due to the RAID, but it sees the partitions as RAIDed and seems to recognize everything ok.  I have updated the BIOS, tried again, same result.  Any help would be GREATLY appreciated.  BTW, it runs just fine as both a VM and a liveCD/USB Persistent install, so it isn't failing completely, just at GRUB.

---

### Post by mikeyphi on 2010-02-22
There's some info here about installing on RAID

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

