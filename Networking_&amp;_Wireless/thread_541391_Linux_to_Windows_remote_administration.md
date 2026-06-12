---
title: "Linux to Windows remote administration"
date: 2007-09-02
forum: Networking &amp; Wireless
---

### Post by FRuMMaGe on 2007-09-02
I have a local area network at my house and everyone else uses Windows.  Is there a good Linux to Windows remote administration application that would allow me to set up the other computers from my Linux workstation?

---

### Post by darkwyrm on 2007-09-04
It depends on how you want to do it. UltraVNC is probably the easiest if you have the network bandwidth. Alternatively, it's not all that tough to set up an ssh server on it with Cygwin. If you want to really overengineer things, I *think* you could set up your Linux box as a Domain server with Samba, but that's a _lot_ of work.

---

