---
title: "Setting up a static IP"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by ketzerei on 2007-09-05
OK, here's whats up. I've read a few other threads and posts and so far havent found the answer for what im looking for. I have a Modem, plugged into an internet cable. We do not posses a router, but we do own a hub. My question is, can I hook our computer upstairs to the hub, along with our computer downstairs, and then in turn plug the hub into the modem? Also, if I do, do I need to use static ip or assign my own somehow to get internet access? Help very much appreciated.

---

### Post by KCPokes on 2007-09-05
Yes, to a point, you can do that, meaning you can plug your modem into the hub and all machines into the hub.  Problem is, depending on your provider, you will be limited to a number of IP addresses.  A hub will not allow you to assign private static IPs internally as there is no layer 3 device to separate the two networks; your 192.168.xxx.xxx network would exist with your providers network, which means your machines would essentially be unknown to any network devices.  

You will need a router to accomplish what you are attempting as it is the only way to separate the networks.

---

### Post by ketzerei on 2007-09-05
Wait, so I cant accomplish it this way? Crap.

---

### Post by KCPokes on 2007-09-05
You could accomplish it only if your ISP allowed you to pull three separate IPs; one for each machine you had hooked up to the hub.  Most dont.  If they did, just remember that you have now essentially put all three of your machines "smack dab in the middle of the internet".  That's the big draw to having a router, or firewall; it creates your own private network and gives you that layer of protection.

---

