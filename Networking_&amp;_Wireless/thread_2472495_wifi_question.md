---
title: "wifi question"
date: 2022-02-28
forum: Networking &amp; Wireless
---

### Post by jgw on 2022-02-28
I was messing with this system and checked the settings for wifi.  It was strange (haven't paid much attention as it works).
Anyway, usually I just let the settings do what they do.  I usually will connect with SBG6900AC-C8DC7 and then the settings program puts a little check mark after it so I know what wifi I am using.  There are about 30 listed but I only am using this one.  Then I noticed that there was a setting for Realtek Wi-Fi to be turned on (normally its not).  So I turned it on.  I remain connected but now there is no checked wi-fi in the visible network list.  I thought that kinda strange but, again, everything is working.  

Here is lshw -C network results:
```
sudo lshw -C network
[sudo] password for greg: 
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.lshw -C network
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 06
       serial: 40:8d:5c:4d:8d:8e
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.13.0-30-generic firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:30 ioport:e000(size=256) memory:fea00000-fea00fff memory:d0800000-d0803fff
  *-network:0
       description: Wireless interface
       physical id: 1
       bus info: usb@2:5.4.2
       logical name: wlx008736326fa1
       serial: 00:87:36:32:6f:a1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=mt7601u driverversion=5.13.0-30-generic firmware=N/A ip=192.168.0.4 link=yes multicast=yes wireless=IEEE 802.11
  *-network:1
       description: Wireless interface
       physical id: 2
       bus info: usb@8:2
       logical name: wlxa09f10be0951
       serial: a0:9f:10:be:09:51
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl88x2bu driverversion=5.13.0-30-generic multicast=yes wireless=unassociated
greg@movies:~$ 
```

Anyway, again, everything seems to be working fine.  My question is whether I should turn off the Realtek thing or not.  I also am not really sure which WiFi I am using (am I using mine or somebody else's?)

Thank you...................

---

### Post by morrownr on 2022-03-01
Hi jgw,

It appears that you have two USB WiFi adapters.

driver=mt7601u - this one is a N150 adapter with a Mediatek chipset and it uses an in-kernel driver which means it plug and play...  no need to install a driver. It is connected. You are using this adapter.

driver=rtl88x2bu - this one is an AC1200 adapter with a Realtek chipset and it requires a driver to be installed. It is not connected.

There are probably some wireless tutorials available.

---

