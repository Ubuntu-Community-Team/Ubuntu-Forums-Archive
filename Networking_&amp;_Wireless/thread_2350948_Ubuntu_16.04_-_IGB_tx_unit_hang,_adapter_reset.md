---
title: "Ubuntu 16.04 - IGB tx unit hang, adapter reset"
date: 2017-01-29
forum: Networking &amp; Wireless
---

### Post by chris2471 on 2017-01-29
Hi Guys,
I have a Gigabyte 990x MB + nvidia graphics card, that dual boots ubuntu and windows.
I cannot connect this pc to the internet or local network by any means when i boot with ubuntu. I also have an issue with booting when the pc is a warm start - the screen is black and it just boots the grub default without displaying the bios or the grub menu. From a cold start it works as expected - unsure if this is relevant. 

I have tried so many solutions - such as altering the /etc/networks/interfaces, setting up a static ip, reinstalling etc.

```


########## wireless info START ##########

Report from: 29 Jan 2017 16:59 GMT +0000

Booted last: 29 Jan 2017 00:00 GMT +0000

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-59-generic #80-Ubuntu SMP Fri Jan 6 17:47:47 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, nomodeset

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:30a1]
    Kernel driver in use: ath9k

06:00.0 Ethernet controller [0200]: Intel Corporation I211 Gigabit Network Connection [8086:1539] (rev 03)
    Subsystem: Gigabyte Technology Co., Ltd I211 Gigabit Network Connection [1458:e000]
    Kernel driver in use: igb

##### lsusb #############################

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 003: ID 0461:4de3 Primax Electronics, Ltd 
Bus 008 Device 002: ID 045e:07b6 Microsoft Corp. 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

mxm_wmi                16384  0
ath9k                 143360  0
ath9k_common           36864  1 ath9k
ath9k_hw              466944  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              737280  1 ath9k
cfg80211              565248  4 ath,ath9k_common,ath9k,mac80211
wmi                    20480  1 mxm_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp6s0    Link encap:Ethernet  HWaddr <MAC 'enp6s0' [IF1]>  
          inet6 addr: fe80::cd7f:b618:54e5:51ff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fe100000-fe11ffff 

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:43 errors:0 dropped:0 overruns:0 frame:0
          TX packets:93 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8636 (8.6 KB)  TX bytes:39661 (39.6 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp6s0    no wireless extensions.

wlp2s0    IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       848     1  0 16:54 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp6s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        I211 Gigabit Network Connection
GENERAL.DRIVER:                         igb
GENERAL.DRIVER-VERSION:                 5.3.0-k
GENERAL.FIRMWARE-VERSION:                0. 6-1
GENERAL.HWADDR:                         <MAC 'enp6s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          70 (connecting (getting IP configuration))
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:15.3/0000:06:00.0/net/enp6s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       f7a7900b-610b-31f3-af86-805e01bc6fc1
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   f7a7900b-610b-31f3-af86-805e01bc6fc1 | Wired connection 1

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR9285 Wireless Network Adapter (PCI-Express)
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.4.0-59-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:03.0/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
_XLN Free Wi-Fi  <MAC '_XLN Free Wi-Fi' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  75      &#9602;&#9604;&#9606;_  --        no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/SKY3CD78]] (600 root)
[connection] id=SKY3CD78 | type=wifi | permissions=user:chris:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=SKY3CD78
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: Europe/London (based on set time zone)

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

lo        no frequency information.

enp6s0    no frequency information.

wlp2s0    13 channels in total; available frequencies :
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

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp6s0    Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.462 GHz (Channel 11)

wlp2s0    Scan completed :
          Cell 01 - Address: <MAC '_XLN Free Wi-Fi' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:off
                    ESSID:"_XLN Free Wi-Fi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000567da87756
                    Extra: Last beacon: 12ms ago
          Cell 02 - Address: <MAC 'boleyn way2016' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"boleyn way2016"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000567da85fe8
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath9k]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     1B84AD8C53440158CD581F2
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           led_active_high:Invert LED polarity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)

[ath9k_common]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     6FBD9F8A613FDFA282AB4FE
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 

[ath9k_hw]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     FA7ECFBA5761A5B3ED96BB2
depends:        ath
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 

[ath]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-59-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0B114888238BEBBE8043BC5
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-59-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     FD4B9DA2F385F0531B5CB0B
depends:        
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
led_active_high: -1
nohwcrypt: 1
ps_enable: 0
use_chanctx: 0

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

[/etc/modprobe.d/ath9k.conf]
options ath9k nohwcrypt=1

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

##### dmesg #############################

[  112.928437] igb 0000:06:00.0 enp6s0: Reset adapter
[  112.928466] igb 0000:06:00.0 enp6s0: igb: enp6s0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  113.061802] igb 0000:06:00.0 enp6s0: igb: enp6s0 NIC Link is Down
[  113.924585] igb 0000:06:00.0 enp6s0: Reset adapter
[  115.633067] igb 0000:06:00.0 enp6s0: igb: enp6s0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  125.937650] igb 0000:06:00.0 enp6s0: Reset adapter
[  127.626213] igb 0000:06:00.0 enp6s0: igb: enp6s0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  137.938743] igb 0000:06:00.0 enp6s0: Reset adapter
[  139.931446] igb 0000:06:00.0 enp6s0: igb: enp6s0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  276.674039] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)

########## wireless info END ############



```

I also occassionally see the error TX UNIT HANG DETECTED in dmesg. I just tried to boot on the ubuntu 15.10 live cd to see if this was any better and saw the TX UNIT HANG DETECTED error also. 

I have 100% functionality on both wireless and wifi through windows, no issues.

Please help, this is driving me insane and so far has destroyed all my free time for the last 3 weeks trying to fix this!

Thanks

---

### Post by chili555 on 2017-01-31
I'm not quite sure what is happening with the ethernet driver and Google isn't very helpful either.

It is tempting to download, compile and install a later version of the driver: [http://www.intel.com/content/www/us/en/support/network-and-i-o/ethernet-products/000005767.html](http://www.intel.com/content/www/us/en/support/network-and-i-o/ethernet-products/000005767.html) However, I have been unable to build it successfully. Moreover, to download anything easily requires internet access. All of this points to getting the wireless working.

The driver ath9k is generally reliable. Aside from being pretty far away, why are you unable to connect?```
Cell 01 - Address: <MAC '_XLN Free Wi-Fi' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    [COLOR="#FF0000"]Quality=21/70  [/COLOR]Signal level=-89 dBm  
                    Encryption key:off
                    ESSID:"_XLN Free Wi-Fi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000567da87756
                    Extra: Last beacon: 12ms ago
```

---

### Post by chris2471 on 2017-01-31
Thanks for the reply.

So with the wireless I can connect occasionally. However it is super unstable, and often drops out or fails to connect with the message wlp2s0: link not ready. 

The signal strength is a bit of a mystery to me too, on Windows, I rarely drop below 50% signal on a bad day, and normally have upwards of 2mbps over wi-fi. On Linux it seems to be barely scraping one bar of signal, and I can often spend several hours without seeing my network appear at all. My ssid is a sky network, and the router is one room away. As shown in the original wireless-script info I posted before, scanning for my network showed nothing (even though I was also at the time connected with full strength on my phone).



I just fired up to catch the errors with my wireless. Here is the output of dmesg:

```

[  147.357495] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  345.197759] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  501.024838] wlp2s0: authenticate with c0:3e:0f:cf:04:09
[  501.038619] wlp2s0: send auth to c0:3e:0f:cf:04:09 (try 1/3)
[  501.072251] wlp2s0: authenticated
[  501.075298] wlp2s0: associate with c0:3e:0f:cf:04:09 (try 1/3)
[  501.079165] wlp2s0: RX AssocResp from c0:3e:0f:cf:04:09 (capab=0x1411 status=0 aid=3)
[  501.079263] wlp2s0: associated
[  501.079281] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[  501.085173] cfg80211: Regulatory domain changed to country: DE
[  501.085176] cfg80211:  DFS Master region: ETSI
[  501.085178] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[  501.085180] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[  501.085183] cfg80211:   (5150000 KHz - 5250000 KHz @ 80000 KHz, 200000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[  501.085185] cfg80211:   (5250000 KHz - 5350000 KHz @ 80000 KHz, 200000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[  501.085187] cfg80211:   (5470000 KHz - 5725000 KHz @ 160000 KHz), (N/A, 2698 mBm), (0 s)
[  501.085189] cfg80211:   (57000000 KHz - 66000000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
[  501.149428] wlp2s0: Limiting TX power to 20 (20 - 0) dBm as advertised by c0:3e:0f:cf:04:09
[  515.118909] sd 6:0:0:0: [sdc] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  515.118919] sd 6:0:0:0: [sdc] tag#0 Sense Key : Not Ready [current] 
[  515.118926] sd 6:0:0:0: [sdc] tag#0 Add. Sense: Medium not present
[  515.118933] sd 6:0:0:0: [sdc] tag#0 CDB: Read(10) 28 00 00 00 01 30 00 00 f0 00
[  515.118937] blk_update_request: I/O error, dev sdc, sector 304
[  515.143165] sd 6:0:0:0: [sdc] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  515.143172] sd 6:0:0:0: [sdc] tag#0 Sense Key : Not Ready [current] 
[  515.143177] sd 6:0:0:0: [sdc] tag#0 Add. Sense: Medium not present
[  515.143181] sd 6:0:0:0: [sdc] tag#0 CDB: Read(10) 28 00 00 00 01 30 00 00 08 00
[  515.143184] blk_update_request: I/O error, dev sdc, sector 304
[  515.143188] Buffer I/O error on dev sdc1, logical block 34, async page read
[  515.167107] sd 6:0:0:0: [sdc] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  515.167123] sd 6:0:0:0: [sdc] tag#0 Sense Key : Not Ready [current] 
[  515.167130] sd 6:0:0:0: [sdc] tag#0 Add. Sense: Medium not present
[  515.167136] sd 6:0:0:0: [sdc] tag#0 CDB: Read(10) 28 00 00 00 01 30 00 00 08 00
[  515.167141] blk_update_request: I/O error, dev sdc, sector 304
[  515.167146] Buffer I/O error on dev sdc1, logical block 34, async page read
[  515.190900] sd 6:0:0:0: [sdc] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  515.190909] sd 6:0:0:0: [sdc] tag#0 Sense Key : Not Ready [current] 
[  515.190916] sd 6:0:0:0: [sdc] tag#0 Add. Sense: Medium not present
[  515.190922] sd 6:0:0:0: [sdc] tag#0 CDB: Read(10) 28 00 00 00 02 20 00 00 08 00
[  515.190926] blk_update_request: I/O error, dev sdc, sector 544
[  515.215093] sd 6:0:0:0: [sdc] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  515.215102] sd 6:0:0:0: [sdc] tag#0 Sense Key : Not Ready [current] 
[  515.215109] sd 6:0:0:0: [sdc] tag#0 Add. Sense: Medium not present
[  515.215115] sd 6:0:0:0: [sdc] tag#0 CDB: Read(10) 28 00 00 00 02 20 00 00 08 00
[  515.215119] blk_update_request: I/O error, dev sdc, sector 544
[  515.215125] Buffer I/O error on dev sdc1, logical block 64, async page read
[  672.081008] cfg80211: World regulatory domain updated:
[  672.081014] cfg80211:  DFS Master region: unset
[  672.081018] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[  672.081023] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[  672.081027] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[  672.081031] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[  672.081035] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[  672.081040] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[  672.081044] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[  672.081047] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[  672.081051] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[  672.899808] wlp2s0: authenticate with c0:3e:0f:cf:04:09
[  672.918251] wlp2s0: send auth to c0:3e:0f:cf:04:09 (try 1/3)
[  672.941270] wlp2s0: authenticated
[  672.943080] wlp2s0: associate with c0:3e:0f:cf:04:09 (try 1/3)
[  673.051228] wlp2s0: associate with c0:3e:0f:cf:04:09 (try 2/3)
[  673.061298] wlp2s0: RX AssocResp from c0:3e:0f:cf:04:09 (capab=0x1411 status=0 aid=3)
[  673.061392] wlp2s0: associated
[  673.067121] cfg80211: Regulatory domain changed to country: DE
[  673.067127] cfg80211:  DFS Master region: ETSI
[  673.067130] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[  673.067136] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[  673.067141] cfg80211:   (5150000 KHz - 5250000 KHz @ 80000 KHz, 200000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[  673.067146] cfg80211:   (5250000 KHz - 5350000 KHz @ 80000 KHz, 200000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[  673.067150] cfg80211:   (5470000 KHz - 5725000 KHz @ 160000 KHz), (N/A, 2698 mBm), (0 s)
[  673.067154] cfg80211:   (57000000 KHz - 66000000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
[  673.389736] wlp2s0: Limiting TX power to 20 (20 - 0) dBm as advertised by c0:3e:0f:cf:04:09
[  748.998963] wlp2s0: deauthenticated from c0:3e:0f:cf:04:09 (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[  749.059028] cfg80211: World regulatory domain updated:
[  749.059034] cfg80211:  DFS Master region: unset
[  749.059037] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[  749.059043] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[  749.059047] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[  749.059051] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[  749.059055] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[  749.059059] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[  749.059063] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[  749.059067] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[  749.059070] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[  764.668720] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
chris@Chris-desktop:~$ 
```

I had to transfer some data off the linux partition so some of that log relates to that, I just got lucky that it disconnected while I was doing that.

---

### Post by chili555 on 2017-01-31
Let's try a few things:```
sudo modprobe -r ath9k
sudo modprobe ath9k btcoex_enable=1
```Any improvement?

```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo service network-manager restart
```I notice this:> cfg80211: Regulatory domain changed to country: **DE**Is that your accurate country code?

---

