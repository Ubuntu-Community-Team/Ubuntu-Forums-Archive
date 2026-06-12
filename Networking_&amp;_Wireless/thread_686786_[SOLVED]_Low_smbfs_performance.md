---
title: "[SOLVED] Low smbfs performance"
date: 2008-02-03
forum: Networking &amp; Wireless
---

### Post by mdw on 2008-02-03
I have an 6.06 server on old hardware that I use as a fileserver (using Samba). Windows XP on my PC reach about 2.5 MB/sec writing to this while Linux on the same hardware only does about 1.5 MB/sec through smbfs. This is also clearly apparent on a MRTG graph of server's LAN connection. My PC's Linux is Feisty, running on AMD 4200+ with 3 GB RAM, fairly out of the box configuration. Server is PII 333 MHz and 192 MB RAM. Network is gigabit ethernet on the PC side, fast ethernet on the server side.
   What might be the problem here?

-mdw

---

### Post by weaverryan on 2008-02-03
Once upon a time I had a few network drives mounted via smbfs. After a sys update, the performance went down hard, much worse than you're reporting.

My solution was to change my mount to cifs. This really sped things up, and I've been rocking ever since.

I think I have an article on how to mount via cifs. Shout if you need it.

---

### Post by mdw on 2008-02-04
I switched to CIFS and indeed, the performance is now on par with Windows, maybe even slightly better.

Thanks for help.

-mdw

---

