---
title: "AMD64 No network access on 8.10, ifconfig shows device info though"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by Athiril on 2008-11-08
Running off CD on 8.10 AMD64

I have quite a few issues with this...

(Others are that the nvidia installer just quits with a blank message box with ok button - though no network access for it to download driver)

(The other is gparted can resize my windows ntfs partition but installer cannot, it quits with some kind of error doing something to the partition, which means gotta restart into windows then restart again to boot ubuntu as partition gets locked and cant mount it or do anything with it :/, also does not recognise my RAID0, sees the 2 drives as separate (3 hard drives total))


I have an ASUS P5N-MX, running 4GB of DDR2, Q6600, GTX 260, 2x WD 640GB RAID0 (onboard nvidia raid controller), and 1x 300GB Seagate SATA.

Am using a fresh burned copy of AMD64 Ubuntu 8.10, nothing is wrong with the CD or burn itself.



My network wont connect, cannot ping router, even when using manual settings, so no network, no internet.

sudo ifdown eth0 says device is not configured, sudo ifconfig eth0 shows info about the device, and Ubuntu picks up the nvidia network controller fine.. when I do a hardware test it finds it fine as well, just no actual getting onto the network.

---

