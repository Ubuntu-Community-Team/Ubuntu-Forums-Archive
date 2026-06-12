---
title: "Can Ubuntu do what I need?"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by athowell on 2008-06-24
I want to setup a computer with 2 network cards. 1 wireless and 1 LAN.

The wireless card is set to connect to my roomates wireless netgear switch that has roadrunner internet on it.

[using xbuntu for this box because it's only 500mhz 256mb ram]

The LAN card will be directly plugged into the uplink port on my wireless linksys switch.

Can Ubuntu, the box sitting in the middle. Allow me to connect to the Linksys switch via laptop and route my packets from the LAN to the wireless card and give me access to the internet?

I was going to load up firestarter because my friend says it should allow me to share my connection and act like a router.

My brain hurts now, please help.

---

### Post by spd106 on 2008-06-24
Yes, it can do this.

You need to: 

1) Figure out the DHCP situation.

You only want one DHCP server really and this will be your friends wifi router. So I would turn off the DHCP server in your router and make sure that the Xubuntu box doesn't have it on too.

2) Bridging (or NAT)

You need to set-up the Xubuntu box as a bridge between the wifi and your wired network. There are instructions on this wiki page [https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge)

If you can't get the bridge working then fall back to using NAT with firestarter or similar instead.
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

---

