---
title: "I have changed from dhcp to inet static and now &quot;couldn't read network/interfaces&quot;"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by dacssvenezia on 2006-10-27
Hi to all,
I have changed from dhcp to inet static and now "couldn't read network/interfaces".
Could it be a permission problem? Who have to be the owner of network interfaces file?
I think i have modified correctly but i can't solve, does anyone have suggestion?
Sorry for my english and thanks to all

---

### Post by mssever on 2006-10-27
Interfaces' permissions:
```
-rw-r--r-- 1 root root 187 2006-10-27 00:49 /etc/network/interfaces
```Of course, the permissions on the parent directories need to be sufficiently permissive, but unless you changed them, I don't see how they could become messed up.

Could you post your interfaces file?

---

