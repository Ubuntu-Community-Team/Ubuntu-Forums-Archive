---
title: "Super Strange internet issue"
date: 2016-01-18
forum: Networking &amp; Wireless
---

### Post by William_Miller on 2016-01-18
I have a pc running Ubuntu 14.04. I originally had it connected to ethernet, cat5e, to a Linksys E300 router. My kid's mom has 2 iMac all-in-ones, and an iPhone, all connected wirelessly. Our roommate has an iPhone and a Macbook, both connected wirelessly. One day I came home and I was connected to the internet but all wireless had stopped. I used to fix computers and networks, so this should have been easy. It was not. Replaced router with Linksys E1200, replaced all ethernet cables, and I still have the problem. I even got 2 usb wireless cards, same issue.
When my Ubuntu machine is connected to the internet, no other machine can connect to the internet. 
I even plugged in the usb wireless card to a Windows XP machine, plugged an ethernet from it to my Ubuntu machine and made a network bridge so the internet came from the XP machine to my Ubuntu machine, and I still have the same issue. 

The only thing that makes sense is a virus, which I understand is hard to get on Linux.
I am using Wine for a few programs, so maybe I got a Windows virus that is running through Wine in the background? Unlikely.

HELP!!!!!

---

### Post by hkphooey on 2016-01-18
Do you have a fixed IP address assigned to the Ubuntu machine? If you have duplicate IP addresses on the network, that can create enough traffic to shut down your network. Check all IP addresses, and use DHCP if possible.

---

### Post by Bucky Ball on 2016-01-19
Yes, use DHCP, or, if you need/want static IPs, set up your router to only serve a range of IP addresses that don't interfere with your static IPs. For instance, you could set the DHCP server on the router to serve IPs between 192.168.0.100-120. Start your static IPs with anything above and including 192.168.0.121 and below and including 192.168.0.99.

This is the setup I use. The router is setup to serve ten IPs, when required, between a specific range (for visitors). All the permanent, home computers have static IPs. Easier to identify the little beggars. ;)

---

