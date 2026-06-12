---
title: "NetworkManager 0.7 wireless priority over wired"
date: 2008-10-26
forum: Networking &amp; Wireless
---

### Post by fitzman49 on 2008-10-26
Here is the story about my network setup and my problem.

I have my desktop running intrepid release candidate with the newest version of Network Manager from their SVN repo. My setup is pretty weird compared to most peoples.  I use my wireless connection to get a connection from my router which is connected to the internet using DHCP to get an address.  I have a simultaneous wired connection that I have connected to my printer using a static address.  So I have two interfaces running at the same time.

My problem is when I use network manager to manage both connections (since I heard this is now possible in version 0.7), it will start the wireless connection first, then the wired connection.  This will cause the default route in my routing table to point to the wired connection causing me to have no internet unless I manually enter in the following:
```
sudo route delete default gw 111.111.111.1
sudo route add default gw 192.168.1.1
```

I would rather not change my physical setup since the other people I live with are weary about having all kinds of stuff hooked up directly to the router.  I would also not like to buy a USB cable since I'm cheap and I have a few extra ethernet cables lying around.  My question is does anyone know of a way to get network manager to load the wired connection first then wireless to avoid the annoying manual fix every time I boot?  I can't seem to find a config file for network manager to change settings so maybe that is my problem but any help is appreciated.

Thanks,
Fitz

---

### Post by fitzman49 on 2008-10-26
Well after hours of fooling around, I figured out that instead of using network manager for both connections I entered the static configuration in /etc/network/interfaces and let network manager handle only my wireless interface.  Worked like a charm.  This could also be useful for people who would like to use multiple network connections at the same time.

---

### Post by COKEDUDE on 2011-02-13
Could you explain what you added to /etc/network/interfaces?

---

### Post by simioliolio on 2011-10-27
i stumbled across this problem earlier. for the wireless, i set automatic dhcp, and for wired, i have a static ip which is out of the wireless subnet, so my wireless acquires ip 192.168.0.31, with subnet 255.255.255.0, and my wired is manual at 192.168.2.2, subnet mask 255.255.255.0, but could only get the internet to work with the wired connection active if the gateway of the wired connection was set to 0.0.0.0. seems to work so far...

---

