---
title: "CNet CWP-854 (RT61) can't connect, can scan in 6.06, cannot in 6.10"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by pbb on 2007-02-26
I'm trying to get my CNet CWP-854 working under Ubuntu, but I can't manage.

Using the 6.06 live CD, it can scan for access points (they are listed in the Network applet, and iwlist scan shows them). Once, I have been able to connect to the network, but all other times (doing exactly the same) I get no connection. (Pinging the router says unreachable.)

With the 6.10 live CD, it cannot even find any access points, let alone connect. Oh, and what does the "wmaster0" networking device do?

I've got 6.10 on the harddisk, where it does exactly the same as on the live CD. I could not install 6.06, since the install process dies silently when Partition Editor tries to format the partitions.

Here are some command outputs:

-= Ubuntu 6.06 =-

lshw:
  *-network
       description: Wireless interface
       physical id: 2
       logical name: ra0
       serial: 00:08:a1:9b:6a:fe
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=10.0.0.5 multicast=yes wireless=RT61 Wireless

lspci:
0000:00:0a.0 Network controller: RaLink: Unknown device 0302

ifconfig:
ra0       Link encap:Ethernet  HWaddr 00:08:A1:9B:6A:FE
          inet addr:10.0.0.5  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:a1ff:fe9b:6afe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24920 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2715 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2000122 (1.9 MiB)  TX bytes:356 (356.0 b)
          Interrupt:185

iwconfig:
ra0       RT61 Wireless  ESSID:"pbb"
          Mode:Auto  Channel:11  Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=48/70  Signal level:-121 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwlist scan:
ra0       Scan completed :
          Cell 01 - Address: 00:14:BF:FA:17:A6
                    Mode:Managed
                    ESSID:"pbb"
                    Encryption key:off
                    Channel:11
          Cell 02 - Address: 00:11:95:E6:70:2A
                    Mode:Managed
                    ESSID:"ARNAR"
                    Encryption key:on
                    Channel:6

-= Ubuntu 6.10 =-

lshw:
        *-network
             description: Wireless interface
             product: RaLink
             vendor: RaLink
             physical id: a
             bus info: pci@00:0a.0
             logical name: wmaster0
             version: 00
             serial: 00:08:a1:9b:6a:fe
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list logical wireless ethernet physical
             configuration: broadcast=yes driver=rt61pci multicast=yes wireless=IEEE 802.11g
             resources: iomemory:ef000000-ef007fff irq:185

lspci:
00:0a.0 Network controller: RaLink Unknown device 0302

ifconfig:
wlan0     Link encap:Ethernet  HWaddr 00:08:A1:9B:6A:FE  
          inet6 addr: fe80::208:a1ff:fe9b:6afe/64 Scope:Link
          UP RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:3816 (3.7 KiB)
          Base address:0x5000 

wmaster0  Link encap:UNSPEC  HWaddr 00-08-A1-9B-6A-FE-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x5000 

iwconfig:
wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"pbb"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          
iwlist scan:
wmaster0  Failed to read scan data : Operation not supported
wlan0     No scan results

---

