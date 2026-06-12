---
title: "Wireless Card after re-boot"
date: 2006-10-16
forum: Networking &amp; Wireless
---

### Post by scottsanpedro on 2006-10-16
Hi,
I have managed to get my belkin pre-n card running on my laptop now. 
When I re-boot I find that two other connections also become 'Active' after me de-activating them. The wireless connection will not kick in until they are disabled.

Also the default gateway disappears from the ative wireless settings.  

Any help would be gratefully accepted :)

Many thanks  Scottsanpedro

---

### Post by Dr. Nick on 2006-10-16
If you have to deactivate connections before your wireless will work you may just need to disable them. 

If you are in gnome then open the network dialog and click the 2 connections you deactivate, their should be a check box with "enable this connection" that you can uncheck.

Also look at the file /etc/network/interfaces and you may be able to set the gateway and what card gets used first, I know with my wireless I always had to disable the ethernet

---

