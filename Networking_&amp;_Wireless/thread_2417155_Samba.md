---
title: "Samba"
date: 2019-04-21
forum: Networking &amp; Wireless
---

### Post by esegege on 2019-04-21
I finally installs and configure samba to share folders with Windows 10. Its working ok but I found that Samba really dosent shares the folders, it maskes a copy of the folthers om both computers. Please explain me this

TKS

---

### Post by TheFu on 2019-04-21
> **esegege said:**
> I finally installs and configure samba to share folders with Windows 10. Its working ok but I found that Samba really dosent shares the folders, it maskes a copy of the folthers om both computers. Please explain me this

TKS

You've lost me.  I haven't seen the behavior you are describing or might be misunderstanding the meaning.

Samba does share directories. Changes made by 1 client are seen directly on the server and by other clients which have access to that specific share. 

Please share the output from **testparm** run on the samba server.

---

