---
title: "Annoying error with SMBFS/CIFS"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by TyTiger on 2008-11-29
Heres a good one.
I have a NAS Server running FreeNAS with a samba share. I also have a Web server running the typical LAMP Setup and an FTP Server running ubuntu and GproFTPD aswell as my dekstop machine (Ubuntu 8.10)

Currently i have the NAS Share mounted as 'A local drive' so variouse applications can read from the NAS as if it were a local disk and function the same way. 

My only problem is when copying a directory over to the NAS, i get an error saying Access denied, yet i can copy indavidual files and create Directories manually and copy/make files in to them. 

Why is this happening and what have i done wrong? is it fixable. im mostly concerned because the FTP Server will be used by clients wanting to upload files and folders to their web spaces but this presents a problem as it will return errors on occasions and i have seen this happen and believe it to be the same problem. 

In the fstab i have the following line: 
```
//192.168.1.250/disk1	/media/disk1	cifs	guest,uid=1000,iocharset=utf8,codepage=unicode,unicode	0	0
```

Is there something i should know? please feel to ask any further questions in the hope to find a solution. :KS

---

### Post by TyTiger on 2008-11-29
Bump

---

### Post by TyTiger on 2008-11-29
Anyone? :confused:

---

### Post by TyTiger on 2008-12-03
So, either nobody knows or nobody cares..

---

### Post by roblubbers on 2009-05-23
I have the same error with a Philips 8020 cc NAS. If had it since i upgraded to jaunty

---

### Post by roblubbers on 2009-05-27
For me adding 'nodfs' as a mount option solved it.

---

