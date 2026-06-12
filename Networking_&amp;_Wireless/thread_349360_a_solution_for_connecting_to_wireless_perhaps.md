---
title: "a solution for connecting to wireless perhaps?"
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by blackdalek on 2007-01-30
I have one linux machine which has always been a pain in the arse to keep connected to my network due to the flaky support for WPAPSK wireless for network cards I have tried (RT61 and RT2500 chipsets).. True, I can get these cards to work occasionally if I put the effort into it, but the end result is always very touch and go, and connections can never be sustained indefinitely - the network adapters consistently need to be restarted/reinitialised/whatever you want to call it.
Now, connecting to the network through ethernet has never been a problem for any of my linux boxes, and indeed this is how most mine are connected. But this one machine is in a room in the building next door, so I cannot physically lay cable across to it. There is a wireless range extender which gives network access to the machines next door, and that is working very well, except for the one linux machine.
Now I was thinking about this problem, and it occurred to me that I could solve the whole problem by avoiding wireless network adapters in llnux altogther, and using an ethernet-wireless bridge. That way I can just let the bridge connect to the wireless network and plug the linux box's ethernet cable into the bridge. Problem solved. I hope.
I'm thinking about using this - [http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1134692497433&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1134692497433&pagename=Linksys%2FCommon%2FVisitorWrapper)
From the online documentation it seems to be OS independent, so I don't see why this would not work.
Does anybody anticipate any problems which might occur with using this device - keeping in mind that I want to use WPAPSK and I am assuming the linux box will connect to the bridge and the bridge to the range extender and the extender to the main network ADSL gateway/router.

---

### Post by spd106 on 2007-01-30
No, there shouldn't be any problems. Most Wireless Access Points can be configured into bridging mode.

---

### Post by tturrisi on 2007-01-30
It would be easier & cheaper to just use a wlan adapter that has better support for WPA-PSK in linux, such as an atheros, acx, intel or prism chipset adapter, rather than an adapter w/ a Ralink chipset.

---

### Post by blackdalek on 2007-02-03
> **tturrisi said:**
> It would be easier & cheaper to just use a wlan adapter that has better support for WPA-PSK in linux, such as an atheros, acx, intel or prism chipset adapter, rather than an adapter w/ a Ralink chipset.

Maybe so, but I have found it neither cheaper nor easier to procure a PCI wireless adapter with one of the preferred chipsets. 99% of all PCI wireless adapters available in australia seem to be either ralink RT61, RT2500 or similar. The other chipsets you mention I have only encountered in laptop adapters. :(


edit: yes, 99% is a number I just pulled out of the air, cos I liked the sound of it :)

---

