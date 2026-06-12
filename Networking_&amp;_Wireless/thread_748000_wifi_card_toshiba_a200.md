---
title: "wifi card toshiba a200"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by insurin on 2008-04-07
Is it possible to get my wifi card working in ubutnu. I have a toshiba a200 psae1e

lspci shows  Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev             01)

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

kdeinfo only shows eth0 and lo

I have had wireless working using backtrack 2 so it has worked under linux but I do no know how to get it working under kubuntu

---

### Post by Tom--d on 2008-04-14
Install ndiswrapper and use the windows driver to run the card

---

### Post by kevdog on 2008-04-14
The restricted drivers (madwifi) are not configured to run this card?  Did you try installing the linux restricted drivers from synaptic?

Can you type 

lshw -C network
lsmod | grep ath

---

### Post by 67GTA on 2008-04-15
I'm having no luck either with Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter. The restricted drivers manager shows the drivers are installed and enabled. Networkmanager shows no wireless connection, only wired and modem.

```
shawnr@fastback:~$ lshw -C network
 *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:2c:78:66
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.0.102 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
```

```
shawnr@fastback:~$ lsmod | grep ath
ath_pci               101024  0 
wlan                  207728  1 ath_pci
ath_hal               192592  1 ath_pci

```

---

