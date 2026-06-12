---
title: "bridge wireless access to rest of network on same subnet"
date: 2016-06-27
forum: Networking &amp; Wireless
---

### Post by vin3 on 2016-06-27
Hi,

Spent a couple of weeks banging my head against this problem. I've tried Ubuntu (Desktop and Server) 16.04, in a virtual machine which I want to act as a bridge between my main LAN, and a wireless adapter, so that I can get rid of one of the wireless boxes I've got in use right now. I've got a firewall box, which provides various services like DHCP, and also acts as the gateway, on 192.168.0.1

I can get hostapd working OK, I can see the SSID from a laptop, and I can connect so long as I setup a static IP address.

I've set up a bridge using the various guides, and have tried a few different approaches, but in the end just try the various brctl create and add interface steps from the command line. The bridge comes up OK, and the 192.168.0.2 address is pingable from the rest of the network. 

The laptop can ping 192.168.0.2 but no other addresses. Its like no data is crossing across the bridge. 

I've seen a few posts suggesting that this isn't possible, but also a few that seem to have achieved what I want to do (I've turned the 4addr option on which seems suggested as a requirement, and without that on I can't add the wireless device to the bridge anyway). Given that routers running dd-wrt / openwrt seem to manage it, which I think just use linux functionality, it made me think it might be possible. 

Otherwise the more common approach seems to be to run a dhcp network on the wireless side, so in my case I guess 192.168.1.X. But then I wonder about how devices will detect each other still - I guess possible with some routing rules?

Wondered if anyone has managed something similar? I've tried openwrt in a VM on that box too, but struggling to get the iwlwifi drivers detected the wifi card there!

Thanks!

---

### Post by vin3 on 2016-07-03
Ah figured it out in the end! In ESXi a default network switch has promiscuous mode disabled - enabling that fixed the problem!

---

