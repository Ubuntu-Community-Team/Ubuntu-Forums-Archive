---
title: "ubuntu 16.04, wireless keeps dropping every 7 minutes"
date: 2016-05-04
forum: Networking &amp; Wireless
---

### Post by n_cknftdibncfukxdb on 2016-05-04
My computer broke, so I'm trying to use an older computer. It has Windows XP, but that won't run because of a virus, so I installed Ubuntu 16.04. The wireless keeps dropping. I have to keep unchecking and checking "Enable Wi-fi" to get it to work. The wireless device is an Edmiax USB device.

Is there any chance of getting this fixed, or will I need to buy a new Windows/Mac computer?

Here's the wireless info:

```

plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/NETGEAR52]] (600 root)
[connection] id=NETGEAR52 | type=wifi | permissions=user:john:;
[wifi] mac-address=<MAC 'wlx74da38021fd4' [IF]> | mac-address-blacklist= | ssid=NETGEAR52
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp0s25   no frequency information.

lo        no frequency information.

wlx74da38021fd4  13 channels in total; available frequencies :
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
          Current Frequency:2.442 GHz (Channel 7)

##### iwlist scan #######################

enp0s25   Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)

wlx74da38021fd4  Scan completed :
          Cell 01 - Address: <MAC 'NETGEAR52' [AC1]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR52"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b46e893ae1
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'e7c0b8' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"e7c0b8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007a1fd71b33
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Winters' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Winters"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003453471dc4e
                    Extra: Last beacon: 2076ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'DDW366.BC84DB-2.4G' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"DDW366.BC84DB-2.4G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002d2f667e198
                    Extra: Last beacon: 1192ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8xxxu]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/realtek/rtl8xxxu/rtl8xxxu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8723aufw_B_NoBT.bin
firmware:       rtlwifi/rtl8723aufw_B.bin
firmware:       rtlwifi/rtl8723aufw_A.bin
license:        GPL
description:    RTL8XXXu USB mac80211 Wireless LAN Driver
author:         Jes Sorensen <Jes.Sorensen@redhat.com>
srcversion:     6318AD97B9A7F66A430B132
depends:        mac80211
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           debug:Set debug mask (int)
parm:           ht40_2g:Enable HT40 support on the 2.4GHz band (bool)

[rtl8192cu]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
srcversion:     2C9D776AE1B25BDC5405217
depends:        mac80211,rtlwifi,rtl8192c-common,rtl_usb
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_usb]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_usb.ko
description:    USB basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     2C9F7031AC4F080527C5C6E
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 

[rtl8192c_common]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     68438042FA7FFFCF4EB1B75
depends:        rtlwifi
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     251B17ACC83990EE9A63C56
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-21-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     A882F4FE63500846E1C859E
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-21-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     00D8DA6D3B739DDD31FFF50
depends:        
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

grep: /sys/module/rtl8xxxu/parameters/debug: Permission denied
grep: /sys/module/rtl8xxxu/parameters/ht40_2g: Permission denied
[rtl8xxxu]

[rtl8192cu]
debug: 0
swenc: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

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

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[   24.934810] IPv6: ADDRCONF(NETDEV_UP): wlx74da38021fd4: link is not ready
[   24.936690] rtl8192cu: MAC auto ON okay!
[   24.969457] rtl8192cu: Tx queue select: 0x05
[   25.364502] IPv6: ADDRCONF(NETDEV_UP): wlx74da38021fd4: link is not ready
[   25.374126] IPv6: ADDRCONF(NETDEV_UP): enp0s25: link is not ready (repeated 2 times)
[   30.757398] IPv6: ADDRCONF(NETDEV_UP): wlx74da38021fd4: link is not ready
[   32.517360] wlx74da38021fd4: authenticate with <MAC 'NETGEAR52' [AC1]>
[   32.531778] wlx74da38021fd4: send auth to <MAC 'NETGEAR52' [AC1]> (try 1/3)
[   32.537361] wlx74da38021fd4: authenticated
[   32.540159] wlx74da38021fd4: associate with <MAC 'NETGEAR52' [AC1]> (try 1/3)
[   32.584731] wlx74da38021fd4: RX AssocResp from <MAC 'NETGEAR52' [AC1]> (capab=0x411 status=0 aid=9)
[   32.599853] wlx74da38021fd4: associated
[   32.600001] IPv6: ADDRCONF(NETDEV_CHANGE): wlx74da38021fd4: link becomes ready
[ 1444.116048] wlx74da38021fd4: deauthenticating from <MAC 'NETGEAR52' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1444.116342] rtl_usb: reg 0x102, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x100012
[ 1444.116353] rtl_usb: reg 0x422, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x40100104
[ 1444.116361] rtl_usb: reg 0x542, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x90e1317
[ 1444.116373] rtl_usb: reg 0x1cc, usbctrl_vendorreq TimeOut! status:0xffffffed value=0xf00069ce
[ 1445.626348] rtl8192cu: Chip version 0x10 (repeated 2 times)
[ 1457.022802] rtl8192cu: MAC address: <MAC 'wlx74da38021fd4' [IF]>
[ 1457.022810] rtl8192cu: Board Type 0
[ 1457.023044] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[ 1457.023096] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[ 1457.025174] ieee80211 phy2: Selected rate control algorithm 'rtl_rc'
[ 1458.075221] rtl8192cu 1-4:1.0 wlx74da38021fd4: renamed from wlan0
[ 1458.106770] IPv6: ADDRCONF(NETDEV_UP): wlx74da38021fd4: link is not ready
[ 1458.111614] rtl8192cu: MAC auto ON okay!
[ 1458.147116] rtl8192cu: Tx queue select: 0x05
[ 1458.542034] IPv6: ADDRCONF(NETDEV_UP): wlx74da38021fd4: link is not ready (repeated 2 times)
[ 1459.514818] wlx74da38021fd4: authenticate with <MAC 'NETGEAR52' [AC1]>
[ 1459.526204] wlx74da38021fd4: send auth to <MAC 'NETGEAR52' [AC1]> (try 1/3)
[ 1459.552169] wlx74da38021fd4: authenticated
[ 1459.556054] wlx74da38021fd4: associate with <MAC 'NETGEAR52' [AC1]> (try 1/3)
[ 1459.609162] wlx74da38021fd4: RX AssocResp from <MAC 'NETGEAR52' [AC1]> (capab=0x411 status=0 aid=9)
[ 1459.610789] wlx74da38021fd4: associated
[ 1459.610870] IPv6: ADDRCONF(NETDEV_CHANGE): wlx74da38021fd4: link becomes ready
[ 1520.336841] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[ 1522.559758] rtl8xxxu: probe of 2-1:1.0 failed with error -5
[ 1578.783109] wlx74da38021fd4: deauthenticating from <MAC 'NETGEAR52' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1581.673426] rtl8192cu: MAC auto ON okay!
[ 1581.718328] rtl8192cu: Tx queue select: 0x05
[ 1582.169482] IPv6: ADDRCONF(NETDEV_UP): wlx74da38021fd4: link is not ready
[ 1583.128491] wlx74da38021fd4: authenticate with <MAC 'NETGEAR52' [AC1]>
[ 1583.160214] wlx74da38021fd4: send auth to <MAC 'NETGEAR52' [AC1]> (try 1/3)
[ 1583.166428] wlx74da38021fd4: authenticated
[ 1583.168132] wlx74da38021fd4: associate with <MAC 'NETGEAR52' [AC1]> (try 1/3)
[ 1583.175305] wlx74da38021fd4: RX AssocResp from <MAC 'NETGEAR52' [AC1]> (capab=0x411 status=0 aid=9)
[ 1583.197546] wlx74da38021fd4: associated
[ 1583.197656] IPv6: ADDRCONF(NETDEV_CHANGE): wlx74da38021fd4: link becomes ready

########## wireless info END ############

```

---

### Post by wildmanne39 on 2016-05-04
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

There is  lot of information missing from that file you posted.

---

