---
title: "Random disconnects and dramatic speed drops Encore wireless PCI-E ."
date: 2014-06-09
forum: Networking &amp; Wireless
---

### Post by Mike1977 on 2014-06-09
Running Ubuntu 14.04 on a custom build. I have Encore wireless N300 PCI-E Adapter ( seen [here]("http://www.encore-usa.com/us/support/ENEWI-2XN42") ) The driver is available for download at this link as well. I am reading that a common fix for connection issues is to uninstall/reinstall the wireless driver.  But before I jump the gun, I wonder if there is some other things I should look at first? Also, once downloaded, how do I install? Is it in "Software/updates>Additional Drivers"?
It only drops connection for a second, and then re connects. The problem is, I lose my VPN connection and it then reconnects clean. (WiFi drops regardless of vpn or open) 
Looking at the supported wireless cards sticky on this forum,   and the wiki link, but it looks like my wireless card could be one of 2 entries. Not sure which path to go down.

```
lspci

Network controller: Realtek Semiconductor Co., Ltd. RTL8192CE PCIe Wireless Network Adapter (rev 01
```

```
lsmod | grep rtl

rtl8192ce              53550  0 
rtl_pci                26690  1 rtl8192ce
rtlwifi                63475  2 rtl_pci,rtl8192ce
rtl8192c_common        53172  1 rtl8192ce
mac80211              626557  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              484040  2 mac80211,rtlwifi
```

```
iwconfig | grep Power
eth0      no wireless extensions.

lo        no wireless extensions.

          Bit Rate=144.4 Mb/s   Tx-Power=20 dBm   
          Power Management:off
```

```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script 

########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux mike-System-Product-Name 3.13.0-29-generic #53-Ubuntu SMP Wed Jun 4 21:00:20 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 09)
    Subsystem: ASUSTeK Computer Inc. P8H77-I Motherboard [1043:8505]
    Kernel driver in use: r8169

06:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192CE PCIe Wireless Network Adapter [10ec:8178] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8192CE PCIe Wireless Network Adapter [10ec:8178]
    Kernel driver in use: rtl8192ce
07:00.0 USB controller [0c03]: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller [1b21:1042]

##### lsusb #####

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04d9:a06b Holtek Semiconductor, Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 03f0:8904 Hewlett-Packard DeskJet 6940 series
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11bgn  ESSID:"HighMoon"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=144.4 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=20 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:88   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #####

nameserver 127.0.1.1
search hsd1.pa.comcast.net

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0  [HighMoon] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           144 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    HighMoon-guest:  Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 97
    *HighMoon:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2

  IPv4 Settings:
    Address:         192.168.1.146
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             75.75.76.76
    DNS:             75.75.75.75
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
                    Quality=70/70  Signal level=26 dBm  
                    Encryption key:on
                    ESSID:"HighMoon"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 0008486967684D6F6F6E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: DD810050F204104A00011010440001021041000100103B0001031047001002519461683B1AF5B2843176671BB6DB102100074C696E6B7379731023000D4C696E6B7379732045343230301024000776312E302E30321042000234321054000800060050F20400011011000D4C696E6B737973204534323030100800020084103C000103
                    IE: Unknown: DD090010180203F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=26 dBm  
                    Encryption key:off
                    ESSID:"HighMoon-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 000E486967684D6F6F6E2D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081100000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

##### iwlist channel #####

wlan0     13 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)

##### lsmod #####

rtl8192ce              53550  0 
rtl_pci                26690  1 rtl8192ce
rtlwifi                63475  2 rtl_pci,rtl8192ce
rtl8192c_common        53172  1 rtl8192ce
mac80211              626557  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              484040  2 mac80211,rtlwifi

##### modinfo #####

filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     EF063698748457BBEDB4633
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.13.0-29-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:3B:EA:01:C4:BD:A9:65:67:CF:A7:23:C9:70:D8
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     9B7F19319428FF0EFE7E350
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-29-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:3B:EA:01:C4:BD:A9:65:67:CF:A7:23:C9:70:D8
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     27E91755814596D634B7709
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-29-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:3B:EA:01:C4:BD:A9:65:67:CF:A7:23:C9:70:D8
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     32F826C623BC49F764F7974
depends:        
intree:         Y
vermagic:       3.13.0-29-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:3B:EA:01:C4:BD:A9:65:67:CF:A7:23:C9:70:D8
sig_hashalgo:   sha512

##### modules #####

lp
rtc

coretemp
nct6775

coretemp
nct6775

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

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8178 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[    5.120047] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[    5.194147] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    5.194286] rtlwifi: wireless switch is on
[    8.897871] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    8.898113] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   11.059263] wlan0: authenticate with <MAC address removed>
[   11.079193] wlan0: send auth to <MAC address removed> (try 1/3)
[   11.080713] wlan0: authenticated
[   11.082910] wlan0: associate with <MAC address removed> (try 1/3)
[   11.085949] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   11.086080] wlan0: associated
[   11.086087] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   11.130630] wlan0: deauthenticating from <MAC address removed> by local choice (reason=2)
[   11.161112] wlan0: authenticate with <MAC address removed>
[   11.507939] wlan0: send auth to <MAC address removed> (try 1/3)
[   11.509417] wlan0: authenticated
[   11.510494] wlan0: associate with <MAC address removed> (try 1/3)
[   11.517862] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   11.517993] wlan0: associated
[   19.514761] wlan0: Connection to AP <MAC address removed> lost
[   20.825705] wlan0: authenticate with <MAC address removed>
[   20.845680] wlan0: send auth to <MAC address removed> (try 1/3)
[   20.849279] wlan0: authenticated
[   20.853472] wlan0: associate with <MAC address removed> (try 1/3)
[   20.856489] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   20.856620] wlan0: associated

########## wireless info END ############

```

Also went into Network Manager and locked in BSSID number in previously blank field. Still, I see the WiFi icon fluctuating.
BSSID found through running: 
 ```
cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
```
Which gave me a message:
```
WLAN:0 WPA: GROUP
Rekeying completed with ( BSSID NUMBER) 
[GTK=CCMP]
```

---

### Post by Mike1977 on 2014-06-12
Does anyone have ANY insight into this?

---

