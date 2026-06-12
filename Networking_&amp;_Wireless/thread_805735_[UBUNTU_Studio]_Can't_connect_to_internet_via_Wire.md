---
title: "[UBUNTU Studio] Can't connect to internet via Wireless"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by DivinityX on 2008-05-24
So I just installed UBUNTU Studio 8.04 on my computer and I'm lovin everything about it except...I don't know how to connect to the internet, much less my router...someone please help me out

I have a:
Linksys Compact Wireless-G USB Adapter
Linksys Wireless router in my other room, with no password security

also, could someone explain to me why it's so much easier to connect with plain UBUNTU rather than UBUNTU Studio?

---

### Post by mapes12 on 2008-05-24
We'll need to have a look at some things first. Please post the output to:

```
sudo lshw -C network

```
```
cat /etc/resolv.conf
```

```
ifconfig
```

```
iwconfig
```

```
iwlist scan
```
```

cat /etc/network/interfaces
```

Place the output in quote marks please. 4th button in from right on toolbar.

---

### Post by DivinityX on 2008-05-24
OK I ran the codes on terminal, this is what i got...

Code:

sudo lshw -C network

	> RESPONSE = [sudo] password for divinity: 
		(it won't let me type anything)

Code:

cat /etc/resolv.conf

	> RESPONSE = cat: /etc/resolv.conf: No such file or directory

Code:

ifconfig

	> RESPONSE = lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2798 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2798 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:140092 (136.8 KB)  TX bytes:140092 (136.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:39:12:00:27  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:18:39:12:00:27  
          inet addr:169.254.1.132  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-18-39-12-00-27-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Code:

iwconfig

	> RESPONSE = lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Cody's comp"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



Code:

iwlist scan

	> RESPONSE = lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results


Code:

cat /etc/network/interfaces

	> RESPONSE = # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface wlan0 inet ipv4ll
wireless-essid Cody's comp

auto wlan0

---

### Post by mapes12 on 2008-05-24
> So I just installed UBUNTU Studio 8.04 on my computer

The output you have posted (thanks!) does not look good. Did you have this machine running OK (i.e access to internet) under a previous version of Ubuntu?

---

### Post by DivinityX on 2008-05-24
Normal UBUNTU (which i'm running right now) is just fine. My computer has 3 Hard Drives, a 20, 40 and 80 gig, which each have an OS on them...

(Pri. Master) 20G = Windows XP Pro

(Sec. Master) 40G = UBUNTU 8.04 & UBUNTU Studio 8.04

(Pri. Slave)  80G = Windows XP pro

By defalut, UBUNTU Studio runs. (which I do not want to happen)

On the 20G I've been experincing major slow down but I believe that is due to the lack of mem left on the HD, Internet works fine. Doesn't always want to shutdown, very few crashes

On the 40G, it has been partitioned in half to put two OSs on there, UBUNTU works fine, it has a tendency to freeze (Which I believe is because of RAM or Graphics card) rarely the screen goes black and the sound cuts off but the computer still runs (or at least it sounds like it does) Internet works great.

On the 80G, I haven't used its OS in awhile, because I only have it for storage and back up, but it works perfectly fine along with the internet.

So yeah, in case you need to know, here's the other Hardware on the computer...

RAM = 1GB
CPU = 3GHz (Intel Pentium IV)
Video Card = (not quite sure, I lost the info, but I know it's ATI and it works pretty well in my standards...)

I hope this info helps...

---

### Post by pablodamon on 2008-05-24
it worked b4

---

### Post by fongoo on 2010-11-29
Thanks so much guys helped alot :)

---

### Post by buc1 on 2010-12-21
i am having the same problem.  I can hardwire in but cannot get wireless access.  I can see the my network but everytime i try to connect, i get connection failed cannot obtain ip address.  I am using ubuntu 10.10 and this is the first time i have used a linux os. I have read some of the posts so maybe some of this info can.  I have been trying to figure this out for two days.  It's really beating me down. 
 *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 10
       bus info: pci@0000:00:10.0
       logical name: eth0
       version: 10
       serial: 08:00:46:59:12:47
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.0.0.4 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:10 ioport:1800(size=256) memory:e8004800-e80048ff
  *-network
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 02
       serial: 00:1d:7e:f0:de:c5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lsbcmnds driverversion=1.56+Linksys, A Division of Cisc latency=64 link=no multicast=yes wireless=IEEE 802.11g
       resources: irq:10 memory:2c000000-2c001fff
carlos@carlos-PCG-FXA49-UC:~$ 
carlos@carlos-PCG-FXA49-UC:~$ cat /etc/resolv.conf
nameserver 10.0.0.1
carlos@carlos-PCG-FXA49-UC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:46:59:12:47  
          inet addr:10.0.0.4  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:46ff:fe59:1247/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:548 errors:0 dropped:0 overruns:0 frame:0
          TX packets:582 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:240761 (240.7 KB)  TX bytes:169454 (169.4 KB)
          Interrupt:10 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1d:7e:f0:de:c5  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Memory:2c000000-2c002000 

carlos@carlos-PCG-FXA49-UC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSIDff/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Managementff
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

carlos@carlos-PCG-FXA49-UC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSIDff/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Managementff
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

carlos@carlos-PCG-FXA49-UC:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:24:56:C0:2E:51
                    ESSID:"2WIRE572"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:1B:2F:52:336
                    ESSID:"BUCGEAR"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:1E:E5:2F:50:F5
                    ESSID:"Digital.net"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:1CF:20:B7:53
                    ESSID:"Belkin_N_Wireless_20B753"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:50/100  Signal level:-64 dBm  Noise level:-96 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: 3C:EA:4F281
                    ESSID:"2WIRE374"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 
                    Quality:50/100  Signal level:-64 dBm  Noise level:-96 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100 *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 10
       bus info: pci@0000:00:10.0
       logical name: eth0
       version: 10
       serial: 08:00:46:59:12:47
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.0.0.4 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:10 ioport:1800(size=256) memory:e8004800-e80048ff
  *-network
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 02
       serial: 00:1d:7e:f0:de:c5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lsbcmnds driverversion=1.56+Linksys, A Division of Cisc latency=64 link=no multicast=yes wireless=IEEE 802.11g
       resources: irq:10 memory:2c000000-2c001fff
carlos@carlos-PCG-FXA49-UC:~$ 
carlos@carlos-PCG-FXA49-UC:~$ cat /etc/resolv.conf
nameserver 10.0.0.1
carlos@carlos-PCG-FXA49-UC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:46:59:12:47  
          inet addr:10.0.0.4  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:46ff:fe59:1247/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:548 errors:0 dropped:0 overruns:0 frame:0
          TX packets:582 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:240761 (240.7 KB)  TX bytes:169454 (169.4 KB)
          Interrupt:10 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1d:7e:f0:de:c5  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Memory:2c000000-2c002000 

carlos@carlos-PCG-FXA49-UC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSIDff/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Managementff
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

carlos@carlos-PCG-FXA49-UC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSIDff/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Managementff
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

carlos@carlos-PCG-FXA49-UC:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:24:56:C0:2E:51
                    ESSID:"2WIRE572"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:1B:2F:52:336
                    ESSID:"BUCGEAR"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:1E:E5:2F:50:F5
                    ESSID:"Digital.net"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:1CF:20:B7:53
                    ESSID:"Belkin_N_Wireless_20B753"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:50/100  Signal level:-64 dBm  Noise level:-96 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: 3C:EA:4F281
                    ESSID:"2WIRE374"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 
                    Quality:50/100  Signal level:-64 dBm  Noise level:-96 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0 *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 10
       bus info: pci@0000:00:10.0
       logical name: eth0
       version: 10
       serial: 08:00:46:59:12:47
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.0.0.4 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:10 ioport:1800(size=256) memory:e8004800-e80048ff
  *-network
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 02
       serial: 00:1d:7e:f0:de:c5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lsbcmnds driverversion=1.56+Linksys, A Division of Cisc latency=64 link=no multicast=yes wireless=IEEE 802.11g
       resources: irq:10 memory:2c000000-2c001fff
carlos@carlos-PCG-FXA49-UC:~$ 
carlos@carlos-PCG-FXA49-UC:~$ cat /etc/resolv.conf
nameserver 10.0.0.1
carlos@carlos-PCG-FXA49-UC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:46:59:12:47  
          inet addr:10.0.0.4  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:46ff:fe59:1247/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:548 errors:0 dropped:0 overruns:0 frame:0
          TX packets:582 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:240761 (240.7 KB)  TX bytes:169454 (169.4 KB)
          Interrupt:10 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1d:7e:f0:de:c5  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Memory:2c000000-2c002000 

carlos@carlos-PCG-FXA49-UC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSIDff/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Managementff
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

carlos@carlos-PCG-FXA49-UC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSIDff/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Managementff
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

carlos@carlos-PCG-FXA49-UC:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:24:56:C0:2E:51
                    ESSID:"2WIRE572"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:1B:2F:52:336
                    ESSID:"BUCGEAR"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:1E:E5:2F:50:F5
                    ESSID:"Digital.net"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:1CF:20:B7:53
                    ESSID:"Belkin_N_Wireless_20B753"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:50/100  Signal level:-64 dBm  Noise level:-96 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: 3C:EA:4F281
                    ESSID:"2WIRE374"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 
                    Quality:50/100  Signal level:-64 dBm  Noise level:-96 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

carlos@carlos-PCG-FXA49-UC:~$ cat /etc/network/interfaces
auto lo

                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

carlos@carlos-PCG-FXA49-UC:~$ cat /etc/network/interfaces
auto lo

                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

carlos@carlos-PCG-FXA49-UC:~$ cat /etc/network/interfaces
auto lo   
Any help would greatly appreciated.  Thank you

---

