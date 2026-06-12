---
title: "'net usershare' returned error 255:"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by wawadave on 2008-10-24
'net usershare' returned error 255: net usershare add: cannot share path /media/disk/blues as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this.

am trying to share this folder i recently formatted the drive ntfs from fat32 because it would not let add certain files file name problem. now i can add them but cannot share.
any ideas would be helpful!

---

