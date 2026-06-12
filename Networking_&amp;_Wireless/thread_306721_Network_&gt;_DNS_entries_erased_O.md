---
title: "Network &gt; DNS entries erased :O"
date: 2006-11-25
forum: Networking &amp; Wireless
---

### Post by Coburn on 2006-11-25
When I configure Network > DNS to reflect the IP addresses my Netscape provider is currently using, then for some reason _restart_ Network Manager, it shows only the first IP I entered. :shock:  

The others I laboriously entered have :eek: vanished!

Question A:  What is causing this?:confused: 

Question B:  Is there a config file I can enter the IP addresses in that will not succumb to the Eraser-wielding Gremlin?8) 

Thanks

---

### Post by stream303 on 2006-11-25
I run into this problem a lot.

Perhaps something in here might help:

[http://www.ubuntuforums.org/showthread.php?t=305275](http://www.ubuntuforums.org/showthread.php?t=305275)

---

### Post by Coburn on 2006-11-30
I think I figured out what is going on.

/etc/resolv.conf is being rewritten every time.  Maybe that is because I enabled "use IP nameservers" in network-admin.

Anyway, it is not a problem for me.  I haven't found anything yet that doesn't work because of it.

I am able to give permissions to my ISP and my network client in other places, e.g. firestarter.

I noticed it works better to enter isp.netscape.com in the firestarter rules than the IP address.

---

