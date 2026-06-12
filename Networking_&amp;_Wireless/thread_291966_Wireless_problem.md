---
title: "Wireless problem"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by Newbiejohn on 2006-11-03
Okay, I'm running Ubuntu 6.06 on a desktop PC and I'd like to be able to connect to my wireless router (B). I have no problems connecting to it from my iMac (OS X) with Airport. I have two different adapters I can use, but I can't seem to get either of them to work. First I have a Belkin USB wireless adapter (B). When it is connected to the computer, it shows up in the Networking window, but if I enable it, I can't connect to my network and the light on it stays red (supposed to be green when it's "live"). The other one I have is a Linksys WET11 adapter (plugs into the ethernet port). I also can't connect thru it, tho the connection light is on on the adapter. I set it for DHCP. Any ideas what I'm doing wrong? I should think that at least one of these would work. I'm guessing there is something simple I'm missing, but I have no idea what to try.

---

### Post by jimbren on 2006-11-03
If you've got encryption or MAC authentication turned on at the router, turn them off so you can troubleshoot the connection.  With everything opened up on the router, you should be able to connect with no problem.  Then you can proceed from there--turn on MAC authentication and see if it works.  Then turn your WEP back on and see if it works.

jimbo.

---

### Post by Newbiejohn on 2006-11-03
I am not running any encryption or authentication on my router. I live out in the sticks, and my closest neighbor is over a 1/4 mile way, so I don't see any need. I guess I was spoiled by the fact that my Thinkpad worked right away with it's wireless card, so I just figured that the desktop would too. I did check the setting for the wireless card, and checked to make sure the Belkin adapter showed the same (using DHCP).

---

### Post by Newbiejohn on 2006-11-04
> **Newbiejohn said:**
> I am not running any encryption or authentication on my router. I live out in the sticks, and my closest neighbor is over a 1/4 mile way, so I don't see any need. I guess I was spoiled by the fact that my Thinkpad worked right away with it's wireless card, so I just figured that the desktop would too. I did check the setting for the wireless card, and checked to make sure the Belkin adapter showed the same (using DHCP).

Well, I've given up on the Belkin USB adapter. I cn't get a connection with it, and everytime the computer comes out of the screensaver my mouse is frozen for some reason. And no, my mouse is not USB. With the Linksys bridge, I seem to be getting a link between the computer and the bridge (the LAN led on the bridge is lit and flickers occasionally), but I don't seem to be getting any connection wirelessly between the Linksys and my connection point. The WLAN led never lights, and when I try to connect to the web, it just says "looking up ***.com" and stalls. At first I thought maybe it was a DNS server problem, so I added several DNS servers for the eth0 interface, but no good. So I finally decided that bridge isn't talking to the access point. Do I need to install Network Manager to help me get this working? I did use this bridge with the iMac before I put the Airport card in it and it worked okay then, but that's been a while ago. Maybe I should just look for a PCI wireless B card that works with Ubuntu................

---

