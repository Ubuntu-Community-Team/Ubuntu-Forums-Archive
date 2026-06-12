---
title: "[SOLVED] Mounting a SAMBA share"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by globex on 2008-08-21
I'm trying to mount a samba share by adding the following line to /etc/fstab:

> 
//myserver   /mnt/myserver   smbfs   auto  0  0


Then when I run "sudo mount -a" I get the following error:

> mount: wrong fs type, bad option, bad superblock on //myserver,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


However, I have no problems with going to smb://myserver...

---

### Post by Iowan on 2008-08-21
SMBFS is being replaced with CIFS. [This]("http://ubuntuforums.org/showthread.php?t=288534") may help.

---

### Post by sea_monkey987 on 2008-08-21
you can only mount //myserver/share

---

### Post by globex on 2008-08-26
Thank you Iowan, that worked.

---

