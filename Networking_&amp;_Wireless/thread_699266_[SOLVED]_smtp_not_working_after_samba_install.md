---
title: "[SOLVED] smtp not working after samba install"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by SneakPeak on 2008-02-17
Hi,

My ISP requires that I send all outgoing mail through their smtp.  The smtp in question is smtp.vodacom.co.za.  I had everything setup and running correctly.  I then installed samba and firestarter to get internet connection sharing going with a Vista box.  My internet connection sharing is now working but my machine now doesn't see the smtp at all.  Even ping-ing it doesn't work.  I have tried stopping the firewall but that doesn't help.

Any ideas?

Thanks

SneakPeak

---

### Post by SneakPeak on 2008-02-17
Hi 

I got this problem solved.

I went to:

[http://www.hcidata.info/host2ip.cgi](http://www.hcidata.info/host2ip.cgi)

I typed in smtp.vodacom.co.za and it told me the ip was: 196.11.146.148.

I replaced smtp.vodacom.co.za with 196.11.146.148 in all my mail programs and everything is working.

This gives me an idea that my DNS is faulty????  Internet is working well so it is a bit strange.  Any ideas?

:)

---

