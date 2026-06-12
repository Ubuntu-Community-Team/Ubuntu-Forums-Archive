---
title: "Broadcom 4311 - card connects to router, but no ping"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by Ulanbatar on 2007-12-15
I installed a Ubuntu partition on my HP dv6253cl a week ago. So far it's been great, but getting the Broadcom card set up has me spinning in circles. It's a BCM94311MCG (14E4:4311). I followed the [usual ndiswrapper guide]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show#head-f744e28e6c78eb83d22be77819b130016a8e51f3"), and the light on the card is on, the card shows up in ifconfig and iwconfig with correct IP and access point. I can ping localhost and the card's IP, but nothing else on my network.

In the router log I can see that the wireless card is rapidly associating and disconnecting ("disconnected for reason: Received Deauthentication"). The router is a D-Link DIR-625. The setup works as expected when I boot Vista.

I've combed the forum and other places, learned much about Linux in the process - much more, in fact, than if this process had gone smoothly :) - but no dice. Any help in troubleshooting this is much appreciated.

---

### Post by Junglizer on 2007-12-17
check /etc/resolv.conf
check that your routes are correct.

---

### Post by Ulanbatar on 2007-12-21
Yes, routes and resolv.conf are all correct.

I should also mention that everything works fine with a cabled connection it's just the wireless that gives me these problems...

---

