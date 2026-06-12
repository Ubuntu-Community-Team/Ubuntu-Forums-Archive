---
title: "Using Ubuntu server 18.06 as a gateway, with two interfaces."
date: 2019-01-21
forum: Networking &amp; Wireless
---

### Post by MrMe01 on 2019-01-21
Hi folks,

Here's my current setup, I think it might help to explain how I have things set up.
ISP router that serves DNS and DHCP to the household (192.168.*.*), connected via ethernet is an Ubuntu server 18.04 box with two interfaces, on this machine I run Pi-hole and Zentyal.
 

I currently use Zentyal to act as an administration tool, but I wish to move away from it. I use it to set the interface addresses and other details, and use the DNS and DHCP services of Pi-hole. It also allows traffic to move between one interface and the other. Is this bridging, and if so, what packages does Zentyal use, I'd prefer to drop all the configs where required.

Something worth noting, I do use Webmin on this machine too, can I enable this bridge like functionality from there?

What packages should I be using to replace the monstrosity that Zentyal has become?

It really is garbage, I should have stuck with 16.04 and the previous version, but then they borked apt, I was one of the first few to notice and jumped ship as soon as they released the 18.04 version.

---

