---
title: "Setting the internet interface card"
date: 2007-03-30
forum: Networking &amp; Wireless
---

### Post by Jercos on 2007-03-30
Okay, I have three main NICs in my main PC, a wireless card and two ethernet cards. I have a network of old PC's connected to the ethernet card, and my dsl modem on a wireless network in the other room. to test everything out, I have a webserver inside the network and my main PC is a webserver. depending on the order I set things up in, my main PC will either, access the network but not the internet, access the internet but not the network, or it will access the internet fine, and everything in the network will be extreamly slow... is there a way to set one card as being an external access card, and have one card cath all requests in a given subdomain?

---

### Post by Mr. C. on 2007-03-30
Your description is a little confusing, but I think I'm getting this:

1) you want all PCs to be able to access the internet at the same time
2) you are experiencing slow networking
3) one of the wireless cards on your main PC is connected to the wireless A/P/Internet
4) the second wireless card is unused
5) you have a series of PCs connected to a switch (or hub?) which connects to your main PC's Ethernet card

Please clarify,
MrC

---

### Post by Jercos on 2007-03-31
Sorry I didn't specify clearly enough...
A is my main computer,
B, C, and D are other computers,
E is a wired router that I do not want exposed to the internet

A has a wireless card and and ethernet card (as well as another I'm not using)
A, B, C and D are all connected on wired router E
A is connected to the internet over a wireless connection

My goal is to have A connect to a private, disconnected LAN over E, without disrupting its connection over wireless to the open internet

When I am connected to both, A sometimes will try and get an internet page over E, and fail because the LAN nameserver doesn't have the domain (e.g. google.com) or because the server is not on the LAN... what I want is for A to never use E unless it is connection to a 192\.168\.[01]\.* address. hopefully that clears up any confusion...

P.S. I do *NOT* want the internet directly accessable from any computer on E exept A.

And here is what happens when you use paint all your life and then switch to the GIMP:
[IMG]http://jercos.dyndns.org/~jercos/diagram.png[/IMG]

---

### Post by Mr. C. on 2007-03-31
Perfect drawing and explanation.

Your task is simple.  The default in Linux is *not* to forward packets, so everything behind E will not be seen, provided you have two subnets:  B, C, D, and the interface on A are one one subnet, and A's wireless and the LAN port of the A/P are on another.  The subnets must be different.  A should be on E's WAN port.

You need to be sure that your default route on A is set to the LAN IP of your wireless A/P/modem.  It will forward traffic all traffic (not destined for the connected subnets) to the internet via A.

Because you have more than one interface, if Network Manager is running, you'll need to work around a silly bug.  You need to configure the default route (gateway) explicitly, as Network Manager doesn't know which interface to use, and creates two gateways.

In the file /etc/network/interfaces, be sure that there is one gateway listed.  It should be listed under your wireless device (eg. wlan0).  If there are additional gateways, remove them.  This alone is not sufficient, as you have to enable the default route (which may be incorrect currently).  You can manually add the default route each time the network is brought up to work around the bug, or you can manually bring up the second non-internet interface on A.  I would remove the "auto eth0" entry (which I presume is the interface connected to your private net), and bring the interface up manually.  Disable the device in Network manager and then run "ifup eth0".  I'm assuming you are using a static IP for eth0.

Review this if more info is needed: [http://ubuntuforums.org/showthread.php?t=389305&highlight=route+add](http://ubuntuforums.org/showthread.php?t=389305&highlight=route+add)

Test that this configuration works for you.

MrC

---

