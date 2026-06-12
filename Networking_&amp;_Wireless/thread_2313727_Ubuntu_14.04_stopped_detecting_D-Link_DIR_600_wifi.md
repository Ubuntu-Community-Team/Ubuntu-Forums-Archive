---
title: "Ubuntu 14.04 stopped detecting D-Link DIR 600 wifi"
date: 2016-02-15
forum: Networking &amp; Wireless
---

### Post by rodrigueskevin on 2016-02-15
I have been using the D-Link DIR 600 wifi with Ubuntu 14.04 for a couple of years now. But suddenly it has stopped being detected. 

My mobile and other devices are able to detect the wifi successfully. It's only my laptop with Ubuntu 14.04 that seems to not detect it.
Also the laptop detects other wifi successfully.

Some information below if it's useful. My ESSID is "Pacenet" which is not shown as well in the list below. It's detecting the other ESSID as shown.
I've cut some information as it does not allow me to post all of it. Please see the attachment for more information.

$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 54:35:30:e8:55:b1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:18 memory:f7900000-f7907fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 0c
       serial: b8:2a:72:ad:82:11
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=192.168.0.100 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:58 ioport:e000(size=256) memory:f7800000-f7800fff memory:f2100000-f2103fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
kevin@kevin-Vostro-3446:~$ sudo iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 60:E3:27:6E:44:08
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"cisco"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 0005636973636F
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E1003FF00000000000000000000000000000000000000000000
                    IE: Unknown: 331A6E1003FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D16010D0200000000000000000000000000000000000000
                    IE: Unknown: 3416010D0200000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD860050F204104A0001101044000102103B000103104700100000000000001000000060E3276E44081021000754502D4C494E4B10230009544C2D57523732304E10240003312E3010420003312E301054000800060050F20400011011001E54502D4C494E4B20576972656C65737320526F757465722057523732304E100800020086103C000101

kevin@kevin-Vostro-3446:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS"
Linux kevin-Vostro-3446 3.13.0-77-generic #121-Ubuntu SMP Wed Jan 20 10:50:42 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
kevin@kevin-Vostro-3446:~$ lspci -nnk | grep -iA2 net
06:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
	Kernel driver in use: wl
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	Subsystem: Dell Device [1028:0662]
	Kernel driver in use: r8169
kevin@kevin-Vostro-3446:~$ lsusb
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 0a5c:21d7 Broadcom Corp. BCM43142 Bluetooth 4.0
Bus 001 Device 003: ID 064e:9205 Suyin Corp. 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
kevin@kevin-Vostro-3446:~$ iwconfig

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

kevin@kevin-Vostro-3446:~$ sudo iwlist scan

wlan0     Scan completed :
          Cell 01 - Address: 14:CC:20:F5:19:20
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"popim"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 100ms ago
                    IE: Unknown: 0005706F70696D
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 0706494E20010D14
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E1103FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D16010D0000000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E1103FF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34010D0000000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD990050F204104A0001101044000102103B000103104700100000000000001000000014CC20F519101021000754502D4C494E4B10230009544C2D57523734304E10240003342E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523734304E100800020086103C000101104900140024E26002000101600000020001600100020001
          Cell 02 - Address: F4:F2:6D:E9:53:5A
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"MOSHIN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 6876ms ago
                    IE: Unknown: 00064D4F5348494E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEF111BFFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D16080F0600000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD990050F204104A0001101044000102103B00010310470010000102030405060708090A0B0C0D0E0F1021000754502D4C494E4B10230009544C2D57523834304E10240003322E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523834304E100800020086103C000101104900140024E26002000101600000020001600100020001
          Cell 03 - Address: 60:E3:27:6E:44:08
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"cisco"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 100ms ago
                    IE: Unknown: 0005636973636F
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E1003FF00000000000000000000000000000000000000000000
                    IE: Unknown: 331A6E1003FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D16010D0200000000000000000000000000000000000000
                    IE: Unknown: 3416010D0200000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: 
                    IE: Unknown: DD1A00904C3406001300000000000000000000000000000000000000

---

### Post by lensman3 on 2016-02-15
What does "ifconfig" show?

What does "netstat -nr" show?

What does "arp -n" show?

---

### Post by rodrigueskevin on 2016-02-16
kevin@kevin-Vostro-3446:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr b8:2a:72:ad:82:11  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ba2a:72ff:fead:8211/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5442291 (5.4 MB)  TX bytes:584493 (584.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1528 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1528 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:141388 (141.3 KB)  TX bytes:141388 (141.3 KB)

wlan0     Link encap:Ethernet  HWaddr 54:35:30:e8:55:b1  
          inet6 addr: fe80::5635:30ff:fee8:55b1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

kevin@kevin-Vostro-3446:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr b8:2a:72:ad:82:11  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ba2a:72ff:fead:8211/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5442291 (5.4 MB)  TX bytes:584493 (584.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1528 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1528 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:141388 (141.3 KB)  TX bytes:141388 (141.3 KB)

wlan0     Link encap:Ethernet  HWaddr 54:35:30:e8:55:b1  
          inet6 addr: fe80::5635:30ff:fee8:55b1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 


kevin@kevin-Vostro-3446:~$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0


kevin@kevin-Vostro-3446:~$ arp -n
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.0.1              ether   f0:7d:68:59:f6:1e   C                     eth0

---

### Post by rodrigueskevin on 2016-02-16
I also  tried to manually connect to it (Pacenet) but it's not even detected. But I can manage to connect to my neighbor's wifi (MOSHIN).

kevin@kevin-Vostro-3446:~$ nmcli d wifi connect Pacenet password xxxxxxxxxxxx iface wlan0
Error: No network with SSID 'Pacenet' found.

kevin@kevin-Vostro-3446:~$ nmcli d wifi connect MOSHIN password xxxxxxxxxxxx iface wlan0
Error: Connection activation failed: (7) Secrets were required, but not provided.

---

### Post by rodrigueskevin on 2016-02-16
I also  tried to manually connect to it (Pacenet) but it's not even detected. But I can manage to connect to my neighbor's wifi (MOSHIN).

kevin@kevin-Vostro-3446:~$ nmcli d wifi connect Pacenet password xxxxxxxxxxxx iface wlan0
Error: No network with SSID 'Pacenet' found.

kevin@kevin-Vostro-3446:~$ nmcli d wifi connect MOSHIN password xxxxxxxxxxxx iface wlan0
Error: Connection activation failed: (7) Secrets were required, but not provided.

---

