---
title: "wireless network error"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by daniel@danielberg.no on 2008-07-28
Hi all,

I have been using Ubuntu for some time now and I am very pleased with it. I am currently running Ubuntu 7.10 Gutsy Gibbon on my Lenovo T60. I was recently trying to connect to the internet through my Nokia N73 mobile phone and followed some hints at various forum pages. Somewhere along the way I must have made some changes to some file that I shouldn't have. I have been away for some weeks (holidays) since and hence I don't remember exactly what I did, I think I changed the /etc/bluetooth/rfcomm.conf file among other things. I know -- terrible to do these changes and then not keep a backup and not even remembering what I did.

Anyway, now I can't connect to my wireless network. Network manager finds the network and everything seems fine but I can't connect/browse. The output of ifconfig and lspci is shown below. Highly appreciate any help on restoring this -- thanks in advance. 

Regards,
Daniel

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:DE:89:31:2A  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fe89:312a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:2 dropped:406 overruns:0 frame:0
          TX packets:38 errors:0 dropped:3 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18584 (18.1 KB)  TX bytes:15129 (14.7 KB)
          Interrupt:21 Base address:0xe000 Memory:edf00000-edf00fff 

eth1      Link encap:Ethernet  HWaddr 00:15:58:7C:8A:04  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:71527 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10015 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:23707575 (22.6 MB)  TX bytes:1286064 (1.2 MB)
          Base address:0x3000 Memory:ee000000-ee020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:125 errors:0 dropped:0 overruns:0 frame:0
          TX packets:125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24950 (24.3 KB)  TX bytes:24950 (24.3 KB)


Also, the output of lspci may be of help:

$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller

---

### Post by superprash2003 on 2008-07-28
could you post the output of iwconfig also

---

### Post by daniel@danielberg.no on 2008-07-28
$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

irda0     no wireless extensions.

eth0      IEEE 802.11b  ESSID:"KDAB"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:08:A1:6E:49:30   
          Bit Rate:11 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=98/100  Signal level=-27 dBm  Noise level=-28 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1089   Missed beacon:0

$ lshw -C network
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 00
       serial: 00:15:58:7c:8a:04
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.5-1 latency=0 link=no module=e1000 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:18:de:89:31:2a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp firmware=14.2 1:0 () ip=192.168.1.100 latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11b

---

### Post by daniel@danielberg.no on 2008-07-28
...

---

### Post by superprash2003 on 2008-07-28
try pinging your router.. and also try ping google.com and post output

---

### Post by daniel@danielberg.no on 2008-07-28
$ ping 192.168.1.100
PING 192.168.1.100 (192.168.1.100) 56(84) bytes of data.
64 bytes from 192.168.1.100: icmp_seq=1 ttl=64 time=0.036 ms
64 bytes from 192.168.1.100: icmp_seq=2 ttl=64 time=0.029 ms
64 bytes from 192.168.1.100: icmp_seq=3 ttl=64 time=0.029 ms
64 bytes from 192.168.1.100: icmp_seq=4 ttl=64 time=0.029 ms
64 bytes from 192.168.1.100: icmp_seq=5 ttl=64 time=0.030 ms
64 bytes from 192.168.1.100: icmp_seq=6 ttl=64 time=0.031 ms
64 bytes from 192.168.1.100: icmp_seq=7 ttl=64 time=0.028 ms
64 bytes from 192.168.1.100: icmp_seq=8 ttl=64 time=0.031 ms
64 bytes from 192.168.1.100: icmp_seq=9 ttl=64 time=0.032 ms
64 bytes from 192.168.1.100: icmp_seq=10 ttl=64 time=0.029 ms
64 bytes from 192.168.1.100: icmp_seq=11 ttl=64 time=0.032 ms
64 bytes from 192.168.1.100: icmp_seq=12 ttl=64 time=0.030 ms
64 bytes from 192.168.1.100: icmp_seq=13 ttl=64 time=0.030 ms
64 bytes from 192.168.1.100: icmp_seq=14 ttl=64 time=0.029 ms
64 bytes from 192.168.1.100: icmp_seq=15 ttl=64 time=0.030 ms
64 bytes from 192.168.1.100: icmp_seq=16 ttl=64 time=0.030 ms
64 bytes from 192.168.1.100: icmp_seq=17 ttl=64 time=0.031 ms
64 bytes from 192.168.1.100: icmp_seq=18 ttl=64 time=0.037 ms

--- 192.168.1.100 ping statistics ---
18 packets transmitted, 18 received, 0% packet loss, time 17014ms
rtt min/avg/max/mdev = 0.028/0.030/0.037/0.007 ms


$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

---

### Post by daniel@danielberg.no on 2008-07-28
Actually I think it is my router (CNET) that is the problem -- I am able to connect to my nabours lan. But what is the problem when network manager says I am connected but I can't get on the net? I realize that this is now probably a post for a completely different forum. 

Thanks for your help superprash2003!

//Daniel

---

### Post by daniel@danielberg.no on 2008-07-28
Solved it. Turned out the modem refuses to talk to the router after I had plugged the ethernet cable directly into my machine. The modem would only talk to me. Now I rebooted the modem while having the router connected to it and now it works. Sorry for any inconvenience and thanks for the help. 

//Daniel

---

