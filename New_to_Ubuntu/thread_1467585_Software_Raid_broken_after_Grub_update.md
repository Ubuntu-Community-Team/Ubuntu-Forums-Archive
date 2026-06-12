---
title: "Software Raid broken after Grub update"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by jaybeatle on 2010-04-30
Hi everyone.  First post and a ubuntu newb, so please be gentle.

I've been running a 4 drive Software Raid5 utilising mdadm for awhile now.  During my initial installation of Ubuntu Karmic, I had set aside a separate smaller drive to run the OS.  That drive was set as sde1.  Therefore, when I assembled the array sda1 -> sdd1 were used.

Since I upgraded grub via the newest Lucid release, my array is only recognizing drives sdb1 -> sdd1.  After fdisk -l, I realized that grub has assigned sda1 to my OS drive.  I assume I can just add the other drive to the array and reassemble, but is there a simpler way that I'm missing?

Thanks in advance!

UPDATE:

I figured it out.  I just needed to fix the /etc/mdadm/mdadm.conf.  I'm not sure why I didn't think of that initially

---

