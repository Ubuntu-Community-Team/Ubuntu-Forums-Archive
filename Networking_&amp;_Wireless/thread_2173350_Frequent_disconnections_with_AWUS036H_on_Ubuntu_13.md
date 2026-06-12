---
title: "Frequent disconnections with AWUS036H on Ubuntu 13.04"
date: 2013-09-09
forum: Networking &amp; Wireless
---

### Post by christos3 on 2013-09-09
I'm having a problem with disconnections with my Alfa. I face the same problem on Linux Mint 15. On Windows though everything works perfect.


```
$ iwconfig 
wlan2     IEEE 802.11bg  ESSID:"OTE5D8A0C"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 20:F3:A3:5D:8A:14   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0


wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


eth0      no wireless extensions.


lo        no wireless extensions.

```



```
$ nm-tool


NetworkManager Tool


State: connected (global)


- Device: wlan2  [OTE5D8A0C] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8187
  State:             connected
  Default:           yes
  HW Address:        00:C0:CA:51:2B:9B


  Capabilities:
    Speed:           54 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Green n Blue:    Infra, AC:86:74:0D:6C:22, Freq 2432 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    govas:           Infra, 00:16:B6:E4:04:8C, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WEP
    *OTE5D8A0C:      Infra, 20:F3:A3:5D:8A:14, Freq 2437 MHz, Rate 54 Mb/s, Strength 71 WPA
    conn-x91da80:    Infra, CC:1A:FA:91:DA:80, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA
    OTEB35984:       Infra, 00:26:44:B3:59:84, Freq 2452 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1




- Device: wlan1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k_htc
  State:             disconnected
  Default:           no
  HW Address:        00:26:F2:52:D9:E0


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        94:DE:80:2B:FE:78


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off

```

```
$ sudo lshw -C Network  *-network               
       description: Ethernet interface
       product: RTL8111/8168 PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: 94:de:80:2b:fe:78
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:74 ioport:d000(size=256) memory:dc104000-dc104fff memory:dc100000-dc103fff
  *-network:0
       description: Wireless interface
       physical id: 1
       bus info: usb@8:1.4
       logical name: wlan2
       serial: 00:c0:ca:51:2b:9b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=3.8.0-19-generic firmware=N/A ip=192.168.1.2 link=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1
       description: Wireless interface
       physical id: 2
       bus info: usb@2:5.2
       logical name: wlan1
       serial: 00:26:f2:52:d9:e0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ath9k_htc driverversion=3.8.0-19-generic firmware=1.3 link=no multicast=yes wireless=IEEE 802.11bgn



```

Here is an output from iwscanner. At the end as you can it disconnected.
[IMG]http://i.stack.imgur.com/OYp34.png[/IMG]


**What i have tried so far**
 
1 - I disabled the IPv6 for my alfa. I read in another question that this may cause some conflicts.
2 -
```
$ sudo modprobe -rfv rtl8187
rmmod rtl8187
rmmod eeprom_93cx6


$ sudo modprobe -v rtl8187
insmod /lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko

```
So far the nothing worked.


Then,
- I updated the kernel to 3.11
- I installed the compat-drivers (backports) [http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/](http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/)
So far the problem persists.

Then i tried ndiswrapper but it the adapter wasn't even recognised so i reverted.



**NOTE**
I think i have found a pattern. The adapter rarely disconnects when i am just browsing. But when i am downloading somthing especially if it is big (ex bigger than 100M) it is more likely that it will disconnect. Also, but this may be just in my mind, i think it disconnects after the download speed hits it's peak.


Additionally i have noticed that after it disconnects, in the netwotk indicator the adapter is up and it lists all the available networks except mine (the one it just disconnected from).


What is going on?

---

### Post by key-x on 2013-09-09
Have you tried another Driver ? a.e. realtek 8187 L ?
I had the same Problem with the 036NHR (8192cu)

---

### Post by varunendra on 2013-09-09
> **key-x said:**
> Have you tried another Driver ? a.e. realtek 8187 L ?

Apparently not. But its installation on 13.04 is not so straightforward either. The proprietary driver's source code depends some old entities that have been dropped in the newer kernels, so it gives compilation errors on 13.04 and later (now even on 12.04.3, since it uses the newer kernel).

However, the patch is rather simple. Please follow [post=12775665]this post[/post] to download and install the proprietary driver from Realtek (ignore the initial part about removing ndiswrapper). Let us know how well it works for you. Thanks.

Oh, and Welcome to the Forums christos3 ! :)

---

### Post by christos3 on 2013-09-12
I tried that. I still get disconnections...
Is there a way to find out if i am using the right driver.

I even tried using the windows driver with [COLOR=#000000]ndiswrapper.[/COLOR]

I tried other distros and i encounter the same problem (all had kernels > 3.2)

 But in Windows everything works fine.
So it has nothing to do with the adapter itself.

---

### Post by varunendra on 2013-09-12
Time to dig deeper.

Please follow the "Wireless Script" link in my signature below, follow the instructions in the linked post to run the script and post back the report it generates. Thanks.

---

### Post by christos3 on 2013-09-13
I run the script in my Mint15 partition. The problem is the same of course.
It's a fresh installation. I didn't install any other driver. I have the default. I just updated the system.
I think it is equivalent to Ubuntu 13.04.

Here is the output of the script:

```



*************** info trace ***************


***** uname -a *****


Linux linux-mint 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:	LinuxMint
Description:	Linux Mint 15 Olivia
Release:	15
Codename:	olivia


***** lspci *****


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
	Kernel driver in use: r8169


***** lsusb *****


Bus 002 Device 002: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 003 Device 003: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 007 Device 002: ID 046d:c52e Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11bg  ESSID:"OTE5D8A0C"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:227  Invalid misc:9   Missed beacon:0




***** rfkill *****


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


***** lsmod *****


rtl8187                60848  0 
mac80211              606457  1 rtl8187
cfg80211              510937  2 mac80211,rtl8187
eeprom_93cx6           13344  1 rtl8187


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: wlan0  [Auto OTE5D8A0C] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8187
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           54 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    conn-x91da80:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA
    OTE157751:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA
    *OTE5D8A0C:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 71 WPA
    linux-mint:      Ad-Hoc, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WEP
    Green n Blue:    Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off






***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


***** iwlist *****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"OTE5D8A0C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000230f90a126
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 00094F5445354438413043
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A0E1103FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606050700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500010E7A12
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706434120010D10
                    IE: Unknown: DD1E00904C330E1103FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406050700000000000000000000000000000000000000
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"OTE157751"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001088bd811d
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 00094F5445313537373531
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B0001031047001045B019789A201677FF5C06BEC07975BB1021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D4150100800020084103C000101
                    IE: Unknown: DD09001018020000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"linux-mint"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=00000000288cb11e
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000A6C696E75782D6D696E74
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 06020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C1119FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: DD09001018020000040000
                    IE: Unknown: DD070050F202000100
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"conn-x91da80"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f2bfe07751
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000C636F6E6E2D78393164613830
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050000077A12
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: DD1E00904C336E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401050000000000000000000000000000000000000000
          Cell 05 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Green n Blue"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000009afc33e32
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000C477265656E206E20426C7565
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: Unknown: 0706475220010B14
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1ACC111BFF00000000000000000000000100000000000000000000
                    IE: Unknown: 3D1605000400000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00




***** resolv.conf *****


nameserver 127.0.1.1


nameserver 208.67.222.222
nameserver 208.67.220.220


***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


***** modinfo *****


filename:       /lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko
license:        GPL
description:    RTL8187/RTL8187B USB wireless driver
author:         Larry Finger <Larry.Finger@lwfinger.net>
author:         Hin-Tak Leung <htl10@users.sourceforge.net>
author:         Herton Ronaldo Krzesinski <herton@mandriva.com.br>
author:         Andrea Merello <andreamrl@tiscali.it>
author:         Michael Wu <flamingice@sourmilk.net>
srcversion:     4EC70451284400E93948C00
alias:          usb:v1737p0073d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B75p8187d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18E8p6232d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D1pABE6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1371p9401d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v114Bp0150d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0029d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0028d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p000Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v03F0pCA02d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p4260d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p6A00d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p6100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p010Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0769p11F2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8198d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8197d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8189d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8187d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp705Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p171Dd*dc*dsc*dp*ic*isc*ip*in*
depends:        mac80211,eeprom_93cx6,cfg80211
intree:         Y
vermagic:       3.8.0-19-generic SMP mod_unload modversions 




***** udev rules *****


# USB device 0x0bda:0x8187 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# USB device 0x0846:0x9030 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:09.0/0000:03:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


***** dmesg *****


[   39.496107] ieee80211 phy0: hwaddr <MAC address removed>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   39.507610] rtl8187: Customer ID is 0xFF
[   39.508100] rtl8187: wireless switch is on
[   41.810888] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   41.811153] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   45.692982] wlan0: authenticate with <MAC address removed>
[   45.798040] wlan0: send auth to <MAC address removed> (try 1/3)
[   45.800877] wlan0: authenticated
[   45.804507] wlan0: associate with <MAC address removed> (try 1/3)
[   45.806880] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[   45.807492] wlan0: associated
[   45.807520] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


****************** done ******************



```

---

### Post by varunendra on 2013-09-13
Since you have reinstalled and now using the default driver again, there is not much to see or suggest except that maybe you could try changing your router's channel to 1 or 11 instead of 6. These channels usually work better.

If this doesn't fix the problem, please try the proprietary driver following instructions from the link I gave earlier.

---

### Post by christos3 on 2013-09-13
Ok here is the output with the [COLOR=#000000]proprietary driver installed.
I still get disconnections. I see no difference from before... [/COLOR]:([COLOR=#000000]

[/COLOR]```


*************** info trace ***************


***** uname -a *****


Linux linux-mint 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:    LinuxMint
Description:    Linux Mint 15 Olivia
Release:    15
Codename:    olivia


***** lspci *****


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169


***** lsusb *****


Bus 001 Device 002: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 002 Device 002: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 007 Device 002: ID 046d:c52e Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11bg  ESSID:"OTE5D8A0C"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:1   Missed beacon:0




***** rfkill *****


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


***** lsmod *****


r8187l                159270  0 
rtl8187                60848  0 
mac80211              606457  1 rtl8187
cfg80211              510937  2 mac80211,rtl8187
eeprom_93cx6           13344  1 rtl8187


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: wlan0  [Auto OTE5D8A0C] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8187
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           48 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    conn-x91da80:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 52 WPA
    OTE157751:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA
    Green n Blue:    Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    linux-mint:      Ad-Hoc, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WEP
    melistas:        Infra, <MAC address removed>, Freq 2472 MHz, Rate 54 Mb/s, Strength 49 WEP
    *OTE5D8A0C:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 71 WPA


  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off






***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


***** iwlist *****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"linux-mint"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000000004b98ad4
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000A6C696E75782D6D696E74
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 06020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C1119FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: DD09001018020000040000
                    IE: Unknown: DD070050F202000100
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"OTE5D8A0C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000023d416ff40
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 00094F5445354438413043
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A0E1103FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606050700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050001077A12
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706434120010D10
                    IE: Unknown: DD1E00904C330E1103FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406050700000000000000000000000000000000000000
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"OTE157751"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000114d43d5e5
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 00094F5445313537373531
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B0001031047001045B019789A201677FF5C06BEC07975BB1021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D4150100800020084103C000101
                    IE: Unknown: DD09001018020000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"conn-x91da80"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f384671e81
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000C636F6E6E2D78393164613830
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500010E7A12
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: DD1E00904C336E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401050600000000000000000000000000000000000000
          Cell 05 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Green n Blue"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a744a28c9
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000C477265656E206E20426C7565
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: Unknown: 0706475220010B14
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1ACC111BFF00000000000000000000000100000000000000000000
                    IE: Unknown: 3D1605000400000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00




***** resolv.conf *****


nameserver 127.0.1.1


nameserver 208.67.222.222
nameserver 208.67.220.220


***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


***** modinfo *****


filename:       /lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/r8187l.ko
description:    Linux driver for Realtek RTL8187 WiFi cards
author:         Andrea Merello <andreamrl@tiscali.it>
version:        V 1.1
license:        GPL
license:        GPL
author:         Copyright (C) 2004 Intel Corporation <jketreno@linux.intel.com>
description:    802.11 data/management/control stack
license:        GPL
description:    HostAP crypto
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: TKIP
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: CCMP
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: WEP
author:         Jouni Malinen
srcversion:     1034B88085739D87E49E8C8
alias:          usb:v0846p6A00d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p6100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8187d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B75p8187d*dc*dsc*dp*ic*isc*ip*in*
depends:        
vermagic:       3.8.0-19-generic SMP mod_unload modversions 
parm:           ifname:charp
parm:           devname: Net interface name,ath%d=default
parm:           channels: Channel bitmask for specific locales. NYI (int)


filename:       /lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko
license:        GPL
description:    RTL8187/RTL8187B USB wireless driver
author:         Larry Finger <Larry.Finger@lwfinger.net>
author:         Hin-Tak Leung <htl10@users.sourceforge.net>
author:         Herton Ronaldo Krzesinski <herton@mandriva.com.br>
author:         Andrea Merello <andreamrl@tiscali.it>
author:         Michael Wu <flamingice@sourmilk.net>
srcversion:     4EC70451284400E93948C00
alias:          usb:v1737p0073d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B75p8187d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18E8p6232d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D1pABE6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1371p9401d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v114Bp0150d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0029d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0028d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p000Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v03F0pCA02d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p4260d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p6A00d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p6100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p010Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0769p11F2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8198d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8197d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8189d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8187d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp705Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p171Dd*dc*dsc*dp*ic*isc*ip*in*
depends:        mac80211,eeprom_93cx6,cfg80211
intree:         Y
vermagic:       3.8.0-19-generic SMP mod_unload modversions 




***** udev rules *****


# USB device 0x0bda:0x8187 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# USB device 0x0846:0x9030 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:09.0/0000:03:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


***** dmesg *****


[   10.427825] ieee80211 phy0: hwaddr <MAC address removed>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   10.440945] rtl8187: Customer ID is 0xFF
[   10.441435] rtl8187: wireless switch is on
[   10.500710] rtl8187L: Initializing module
[   10.500711] rtl8187L: Wireless extensions version 22
[   10.500712] rtl8187L: Initializing proc filesystem
[   20.364842] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.365076] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.545243] wlan0: authenticate with <MAC address removed>
[   25.658572] wlan0: send auth to <MAC address removed> (try 1/3)
[   25.662482] wlan0: authenticated
[   25.664567] wlan0: associate with <MAC address removed> (try 1/3)
[   25.667212] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[   25.667968] wlan0: associated
[   25.667975] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


****************** done ******************



```[COLOR=#000000]
[/COLOR]

---

### Post by varunendra on 2013-09-13
> **christos3 said:**
> I see no difference from before... :(```

***** lsmod *****


r8187l                159270  0 
**[COLOR="#FF0000"]rtl8187 [/COLOR]**               60848  0 
mac80211              606457  1 rtl8187
cfg80211              510937  2 mac80211,rtl8187
eeprom_93cx6           13344  1 rtl8187


***** nm-tool *****
....

- Device: wlan0  [Auto OTE5D8A0C] ----------------------------------------------
  Type:              802.11 WiFi
  **Driver:           [COLOR="#FF0000"] rtl8187[/COLOR]**
.....

```

Because the driver in use is still rtl8187, not the one we compiled. My mistake, I 'assumed' that its blacklisting and unloading would have been included in the driver's installation script. Apparently not.

Please do it manually -
```
echo "blacklist rtl8187" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rfv rtl8187
sudo modprobe -rfv r8187l
sudo modprobe -v r8187l
```
Do we see any difference now? Positive or negative?

---

### Post by christos3 on 2013-09-13
First of all thank you for your help so far.

I did that and now the system is broken.
Whenever i try to connect to a network i get this screen and the system freezes.
[IMG]http://s22.postimg.org/l8290kl7z/IMG_20130913_214805.jpg[/IMG]


Also i noticed something else.
During the OS booting, when the daemons and services are starting, everything starts ok but i get this:
```
starting mdns/dns-sd daemon [FAIL]
```
Note that this was happening from the moment i installed the OS.

What should i do now? By the moment i plug in the adapter the OS crashes.

---

### Post by varunendra on 2013-09-13
> **christos3 said:**
> What should i do now? By the moment i plug in the adapter the OS crashes.

Well, obviously your kernel doesn't like the module for some reason. Please try booting with nomodeset option, if the kernel still panics, we'll have to roll back this driver. To boot with nomodeset -

While booting, press 'Shift' (or 'Esc' in some systems) key to bring up the Grub menu. In grub screen, press 'e' to edit the kernel boot line. Key down to the line that starts with "linux /boot...." and usually ends with "quite splash". Add the word "nomodeset" before "quite splash", keeping a space between the words. Press Ctrl-X to boot with this option.

This should let you boot in safe graphics mode. Now plug in the adapter and see if the kernel panics again. If it does, you can also try a couple other options alongside nomodeset, like acpi=off, noapic and nolapic. (see details in this very informative [thread]("http://ubuntuforums.org/showthread.php?t=1613132") by P4man)

If none of these help, and the kernel panics in each case as soon as the driver is loaded (adapter is plugged in), temporarily prevent the driver from loading (we'll completely remove it if needed). To do this, open the blacklist file with root access -
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
Remove "blacklist rtl8187" line from its bottom and add "blacklist r8187l" in its place. Proofread, save and close the file.

Now plug-in the adapter again and the default driver will get loaded. So in a way, we'd be where we started.... probably to start with something again.

---

### Post by christos3 on 2013-09-14
Ok i restored the old driver. What should i do now?

---

### Post by varunendra on 2013-09-14
Does your router support N-channel? Have you tried turning it off (select b/g only)? This may be one of reasons causing the trouble with the proprietary driver, may even fix the frequent disconnection issue sometimes.

You mentioned in your first post -
> - I updated the kernel to 3.11
- I installed the compat-drivers (backports) [http://drvbp1.linux-foundation.org/~...tml/backports/](http://drvbp1.linux-foundation.org/~...tml/backports/)
Did you try both these things simultaneously? Or one, then the other?

In terms of driver, we can try the latest backported drivers, but if you already tried kernel 3.11.. then they are mostly the same thing.
If you wish to try (my first suggestion), then please follow the instructions from [post=12787706]this post[/post]. You may have to change "rtlwifi" with "rtl818x" (or what it is named in the package). And obviously, you'd be modprob'ing rtl8187 instead of rtl8192cu for which the post is written. I tried downloading the package to give exact reference, but it failed multiple times, crappy gprs connection here..:(

The other thing may be to try compiling the same proprietary driver on an upgraded kernel, which is 3.8.0-30 from default repo, or 3.11 from ppa. That would be my second recommendation (if the above one you've already tried or doesn't work). I tried to search, but couldn't find any significant references on why the kernel panic occurs with certain driver and/or how to fix it.

So if neither the default one, nor the backported one, nor the proprietary one works, then I have no idea what to suggest.

---

### Post by christos3 on 2013-09-14
I just upgraded the kernel to 3.11 (again).
I will see how it goes and i will post back.

Thanks for the help so far.

---

### Post by christos3 on 2013-09-14
Well i still get disconnections but i am tired.
I give up for the time being.

If i manage to find a solution i will post it.

Thanks for the help.

---

### Post by jerome-xqt on 2014-05-19
Hello,

Just try:

sudo iwconfig wlan0 rate 1M auto

---

