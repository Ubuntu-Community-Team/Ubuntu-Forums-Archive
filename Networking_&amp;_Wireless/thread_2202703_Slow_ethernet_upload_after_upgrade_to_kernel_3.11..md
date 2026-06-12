---
title: "Slow ethernet upload after upgrade to kernel 3.11.0-15-generic"
date: 2014-01-30
forum: Networking &amp; Wireless
---

### Post by Stefan383 on 2014-01-30
I have upgraded Ubuntu 13.10 with the most recent packages offered, including kernel 3.11.0-15-generic. I have gigabit lan and I noticed that when I uploading large files (~2-4GB) to my Ubuntu "NAS", the **upload speed is very bad (8-9MB/s)**. Before upgrade of the kernel it used to be ~50MB/s. I made several tests, but the result was still very slow upload. Download speeds are fine - ~50MB/s

I booted from Ubuntu 13.10 live usb - upload speed was good there - ~50MB/s (there was 3.11.0-12-generic kernel).

Then I booted my Linux with selecting older kernel 3.11.0-12 in Grub menu. --> with this kernel the upload and download speeds are fast - ~50MB/s. So I assume the problem is in the kernel 3.11.0-15.

I have this ethernet controller: Ethernet controller: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet (rev c0) Using this module: atl1c

Further test1: I did one test once more to be sure - a clean  installation of Ubuntu 13.10. Ethernet upload speed was fine - ~50MB/s,  but then Ubuntu asked for upgrade of the packages and installed kernel  3.11.0.15 and after that the upload speed is again only ~8-9MB/s -->  so bad.

Further test2: I installed this kernel:  3.12.0-031200-generic, but again the same behaviour - slow upload speed. 

I even tried this siilly thing - to copy /lib/modules/3.11.0-12-generic/kernel/drivers/net/ethernet/atheros/atl1c/atl1c.ko to /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/atheros/atl1c/atl1c.ko --> but then the same issue with 3.11.0.-15 kernel - slow upload speed.

Any ideas what's wrong with the new kernels? Or how to fix this without sticking to the old kernel or buying new NIC?

THX

---

### Post by Stefan383 on 2014-01-31
No ideas?

---

### Post by Stefan383 on 2014-02-01
Bump

---

### Post by Stefan383 on 2014-02-03
So no ideas? No body with the same NIC / issue?

---

### Post by Stefan383 on 2014-02-11
OK, this bug has been fixed in the currently "proposed updates" kernel 3.11.0-17-generic (version 3.11.0-17.31).

---

