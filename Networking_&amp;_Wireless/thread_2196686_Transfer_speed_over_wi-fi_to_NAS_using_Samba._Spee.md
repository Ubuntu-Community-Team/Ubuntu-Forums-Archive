---
title: "Transfer speed over wi-fi to NAS using Samba. Speed depends on kernel"
date: 2013-12-30
forum: Networking &amp; Wireless
---

### Post by cdysthe on 2013-12-30
Hi,

I often transfer files to a NAS connected to my router. When I installed Ubuntu 13.10 on my laptop I usually got a transfer speeds right below 6 MBps which is decent. Then suddenly the speed dropped to 2-3 MBps and I had no idea why. I looked at recent updates and I just had a kernel upgrade. I then booted the previous version of the kernel and the speed went back up again. I also tried two of the newer mainline kernels, 3.12 and 3.13 from the Ubuntu kernel repo. With 3.12 the speed was still down between 2 and 3 MBps. but with the 3.13 kernel it was up to above 7 MBps, faster than with any other kernel. Why is it such a big difference between kernel versions even between the 3.11 kernels where the initial one that came with 13.10 had the higher upload speed while the latest upgrade 3.11.0.14.15 is slow?

---

### Post by tgalati4 on 2013-12-30
A lot of tablets were purchased for Christmas, so my guess is wireless interference.  The more devices in the vicinity, the less bandwith.  Do your tests with a wired connection to remove the wireless confounding.

---

### Post by cdysthe on 2013-12-30
No, I did not try with wired connection, but I do not think this has to do with devices around here since the difference is so profound and consistent depending on the kernel version booted. I can boot 3.12 and do a couple of transfers without ever getting above 3 MBps. Then reboot 3.13 and the transfer (of the same files) are all of a sudden consistently above 7 MBps.

---

### Post by tgalati4 on 2013-12-30
Run and post some *iperf* results using a wired connection to compare the two kernels.  Some examples in this thread:  [http://ubuntuforums.org/showthread.php?t=2143393&highlight=iperf](http://ubuntuforums.org/showthread.php?t=2143393&highlight=iperf)

---

### Post by silentcreek on 2014-01-08
I'm having the same problems with a wired conneciton (GBit). Until before Kernel updates 3.11.0-14/15 my samba speed was 80-90MB/s, now with Kernel 3.11.0-14/15 it is down to 7-9MB/s (ethernet still works with 1GBit/s - I checked that). Since I don't have a display or keyboard connected to my small server, I can't simply select an older kernel during the boot process, so I'm hoping this issue gets fixed soon.  Timo

---

### Post by cdysthe on 2014-01-08
> **silentcreek said:**
> I'm having the same problems with a wired conneciton (GBit). Until before Kernel updates 3.11.0-14/15 my samba speed was 80-90MB/s, now with Kernel 3.11.0-14/15 it is down to 7-9MB/s (ethernet still works with 1GBit/s - I checked that). Since I don't have a display or keyboard connected to my small server, I can't simply select an older kernel during the boot process, so I'm hoping this issue gets fixed soon.  Timo

I also tried with a wired connection and saw the same reduction with kernel 3.11.0-14/15. I am now running 3.13.0-031300rc7 and have great transfer speeds. Since this kernel otherwise works I'll stick with it until 14.04.

---

### Post by silentcreek on 2014-01-11
I installed Kernel 3.12.7 from the mainline-ppa and everything is back to normal. (I prefer the stable version 3.12 over the release candidate of the more recent version 3.13) Now I just have to see how to keep my kernel updated manually.

---

### Post by cdysthe on 2014-01-11
> **silentcreek said:**
> I installed Kernel 3.12.7 from the mainline-ppa and everything is back to normal. (I prefer the stable version 3.12 over the release candidate of the more recent version 3.13) Now I just have to see how to keep my kernel updated manually.

I still wonder what cause this slowdown in the 3.11 kernels. Guess we'll never know. We're 14.04 soon! :)

---

### Post by silentcreek on 2014-01-12
Me, too. I assume only a few people are affected, otherwise the forums would be full with complaints (even though it took me some days to notice the slowdown). I'd prefer to see a fix in the distribution kernel. But for now, I can live with the mainline kernel. And yes, 14.04 is on the horizon, too.

Btw. does anyone know how the upgrade process deals with an unsupported kernel like the mainline kernel? Will it be replaced automatically with the kernel included in the new release? Even if the installed version would be newer?

---

