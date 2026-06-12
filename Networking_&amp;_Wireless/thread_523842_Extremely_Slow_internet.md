---
title: "Extremely Slow internet"
date: 2007-08-12
forum: Networking &amp; Wireless
---

### Post by Wwiillburr on 2007-08-12
Hey all, I came here from Gentoo after a hiatus and a move.

My internet connection in Linux is extremely slow but in Windows is fine.  Also before I moved there was no difference in speed, which leads me to believe this is a router problem?

I have a Linksys WRT54GL with the DD-WRT firmware.  I upgraded to that to try to resolve this issue.

I have also tried the IPv6 fix in Linux and the tcp_scaling fix.

I also don't think it's a DNS issue because the DNS names are resolved extremely quickly, but the actual transfer of Data is slow.

For instance, when upgrading Fiesty's programs through synaptic, I get download speeds of 3kbs on one laptop and timeouts and 1kbs on another laptop.  I've racked my brains, any help?

---

### Post by 1/0 on 2007-08-12
Have you tried to turn off the wireless security and instead turn on the access control using the MAC address? I figure the security setting could slow down the throughput. Try it and if it doesn't work, turn it back on. 

What's the MTU? It usually is at about 1500 but could need a change to, lets say 1492...

I don't know about rwin but I remember something about the values messing up the throughput. 

Just some ideas.

---

### Post by Wwiillburr on 2007-08-12
I disabled any wireless security until I could get this problem figured out.

Also the MTU change did not affect my problem.

---

### Post by 1/0 on 2007-08-12
This is a wireless connection, right? 

Sounds like either a DNS setup problem or a DHCP problem. Could have to do with releasing the IP:s. I haven't thought through this, just wanted to give you some more ideas.

---

### Post by Wwiillburr on 2007-08-12
Just an update, I brought my computer to a different house with a different router and provider and it works flawlessly.

---

### Post by Wwiillburr on 2007-08-13
After more testing I can not figure out for the life of me what setting my router or ISP would have that would slow down my connection so much.  I guess I could try a different router on my ISP and narrow it down more to either the ISP or the router.

---

### Post by 1/0 on 2007-08-13
It still sounds like some DNS/DHCP thingie. 

First try to connect direct to the internet. Its what the help desk will tell you to do and its good to rule out anything but the router. Then try to connect a computer via cable through via the router and last wireless. 

If the problem rests within the router I would reset all settings after backing them up and start over from the beginning. It sounds like some setting is off with the DNS/DHCP, maybe release times of the IP:s or something. Have you tried setting the Linksys IP (192.168.1.1?) as DNS server in Linux and using static instead of DHCP? It could be to start over than finding that one setting among all. 

I remember reading something about Linksys switching the Linux firmware to something of their own. Very unlikely but it could be a bug, or just a defective router.

---

