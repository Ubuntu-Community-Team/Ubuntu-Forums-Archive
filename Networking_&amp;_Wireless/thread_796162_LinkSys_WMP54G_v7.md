---
title: "LinkSys WMP54G v7"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by MrBrand on 2008-05-16
Hello @all,
i have a problem with the wireless pci card of Linksys.

```
lspci | grep RaLink
```

answer

```
03:01.0 Network controller: RaLink RT2561/RT61 802.11g PCI
```

```
ifconfig
```

answer
```
eth0      Link encap:Ethernet  Hardware Adresse 00:19:db:f7:3f:dc 
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:253 Basisadresse:0x8000

lo        Link encap:Lokale Schleife 
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:4298 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4298 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0
          RX bytes:214900 (209.8 KB)  TX bytes:214900 (209.8 KB)

wlan0     Link encap:Ethernet  Hardware Adresse xxxxxxxx 
          inet Adresse:xxxxxxxx7  Bcast:xxxxxxxxxx5  Maske:xxxxxxxxxx0
          inet6-Adresse: fe80::21b:11ff:feb4:e707/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:118 errors:0 dropped:0 overruns:0 frame:0
          TX packets:196 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:82157 (80.2 KB)  TX bytes:43044 (42.0 KB)

wmaster0  Link encap:UNSPEC  Hardware Adresse xxxxxxxxxxxxxx
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
```

```
iwconfig
```

answer
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"xxxxxxx" 
          Mode:Managed  Frequency:2.437 GHz  Access Point: xxxx   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=50/100  Signal level=-56 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
```

So if I understand correctly is the pci card has been recognized and has a RaLink chip RT61
However, it is to me neither Ifconfig still under Iwconfig as an interface.

Somebody have any idea?
An addition:
I once looked to these instructions: 

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61")

And then, when I go to the search module rt67 I dont find it. For me it is rt61pci Here are the query

```
modinfo rt61pci
```

answer:
```
filename:       /lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
license:        GPL
firmware:       rt2661.bin
firmware:       rt2561s.bin
firmware:       rt2561.bin
description:    Ralink RT61 PCI & PCMCIA Wireless LAN driver.
version:        2.0.10
author:         http://rt2x00.serialmonkey.com
srcversion:     D71C36F67F7A0F8B005A78F
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2x00pci,mac80211,eeprom_93cx6
vermagic:       2.6.24-16-generic SMP mod_unload
```

I should just follow the instructions to the latest Ralink drivers?
Or rather could lead to problems?

---

### Post by chili555 on 2008-05-16
> However, it is to me neither Ifconfig still under Iwconfig as an interface.I don't understand this at all. Can you please explain?

I think I *do* understand this from ifconfig:```
wlan0     Link encap:Ethernet  Hardware Adresse xxxxxxxx 
          inet Adresse:xxxxxxxx7  Bcast:xxxxxxxxxx5  Maske:xxxxxxxxxx0
          RX bytes:82157 (80.2 KB)  TX bytes:43044 (42.0 KB)
```and this, from iwconfig:```
wlan0     IEEE 802.11g  ESSID:"xxxxxxx" 
          Mode:Managed  Frequency:2.437 GHz  Access Point: xxxx  
```They both suggest you are connected and have an IP address. The only thing I see I might change is:```
Bit Rate=1 Mb/s
```If you are surfing the web, I'm sure it's sloooowwwww! Please try```
sudo iwconfig wlan0 rate auto
```I wouldn't be looking for new drivers if I could connect out of the box!

---

### Post by MrBrand on 2008-05-17
Sorry,
the interface wlan0 is an other uinterfsce. Is an Dlink USb Stick that i use at one moment.
 You can find the PCI card if you serch it.
But i dont find an interface of it.

thats my problem.

and one failure more.
I have an WMP54G v4.5 not v7, sorry.

I have tested ndiswrapper but it is not possible tu use the card.
The driver is installed already, but i dont find the card as interface.

---

### Post by chili555 on 2008-05-17
Network Manager, which is installed by default, will not like two interfaces with two IP addresses at one time. Neither will your computer, unless you are connection sharing and one of the cards supports ap mode. Not all do. Please detach the D-Link USB and do:```
sudo modprobe rt61pci
sudo lshw -C network
iwconfig
```Let us know.

---

### Post by MrBrand on 2008-05-20
Sorry, i have many much work last time.
Well i have do it and thats the result:

at first
```
sudo modprobe rt61pci
```

no failure

```
sudo lshw -C network
```

answer
```
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:19:db:f7:3f:dc
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network:0 UNCLAIMED
       description: Network controller
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
  *-network:1
       description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 10
       serial: 00:19:db:f7:3f:dd
       size: 10MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=10MB/s
```

```
iwconfig
```

answer
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.
```

Now, you can see my Problem?
The card is ready and the system knows the card, but i don't have an wireless interface!

---

