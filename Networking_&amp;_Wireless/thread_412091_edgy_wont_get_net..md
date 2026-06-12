---
title: "edgy wont get net."
date: 2007-04-17
forum: Networking &amp; Wireless
---

### Post by Squeak2 on 2007-04-17
OK, I finally got my comp to run 2 OS's(yay) Well, now I went to System-> Administration -> Networking and went to eth1(Wireless config) and I put in my ESSID (100% accurate) and my WEP (also 100% accurate) I set my wireless settings to Automatic Configuration DHCP, I am also 100% sure that my router reads DHCP(Or was is DCHP, same deal though.) Still won't access my internet. I am using a WMP54GS and I looked on the internet and several guides here and none help. Does my WEP have to be lowercase?(I've been using caps), or do I need drivers updated? 

Thanks to all of those who have enough patience to help me out, Hopefully I can get this to work.

---

### Post by dbott67 on 2007-04-17
The WEP key is case sensitive.  There is an issue with RealTek wireless and ESSID, so posting the output of some of the commands below will help determine if it's the problem.

Additionally, if it's your AP, you can try disabling WEP temporarily to eliminate it as the problem.

Can you post the output of the following commands:
```
dbott@edgy:~$ cat /etc/network/interfaces
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

```
and
```
dbott@edgy:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:40:05:B2:AF:45
                    ESSID:"bott"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:75/100  Signal level:-48 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

sit0      Interface doesn't support scanning.
```
and
```
dbott@edgy:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:C5:0C:AD:05  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:CE:31:88:6F  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe31:886f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1800 errors:0 dropped:0 overruns:0 frame:0
          TX packets:158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:395495 (386.2 KiB)  TX bytes:26231 (25.6 KiB)
          Interrupt:169 Memory:dfcfc000-dfd00000 

```
and
```
dbott@edgy:~$ sudo lshw -C network
Password:
  *-network               
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:ce:31:88:6f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.37 firmware=Broadcom,11/02/2005, 4.10.40.0 ip=192.168.1.105 link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:dfcfc000-dfcfffff irq:169
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:0c:ad:05
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=1.00 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:df9fe000-df9fffff irq:217

```

-Dave

---

