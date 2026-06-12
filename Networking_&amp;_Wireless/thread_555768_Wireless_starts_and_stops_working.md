---
title: "Wireless starts and stops working"
date: 2007-09-19
forum: Networking &amp; Wireless
---

### Post by BinaryBrother on 2007-09-19
I'm using a USB Belkin, I also am having these odd connection problems... Although if I give mine time, network activity will eventually fix itself... I can be watching a streaming movie or viewing a page and my network activity will just drop to 0% and apparently hang for several mins... Then after anywhere from a min to 5, it picks back up perfectly... I don't use encryption on my network, only MAC blocking for those who like to steal... Which on average is once a year. Using Ubuntu Feisty all latest updates and such... Please address this issue if you can help! Thanks ahead of time... BinaryBrother

---

### Post by BinaryBrother on 2007-09-20
I am using a wireless Belkin via USB, to connect to a Linksys wireless router. Ubuntu Feisty. Wireless works for random intervals, and then completely stops for intervals of 1 to 5 mins, the connectivity then picks right back up, except for my torrent client, which has to be restarted. This problem is not caused by my torrent client, as it happens with or without the client executed. I am NOT using ndiswrapper because Ubuntu was pretty friendly with my Belkin. Picked it right up, and connected to my router, My MAC is listed on the router as a user. As it is during outages. I replied to an old thread saying I needed help, and no-one has replied in 2 days. So I apologize for re-opening a new one. Apparently I'm not the only one having this problem. There seems to be no concrete answer in these forums yet, hopefully we can get this problem fixed. I tried to be direct, and informational. If anymore information is required, simply ask. :)

---

### Post by BinaryBrother on 2007-09-21
I was hoping that you guys could actually help??

---

### Post by amgat on 2007-09-21
You need to tell us more about your hardware.
What model is it?

Type "sudo lsusb" from shell and post the results here.

---

### Post by BinaryBrother on 2007-09-21
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 050d:0050 Belkin Components 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 04d9:0499 Holtek Semiconductor, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 05fe:1010 Chic Technology Corp. 
Bus 001 Device 001: ID 0000:0000

I apologize deeply... :( My router was throwing a fit, my cousin on his Windows machine couldn't even connect to it... I power cycled, and it was still fried... I done a hard reset, and it seemed to have fixed it so far... :lolflag:

---

### Post by amgat on 2007-09-21
What kind of router you got? Some routers can't handle the load when using bit torrent technology.

---

### Post by BinaryBrother on 2007-09-21
It is a Linksys, but it handles .Torrents perfectly on a windows machine, and has for quite sometime now... :P

---

### Post by amgat on 2007-09-21
I have a linksys wrt54gs myself. The router "collects" active connections without flushing them for hours. When downloading very active torrents, the routers memory is filled up and causing the router to crash (and burn!).
I also had strange disconnection and hang problems in generally.  I installed a custom linux based firmware and never had these problems again. 
What linksys model you got?

---

