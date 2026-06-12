---
title: "2 Ubuntu PCs, NIC Crossover - No ping"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by AlefD on 2007-09-23
*** Warning - Quite a long, tedious, post ;-) ***

Hi folks.

First and foremost - thank you all for the great work you're doing here. Kudos.

I'm trying to connect two PCs (one is Pentium 4 {aka P4}, the other id Pentium 3 {aka P3}) to each other, using 2 NICs on one, 1 NIC on the other, crossover cable, while using one of them to connect to the internet. No hub, switch or router. Xubuntu 7.04 on both.

P3, 1 NIC (eth1): 192.168.0.1 - - > P4, 1 NIC (eth0) : 192.168.0.2 - - -> P4 2nd NIC (eth1) by dhcp 172.21.56.94 - -> P4 ppp connection - - -> "hello world"

P3 - one NIC, but with two 'exits' (I think):
eth0 is for an old tv-cable-like (coaxial rg59), which is not in use
eth1 is for a normal network cable (category 5)
static ip (192.168.0.2), mask is 255.255.255.0, getway is 192.168.0.1

P4 - two 'normal' NICs:
eth0 is used to connect to P3
static ip (192.168.0.1), mask is 255.255.255.0
eth1 is used to connect to a modem (ip assigned by dhcp).

Static ip / mask / getway were set-up using the menu, i.e.: "System -> Network".

The modem is like adsl, it connects to the ISP's DHCP, DNS etc, but it doesn't have a static ip and it requies a certain script for authentication, "pptp" it's called, I think. 


I tried each of the three  cards at its turn (P3eth1, P4eth0, P4eth1), using dhcp-assigned-ip (and running authentication scrip)  - and they all, independently ofcourse, could connect to the Internet. i.e. - hardware is okay.

As for P3 eth0/1 - I tried connecting to the internet directly from either eth0 or eth1, while pluging the cable the only place I had. It turns out it's eth1. I disabled eth0 {won't help us even if it's enabled - I tried}

The prob -
P3eth1 cannot ping P4eth0.

I tried 'jugglling' with the cards - changing them and trying all the combinations with both PCs - still no good. Result is alwaus: Internet - yes, Ping between PCs - nope.


Posting all my info:

_**P4, 2 physical NIC, one to P3, the other to the modem**_

lspci
> 00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 05)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS
02:01.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

/etc/network/interfaces
> auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
address 192.168.0.2
netmask 255.255.255.0

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0

auto eth0
(I guess that's what "System -> Network".did. Haven't touched it)


ifconfig
> eth0      Link encap:Ethernet  HWaddr 00:50:BF:0E:30:16  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:bfff:fe0e:3016/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:2850 (2.7 KiB)
          Interrupt:16 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:05:1C:15:0D:76  
          inet addr:172.21.56.94  Bcast:255.255.255.255  Mask:255.255.252.0
          inet6 addr: fe80::205:1cff:fe15:d76/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:733253 errors:0 dropped:0 overruns:0 frame:0
          TX packets:680932 errors:72 dropped:0 overruns:0 carrier:72
          collisions:0 txqueuelen:1000 
          RX bytes:332462641 (317.0 MiB)  TX bytes:253088537 (241.3 MiB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:851 errors:0 dropped:0 overruns:0 frame:0
          TX packets:851 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:56144 (54.8 KiB)  TX bytes:56144 (54.8 KiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:85.64.251.62  P-t-P:212.29.206.206  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1460  Metric:1
          RX packets:291360 errors:0 dropped:0 overruns:0 frame:0
          TX packets:385048 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:164669810 (157.0 MiB)  TX bytes:215881881 (205.8 MiB)

As a last resort, I also tried -
"sudo arp -s 192.168.0.1 00:60:6E:30:0C:31"

arp 
> Address                  HWtype  HWaddress           Flags Mask            Iface
172.21.56.1              ether   00:12:43:AA:2C:95   C                     eth1
192.168.0.1              ether   00:60:6E:30:0C:31   CM                    eth0

netstat -rn

> Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
172.26.255.17   172.21.56.1     255.255.255.255 UGH       0 0          0 eth1
212.29.206.206  0.0.0.0         255.255.255.255 UH        0 0          0 ppp0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
172.21.56.0     0.0.0.0         255.255.252.0   U         0 0          0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth1
0.0.0.0         212.29.206.206  0.0.0.0         UG        0 0          0 ppp0


_**P3, 1 physical NIC, to P4, using crossover cable**_

lspci
> 00:00.0 Host bridge: Silicon Integrated Systems [SiS] 620 Host (rev 02)
00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge) (rev b1)
00:01.1 Class ff00: Silicon Integrated Systems [SiS] ACPI
00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 11)
00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
00:0b.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 10)
00:0f.0 Multimedia audio controller: C-Media Electronics Inc CM8338A (rev 10)
00:10.0 Communication controller: PCTel Inc HSP MicroModem 56 (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 530/620 PCI/AGP VGA Display Adapter (rev 2a)

/etc/network/interfaces
> auto lo
iface lo inet loopback

iface eth1 inet static
address 192.168.0.1
netmask 255.255.255.0
gateway 192.168.0.2

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth1

ifconfig
> eth1      Link encap:Ethernet  HWaddr 00:60:6E:30:0C:31  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::260:6eff:fe30:c31/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:4955 (4.8 KiB)
          Interrupt:12 Base address:0xdc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5440 (5.3 KiB)  TX bytes:5440 (5.3 KiB)


Again i tried arp -
sudo arp -s 192.168.0.2 00:50:1C:15:0D:76

arp
> Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.0.2              ether   00:50:1C:15:0D:75   CM                    eth1

netstat -rn
<returns nothing>

[Is that ok ?]


**_PING ME !_**

Self pings are ok. Like:
> PING 192.168.0.2 (192.168.0.2) 56(84) bytes of data.
64 bytes from 192.168.0.2: icmp_seq=1 ttl=64 time=0.043 ms
64 bytes from 192.168.0.2: icmp_seq=2 ttl=64 time=0.057 ms
64 bytes from 192.168.0.2: icmp_seq=3 ttl=64 time=0.053 ms

--- 192.168.0.2 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.043/0.051/0.057/0.005 ms

[The other one, the P3 / 192.168.0.1, is the same]


Trying to ping to each other:

> PING 192.168.0.2 (192.168.0.2) 56(84) bytes of data.
From 192.168.0.1 icmp_seq=1 Destination Host Unreachable
From 192.168.0.1 icmp_seq=2 Destination Host Unreachable
From 192.168.0.1 icmp_seq=3 Destination Host Unreachable

--- 192.168.0.2 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2010ms
, pipe 3

[Same with P4/192.168.0.2 trying to ping the P3/192.168.0.1]


Lights !
All 3 NICs have, each, 2 leds - "ACT" & "LINK".
On both the P4 and the P3 - "Link" is on, always (only when I connect the cable ofcourse).
Sometimes ACT flashes (on both), for 3 seconds and then stops for a minute or so (and then flashes again, etc).

PS -
Also tried normal, non-crossover cable. Didn't work.
Tried another cross cable. Didn't work.

Help !
;-)

Daniel.

---

### Post by bjd on 2007-09-24
netstat -rn on P3 should have something in it. Now it probably does not know where to send the packets. 

Also in /etc/network/interfaces on P4, the address and netmask under *iface eth1* are a bit redundant and conflicting with eth0. Although i don't think it's causing any trouble now, it's probably better to remove them.

In /etc/network/interface on P3, put the *auto eth1* above the *iface eth1* block.
Not sure if this is necessary, but just for sake of consistency.

Try the above first if it then doesn't work try manually setting routes on P3 (although this should be automatically done by the network init scripts):
*sudo route add -net 192.168.0.0 netmask 255.255.255.0 dev eth1*
*sudo route add default gw 192.168.0.2*

---

### Post by TheGreatFuzzMan on 2007-09-24
> **AlefD said:**
> 
The prob -
P3eth1 cannot ping P4eth0.

I tried 'jugglling' with the cards - changing them and trying all the combinations with both PCs - still no good. Result is alwaus: Internet - yes, Ping between PCs - nope.


So P3 does have an internet connection? If so, it seems like it might just be a firewall issue. Look at the firewall settings on P4. If you are comfortable doing it, take the firewall down, then try the ping. If it works, its a firewall problem. If not, then we might still have a network issue. If its only a firewall problem, it is easy to fix. 

Are you able to ping P3 from P4?

---

### Post by AlefD on 2007-09-24
TheGreatFuzzMan -


No. P4 has internet connection (via nic+modem).
I just wanted to test P3, so I disconnected P4 from the modem and then connected P3 to the modem - the internet on P3 worked. It was just a test. 

iptables -L 
> Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination     

[It's the same for P4 and for P3. No firestarter etc]

As for pinging -

> Trying to ping to each other:

[QUOTE]PING 192.168.0.2 (192.168.0.2) 56(84) bytes of data.
From 192.168.0.1 icmp_seq=1 Destination Host Unreachable
From 192.168.0.1 icmp_seq=2 Destination Host Unreachable
From 192.168.0.1 icmp_seq=3 Destination Host Unreachable

--- 192.168.0.2 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2010ms
, pipe 3 

**[Same with P4/192.168.0.2 trying to ping the P3/192.168.0.1]**[/QUOTE]


____


bjd -


> Also in /etc/network/interfaces on P4, the address and netmask under iface eth1 are a bit redundant and conflicting with eth0. Although i don't think it's causing any trouble now, it's probably better to remove them.

Done. No change.



> In /etc/network/interface on P3, put the auto eth1 above the iface eth1 block.

Result: No network at all, I couldn't even do self-ping.



> sudo route add -net 192.168.0.0 netmask 255.255.255.0 dev eth1
sudo route add default gw 192.168.0.2

Seem to go ok - does not return any message. 
But still no ping between P3 and P4.
Doing netstat on P3 shows no internet connections. [only a list of "unix domain sockets"]



___

Thanx ;-)
Any other thoughts ? 

Are there any other ways to query the NIC ? 
{ Since 'link' led is on, 'act' sometimes flashes - i assume they are able to "talk" to each other.. }

---

