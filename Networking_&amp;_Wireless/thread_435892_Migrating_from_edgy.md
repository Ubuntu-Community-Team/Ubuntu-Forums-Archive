---
title: "Migrating from edgy"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by tmurph6 on 2007-05-07
I clean installed feisty fawn on my computer and it didn't recognize my wireless card, which is odd because edgy always has.  So i clean installed edgy and it didn't recognize my wired connection but it did recognize my wireless card.  I was wondering if I migrated to feisty fawn via an upgrade would it cause my wireless card to not work?  Or is the fact that drivers are installed now on edgy gonna make it work on feisty.  Right now there is no reason to upgrade to feisty fawn because everything is working great, but I would like to be fully upgraded to feisty.

---

### Post by dbott67 on 2007-05-07
Some people have had issues with certain network cards in Feisty.  Can you post the output of the following commands:
```
scpl@dns2:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

``````
scpl@dns2:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:E0:29:7C:65:3F
          inet addr:192.168.128.59  Bcast:192.168.128.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:29ff:fe7c:653f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:732483 errors:0 dropped:0 overruns:0 frame:0
          TX packets:101659 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:352562729 (336.2 MiB)  TX bytes:6776681 (6.4 MiB)
          Interrupt:9 Base address:0x4c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1740 (1.6 KiB)  TX bytes:1740 (1.6 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

``````
scpl@dns2:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

``````
scpl@dns2:~$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: SMC2-1211TX
       vendor: Accton Technology Corporation
       physical id: b
       bus info: pci@02:0b.0
       logical name: eth0
       version: 10
       serial: 00:e0:29:7c:65:3f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.128.59 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:d800-d8ff iomemory:feafbc00-feafbcff irq:9

``````
scpl@dns2:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:e0:29:7c:65:3f arp 1

```*Note: if you can't get online with your system & you have a USB thumb drive (or floppy or some other removable media you can write to) you can use the 'redirect' function to write the output of the commands to a file and then copy them to the USB. Start in your home directory (**cd ~**):*

```
cat /etc/network/interfaces > interfaces.txt
``````
ifconfig -a > ifconfig.txt
``````
iwlist scanning > iwlist.txt
``````
sudo lshw -C network > lshw.txt
``````
cat /etc/iftab > iftab.txt
```Copy all 5 files to floppy/USB, bring them over to Windows and then post them here. All five files should be in your home directory.

-Dave

---

### Post by tmurph6 on 2007-05-07
tim@tim-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid hit and run

tim@tim-desktop:~$ ifconfig -a
lo        Link encap:Local Loopback  tim@tim-desktop:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

wlan0 mac 00:05:5d:99:98:49 arp 1

          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:05:5D:99:98:49  
          inet addr:192.168.1.113  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::205:5dff:fe99:9849/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22401 errors:0 dropped:723 overruns:0 frame:0
          TX packets:18658 errors:31 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27456593 (26.1 MiB)  TX bytes:2665562 (2.5 MiB)
          Interrupt:177 Memory:f894a000-f894a100 

tim@tim-desktop:~$ iwlist scanning
lo        Interface doesn't support scanning.

---

### Post by tmurph6 on 2007-05-07
wlan0     Scan completed :
          Cell 01 - Address: 00:14:BF:0C:61:49
                    ESSID:"apt 134"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:205  Signal level:0  Noise level:92
                    Extra: Last beacon: 3ms ago
          Cell 02 - Address: 00:16:B6:67:7C:30
                    ESSID:"apt233"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:175  Signal level:0  Noise level:1
                    Extra: Last beacon: 675ms ago
          Cell 03 - Address: 00:18:39:DB:5A:8D
                    ESSID:"Ma Boi Mike"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:153  Signal level:0  Noise level:49
                    Extra: Last beacon: 0ms ago

---

### Post by tmurph6 on 2007-05-07
Cell 04 - Address: 00:15:E9:F3:E6:6E
                    ESSID:"The Juggernaut 2: Juggment Day"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54 
                    Quality:139  Signal level:0  Noise level:29
                    Extra: Last beacon: 129ms ago
          Cell 05 - Address: 00:13:10:90:A0:4D
                    ESSID:"bobbylee"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:201  Signal level:0  Noise level:90
                    Extra: Last beacon: 7ms ago
          Cell 06 - Address: 00:16:B6:F2:84:71
                    ESSID:"Danielle"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:217  Signal level:0  Noise level:96
                    Extra: Last beacon: 5ms ago
          Cell 07 - Address: 00:18:39:C4:29:B3
                    ESSID:"Believe"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:203  Signal level:0  Noise level:91
                    Extra: Last beacon: 5ms ago
          Cell 08 - Address: 00:18:39:56:D6:72
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:220  Signal level:0  Noise level:98
                    Extra: Last beacon: 9ms ago
          Cell 09 - Address: 00:16:B6:23:AA:44
                    ESSID:"club124"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:175  Signal level:0  Noise level:50
                    Extra: Last beacon: 117ms ago
          Cell 10 - Address: 00:16:B6:F2:87:A9
                    ESSID:"BEAST322"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:145  Signal level:0  Noise level:33
                    Extra: Last beacon: 9ms ago

---

### Post by tmurph6 on 2007-05-07
Cell 11 - Address: 00:18:39:4A:82:B9
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:141  Signal level:0  Noise level:30
                    Extra: Last beacon: 19ms ago
          Cell 12 - Address: 00:15:E9:D1:68:50
                    ESSID:"dlink"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54 
                    Quality:152  Signal level:0  Noise level:36
                    Extra: Last beacon: 7ms ago
          Cell 13 - Address: 00:14:6C:F6:3D:C0
                    ESSID:"Coons"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54 
                    Quality:129  Signal level:0  Noise level:6
                    Extra: Last beacon: 52ms ago
          Cell 14 - Address: 00:15:E9:7A:54:94
                    ESSID:"thefiremen"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54 
                    Quality:175  Signal level:0  Noise level:1
                    Extra: Last beacon: 66ms ago

---

### Post by tmurph6 on 2007-05-07
sit0      Interface doesn't support scanning.

tim@tim-desktop:~$ sudo lshw -C network
Password:
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@04:00.0
       version: 12
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: iomemory:e8000000-e8003fff ioport:a000-a0ff irq:10
  *-network
       description: Wireless interface
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@05:01.0
       logical name: wlan0
       version: 20
       serial: 00:05:5d:99:98:49
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 ip=192.168.1.113 multicast=yes wireless=802.11b linked
       resources: ioport:b000-b0ff iomemory:ea000000-ea0000ff irq:177
tim@tim-desktop:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

wlan0 mac 00:05:5d:99:98:49 arp 1
tim@tim-desktop:~$

---

### Post by tmurph6 on 2007-05-07
sorry for posting so many times, didn't know how else to do it.  Kind of new at this:lolflag:

---

### Post by dbott67 on 2007-05-07
> **tmurph6 said:**
> sorry for posting so many times, didn't know how else to do it.  Kind of new at this:lolflag:

Just wrap any output with "code" tags (i.e. [COLOR=Red][[/COLOR][COLOR=Blue]tag-name[/COLOR][COLOR=Red]][/COLOR]output goes here[COLOR=Red][/[/COLOR][COLOR=Blue]tag-name[/COLOR][COLOR=Red]][/COLOR] ; replace tag-name with [COLOR=Blue]code [/COLOR]or [COLOR=Blue]quote[COLOR=Black], etc.  Each ***opening*** tag-name is wrapped with square brackets [COLOR=Red][ ][/COLOR], and each ***closing*** tag-name is also wrapped in square brackets, and also includes a forward slash in front of the closing tag-name [COLOR=Red][/ ][/COLOR].

All of my examples were wrapped with 'code' tags.  This is what yours sould look like (notice how much easier it is to read):

[/COLOR][/COLOR]```
tim@tim-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid hit and run
``````

tim@tim-desktop:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:05:5D:99:98:49  
          inet addr:192.168.1.113  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::205:5dff:fe99:9849/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22401 errors:0 dropped:723 overruns:0 frame:0
          TX packets:18658 errors:31 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27456593 (26.1 MiB)  TX bytes:2665562 (2.5 MiB)
          Interrupt:177 Memory:f894a000-f894a100 

``````

tim@tim-desktop:~$ iwlist scanning
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:BF:0C:61:49
                    ESSID:"apt 134"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:6
                    Encryption key:eek:n
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:205  Signal level:0  Noise level:92
                    Extra: Last beacon: 3ms ago
          Cell 02 - Address: 00:16:B6:67:7C:30
                    ESSID:"apt233"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:eek:ff
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:175  Signal level:0  Noise level:1
                    Extra: Last beacon: 675ms ago
          Cell 03 - Address: 00:18:39:grin:B:5A:8D
                    ESSID:"Ma Boi Mike"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:eek:n
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:153  Signal level:0  Noise level:49
                    Extra: Last beacon: 0ms ago
         Cell 04 - Address: 00:15:E9:F3:E6:6E
                    ESSID:"The Juggernaut 2: Juggment Day"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:eek:n
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54 
                    Quality:139  Signal level:0  Noise level:29
                    Extra: Last beacon: 129ms ago
          Cell 05 - Address: 00:13:10:90:A0:4D
                    ESSID:"bobbylee"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:eek:n
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:201  Signal level:0  Noise level:90
                    Extra: Last beacon: 7ms ago
          Cell 06 - Address: 00:16:B6:F2:84:71
                    ESSID:"Danielle"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:eek:n
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:217  Signal level:0  Noise level:96
                    Extra: Last beacon: 5ms ago
          Cell 07 - Address: 00:18:39:C4:29:B3
                    ESSID:"Believe"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:eek:n
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:203  Signal level:0  Noise level:91
                    Extra: Last beacon: 5ms ago
          Cell 08 - Address: 00:18:39:56:grin:6:72
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:eek:ff
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:220  Signal level:0  Noise level:98
                    Extra: Last beacon: 9ms ago
          Cell 09 - Address: 00:16:B6:23:AA:44
                    ESSID:"club124"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:eek:n
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:175  Signal level:0  Noise level:50
                    Extra: Last beacon: 117ms ago
          Cell 10 - Address: 00:16:B6:F2:87:A9
                    ESSID:"BEAST322"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:eek:n
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:145  Signal level:0  Noise level:33
                    Extra: Last beacon: 9ms ago
         Cell 11 - Address: 00:18:39:4A:82:B9
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:eek:ff
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:141  Signal level:0  Noise level:30
                    Extra: Last beacon: 19ms ago
          Cell 12 - Address: 00:15:E9:grin:1:68:50
                    ESSID:"dlink"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:eek:ff
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54 
                    Quality:152  Signal level:0  Noise level:36
                    Extra: Last beacon: 7ms ago
          Cell 13 - Address: 00:14:6C:F6:3D:C0
                    ESSID:"Coons"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:eek:n
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54 
                    Quality:129  Signal level:0  Noise level:6
                    Extra: Last beacon: 52ms ago
          Cell 14 - Address: 00:15:E9:7A:54:94
                    ESSID:"thefiremen"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:eek:n
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54 
                    Quality:175  Signal level:0  Noise level:1
                    Extra: Last beacon: 66ms ago
sit0      Interface doesn't support scanning.

``````

tim@tim-desktop:~$ sudo lshw -C network
Password:
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@04:00.0
       version: 12
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: iomemory:e8000000-e8003fff ioport:a000-a0ff irq:10
  *-network
       description: Wireless interface
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@05:01.0
       logical name: wlan0
       version: 20
       serial: 00:05:5d:99:98:49
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 ip=192.168.1.113 multicast=yes wireless=802.11b linked
       resources: ioport:b000-b0ff iomemory:ea000000-ea0000ff irq:177

``````

tim@tim-desktop:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

wlan0 mac 00:05:5d:99:98:49 arp 1
```Anyhow, give me a bit to go over the output & I'll get back to you.

-Dave

---

### Post by dbott67 on 2007-05-07
Did the wired connection ever work in Edgy?

There are some issues with drivers in Edgy & Feisty that others have experienced.  Your best bet is to search the forums using some combination of the chipset, driver & make/model of the card.  You might also want to add Feisty or Edgy to the search term to narrow the scope.

For example, "rtl8180 edgy" returns this:
[http://ubuntuforums.org/search.php?searchid=19684953](http://ubuntuforums.org/search.php?searchid=19684953)

While "rtl8180 feisty" returns this:
[http://ubuntuforums.org/search.php?searchid=19685055](http://ubuntuforums.org/search.php?searchid=19685055)

As for the wired interface, we need to dig a little more.  Can you post the output of:
```
dbott@feisty:~$ sudo lspci -nn
Password:
00:00.0 Host bridge [0600]: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge [8086:1a30] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge [8086:1a31] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 12)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801BA ISA Bridge (LPC) [8086:2440] (rev 12)
00:1f.1 IDE interface [0101]: Intel Corporation 82801BA IDE U100 [8086:244b] (rev 12)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB (Hub #1) [8086:2442] (rev 12)
00:1f.3 SMBus [0c05]: Intel Corporation 82801BA/BAM SMBus [8086:2443] (rev 12)
00:1f.4 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB (Hub #2) [8086:2444] (rev 12)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 AP [Radeon 9600] [1002:4150]
01:00.1 Display controller [0380]: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary) [1002:4170]
02:0a.0 Multimedia audio controller [0401]: Creative Labs SB Live! EMU10k1 [1102:0002] (rev 07)
02:0a.1 Input device controller [0980]: Creative Labs SB Live! Game Port [1102:7002] (rev 07)
[COLOR=Red]02:0b.0 Ethernet controller [0200]: D-Link System Inc RTL8139 Ethernet [1186:1300] (rev 10)[/COLOR]
02:0d.0 USB Controller [0c03]: ALi Corporation USB 1.1 Controller [10b9:5237] (rev 03)
02:0d.1 USB Controller [0c03]: ALi Corporation USB 1.1 Controller [10b9:5237] (rev 03)
02:0d.2 USB Controller [0c03]: ALi Corporation USB 1.1 Controller [10b9:5237] (rev 03)
02:0d.3 USB Controller [0c03]: ALi Corporation USB 2.0 Controller [10b9:5239] (rev 01)

```

We're looking for the Ethernet information.

-Dave

---

### Post by tmurph6 on 2007-05-07
the wired does not work in edgy however it does work in feisty

---

