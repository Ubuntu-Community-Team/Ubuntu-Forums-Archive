---
title: "HP DV8000 Wireless card will not turn on.  The button for the &quot;light&quot;  won't work..."
date: 2008-12-26
forum: New to Ubuntu
---

### Post by fidgetyacolyte on 2008-12-26
This is my first time ever using ubuntu or linux.  I have a fresh install of Ubuntu 6.06 on my hard drive, and it is NOT partitioned, so this computer is running solely off Ubuntu, and it seems from what I read here that not only is the Broadcom 4318 a hassle to make work, its even more of a hassle with HP DV8000.  I've read through both HOW-TOs (CompWiz's and the one he links to about dv8000) and it seems like everything works fine up until the point my wireless card is supposed to start doing something.  When the light is supposed to come on, mine stays off.  When I ran Windows XP, I could turn the card off or on by pushing a button, and a light under the monitor would turn on to indicate the wireless card is on.  

When I look in my terminal at "lshw" i get the following result for my broadcom card:```
*-network:0 UNCLAIMED
                description: Network controller
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@06:02.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                resources: iomemory:c0204000-c0205fff irq:10

```

I've read a bit and I heard there was an rf_kill switch or something that I need to turn on/off.  I'm getting kinda confused, and this wired connection  really puts a hamper on having a laptop.  Any assistance would be greatly appreciated!

Sorry if I'm being vague, if you need anymore information I'll gladly supply.

thanks!

---

### Post by overdrank on 2008-12-28
Moved to Absolute Beginner Talk :)

---

### Post by Sealbhach on 2008-12-28
There's way better wireless support in the latest release, 8.10. I don't know why you would want to use such an old release?:confused:


.

---

