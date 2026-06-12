---
title: "accents in samba mount"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by guillemsola on 2007-08-06
Hi!

I have a cheap NAS disk conceptronic CHD3LAN. It works with samba. I can mount it per example in fstab with

> //192.168.1.3/PUBLIC /mnt/NAS smbfs auto,username=guille,password=guille,uid=1000,umask=000 0 0

It works well, but there is a problem with accents., they appear as ?. I live in Spain and we use lot of accents.

I try with

> //192.168.1.3/PUBLIC /mnt/NAS smbfs auto,username=guillem,password=guillem,uid=1000,umask=000,iocharset=iso8859-1,codepage=cp850 0 0

and also with iocharset=utf8 and many other possibilities but accents never appear

My locale is set to ca_ES@UTF8 and I tried also to change it to ca_ES@iso8859-1 but they never appear in a correct way.

The question is that if I do the mount with nautilus browsing lan with smb://192.168.1.3/PUBLIC accents appear fine.

Does anybody knows how to solve this, cause in some machines I doesn't use X and I need it to work with mount command. Note: cifs seems not to work with this NAS box.

Why if I browse Nas box trough Nautilus-Lan explore I can see accents fine but not trough mount?

Thanks in advance
Guillem Solà

---

### Post by dmizer on 2007-08-07
i had the same problem a while back.  use cifs instead of smbfs.  it handles utf8 better.

the second link in my sig will take you to the howto i wrote for that.

---

### Post by guillemsola on 2007-08-09
HI, Nice how-to! But after follow steps on your guide I try with

> sudo mount -t cifs //STORAGE-217F/PUBLIC /mnt/cifs/ -o guest,iocharset=utf8

without succes. It takes a wail to say

mount error 111 = Connection refused

on dmseg
> 
 2742.153002]  CIFS VFS: Error connecting to IPv4 socket. Aborting operation
[ 2742.153012]  CIFS VFS: cifs_mount failed w/return code = -111


I'm sure that this is my netbios name.

The question is, where I can use samba mount, can I use cifs too? I cannot find much information about cifs.

Thanks!

---

### Post by dmizer on 2007-08-18
sounds like an error resulting from a firewall on the client or server.

if so, you'll need to make sure that ports 445 and 139 are open to internal traffic.

you can use smbfs in the same place as cifs, but smbfs is not maintained and full of problems (for example ... no network file transfers larger than 2 gig).  smbfs is also slower, and much less friendly to multiple languages.

---

