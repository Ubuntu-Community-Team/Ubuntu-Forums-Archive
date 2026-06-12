---
title: "Connecting through D-Link wireless extender"
date: 2006-12-26
forum: Networking &amp; Wireless
---

### Post by thistransition on 2006-12-26
I just bought a D-Link DWL-g710 wireless extender and am trying to connect to a D-Link DI-624 router.  My router is in my basement and I have the extender connected with an ethernet cable to my Ubuntu PC upstairs.

When plugged in, all of the lights on the DWL-g710 extender seem to be working fine.  The power button remains green, the LAN light is solid green, and the WLAN is blinking green (signaling data transfer).  Since there is an ethernet cable from the extender to the PC, I do not have a wireless card installed.

Is there some type of installation required?
New drivers?

I was fooling around with some of the settings in Firefox but nothing seemed to make a difference.  Are there any important settings in Firefox for a wireless connection?
The installation CD it came with does not run since the AUTORUN is a .exe.

For some reason, WINE does not work. It says it is installed in the Add/Remove programs but I cannot use it.

Any ideas?
Any help would be appreciated! Thanks!

---

### Post by ButteBlues on 2006-12-26
Go to the default IP of your router and do a little configuration. That's what I had to do. :)

---

### Post by thistransition on 2006-12-26
hm i'll try that.. i tried to go to the default ip of the extender but it didn't recognize it.
what if i can't connect to the router? i should have another post up tomorrow afternoon.

---

### Post by ButteBlues on 2006-12-26
I'm not terribly sure if you can't fix it on the router end.

I got a wireless router for Christmas (Linksys) and I know that even the ethernet didn't work until I played around in the router's settings. I think I just changed a few minor things and it worked...

IIRC, I changed my local ip from 192.168.1.1 to 192.168.2.1... which got ethernet working. To get wireless up, I think I just used the same configuration editor to change the SSID and add a WEP key.

After that, a simple restart of the computer or reloading of network devices ( I think the command is "sudo /etc/init.d/networking restart") and the Internet should be up. :)

If not, direct a call to Customer Service - I dunno about D-Link's stuff, but the Linksys stuff comes with free telephone customer service in US and Canada.

---

