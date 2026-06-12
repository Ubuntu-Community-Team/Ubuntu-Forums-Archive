---
title: "slow internet, unpredictable internet (no issue under windows)"
date: 2014-05-16
forum: Networking &amp; Wireless
---

### Post by gandhi2 on 2014-05-16
Hi there brilliant people,

I recently installed Xubuntu 14.04 on my computer (P4 3ghz, 2gb RAM)

and i'm having issues with the internet being very unpredictable and slow....... i'm not really sure what to do?

I'm using a USB WIFI DONGLE (buffalo).

if i switch back to Windows the internet is very reliable.

any suggestion would be awesome!!

Gandhi

---

### Post by varunendra on 2014-05-16
While you are connected via the USB dongle, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by gandhi2 on 2014-05-18
here it is:
```

########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux gandhi-ATI-Xpress200 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:31:42 UTC 2014 i686 i686 i686 GNU/Linux

##### lspci #####

02:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8139]
    Kernel driver in use: 8139too

##### lsusb #####

Bus 001 Device 005: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader
Bus 001 Device 002: ID 0411:0066 BUFFALO INC. (formerly MelCo., Inc.) WLI-U2-KG54 WLAN
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 045e:0029 Microsoft Corp. IntelliMouse Optical
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11bg  ESSID:"Gspot"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:67   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [Gspot] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2500usb
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
    Lucan Household: Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 100 WPA2
    *Gspot:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 88 WPA2
    VM958760-2G:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    A10Wire:         Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 27 WPA
    VM533959-2G:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.157
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-33 dBm  
                    Encryption key:on
                    ESSID:"Gspot"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002eadd4ba6
                    Extra: Last beacon: 1888ms ago
                    IE: Unknown: 00054773706F74
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A2C0001FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000300000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD610050F204104A0001101044000102103B00010310470010F8273176EF7B5408B7AF2F64EC3466CA10210001201023000120102400012010420001201054000800000000000000001011000120100800022108103C0001011049000600372A000120
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"VM958760-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003a0373e180
                    Extra: Last beacon: 21080ms ago
                    IE: Unknown: 000B564D3935383736302D3247
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAD011BFFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1601001500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=70/70  Signal level=-29 dBm  
                    Encryption key:on
                    ESSID:"Lucan Household"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000164a2eb4e1d
                    Extra: Last beacon: 1504ms ago
                    IE: Unknown: 000F4C7563616E20486F757365686F6C64
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 331AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1607071500000000000000000000000000000000000000
                    IE: Unknown: 341607071500000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD990050F204104A0001101044000102103B0001031047001000000000000010000000A0F3C156C5681021000754502D4C494E4B10230009544C2D57523834314E10240003382E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523834314E100800020086103C000101104900140024E26002000101600000020001600100020001
          Cell 04 - Address: <MAC address removed>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"A10Wire"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000e46b20d14c
                    Extra: Last beacon: 792ms ago
                    IE: Unknown: 000741313057697265
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030109
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706545720010D10
                    IE: Unknown: DD270050F204104A000110104400010110470010BC329E001DD811B2860100507F6CD0D8103C000100
                    IE: Unknown: 050400010060
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1609070700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500011B7A12
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3409070700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4300000000

##### iwlist channel #####

wlan0     11 channels in total; available frequencies :
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
          Current Frequency=2.437 GHz (Channel 6)

##### lsmod #####

rt2500usb              30861  0 
rt2x00usb              20041  1 rt2500usb
rt2x00lib              48886  2 rt2x00usb,rt2500usb
mac80211              545990  2 rt2x00lib,rt2x00usb
cfg80211              409394  2 mac80211,rt2x00lib

##### modinfo #####

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
license:        GPL
description:    Ralink RT2500 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     B83335DDC3F4A64249F1603
alias:          usb:v5A57p0260d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0F88p3012d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0EB0p9020d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0769p11F3d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v114Bp0110d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0707pEE13d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0681p3C06d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v079Bp004Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp9020d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp2570d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp1706d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p6869d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p6865d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p6861d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0097d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p008Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0067d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0066d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p005Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE000d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1044p8007d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1044p8001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C00d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C02d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p001Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p0011d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p000Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp7051d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp7050d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1707d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1706d*dc*dsc*dp*ic*isc*ip*in*
depends:        rt2x00lib,rt2x00usb
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:A1:7E:EF:58:C6:AC:5E:9A:85:71:2C:92:08:DF
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     44768071492503F8EFE1EED
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:A1:7E:EF:58:C6:AC:5E:9A:85:71:2C:92:08:DF
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     C57F87A3569F5363E79FD42
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:A1:7E:EF:58:C6:AC:5E:9A:85:71:2C:92:08:DF
sig_hashalgo:   sha512

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

##### udev rules #####

# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x:0x (rt2500usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   11.371458] ieee80211 phy0: rt2x00_set_chip: Info - Chipset detected - rt: 2570, rf: 0005, rev: 0005
[   14.046629] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.047733] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.497118] wlan0: authenticate with <MAC address removed>
[   16.543489] wlan0: send auth to <MAC address removed> (try 1/3)
[   16.546563] wlan0: authenticated
[   16.549381] wlan0: associate with <MAC address removed> (try 1/3)
[   16.552239] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[   16.554298] wlan0: associated
[   16.554360] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   16.748350] wlan0: deauthenticating from <MAC address removed> by local choice (reason=2)
[   16.782343] wlan0: authenticate with <MAC address removed>
[   16.799414] wlan0: send auth to <MAC address removed> (try 1/3)
[   16.801150] wlan0: authenticated
[   16.808060] wlan0: associate with <MAC address removed> (try 1/3)
[   16.812489] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[   16.822692] wlan0: associated
[   26.084077] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[   26.084090] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[   30.972031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[   30.972041] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[   35.208028] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[   35.208038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[   39.444032] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[   39.444042] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[   48.872031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[   48.872040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[   53.108029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[   53.108038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[   57.344030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[   57.344039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[   61.580029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[   61.580038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[   65.912031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[   65.912039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[   70.152031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[   70.152040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[   74.442738] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[   74.442751] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[   78.820043] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[   78.820054] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[   83.060031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[   83.060040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[   87.296028] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[   87.296037] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[   95.720036] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[   95.720045] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[   99.960056] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[   99.960069] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  104.568043] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  104.568053] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  110.092040] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  110.092050] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  114.576053] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  114.576063] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  119.108035] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  119.108045] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  123.480116] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  123.480134] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  124.656070] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  129.964057] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  129.964072] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  134.228043] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  134.228052] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  138.556075] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  138.556093] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  142.792046] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  142.792056] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  147.040083] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  147.040098] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  151.276054] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  151.276068] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  159.668043] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  159.668053] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  164.328163] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  164.328180] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  168.980080] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  168.980096] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  173.256039] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  173.256049] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  177.592073] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  177.592085] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  181.852045] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  181.852054] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  186.340042] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  186.340052] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  190.728068] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  190.728081] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  195.064069] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  195.064079] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  201.404100] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  201.404117] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  206.252037] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  206.252046] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  210.680037] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  210.680046] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  214.916040] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  214.916050] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  219.192061] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  219.192083] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  225.196074] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  225.196088] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  229.552053] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  229.552065] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  240.064033] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  240.064043] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  244.392035] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  244.392044] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  250.528039] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  250.528052] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  256.300069] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  256.300083] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  261.040047] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  261.040056] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  265.500075] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  265.500095] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  270.248048] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  270.248058] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  276.152049] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  276.152059] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  282.604039] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  282.604051] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  282.683605] ieee80211 phy0: rt2x00usb_watchdog_tx_dma: Warning - TX queue 0 DMA timed out, invoke forced forced reset
[  287.700065] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  287.700076] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  293.056032] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  293.056042] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  297.820041] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  297.820051] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  302.156033] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  302.156042] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  306.484032] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  306.484041] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  310.856030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  310.856040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  315.096032] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  315.096041] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  323.216032] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  323.216041] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  328.472030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  328.472039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  333.628030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  333.628040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  342.076030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  342.076040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  346.472033] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  346.472042] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  350.808028] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  350.808037] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  355.108075] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  355.108084] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  359.344030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  359.344038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  363.580031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  363.580040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  367.816029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  367.816038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  372.052030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  372.052039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  376.288037] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  376.288049] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  380.724030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  380.724039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  384.964041] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  384.964050] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  389.228029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  389.228038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  393.640029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  393.640039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  397.876027] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  397.876036] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  402.116032] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  402.116041] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  406.356028] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  406.356037] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  410.600030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  410.600039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  414.936032] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  414.936041] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  419.172030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  419.172039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  423.408032] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  423.408042] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  427.644029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  427.644038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  431.884029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  431.884038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  436.120032] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  436.120041] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  440.360031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  440.360040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  444.596031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  444.596041] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  448.832030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  448.832039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  453.072060] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  453.072073] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  463.256053] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  463.256063] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  468.844032] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  468.844041] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  473.188029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  473.188039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  477.492030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  477.492039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  481.792046] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  481.792055] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  486.128029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  486.128038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  490.392029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  490.392038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  494.728029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  494.728038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  499.248030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  499.248039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  503.680029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  503.680039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  508.312029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  508.312038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  512.608030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  512.608039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  517.980032] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  517.980041] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  522.492029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  522.492038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  526.832047] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  526.832056] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  531.072029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  531.072038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  535.348030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  535.348039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  539.856029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  539.856038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  544.092041] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  544.092051] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  548.328029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  548.328038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  552.564029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  552.564038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  556.800029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  556.800038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  561.040093] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  561.040105] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  565.484029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  565.484038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  570.396029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  570.396038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  575.400029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  575.400038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  583.820030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  583.820039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  588.156030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  588.156039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  592.392031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  592.392040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  596.728029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  596.728038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  600.964030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  600.964039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  605.292030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  605.292039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  609.696029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  609.696038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  615.236030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  615.236039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  619.732029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  619.732038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  624.028037] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  624.028047] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  628.364029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  628.364038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  632.688029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  632.688038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  636.924030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  636.924039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  642.228029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  642.228038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  646.772029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  646.772038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  651.012037] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  651.012047] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  655.248030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  655.248039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  659.584029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  659.584038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  663.920032] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  663.920041] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  668.156047] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  668.156056] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  672.400032] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  672.400041] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  676.872029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  676.872038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  681.376030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  681.376039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  685.712028] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  685.712037] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  690.048029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  690.048038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  694.284028] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  694.284037] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  698.520028] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  698.520037] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  706.980032] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  706.980041] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  711.216029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  711.216037] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  715.452029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  715.452038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  719.688029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  719.688038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  723.924029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  723.924038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  728.160029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  728.160038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  732.400028] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  732.400037] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  736.636032] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  736.636041] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  740.872031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  740.872040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  745.116031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  745.116040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  749.352029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  749.352038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  753.592031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  753.592041] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  757.872029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  757.872038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  762.112031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  762.112040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  766.348031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  766.348040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  770.584029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  770.584038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  774.820030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  774.820040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  779.056031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  779.056040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  783.296030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  783.296040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  787.532029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  787.532038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  791.768030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  791.768039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  796.004037] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  796.004047] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  800.240034] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  800.240043] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  804.512031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  804.512040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  809.364029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  809.364038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  814.092042] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  814.092052] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  818.332030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  818.332039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  826.992032] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  826.992041] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  831.304030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  831.304039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  835.640030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  835.640039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  839.976062] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  839.976073] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  844.212032] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  844.212041] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  849.128030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  849.128040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  853.364030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  853.364039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  857.936030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  857.936039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  862.280029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  862.280038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  866.948030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  866.948039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  871.184028] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  871.184038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  875.520030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  875.520039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  879.856030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  879.856039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  884.156030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  884.156040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  888.392029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  888.392038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  892.732029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  892.732038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  896.976034] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  896.976043] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  901.220031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  901.220040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  905.556029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  905.556039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  909.792036] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  909.792048] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  914.296030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  914.296040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  918.540028] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  918.540037] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  922.880045] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  922.880055] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  927.116031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  927.116040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  931.364030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  931.364039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  935.648049] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  935.648059] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  944.420086] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  944.420101] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  949.076058] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  949.076070] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  953.412080] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  953.412109] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  957.748078] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  957.748101] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  962.088041] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  962.088056] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  966.324032] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  966.324042] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  971.004090] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  971.004110] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  975.980042] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  975.980052] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  980.220041] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  980.220051] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  984.556084] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  984.556096] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  989.108045] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  989.108057] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  993.348076] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  993.348093] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[  997.784043] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[  997.784053] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1002.120035] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1002.120045] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1006.356094] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1006.356105] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1010.924038] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1010.924047] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1015.928058] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1015.928071] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1020.936040] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1020.936050] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1025.940103] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1025.940120] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1030.176043] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1030.176053] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1034.512051] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1034.512062] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1038.848041] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1038.848051] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1043.088048] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1043.088058] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1048.392051] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1048.392062] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1052.652072] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1052.652086] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1057.660058] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1057.660071] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1066.084043] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1066.084053] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1070.324100] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1070.324119] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1074.664098] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1074.664122] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1078.900097] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1078.900118] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1083.148044] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1083.148056] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1087.392059] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1087.392071] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1091.628041] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1091.628053] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1095.968047] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1095.968057] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1100.220068] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1100.220087] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1104.460089] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1104.460113] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1108.820086] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1108.820104] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1113.056105] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1113.056121] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1117.296100] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1117.296126] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1121.568034] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1121.568044] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1125.820083] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1125.820104] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1130.064088] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1130.064116] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1134.312056] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1134.312070] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1138.548040] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1138.548051] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1142.800035] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1142.800045] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1147.040043] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1147.040053] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1151.276059] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1151.276072] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1155.516039] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1155.516049] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1159.792054] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1159.792065] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1164.028045] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1164.028058] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1169.872094] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1169.872111] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1174.108069] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1174.108082] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1178.344038] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1178.344050] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1182.766765] wlan0: disassociated from <MAC address removed> (Reason: 4)
[ 1182.901433] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1184.116782] wlan0: authenticate with <MAC address removed>
[ 1184.148927] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1184.152485] wlan0: authenticated
[ 1184.156060] wlan0: associate with <MAC address removed> (try 1/3)
[ 1184.158862] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 1184.160462] wlan0: associated
[ 1188.336074] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1188.336095] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1192.584074] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1192.584095] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1197.144041] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1197.144052] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1201.476058] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1201.476070] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1208.352031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1208.352040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1214.296031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1214.296040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1218.540030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1218.540039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1222.856030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1222.856039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1227.096043] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1227.096052] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1231.332100] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1231.332110] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1235.668030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1235.668039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1239.904029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1239.904038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1244.140030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1244.140039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1248.380028] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1248.380037] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1252.616031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1252.616040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1256.852031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1256.852040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1261.088027] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1261.088036] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1265.324030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1265.324040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1269.804033] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1269.804042] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1274.100033] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1274.100043] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1278.336030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1278.336039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1282.616030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1282.616039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1286.856030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1286.856039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1291.092040] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1291.092049] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1295.396030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1295.396039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1304.428031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1304.428040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1308.664028] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1308.664036] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1312.908029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1312.908038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1317.152031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1317.152041] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1321.396030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1321.396039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1325.632031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1325.632041] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1329.868029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1329.868038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1334.380035] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1334.380045] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1338.620030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1338.620039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1342.916070] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1342.916084] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1347.196055] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1347.196066] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1351.440073] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1351.440093] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1355.724042] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1355.724052] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1363.484041] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1363.484050] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1369.064034] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1369.064044] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1374.244035] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1374.244045] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1378.480032] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1378.480041] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1382.720031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1382.720040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1386.956030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1386.956039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1391.192031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1391.192040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1395.432031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1395.432040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1399.672030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1399.672039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1403.908028] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1403.908037] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1408.144028] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1408.144037] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1412.384030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1412.384039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1416.620030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1416.620039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1426.300029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1426.300038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1430.572028] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1430.572037] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1434.812029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1434.812038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1439.048031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1439.048040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1443.372028] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1443.372038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1447.712030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1447.712039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1451.976031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1451.976040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1456.212028] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1456.212037] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1460.448030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1460.448040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1464.692059] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1464.692069] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1468.932045] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1468.932055] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1473.168031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1473.168040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1477.420038] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1477.420050] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1481.836033] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1481.836043] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1486.488042] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1486.488052] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1491.188040] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1491.188052] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1496.812044] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1496.812054] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1504.040044] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1504.040055] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1510.200043] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1510.200053] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1517.492032] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1517.492040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1522.824030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1522.824040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1527.140032] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1527.140041] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1531.376032] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1531.376041] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1535.612031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1535.612040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1544.372030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1544.372040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1548.612030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1548.612039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1552.944027] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1552.944035] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1557.180030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1557.180039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1561.416030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1561.416039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1565.652030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1565.652039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1569.888031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1569.888040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1575.236030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1575.236040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1579.472031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1579.472040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1583.708029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1583.708038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1587.972040] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1587.972049] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1592.208031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1592.208040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1596.544035] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1596.544045] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1600.780030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1600.780040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1605.016038] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1605.016049] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1609.256030] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1609.256039] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1613.492029] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1613.492038] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1617.732041] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1617.732050] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1622.308031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1622.308040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1626.644031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1626.644041] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1631.020043] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1631.020055] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1635.292050] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1635.292060] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1639.584050] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1639.584059] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1643.920045] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1643.920055] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1648.224031] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1648.224040] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1663.016042] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1663.016052] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup
[ 1671.664048] ieee80211 phy0: rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16)
[ 1671.664057] ieee80211 phy0: rt2x00lib_autowakeup: Error - Device failed to wakeup

########## wireless info END ############


```

---

### Post by varunendra on 2014-05-20
Please try -
```
sudo iwconfig wlan0 power off
```
and try changing the channel in the router to channel 1 or 11 as they usually offer better signal quality. Also check if there is a service/feature called "WMM" enabled on the router. If it is, disable it. It is usually found with/under QoS setting.

Along with above changes, also try a driver parameter in Ubuntu -
```
sudo modprobe -rv rt2500usb
sudo modprobe -v rt2500usb nohwcrypt=Y
```
This would be a temporary change that would be lost at next boot. If it helps, we can make it permanent.

If none of these helps, please follow the instructions in this post to run an experimental version of the wireless_script, and post back the fresh report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by gandhi2 on 2014-05-21
Hi there thank you for this !!!! WOOP WOOP!!!! this worked ```

sudo iwconfig wlan0 power off
```

how do i make it permanent? and if you like i'd love to know what that piece of code actually did?

thank you again

---

### Post by varunendra on 2014-05-21
> **gandhi2 said:**
> how do i make it permanent? and if you like i'd love to know what that piece of code actually did?

It turned 'Power Management' on the adapter off. Power Management causes the device to go into a low power or 'sleep' state (to save power) whenever it thinks that the device is idle. This can make the link quality to be poor and unstable. Turning it off makes the device operate in full power mode all the time (unless you manually switch off the wireless), thus keeping the link healthy all the time (at least the part that depends on signal strength).

Usually, it should already be permanent, once turned off by 'iwconfig' (the command you ran). But if it turns on automatically, there are more than one possible ways to turn it off. I am listing them in order of recommendation -

[Try these ONLY IF the power management is automatically turning on again, which can be confirmed by the output of command "iwconfig"]

[INDENT]**1)** Try creating a blank file 'wireless' in /etc/pm/power.d/ directory -
```
sudo touch /etc/pm/power.d/wireless
```
Then turn the power management off with the previous command (sudo iwconfig wlan0 power off), and see if it remains off (even across reboots). If not, try the next trick -

**2)** Turn the above blank file into a deliberate script, and make it executable -
```
echo "/sbin/iwconfig wlan0 power off" | sudo tee /etc/pm/power.d/wireless
sudo chmod +x /etc/pm/power.d/wireless
```
Then run the 'iwconfig wlan0 power off' command manually to turn it off, and see if it remains off this time.

**3)** If not, then the crudest trick, with no better chance of success (it'll work during startup for sure, but not once the system comes into running mode) -
```
sudo sed -i '/^exit 0/i /sbin/iwconfig wlan0 power off' /etc/rc.local
```
This will insert the "/sbin/iwconfig wlan0 power off" command into /etc/rc.local file (above last line - "exit 0"), thus making it run everytime the system boots.[/INDENT]

Try them in order as suggested, and let me know (for experience's sake) which one works. No need to try 2 or 3 if the first one works.

---

