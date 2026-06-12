---
title: "Need help getting wireless internet to activate at startup"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by Ben2r25 on 2007-11-24
When  I first installed Ubuntu 7.10 it recognized I had a wireless card but it wouldn't detect my network (it's a linksys wmp54gs.) I used ndiswrapper to install the driver linksys provides. I entered all the settings for my network (my network uses WPA2) and it connected. When I restarted the computer It did not connect automatically. When I opened up the network manager It had changed the security from WPA2 to WPA. I changed it and it connected. I have saved my settings to a location and all that I need to do is tell the network manager to uses the settings in that location to work now. How can I get it to load the settings from the location I created automatically?

---

### Post by jhetrick62 on 2007-11-24
I had a similar problem although I was not using encryption.  I downloaded wifi radar and it has handled the wireless network connection like a champ since then.

It's in Synaptic for download.  Now they do seem to conflict if there is a wired connection and you attempt to use wireless anyway.  It will allow you to disable the wired, and do the wireless.  But if you attempt to then leave the wireless and go back to the active wired connection, it seems to stall.

That really isn't an issue for me though as I only use wireless when there is no wired connection.  Give that a try. Network manager wasn't working well for me either.

Jeff

---

