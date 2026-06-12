---
title: "Problems mounting drives in Ubuntu with smb shares"
date: 2007-07-28
forum: Networking &amp; Wireless
---

### Post by waynepr72 on 2007-07-28
I set up shared drive using Ubuntu function in administration.

This drive is a NFS mounted originally with NFS-3g so I could read and write in Linux to it.


9339: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed.

When using the following, any ideas?

sudo smbmount //192.168.1.100/Video_PC_250MB /studypc -o username=XXXXXX,password=XXXXXX,uid=1000,mask=000

Advised appreciated.

Wayne

---

