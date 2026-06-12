---
title: "Ralink RT61 worked and crashed"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by lipry on 2009-01-26
Hi,

Can anybody help me with the wireless D-link on Ralink?

Thank you very much in advance!

My D-link PCI wireless card have been working perfectly on Ubuntu 8.10 for a few days, but suddenly crashed - one day the connection was lost, and the Network Tool could not connect to my hidden wireless network.
And next day, the small connection icon (a computer display) in the lower right corner of the desktop dissapeared.

I tried *sudo ifconfig wlan0 up*, but had no results.

My win computers continue working perfectly with wlan.



_lipry@lipry-desktop:~$ lspci_
...
02:02.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

_lipry@lipry-desktop:~$ ifconfig_
eth0      Link encap:Ethernet  HWaddr 00:04:61:6d:25:74  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:270 errors:0 dropped:0 overruns:0 frame:0
          TX packets:270 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17248 (17.2 KB)  TX bytes:17248 (17.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:11:05:df:43  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-11-05-DF-43-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

_lipryi@lipry-desktop:~$ iwconfig_
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=8 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

_lipry@lipry-desktop:~$ sudo iwlist scan_
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

_lipry@lipry-desktop:~$ sudo lshw -C network_

  *-network:0             
       description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: RaLink
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wmaster0
       version: 00
       serial: 00:1b:11:05:df:43
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 10
       serial: 00:04:61:6d:25:74
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 66:41:f4:9b:b2:d0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by lipry on 2009-02-04
up :)

---

