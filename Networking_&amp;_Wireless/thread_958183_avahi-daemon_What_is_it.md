---
title: "avahi-daemon? What is it?"
date: 2008-10-25
forum: Networking &amp; Wireless
---

### Post by extruct on 2008-10-25
Hey, I noticed in Services that avahi-daemon is running. I googled it and I understood that its some sort of auto discovery of new devices on LAN.
I wonder if I need it, can I safely disable it?
I got wired home network with 2 PC's.

Thanks.

[UPDATE]
Seems like this dam avahi blocks my internet. Around 2 weeks ago my internet started to disconnect suddenly and couldn't even login to my router's ip (10.0.0.138), internet got totally blocked!
May it be avahi? After internet dies I run ifconfig and got: eth0 eth0-avahi and lo

Help please!

---

### Post by shandiddy on 2008-12-08
I have had this exact same problem for a while now.  My internet works perfectly until my computer has that "avahi:eth0" address.  My other PC's work perfectly fine, during that time so I know it's not the router or the modem.

Post any possibly solutions

thanks

---

### Post by Iowan on 2008-12-08
Avahi is *supposed* to be zero configuration networking. Unless you specifically use it, avahi generally indicates a problem somewhere - like DHCP failing to provide an address. Avahi will provide an address (169.254.X.X), but since this is probably not in the "normal" subnet, networking fails.

---

