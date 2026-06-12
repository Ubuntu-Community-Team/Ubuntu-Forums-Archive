---
title: "Problems installing on external HD"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by pourquoipas on 2009-11-19
I've tried to installa ubuntu 9.10 on an external 320 GB Lacie HD.  The installation go smooth, and also the first two,three restarts but then it start to han when booting sayn errors like  &quot;Ext3-fs error (device sdb2): ext3_find_entry: reading directory #NNNNNNN offset 0&quot; Where at NNNNNN you can substitute various numbers.  When i'm booting system from an udb key with a live xubuntu 9.04 on it, i can plug and navigate on drive without any problem, i've done a badsector check without any error, and also e2fsck cant recognize any error.  I've tried to zerofill all hd and reinstalled xubuntu from the live distro on the usb key, and then upgraded to 9.10, but after 2-3 restart the error come again.  I've tried both ext3 and ext4 but i get always the same error.   On HD i usually made 4 partitions , swap (sdb0) , root (sdb1), home (sdb2) and, usually using ubuntu, i made a 4th ntfs partition to use as repository for both ubuntu and windows.  I don't know if this ntfs partition can generate some strange error on disk checking.   The hd appear not support smart, i don't know if it's cause usb interface.

---

