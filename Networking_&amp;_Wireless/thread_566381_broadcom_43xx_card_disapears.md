---
title: "broadcom 43xx card disapears"
date: 2007-10-03
forum: Networking &amp; Wireless
---

### Post by kane77 on 2007-10-03
I have a problem with my wifi in my laptop (it's broadcom) I installed the fwcutter but it acts strange: 
it works (I have eth1 listed in ifconfig, it scans with iwlist scan), then when I enable roaming mode it still seems to work, but when I disable it again it stops working and it disapears from ifconfig, iwlist says eth1 doesn't support scanning.. 
do you think that this is a driver issue?

---

### Post by kevdog on 2007-10-03
Im not sure what would be causing that unless the interface isnt being brought back up either automatically or manually.  When you get this problem, try typing--
sudo ifup eth1

and then retry iwlist scan.

---

### Post by kane77 on 2007-10-10
> **kevdog said:**
> Im not sure what would be causing that unless the interface isnt being brought back up either automatically or manually.  When you get this problem, try typing--
sudo ifup eth1

and then retry iwlist scan.

no ifup throws an error code..

---

### Post by kevdog on 2007-10-10
Not sure what is causing the problem, however I would probably switch course, and go for a ndiswrapper install of the winxp drivers rather than the bcm43xx cutter approach.  Seems like the ndiswrapper approach is much more stable (at least thats what it appears like through perusal of the forums).

---

