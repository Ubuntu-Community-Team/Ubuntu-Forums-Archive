---
title: "Buying a new Broadband Modem"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by adelgado on 2007-05-10
I'm going to buy a new broadband modem soon and I am wondering if I have to worry about the model.

At first, I though I should search to see if a specific modem was Linux-Compatible, but then I though, "They are all Ethernet, and they all use PPPoE protocol, so is there really a difference? Do I even need a driver?"

It's important to notice, though, that it is a router-kinda modem: It's one of those with 4 RJ45 Ethernet ports and one port for connection with the Internet (Like the D-Link 500G Modem).


Thanks in advance!

---

### Post by GTvulse on 2007-05-10
In general, it doesn't matter much. On the other hand, it depends on your needs and plans for the future. For example: Do you want to use wireless and not buy a second wi-fi router in a few months? Are four wired ports enough for your LAN or would you need a switch? Is there the possibility that your ISP offers aDSL-2 in the future? How reliable is the firmware in the modem you want to purchase, will it break if using something like bittorrent? Does the modem support uPnP, port triggers, hardware firewall, etc.? Does your ISP offer PPPoE, PPPoATM, or some other type of connection? Does the modem support such technology? Will you be using the modem as a router or as a bridge (with a second router inside the LAN)?

Those are questions you have to answer yourself, but IMHO they are a good framework to make a decision on your purchase.

Good luck!

---

### Post by adelgado on 2007-05-10
Thanks for the answer.
Well, I don't want to use wireless in the future.
Four wired ports are more than enough to my LAN.
My ISP certainly won't offer ADSL-2in the future, at least not in the _near_ future.

How can I get information abaout the firmware, and there are really modems that'll break if I use something as BitTorrent?

What are uPnP's; what are port triggers? Do I need them? How can I find out if the modem does support them?

My ISP offers PPPoE, and the modem will support it. What's PPPoATM?

I will be using the modem as a router.


Thanks in advance!

---

### Post by adelgado on 2007-05-11
Up! (Just upping because I need to buy it today...) :oops:

---

### Post by GTvulse on 2007-05-11
Best way to find out if the modem has firmware problems is to do a quick search in Google. You can always dig out the dirt there. 

UPnP is "Universal Plug and Play". which is a technique for automatic assignment of Traversal NAT service ports; very common in MS Windows, not many GNU/Linux applications use it but some do: Azureus, aMule 2.2/3.0 will (not released yet); it is in the plans for Deluge Torrent and GTK-Gnutella as far as I know and it may already be implemented in Transmission (but I haven't tested the latest stable version yet).

Port triggers are Traversal NAT service port assignments that open only when activated from inside the LAN (a sort of port-knocing from the inside). Else, the assigned ports are open permanently, that is hard-wired. This is the state of things for most people using GNU/Linux BTW; a proposition that may or may not appeal to you (and the only reason I justify using a firewall inside a NAT, a couple of iptables rules controlling access to those ports in the pre-up interface scripts are usually more than enough).

---

