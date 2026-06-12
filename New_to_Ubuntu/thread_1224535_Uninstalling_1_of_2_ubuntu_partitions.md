---
title: "Uninstalling 1 of 2 ubuntu partitions"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by lolwhites on 2009-07-27
When I first upgraded from 8.10 to 9.04, I ran into graphics problems due to my Intel chipset.I tries various howtos and ended up borking my system, so I reinstalled 8.10.

Recently, rather than risk my system, I installed 9.04 alongside 8.10 as a dual boot system, to allow me to tweak with the 9.04 partition while leaving the main one intact. After a few upgrades, it was clear that I now have proper graphics.

My question is this: What's the best way of upgrading my 8.10 partition to 9.04 and reclaiming the disk space. My plan is to first use Gparted to delete the 9.04 partition and resize the 8.10 one to reclaim all the space, then upgrade 8.10 to 9.04. Is that the right way to go?

---

### Post by credobyte on 2009-07-27
Boot from your Live CD and do all the stuff from there ( delete, merge, etc. ). 8.10 uses ext3 ( in your case ) ?

---

### Post by lolwhites on 2009-07-27
I know I'll have to use a live CD to sort out the partitions, but I want to upgrade 8.10 to 9.04 via the software update tool so as to automatically update the extra repos I've added rather than add them again manually.

My 8.10 uses ext3

---

