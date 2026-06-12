---
title: "UNCLAIMED wireless network card. Atheros"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by lukemack on 2007-11-15
I would like to get my wireless card working in Ubuntu 7.10. I have been putting this off as I had such a nightmare last time with a broadcom card.

lshw gives me:


 *-network:1 UNCLAIMED
                description: Ethernet controller
                product: AR5212/AR5213 Multiprotocol MAC/baseband processor
                vendor: Atheros Communications, Inc.
                physical id: 2
                bus info: pci@0000:02:02.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64 maxlatency=28 mingnt=10

It shows up if I do an lspci too.

iwconfig - no wireless extensions.

modprobe ath_pci
FATAL: Module ath_pci not found.


I have read many posts on the forums regarding getting this card to work but can't seem to find a definitive answer. I have installed the restricted modules for my kernel and rebooted - this made no difference.

can anyone tell me if I need to use the madwifi drivers to get this card working? I have installed madwifi-tools, again - no difference.

uname-r - 2.6.22-14-server

many thanks for any assistance. 

luke.

---

### Post by rustybronco on 2007-11-15
Cant help much, try...  [http://madwifi.org/](http://madwifi.org/) 
if you know your wireless card they tell you if its supported.
> uname-r - 2.6.22-14-server a server install?

---

### Post by lukemack on 2007-11-16
I resolved this by compiling and installing madwifi from source (instructions elsewhere on this forum). The card was then recognised.

To get connected (including WPA encryption), I installed network manager (sudo apt-get network-manager-gnome), rebooted and then used network manager to configure the connection.

I didn't have to manually edit the etc/network/interfaces or wpa_supplicant.conf file. It 'just worked' (eventually).

Card type - Atheros 5212/5213 (Netgear). Ubuntu SERVER 7.10

---

### Post by squideekie on 2008-01-21
Could you post links to how to do this? I am having the same problem

Thanks in advance

---

### Post by lukemack on 2008-01-22
I did this a long time ago so not 100% sure. If you still need help then PM me.

---

