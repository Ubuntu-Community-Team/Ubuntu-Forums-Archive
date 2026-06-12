---
title: "Compaq Presario CQ50-215NR - Wireless Not Working"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by papuccino1 on 2009-09-09
Here's a link to my machines specs: 
[Link]("http://reviews.cnet.com/laptops/hp-compaq-cq50-215nr/4505-3121_7-33309966.html")

I'm using Ubuntu 9.04. Please tell me what to write down in terminal so I can help you guys help me. :)

Symptoms:
Wifi "Light" on machine stays orange (meaning "off") regardless wether I press it or not.

No detection of my wireless network (I'm guessing because I technically don't have a wireless adapter according to Ubuntu)

Using a cable, my internet is fine.

Thank you.

---

### Post by NightwishFan on 2009-09-09
Are there any restricted drivers for the card? Go to system->administration->hardware drivers.

---

### Post by papuccino1 on 2009-09-09
OK, after some tinkering around I managed to make my wiresless card work.

I disables the restricted driver from where you said (DISABLED IT), and rebooted.

Now I can finally see my wireless connection and I'm using it as I type this! :)


One problem though...usually on Windows XP/Vista I could turn off my wireless card, can't I do this in Ubuntu? :S Sometimes I want to save battery power and I used to turn it off. I thought Linux could do this

MASSIVE PROBLEM. When I unplug my machine from the AC my wiresless goes down. wtf

---

### Post by atomizer on 2009-09-09
Light will not work, never had a setup which made my wifi-light turn to blue. The button does work.

Nice you have managed to get the wifi working

---

### Post by papuccino1 on 2009-09-09
Here's the output to that command:

> *-network               
       description: Ethernet interface
       product: MCP78S [GeForce 8200] Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:16:47:66:60
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 01
       serial: 00:23:4d:d6:f3:35
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.0.8 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: c6:09:ee:c5:c7:5e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


---

### Post by atomizer on 2009-09-09
AR242 drivers are build in to the kernel, as you have noticed.(since the card works after disableing the prop. drivers) But the light will not work. Probably your switch does work, and you should be able to switch your wireless on/off by pressing the button.

---

