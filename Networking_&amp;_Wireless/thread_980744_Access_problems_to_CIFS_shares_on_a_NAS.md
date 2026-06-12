---
title: "Access problems to CIFS shares on a NAS"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by fcigoi on 2008-11-13
Hi all,

I have installed a NAS on my network, created the shares on it and tried to mount them on my machine via network using a SMB.
The first time all went well and I managed to copy files to the shared drive, but after a reboot the owner of the shares on the NAS turned into a number and I am unable to read/write to them any further.
I think it's a matter of setting access privileges correctly but I have tried various things without being able to change back the owner of the shares back to whatever they were in the beginning.
Any ideas ?

---

### Post by fcigoi on 2008-11-13
Sorted by deleting and re-creating the local dirs within /media, and adding "nounix" to the mounting options within fstab. 
I probably changed the access rights on the old ones inadvertently

---

