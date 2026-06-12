---
title: "[SOLVED] card works but unable to connect"
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by irwineffect on 2008-10-02
alright so I transfered from xp to ubuntu a few weeks ago and I decided to see if I could get my wireless card to work. I plug it in, the card's "power" light turns on and the "act" light starts to blink, just like the card did with xp. I click on the network monitor and my home wireless network shows up. I click to connect, input my WPA password, and the computer trys to connect, but never does. I thought the problem just might be the fact that my network is encrypted, so I removed the WPA encryption. still no luck. So I assume that I have the neccesary drivers built in since I can see my wireless network, so why can't I connect?

---

### Post by nixscripter on 2008-10-03
What kind of card is it? Sometimes the drivers don't have all the capabilities of the card. Open a terminal and post the output of the command: ```
lshw -C network
```

Make sure to put [code] tags around it so it's readable.

---

### Post by irwineffect on 2008-10-04
It is a Airlink Wireless CardBus Adapter   AWLC3025




```
 *-network               
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:88:9d:6a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=natsemi driverversion=2.1 ip=192.168.0.101 latency=90 maxlatency=52 mingnt=11 module=natsemi multicast=yes
  *-network
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:e0:98:d7:8e:e3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci latency=64 module=acx multicast=yes wireless=IEEE 802.11b+/g+

```

---

### Post by irwineffect on 2008-10-04
well I did a little more searching and I used the windows wireless drivers installer (ndiswrapper) to install the windows driver for the card. It works now! Thanks though. All I needed was the right driver.

---

