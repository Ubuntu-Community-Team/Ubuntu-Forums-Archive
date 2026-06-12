---
title: "Separate home partition without live CD"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by jerrynewt on 2008-12-17
Is there any way to create a separate home partition without using a live CD? I have Jaunty 9.04 installed on my laptop (specs in signature) and used the alternate install as this is still alpha stage and no live cd is available that I can find. Being a bit slow ( my normal state I think), I didn't create the separate home during installation. Short of a new install, just wondering if it can be done. I already have the HD formatted to sda1, sda3, and sda5. Install on sda1, sda3 as ext3, and sda5 for swap. Could someone point me in the right direction? Thanks and Merry Christmas everybody !!!

---

### Post by rybaxs on 2008-12-17
hello jerrynewt,

is Ubuntu 9.04 reads ext4 file system?

---

### Post by starcannon on 2008-12-17
@OP heres a nice walk through for just your situation (not 9.04 but you know, needing to move home to its own partition)

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

enjoy and good luck, and for the love of the holy data, please back up anything you can't live without before you proceed.

---

### Post by mikewhatever on 2008-12-17
Yes, it can be done, pretty much the same way it's done with the live cd. You have to partition manually, then mount the partitions.
That said, Jaunty is still in an early alpha stage and shouldn't be used for anything else but testing.

---

