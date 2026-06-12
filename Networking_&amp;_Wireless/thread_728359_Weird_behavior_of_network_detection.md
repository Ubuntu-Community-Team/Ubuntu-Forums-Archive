---
title: "Weird behavior of network detection"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by arashiko28 on 2008-03-18
Ok, so this is the weirdest thig I've ever seen, not to mention riddiculous.

I have at home a Siemens Speedstream 4200 router, internet works just fine, I have it connected trough a D-link ethernet card (my original lan port is damaged).

Anyway, the thing is that right now, I'm on my cousin's house, with the exact same model of ruter, the same phone &  internet company and yet, my computer does not connect to the internet. And of course, my cousin's does. Please someone help me... :confused:

My netwirk configuration is set to roaming mode, I tried changing it to automatic and static address, and nothing works. What I'm I doing wrong if it's the same thing?

---

### Post by mindwarp on 2008-03-18
You may want to reset the router.  Some broadband companies bind to the computers MAC address.

Failing that, explain your network.  Does the 4200 serve dhcp addresses?  Have you tried dhclient eth0?  What does /sbin/ifconfig -a say?

Check out: [http://help.ubuntu.com/community/InternetAndNetworking](http://help.ubuntu.com/community/InternetAndNetworking)
so you can describe things and we can help you better.

---

