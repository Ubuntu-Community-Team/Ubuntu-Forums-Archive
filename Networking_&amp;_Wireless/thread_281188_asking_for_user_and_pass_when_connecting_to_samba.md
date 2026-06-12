---
title: "asking for user and pass when connecting to samba"
date: 2006-10-20
forum: Networking &amp; Wireless
---

### Post by invictus on 2006-10-20
Hi

When I share a folder by rightclicking and selecting "share" (also setting browsable and read only) and try to access it from a windows client later I get asked for username / password (typing "guest" as user doesnt work). This wasnt the case a few days ago. It just happend and now I cant access it. How can I disable the user/pass dialog when connecting? I also tried using my useraccount login as user/pass, but it didnt work either. I want to be able to share to everyone without password.

Thanks.

---

### Post by invictus on 2006-10-20
I got a tip elsewhere to switch "security = user" to "security = share" in smb.conf and it worked. However I have no idea how it went from share to user in the first place.

Case closed :-D

---

