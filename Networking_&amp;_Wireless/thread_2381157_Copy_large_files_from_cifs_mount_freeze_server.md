---
title: "Copy large files from cifs mount freeze server"
date: 2017-12-27
forum: Networking &amp; Wireless
---

### Post by wuethrich on 2017-12-27
I've mounted a cifs share via /etc/fstab and I can access it without any problems. 

But when I try to copy large files (>2GB) my system freeze and I cannot ping it until it recovers after 5-10 minutes. When I copy smaller files (~700mb) the system freezes to but after 1-2min the file was copied to the correct location.

Is there anything I can do so that the copy process doesn't it up all my resources and freezes the server?

---

### Post by TheFu on 2017-12-28
Use either nice or ionice to limit any single process taking over all the CPU.
However, I've found that for older systems trying to use USB-connected storage, this doesn't always work.  I have a system from 2010 that effectively locks up whenever doing lots of disk I/O to USB disks.  I followed the issue as far down the hardware as I could and determined that the backplane of the system wasn't designed to handle USB3 throughput over the PCI ports.  Basically, there was nothing I could do do make it better besides slow the disks down to USB2 speeds.

I can also confirm that newer, very cheap, Intel systems ($100 for G3258 CPU+MB) that have USB3 built-in, handle the same throughput just fine.

I'm assuming that you are trying to write to USB storage because that is where I've seen this issue?   If that isn't the case, please outline all the components from the NIC to the MB to the SATA connection to the disk being used.  Also, the amount of disk buffers and network buffers would matter, as would the method used to copy the files. The exact motherboard version, including any revisions could lead to an architecture diagram that will show where the MB design fails to move the data as quickly as your disk can support.  Can't always find those, but sometimes you can.  If their is a throughput limitation built into the MB, no use in trying to find other solutions to the issue.

 I almost always use rsync to copy files. This provides a --bwlimit setting which might be useful to you.  The manpage has details.

---

### Post by wuethrich on 2018-01-01
I'm trying copy large files from a NAS to my server over network. I tried the --bwlimit and it worked with a limit of 5m but that's slower than my internet connection. When I try higher limits like 10m my server freezes again. That's really strange because I can download large files from the internet with a bandwidth higher than 10m without any issue.

nice or ionice isn't really an option because my ultimate goal is to use the mount like a normal folder so that other programs can access it and I can't limit every program that access these files.

I've attached hardware specs ([ATTACH]277990[/ATTACH]). If you need any further information just let me know. Thanks!

---

