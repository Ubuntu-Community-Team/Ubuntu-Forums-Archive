---
title: "Access Samba share only by IP address from Windows; Mac OS access ok by name"
date: 2015-03-08
forum: Networking &amp; Wireless
---

### Post by Pete_Dowty on 2015-03-08
I've been trying to setup a samba share on an old laptop setup as Lubuntu box.  Based on posting I found I changed the name resolve order to be "bcast host lmhosts wins" in smb.conf.  From Windows 8.1 the share does not appear automatically in Windows Explorer.  If I type "\\192.168.1.XX" in the address bar then the share appears listed by IP address (the share name never appears).

I figured I would keep searching posts and trying different things but just yesterday I bought a new iMac running Max OS X Yosemite and was surprised to see the samba share is automatically seen and listed by the share name.

I would appreciate any suggestions to get the share accessible by name from Windows.

---

### Post by bab1 on 2015-03-08
> **Pete_Dowty said:**
> I've been trying to setup a samba share on an old laptop setup as Lubuntu box.  Based on posting I found I changed the name resolve order to be "bcast host lmhosts wins" in smb.conf.  From Windows 8.1 the share does not appear automatically in Windows Explorer.  If I type "\\192.168.1.XX" in the address bar then the share appears listed by IP address (the share name never appears).

I figured I would keep searching posts and trying different things but just yesterday I bought a new iMac running Max OS X Yosemite and was surprised to see the samba share is automatically seen and listed by the share name.

I would appreciate any suggestions to get the share accessible by name from Windows.
This is a Windows problem.  I would try a windows forum for the answer.  I would see if the Windows client has NETBIOS over TCP (NBT) enabled.  Windows considers this "old school", but Samba needs it to be functioning.

---

