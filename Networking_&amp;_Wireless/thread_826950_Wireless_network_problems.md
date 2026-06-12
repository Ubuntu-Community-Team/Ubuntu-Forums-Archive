---
title: "Wireless network problems"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by asav01 on 2008-06-12
Hello,
I am a newbie with Ubuntu, but I have worked with Windows before.
I have a PC, connected to a local network, that is connected to the internet through a router.
In PC 1 I have two network cards, one wired, one wireless (Atheros chipset).
I use the wired NIC to connect to the internet. This connection is currently working.
I want to use the wireless NIC to connect an iPhone to the internet.
I have tried to use Windows XP Pro for this job, but I couldn't get a reliable connection and I hope I'll have better luck with Ubuntu.
Having no idea how to fix this on my own, I provide the output of some commands I found on this forum to ease things up:

**lspci**
```
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 81)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 81)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)
04:00.0 VGA compatible controller: nVidia Corporation NV41.1 [GeForce 6800] (rev a2)
```

**lshw -C network**
```
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 00:13:d4:86:fa:ba
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.1.1 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:01:02.0
       logical name: wifi0
       version: 01
       serial: 00:19:e0:6e:17:de
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
```

**cat /etc/network/interfaces**
```

auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.1
netmask 255.255.255.0
gateway 192.168.1.254

auto eth0
```

**ifconfig**
```

ath0      Link encap:Ethernet  HWaddr 00:19:e0:6e:17:de  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:63 errors:0 dropped:0 overruns:0 frame:0
          TX packets:115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8026 (7.8 KB)  TX bytes:24097 (23.5 KB)

ath0:avahi Link encap:Ethernet  HWaddr 00:19:e0:6e:17:de  
          inet addr:169.254.7.214  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:13:d4:86:fa:ba  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fe86:faba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7550 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7871 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6410144 (6.1 MB)  TX bytes:1246724 (1.1 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2693 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2693 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:137024 (133.8 KB)  TX bytes:137024 (133.8 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-19-E0-6E-17-DE-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:975 errors:0 dropped:0 overruns:0 frame:44749
          TX packets:2092 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:121698 (118.8 KB)  TX bytes:121013 (118.1 KB)
          Interrupt:22 
```

**iwconfig**
```

lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"abc"  Nickname:""
          Mode:Master  Frequency:2.447 GHz  Access Point: 00:19:E0:6E:17:DE   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.
```

**route**
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     0      0        0 ath0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.254   0.0.0.0         UG    100    0        0 eth0
default         *               0.0.0.0         U     1000   0        0 ath0
```



I have searched the forum, and even if I find informations in other posts, I don't know how to apply them to my specific problem because I don't know how to do things in Ubuntu.

---

