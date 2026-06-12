---
title: "Netgear N150 usb WiFi adapter, Ubuntu 12.04"
date: 2014-03-05
forum: Networking &amp; Wireless
---

### Post by Scot_dobson on 2014-03-05
I'm a complete noob to linux and I just switched from windows 7. I'm using a netgearN150 usb WiFi adapter and in windows I was getting ~30Mb/sec in Ubuntu I'm getting about .5Mb/sec. I've looked all over but none of the stuff I tried worked, and most of it was way over my head so I probably did it wrong anyway. What can I do? Thanks.

Edit: if it helps here's the output from iwconfig:
```
scot@ScotsLaptop:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"Router1"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 20:AA:4B:1D:F9:60   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=45/70  Signal level=-65 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:8886   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.
```

---

### Post by phidia on 2014-03-06
Apparently there is a revised driver for that adapter which is referenced at [this forum thread]("http://ubuntuforums.org/showthread.php?t=2036445").

And even though it's odd one of the posters at that thread claims to have fixed the problems with that adapter by getting a driver from [here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false")-odd because it's a realtek website and driver.

I don't know if that will help but it should be worth a try. Sometimes we fumble through things before a solution is found?

---

### Post by varunendra on 2014-03-06
Scot,
Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. It will give us a complete picture of your wifi setup, so that we can find and fix the problems if there are any in the configuration.

---

### Post by Scot_dobson on 2014-03-23
Sorry for the long delay... I took me awhile to figure out how to run the script. Eventually I got the bright idea to read ALL the directions in your post!:p

```


########## wireless info START ##########


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise


##### kernel #####


Linux ScotsLaptop 3.11.0-18-generic #32~precise1-Ubuntu SMP Thu Feb 20 17:54:21 UTC 2014 i686 athlon i386 GNU/Linux


##### lspci #####


00:14.0 Bridge [0680]: NVIDIA Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Kernel driver in use: forcedeth


##### lsusb #####


Bus 001 Device 002: ID 1a40:0201 Terminus Technology Inc. Hub
Bus 001 Device 004: ID 0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA Card Info #####


##### rfkill #####


1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### iw reg get #####


##### interfaces #####


auto lo
iface lo inet loopback


##### iwconfig #####


wlan0     IEEE 802.11bgn  ESSID:"Router1"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:664   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0


##### resolv.conf #####


nameserver 127.0.0.1


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: wlan0  [Router1] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k_htc
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           72 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *Router1:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 56 WPA WPA2
    Router1-guest:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 62
    network1:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 9 WPA
    myqwest0308:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             8.8.8.8
    DNS:             8.8.4.4


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


##### iwlist #####


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"Router1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000001cfc054c
                    Extra: Last beacon: 180ms ago
                    IE: Unknown: 0007526F7574657231
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: DD760050F204104A0001101044000102103B00010310470010071EDD7715B4E5FFF947F3A59524247D102100074C696E6B7379731023000545313230301024000776322E302E30321042000234321054000800060050F2040001101100054531323030100800022688103C0001011049000600372A000120
                    IE: Unknown: DD090010180201F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:off
                    ESSID:"Router1-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000001d0a8f70
                    Extra: Last beacon: 176ms ago
                    IE: Unknown: 000D526F75746572312D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081100000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=16/70  Signal level=-94 dBm  
                    Encryption key:on
                    ESSID:"myqwest0308"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001f30471e1
                    Extra: Last beacon: 404ms ago
                    IE: Unknown: 000B6D79717765737430333038
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AEC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180209F0040000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"network1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001f2ffca6b
                    Extra: Last beacon: 708ms ago
                    IE: Unknown: 00086E6574776F726B31
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AEC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180209F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


##### iwlist channel #####


wlan0     14 channels in total; available frequencies :
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
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency=2.437 GHz (Channel 6)


##### lsmod #####


ath9k_htc              91218  0 
mac80211              534922  1 ath9k_htc
ath9k_common           13619  1 ath9k_htc
ath9k_hw              437399  2 ath9k_htc,ath9k_common
ath                    19435  3 ath9k_htc,ath9k_common,ath9k_hw
cfg80211              416271  3 ath9k_htc,mac80211,ath


##### modinfo #####


filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
firmware:       htc_9271.fw
firmware:       htc_7010.fw
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     62A11322E52E7942593ABEA
alias:          usb:v0CF3p20FFd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04DAp3904d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p017Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApA704d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9018d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p7010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1668p1200d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p7015d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v057Cp8403d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pB002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pB003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v040Dp3801d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp4605d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3350d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3349d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3348d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3346d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3328d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3327d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3A10d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9030d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p1006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p9271d*dc*dsc*dp*ic*isc*ip*in*
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)


filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     2DB88A2876852DC1D8C5A1D
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     6F97CF09431D08603B6A91A
depends:        ath
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     A890CDBC88E6EF28CD751DD
depends:        cfg80211
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 686 


##### modules #####


lp


##### blacklist #####


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


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


##### udev rules #####


# PCI device 0x10de:/sys/devices/pci0000:00/0000:00:14.0 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x0846:0x9030 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[   13.549732] usb 1-2.1: ath9k_htc: Firmware htc_9271.fw requested
[   13.549888] usbcore: registered new interface driver ath9k_htc
[   14.408486] usb 1-2.1: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[   14.644595] ath9k_htc 1-2.1:1.0: ath9k_htc: HTC initialized with 33 credits
[   14.836351] ath9k_htc 1-2.1:1.0: ath9k_htc: FW Version: 1.3
[   14.836359] ath: EEPROM regdomain: 0x60
[   14.836363] ath: EEPROM indicates we should expect a direct regpair map
[   14.836367] ath: Country alpha2 being used: 00
[   14.836369] ath: Regpair used: 0x60
[   24.341534] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.600924] wlan0: authenticate with <MAC address removed>
[   27.744796] wlan0: send auth to <MAC address removed> (try 1/3)
[   27.746871] wlan0: authenticated
[   27.748077] wlan0: associate with <MAC address removed> (try 1/3)
[   27.752001] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[   27.755609] wlan0: associated
[   27.755654] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3319.586916] wlan0: deauthenticated from <MAC address removed> (Reason: 7)
[ 3320.749062] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3321.412824] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3324.525702] wlan0: authenticate with <MAC address removed>
[ 3324.676135] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3324.679465] wlan0: authenticated
[ 3324.680207] wlan0: associate with <MAC address removed> (try 1/3)
[ 3324.684225] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 3324.689234] wlan0: associated
[ 3324.689326] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3331.453416] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3331.737316] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3332.406674] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3368.380226] usb 1-2.1: ath9k_htc: USB layer deinitialized
[ 3373.802813] usb 1-6: ath9k_htc: Firmware htc_9271.fw requested
[ 3374.093173] usb 1-6: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[ 3374.328281] ath9k_htc 1-6:1.0: ath9k_htc: HTC initialized with 33 credits
[ 3374.519162] ath9k_htc 1-6:1.0: ath9k_htc: FW Version: 1.3
[ 3374.519178] ath: EEPROM regdomain: 0x60
[ 3374.519184] ath: EEPROM indicates we should expect a direct regpair map
[ 3374.519192] ath: Country alpha2 being used: 00
[ 3374.519196] ath: Regpair used: 0x60
[ 3374.669394] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3377.725197] wlan0: authenticate with <MAC address removed>
[ 3377.875493] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3377.877749] wlan0: authenticated
[ 3377.880464] wlan0: associate with <MAC address removed> (try 1/3)
[ 3377.884337] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 3377.888138] wlan0: associated
[ 3377.888230] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3384.289625] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3384.508892] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3385.247926] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3426.168417] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3426.648720] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3426.996473] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3428.877962] wlan0: authenticate with <MAC address removed>
[ 3429.039228] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3429.042094] wlan0: authenticated
[ 3429.044112] wlan0: associate with <MAC address removed> (try 1/3)
[ 3429.047877] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 3429.051960] wlan0: associated
[ 3429.052182] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############



```

---

### Post by varunendra on 2014-03-24
> **Scot_dobson said:**
> ```

  Wireless Access Points (* = current AP)
    ***Router1**:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 56 **[COLOR="#FF0000"]WPA WPA2[/COLOR]**
....
....
wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    **[COLOR="#FF0000"]Channel:6[/COLOR]**
                    ....
                    IE: WPA Version 1
                        Group Cipher : **[COLOR="#FF0000"]TKIP[/COLOR]**

```
First of all, please change the encryption type in the router from its current WPA/WPA2 mixed mode with **[COLOR="#FF0000"]TKIP[/COLOR]** to pure WPA2-PSK with AES (CCMP). No mixed mode, no TKIP.

Then, try these, one at a time, try the next only if one doesn't work -

**1)** Change the channel in the router to 1 or 11. Currently it is set to channel 6. Make sure to reboot the router after saving any changes (including the above change of encryption type).

**2)** Create a conf file to load the driver with a parameter "nohwcrypt=1". This command will do it for you -
```
echo "options ath9k_htc nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k_htc.conf
```
This change will take effect after a reboot.

**3)** Try explicitly defining your Country Code for respective RegDomain settings with the following command -
```
sudo iw reg set *[COLOR="#0000CD"]**US**[/COLOR]*
```
Replace *[COLOR="#0000CD"]**US**[/COLOR]* with your own country's regdomain code. Refer to this table to find the code for your country : [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table)
This will be a temporary change that will be lost at next boot. So you will need to re-run the above command if you reboot your computer. If it helps, we can make it permanent.

**4)** If none of the above seem to help, try a newer version of the driver as suggested in this post : [http://ubuntuforums.org/showpost.php?p=12963298](http://ubuntuforums.org/showpost.php?p=12963298)

Once again, try one at a time, and proceed to next solution only if the previous one didn't work. While doing so, you do not need to revert the previous change. In fact it is highly recommended to keep the change of encryption as recommended even if it doesn't help.

Let us know which one works, if any.

---

### Post by Scot_dobson on 2014-03-24
Sorry, I only see wpa/wpa2 personal or wpa/wpa2 enterprise. Where would I go to do wpa2-psk?

---

### Post by varunendra on 2014-03-24
Do you have an option that says only "**WPA2**" ? That's it. "PSK" part is automatically implemented.

---

### Post by Scot_dobson on 2014-03-24
Nope, just the mixed personal or enterprise options. Am I looking in the right place? I'm going network tools -> devices -> configure(wlan0) -> wireless -> my access point -> edit -> wireless security.

---

### Post by varunendra on 2014-03-24
Ah, I should have realized. It is not something to be changed in your computer, it is a change that needs to be done in the router.

Please refer to your router's manual to see how to access its admin control web-interface and change those settings.

---

### Post by Scot_dobson on 2014-03-25
Oh! Okay, there isn't an option for wpa2-psk, but I looked it up and wpa2-personal is the same thing right? Also, I'll have to clear it with my Dad before I mess with the router, I'm usually not allowed to play around with the network which is why I'm so clueless with it.

---

### Post by varunendra on 2014-03-25
> **Scot_dobson said:**
> Oh! Okay, there isn't an option for wpa2-psk, but I looked it up and wpa2-personal is the same thing right? Right.

> Also, I'll have to clear it with my Dad before I mess with the router
Probably he'll trust a professional advice from Intel more than one coming from a volunteer on a forum : [https://communities.intel.com/thread/46704](https://communities.intel.com/thread/46704) :)

---

### Post by Scot_dobson on 2014-04-20
So I did all that stuff, I had to revert to WPA mixed though because some of my stuff actually used it, most things actually made it worse but the new driver sped it up about 5x faster, I get a constant 1MB/sec download and 5MB/sec upload. Do you have any idea why my upload speed would be so much faster than the download speed? I thought it was supposed to be the otherway around because people download more than upload. Anyway thanks for all the help, my computer is much more usable in linux now!

---

### Post by varunendra on 2014-04-21
> **Scot_dobson said:**
> Do you have any idea why my upload speed would be so much faster than the download speed? I thought it was supposed to be the other way around..

It is usually indeed the other way around, and I can't say for sure why your download speed is slower than upload speed. Can you upload a fresh report of the wireless_script showing the current status please? That may help determining if there is something else we can try to optimize the performance.

---

### Post by Scot_dobson on 2014-04-21
Okay, thanks! Here's the wireless script again.
```


########## wireless info START ##########


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise


##### kernel #####


Linux ScotsLaptop 3.11.0-19-generic #33~precise1-Ubuntu SMP Wed Mar 12 21:17:09 UTC 2014 i686 athlon i386 GNU/Linux


##### lspci #####


00:14.0 Bridge [0680]: NVIDIA Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Kernel driver in use: forcedeth


##### lsusb #####


Bus 001 Device 002: ID 1a40:0201 Terminus Technology Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]


##### PCMCIA Card Info #####


##### rfkill #####


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### iw reg get #####


##### interfaces #####


auto lo
iface lo inet loopback


##### iwconfig #####


wlan0     IEEE 802.11bgn  ESSID:"Router1"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=28.9 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=31/70  Signal level=-79 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:24   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0


##### resolv.conf #####


nameserver 127.0.0.1
search hsd1.ut.comcast.net


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: wlan0  [Router1] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k_htc
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           28 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Router1-guest:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47
    *Router1:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 36 WPA WPA2
    myqwest0308:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    network1:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA


  IPv4 Settings:
    Address:         192.168.1.131
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             75.75.76.76
    DNS:             75.75.75.75
    DNS:             192.168.1.1


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


##### iwlist #####


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Router1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000146e1687a9
                    Extra: Last beacon: 232ms ago
                    IE: Unknown: 0007526F7574657231
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: DD760050F204104A0001101044000102103B00010310470010071EDD7715B4E5FFF947F3A59524247D102100074C696E6B7379731023000545313230301024000776322E302E30321042000234321054000800060050F2040001101100054531323030100800022688103C0001011049000600372A000120
                    IE: Unknown: DD090010180202F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:off
                    ESSID:"Router1-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001476c87ae5
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 000D526F75746572312D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081100000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"myqwest0308"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000850cd9a37
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 000B6D79717765737430333038
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AEC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B00010310470010607C6895F6511206722D8C6C154FF3DF1021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D4150100800020084103C000101
                    IE: Unknown: DD090010180207F0040000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=15/70  Signal level=-95 dBm  
                    Encryption key:on
                    ESSID:"network1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000850cd849d
                    Extra: Last beacon: 1512ms ago
                    IE: Unknown: 00086E6574776F726B31
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AEC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180207F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


##### iwlist channel #####


wlan0     14 channels in total; available frequencies :
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
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency=2.412 GHz (Channel 1)


##### lsmod #####


ath9k_htc              91322  0 
mac80211              534922  1 ath9k_htc
ath9k_common           13619  1 ath9k_htc
ath9k_hw              437399  2 ath9k_htc,ath9k_common
ath                    19435  3 ath9k_htc,ath9k_common,ath9k_hw
cfg80211              416271  3 ath9k_htc,mac80211,ath


##### modinfo #####


filename:       /lib/modules/3.11.0-19-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
firmware:       htc_9271.fw
firmware:       htc_7010.fw
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     E29A56ECDADF6F275F92AC4
alias:          usb:v0CF3p20FFd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04DAp3904d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p017Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApA704d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9018d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p7010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1668p1200d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p7015d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v057Cp8403d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pB002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pB003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v040Dp3801d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp4605d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3350d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3349d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3348d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3346d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3328d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3327d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3A10d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9030d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p1006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p9271d*dc*dsc*dp*ic*isc*ip*in*
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
intree:         Y
vermagic:       3.11.0-19-generic SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


filename:       /lib/modules/3.11.0-19-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     2DB88A2876852DC1D8C5A1D
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.11.0-19-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.11.0-19-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     6F97CF09431D08603B6A91A
depends:        ath
intree:         Y
vermagic:       3.11.0-19-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.11.0-19-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     A890CDBC88E6EF28CD751DD
depends:        cfg80211
intree:         Y
vermagic:       3.11.0-19-generic SMP mod_unload modversions 686 


##### modules #####


lp


##### blacklist #####


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


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


##### udev rules #####


# PCI device 0x10de:/sys/devices/pci0000:00/0000:00:14.0 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x0846:0x9030 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# USB device 0x148f:0x5370 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


##### dmesg #####


[   15.027137] ath9k_htc: unknown parameter 'nowcrypt' ignored
[   15.027455] usb 1-2.6: ath9k_htc: Firmware htc_9271.fw requested
[   15.027616] usbcore: registered new interface driver ath9k_htc
[   15.681899] usb 1-2.6: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[   15.917509] ath9k_htc 1-2.6:1.0: ath9k_htc: HTC initialized with 33 credits
[   16.108762] ath9k_htc 1-2.6:1.0: ath9k_htc: FW Version: 1.3
[   16.108770] ath: EEPROM regdomain: 0x60
[   16.108773] ath: EEPROM indicates we should expect a direct regpair map
[   16.108778] ath: Country alpha2 being used: 00
[   16.108780] ath: Regpair used: 0x60
[   25.575320] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.952823] wlan0: authenticate with <MAC address removed>
[   29.095959] wlan0: send auth to <MAC address removed> (try 1/3)
[   29.105784] wlan0: authenticated
[   29.108083] wlan0: associate with <MAC address removed> (try 1/3)
[   29.111675] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   29.115764] wlan0: associated
[   29.115825] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############
```

---

### Post by varunendra on 2014-04-21
As per the report, not only the encryption type is unchanged (still WPA/WPA2 mixed mode, I understand you reverted to it intentionally), but also you are still using the default driver, not the newer one, and there is a typo in the parameter that I suggested to add. So basically there is no change at all!

Suggestions are -

[indent]**1)** Please repeat this command (correctly this time, without typos) to correct the parameter -
```
echo "options ath9k_htc nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k_htc.conf
```
This will overwrite the current file, with correct entry. Your current file (/etc/modprobe.d/ath9k_htc.conf) contains "**[COLOR="#FF0000"]nowcrypt[/COLOR]**", whereas it should be "**nohwcrypt**".

**2)** If the above one doesn't help, please retry compiling and installing the newer driver as originally suggested in point 4 of post #5. Make sure the steps are finished properly, without errors. Then post back the outputs of -
```
modinfo ath9k
modinfo ath9k_htc
```

**3)** Unless you have some really old legacy devices that can't support WPA2, you shouldn't need WPA. So if you can, check your devices again due to which you decided to revert to WPA/WPA2 mixed mode, and if they support WPA2, please convince your dad to change the encryption to pure WPA2-psk with AES, and avoid WPA/WPA2 mixed mode with TKIP. Since there was a typo in your parameter file (pointed out above), whatever 'worse' situations you faced (in Ubuntu only) could be a result of that.[/indent]

---

### Post by Scot_dobson on 2014-04-23
Okay, I did that, but have to wait until I can get on a wired connection to mess with the router again. Heres the output of the wifi module command thingys:
```
scot@ScotsLaptop:~$ modinfo ath9k
filename:       /lib/modules/3.11.0-19-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko
version:        backported from Linux (v3.13.2-0-gfd82174) using backports v3.13.2-1-0-gaef13bc
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     A7623E4A23D648C3DACFE05
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd00003027bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002810bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Fsd00007202bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002130bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000612bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000652bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000642bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd0000302Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003027bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Ebc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Dbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Abc*sc*i*
alias:          pci:v0000168Cd00000036sv00001028sd0000020Ebc*sc*i*
alias:          pci:v0000168Cd00000036sv0000103Csd0000217Fbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000103Csd000018E3bc*sc*i*
alias:          pci:v0000168Cd00000036sv000017AAsd00003026bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd0000213Abc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000662bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000672bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000622bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd00003028bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E069bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd0000302Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003026bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003025bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002812bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002811bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00006671bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000632bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd0000A119bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E068bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002176bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003028bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv000010CFsd00001783bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000064bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000063bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000103Csd00001864bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006641bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006631bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001043sd0000850Ebc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002110bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001969sd00000091bc*sc*i*
alias:          pci:v0000168Cd00000034sv000017AAsd00003214bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000168Csd00003117bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006661bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002116bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001043sd0000850Dbc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00001C01bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00001C00bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001F95bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001195bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001F86bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001186bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00002001bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00002000bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Fsd00007197bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E04Fbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E04Ebc*sc*i*
alias:          pci:v0000168Cd00000032sv000011ADsd00006628bc*sc*i*
alias:          pci:v0000168Cd00000032sv000011ADsd00006627bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001C56sd00004001bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002100bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002C97bc*sc*i*
alias:          pci:v0000168Cd00000032sv000017AAsd00003219bc*sc*i*
alias:          pci:v0000168Cd00000032sv000017AAsd00003218bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C708bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C680bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C706bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Fbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Ebc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Dbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd00004106bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd00004105bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000185Fsd00003027bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000185Fsd00003119bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000168Csd00003122bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000168Csd00003119bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E075bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002152bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd0000126Abc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002126bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001237bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002086bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv00001A3Bsd00002C37bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd00001536bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd0000147Dbc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd0000147Cbc*sc*i*
alias:          pci:v0000168Cd0000002Asv0000185Fsd0000309Dbc*sc*i*
alias:          pci:v0000168Cd0000002Asv00001A32sd00000306bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000011ADsd00006642bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000011ADsd00006632bc*sc*i*
alias:          pci:v0000168Cd0000002Asv0000105Bsd0000E01Fbc*sc*i*
alias:          pci:v0000168Cd0000002Asv00001A3Bsd00001C71bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,mac80211,ath9k_common,compat,cfg80211,ath
vermagic:       3.11.0-19-generic SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
scot@ScotsLaptop:~$ modinfo ath9k_htc
filename:       /lib/modules/3.11.0-19-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
firmware:       htc_9271.fw
firmware:       htc_7010.fw
version:        backported from Linux (v3.13.2-0-gfd82174) using backports v3.13.2-1-0-gaef13bc
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     7CDB3791DCE38672E4D8AC5
alias:          usb:v0CF3p20FFd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04DAp3904d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p017Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApA704d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9018d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p7010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1668p1200d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p7015d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v057Cp8403d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pB002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pB003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v040Dp3801d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp4605d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3350d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3349d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3348d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3346d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3328d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3327d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3A10d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9030d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p1006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p9271d*dc*dsc*dp*ic*isc*ip*in*
depends:        mac80211,ath9k_hw,ath9k_common,compat,ath,cfg80211
vermagic:       3.11.0-19-generic SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)

```

---

### Post by varunendra on 2014-04-24
Okay, the drivers are the newer ones now. I'd be curious to have your feedback on this one, not holding my breath though. :p

---

### Post by Scot_dobson on 2014-04-24
A little difference, I get 1.5Mb/s download and 5Mb/s upload now. It's really strange that my upload is so much faster than download. I wish I knew why. Thanks again for all your help!

Edit: Something interesting I just found: [http://brikis98.blogspot.com/2012/02/got-slow-download-but-fast-upload.html](http://brikis98.blogspot.com/2012/02/got-slow-download-but-fast-upload.html) they're using the same ISP and router as I am, and having the same problem. A quick summery of what it says in case you don't want to read the whole thing, Comcast (the ISP) tags all incoming packets as low priority, so when the router gets it, it does it slowly. Turning off the option on the router to prioritize things gets around that and puts things back to full speed. I'm gonna go try this and report back.

---

### Post by Scot_dobson on 2014-04-24
Success!! I now get 10Mb/s download and 5Mb/s upload. MUCH better! I love life.

---

### Post by varunendra on 2014-04-25
Please mark the thread as [SOLVED] then, and I'm certainly bookmarking your last post about comcast. :)

Interesting, and weird!

**EDIT:**

And now I feel like an ignorant stupid. I have already seen problems with WMM support and I should have remembered that. :|

---

