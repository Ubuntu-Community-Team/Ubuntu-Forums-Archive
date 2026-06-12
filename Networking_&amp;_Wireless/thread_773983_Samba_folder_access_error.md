---
title: "Samba folder access error"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by Battalion on 2008-04-29
Hi there,

I'm using Ubuntu 7.04 with samba installed.  I run a network to connect my pc (ubuntu) with my laptop(windows xp).  I can access everything on the laptop with no problems.

On the pc, the shares on my ntfs drive (running ntfs-3g) are fully accessible but the shares on my fat32 drive are not.   

Please help me figure out how to allow access to these files on fat32.  My security level is set to "user" and samba returns an error when trying to access them

---

### Post by s13884 on 2008-04-29
Hi,

Could you just pest the output of the smbtree command over here? 

smbtree: you can find the list of whole share.

Cheers

---

