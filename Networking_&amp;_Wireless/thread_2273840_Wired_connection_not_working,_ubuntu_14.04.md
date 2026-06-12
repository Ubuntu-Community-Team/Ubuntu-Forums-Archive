---
title: "Wired connection not working, ubuntu 14.04"
date: 2015-04-16
forum: Networking &amp; Wireless
---

### Post by Weijia on 2015-04-16
Wireless works fine without any problem, but the wired connection is not working suddenly. I'm running Ubuntu 14.04. 


Here are some info.
[COLOR=#000000][FONT=fontello]

[/FONT][/COLOR][B]sudo lshw -C network
```
[/B]  *-network       description: Ethernet interface
       product: Ethernet Connection I218-V
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: 68:f7:28:6e:25:a2
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=0.6-4 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:58 memory:f1a00000-f1a1ffff memory:f1a3e000-f1a3efff ioport:4080(size=32)
  *-network DISABLED
       description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 83
       serial: 5c:c5:d4:36:de:a4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-48-generic firmware=22.24.8.0 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:61 memory:f1800000-f1801fff


[B]
```

nm-tool
```
[/B]

NetworkManager Tool


State: disconnected


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             unavailable
  Default:           no
  HW Address:        5C:C5:D4:36:DE:A4


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             disconnected
  Default:           no
  HW Address:        68:F7:28:6E:25:A2


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on




[B]
```

[/B]cat /etc/network/interfaces

```
# interfaces(5) file used by ifup(8) and ifdown(8)auto lo
iface lo inet loopback



```cat /etc/NetworkManager/NetworkManager.conf
```
[main]plugins=ifupdown,keyfile,ofono
dns=dnsmasq


no-auto-default=68:F7:28:6E:25:A2,


[ifupdown]
managed=false



```

---

### Post by michi1983 on 2015-04-16
You could try to open a terminal and then type ```
sudo ifup eth0
``` and then a ```
sudo dhclient eth0
```

---

### Post by Weijia on 2015-04-16
I have tried. but it still not work. It seems something wrong with the server?

---

### Post by michi1983 on 2015-04-17
> **Weijia said:**
> I have tried. but it still not work. It seems something wrong with the server?

Well, it would be cool if you post the output of your terminal when you type in commands so we can see **WHAT** exactly doesn't work ;)

Server? Is your Ubuntu machine connected to a server? If yes, what kind of server? Does it provide you with DHCP and DNS for internet?

---

