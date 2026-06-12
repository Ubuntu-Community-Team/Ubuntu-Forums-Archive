---
title: "NFS mount other drives"
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by JohnnyH on 2007-07-19
I have the NFS setup, it works fine, i can copy, delete, however, i just cannot access other drives in the server computer except the Filesystem drive.

the other drive is /dev/sdb on my ubuntu(server), but if i access from my mac(client), sdb is not even in /dev.

Anyone know why?

---

### Post by netztier on 2007-07-19
> **JohnnyH said:**
> I have the NFS setup, it works fine, i can copy, delete, however, i just cannot access other drives in the server computer except the Filesystem drive.

the other drive is /dev/sdb on my ubuntu(server), but if i access from my mac(client), sdb is not even in /dev.

Anyone know why?

On the server, has /dev/sdb been partitioned (fdisk, cfdisk), has it been formatted (mkfs) and been mounted on the server (/etc/fstab) ?

And if yes, did you then export that drive/filesystem via **/etc/exports**? 

That's what it takes before being able to mount it remotely via NFS.

best regards

Marc

---

