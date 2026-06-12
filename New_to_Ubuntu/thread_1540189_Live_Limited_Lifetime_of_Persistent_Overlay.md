---
title: "Live Limited Lifetime of Persistent Overlay"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by rrll1977 on 2010-07-27
Hi thanks for looking to,

I was wondering whether LUBUNTU live has also a limited lifetime persistent overlay as mentioned on this wiki:

> [How to create and use Live USB]("http://fedoraproject.org/wiki/FedoraLiveCD/USBHowTo")
.....
**Limited Lifetime of Persistent Overlay** 
One very important note about using the "primary" persistent overlay for system changes is that due to the way it's currently implemented (as a LVM copy-on-write snapshot), every single change to it (writes AND deletes) subtracts from its free space, so it will eventually be "used up" and your USB stick will no longer boot. Because of these limitations, it is advisable to use the system-level persistence sparingly, for configuration changes and important security updates only. For a truly persistent write-many (vs write-once) overlay, use the --home-size-mb option to create a home directory filesystem image for personal files. Unlike the primary system overlay image, the home.img can be re-used and loop mounted outside of the liveusb environment.

I tried fedora 13 live on a 1GB usb drive but after a couple of days of using the system only for browsing, the usd disk was full and couldn't boot anymore.

Thanks for the info.

---

