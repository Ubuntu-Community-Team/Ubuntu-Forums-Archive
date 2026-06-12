---
title: "FreeNAS"
date: 2014-07-01
forum: Networking &amp; Wireless
---

### Post by mayagrafix on 2014-07-01
Back in Windows Xp days when you hooked up to Internet the setup wizard gave you the option of channeling the internet thru one computer so that this computer would be able to distribute the signal to all other computers in your home network.

Is this the same as what a FreeNAS box does today?

---

### Post by tgalati4 on 2014-07-01
No.  [freenas]("http://www.freenas.org") (two flavors--old is [http://www.nas4free.org](http://www.nas4free.org)) is a BSD unix distribution that performs as a file server--network attached storage (NAS).  You can add packages to it to perform other things such as serving media (uPnP/DNLA), and running simple web servers.

What you are thinking of is "internet sharing" or a machine acting as a router or gateway that filters the packets before they get to the rest of your local network.

---

