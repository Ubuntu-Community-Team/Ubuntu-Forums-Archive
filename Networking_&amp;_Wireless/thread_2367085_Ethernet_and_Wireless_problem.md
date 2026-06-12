---
title: "Ethernet and Wireless problem"
date: 2017-07-25
forum: Networking &amp; Wireless
---

### Post by sicd on 2017-07-25
Hi everyone. I am trying to install Lubuntu 17.04 on my Pavillion dv2500 Notebook PC. I tried 2 years ago but i coudn't install net cards so i installed KaOS on it and it worked great (btw, i have Lubuntu 14 on Samsung N210 and keeps running great). But now i want to try again Lubuntu on this laptop. However the problem persist. I've been reading some similar post but i can't solve this problem. Hope you can help me. (Sorry my bad english, greetings from México n_n)




The ethernet icon shows connection stablished but doesn't work. Wireless connection doesn't show available networks.




Results from sudo lshw -C network:




```
description: Ethernet interface

product: 88E8039 PCI-E Fast Ethernet Controller

vendor Marvell Technology Group Ltd.

physical id: 0

bus info: pci@0000:05:00.0

logical name: ens3

version:14

serial: 00:1d:72:40:64:2a

capacity:100Mbit/s

width:64bits

clock:33 Mhz

capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 1bt-fd 100bt-fd autonegotiation

configuration: autonegotiaton=on broadcast=yes driver=sky2 driver version= 1.30 latency=0 multicast=yes port=twisted pair

resources: irq:28 memory_f4200000-f4203fff ioport:3000(size=256)




description: Network controller

product: BCM4311 802.11b/g WLAN

vendor: Broadcom Limited

Physical id: 0

bus info: pci@0000:07:00.0

version: 02

width: 64bits

clock 33Mhz

capabilities: pm msi pciexpress bus_master cap_list

configuration: driver=b43-pci-bridge latency=0

resources: irq:19 memory:f4300000-f4303fff


```


Results from lspci:

```
05:00.0 Ethernet controller: Marvell Technology Group LTD. 88e8039 PCI-E Fast Ethernet controller (rev14)

07:00.0 Network controller: broadcom Limited BCM4311 802.11 b/g WLAN (rev 02)


```


Results from iwconfig:

```
ens3   no wireless extensions

lo        no wireless extensions


```


Results from ifconfig:

```
The program 'ifcofig' is currently not installed. You can install it by typing: sudo apt install net-tools


```


Results from sudo apt install net-tools

```
Leyendo lista de paquetes... hecho (reading package list... done)

Creando árbol de dependencias (creating dependecy tree)

Leyendo la información de estado... hecho

E: No se ha podido localizar el paquete net -tools (unable to find net tools package)


```


However i connect ethernet cable (icon shows connected) and  opened 'Connection Information':




```
Active network connections

Wired connection 1 (default)

General 

Interface: Ethernet (ens3)

Hardware Address: 00:01:72:40:64:2a

Driver: sky2

Speed:100 mb/s

security. none

IPv4... (all good i think)

IPv6... (all good i think)


```


I don't understand why interfaces are like ens3 instead wlan# and eth#. I supposed there is a problem. And how i can install ifconfig if i don't have network available!?




any ideas? plz plz plz plz.




Thank you all!

---

### Post by jeremy31 on 2017-07-25
*Thread moved to **Networking & Wireless**.*
See [this post](https://ubuntuforums.org/showthread.php?t=2316978) to get your wireless going

---

### Post by johndough2 on 2017-07-26
Hi

If you can run the excellent script as advised above we may be able to help.

Broadcom is something I would expect to be supported, so please run the script.

---

