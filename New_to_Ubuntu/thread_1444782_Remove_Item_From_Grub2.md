---
title: "Remove Item From Grub2"
date: 2010-04-01
forum: New to Ubuntu
---

### Post by Fidelio on 2010-04-01
Hi,
I'm sorry if this is very obvious, but I can't work out how to do it. I have a laptop running 9.10. It's a dual boot with Vista. There is a 'hidden' partition, ie hidden from vista but not from grub, which has re-installation files for Vista, and this shows up in the grub menu when I boot.
So it shows Ubuntu, then Vista Loader sda1, Vista Loader sda 2. Sda2 is the actual Vista boot. Sda1 is the recovery partition. If I (or my wife, or my kids...) select the wrong Vista Loader it starts doing its recovery thing and wipes Grub, so I really want to remove this entry from the boot options. Can't work out how to at all. Any ideas?
Thanks
Andy

---

### Post by Girya on 2010-04-01
I used this how to to get rid of different kernels from the grub menu maybe it will help. 

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2]("http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2")

---

### Post by drs305 on 2010-04-01
Here is a guide I wrote when Grub 2 came out called "Grub 2 Title Tweaks" that covers how to hide Windows Recovery partitions:
[http://ubuntuforums.org/showthread.php?t=1287602]("http://ubuntuforums.org/showthread.php?t=1287602")

The entire post is high on the "Geek" scale - it's not difficult but it is different from normal GUI operations. If you don't understand something just ask.

---

### Post by Fidelio on 2010-04-01
> **drs305 said:**
> Here is a guide I wrote when Grub 2 came out called "Grub 2 Title Tweaks" that covers how to hide Windows Recovery partitions:
[http://ubuntuforums.org/showthread.php?t=1287602]("http://ubuntuforums.org/showthread.php?t=1287602")

The entire post is high on the "Geek" scale - it's not difficult but it is different from normal GUI operations. If you don't understand something just ask.

Beezer! Thanks. That was exactly what I was after.

---

