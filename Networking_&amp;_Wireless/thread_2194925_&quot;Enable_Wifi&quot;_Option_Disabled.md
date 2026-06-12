---
title: "&quot;Enable Wifi&quot; Option Disabled"
date: 2013-12-21
forum: Networking &amp; Wireless
---

### Post by frukvt0 on 2013-12-21
So recently I went to a friend's house and tried connecting to their wifi but the "enable wifi" option was disabled. I did some googling and entered a code in the terminal which made it disappear (I don't remember what code(s) I used). Finally today after much searching on google it's come back, but I can't click it. I'd like to add that I'm extremely new to linux.

lshw -c network: 
```
*-network DISABLED      
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: c4:17:fe:45:45:52
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.141 (r415941) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: a4:ba:db:a0:e1:69
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full ip=192.168.1.4 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:f68fc000-f68fffff ioport:de00(size=256)

```

rfkill list: 
```

0: phy1: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

```

ifconfig: 
```

eth0      Link encap:Ethernet  HWaddr a4:ba:db:a0:e1:69  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a6ba:dbff:fea0:e169/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:291534 errors:0 dropped:0 overruns:0 frame:0
          TX packets:216466 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:324613431 (324.6 MB)  TX bytes:80367124 (80.3 MB)
          Interrupt:18 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:221492 errors:0 dropped:0 overruns:0 frame:0
          TX packets:221492 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16950808 (16.9 MB)  TX bytes:16950808 (16.9 MB)

```

iwconfig:
```

lo        no wireless extensions.


eth0      no wireless extensions.


eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

---

### Post by varunendra on 2013-12-22
Welcome to the forums frukvt0 !

While being connected to internet via cable, please do -
```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install firmware-b43-lpphy-installer
```
..then reboot. Do you have a working wifi now?

The first command above will remove the "sta" driver which most of us believe is not correct for this card, and the second command will install the correct firmware for the card which is required by the driver "b43" which we think is the correct one.

If this doesn't help solving the problem, please post back the outputs of -
```
lspci -nnk | grep -iA2 net
rfkill list
dmesg | grep b43
```

---

