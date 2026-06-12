---
title: "cannot access the internet while connected to the network wirelessly"
date: 2014-01-14
forum: Networking &amp; Wireless
---

### Post by dfa5000 on 2014-01-14
greetings members and guests :D i'm hoping you can help me with a problem that has so far escaped my ability to solve it. i think it's an interesting one, but with my luck it'll be a simple fix i've just overlooked :o

the issue is that i cannot access the internet while connected to my home network wirelessly. other devices including a non-linux computer and smart television are able to access the internet while connected to the network wirelessly. i can only access the internet while using a wired connection to my home network. but i can access the internet wirelessly using my cell phone as a hotspot.

based on other threads, i've tried what i think are the basic steps so i could really use some help. thanks in advance.

```

dfa5000@NP305E5A:~$ uname -a
Linux NP305E5A 3.2.0-58-generic-pae #88-Ubuntu SMP Tue Dec 3 18:00:02 UTC 2013 i686 athlon i386 GNU/Linux

```
```

dfa5000@NP305E5A:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c624]
    Kernel driver in use: r8169
--
04:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Samsung Electronics Co Ltd Device [144d:4105]
    Kernel driver in use: ath9k

```
```

dfa5000@NP305E5A:~$ iwconfig
lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"69W5F"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:26:B8:78:27:BB   
          Bit Rate=48 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=31/70  Signal level=-79 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:25   Missed beacon:0


eth0      no wireless extensions.

```
```

dfa5000@NP305E5A:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [69W5F] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        E8:11:32:E6:FD:CE

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    DROID RAZR M 3756: Infra, B0:79:94:7D:B5:CE, Freq 2447 MHz, Rate 54 Mb/s, Strength 50 WPA2
    *69W5F:          Infra, 00:26:B8:78:27:BB, Freq 2462 MHz, Rate 54 Mb/s, Strength 41 WPA WPA2

  IPv4 Settings:
    Address:         192.168.0.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1
    DNS:             207.69.188.186

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        E8:03:9A:16:D0:E8

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off

```
```

dfa5000@NP305E5A:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

```
```

dfa5000@NP305E5A:~$ sudo lshw -C network
[sudo] password for dfa5000: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: e8:03:9a:16:d0:e8
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:e000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
  *-network
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: e8:11:32:e6:fd:ce
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-58-generic-pae firmware=N/A ip=192.168.0.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:fea00000-fea7ffff memory:fea80000-fea8ffff

```

---

### Post by r3dd on 2014-01-14
Perhaps it is a router issue. I had the same issue yesterday and to fix it I had to set my routers lease time to 0 so it would forget all of the MAC addresses then I could get on no problem. If you use a static IP scheme for your systems like I do make sure you reset that to 1440 if it works. Wouldn't want another computer getting brought in to the network and creating an IP conflict.

---

### Post by varunendra on 2014-01-15
> **dfa5000 said:**
> ```

  Wireless Access Points (* = current AP)
    DROID RAZR M 3756: Infra, B0:79:94:7D:B5:CE, Freq 2447 MHz, Rate 54 Mb/s, Strength 50 WPA2
    *69W5F:          Infra, 00:26:B8:78:27:BB, Freq 2462 MHz, Rate 54 Mb/s, Strength 41 **[COLOR="#FF0000"]WPA WPA2[/COLOR]**

```

Most of us wireless worms here have a paranoia with the above encryption type - [COLOR="#FF0000"]WPA/WPA2[/COLOR] mixed mode. If the router has N-channel enabled, that may be a definite problem with this encryption type, since it offers high speed traffic while the WPA/WPA2 mixed mode uses TKIP algorithm for encryption which is very inefficient.

Considering the above, please try changing the encryption to pure WPA2-PSK with AES in the router. No mixed mode, no TKIP. If that alone doesn't help, please also try disabling N-channel in the router.

At the driver level in Ubuntu, you may try this (before or after the above changes) -
```
sudo modprobe -rv ath9k
sudo modprobe -v ath9k nohwcrypt=1
```
This would be a temporary change that would be lost at next boot. If it helps, we can make it permanent.

If the above don't help, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

**PS:**
Your route -n output doesn't seem wrong, but I think usually there should also be a route specific to the gateway host. So this may be worth trying -
```
sudo route add 192.168.0.1 wlan0
```
I think you should try this first. If it doesn't make any difference, reboot and try above suggestions.

---

### Post by dfa5000 on 2014-01-15
> **alan.e.redding said:**
> Perhaps it is a router issue. I had the same issue yesterday and to fix it I had to set my routers lease time to 0 so it would forget all of the MAC addresses then I could get on no problem. If you use a static IP scheme for your systems like I do make sure you reset that to 1440 if it works. Wouldn't want another computer getting brought in to the network and creating an IP conflict.
i appreciate that suggestion alan.e.redding, i'll take a look at my router settings. most of them i don't understand but that's just more to learn :)

---

### Post by dfa5000 on 2014-01-15
> **varunendra said:**
> **PS:**
Your route -n output doesn't seem wrong, but I think usually there should also be a route specific to the gateway host. So this may be worth trying -
```
sudo route add 192.168.0.1 wlan0
```
I think you should try this first. If it doesn't make any difference, reboot and try above suggestions.
thank you for the response, Varun. i tried this suggestion first and then changed the router security (WPA2), encryption type (AES), then the 802.11 mode (b+g). i was still experiencing the issue so i tried:
```
sudo modprobe -rv ath9k
sudo modprobe -v ath9k nohwcrypt=1
```
unfortunately still no internet access. next step is the wireless script so i'll do that and report back.

---

### Post by dfa5000 on 2014-01-15
here's the output of the wireless script
```


*************** info trace ***************


***** uname -a *****


Linux NP305E5A 3.2.0-58-generic-pae #88-Ubuntu SMP Tue Dec 3 18:00:02 UTC 2013 i686 athlon i386 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise


***** lspci *****


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c624]
    Kernel driver in use: r8169
--
04:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Samsung Electronics Co Ltd Device [144d:4105]
    Kernel driver in use: ath9k


***** lsusb *****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 2232:1020  
Bus 005 Device 002: ID 0cf3:3004 Atheros Communications, Inc. 


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


***** rfkill *****


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


***** lsmod *****


ath9k                 117356  0 
mac80211              436493  1 ath9k
ath9k_common           13781  1 ath9k
ath9k_hw              391626  2 ath9k,ath9k_common
ath                    19387  3 ath9k,ath9k_common,ath9k_hw
ath3k                  12825  0 
cfg80211              178877  3 ath9k,mac80211,ath
bluetooth             158447  24 rfcomm,bnep,ath3k,btusb


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    69W5F:           Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2
    DROID RAZR M 3756: Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 44 WPA2
    linksys:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA
    2WIRE614:        Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    Rary's Telepathic Bond: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA
    treclub:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    Tenda:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    2WIRE396:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    2WIRE181:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    Nickie:          Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 15 WEP




- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.0.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.0.1
    DNS:             207.69.188.186






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


no-auto-default=<MAC address removed>,


[ifupdown]
managed=false


***** interfaces *****


auto lo
iface lo inet loopback




***** iwlist *****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000266b2b2889
                    Extra: Last beacon: 668ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180201F4
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC address removed>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000024c0b1185
                    Extra: Last beacon: 512ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030108
                    IE: Unknown: 05050002000000
                    IE: Unknown: 07245553200101170201170301170401170501170601170701170801170901170A01160B0116
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A2C0103FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1608000000000200000000000000000000000000000000
                    IE: Unknown: DD180050F2020101810003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"treclub"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001cdb99967f6
                    Extra: Last beacon: 304ms ago
                    IE: Unknown: 0007747265636C7562
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 04 - Address: <MAC address removed>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Nickie"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000473d2db86
                    Extra: Last beacon: 780ms ago
                    IE: Unknown: 00064E69636B6965
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3403051B00000000000000000000000000000000000000
                    IE: Unknown: 3D1603051B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD8E0050F204104A0001101044000102103B0001031047001000000000000010000000A021B7AB1B9A1021000D4E6574676561722C20496E632E10230009574E523130303076321024000456324831104200046E6F6E651054000800060050F20400011011001E574E523130303076322D564328576972656C6573732041502D322E344729100800020086103C000103
                    IE: Unknown: DD050050F20500




***** resolv.conf *****


nameserver 127.0.0.1
search Home


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


filename:       /lib/modules/3.2.0-58-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     5396C6B49418C30B65FDBC1
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,ath9k_common,mac80211,cfg80211,ath
intree:         Y
vermagic:       3.2.0-58-generic-pae SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)


filename:       /lib/modules/3.2.0-58-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     87C8338518A200F45D72110
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.2.0-58-generic-pae SMP mod_unload modversions 686 


filename:       /lib/modules/3.2.0-58-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     5A4F26731216C44D9DA1D5C
depends:        ath
intree:         Y
vermagic:       3.2.0-58-generic-pae SMP mod_unload modversions 686 
parm:           force_new_ani:Force new ANI for AR5008, AR9001, AR9002 (int)


filename:       /lib/modules/3.2.0-58-generic-pae/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     8B429DBE4586F4065E2EA2E
depends:        cfg80211
intree:         Y
vermagic:       3.2.0-58-generic-pae SMP mod_unload modversions 686 


filename:       /lib/modules/3.2.0-58-generic-pae/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     E95D42A737C6E861093264C
alias:          usb:v0489pE036d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0489pE03Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0489pE02Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3pE003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p3121d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3402d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04C5p1330d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0489pE04Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0489pE056d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0489pE04Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3393d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0489pE057d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0930p0219d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3pE005d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3pE004d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3362d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04CAp3008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04CAp3006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04CAp3005d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04CAp3004d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3375d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p817Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p311Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p3008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p3004d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p0036d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v03F0p311Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0489pE027d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0489pE03Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0930p0215d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3pE019d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p3002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p3000d*dc*dsc*dp*ic*isc*ip*
depends:        bluetooth
intree:         Y
vermagic:       3.2.0-58-generic-pae SMP mod_unload modversions 686 




***** udev rules *****


# PCI device 0x168c:0x0032 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


***** dmesg *****


[   22.350634] Bluetooth: Atheros AR30xx firmware driver ver 1.0
[   22.374271] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x350f00)
[   22.725415] ath9k 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.725428] ath9k 0000:04:00.0: setting latency timer to 64
[   22.732609] ath: EEPROM regdomain: 0x65
[   22.732611] ath: EEPROM indicates we should expect a direct regpair map
[   22.732614] ath: Country alpha2 being used: 00
[   22.732616] ath: Regpair used: 0x65
[   22.809253] Registered led device: ath9k-phy0
[   23.725904] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.729380] ADDRCONF(NETDEV_UP): wlan0: link is not ready


****************** done ******************



```

---

### Post by varunendra on 2014-01-18
Sorry for such a delayed response, too short of time these days.

The first suggestion, based on this -
> **dfa5000 said:**
> ```

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          **Power Management:[COLOR="#FF0000"]on[/COLOR]**

```

Please try turning the power management off by -
```
sudo iwconfig wlan0 power off
```
Then check the output of "iwconfig" again. Is the "Power Management" off? Does it help connecting? If not, my next suggestion would be a big step ahead *(because I may not be able to respond back for another few days, hence the big shot at once*) - compiling a much newer driver from kernel 3.12.

To compile the newer driver, make sure the essential components required for compilation are installed beforehand -
```
sudo apt-get install linux-headers-generic build-essential
```

Then,

[INDENT]**1)** Download the "**backports-3.12-1**" backports package from here : [http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/](http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/)

**2)** Copy the downloaded package on your desktop, then Right-click it > Extract here.

**3)** Open a terminal (Ctrl-Alt-T), change to the extracted directory, compile and install the driver as follows -
```
cd Desktop/backports-3.12-1
make defconfig-ath9k
make
sudo make install
```[/INDENT]

This will install the newer driver in your system. Keep an eye on the entire process and report back if you see any errors. If all goes smooth, reboot and see if the newer driver performs any better. If not, you may try the same procedure as above with an even newer backports package from the same above link.

Let us know how it goes, and we may try something else if required (although right now I can't think what else I can try with this driver :P).

---

### Post by dfa5000 on 2014-01-21
Thank you very much, Varun. No worries about the response time, I'm just appreciative you took the time. Like you said, sometimes there's not enough of it to get everything done. :) I'll try your suggestions and update this thread soon.

---

### Post by dfa5000 on 2014-01-23
Unfortunately I'm still experiencing the issue after turning off power management (I'm curious that it was on considering it wasn't in my initial post). So I've decided to do more research before I compile a newer driver; I really need to understand this better than I do now. I also want to take another look at my router; it bugs me that I can access the internet using my phone's wireless but not the router's.

---

### Post by varunendra on 2014-01-24
Would it be sufficient to say that the 'ath9k' driver (and many other wireless drivers) were suffering some serious regressions in kernel versions 3.2 to 3.8 (probably 3.9-10 as well). The newer versions of these driver are much improved, and the one I suggested is reported by many to be working much better.

The backported driver I proposed is the same that you'll get if you install kernel 3.12. If you have a fast internet connection and downloading a full ISO is not a problem for you, you may try downloading 13.10 or 14.04 (not officially released yet, and may see critical changes until officially released) and test them in live mode to make sure the drivers in them work as expected.

---

