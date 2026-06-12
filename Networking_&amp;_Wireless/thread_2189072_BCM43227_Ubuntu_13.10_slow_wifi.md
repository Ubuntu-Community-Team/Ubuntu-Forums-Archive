---
title: "BCM43227 Ubuntu 13.10 slow wifi"
date: 2013-11-20
forum: Networking &amp; Wireless
---

### Post by yiannis.kouts on 2013-11-20
Hi,i have Ubuntu 13.10 on an Acer Aspire 5750. After the installation i had no wireless connection and i found out that enabling the use of a propritary driver(Broadcome 812.11 Linux STA wireless driver from bcmwl-kernel-source) would be the solution. Indeed i now can connect but the speed is not what it should be, it is actually a lot slower than when i boot from windows. 

Here is my system information(i'm a new user so if i have forgotten something please tell me and i will add it):

```
Network controller: Broadcom Corporation BCM43227 802.11b/g/n

ifconfig: 
eth1      Link encap:Ethernet  HWaddr 64:27:37:63:ef:9d  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::6627:37ff:fe63:ef9d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3124 errors:0 dropped:0 overruns:0 frame:472003
          TX packets:3672 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2145229 (2.1 MB)  TX bytes:597781 (597.7 KB)
          Interrupt:17 

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"ael"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: BA:8B:97:DB:61:A1   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


lsmod | grep "wlan_module_name"   gives nothing as a result

*-network               
       description: Ethernet interface
       product: NetLink BCM57785 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: dc:0e:a1:25:3c:32
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.132 firmware=sb latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:c0430000-c043ffff memory:c0440000-c044ffff memory:c0450000-c04507ff
  *-network
       description: Wireless interface
       product: BCM43227 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 00
       serial: 64:27:37:63:ef:9d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.141 (r415941) ip=192.168.2.4 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:c0500000-c0503fff




iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: BA:8B:97:DB:61:A1
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-21 dBm  
                    Encryption key:on
                    ESSID:"ael"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 51508ms ago
                    IE: Unknown: 000361656C
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020000040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00

uname -mr
3.11.0-13-generic i686




service networking restart
stop: Unknown job: networking
start: Unknown job: networking

```

---

### Post by praseodym on 2013-11-20
Change the encryption to WPA2-AES (CCMP) in your router

---

### Post by yiannis.kouts on 2013-11-20
thanks,that actually improved the speed but unfortunatelly it doesn't solve the problem entirelly.

---

### Post by praseodym on 2013-11-21
Try a fixed channel, not hiding the network and change the bandwidth to 20MHz instead of 20/40MHz

---

### Post by yiannis.kouts on 2013-11-21
> **praseodym said:**
> Try a fixed channel, not hiding the network and change the bandwidth to 20MHz instead of 20/40MHz
I'm afraid i don' know how to do either.Could you please explain a bit more?

---

### Post by praseodym on 2013-11-22
Go to the router interface and change the settings there. Check the manual

---

