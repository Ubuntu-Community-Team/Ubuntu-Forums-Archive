---
title: "Share Windows Internet with Ubuntu"
date: 2008-09-06
forum: Networking &amp; Wireless
---

### Post by wubifun on 2008-09-06
Hi
I have a Windows laptop (connected to the internet via wireless), which is also connected to my Ubuntu (8.10) laptop via Crossover cable. Does anyone know how I could share the internet between them (with the Windows laptop acting as the server)?

---

### Post by spd106 on 2008-09-06
A popular solution is to use [Firestarter]("https://help.ubuntu.com/community/Firestarter") to configure the connection sharing.

You may also be interested looking for ufw tutorials on the web or elsewhere in this forum.

---

### Post by pytheas22 on 2008-09-06
If you want to use Windows as the server/router, enable Internet Connection Sharing on the Windows machine (there are lots of tutorials available via Google).  You'll have to bridge the wireless and cable connections.

Firestarter can only be used if you're trying to use Ubuntu as the router, I think.

---

