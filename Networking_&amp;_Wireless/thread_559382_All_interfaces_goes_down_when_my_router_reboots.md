---
title: "All interfaces goes down when my router reboots"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by joke_dst on 2007-09-25
I have WLAN connection on my laptop, but also a router connected with a TP cable, and when I reboot the router, both the WLAN and the Ethernet interface the router is connected to is disconnected! Basically the interfaces looses their IP addresses.

To get the WLAN to work again I have to manually run dhclient. If i just let it sit it starts working again after a few minutes. 

Any ideas on how to circumvent this? Especially the WLAN interface, I really don't see why it shuts down the WLAN because the ethernet port got disconnected!?

---

### Post by RaZer0r on 2007-09-25
when you reboot your router, the router will disconnect all power to every RJ45 port. this evolves in a real disconnect. Your laptop will recognice this as a manual cable disconnect, and so lose internet, and ip. It will reconnect automaticly;.. as you said. just run:

sudo ifdown -a && ifup -a

and your connection should be up.

---

### Post by joke_dst on 2007-09-25
But there must be a way to make the WLAN interface stay up when an ethernet cable is disconnected, right? I mean, this is LINUX after all! :)

How do I "protect" my WLAN (and other ethernet interfaces) from disconnecting when I unplug a cable?

---

### Post by netztier on 2007-09-25
> **joke_dst said:**
> I have WLAN connection on my laptop, but also a router connected with a TP cable, and when I reboot the router, both the WLAN and the Ethernet interface the router is connected to is disconnected! Basically the interfaces looses their IP addresses.

To get the WLAN to work again I have to manually run dhclient. If i just let it sit it starts working again after a few minutes. 

Any ideas on how to circumvent this? Especially the WLAN interface, I really don't see why it shuts down the WLAN because the ethernet port got disconnected!?

Now what ... because you reboot the router (what model/brand is that device, anyway?) or because your unplug an ethernet cable from that router?

Can you give more details about your network topology, please?

best regards

Marc

---

### Post by joke_dst on 2007-09-25
I have a laptop with a WLAN interface and an ethernet port. I connect to the internet through the WLAN and is connected to a router (a Dovado WRG) with the ethernet cable. The router is **not** connected to the internet.

I have dhclient set up to listen to the WLAN and the ethernet port set to a static IP (ifconfig eth0 192.168.0.2), this so the routing table won't include the router (it's a dead end basically). 

When I reboot the router (which I do pretty often) I lose my WLAN connection as well. After a while it comes back up, I guess it's the dhclient or something, not sure. But I don't want to lose my WLAN connection just because I lose the ethernet connection!

The same happens if I unplug the ethernet cable; the WLAN interface loses it's IP and I can't connect to the internet. 

I can speed up the reconnect process by taking the WLAN interface down+up but that's a mess really. I can also restart the dhclient manually and the WLAN starts working again.

Any ideas how to make the WLAN stay up when the ethernet cable is disconnected?

---

