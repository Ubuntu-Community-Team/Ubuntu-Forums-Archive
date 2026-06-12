---
title: "Wired Ethernet not connecting to Ubuntu 18.04 server (wifi works)"
date: 2021-02-19
forum: Networking &amp; Wireless
---

### Post by treeeskimo on 2021-02-19
Trying to determine the issue behind why my server (18.04) cannot connect to through the ethernet cable. It was was working fine a few days ago but after I attempted to do some re-wiring, the server could no longer connect to my network. I checked the wiring and did not see anything misplaced and even made sure everything was plugged in properly. What should I be looking for in the machine? Is there something simple I am over looking? My network provider is comcast business. Any help is appreciated. 

Output of ifconfig
```

  eno1: flags=4163<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 10.1.10.201 netmask 255.255.255.0 broadcast 10.1.10.255
        inet6 fe80::a6ba:dbff:fe2e:1c63 prefixlen64 scopeid 0x20<link>
        ether a4:ba:db:2e:1c:63  txqueuelen 1000  (Ethernet)
        RX packets 11617  bytes 1969830 (1.9 MB)
        RX errors 0  dropped 1  overruns 0  frame 0
        TX packets 65450  bytes 4492101 (4.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 36  
  swlo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 302383  bytes 28242833 (28.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 302383  bytes 28242833 (28.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

  eno2: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        
        ether a4:ba:db:2e:1c:65 txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

[COLOR=#000000][FONT=Arial]Output of lshw -C network
[/FONT][/COLOR]```

[SIZE=1][FONT=courier new][COLOR=#000000] *-network:0              [/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       description: Ethernet interface[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       product: NetXtreme II BCM5709 Gigabit Ethernet [/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       vendor: Broadcom Inc. and subsidiaries[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       physical id: 0[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       bus info: pci@0000:01:00.0[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       logical name: en01[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       version: 20[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       serial: a4:ba:db:2e:1c:63[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       capacity: 1Gbit/s[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       width: 64 bits[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       clock: 33MHz[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       capabilities: pm vpd msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       configuration: autonegotiation=on broadcast=yes driver=bnx2 driverversion=2.2.6 duplex=full firmware=17=7.12.19 bc 7.10.0 NCSI 2.0.13 ip=10.1.10.201 latency=0 link=no multicast=yes port=twisted pair[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       resources: irq:32 memory:d6000000-d7ffffff[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new]
[/FONT][/SIZE][SIZE=1][FONT=courier new][COLOR=#000000]*-network:1                      
       description: Ethernet interface[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       product: NetXtreme II BCM5709 Gigabit Ethernet [/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       vendor: Broadcom Inc. and subsidiaries[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       physical id: 0.1[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       bus info: pci@0000:01:00.1[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       logical name: en02[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       version: 20[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       serial: a4:ba:db:2e:1c:65[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       capacity: 1Gbit/s[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       width: 64 bits[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       clock: 33MHz[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       capabilities: pm vpd msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       configuration: autonegotiation=on broadcast=yes driver=bnx2 driverversion=2.2.6 duplex=full firmware=17=7.12.19 bc 7.10.0 NCSI 2.0.13 latency=0 link=no multicast=yes port=twisted pair[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       resources: irq:32 memory:d8000000-d9ffffff[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new]


[/FONT][/SIZE][SIZE=1][FONT=courier new][COLOR=#000000]*-network:0 DISABLED                     
       description: Ethernet interface[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       product: NetXtreme II BCM5709 Gigabit Ethernet [/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       vendor: Broadcom Inc. and subsidiaries[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       physical id: 0.1[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       bus info: pci@0000:01:00.1[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       logical name: en03[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       version: 20[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       serial: a4:ba:db:2e:1c:67[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       capacity: 1Gbit/s[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       width: 64 bits[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=courier new][COLOR=#000000]       clock: 33MHz[/COLOR][/FONT][/SIZE]

```

---

### Post by TheFu on 2021-02-19
If you didn't change the networking on the router and didn't change the settings on the server, then the problem is in the wiring.
[https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) has some steps to see where the issue lies. 
Read it carefully. Do the steps in order.  If you can't ping your router, which is what I expect, it is the wiring.

BTW, when posting, please don't change the fonts.  Use "code tags" in these forums:  [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code) explains how.  Please edit your first post and fix it. Make it easy for people to help you. Please.

---

### Post by treeeskimo on 2021-02-19
Thank you for the advice and the link. I could not ping the router and got the error "unreachable host" so it must be a driver configuration error. How do i proceed?

---

### Post by TheFu on 2021-02-19
> **treeeskimo said:**
> Thank you for the advice and the link. I could not ping the router and got the error "unreachable host" so it must be a driver configuration error. How do i proceed?

Probably not.
CHECK THE WIRING. Try different ports, different wires, check the patch panel.
Any chance the disabled ethernet port is the one with the cable attached? 

In general, there aren't any network config items needed for wired ethernet on servers since servers don't usually switch into low-power modes.

---

