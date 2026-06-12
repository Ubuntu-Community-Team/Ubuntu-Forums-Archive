---
title: "not resolving domains."
date: 2008-08-16
forum: Networking &amp; Wireless
---

### Post by wparsons on 2008-08-16
I discovered a recent issue with my testing server this morning.  Something is failing, and not allowing me to ping via URL.

The weird thing is that I can 'dig' a url just fine.

Its also kind of weird, since I can access the server via the domain pointing to my network just fine as well.  Its just an outgoing problem on the server only.

The only thing I've done recently was install winbind since I was having trouble mounting smb shares via computer name.

Its one of 4 machines on the LAN, everything is peachy with the rest.

/etc/hots appears fine to me, and resolve.conf has the DNS server for my ISP(which has been there all along), as well as the IP of my router(also been there all along)

Any suggestions on where to look?

---

