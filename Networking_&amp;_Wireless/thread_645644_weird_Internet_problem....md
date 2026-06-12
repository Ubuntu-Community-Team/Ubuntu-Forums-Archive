---
title: "weird Internet problem..."
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by stech1 on 2007-12-20
My cable modem lost connection some time during the night. Had to call and the Road Runner people who said their system went down.. they sent a signal  to my modem to get it working again. I have a Ubuntu box and a WinXP box sharing an Internet connection via a Netgear 4 port wireless router. 

Once I knew the cable modem was working, I rebooted the router, rebooted the Ubuntu box, ect. Afterwards, I still had no  Internet connection on either box. So, thinking perhaps the router was the problem, I unplugged it and hooked the cable modem directly to the XP box... presto, Internet connection worked. So, I went to my Ubuntu box, plugged it in directly, rebooted... nothing. 

When I do dmesg, with the cable modem directly connected to the Ubuntu box, it shows that the eth0 connection is up and running. I am kind of mythed... its hard for me to believe that a router and an ethernet connection (onbaord) could go bad at the same time like that. I suppose it could happen. 

Is there some other way I can tell for sure that the ethernet card in the Ubuntu box is working? I mean, I can unplug the modem from the box and dmesg it, and it shows eth0 is down.. which indicates to me that its working... course, I am an idiot, so what do I know? LOL

Thanks for any help!

---

