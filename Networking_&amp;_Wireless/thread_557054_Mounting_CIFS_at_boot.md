---
title: "Mounting CIFS at boot"
date: 2007-09-22
forum: Networking &amp; Wireless
---

### Post by can2002 on 2007-09-22
Hi,

I've had a problem with both Edgy & Feisty where CIFS shares I'm trying to mount via fstab won't automatically mount at boot time.  An example entry in my fstab file is below:

//192.168.1.1/guest  /mnt/guest  cifs  guest,file_mode=0777,dir_mode=0777 0 0

The odd thing is that if I execute 'mount -a -t cifs' once the host has booted, all the CIFS entries mount fine.

I'm probably being stupid, but any pointers would be appreciated!!

Cheers,
Chris

---

