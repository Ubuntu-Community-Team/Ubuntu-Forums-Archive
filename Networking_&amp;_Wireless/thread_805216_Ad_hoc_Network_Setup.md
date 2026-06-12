---
title: "Ad hoc Network Setup"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by suby-luby on 2008-05-23
I just installed Ubuntu 8.04 and would like to setup an ad hoc network. I tried using the Network Manager, "Create New Wireless Network", but my other laptop cannot detect the network I try to establish.

Can you one please help with this matter, it is very important.

Thanks:popcorn:

---

### Post by lswb on 2008-05-25
Some of the wireless drivers supplied with 8.04 unfortunately appear to have less functionality that the older drivers used with earlier distributions. I had this same problem when I was using an rt2500 PC card; The r2x00pci drivers do not support ad hoc mode. I managed to compile a version of the older serialmonkey rt2500 driver and was able to set up an ad-hoc network using iwconfig, but guess what, the rt2500 driver isn't recognized by Network Manager! Arrgh! Tried wicd for a while with some success but it had its quirks also.

This was all especially frustrating since I had all these things working under Dapper on my older notebook, though it took multiple tools and a script or 2. At any rate, I wanted to leave the rt2500 card with the old notebook, and after I installed an Intel Pro 2200 mini-pci card in my new notebook, I was able to get things sorted out. The ipw2200 driver that this wireless card uses both supports ad-hoc mode and is recognized by Network Manager.

I know this doesn't directly help you but I just had to vent! What kind of wireless device are you using? show the output of iwconfig and let's see what we can figure out.

---

