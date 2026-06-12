---
title: "Ubuntu Desktop and IBM xSeries server: Disks and SAN issues"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by Abu_Dayya on 2010-11-30
I installed Ubuntu 9.04 on an IBM xSeries 346 server, in a dual mode setup with windows 2003nt I guess. I don't usually work with xSeries machines, hence my problems.

- There are two 73GB disks on there, and configured with RAID (don't know which one exactly, but I'm assuming RAID1) which I didn't know of in the begining. To install ubuntu, I partitioned the C: drive in windows and made D:. then when I went ahead and began installing ubuntu, I found 4 disks. Two for windows and two empty ones, which are the ones I partitioned to make the D: drive. So I chose one of the empty ones and installed ubuntu. Now in Ubuntu I see the two Windows disks, plus an empty D: disk???

Is there a way to clean this mess up? either by running ubuntu in RAID1 on the two emtpy disks or something?

- The second (and most important) issue, is that I have a 1TB disk on a SAN connected to the server through two Fibre Channel cards. The disk is accessable in Windows, but I don't see it in Ubuntu. when I run lspci I see two fibre channels apearing

```
Fibre Channel: QLogic Corp. QLA2300 64-bit fibre channel Adapter
```
So, what to do to get the disk in Ubuntu?

Thanks

---

### Post by mikechant on 2010-11-30
Have a look at this:
[http://cateee.net/lkddb/web-lkddb/SCSI_QLA_FC.html](http://cateee.net/lkddb/web-lkddb/SCSI_QLA_FC.html)

I'm pretty sure the 9.04 kernel is in the range specified (i.e. >2.6.16), so you should have the driver installed, but I'm not sure whether this implies you need to manually obtain the relevant firmware image - worth a look?

---

### Post by ibizatunes on 2010-11-30
Why not install 10:04 LTS server version, 
as 9.04 is end of life or getting that way..... you need to download the drivers your you Qlogic card, and then compile them into the kernel

---

### Post by mikechant on 2010-11-30
> you need to download the drivers your you Qlogic card, and then compile them into the kernel 

This should not be necessary, I've checked and 9.04 used the 2.6.28 kernel, so the drivers should already be included (although as per above the firmware image might be needed but that's a simple download/place in directory, no recompile reqd).

However, I'd certainly agree that it would be a very good idea to get onto the LTS 10.4 version ASAP, 9.04 support was scheduled to end last month (Oct 2010).

---

### Post by Abu_Dayya on 2010-12-06
> **mikechant said:**
> Have a look at this:
[http://cateee.net/lkddb/web-lkddb/SCSI_QLA_FC.html](http://cateee.net/lkddb/web-lkddb/SCSI_QLA_FC.html)

I'm pretty sure the 9.04 kernel is in the range specified (i.e. >2.6.16), so you should have the driver installed, but I'm not sure whether this implies you need to manually obtain the relevant firmware image - worth a look?

Firmware image of what exactly?

---

### Post by Abu_Dayya on 2010-12-06
> **mikechant said:**
> This should not be necessary, I've checked and 9.04 used the 2.6.28 kernel, so the drivers should already be included (although as per above the firmware image might be needed but that's a simple download/place in directory, no recompile reqd).

However, I'd certainly agree that it would be a very good idea to get onto the LTS 10.4 version ASAP, 9.04 support was scheduled to end last month (Oct 2010).

I posted the previous post without opening the link you provided, but now I see where to get it from. Now my question is where to place it? in which directory?

And I'd rather fix the problem I have on 9.04 instead of having to upgrade to 10.04

---

### Post by mikechant on 2010-12-08
> Now my question is where to place it? in which directory?

I think you need to put the ql2300_fw.bin either in /lib/firmware or /lib/firmware/[kernelversion] - this may have changed at some point so you could try both.

---

