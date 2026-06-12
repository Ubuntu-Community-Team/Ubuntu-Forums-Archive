---
title: "ubuntu server 13.04 (desktop install) NETWORK PRIORITY"
date: 2013-10-14
forum: Networking &amp; Wireless
---

### Post by KELLOGGVOIDS on 2013-10-14
I installed using the server ISO because I wanted to create a dual boot with windows 7 and a LUKS LVM encrypted partition. I succeeded. The thing is, I had to do some things manually, and that's fine. 
If I installed the regular 13.04 desktop iso, the wireless icon can come up on the top right, no matter what location I am. I do not want to connect to a specific network with a static, I just want the wireless symbol to come so I can connect to whatever I want.
The thing is, when I installed using the server 13.04 iso, I had an ethernet plugged in, and I picked that one during the installation.

Now if I don't have the ethernet plugged in, during boot after my crypt key it says: "waiting for network configuration..." "waiting up to 60 more seconds for network configuration..."  "booting system without full network configuration"
Now, it still loads. I login. When I come to the desktop, the wireless icon takes a long time to show up on the top right. (not more than 5 min)
I understand that there are many posts about this, but the one's ive seen all give solutions for static ip's on specific networks in the interfaces file.

here is my interfaces file:

[B]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp



[/B]and i also have this command:
_sudo lshw -C network_


  [B]*-network               
       description: Ethernet interface
       product: QCA8171 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 13
       serial: xxxxxxxxxxxx [/B](purposely removed)[B]
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx driverversion=1.2.3 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:f0100000-f013ffff ioport:2000(size=128)

  *-network
       description: Wireless interface
       product: AR9462 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: xxxxxxxxxxxxxx
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.8.0-31-generic firmware=N/A ip=192.168.1.7 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:f0000000-f007ffff memory:f0400000-f040ffff
[/B]

---

### Post by KELLOGGVOIDS on 2013-10-17
i erased this part 

[B]auto eth0
iface eth0 inet dhcp

[/B]it works

---

