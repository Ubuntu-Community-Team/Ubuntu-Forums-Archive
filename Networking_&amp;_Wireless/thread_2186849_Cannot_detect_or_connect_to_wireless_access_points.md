---
title: "Cannot detect or connect to wireless access points after reboot"
date: 2013-11-09
forum: Networking &amp; Wireless
---

### Post by mackycastillo on 2013-11-09
Currently using a MacBook Pro 8-1 on Ubuntu 12.10 and this is the first time this has ever happened since I installed 12.04 on it years ago.

After a few hours of TF2, I decided to do a regular reboot when our router somehow went to factory settings, Fixed that by using a wired connection to the router and backup settings for the router, so that's taken care of. After the reboot, the laptop won't automatically connect to my wireless network anymore and the network dropdown menu in the panel cannot detect any wireless network in the area.

iwconfig still detects wlan0:

```
[SIZE=2][FONT=courier new]wlan0     IEEE 802.11bg  ESSID:off/any  [/FONT][/SIZE]
[SIZE=2][FONT=courier new]          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   [/FONT][/SIZE]
[SIZE=2][FONT=courier new]          Retry  long limit:7   RTS thr:off   Fragment thr:off[/FONT][/SIZE]
[SIZE=2][FONT=courier new]          Power Management:off[/FONT][/SIZE]
```
          
lshw shows this:

```
[SIZE=2][FONT=courier new]$ sudo lshw -C network[/FONT][/SIZE]
[SIZE=2][FONT=courier new]  *-network               [/FONT][/SIZE]
[SIZE=2][FONT=courier new]       description: Ethernet interface[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       product: NetXtreme BCM57765 Gigabit Ethernet PCIe[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       vendor: Broadcom Corporation[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       physical id: 0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       bus info: pci@0000:02:00.0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       logical name: eth0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       version: 10[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       serial: c8:2a:14:19:93:7b[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       size: 100Mbit/s[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       capacity: 1Gbit/s[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       width: 64 bits[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       clock: 33MHz[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.125 duplex=full firmware=57765-v1.37 ip=192.168.1.34 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       resources: irq:16 memory:a0400000-a040ffff memory:a0410000-a041ffff[/FONT][/SIZE]
[SIZE=2][FONT=courier new]  *-network[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       description: Network controller[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       product: BCM4331 802.11a/b/g/n[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       vendor: Broadcom Corporation[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       physical id: 0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       bus info: pci@0000:03:00.0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       version: 02[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       width: 64 bits[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       clock: 33MHz[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       capabilities: pm msi pciexpress bus_master cap_list[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       configuration: driver=bcma-pci-bridge latency=0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       resources: irq:17 memory:a0600000-a0603fff[/FONT][/SIZE]
[SIZE=2][FONT=courier new]  *-network[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       description: Wireless interface[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       physical id: 2[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       logical name: wlan0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       serial: e0:f8:47:38:71:96[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       capabilities: ethernet physical wireless[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       configuration: broadcast=yes driver=b43 multicast=yes wireless=IEEE 802.11bg[/FONT][/SIZE]

```


Doesn't seem to be blocked:

```
[SIZE=2][FONT=courier new]$ rfkill list[/FONT][/SIZE]
[SIZE=2][FONT=courier new]0: hci0: Bluetooth[/FONT][/SIZE]
[SIZE=2][FONT=courier new]    Soft blocked: yes[/FONT][/SIZE]
[SIZE=2][FONT=courier new]    Hard blocked: no[/FONT][/SIZE]
[SIZE=2][FONT=courier new]2: phy0: Wireless LAN[/FONT][/SIZE]
[SIZE=2][FONT=courier new]    Soft blocked: no[/FONT][/SIZE]
[SIZE=2][FONT=courier new]    Hard blocked: no[/FONT][/SIZE]
```

But it still can't scan anything:

```
[SIZE=2][FONT=courier new]$ sudo iwlist scan[/FONT][/SIZE]
[SIZE=2][FONT=courier new]eth0      Interface doesn't support scanning.[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]lo        Interface doesn't support scanning.[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]virbr0    Interface doesn't support scanning.[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]wlan0     No scan results[/FONT][/SIZE]
```

I tried "modprobe -r b43" and then "modprobe b43" and still nothing.

nm-tool says it's disconnected, but I don't know how to connect it back.

```
[SIZE=2][FONT=courier new]$ nm-tool[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]NetworkManager Tool[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]State: connected (global)[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]- Device: wlan0 ----------------------------------------------------------------[/FONT][/SIZE]
[SIZE=2][FONT=courier new]  Type:              802.11 WiFi[/FONT][/SIZE]
[SIZE=2][FONT=courier new]  Driver:            b43[/FONT][/SIZE]
[SIZE=2][FONT=courier new]  State:             disconnected[/FONT][/SIZE]
[SIZE=2][FONT=courier new]  Default:           no[/FONT][/SIZE]
[SIZE=2][FONT=courier new]  HW Address:        E0:F8:47:38:71:96[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]  Capabilities:[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]  Wireless Properties[/FONT][/SIZE]
[SIZE=2][FONT=courier new]    WEP Encryption:  yes[/FONT][/SIZE]
[SIZE=2][FONT=courier new]    WPA Encryption:  yes[/FONT][/SIZE]
[SIZE=2][FONT=courier new]    WPA2 Encryption: yes[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]  Wireless Access Points [/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]- Device: eth0  [Auto Ethernet] ------------------------------------------------[/FONT][/SIZE]
[SIZE=2][FONT=courier new]  Type:              Wired[/FONT][/SIZE]
[SIZE=2][FONT=courier new]  Driver:            tg3[/FONT][/SIZE]
[SIZE=2][FONT=courier new]  State:             connected[/FONT][/SIZE]
[SIZE=2][FONT=courier new]  Default:           yes[/FONT][/SIZE]
[SIZE=2][FONT=courier new]  HW Address:        C8:2A:14:19:93:7B[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]  Capabilities:[/FONT][/SIZE]
[SIZE=2][FONT=courier new]    Carrier Detect:  yes[/FONT][/SIZE]
[SIZE=2][FONT=courier new]    Speed:           100 Mb/s[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]  Wired Properties[/FONT][/SIZE]
[SIZE=2][FONT=courier new]    Carrier:         on[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]  IPv4 Settings:[/FONT][/SIZE]
[SIZE=2][FONT=courier new]    Address:         192.168.1.34[/FONT][/SIZE]
[SIZE=2][FONT=courier new]    Prefix:          24 (255.255.255.0)[/FONT][/SIZE]
[SIZE=2][FONT=courier new]    Gateway:         192.168.1.1[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]    DNS:             192.168.1.1[/FONT][/SIZE]

```[SIZE=2][FONT=courier new]
[/FONT][/SIZE]



I have this launcher on my top panel (on GNOME2) that I put so that it does:

```
nmcli nm wifi off
nmcli nm wifi on
```

whenever I get disconnected to the internet (either while on TF2, DOTA 2, or just regular browsing) yet turning wifi on or off with nmcli still doesn't work.

Need help please.

[EDIT]
Weird. Last night, while trying to fix the problem, I tried doing various fixes which required rebooting multiple times. After shutting down (without making any changes from before), I slept and turned the laptop on first thing in the morning. It can now scan for and access wireless networks. I'll try to find out what happened in the meantime.

---

