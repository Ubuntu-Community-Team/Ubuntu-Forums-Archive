---
title: "RT2500, unstable slow connection"
date: 2013-12-27
forum: Networking &amp; Wireless
---

### Post by sergi-3 on 2013-12-27
This is based on a previous thread: [http://ubuntuforums.org/showthread.php?t=2195282](http://ubuntuforums.org/showthread.php?t=2195282)

I removed wicd and ndiswrapper, and reverted to the driver provided by the kernel (rt2500pci) and the standard network manager. The problem persists: although I am able to connect just fine, after some time the connection becomes really unreliable, with very low speeds, long ping times and so on. Also, I have noticed that my soulseek client (nicotine+) is unable to connect to any other users / start downloads, whereas it works perfectly when I use the wired connection.

My wireless card:
```

sergi@shak:~$ lspci -nnk | grep -iA2 net
00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
    Subsystem: ASRock Incorporation 939NF6G-VSTA Board [1849:03ef]
    Kernel driver in use: forcedeth
--
01:08.0 Network controller [0280]: Ralink corp. RT2500 Wireless 802.11bg [1814:0201] (rev 01)
    Subsystem: Linksys WMP54G v4.0 PCI Adapter [1737:0032]
    Kernel driver in use: rt2500pci


```

Ubuntu and kernel version:
```

sergi@shak:~$ lsb_release -d
Description:    Ubuntu 12.04.3 LTS
sergi@shak:~$ uname -mr
3.2.0-57-generic x86_64

```

lsmod output with rt2x00 related info:
```

sergi@shak:~$ lsmod | grep rt2
rt2500pci              27646  0 
rt2x00pci              14620  1 rt2500pci
rt2x00lib              55382  2 rt2500pci,rt2x00pci
mac80211              506862  2 rt2x00pci,rt2x00lib
cfg80211              205774  2 rt2x00lib,mac80211
eeprom_93cx6           12767  1 rt2500pci

```

lshw network output: 
```

sergi@shak:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: RT2500 Wireless 802.11bg
       vendor: Ralink corp.
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: wlan0
       version: 01
       serial: 00:12:17:91:7e:20
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci driverversion=3.2.0-57-generic firmware=N/A ip=192.168.2.112 latency=32 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:faefe000-faefffff


```

iwconfig
```

sergi@shak:~$ iwconfig 
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"pizzaiolo"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:11:8D:E0:E0   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:11  Invalid misc:741   Missed beacon:0

eth0      no wireless extensions.

```

iwlist scan:
```

sergi@shak:~$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:11:8D:E0:E0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"pizzaiolo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002589a0eee8
                    Extra: Last beacon: 27980ms ago
                    IE: Unknown: 000970697A7A61696F6C6F
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

eth0      Interface doesn't support scanning.

```

Info on the loaded module:
```

sergi@shak:~$ modinfo rt2500pci
filename:       /lib/modules/3.2.0-57-generic/kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
license:        GPL
description:    Ralink RT2500 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     B0FB755986B42553D4F3F0E
alias:          pci:v00001814d00000201sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.2.0-57-generic SMP mod_unload modversions

```

Any help will be greatly appreciated... this is driving me mad. And i really want to get rid off this cable!!

---

