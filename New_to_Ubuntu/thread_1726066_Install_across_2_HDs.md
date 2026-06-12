---
title: "Install across 2 HDs"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by Autodave on 2011-04-10
I have an Asus EEEPC.  1 gig ram, 2 SSD: one is a 4 gig and the other a 16 gig.  The 4 gig is much faster drive than the 16 gig.  I would like to use the 4 gig to boot and swap and the 16 gig for everything else.  How do I accomplish this when installing Ubuntu?  I am not a noob, but I have never done an install other than using entire disk and allowing Ubuntu to determine partition sizes.

Thanks in advance!

---

### Post by wolfen69 on 2011-04-10
Just choose to install ubuntu to the 4gb drive. Not much else you need to know.

---

### Post by seawolf167 on 2011-04-10
Aye, when setting up your partitioning scheme, point /boot & swap to your 4GB and mount them as /boot & swap respectively, then point everything else to your other hdd (say /, /home, etc.)

---

### Post by Hedgehog1 on 2011-04-10
You can combine the two SD drives as a single larger file system:

[IMG]http://img863.imageshack.us/img863/6315/netbooksd.png[/IMG]


***The Hedge***

:KS

**EDIT:** seawolf167's idea of '/boot' & 'swap' on the 4 gig SD and put '/' (root) and (therefore) everything else on the 16 gig SD is very a decent plan.

---

