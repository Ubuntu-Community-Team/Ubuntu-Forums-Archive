---
title: "Problem with sharing over home network"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by cika.mancic on 2008-06-26
I had install Samba, and tried to share some folders on my mashine. It worked fine with folders in my Filesystem partition, but with my NTFS partition it gone mad. it says "'net usershare' returned error 255: net usershare add: cannot share path /media/disk/Novo/Batina/Pozadine as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this."
Is there a way to share anything from my NTFS partition?
Sorry for my English, and thanks!

---

### Post by cika.mancic on 2008-06-26
Add:
I tried to do what the warning told me. I add the line "usershare owner only = False" in smb.conf, and nothing happend...
What now?

---

### Post by superprash2003 on 2008-06-26
are you able to write normally to the ntfs drive? do you have ntfs-3g drivers installed? please post your smb.conf file here

---

