---
title: "Wireless interface &quot;vanished&quot; from Network Manager"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by EduMaxwell on 2007-05-09
I put Feisty onto my new Acer Aspire 5050 and had an easy time connecting to wireless with NetworkManager...until two days ago.  Suddenly, my wireless interface no longer exisits, not in NetworkManager at least.  From my little knowledge, it seems that I either did something to corrupt the drivers, or there is a hardware problem (caused by what, I don't know).  The only (circumstantial) evidence for anything is that I took the notebook to school and tried to connect to the wireless network there (without success).  Came back home and *poof*, no more wireless interface in Network Manager.

Lovin' Feisty, just want wireless back.  Code follows...and Thank you in advance! :) 

**lshw:**
 *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@08:02.0
                logical name: eth0
                version: 10
                serial: 00:16:36:e4:44:d8
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.2.101 latency=64 maxlatency=64 mingnt=32 multicast=yes
                resources: ioport:a000-a0ff iomemory:d0211c00-d0211cff irq:20
           *-network:1 UNCLAIMED
                description: Ethernet controller
                product: AR5005G 802.11abg NIC
                vendor: Atheros Communications, Inc.
                physical id: 4
                bus info: pci@08:04.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=168 maxlatency=28 mingnt=10
                resources: iomemory:d0200000-d020ffff irq:21

**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by chrisbain88 on 2007-05-09
hi
i had a similar problem with my wireless on my acer apire 3683.
it wasnt until i upgraded to 7.04 that i think i found the solution.
if u run windows aswel and use the disable wireless button on the laptop, i found that when i booted back into ubuntu it was gone, however when i booted into windows and enabled my wireless with the button on my laptop i had it appear again the the list in ubuntu.
hope this helps
chris

---

### Post by EduMaxwell on 2007-05-09
Thanks.  Up until Feisty, the WLAN in many Acer Aspires has given Ubuntu users some problems -- not unresolvable though.  I had my wireless up and running in Dapper and Edgy after some work.  Feisty seems to have resolved most of the issues...excepting perhaps my current dilemma.  

I do not run Windows on my Acer and have tried to turn the wireless on and off (using the switch on the front of my notebook) with Feisty running.  You might be onto something though.  I wonder if there is a way to turn the wireless on and off without another OS running.  It could very well have something to do with activating the card physically, rather than a problem with the drivers.  I am still not sure and don't have enough Ubuntu experience to know what I am talking about...hoping for some more help!  Thanks again.

---

### Post by EduMaxwell on 2007-05-10
Well, I came home from school and powered up the Acer today to do some more troubleshooting.  I started by running the Live CD (Feisty) to see if I would get wireless on that...to no avail.  Then I restarted and booted up my regular Feisty and...*poof* again.  Wireless is back.  It is "fixed" for now, though I have NO idea how.  

Has anyone else come upon this little trick that Feisty is playing on me?  I am happy to have wireless back, but a little timid about depending on it in a pinch.

---

### Post by pmagill on 2007-05-10
I too have the same problem one day it was there the next its gone???
Gonna try the live cd approach as you mentioned before

---

### Post by EduMaxwell on 2007-05-12
The more I think about it, the more I am convinced that the wireless problem had to do with activating the card using the switch in front of the notebook (orange light switch to the right of the bluetooth switch).  While booting up, I held that switch for a good three seconds, and when I logged in my wireless was back.  What is strange is that I had no indication outside of terminal queries and the NetworkManager applet whether my card was activated.  So the Acer will not tell you (with the light) whether the card is activated...IF my theory is correct.

---

### Post by stchman on 2007-05-14
> **EduMaxwell said:**
> I put Feisty onto my new Acer Aspire 5050 and had an easy time connecting to wireless with NetworkManager...until two days ago.  Suddenly, my wireless interface no longer exisits, not in NetworkManager at least.  From my little knowledge, it seems that I either did something to corrupt the drivers, or there is a hardware problem (caused by what, I don't know).  The only (circumstantial) evidence for anything is that I took the notebook to school and tried to connect to the wireless network there (without success).  Came back home and *poof*, no more wireless interface in Network Manager.

Lovin' Feisty, just want wireless back.  Code follows...and Thank you in advance! :) 

**lshw:**
 *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@08:02.0
                logical name: eth0
                version: 10
                serial: 00:16:36:e4:44:d8
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.2.101 latency=64 maxlatency=64 mingnt=32 multicast=yes
                resources: ioport:a000-a0ff iomemory:d0211c00-d0211cff irq:20
           *-network:1 UNCLAIMED
                description: Ethernet controller
                product: AR5005G 802.11abg NIC
                vendor: Atheros Communications, Inc.
                physical id: 4
                bus info: pci@08:04.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=168 maxlatency=28 mingnt=10
                resources: iomemory:d0200000-d020ffff irq:21

**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

That happened to me a while back.  A patch came through that updated the kernel, when that happened it broke madwifi.  I just did a make on the madwifi drivers again.

---

