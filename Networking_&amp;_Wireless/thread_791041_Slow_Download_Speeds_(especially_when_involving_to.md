---
title: "Slow Download Speeds (especially when involving torrents)."
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by Bridger987 on 2008-05-11
Hello all,

I have (finally) successfully gotten my network cart to work (almost) consistantly, with the advent of Ubuntu 8.04.  Woot!  I, finally, am using Ubuntu as the OS on my main computer.

But, of course, there are still snags.  

Download speeds on Ubuntu, although not as incredibly slow as they were for me with Ubuntu 7.10, are still slower than their Windows counterparts.  I'm not complaining, mind you.  They're more than acceptable.  But nowhere is this difference in speed felt more than when downloading files via .Torrent trackers.

I realize that when downloading using a BitTorrent-like client, download speeds are normally slightly slower than with other forms of downloads.  But the highest speeds I've been able to get, consistently with many different files from different locations, has been around 2.0 kbps.  I'm wondering if there is anything, an obscure setting perhaps, that could be causing this to happen.

Also, after I finally close Azureus/Transmission/Miro having been unsuccessful, my internet speeds remain just as slow in other programs (Firefox) as they were in the BitTorrent-like client, even though speeds in Firefox are normally perfectly acceptable.

Oh, and one more thing:  My ISP does -not- have a history of screwing with P2P traffic.  :-)

Thanks!

---

### Post by |{urse on 2008-05-11
> a BitTorrent-like client

Not that it would solve your problem to use a different client but it would help me to assist if i knew exactly which one. Also are you able to login to  your router? And what model is your router?

---

### Post by Bridger987 on 2008-05-11
To quote myself:

> **Bridger987 said:**
> Also, after I finally close Azureus/Transmission/Miro having been unsuccessful . . .

:lolflag:

I have tried all of those that are listed above (Azureus, Transmission, and Miro) with no luck.  Although, if I would have to choose only one to work with, it would be Azureus.

---

### Post by |{urse on 2008-05-11
azureus, okay. and what model of router do you have?

I'd need to know in order to help you set up port-forwarding.

Tell you what, when you find you router model here

[http://portforward.com/routers.htm](http://portforward.com/routers.htm)

follow the instructions to forward the proper ports that torrents primarily use. If you have trouble viewing your router's admin page via firefox try installing firefox's java plugin.

sudo apt-get install sun-java6-plugin

this is necessary for some of the newer linksys routers.

generally to login to your router open firefox and specify your local ip like this

[http://192.168.1.1](http://192.168.1.1)

in the address bar.

---

### Post by |{urse on 2008-05-15
s'been a few days lol did this help you or not?

---

