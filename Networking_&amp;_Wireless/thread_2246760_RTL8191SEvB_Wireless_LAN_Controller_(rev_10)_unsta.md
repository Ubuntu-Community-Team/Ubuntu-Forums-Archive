---
title: "RTL8191SEvB Wireless LAN Controller (rev 10) unstabilities 14.04"
date: 2014-10-03
forum: Networking &amp; Wireless
---

### Post by jean_bono2 on 2014-10-03
Hello dear Ubuntu community
I have coped with this unstability for a while now  and having a bit of time on my hands now I'm wondering if there is a way to fix this
My computer is connected to the internet and works generally quite well but from time to time, the connection stops for a few seconds ( withouth deconnecting from the wifi ) or becomes very slow.
My first impression is that the wifi module isn't quite operationnal but I have to admit I don't know much about an alternative.
Anybody here able to help?
here is the output of the wonderful wireless_scripts :
```

########## wireless info START ##########

Report from: 03 Oct 2014 09:17 BST +0100

Booted last: 02 Oct 2014 23:35 BST +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:07 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172]
    Kernel driver in use: rtl8192se

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: Mitac Device [1071:9270]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 004: ID 05e3:0505 Genesys Logic, Inc. 
Bus 002 Device 003: ID 040b:2013 Weltrend Semiconductor 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8192se              63196  0 
rtl_pci                26690  1 rtl8192se
rtlwifi                63475  2 rtl_pci,rtl8192se
mac80211              630653  3 rtl_pci,rtlwifi,rtl8192se
cfg80211              484040  2 mac80211,rtlwifi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e4b:d6ff:feea:a909/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1929065 errors:0 dropped:0 overruns:0 frame:0
          TX packets:706206 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2110663434 (2.1 GB)  TX bytes:419303801 (419.3 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Sarah Moody"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Sarah Moody' [AC1]>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=36/70  Signal level=-74 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:12650   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [Sarah Moody] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192se
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           18 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Sarah Moody:    Infra, <MAC 'Sarah Moody' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 51 WPA
    SKYCBC48:        Infra, <MAC 'SKYCBC48' [AN2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA2

  IPv4 Settings:
    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/bono-mobile]] (600 root)
[connection] id=bono-mobile | type=802-11-wireless
[802-11-wireless] ssid=bono-mobile | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Sarah Moody]] (600 root)
[connection] id=Sarah Moody | type=802-11-wireless
[802-11-wireless] ssid=Sarah Moody | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Sarah Moody 1]] (600 root)
[connection] id=Sarah Moody 1 | type=802-11-wireless
[802-11-wireless] ssid=Sarah Moody | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

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

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.472 GHz (Channel 13)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Sarah Moody' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Sarah Moody"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000013756c3206
                    Extra: Last beacon: 56ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'virginmedia1706905' [AC2]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"virginmedia1706905"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000bc22bdd929e
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8192se]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
firmware:       rtlwifi/rtl8192sefw.bin
description:    Realtek 8192S/8191S 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     C53951858E34882052195CA
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        38:F3:B6:C6:3A:85:AF:FD:FB:BE:0E:53:33:9D:F8:E0:C6:B6:C9:D5
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

[rtl_pci]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        38:F3:B6:C6:3A:85:AF:FD:FB:BE:0E:53:33:9D:F8:E0:C6:B6:C9:D5
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        38:F3:B6:C6:3A:85:AF:FD:FB:BE:0E:53:33:9D:F8:E0:C6:B6:C9:D5
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        38:F3:B6:C6:3A:85:AF:FD:FB:BE:0E:53:33:9D:F8:E0:C6:B6:C9:D5
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        38:F3:B6:C6:3A:85:AF:FD:FB:BE:0E:53:33:9D:F8:E0:C6:B6:C9:D5
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8192se]
debug: 0
fwlps: N
ips: Y
swenc: N
swlps: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

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

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8172 (rtl8192se)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[   18.514744] wlan0: associate with <MAC 'Sarah Moody' [AC1]> (try 1/3)
[   18.520696] wlan0: RX AssocResp from <MAC 'Sarah Moody' [AC1]> (capab=0x411 status=0 aid=2)
[   18.523806] wlan0: associated
[   18.523819] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   26.828071] wlan0: Connection to AP <MAC 'Sarah Moody' [AC1]> lost
[   28.005054] wlan0: authenticate with <MAC 'Sarah Moody' [AC1]>
[   28.016138] wlan0: send auth to <MAC 'Sarah Moody' [AC1]> (try 1/3)
[   28.018227] wlan0: authenticated
[   28.018392] rtl8192se 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   28.020573] wlan0: associate with <MAC 'Sarah Moody' [AC1]> (try 1/3)
[   28.023746] wlan0: RX AssocResp from <MAC 'Sarah Moody' [AC1]> (capab=0x411 status=0 aid=2)
[   28.026523] wlan0: associated
[  186.408536] wlan0: deauthenticating from <MAC 'Sarah Moody' [AC1]> by local choice (reason=3)
[  187.358379] wlan0: authenticate with <MAC 'Sarah Moody' [AC1]>
[  187.368981] wlan0: send auth to <MAC 'Sarah Moody' [AC1]> (try 1/3)
[  187.371143] wlan0: authenticated
[  187.371386] rtl8192se 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  187.373505] wlan0: associate with <MAC 'Sarah Moody' [AC1]> (try 1/3)
[  187.381143] wlan0: RX AssocResp from <MAC 'Sarah Moody' [AC1]> (capab=0x411 status=0 aid=2)
[  187.384499] wlan0: associated
[  195.779026] wlan0: Connection to AP <MAC 'Sarah Moody' [AC1]> lost
[  196.972739] wlan0: authenticate with <MAC 'Sarah Moody' [AC1]>
[  196.983767] wlan0: send auth to <MAC 'Sarah Moody' [AC1]> (try 1/3)
[  196.985917] wlan0: authenticated
[  196.986117] rtl8192se 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  196.988259] wlan0: associate with <MAC 'Sarah Moody' [AC1]> (try 1/3)
[  196.991343] wlan0: RX AssocResp from <MAC 'Sarah Moody' [AC1]> (capab=0x411 status=0 aid=2)
[  196.994086] wlan0: associated

########## wireless info END ############


```

Thanks for your time
Jean

---

### Post by jean_bono2 on 2014-10-04
Bump

I have tried a few things but I still get some deconnections
here are the new infos :
```

########## wireless info START ##########

Report from: 04 Oct 2014 21:48 BST +0100

Booted last: 04 Oct 2014 19:00 BST +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:07 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172]
    Kernel driver in use: rtl8192se

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: Mitac Device [1071:9270]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 004: ID 05e3:0505 Genesys Logic, Inc. 
Bus 002 Device 003: ID 040b:2013 Weltrend Semiconductor 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8192ce              53550  0 
rtl8192c_common        53099  1 rtl8192ce
rtl8192se              63095  0 
rtlwifi                77814  2 rtl8192ce,rtl8192se
mac80211              630653  3 rtlwifi,rtl8192ce,rtl8192se
cfg80211              484040  2 mac80211,rtlwifi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e4b:d6ff:feea:a909/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:299405 errors:0 dropped:0 overruns:0 frame:0
          TX packets:207688 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:262327685 (262.3 MB)  TX bytes:126070161 (126.0 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Sarah Moody"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Sarah Moody' [AC1]>   
          Bit Rate=24 Mb/s   Tx-Power=30 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:125   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [Sarah Moody] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192se
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           24 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    virginmedia1706905: Infra, <MAC 'virginmedia1706905' [AC2]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    *Sarah Moody:    Infra, <MAC 'Sarah Moody' [AC1]>, Freq 2437 MHz, Rate 24 Mb/s, Strength 46 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/bono-mobile]] (600 root)
[connection] id=bono-mobile | type=802-11-wireless
[802-11-wireless] ssid=bono-mobile | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Sarah Moody]] (600 root)
[connection] id=Sarah Moody | type=802-11-wireless
[802-11-wireless] ssid=Sarah Moody | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Sarah Moody 1]] (600 root)
[connection] id=Sarah Moody 1 | type=802-11-wireless
[802-11-wireless] ssid=Sarah Moody | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/networkwireless]] (600 root)
[connection] id=networkwireless | type=802-11-wireless
[802-11-wireless] ssid=networkwireless | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country BO:
    (2402 - 2482 @ 40), (N/A, 30)
    (5735 - 5835 @ 40), (N/A, 30)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

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

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.472 GHz (Channel 13)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Sarah Moody' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"Sarah Moody"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000180f6678
                    Extra: Last beacon: 56ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'virginmedia1706905' [AC2]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"virginmedia1706905"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000be0c5cb0186
                    Extra: Last beacon: 476ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8192ce]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Benjamin Porter    <BenjaminPorter86@gmail.com>
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     53EBB785CF741A05F34B0A0
depends:        rtlwifi,rtl8192c-common,mac80211
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl8192c_common]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c_common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     32F826C623BC49F764F7974
depends:        
vermagic:       3.13.0-36-generic SMP mod_unload modversions 

[rtl8192se]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
firmware:       rtlwifi/rtl8192sefw.bin
description:    Realtek 8192S/8191S 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     E017555728164F306FD7A0C
depends:        rtlwifi,mac80211
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtlwifi]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
author:         Benjamin Porter    <BenjaminPorter86@gmail.com>
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     2F6F23788C82F9B57DF797B
depends:        mac80211,cfg80211
vermagic:       3.13.0-36-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        38:F3:B6:C6:3A:85:AF:FD:FB:BE:0E:53:33:9D:F8:E0:C6:B6:C9:D5
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        38:F3:B6:C6:3A:85:AF:FD:FB:BE:0E:53:33:9D:F8:E0:C6:B6:C9:D5
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8192ce]
debug: 0
fwlps: N
ips: Y
swenc: Y
swlps: N

[rtl8192se]
debug: 0
fwlps: N
ips: Y
swenc: N
swlps: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc
rtl8192ce

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

[/etc/modprobe.d/modprobe.conf]
options rtl8192ce ips=1
options rtl8192ce fwlps=0
options rtl8192ce swenc=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8172 (rtl8192se)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[ 4000.349881] wlan0: authenticate with <MAC 'Sarah Moody' [AC1]>
[ 4000.352822] wlan0: direct probe to <MAC 'Sarah Moody' [AC1]> (try 1/3)
[ 4000.553524] wlan0: direct probe to <MAC 'Sarah Moody' [AC1]> (try 2/3)
[ 4000.757619] wlan0: direct probe to <MAC 'Sarah Moody' [AC1]> (try 3/3)
[ 4000.961738] wlan0: authentication with <MAC 'Sarah Moody' [AC1]> timed out
[ 4002.527308] wlan0: authenticate with <MAC 'Sarah Moody' [AC1]>
[ 4002.537942] wlan0: direct probe to <MAC 'Sarah Moody' [AC1]> (try 1/3)
[ 4002.738842] wlan0: direct probe to <MAC 'Sarah Moody' [AC1]> (try 2/3)
[ 4002.942989] wlan0: direct probe to <MAC 'Sarah Moody' [AC1]> (try 3/3)
[ 4003.147095] wlan0: authentication with <MAC 'Sarah Moody' [AC1]> timed out
[ 4005.210910] wlan0: authenticate with <MAC 'Sarah Moody' [AC1]>
[ 4005.211107] wlan0: direct probe to <MAC 'Sarah Moody' [AC1]> (try 1/3)
[ 4005.412493] wlan0: direct probe to <MAC 'Sarah Moody' [AC1]> (try 2/3)
[ 4005.616607] wlan0: direct probe to <MAC 'Sarah Moody' [AC1]> (try 3/3)
[ 4005.820722] wlan0: authentication with <MAC 'Sarah Moody' [AC1]> timed out
[ 4009.018785] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[ 4117.501622] wlan0: authenticate with <MAC 'Sarah Moody' [AC1]>
[ 4117.512168] wlan0: send auth to <MAC 'Sarah Moody' [AC1]> (try 1/3)
[ 4117.514274] wlan0: authenticated
[ 4117.514451] rtl8192se 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 4117.520845] wlan0: associate with <MAC 'Sarah Moody' [AC1]> (try 1/3)
[ 4117.523928] wlan0: RX AssocResp from <MAC 'Sarah Moody' [AC1]> (capab=0x411 status=0 aid=2)
[ 4117.527380] wlan0: associated
[ 4117.527418] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4117.564168] wlan0: deauthenticating from <MAC 'Sarah Moody' [AC1]> by local choice (reason=2)
[ 4117.585231] wlan0: authenticate with <MAC 'Sarah Moody' [AC1]>
[ 4117.585486] wlan0: send auth to <MAC 'Sarah Moody' [AC1]> (try 1/3)
[ 4117.587789] wlan0: authenticated
[ 4117.588117] rtl8192se 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 4117.588939] wlan0: associate with <MAC 'Sarah Moody' [AC1]> (try 1/3)
[ 4117.591898] wlan0: RX AssocResp from <MAC 'Sarah Moody' [AC1]> (capab=0x411 status=0 aid=2)
[ 4117.595425] wlan0: associated
[ 5551.469157] wlan0: Connection to AP <MAC 'Sarah Moody' [AC1]> lost
[ 5558.694014] wlan0: authenticate with <MAC 'Sarah Moody' [AC1]>
[ 5558.704856] wlan0: direct probe to <MAC 'Sarah Moody' [AC1]> (try 1/3)
[ 5558.905477] wlan0: send auth to <MAC 'Sarah Moody' [AC1]> (try 2/3)
[ 5560.090170] wlan0: send auth to <MAC 'Sarah Moody' [AC1]> (try 3/3)
[ 5561.066746] wlan0: authentication with <MAC 'Sarah Moody' [AC1]> timed out
[ 5567.560017] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9712.291017] wlan0: authenticate with <MAC 'Sarah Moody' [AC1]>
[ 9712.301573] wlan0: send auth to <MAC 'Sarah Moody' [AC1]> (try 1/3)
[ 9712.303761] wlan0: authenticated
[ 9712.303978] rtl8192se 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 9712.306071] wlan0: associate with <MAC 'Sarah Moody' [AC1]> (try 1/3)
[ 9712.310537] wlan0: RX AssocResp from <MAC 'Sarah Moody' [AC1]> (capab=0x411 status=0 aid=2)
[ 9712.313238] wlan0: associated
[ 9712.313272] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############


```

---

### Post by jeremy31 on 2014-10-04
One thing you could try is to change your wifi security to WPA2-AES as I see this in the wireless-info
```
[COLOR=#000000][FONT=Ubuntu Mono]rtl8192se 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
```[/FONT][/COLOR]

---

### Post by wildmanne39 on 2014-10-04
Hi, please do everything in the answer at the following link, it help often times with this problematic driver buyt not all ways.
[http://askubuntu.com/questions/504777/unstable-wireless-connection-in-ubuntu-14-04/505246#505246](http://askubuntu.com/questions/504777/unstable-wireless-connection-in-ubuntu-14-04/505246#505246)
When you run the commands in the link I gave you change rtl8192[COLOR="#FF0000"]ce[/COLOR] to rtl8192[COLOR="#FF0000"]se[/COLOR].
Thanks

---

### Post by wildmanne39 on 2014-10-04
You also have two drivers loaded, we need to blacklist the one that you do not need please run the following command.
```
echo "blacklist rtl8192ce" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Thanks

---

### Post by jean_bono2 on 2014-10-04
Thank you for your replies
I will try and do the changes to the router tomorrow
But i managed to change the ipv6 settings
and also to modify the parameter of rtl8192se
and blacklist rtl8192ce
I'll let you know if that changes anything
Thanks and good night

---

### Post by jean_bono2 on 2014-10-07
Hello again
I did all the changes I could
switched to channel 1
passphrase in WPA2 AES
ipv6 disabled
and made sure that the router was in 802.11bg

But i'm still getting some unstabilities
```

########## wireless info START ##########

Report from: 07 Oct 2014 23:54 BST +0100

Booted last: 07 Oct 2014 21:54 BST +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:07 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172]
    Kernel driver in use: rtl8192se

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: Mitac Device [1071:9270]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 005: ID 04e8:685c Samsung Electronics Co., Ltd GT-I9250 Phone [Galaxy Nexus]
Bus 002 Device 004: ID 05e3:0505 Genesys Logic, Inc. 
Bus 002 Device 003: ID 040b:2013 Weltrend Semiconductor 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04e8:61b6 Samsung Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8192ce              53550  0 
rtl8192c_common        53099  1 rtl8192ce
rtl8192se              63095  0 
rtlwifi                77814  2 rtl8192ce,rtl8192se
mac80211              630653  3 rtlwifi,rtl8192ce,rtl8192se
cfg80211              484040  2 mac80211,rtlwifi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e4b:d6ff:feea:a909/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:67319 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:63960767 (63.9 MB)  TX bytes:10901170 (10.9 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Sarah Moody"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'Sarah Moody' [AC3]>   
          Bit Rate=18 Mb/s   Tx-Power=33 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=36/70  Signal level=-74 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:41   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [Sarah Moody] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192se
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           18 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    virginmedia1706905: Infra, <MAC 'virginmedia1706905' [AC1]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    SKYCBC48:        Infra, <MAC 'SKYCBC48' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2
    *Sarah Moody:    Infra, <MAC 'Sarah Moody' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 46 WPA2

  IPv4 Settings:
    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/bono-mobile]] (600 root)
[connection] id=bono-mobile | type=802-11-wireless
[802-11-wireless] ssid=bono-mobile | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Sarah Moody]] (600 root)
[connection] id=Sarah Moody | type=802-11-wireless
[802-11-wireless] ssid=Sarah Moody | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.472 GHz (Channel 13)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'virginmedia1706905' [AC1]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"virginmedia1706905"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000c1ee3cc0281
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'SKYCBC48' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"SKYCBC48"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000dbf92e9a4b
                    Extra: Last beacon: 1984ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Sarah Moody' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Sarah Moody"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000055269f717
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8192ce]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Benjamin Porter    <BenjaminPorter86@gmail.com>
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     53EBB785CF741A05F34B0A0
depends:        rtlwifi,rtl8192c-common,mac80211
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl8192c_common]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c_common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     32F826C623BC49F764F7974
depends:        
vermagic:       3.13.0-36-generic SMP mod_unload modversions 

[rtl8192se]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
firmware:       rtlwifi/rtl8192sefw.bin
description:    Realtek 8192S/8191S 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     E017555728164F306FD7A0C
depends:        rtlwifi,mac80211
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtlwifi]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
author:         Benjamin Porter    <BenjaminPorter86@gmail.com>
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     2F6F23788C82F9B57DF797B
depends:        mac80211,cfg80211
vermagic:       3.13.0-36-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        38:F3:B6:C6:3A:85:AF:FD:FB:BE:0E:53:33:9D:F8:E0:C6:B6:C9:D5
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        38:F3:B6:C6:3A:85:AF:FD:FB:BE:0E:53:33:9D:F8:E0:C6:B6:C9:D5
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8192ce]
debug: 0
fwlps: N
ips: N
swenc: Y
swlps: N

[rtl8192se]
debug: 0
fwlps: N
ips: Y
swenc: N
swlps: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc
rtl8192ce

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
blacklist rtl8192ce

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

[/etc/modprobe.d/modprobe.conf]
options rtl8192ce ips=1
options rtl8192ce fwlps=0
options rtl8192ce swenc=1

[/etc/modprobe.d/rtl8192ce.conf]
options rtl8192ce swenc=1 ips=0

[/etc/modprobe.d/rtl8192se.conf]
options rtl8192ce swenc=1 ips=0

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8172 (rtl8192se)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[ 6903.958247] wlan0: send auth to <MAC 'Sarah Moody' [AC3]> (try 1/3)
[ 6903.965442] wlan0: authenticated
[ 6903.966677] wlan0: associate with <MAC 'Sarah Moody' [AC3]> (try 1/3)
[ 6904.070723] wlan0: associate with <MAC 'Sarah Moody' [AC3]> (try 2/3)
[ 6904.174793] wlan0: associate with <MAC 'Sarah Moody' [AC3]> (try 3/3)
[ 6904.180239] wlan0: RX AssocResp from <MAC 'Sarah Moody' [AC3]> (capab=0x411 status=0 aid=3)
[ 6904.183535] wlan0: associated
[ 7035.455065] wlan0: Connection to AP <MAC 'Sarah Moody' [AC3]> lost
[ 7036.639917] wlan0: authenticate with <MAC 'Sarah Moody' [AC3]>
[ 7036.651114] wlan0: send auth to <MAC 'Sarah Moody' [AC3]> (try 1/3)
[ 7036.657518] wlan0: authenticated
[ 7036.659672] wlan0: associate with <MAC 'Sarah Moody' [AC3]> (try 1/3)
[ 7036.667476] wlan0: RX AssocResp from <MAC 'Sarah Moody' [AC3]> (capab=0x411 status=0 aid=3)
[ 7036.670341] wlan0: associated
[ 7094.022773] wlan0: Connection to AP <MAC 'Sarah Moody' [AC3]> lost
[ 7095.293220] wlan0: authenticate with <MAC 'Sarah Moody' [AC3]>
[ 7095.302787] wlan0: send auth to <MAC 'Sarah Moody' [AC3]> (try 1/3)
[ 7095.305050] wlan0: authenticated
[ 7095.307506] wlan0: associate with <MAC 'Sarah Moody' [AC3]> (try 1/3)
[ 7095.310631] wlan0: RX AssocResp from <MAC 'Sarah Moody' [AC3]> (capab=0x411 status=0 aid=3)
[ 7095.313719] wlan0: associated
[ 7112.494032] wlan0: Connection to AP <MAC 'Sarah Moody' [AC3]> lost
[ 7113.694950] wlan0: authenticate with <MAC 'Sarah Moody' [AC3]>
[ 7113.706256] wlan0: send auth to <MAC 'Sarah Moody' [AC3]> (try 1/3)
[ 7113.709149] wlan0: authenticated
[ 7113.710557] wlan0: associate with <MAC 'Sarah Moody' [AC3]> (try 1/3)
[ 7113.713637] wlan0: RX AssocResp from <MAC 'Sarah Moody' [AC3]> (capab=0x411 status=0 aid=3)
[ 7113.716832] wlan0: associated
[ 7160.979659] wlan0: Connection to AP <MAC 'Sarah Moody' [AC3]> lost
[ 7168.236511] wlan0: authenticate with <MAC 'Sarah Moody' [AC3]>
[ 7168.247395] wlan0: send auth to <MAC 'Sarah Moody' [AC3]> (try 1/3)
[ 7168.351852] wlan0: send auth to <MAC 'Sarah Moody' [AC3]> (try 2/3)
[ 7168.455926] wlan0: send auth to <MAC 'Sarah Moody' [AC3]> (try 3/3)
[ 7168.559999] wlan0: authentication with <MAC 'Sarah Moody' [AC3]> timed out
[ 7169.913815] wlan0: authenticate with <MAC 'Sarah Moody' [AC3]>
[ 7169.924327] wlan0: send auth to <MAC 'Sarah Moody' [AC3]> (try 1/3)
[ 7170.028895] wlan0: send auth to <MAC 'Sarah Moody' [AC3]> (try 2/3)
[ 7170.132948] wlan0: send auth to <MAC 'Sarah Moody' [AC3]> (try 3/3)
[ 7170.237005] wlan0: authentication with <MAC 'Sarah Moody' [AC3]> timed out
[ 7172.086564] wlan0: authenticate with <MAC 'Sarah Moody' [AC3]>
[ 7172.097668] wlan0: send auth to <MAC 'Sarah Moody' [AC3]> (try 1/3)
[ 7172.198209] wlan0: send auth to <MAC 'Sarah Moody' [AC3]> (try 2/3)
[ 7172.302293] wlan0: send auth to <MAC 'Sarah Moody' [AC3]> (try 3/3)
[ 7172.406325] wlan0: authentication with <MAC 'Sarah Moody' [AC3]> timed out
[ 7177.420532] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[ 7229.714801] wlan0: authenticate with <MAC 'Sarah Moody' [AC3]>
[ 7229.725840] wlan0: send auth to <MAC 'Sarah Moody' [AC3]> (try 1/3)
[ 7229.728657] wlan0: authenticated
[ 7229.729280] wlan0: associate with <MAC 'Sarah Moody' [AC3]> (try 1/3)
[ 7229.732328] wlan0: RX AssocResp from <MAC 'Sarah Moody' [AC3]> (capab=0x411 status=0 aid=3)
[ 7229.736734] wlan0: associated
[ 7229.736750] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7229.751970] wlan0: deauthenticating from <MAC 'Sarah Moody' [AC3]> by local choice (reason=2)
[ 7229.773730] wlan0: authenticate with <MAC 'Sarah Moody' [AC3]>
[ 7229.774001] wlan0: send auth to <MAC 'Sarah Moody' [AC3]> (try 1/3)
[ 7229.776050] wlan0: authenticated
[ 7229.777336] wlan0: associate with <MAC 'Sarah Moody' [AC3]> (try 1/3)
[ 7229.780167] wlan0: RX AssocResp from <MAC 'Sarah Moody' [AC3]> (capab=0x411 status=0 aid=3)
[ 7229.783873] wlan0: associated

########## wireless info END ############


```
Is there anything I missed?
Looking at lsmod it feels like I'm still loading too many modules
Thanks

---

### Post by varunendra on 2014-10-07
> **jean_bono2 said:**
> Looking at lsmod it feels like I'm still loading too many modules
Because you have added the wrong module to your /etc/modules file as well, which overrides the blacklisting and loads it -
> **jean_bono2 said:**
> ```
##### /etc/modules ######################

lp
rtc
**[COLOR="#FF0000"]rtl8192ce[/COLOR]**

```
Please remove that entry with -
```
sudo sed -i '/rtl8192/ d' /etc/modules
```
I believe the blacklisting won't be necessary after removing that entry. Of course you'll need to reboot to see the change (in the output of "lsmod").

And you can (read - 'should') also delete the unnecessary conf files -
```
sudo rm /etc/modprobe.d/modprobe.conf
sudo rm /etc/modprobe.d/rtl8192ce.conf
```
..and overwrite the "rtl8192se.conf" file to correct its contents, as it is setting options for "rtl....[COLOR="#FF0000"]ce[/COLOR]", not "...[COLOR="#0000CD"]se[/COLOR]" -
```
echo "options rtl8192se fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8192se.conf
```
Let us know the outcome. Post back a fresh report with the changes applied if the problem persists.

---

### Post by jean_bono2 on 2014-10-08
Thank you Varun for your time
I've done all these changes and restarted the computer
lsmod only presents the rtl8192[COLOR=#0000ff]se[/COLOR] which is what we wanted I suppose
I'll let you know if there is any problems still.

My iwconfig gives this
```
bono178@Bill:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Sarah Moody"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:22:3F:D0:B1:22   
          Bit Rate=18 Mb/s   Tx-Power=33 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=36/70  Signal level=-74 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:126   Missed beacon:0


```

Is that bit rate and Tx power fine?
I know a lot of people say you should put the bit rate to 54M
any advice?
Cheers

---

### Post by varunendra on 2014-10-08
The Tx power is more than fine, but the Bit Rate is a bit on the lower side. With a typical router that supports 'N' speeds, it should be above 54 Mbps (depending upon how much the router supports, how many connections are active, how good is the signal quality etc.).

With an older g-mode router, the best speeds are around 48 Mbps (it theoretically supports 54 Mbps max, with some proprietary patches - 110 Mbps max., but you never get the 'theoretical max.').

However, since your signal quality doesn't seem good enough (36/70) to support good speeds, so I think the max you can get 'practically' would be around 24-36 Mbps. You can try to manually set a higher speed with -
```
sudo iwconfig wlan0 rate 36M
```
..which would fix it to 36 Mbps. Or,
```
sudo iwconfig wlan0 rate 36M auto
```
..which would set it to 36 Mbps or lower, depending upon the signal quality. Please note that setting the rate higher than feasible on a signal strength may cause disconnection issues. So you may try various speeds and set it to the one that seems stable and good.

To set it to automatic mode again (so that the speed can dynamically change depending upon the signal quality) -
```
sudo iwconfig wlan0 rate auto
```

If the connection doesn't seem satisfactory, please post a fresh report to let us see if something else can be optimized.

---

### Post by jean_bono2 on 2014-10-08
Hello again
I'm afraid I'm still getting some deconnections...
```

########## wireless info START ##########

Report from: 08 Oct 2014 23:29 BST +0100

Booted last: 08 Oct 2014 09:10 BST +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:07 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172]
    Kernel driver in use: rtl8192se

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: Mitac Device [1071:9270]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 004: ID 05e3:0505 Genesys Logic, Inc. 
Bus 002 Device 003: ID 040b:2013 Weltrend Semiconductor 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8192se              63095  0 
rtlwifi                77814  1 rtl8192se
mac80211              630653  2 rtlwifi,rtl8192se
cfg80211              484040  2 mac80211,rtlwifi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e4b:d6ff:feea:a909/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:342308 errors:0 dropped:0 overruns:0 frame:0
          TX packets:259920 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:385965578 (385.9 MB)  TX bytes:36202231 (36.2 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Sarah Moody"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'Sarah Moody' [AN2]>   
          Bit Rate=18 Mb/s   Tx-Power=33 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:67   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [Sarah Moody] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192se
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           18 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    virginmedia1706905: Infra, <MAC 'virginmedia1706905' [AN1]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    *Sarah Moody:    Infra, <MAC 'Sarah Moody' [AN2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 48 WPA2
    SKYCBC48:        Infra, <MAC 'SKYCBC48' [AN3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA2

  IPv4 Settings:
    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/bono-mobile]] (600 root)
[connection] id=bono-mobile | type=802-11-wireless
[802-11-wireless] ssid=bono-mobile | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Sarah Moody]] (600 root)
[connection] id=Sarah Moody | type=802-11-wireless
[802-11-wireless] ssid=Sarah Moody | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Device or resource busy

##### module infos ######################

[rtl8192se]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
firmware:       rtlwifi/rtl8192sefw.bin
description:    Realtek 8192S/8191S 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     E017555728164F306FD7A0C
depends:        rtlwifi,mac80211
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtlwifi]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
author:         Benjamin Porter    <BenjaminPorter86@gmail.com>
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     2F6F23788C82F9B57DF797B
depends:        mac80211,cfg80211
vermagic:       3.13.0-36-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        38:F3:B6:C6:3A:85:AF:FD:FB:BE:0E:53:33:9D:F8:E0:C6:B6:C9:D5
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        38:F3:B6:C6:3A:85:AF:FD:FB:BE:0E:53:33:9D:F8:E0:C6:B6:C9:D5
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8192se]
debug: 0
fwlps: N
ips: N
swenc: N
swlps: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

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
blacklist rtl8192ce

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

[/etc/modprobe.d/rtl8192se.conf]
options rtl8192se fwlps=N ips=N

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8172 (rtl8192se)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[41689.520951] wlan0: Connection to AP <MAC 'Sarah Moody' [AN2]> lost
[41702.217233] wlan0: authenticate with <MAC 'Sarah Moody' [AN2]>
[41702.228070] wlan0: send auth to <MAC 'Sarah Moody' [AN2]> (try 1/3)
[41702.230413] wlan0: authenticated
[41702.232428] wlan0: associate with <MAC 'Sarah Moody' [AN2]> (try 1/3)
[41702.237031] wlan0: RX AssocResp from <MAC 'Sarah Moody' [AN2]> (capab=0x411 status=0 aid=1)
[41702.240278] wlan0: associated
[50105.473577] wlan0: Connection to AP <MAC 'Sarah Moody' [AN2]> lost
[50112.361040] wlan0: authenticate with <MAC 'Sarah Moody' [AN2]>
[50112.361219] wlan0: send auth to <MAC 'Sarah Moody' [AN2]> (try 1/3)
[50112.370825] wlan0: authenticated
[50112.373623] wlan0: associate with <MAC 'Sarah Moody' [AN2]> (try 1/3)
[50112.401117] wlan0: RX AssocResp from <MAC 'Sarah Moody' [AN2]> (capab=0x411 status=0 aid=1)
[50112.404536] wlan0: associated
[50219.771264] wlan0: Connection to AP <MAC 'Sarah Moody' [AN2]> lost
[50232.423873] wlan0: authenticate with <MAC 'Sarah Moody' [AN2]>
[50232.434393] wlan0: direct probe to <MAC 'Sarah Moody' [AN2]> (try 1/3)
[50232.634797] wlan0: direct probe to <MAC 'Sarah Moody' [AN2]> (try 2/3)
[50232.838896] wlan0: direct probe to <MAC 'Sarah Moody' [AN2]> (try 3/3)
[50233.043122] wlan0: authentication with <MAC 'Sarah Moody' [AN2]> timed out
[50235.471685] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[51398.820150] wlan0: authenticate with <MAC 'Sarah Moody' [AN2]>
[51398.820336] wlan0: send auth to <MAC 'Sarah Moody' [AN2]> (try 1/3)
[51398.920961] wlan0: send auth to <MAC 'Sarah Moody' [AN2]> (try 2/3)
[51398.923039] wlan0: authenticated
[51398.924986] wlan0: associate with <MAC 'Sarah Moody' [AN2]> (try 1/3)
[51399.029019] wlan0: associate with <MAC 'Sarah Moody' [AN2]> (try 2/3)
[51399.133092] wlan0: associate with <MAC 'Sarah Moody' [AN2]> (try 3/3)
[51399.137411] wlan0: RX AssocResp from <MAC 'Sarah Moody' [AN2]> (capab=0x411 status=0 aid=1)
[51399.140880] wlan0: associated
[51399.140899] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############


```

Is it possible that the signal is just too weak and I need to bring a separate router upstairs?

---

### Post by varunendra on 2014-10-08
> **jean_bono2 said:**
> ```
##### module parameters #################

[rtl8192se]
debug: 0
fwlps: N
ips: N
swenc: N
**[COLOR="#FF0000"]swlps: Y[/COLOR]**
```
Interesting to see "swlps=Y" while modinfo says that its default value should be 0 (N)! Did you manually load it with the "Y" option? Because I can't see any configuration file to do that. If you did it manually (by running "modprobe ..." command with "swlps=Y" option), just don't do it and see if it helps. If it is happening by itself, let us force the value 'N' to keep it disabled too. To force it, just add the option to the existing list of options in the "rtl8192se.conf" file, which the following command will do for you -
```
sudo sed -i 's/options.*/& swlps=N/' /etc/modprobe.d/rtl8192se.conf
```
Reboot and if the disconnection happens again, check the parameter values with -
```
grep -R [[:alnum:]] /sys/module/rtl8192se/parameters
```
We want to see the values of **ips, fwlps** and **swlps** to be "**N**".

> **jean_bono2 said:**
> Is it possible that the signal is just too weak and I need to bring a separate router upstairs?
Yes it is quite possible. But then 38/70 is not too bad. I can stay connected all day long on that kind of signal quality (34 to 38), but then I have a different card (Atheros AR9285, which I personally consider to be far better than most Realtek cards) and the signal strength in my office usually remains stable.

Let's try to make a few more things better just to rule out the possibility of them playing up.

Assuming from your timezone setting that you are in London (or nearby), please set your RegDomain code explicitly -
```
sudo sed -i 's/^REG.*=$/&GB/' /etc/default/crda
sudo iw reg set GB
```
If you happen to be in a different place, please refer to this table to confirm your country code (and replace 'GB' with that one above) : [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table)

Also, if it is not too much trouble, try changing the SSID of your router (by logging into the router's admin panel) to something that doesn't contain blank spaces, nor special characters. For example, you could change it to "sarah_moody". But do it only if it is easy for you. Since you are able to connect, I don't think the SSID name should be a problem here.

If these two changes don't help, we can still try out a couple of newer drivers to see if they can perform any better. But if the problem is really the signal quality, I doubt they may.

Do you have any other device/laptop to check the signal quality at the same place to confirm that the low signal is not a card or driver fault? For example another laptop running windows or a WiFi capable handheld like a tablet or smart phone?

---

