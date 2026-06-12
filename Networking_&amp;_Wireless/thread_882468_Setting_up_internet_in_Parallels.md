---
title: "Setting up internet in Parallels"
date: 2008-08-07
forum: Networking &amp; Wireless
---

### Post by kiranimo on 2008-08-07
So I am completely new to Linux, I have a Mac Mini Core Duo, and I haven't used Windows since '98. So a lot of this is new to me. But I just downloaded Ubuntu 8.04.1 and installed it using Parallels. 

I cannot figure out how to get online. I tried going to Networks, and then looking through all the tabs, but I can't figure it out at all. I'm on wireless internet for my Mac if that makes any difference. 

Please help!

---

### Post by Dougxdrums on 2009-08-01
I had a similar problem, this configuration worked for me...

Open parallels, change your networking to bridged networking and select airport.
In Ubuntu go to your network settings, double-click wired network, disable roaming mode and change your configuration to automatic configuration (DHCP).

That did it for me.

---

