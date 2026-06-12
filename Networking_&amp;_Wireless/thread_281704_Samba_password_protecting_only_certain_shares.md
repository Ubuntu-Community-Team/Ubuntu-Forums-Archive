---
title: "Samba password protecting only certain shares"
date: 2006-10-21
forum: Networking &amp; Wireless
---

### Post by zgerrz on 2006-10-21
I've tried looking in Samba guides, but I can't find a way to force users to enter a password to view a specific share only. I realize I could make security = user to get a password prompt for every share, but I just want specific shares to require a password, and preferably no username either.

Is there a way to set a particular password for a specific share without requiring every share to have password access? I have security = share but I can't find a way to make this work right.

---

### Post by emersony on 2006-10-21
Z- 

   I take it that you are already aware that you can set that from the Windows side, ie the shares themselves. You can set who can access each folder as well as the windows equivalent of umask. 

Emerson

---

### Post by zgerrz on 2006-10-21
These shares are present on my Ubuntu system.

I am trying to access them using my Windows XP machines.

---

