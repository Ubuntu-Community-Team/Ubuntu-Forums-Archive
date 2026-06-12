---
title: "No internet after upgrade to 16.04.2 xenial"
date: 2017-03-26
forum: Networking &amp; Wireless
---

### Post by toddh on 2017-03-26
I recently ran the upgrade for Xenial 16.04.2 from Trusty 14.04.1 on my sony vaio.  In the process my internet connection is no longer accessible through ubuntu.  I have a dual boot on the laptop and can access the internet through windows 7.

See below for some of the reports other threads have included while troubleshooting issues internet connectivity.  If there are other commands which may be helpful, please feel free to ask.  There are some security and other updates (such as Chrome and "Debhelper add-on to call autoreconf and clean up after the build") which are still waiting from a previous check (before internet connectivity was lost).  Obviously, the internet works using my other laptop to post this thread :-)

Commands: 
[INDENT]lsb_release -a
nmcli -p d
nmcli -p g
ifconfig -a
route -n
netstat -i
lspci
traceroute google.com
ping -c1 google.com
[/INDENT]

```
~~:/etc$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial


~~:/etc$ nmcli -p d
==========================================================
                    Status of devices
==========================================================
DEVICE  TYPE      STATE      CONNECTION                  
----------------------------------------------------------                 
wlan0   wifi      connected  donate-to_thierlmaier@gmail 
br0     bridge    unmanaged  --                          
eth0    ethernet  unmanaged  --                          
lo      loopback  unmanaged  --                          


~~:/etc$ nmcli -p g
=============================================================
                    NetworkManager status
=============================================================
STATE      CONNECTIVITY  WIFI-HW  WIFI     WWAN-HW  WWAN    
-------------------------------------------------------------
connected  full          enabled  enabled  enabled  enabled 


~~:/etc$ ifconfig -a
br0       Link encap:Ethernet  HWaddr 54:42:49:01:04:ae  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5642:49ff:fe01:4ae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1505 errors:0 dropped:0 overruns:0 frame:0
          TX packets:567 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:176875 (176.8 KB)  TX bytes:50468 (50.4 KB)

eth0      Link encap:Ethernet  HWaddr 54:42:49:01:04:ae  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2359 errors:0 dropped:0 overruns:0 frame:0
          TX packets:567 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:431146 (431.1 KB)  TX bytes:50468 (50.4 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2310 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2310 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:185675 (185.6 KB)  TX bytes:185675 (185.6 KB)

wlan0     Link encap:Ethernet  HWaddr 2c:81:58:f3:ad:ec  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e81:58ff:fef3:adec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2334 errors:0 dropped:0 overruns:0 frame:0
          TX packets:763 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:370782 (370.7 KB)  TX bytes:106069 (106.0 KB)


~~:/etc$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 br0
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 br0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 br0


~~:/etc$ netstat -i
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
br0        1500 0      1528      0      0 0           567      0      0      0 BMRU
eth0       1500 0      2390      0      0 0           567      0      0      0 BMRU
lo        65536 0      2312      0      0 0          2312      0      0      0 LRU
wlan0      1500 0      2364      0      0 0           765      0      0      0 BMRU


~~:/etc$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation HM55 Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller
03:00.1 System peripheral: Ricoh Co Ltd R5U2xx (R5U230 / R5U231 / R5U241) [Memory Stick Host Controller]
03:00.4 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller
04:00.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB] (rev 11)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved (rev 02)


~~:/etc$ traceroute google.com
traceroute to google.com (172.217.12.14), 64 hops max
  1   192.168.1.10  2999.060ms !H  2999.911ms !H  2999.888ms !H 


~~:/etc$ ping -c1 google.com
PING google.com (172.217.12.14) 56(84) bytes of data.
From toddh-VPCEB13FX.local (192.168.1.10) icmp_seq=1 Destination Host Unreachable

--- google.com ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms


```

Thank you in advance for helping me re-establish internet connectivity with ubuntu.

---

