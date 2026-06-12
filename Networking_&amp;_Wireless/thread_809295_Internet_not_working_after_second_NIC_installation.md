---
title: "Internet not working after second NIC installation"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by Carisma on 2008-05-27
Okay...over the weekend my NIC on my motherboard went out without any notice.  So I decided to go buy a NIC card from Bestbuy ([D-Link - Desktop 10/100 PCI Network Card]("http://www.bestbuy.com/site/olspage.jsp?skuId=3863251&type=product&id=1051384161297")).

It works on a Windows box but when I tried it on my Linux box it doesn't work.  It starts up with the following eth:

eth0 - doesn't work
eth1 - doesn't work
eth1:avah - pulls back a IP address (162.xxx.x.xxx)

Unfortunately, I am not at home right now to pull back anything.  I can later tonight though.

Any help would be greatly appreciated.

Thanks in advance.

---

### Post by tigerplug on 2008-05-27
> **Carisma said:**
> Okay...over the weekend my NIC on my motherboard went out without any notice.  So I decided to go buy a NIC card from Bestbuy ([D-Link - Desktop 10/100 PCI Network Card]("http://www.bestbuy.com/site/olspage.jsp?skuId=3863251&type=product&id=1051384161297")).

It works on a Windows box but when I tried it on my Linux box it doesn't work.  It starts up with the following eth:

eth0 - doesn't work
eth1 - doesn't work
eth1:avah - pulls back a IP address (162.xxx.x.xxx)

Unfortunately, I am not at home right now to pull back anything.  I can later tonight though.

Any help would be greatly appreciated.

Thanks in advance.


Which Eth interface is set as the default?

---

### Post by Carisma on 2008-05-27
> **tigerplug said:**
> Which Eth interface is set as the default?Prior to the install of the new NIC, it was set to eth0.

---

### Post by Carisma on 2008-05-27
So far, I have been told to do the following when I get home:

[COLOR=#000000]- [/COLOR][COLOR=#000000]run ethtool -p eth0 to see WHICH one is eth0 [/COLOR][COLOR=#000000][COLOR=#0163B3] [/COLOR]then a tcpdump -i eth0 to see if it sees anything on the wire[/COLOR][COLOR=#000000]
[/COLOR]

---

### Post by tigerplug on 2008-05-27
> **Carisma said:**
> So far, I have been told to do the following when I get home:

[COLOR=#000000]- [/COLOR][COLOR=#000000]run ethtool -p eth0 to see WHICH one is eth0 [/COLOR][COLOR=#000000][COLOR=#0163B3] [/COLOR]then a tcpdump -i eth0 to see if it sees anything on the wire[/COLOR][COLOR=#000000]
[/COLOR]

Yup - thats a good idea. Do that. At least with TCP dump you'll know whats happening if anything at all :)

---

### Post by Carisma on 2008-05-27
> **tigerplug said:**
> Yup - thats a good idea. Do that. At least with TCP dump you'll know whats happening if anything at all :)
What should I look for?

---

### Post by Carisma on 2008-05-28
Okay I think I figured it.

So I did a fresh install of 7.10 and the onboard NIC worked but once I installed all the updates, it kicked the internet again.  I don't know what update did it because there were 220 updates.

After that I tried everything to get it working again without any luck.

So right now, I am looking to see what are the latest updates to see which one might have changed the NIC.

---

