---
title: "Lost LAN access (server ed)"
date: 2008-04-16
forum: Networking &amp; Wireless
---

### Post by gnarf on 2008-04-16
Hi first off I'm a complete noob on linux.

My problem is that I'm trying to run my file server with a lan accessible interface, but also have a FTP interface (not necessarily in the same dir). I get everything setup ok (using LAMP) and the first time or two everything runs fine. I can LAN network between my windows box, setup a network drive (via samba) that all works, ok then I go to setup FTP and when I access anything using my web IP (which I configured my router to pass on to my linux box) I no longer can access anything via my LAN IPs and I lose my network access to my server. I can't SSH into the server unless I use my web IP whereas before it was my local IP currently I'm still logged in from my local IP through SSH, but when I try to duplicate my session I get a network error, so I have to login via the web IP. I would think that it'd be possible to have both, and why only after I type my web IP into a browser does it no longer allow me LAN access? 

remember, noob, talk in small words :)

---

### Post by Iowan on 2008-04-17
"...my web IP"? Is that the external address? I wonder (means I'm guessing) if the address got changed?  IIRC, it should be difficult to access the (internal) machine using the external address.

---

