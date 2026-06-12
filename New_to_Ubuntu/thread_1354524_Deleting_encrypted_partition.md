---
title: "Deleting encrypted partition"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by thatperson42 on 2009-12-14
When I first installed Ubuntu 9.10, I chose to have it encrypted during set-up. Now, I've had some kernel problems (and filed a bug report), and I'm unable to log on normally (if I try doing so it just reboots). I can log on in recovery mode (with just access to the terminal), and I can boot from a live cd.

If I try to reinstall the system from a live cd, the computer just reboots (I presume this is because the hard drive is encrypted). How do I decrypt the hard drive or reinstall the system?

---

### Post by x33a on 2009-12-14
you could boot from gparted live disc. then use it to format the root partition. make a new partition and install ubuntu on it.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by talsemgeest on 2009-12-14
Simply boot from the live CD, go to System>Administration>Partition editor, and delete the partitions. Then you can install ubuntu onto the free space.

---

