---
title: "Wireless worked on first boot, now doesn't"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by Merx on 2008-08-02
Hi

I have just installed Xubuntu 8.04.1. On my first boot I went into System Network and entered the details for my wireless connection (ESSID, WPA Personal, Password, DHCP). The connection started working, I could access the internet although the response seemed quite slow.

Since rebooting after that first boot the wireless connection doesn't work and as a very new newbie I don't know why. Can someone please tell me how to get the wireless connection started and how to have it start automatically?

The lspci command shows my wireless card as follows:

01:09.0 Network controller: RaLink RT2561/RT61 802.11g PCI
        Subsystem: RaLink EW-7108PCg
        Flags: bus master, slow devsel, latency 64, IRQ 10
        Memory at ff8f0000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: <access denied>

The /etc/network/interfaces file is as follows:

auto lo
iface lo inet loopback


iface wlan0 inet dhcp
wpa-psk c50d2d58191f4e6452eee3eac096b17255ef787b0cb6efba145987d1ad1c1416
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid johns

auto wlan0

---

### Post by Merx on 2008-08-03
Found from another post on this forum that I could get my connection back by re-entering my password under System-Network-Wireless Connection.

Then from another post found that installing Wicd as a replacement for Network Manager would make it faster to connect in each session than re-entering my password. There was information on how to have the connection automatically start in Ubuntu but not for Xubuntu so I'll start a new thread to find that out.

---

