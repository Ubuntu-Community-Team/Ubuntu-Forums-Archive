---
title: "(Internet Connection Sharing) Some sites don't work, MSN also"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by stnever on 2007-04-16
Um, I have another networking problem...

I managed to get my connection to the Internet working (through my DSL modem). I have also managed to share it among 2 other computers at home. These other boxes are running WindowsXP, my box is the gateway.

They can connect to several sites without problems. One of them plays WOW, all working. But, a few sites won't load (example: [www.blizzard.com](www.blizzard.com), [www.uol.com.br)](www.uol.com.br)), and none of them can connect to MSN (or LiveMessenger). I can view these sites normally and can connect to aMSN. Been like this for a few days already.

I shared my connection by following the steps on this other tutorial here:
[http://ubuntuforums.org/showthread.php?t=91370&highlight=share+internet+connection](http://ubuntuforums.org/showthread.php?t=91370&highlight=share+internet+connection)

(in a nutshell, I used iptables, dnsmasq, and ipmasq, but I don't really know what I am doing while following the tutorial :D )

Anyone have any ideas why this could happen? Can I inspect iptables's tables somewhere? Can someone confirm this setup (ubuntu gateway, winxp box with msn) working?

TIA!

---

### Post by Austin_KW on 2007-04-16
Could be it be a problem with fragmentation. Check ifconfig, is the mtu different on the 2 interfaces?

---

### Post by Austin_KW on 2007-04-16
I saw one of your other posts, You are sharing your ppp link which has an mtu of 1492, Your windows PCs will be using an MTU of 1500. Somewhere (possibly your connection or the Web sites) the path mtu discovery is not working properly. 

Try setting your windows PCs MTU to 1492.  The easiest way to do this is  to download a program called 'Dr. TCP'

---

### Post by stnever on 2007-04-17
I'll try it later today, thank you! ;)

Would it help if I increased this MTU on the ppp0 interface? I tried:

> sudo ifconfig ppp0 mtu 1500

Tthe guys who own the windows boxes won't be here for at least 8hrs, but just before they left we attempted to connect and failed. I will try using Dr. TCP later. (It's weird because with my old XP's connection sharing, everything worked... I wonder if I need to forward any ports or something like that?)

---

### Post by Austin_KW on 2007-04-17
If it is an MTU problem then the usual workaround is to lower the mtu on the link between the windows and ubuntu pc because windows thinks it has a mtu 1500 link to the web servers.

FYI see [**http://www.netheaven.com/pmtu.htm**l](**http://www.netheaven.com/pmtu.htm**l) or google "path mtu discovery" 
I dont know if you can increase the mtu on the outgoing link, It might be possible (see the last paragrap of above link) but it could reduce the perfromance of your internet connection.

---

