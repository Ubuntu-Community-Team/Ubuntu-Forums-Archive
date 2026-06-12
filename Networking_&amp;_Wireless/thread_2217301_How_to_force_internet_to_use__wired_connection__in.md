---
title: "How to force internet to use  wired connection  in Lubuntu?"
date: 2014-04-16
forum: Networking &amp; Wireless
---

### Post by Andy3142 on 2014-04-16
The internet on my Samsung N220 Lubuntu netbook works fine in the  office. At home it works kind-of, but  the internet hangs up every  couple of minutes, then works again when I disconnect/reconnect the  wireless connection. The obvious  fix would be to try using the wired  connection. 

This does work in that I can log into the router  control panel via the wired connection. However I do not seem to be able  to use the internet over the ethernet cable. If I "enable networking"  but "disable wireless" in the little pop-up on the desktop, the internet  stops working.

I'm  a complete Linux newcomer and no idea what diagnostics to post. Desktop > Preferences > Network connections shows 
"Wired network one" = eth0 perfectly good, with "connect automatically" checked. To repeat, I can connect to the router control panel OK.

I would prefer if I could get the internet working over the cable by use of this or other GUI widget, but it would be a huge relief to get it working any way at all. It must be nearly OK ... just that last step.

Alternatively,  any tips on how to stop the internet hanging up on the wireless  connection  would also do the job, however, to me this looks  trickier to fix than just geting the cable connection working.

Many thanks

Andy

---

### Post by praseodym on 2014-04-16
Hi,

check if there's a MAC-address filter active in your router. How do you add your Login/PW of your provider? Is it in your router interface? Try to delete any connection in "cable" and "DSL" of the network-manager and reboot your system.

For wireless: Set the encryption mode to pure WPA2-AES (CCMP) at home and a fixed channel.

---

### Post by Andy3142 on 2014-04-17
Thanks for your reply, it's solved, the keyword is "reboot" and what that means. What I find is that if I power down completely and start again, then the cable connection is used and the wireless connection is not started. If however I am using the wireless, plug the cable in and do "restart" then the wireless is still preferred and the cable is not used. This is different from my experience with PCs, where I am pretty sure that a restart is identical to power down and start again. 

Andrew

---

