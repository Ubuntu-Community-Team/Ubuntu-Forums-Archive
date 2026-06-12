---
title: "WINE and MAC Address"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by jojarth on 2011-05-02
Hi all,

I'm using 10.10, and just switched over from Windows. I have most of my programs working, except for the remote software my company uses for remote support. I get it to work in WINE, however it is licensed to the MAC address on my laptop, but WINE does not detect that I have any MAC address at all, so I can't finalize the licensing. I know that internet works via WINE (World of Warcraft plays great). 

Does anyone know how I can get a program in WINE to see the MAC Address of my network adapter?

If I have to, I can set one, and just set it the same as my current adapter, but I can't find anything on that either.

I will also email the vendor and see if they have any ideas.

Thanks.

---

### Post by Tony Flury on 2011-05-02
you should get the MAC address via ifconfig - it is labelled as HWADDR.

---

