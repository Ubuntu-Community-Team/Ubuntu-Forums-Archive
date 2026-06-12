---
title: "Switch Cards? What's the best NICs for Ubuntu or pfSense Router Build?"
date: 2019-09-11
forum: Networking &amp; Wireless
---

### Post by uRock on 2019-09-11
I have a whole rack of Cisco routers and switches, but they're all 100Mbps. What NICs do you use for your home router.  

 My current Asus router has great wireless, but gets bogged down when more than one person has their home screen open in the browser. My daughter and I put together a home screen on every computer that has buttons for each of our favorite websites, but also has all of our motion cameras streaming footage. The ASUS only has four switchports and I need more.

---

### Post by TheFu on 2019-09-11
I have an [APU2C4]("https://pcengines.ch/apu2c4.htm") for my router running pfSense ($150-ish).  It has Intel i210 NICs.  I specifically avoid non-Intel, since BSD doesn't do well with lessor NICs and Intel ASICs handle more on the NIC itself, which reduces the number of PCI interrupts for similar throughput.  I expect the router will last another 10 yrs, at least, so about $10/yr of service and there are quarterly updates for any issues. A patched router is important.  Most home wifi-routers get updates for about 3 yrs, then we are expected to spend another $250 for a new model.

My newest machine has a Intel i211 NIC on the motherboard. I specifically wanted intel for the NIC and no wifi.  I avoid using wifi at home. Even my wifi-only laptops use a USB3-to-GigE adaptor.  There's no comparison between a wired GigE connection and any available wifi today.

I use cheap $18 dumb 8-port switches for each physically separate network.

Aren't old Cisco gear without support?  Isn't that a security concern?

---

### Post by uRock on 2019-09-11
> **TheFu said:**
> I have an [APU2C4]("https://pcengines.ch/apu2c4.htm") for my router running pfSense ($150-ish).  It has Intel i210 NICs.  I specifically avoid non-Intel, since BSD doesn't do well with lessor NICs and Intel ASICs handle more on the NIC itself, which reduces the number of PCI interrupts for similar throughput.  I expect the router will last another 10 yrs, at least, so about $10/yr of service and there are quarterly updates for any issues. A patched router is important.  Most home wifi-routers get updates for about 3 yrs, then we are expected to spend another $250 for a new model.

My newest machine has a Intel i211 NIC on the motherboard. I specifically wanted intel for the NIC and no wifi.  I avoid using wifi at home. Even my wifi-only laptops use a USB3-to-GigE adaptor.  There's no comparison between a wired GigE connection and any available wifi today.

I use cheap $18 dumb 8-port switches for each physically separate network.

Aren't old Cisco gear without support?  Isn't that a security concern?
Lots of good info. My 1841 router has the newest IOS, but the other ones do not. I just bought them for doing my Cisco labs when I got started. I don't use them for production, as much as I would like to.

Thanks!

---

