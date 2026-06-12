---
title: "Networking"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by billaboard on 2009-02-09
I have a small network of 2 Vista laptops, one xp laptop (all wireless), a W2k desktop, 2 XP desktops, a Windows Home server, a Vista 64 desktop and an old machine trying Win7. All have had to be converted to NTFS for the server to work properly, All log on with the same username and password.

I've now added this older laptop that I installed with Ubuntu 8,04 some time ago, and have installed SAMBA to some instructions I found here.

I can see the Windows workgroup and see all the individual machines, but can only see the individual shared folders on the W2k machine. What have I missed?

---

### Post by juanoleso on 2009-02-09
One possibility could be firewall settings on the windows xp and vista machines.  Win 2k is the only machine without a firewall.  I'm not sure of specific settings, but it would definitely be something to look at.

---

### Post by billaboard on 2009-02-09
I'm fairly sure it's not a firewall problem at the Windows end. I've disabled the Windows firewall on one XP and one Vista machine, and no difference. I can still just see the machines, but not the shared directories. I thought it might be that the Win 2k machine was FAT32, but just checked and it's NTFS on both partitions like the other machines.
Unfortunately the older laptop that has Ubuntu on has just repeated it's old trick of locking up, so I'll have to wait till it works again or find another machine to try. It would be useful to sort out why I hit this networking problem, as it's the network interaction with Windows that always seems to catch me out (as with BEOS when I tried that).
Thanks for the suggestion, though.

---

