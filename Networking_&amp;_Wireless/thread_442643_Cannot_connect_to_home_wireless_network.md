---
title: "Cannot connect to home wireless network"
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by 1llusion on 2007-05-13
Let me start off by saying that I am quite new to ubuntu and linux.  I am currently dual booting XP and ubuntu 6.10.  I am having difficulty connecting to my home network which is using WEP encryption.  I have tried searching around to find a solution, but have wound up quite confused.  I have previously connected to my school's wireless network,  but even that would only work sometimes.

My wireless card is an Intel PROSet/Wireless 3945 ABG and my laptop is a Dell 9400.

I found a post where a user was having difficulty connecting to wireless and another user requested the outputs of the following commands:

```
cat /etc/network/interfaces
ifconfig -a
sudo lshw -C network
iwlist scanning
route -n 
lspci
```

Here are my outputs from those commands,

```
cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
name Wireless LAN card
wireless_mode managed
wireless_essid mynetwork
wireless_key mykey

wireless_channel 11
auto wlan0






iface eth1 inet dhcp
wireless-essid mynetwork
wireless-key mykey

auto eth1
```

```
ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:C5:43:15:70  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 

eth1      Link encap:Ethernet  HWaddr 00:18:DE:0E:17:71  
          inet6 addr: fe80::218:deff:fe0e:1771/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5603 errors:268 dropped:280 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13901 (13.5 KiB)  TX bytes:3964 (3.8 KiB)
          Interrupt:177 Base address:0x2000 Memory:dcfff000-dcffffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:498 errors:0 dropped:0 overruns:0 frame:0
          TX packets:498 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26776 (26.1 KiB)  TX bytes:26776 (26.1 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

```
sudo lshw -C network
*-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0c:00.0
       logical name: eth1
       version: 02
       serial: 00:18:de:0e:17:71
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.1.0mp firmware=13.0 1:0 () link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:dcfff000-dcffffff irq:177
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:43:15:70
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=1.00 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:dcbfe000-dcbfffff irq:177
```

```
iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:90:96:AE:31:B9
                    ESSID:"Grainger Network"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=82/100  Signal level=-52 dBm  Noise level=-52 dBm
                    Extra: Last beacon: 44ms ago

sit0      Interface doesn't support scanning
```

```
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```

```
lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0298 (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:01.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```


Any help at all would be greatly appreciated, as I am unsure of what to do.

Thanks,
Alan

---

### Post by RomeReactor on 2007-05-13
Hi. From the output of **sudo lshw -c network**

```
*-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       ...
       **logical name: eth1**
```

**eth1** is your wireless card's designation; is this card enabled in **System-->Administration-->Network**?

---

### Post by 1llusion on 2007-05-13
I just checked, and the card is enabled.

---

### Post by RomeReactor on 2007-05-13
Just to be clear: in your **/etc/network/interfaces** file, this line:

```
wireless_essid mynetwork
```

actually says this:

```
wireless_essid Grainger Network
```

right? Also, please run

```
sudo dhclient eth1
```

in the terminal and post the output.

---

### Post by 1llusion on 2007-05-13
Yes, the /etc/network/interfaces file has the wireless_essid as Grainger Network, for some reason I changed it when I posted.

The output was;

```
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:18:de:0e:17:71
Sending on   LPF/eth1/00:18:de:0e:17:71
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```


edit-- i just thought that I should add that I can see the network and signal strength, I just cannot connect to it.

---

### Post by RomeReactor on 2007-05-13
Try disabling the wep encryption in your router to see if it lets you connect. Also, Network-Manager hasn't worked for many people (myself included); I had the same symptoms when I did a fresh install of Feisty: Network-Manager would should my router as connected with good signal strength, but never actaully letting me access the net. I would recommend uninstalling it and replacing it with [WICD]("http://wicd.sourceforge.net/"); it works so much better.

---

### Post by chili555 on 2007-05-14
Notice there is a space in the ESSID? I don't believe *iwconfig* handles spaces well, if at all. Please try:```
wireless-essid "Grainger Network"
```Also, I believe the correct format is:```
wireless-key 0123456789abcdef
wireless-essid myrouter1
```and not wireless_key, etc. That is, hyphens and not underscores. My belief is based on my ipw3945 connecting to my WEP network perfectly.

---

### Post by RomeReactor on 2007-05-15
chili555 is right; didn't notice it before...

---

### Post by boonwee on 2007-05-19
hi. i just installed feisty on my new notebook with intel 3945 chipset and i have exactly the same problem described here.

i turned off WEP and turned on SSID broadcast in my router and i still cannot connect. can anyone help me with this as i need wireless to work on this notebook.

my /etc/network/interfaces file:

i[I]face eth1 inet dhcp
wireless-essid myssid
wireless-key mywepkey[/I]


**ifconfig-a:**

[I]eth0      Link encap:Ethernet  HWaddr 00:16:D4:A5:DC:11  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3338 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3230 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:823853 (804.5 KiB)  TX bytes:296525 (289.5 KiB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:19:D2:27:72:FB  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:2147 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:180 (180.0 b)
          Interrupt:17 Base address:0xc000 Memory:e4000000-e4000fff [/I]


**sudo lshw -C network:**

[I]  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5753M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@08:00.0
       logical name: eth0
       version: 21
       serial: 00:16:d4:a5:dc:11
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.72 duplex=full firmware=5753m-v3.56 ip=192.168.1.104 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:e4100000-e410ffff irq:16
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@10:00.0
       logical name: eth1
       version: 02
       serial: 00:19:d2:27:72:fb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () latency=0 link=no multicast=yes wireless=unassociated
       resources: iomemory:e4000000-e4000fff irq:17[/I]


**lspci | grep Intel:**

*10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)*


**sudo dhclient eth1:**

[I]Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:19:d2:27:72:fb
Sending on   LPF/eth1/00:19:d2:27:72:fb
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/I]


i must add that i can see the network and i can see the signal strength at more than 95%. however, it is just not connecting. i have no problems with 2 other windows notebook and 1 other windows desktop connecting to the same router and surfing the net.

---

### Post by chili555 on 2007-05-20
I notice your ethernet interface has an IP address: > eth0 Link encap:Ethernet HWaddr 00:164:A5C:11
inet addr:192.168.1.104 Bcast:192.168.1.255 Mask:255.255.255.0Feisty, by default, installs Network Manager. NM, by design, gives preference to wired connections and will not connect to wireless if wired is available. In order to see if your wireless will work, please detach the cable and do:```
sudo ifdown eth0
```and then try your wireless.

---

### Post by darwin_te on 2007-05-27
Kubuntu 7.04 (Feisty)
ASUS G1

Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

WEP 104-bit (128-bit) setting connecting to Windows AP:

/etc/network/interfaces:

########################
#home - wifi
########################

auto eth1
iface eth1 inet static
address 192.168.1.106
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid youressidhere

# passphrase is test
# see [http://www.powerdog.com/wepkey.cgi](http://www.powerdog.com/wepkey.cgi) (Passphrase To Hexadecimal WEP Keys)
wireless-key1 9FDF3BFDFB10AFEB0925EF9605

wireless-defaultkey 1
wireless-keymode open

command line to bring wireless network up:

>ifup eth1

---

