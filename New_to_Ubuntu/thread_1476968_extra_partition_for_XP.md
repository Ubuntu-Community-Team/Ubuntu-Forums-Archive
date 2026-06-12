---
title: "extra partition for XP"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by macsif on 2010-05-08
Hi,
Have just upgraded to 10.04 (Lucid) on my 80GB HDD. Nothing else on there. I would like to partition and put XP on a new partition.
a) is this possible ?
b) if so what is the proceedure.
Many thanks for any help.

---

### Post by cariboo on 2010-05-08
You can do what you want, but you have to make room at the front of the partition, as XP needs it's boot files on the first partition of the first hard drive. You can use gparted to accomplish what you need, it is in the repositories.

---

### Post by rcayea on 2010-05-08
You would have to boot from a live cd so that your hard drive can be not mounted. Then you should go to System -> Administration -> Gparted and use that to make your self room with that partition manager. If you don't have it installed Gparted can be accessed from Synaptic.

---

### Post by rcayea on 2010-05-08
Do you have the live cd? And, do you know how to boot from one?

Or, if you dont have any problem with it, you could install XP clean on the Hard drive and then use easeus partition manager, it is free....and make your ubuntu install partition from that. tHe benefit is that you can do this just from the desktop.

---

