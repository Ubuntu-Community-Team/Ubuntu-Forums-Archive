---
title: "Network configuration help"
date: 2008-10-29
forum: Networking &amp; Wireless
---

### Post by eppo on 2008-10-29
I was just wondering, right now i have my ubuntu server setup with 2 network cards. one attached to my cablemodem, and 1 attached to my home network. would i be better off to get a WRT54G and run openwrt on that, and put it in between my cablemodem and my home network? that way i would just set the router to forward to my ubuntu servers ssh port, so that would be the only port open. right now i have vmware server's web utility open on my cablemodems side, 2 ports are open for mythtv, but i have those stealthed.
should i just leave it like it is, or would having openwrt between the internet and my network be much safer?
thanks

---

### Post by SpaceTeddy on 2008-10-29
safe is a matter of perspective here. If you do take the openwrt solution, there will be a busybox running on the little router - and guess what that is - right, a Linux as well. 

Anyways, the advantage i see with the openwrt solution is that you can have more than one comp in your network to use the internet at the same time. Also, if you map a hostname, there is no funny business of mapping the name right internal and external (the openwrt box gets the name, and internal clients usually don't get forwarded).
        
The disadvantage is that you have to spend money, de-brick it, spend time figuring it out, and sometimes it does not work right. Also, it is one more piece of hardware that sucks power and can give you headaches.

Ok, back to the security issue :)
from my point of view - it doesn't make a lot of difference. In both cases, you need to configure iptables properly to get the security right... if you do that on the openwrt or the Ubuntu box itself does not really matter. And just because you have another firewall does not automatically mean it gets any safer...

my two cents...

---

### Post by eppo on 2008-10-30
thats kinda what i figured, i've wanted to play with openwrt, and was just thinking about doing something like that. maybe if i pick up some type of wireless device and need a wireless router i might try it out.

---

