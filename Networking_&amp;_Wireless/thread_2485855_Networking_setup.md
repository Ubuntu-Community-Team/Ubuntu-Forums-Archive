---
title: "Networking setup"
date: 2023-04-12
forum: Networking &amp; Wireless
---

### Post by janderion on 2023-04-12
Hey there, I have been messing around with networking on a machine of mine and I want to know how I can setup multiple ethernet connections that are being shared from one machine.

To be clear, I have a Main Machine (MM) that has a source ethernet connection to my dorm room's internet, and multiple ethernet cards that share internet connection from MM, what sort of networking setup do I have to do to make it so that the various other machines connected to MM can talk to each other?

---

### Post by TheFu on 2023-04-12
You need a router.  You can buy a cheap router for $10 used or setup your MM as a router.  Beware, creating your own router can have terrible security implications, but if you want to learn, it is a good method.

**Update:**
Typically, I wouldn't suggest getting a $10 router to protect a network. Usually those are so far behind on security patches as to be a huge danger.  

About the cheapest, yet good-enough router, would be in the $50-$80 range from Asus, Mikrotik, or Ubiquiti.  I think Ubiquiti makes a non-wifi router with 4 ports for $50-ish.  Yep, the "Ubiquiti Networks ER-X EdgeRouter X". It uses a different OS, specifically designed for routing.  It is sized like a small switch.  For the price, it is an excellent router.

Sadly, it doesn't appear that Asus makes any non-Wifi routers.  Their cheapest "wifi-5" (that's an 802.11ac model) can have the wifi disabled. That's what I'd do to avoid wifi in-security.  Asus is really good at patching their network equipment for longer than other home router brands.

If you just want to learn about routing while in a safe environment, I'd say to setup a virtual machine using PCIe passthru for at least 1 NIC and run OPNSense inside the VM.  I'd never do this for a router protecting a WAN connection, but for a home lab in a relatively safe environment, it can be a good way to learn things with mid-sized enterprise solutions for free.  The PCIe passthru is a critical aspect of the solution. If you can't do that part, then go spend $50+ and get a cheap Ubiquiti ER.

---

### Post by SeijiSensei on 2023-04-12
Most routers these days offer an array of features that would take you hours to set up without experience. You don't just need routing. You probably want a DNS server so the machines can identify each other. You might want to do IP filtering for which you'd need a well-developed set of iptables rules. Take TheFu's advice and go buy a router.

---

