---
title: "Store and download programs to an external hardrive."
date: 2010-08-25
forum: New to Ubuntu
---

### Post by Cameron Murray on 2010-08-25
The partition I use for Ubuntu Netbook edition is only 4Gb large.

I don't want to expand the partition, is there a way to set up all files (after a point) are to be stored and run from a external hardisk?

Any help is much appreciated =)

Thanks

---

### Post by leprkhn on 2010-08-25
Well, I suppose you could install Ubuntu on the external hard drive. Then choose to boot from USB device in the netbook's BIOS settings and make USB the first boot device. Or you can press a button - F12 on my Aspire One - at the initial boot screen to access a boot menu, and choose to boot from the USB (I'm assuming) hard drive.

If that's not an option, look into editing your /etc/fstab file to mount your /home and /usr directories in the external drive. Also, if the partition is 4GB in size because you've got an SSD in the netbook, you probably want to move your swap partition off the SSD.

See this link for some optimizations for running Linux on an SSD.
[http://opentechnow.blogspot.com/2010/02/linux-ssd-optimization-guide.html](http://opentechnow.blogspot.com/2010/02/linux-ssd-optimization-guide.html)

---

