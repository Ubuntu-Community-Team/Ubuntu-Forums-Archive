---
title: "Lubuntu 14.04 Intel Pro/Wireless 2200BG on older Dell laptop does not connect"
date: 2014-04-24
forum: Networking &amp; Wireless
---

### Post by Don_Tai on 2014-04-24
Update: April 25 2014 For some unknown reason my wireless came to life and found other networks, but could not find mine, even though the wireless router was within 15'. While experimenting I found out that when I do not broadcast my router's SSID, Lubuntu will not find the network. I reset my router to broadcast the SSID and in Lubuntu "Network Connections" was then able to check the dropdown for BSSID and select my router's Mac address. Once saved in Lubuntu, I was able to stop broadcasting my router's SSID, and Lubuntu was able to then log into my hidden SSID network.

How do I mark this thread closed? Could someone please close this thread?

I hope I can get some help here. I have a 2005 Dell Inspiron 6000 laptop with an Intel Pro/Wireless 2200BG card. I've tried to go through many threads for a solution but could not find one. This laptop used to have a very tired version of XP and the wireless card did work. I did a new install of Lubuntu 14.04 on April 17 2014, and have done all updates since then, using "Software Updater". I have a little xubuntu and less lubuntu experience. Other than Chromium I have not added much new software. I did add some "Manage Networks" applets to the task bar.

Here is all the info from my wireless-info.txt

Any help would be much appreciated. Thanks.

##### release #####

```
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty
```

##### kernel #####

```
Linux Tai 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux
```

##### lspci #####

```
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Inspiron 6000 laptop [1028:0188]
    Kernel driver in use: b44

03:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
    Subsystem: Intel Corporation Dell B130 laptop integrated WLAN [8086:2721]
    Kernel driver in use: ipw2200
```

##### lsusb #####, ##### PCMCIA Card Info #####

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 413c:3016 Dell Computer Corp. Optical 5-Button Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
```

##### rfkill #####

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

##### iw reg get #####

##### interfaces #####

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
```

##### iwconfig #####

```
eth1      IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

##### route #####, ##### resolv.conf #####

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1
search home
```

##### nm-tool #####

```
NetworkManager Tool

State: connected (global)

- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ipw2200
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    zoey:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    Terry & Hannah:  Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    TealDove:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.115
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.2.1
```


##### NetworkManager.state #####

```
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
```

##### NetworkManager.conf #####

```
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false
```

##### iwlist #####

```
eth1      Scan completed :
          Cell 01 - Address: <MAC address removed>
                    ESSID:"TealDove"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=29/100  Signal level=-82 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 236ms ago
          Cell 02 - Address: <MAC address removed>
                    ESSID:"\x00\x00\x00\x00\x00\x00"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=86/100  Signal level=-43 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 116ms ago
          Cell 03 - Address: <MAC address removed>
                    ESSID:"zoey"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 11 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=46/100  Signal level=-73 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 92ms ago
          Cell 04 - Address: <MAC address removed>
                    ESSID:""
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 11 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=44/100  Signal level=-74 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 14120ms ago
          Cell 05 - Address: <MAC address removed>
                    ESSID:"Terry & Hannah"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=39/100  Signal level=-77 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 14040ms ago
          Cell 06 - Address: <MAC address removed>
                    ESSID:""
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 11 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=86/100  Signal level=-43 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 156ms ago
          Cell 07 - Address: <MAC address removed>
                    ESSID:"TealDove-guest"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=27/100  Signal level=-83 dBm  
                    Extra: Last beacon: 228ms ago
          Cell 08 - Address: <MAC address removed>
                    ESSID:"Brazil"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=35/100  Signal level=-79 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 72ms ago
```

##### iwlist channel #####

```
eth1      11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Channel=0
```

##### lsmod #####

```
ipw2200               136401  0 
libipw                 33144  1 ipw2200
lib80211               14040  2 libipw,ipw2200
cfg80211              409394  2 libipw,ipw2200
ssb                    51854  1 b44
```

##### modinfo #####

```
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
firmware:       ipw2200-bss.fw
firmware:       ipw2200-sniffer.fw
firmware:       ipw2200-ibss.fw
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        1.2.2kmprq
description:    Intel(R) PRO/Wireless 2200/2915 Network Driver
srcversion:     6432FDB1497A8B2EC025CB2
alias:          pci:v00008086d00004224sv*sd*bc*sc*i*
alias:          pci:v00008086d00004223sv*sd*bc*sc*i*
alias:          pci:v00008086d00004221sv*sd*bc*sc*i*
alias:          pci:v00008086d00004220sv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Fsv*sd*bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002762bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002761bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002754bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002753bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002752bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002751bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002742bc*sc*i*
alias:          pci:v00008086d00001043sv0000103Csd00002741bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002741bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002732bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002731bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002722bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002721bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002712bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002711bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002702bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002701bc*sc*i*
depends:        cfg80211,libipw,lib80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           associate:auto associate when scanning (default off) (int)
parm:           auto_create:auto create adhoc network (default on) (int)
parm:           led:enable led control on some systems (default 1 on) (int)
parm:           debug:debug output mask (int)
parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
parm:           rtap_iface:create the rtap interface (1 - create, default 0) (int)
parm:           qos_enable:enable all QoS functionalitis (int)
parm:           qos_burst_enable:enable QoS burst mode (int)
parm:           qos_no_ack_mask:mask Tx_Queue to no ack (int)
parm:           burst_duration_CCK:set CCK burst value (int)
parm:           burst_duration_OFDM:set OFDM burst value (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)
parm:           bt_coexist:enable bluetooth coexistence (default off) (int)
parm:           hwcrypto:enable hardware crypto (default off) (int)
parm:           cmdlog:allocate a ring buffer for logging firmware commands (int)
parm:           roaming:enable roaming support (default on) (int)
parm:           antenna:select antenna 1=Main, 3=Aux, default 0 [both], 2=slow_diversity (choose the one with lower background noise) (int)

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
alias:          pci:v000014E4d00004350sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004325sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004324sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D6sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004322sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004321sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004320sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004319sv*sd*bc*sc*i*
alias:          pci:v000014A4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004307sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004306sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004301sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512
```

##### modules #####

```
lp
ipw2000
ipw2200
```

##### blacklist #####

```
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

[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb

[/etc/modprobe.d/libpisock9.conf]
blacklist visor
```

##### udev rules #####

```
# PCI device 0x14e4:0x170c (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4220 (ipw2200)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

```

##### dmesg #####

```
[    1.556098] ssb: Found chip with id 0x4401, rev 0x02 and package 0x00
[    1.556110] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[    1.556117] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[    1.556124] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[    1.596136] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    1.616576] b44 ssb0:0 eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver <MAC address removed>
[   13.513396] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   13.513402] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   13.513671] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   13.829369] ipw2200: Radio Frequency Kill Switch is On:
[   13.839803] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   17.705851] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[  376.000345] b44 ssb0:0 eth0: Link is up at 100 Mbps, full duplex
[  376.000358] b44 ssb0:0 eth0: Flow control is off for TX and off for RX
[  638.000268] b44 ssb0:0 eth0: Link is down
[  707.000367] b44 ssb0:0 eth0: Link is up at 100 Mbps, full duplex
[  707.000380] b44 ssb0:0 eth0: Flow control is off for TX and off for RX
[  795.418349] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready

```

---

