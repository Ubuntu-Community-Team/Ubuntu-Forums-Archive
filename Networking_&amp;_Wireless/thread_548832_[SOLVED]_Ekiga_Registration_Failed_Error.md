---
title: "[SOLVED] Ekiga Registration Failed Error"
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by digitalbenji on 2007-09-11
Hi,
   I've checked out the other threads on this, the prime one being: 
Ekiga - Registration Failed[http://ubuntuforums.org/showthread.php?t=145047&page=2]("http://ubuntuforums.org/showthread.php?t=145047&page=2") and they did not help me.  I have changed the STUN server in my Ekiga to be one that I can ping, and I have opened up the necessary ports on my router.  I have tried both wired and wireless, but Ekiga keeps timing out when it tries to connect to the Ekiga login server.  Does anyone have any idea how I can get this to work?  I have an Ekiga account that I can log in with.  My router is a WRT54G with the latest firmware.

Help is much appreciated, thanks

---

### Post by digitalbenji on 2007-09-12
watch out for those bumps in the road!

---

### Post by digitalbenji on 2007-09-12
Ok, I tested Ekiga from a seperate router, and it worked.  The issue has to be with my WRT54G or my Cable modem.  

Can anyone advise me on how to configure it to work with Ekiga?

---

### Post by YannickDefais on 2007-09-12
Hi,

In the user guide (link on the right):
[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1149562300349&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1149562300349&pagename=Linksys%2FCommon%2FVisitorWrapper)

page  15 of the PDF you probably can apply "Port triggering":
[http://wiki.ekiga.org/index.php/Ekiga_behind_a_NAT_router#Symmetric_NAT:_Dynamic_navigation_of_NAT_routers](http://wiki.ekiga.org/index.php/Ekiga_behind_a_NAT_router#Symmetric_NAT:_Dynamic_navigation_of_NAT_routers)

Regards,
Yannick

---

### Post by digitalbenji on 2007-10-01
I believe this issue was resolved by applying the latest firmware to my wireless router, a wrt54g.

---

