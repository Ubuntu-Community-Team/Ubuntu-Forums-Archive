---
title: "Internet not working and routing tables look empty"
date: 2013-11-07
forum: Networking &amp; Wireless
---

### Post by crobertsbmw on 2013-11-07
I don't know what the deal is, but I am not getting internet through the router. I started searching around the internet and was told to run netstat. So I ran netstat -nr and got back a table with 3 entries. Then, because I don't know what I am doing I duplicated an entry (but I doubt that matters). I ran netstat on my macbook which does have internet and got a whole bunch of entries, so I want to think that something bad happened to this. I don't know what the problem could be. The last couple days we have had problems with the company that provides our internet and then my roommate reset our router. I don't know why any of that would have affected this problem but it it seems too coincidental.. Anyway, I have no idea what to do. Any help would be appreciated. Also, when I run ping google.com it responds with 'unkown host google.com'..


```


0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0



```It's an HP Pavilion running Ubuntu 13.04


Here's some other stuff:
$ lspci
```
Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller (rev 03)



```$ lsusb
```
Bus 001 Device 003: ID 0bda:5801 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



```$ ifconfig
```
eth0      Link encap:Ethernet  HWaddr 98:4b:e1:c7:c3:b5  
          inet6 addr: fe80::9a4b:e1ff:fec7:c3b5/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:630 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:85803 (85.8 KB)  TX bytes:9728 (9.7 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:11008 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11008 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:724277 (724.2 KB)  TX bytes:724277 (724.2 KB)


wlan0     Link encap:Ethernet  HWaddr 90:00:4e:35:bf:b5  
          inet addr:192.168.1.121  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::9200:4eff:fe35:bfb5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22581 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5538 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2555311 (2.5 MB)  TX bytes:543563 (543.5 KB)



```$ iwconfig
```
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"dd-wrt"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 68:7F:74:C2:E6:C0   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:317  Invalid misc:341   Missed beacon:0



```$ dmesg


```
...
[   28.620796] wlan0: authenticate with 08:60:6e:e8:da:0f
[   28.634044] wlan0: send auth to 08:60:6e:e8:da:0f (try 1/3)
[   28.636239] wlan0: 08:60:6e:e8:da:0f denied authentication (status 1)
[   57.093316] wlan0: authenticate with 08:60:6e:e8:da:0f
[   57.106149] wlan0: send auth to 08:60:6e:e8:da:0f (try 1/3)
[   57.108264] wlan0: 08:60:6e:e8:da:0f denied authentication (status 1)
[   85.081453] wlan0: authenticate with 08:60:6e:e8:da:0f
[   85.094789] wlan0: send auth to 08:60:6e:e8:da:0f (try 1/3)
[   85.096980] wlan0: 08:60:6e:e8:da:0f denied authentication (status 1)
[  113.086107] wlan0: authenticate with 08:60:6e:e8:da:0f
[  113.113433] wlan0: send auth to 08:60:6e:e8:da:0f (try 1/3)
[  113.117438] wlan0: 08:60:6e:e8:da:0f denied authentication (status 1)
[  141.060381] wlan0: authenticate with 68:7f:74:c2:e6:c0
[  141.083873] wlan0: send auth to 68:7f:74:c2:e6:c0 (try 1/3)
[  141.091686] wlan0: authenticated
[  141.094070] wlan0: associate with 68:7f:74:c2:e6:c0 (try 1/3)
[  141.100000] wlan0: RX AssocResp from 68:7f:74:c2:e6:c0 (capab=0x401 status=0 aid=2)
[  141.100237] wlan0: associated
[  141.100271] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  391.256546] usb 2-3: new high-speed USB device number 2 using ehci-pci
...

```

$ sudo lshw -C network


```
 *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 90:00:4e:35:bf:b5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.8.0-32-generic firmware=N/A ip=192.168.1.121 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0100000-f010ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168 PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 98:4b:e1:c7:c3:b5
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff memory:f0010000-f001ffff



```

---

### Post by crobertsbmw on 2013-11-07
Update:
I took my computer into work this morning at the wireless works fine there. I decided it had to be something with the ISP. I gave them a call and they made me plug the computer directly into the wall again, and then the internet worked. However the router works for all the other computers in my apt, just not my Ubuntu machine. So it has something to do with my specific computer and my specific router...

---

