---
title: "Toshiba Satellite c660d wireless issues"
date: 2014-05-28
forum: Networking &amp; Wireless
---

### Post by buga-burga on 2014-05-28
Hello everybody.
I have a problem with connecting to a wireless network on my laptop. While using Windows I had no problem, it was a very good connection with high speed. With Ubuntu I can even rarely connect to the network and when i do the signal is very weak and the speed is slow. I have tired with "swenc" "ips" and "fwlps" but it did not help. I also tried something with ndiswrapper, but eventually I deleted it. Can someone please help me? 
Thanks in advance.

---

### Post by buga-burga on 2014-05-28
```

########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux nikola-Satellite-C660D 3.13.0-27-generic #50-Ubuntu SMP Thu May 15 18:06:16 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8181]
    Kernel driver in use: rtl8192ce
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Toshiba America Info Systems Device [1179:fd3c]
    Kernel driver in use: r8169

##### lsusb #####

Bus 002 Device 002: ID 064e:a216 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 19d2:0117 ZTE WCDMA Technologies MSM 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

##### rfkill #####

8: phy0: Wireless LAN
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

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.64.64.64     0.0.0.0         UG    0      0        0 ppp0
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0  [TP-LINK_FD6B42] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connecting (configuring)
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    dlink:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA
    TP-LINK_FD6B42:  Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA2

- Device: ttyUSB2  [VIP Mobile Default] ----------------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            option1
  State:             connected
  Default:           yes

  Capabilities:

  IPv4 Settings:
    Address:         10.82.49.238
    Prefix:          32 (255.255.255.255)
    Gateway:         10.64.64.64

    DNS:             10.85.64.173
    DNS:             10.85.64.174

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
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_FD6B42"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a269553387
                    Extra: Last beacon: 24ms ago
                    IE: Unknown: 000E54502D4C494E4B5F464436423432
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004b972a7179
                    Extra: Last beacon: 544ms ago
                    IE: Unknown: 0005646C696E6B
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C

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

##### lsmod #####

rtl8192ce              53550  0 
rtl_pci                26690  1 rtl8192ce
rtlwifi                63475  2 rtl_pci,rtl8192ce
rtl8192c_common        53172  1 rtl8192ce
mac80211              626511  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              484040  2 mac80211,rtlwifi

##### modinfo #####

filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
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
vermagic:       3.13.0-27-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:43:25:CC:F7:B9:5B:51:F6:C1:19:38:0E:B9:33
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

filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     9B7F19319428FF0EFE7E350
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-27-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:43:25:CC:F7:B9:5B:51:F6:C1:19:38:0E:B9:33
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     27E91755814596D634B7709
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-27-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:43:25:CC:F7:B9:5B:51:F6:C1:19:38:0E:B9:33
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
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
vermagic:       3.13.0-27-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:43:25:CC:F7:B9:5B:51:F6:C1:19:38:0E:B9:33
sig_hashalgo:   sha512

##### modules #####

lp
rtc

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

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8176 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   15.573963] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[   15.865140] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   15.865382] rtlwifi: wireless switch is on
[   18.838690] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.839152] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.330133] wlan0: authenticate with <MAC address removed>
[   21.338774] wlan0: direct probe to <MAC address removed> (try 1/3)
[   21.539466] wlan0: direct probe to <MAC address removed> (try 2/3)
[   21.743329] wlan0: direct probe to <MAC address removed> (try 3/3)
[   21.947171] wlan0: authentication with <MAC address removed> timed out
[   22.638820] wlan0: authenticate with <MAC address removed>
[   22.638905] wlan0: direct probe to <MAC address removed> (try 1/3)
[   22.842512] wlan0: direct probe to <MAC address removed> (try 2/3)
[   23.046351] wlan0: direct probe to <MAC address removed> (try 3/3)
[   23.250700] wlan0: authentication with <MAC address removed> timed out
[  465.361538] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  466.275322] wlan0: authenticate with <MAC address removed>
[  466.275429] wlan0: direct probe to <MAC address removed> (try 1/3)
[  466.475380] wlan0: direct probe to <MAC address removed> (try 2/3)
[  466.679436] wlan0: direct probe to <MAC address removed> (try 3/3)
[  466.882871] wlan0: authentication with <MAC address removed> timed out
[  468.163940] wlan0: authenticate with <MAC address removed>
[  468.185443] wlan0: direct probe to <MAC address removed> (try 1/3)
[  468.389072] wlan0: direct probe to <MAC address removed> (try 2/3)
[  468.592817] wlan0: direct probe to <MAC address removed> (try 3/3)
[  468.796508] wlan0: authentication with <MAC address removed> timed out
[  470.497124] wlan0: authenticate with <MAC address removed>
[  470.498681] wlan0: direct probe to <MAC address removed> (try 1/3)
[  470.702189] wlan0: direct probe to <MAC address removed> (try 2/3)
[  470.905936] wlan0: direct probe to <MAC address removed> (try 3/3)
[  471.109681] wlan0: authentication with <MAC address removed> timed out
[  473.281274] wlan0: authenticate with <MAC address removed>
[  473.284511] wlan0: direct probe to <MAC address removed> (try 1/3)
[  473.486721] wlan0: direct probe to <MAC address removed> (try 2/3)
[  473.690468] wlan0: direct probe to <MAC address removed> (try 3/3)
[  473.894212] wlan0: authentication with <MAC address removed> timed out
[  486.249205] wlan0: authenticate with <MAC address removed>
[  486.250329] wlan0: direct probe to <MAC address removed> (try 1/3)
[  486.450494] wlan0: direct probe to <MAC address removed> (try 2/3)
[  486.654316] wlan0: direct probe to <MAC address removed> (try 3/3)
[  486.858061] wlan0: authentication with <MAC address removed> timed out
[ 2748.910057] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2749.833246] wlan0: authenticate with <MAC address removed>
[ 2749.833357] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2749.835936] wlan0: authenticated
[ 2749.836138] rtl8192ce 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2749.836142] rtl8192ce 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2749.836144] rtl8192ce 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2749.836889] wlan0: associate with <MAC address removed> (try 1/3)
[ 2749.839033] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 2749.839140] wlan0: associated
[ 2749.839165] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2784.737970] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2823.203784] rtl8192ce: rtl8192ce: FW Power Save off (module option)
[ 2823.203801] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[ 2823.215563] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[ 2823.215831] rtlwifi: wireless switch is on
[ 2823.622156] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2823.622536] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2844.022631] wlan0: authenticate with <MAC address removed>
[ 2844.360729] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2844.362875] wlan0: authenticated
[ 2849.362549] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2849.363370] wlan0: authenticate with <MAC address removed>
[ 2849.363529] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2849.366811] wlan0: authenticated
[ 2854.363307] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2880.420200] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[ 2880.431624] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[ 2880.434355] rtlwifi: wireless switch is on
[ 2880.803408] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2880.805004] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2890.919026] wlan0: authenticate with <MAC address removed>
[ 2891.251832] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2891.253247] wlan0: authenticated
[ 2896.254320] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2906.357261] wlan0: authenticate with <MAC address removed>
[ 2906.357419] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2906.361132] wlan0: authenticated
[ 2911.357021] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2921.853927] wlan0: authenticate with <MAC address removed>
[ 2921.854038] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2921.855967] wlan0: authenticated
[ 2926.577720] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2936.574551] wlan0: authenticate with <MAC address removed>
[ 2936.574744] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2936.577233] wlan0: authenticated
[ 2941.572081] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2952.566998] wlan0: authenticate with <MAC address removed>
[ 2952.567089] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2952.568724] wlan0: authenticated
[ 2956.436583] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2975.812226] rtl8192ce: rtl8192ce: Power Save off (module option)
[ 2975.812282] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[ 2975.812803] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[ 2975.813258] rtlwifi: wireless switch is on
[ 2976.193490] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2976.195820] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2986.306474] wlan0: authenticate with <MAC address removed>
[ 2986.306577] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2986.308117] wlan0: authenticated
[ 2991.305934] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3001.405146] wlan0: authenticate with <MAC address removed>
[ 3001.405301] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3001.406862] wlan0: authenticated
[ 3006.402086] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3016.896562] wlan0: authenticate with <MAC address removed>
[ 3016.896654] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3016.898172] wlan0: authenticated
[ 3021.895407] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3032.896740] wlan0: authenticate with <MAC address removed>
[ 3032.896896] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3032.899303] wlan0: authenticated
[ 3037.895212] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3073.156056] rtl8192ce: rtl8192ce: Power Save off (module option)
[ 3073.156075] rtl8192ce: rtl8192ce: FW Power Save off (module option)
[ 3073.156114] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[ 3073.156680] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[ 3073.160208] rtlwifi: wireless switch is on
[ 3073.548985] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3073.550480] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3107.318571] wlan0: authenticate with <MAC address removed>
[ 3107.318678] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3107.320506] wlan0: authenticated
[ 3112.319804] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3122.420411] wlan0: authenticate with <MAC address removed>
[ 3122.420508] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3122.422962] wlan0: authenticated
[ 3125.309554] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3435.171193] wlan0: authenticate with <MAC address removed>
[ 3435.171298] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3435.173213] wlan0: authenticated
[ 3440.171300] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3453.147191] wlan0: authenticate with <MAC address removed>
[ 3453.147287] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3453.149730] wlan0: authenticated
[ 3458.148398] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3469.145370] wlan0: authenticate with <MAC address removed>
[ 3469.145531] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3469.148474] wlan0: authenticated
[ 3474.142725] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3488.050017] wlan0: authenticate with <MAC address removed>
[ 3488.050227] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3488.052450] wlan0: authenticated
[ 3493.051881] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3591.393299] rtl8192ce: rtl8192ce: FW Power Save off (module option)
[ 3591.393353] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[ 3591.393572] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[ 3591.393786] rtlwifi: wireless switch is on
[ 3591.766438] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3591.766786] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3612.173763] wlan0: authenticate with <MAC address removed>
[ 3612.504959] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3612.507238] wlan0: authenticated
[ 3617.505705] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3617.506638] wlan0: authenticate with <MAC address removed>
[ 3617.506818] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3617.509968] wlan0: authenticated
[ 3622.503352] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3639.859619] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[ 3639.872242] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[ 3639.877066] rtlwifi: wireless switch is on
[ 3640.221797] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3640.223495] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3650.362812] wlan0: authenticate with <MAC address removed>
[ 3650.695277] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3650.696689] wlan0: authenticated
[ 3655.694643] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3665.793777] wlan0: authenticate with <MAC address removed>
[ 3665.793885] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3665.796058] wlan0: authenticated
[ 3670.790998] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3689.482394] rtl8192ce: rtl8192ce: Power Save off (module option)
[ 3689.482408] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[ 3689.506505] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[ 3689.507921] rtlwifi: wireless switch is on
[ 3689.866722] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3689.871194] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3722.867007] wlan0: authenticate with <MAC address removed>
[ 3722.867099] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3723.068338] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3723.272318] wlan0: send auth to <MAC address removed> (try 3/3)
[ 3723.274190] wlan0: authenticated
[ 3727.868525] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3737.970550] wlan0: authenticate with <MAC address removed>
[ 3737.970709] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3737.974218] wlan0: authenticated
[ 3742.969595] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3768.519377] rtl8192ce: rtl8192ce: Power Save off (module option)
[ 3768.519382] rtl8192ce: rtl8192ce: FW Power Save off (module option)
[ 3768.519394] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[ 3768.519602] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[ 3768.519823] rtlwifi: wireless switch is on
[ 3768.914466] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3768.915746] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3780.191580] wlan0: authenticate with <MAC address removed>
[ 3780.191677] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3780.199976] wlan0: authenticated
[ 3785.193232] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3795.291229] wlan0: authenticate with <MAC address removed>
[ 3795.291444] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3795.294725] wlan0: authenticated
[ 3800.290338] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4115.660089] wlan0: authenticate with <MAC address removed>
[ 4115.660196] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4115.863581] wlan0: send auth to <MAC address removed> (try 2/3)
[ 4115.867969] wlan0: authenticated
[ 4120.658582] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4133.630666] wlan0: authenticate with <MAC address removed>
[ 4133.630764] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4133.632538] wlan0: authenticated
[ 4138.633878] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4168.544296] wlan0: authenticate with <MAC address removed>
[ 4168.544460] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4168.550150] wlan0: authenticated
[ 4173.544637] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4193.536492] wlan0: authenticate with <MAC address removed>
[ 4193.536589] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4193.539734] wlan0: authenticated
[ 4198.538018] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4524.349485] wlan0: authenticate with <MAC address removed>
[ 4524.349578] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4524.351890] wlan0: authenticated
[ 4529.346729] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4549.247102] wlan0: authenticate with <MAC address removed>
[ 4549.247304] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4549.250852] wlan0: authenticated
[ 4554.248884] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4574.241745] wlan0: authenticate with <MAC address removed>
[ 4574.241872] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4574.244425] wlan0: authenticated
[ 4579.238965] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4599.226974] wlan0: authenticate with <MAC address removed>
[ 4599.227137] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4599.230205] wlan0: authenticated
[ 4604.227701] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4933.046793] wlan0: authenticate with <MAC address removed>
[ 4933.046952] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4933.049276] wlan0: authenticated
[ 4938.046863] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4957.951845] wlan0: authenticate with <MAC address removed>
[ 4957.951948] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4957.954939] wlan0: authenticated
[ 4962.952190] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4982.942684] wlan0: authenticate with <MAC address removed>
[ 4982.942786] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4982.946735] wlan0: authenticated
[ 4987.944310] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 5007.941006] wlan0: authenticate with <MAC address removed>
[ 5007.941109] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5007.943384] wlan0: authenticated
[ 5012.938886] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 5341.742091] wlan0: authenticate with <MAC address removed>
[ 5341.742207] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5341.744840] wlan0: authenticated
[ 5346.742223] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 5366.650465] wlan0: authenticate with <MAC address removed>
[ 5366.650567] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5366.652881] wlan0: authenticated
[ 5371.647527] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 5391.638145] wlan0: authenticate with <MAC address removed>
[ 5391.638308] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5391.642671] wlan0: authenticated
[ 5396.636877] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 5416.631649] wlan0: authenticate with <MAC address removed>
[ 5416.631813] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5416.634902] wlan0: authenticated
[ 5421.630853] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)

########## wireless info END ############
```

---

