---
title: "'unknown hardware address tupe 801'  - Is this a problem?"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by Tim Silver on 2008-05-09
Hi,

Jetsam got me sudo-ing so I'm continuing with 'kevdog's' sticky.

When I entered
```
sudo dhclient -r wmaster0
```

the report was (ignoring the preamble)
```
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0
Sending on   LPF/wmaster0
Sending on   Socket/fallback
```

Is this OK/normal? Or do I need more help?

---

### Post by Ayuthia on 2008-05-09
I don't think that wmaster0 is usually used.  Normally a wireless card is labled wlan0 or eth1.

---

### Post by Tim Silver on 2008-05-12
Hi Ayuthia,

Thanks for reply.

But that's the logical name from the 'system'.

```
lshw -C network
```

---

### Post by Ayuthia on 2008-05-12
> **Tim Silver said:**
> Hi Ayuthia,

Thanks for reply.

But that's the logical name from the 'system'.

```
lshw -C network
```
Can you post your ifconfig, iwconfig, lspci -nn, and lshw -C network info?

If you don't have a working wired connection, can you tell us what names show up for ifconfig and what your wireless card is.  It should be a network controller or an ethernet controller.

---

### Post by jacobdm on 2008-05-12
Actually, I'm having exactly the same problem when following the directions in the sticky.  I am trying to set up a WPA network and I'm using the madwifi driver that is "experimental" for the AR5008.

If it will help any, here are the ifconfig, iwconfig, lspci -nn, and lshw -C network for my system:

================================================================
david@david-desktop:/etc$ ifconfig
================================================================
ath0      Link encap:Ethernet  HWaddr 00:19:5b:45:d7:1c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28 (28.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1b:fc:e1:56:a5  
          inet addr:192.168.1.190  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:fee1:56a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16682 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11237 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21962000 (20.9 MB)  TX bytes:1143905 (1.0 MB)
          Interrupt:252 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:1b:fc:e1:5d:21  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:253 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1986 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1986 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:99892 (97.5 KB)  TX bytes:99892 (97.5 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-19-5B-45-D7-1C-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2329 errors:0 dropped:0 overruns:0 frame:1435
          TX packets:1150 errors:350 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:316964 (309.5 KB)  TX bytes:54867 (53.5 KB)
          Interrupt:17 

================================================================
david@david-desktop:/etc$ iwconfig
================================================================
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:19 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=7/70  Signal level=-89 dBm  Noise level=-96 dBm
          Rx invalid nwid:109  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

================================================================
david@david-desktop:/etc$ lspci -nn
================================================================
00:00.0 Host bridge [0600]: nVidia Corporation C55 Host Bridge [10de:03a1] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ac] (rev a1)
00:00.2 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03aa] (rev a1)
00:00.3 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03a9] (rev a1)
00:00.4 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ab] (rev a1)
00:00.5 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03a8] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b5] (rev a1)
00:00.7 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b4] (rev a1)
00:01.0 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ad] (rev a1)
00:01.1 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ae] (rev a1)
00:01.2 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03af] (rev a1)
00:01.3 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b0] (rev a1)
00:01.4 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b1] (rev a1)
00:01.5 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b2] (rev a1)
00:01.6 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b3] (rev a1)
00:02.0 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b6] (rev a1)
00:02.1 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03bc] (rev a1)
00:02.2 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ba] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C55 PCI Express bridge [10de:03b7] (rev a1)
00:09.0 RAM memory [0500]: nVidia Corporation MCP55 Memory Controller [10de:0369] (rev a1)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP55 LPC Bridge [10de:0360] (rev a2)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP55 SMBus [10de:0368] (rev a2)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036c] (rev a1)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036d] (rev a2)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP55 IDE [10de:036e] (rev a1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a2)
00:0e.1 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a2)
00:0e.2 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a2)
00:0f.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI bridge [10de:0370] (rev a2)
00:0f.1 Audio device [0403]: nVidia Corporation MCP55 High Definition Audio [10de:0371] (rev a2)
00:11.0 Bridge [0680]: nVidia Corporation MCP55 Ethernet [10de:0373] (rev a2)
00:12.0 Bridge [0680]: nVidia Corporation MCP55 Ethernet [10de:0373] (rev a2)
00:16.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0378] (rev a2)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G71 [GeForce 7900 GS] [10de:0292] (rev a1)
02:07.0 Network controller [0280]: Atheros Communications Inc. AR5416 802.11abgn Wireless PCI Adapter [168c:0023] (rev 01)
02:0b.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. IEEE 1394 Host Controller [1106:3044] (rev c0)
03:00.0 Mass storage controller [0180]: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller [1095:3132] (rev 01)

================================================================
david@david-desktop:/etc$ lshw -C network
================================================================
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: AR5416 802.11abgn Wireless PCI Adapter
       vendor: Atheros Communications Inc.
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: wifi0
       version: 01
       serial: 00:19:5b:45:d7:1c
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=96 module=ath_pci multicast=yes wireless=IEEE 802.11g
david@david-desktop:/etc$

---

### Post by BoredSilly on 2008-05-14
> **Tim Silver said:**
> Hi Ayuthia,

Thanks for reply.

But that's the logical name from the 'system'.

```
lshw -C network
```

I'm having the same problem, lshw -c network tells me the logical name is wmaster0 and the driver (rt61pci) seems to be attached to it but wlan0 is my wireless card. Can't really get anywhere, funny thing is it worked using kubuntu just can't get it working under ubuntu!

---

