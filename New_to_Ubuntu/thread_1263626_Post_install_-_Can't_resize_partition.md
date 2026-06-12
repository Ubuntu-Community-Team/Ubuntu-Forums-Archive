---
title: "Post install - Can't resize partition"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by franklin_m on 2009-09-11
Hello,

I successfully installed netbook remix (9.04) on my netbook in a dual boot configuration with windowsxp.  I'd like to decrease the size of the windows partition so that I can make room for a shared area. I've downloaded and installed Gparted, but it won't let me adjust the size. Any help would be appreciated.

(I've tried logging on as root user...same result).

Thanks,
Frank

---

### Post by Bartender on 2009-09-11
Follow the link under my sig, download the latest stable version, burn to a CD as an image (just like an Ubuntu CD) then boot from the CD.  GParted looks the same (because it is) as the partitioner you were trying to use, but it works better when implemented from the stand-alone disc because the partitions aren't mounted.  In all likelihood the partition you're trying to move is mounted, or next to a partition that's mounted.

---

### Post by LewRockwell on 2009-09-11
> **franklin_m said:**
> Hello,

I successfully installed netbook remix (9.04) on my netbook in a dual boot configuration with windowsxp.  I'd like to decrease the size of the windows partition so that I can make room for a shared area. I've downloaded and installed Gparted, but it won't let me adjust the size. Any help would be appreciated.

(I've tried logging on as root user...same result).

Thanks,
Frank

you'll need to boot from a LiveCD via an external optical device or boot from a LiveUSB media to work properly with the internal hard drive

.

---

### Post by franklin_m on 2009-09-13
Thanks everyone. I used Gparted as bootable CD and was able to resize.

Frank

---

