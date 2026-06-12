---
title: "Centrino Advanced-N 6235 (rev 24) - wifi almost unusable lately"
date: 2016-06-08
forum: Networking &amp; Wireless
---

### Post by paul261 on 2016-06-08
Hi, I didn't want to resort to posting in here, but I've been wrestling with this issue for... ages now... and **I gots work to do**. :( Wireless quality is horrible, download speeds are around 6Mbps (if it doesn't just stall out or sit there trying to resolve hosts) when it should be more like 75mbps (which is what my iPad gets). And I can hardly ever see/connect to my N network. Can any networking veterans give me a much-appreciated hand? Thanks! 

Here is the result of the wireless-info script:


```
########## wireless info START ##########


Report from: 08 Jun 2016 11:36 EDT -0400


Booted last: 05 Jun 2016 14:46 EDT -0400


Script from: 26 May 2016 21:56 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-87-generic #133-Ubuntu SMP Tue May 24 18:32:09 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


GNOME Flashback (Metacity)


##### lspci #############################


02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6235 [8086:088e] (rev 24)
    Subsystem: Intel Corporation Centrino Advanced-N 6235 AGN [8086:4060]
    Kernel driver in use: iwlwifi


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 009: ID 125f:312b A-DATA Technology Co., Ltd. Superior S102 Pro
Bus 003 Device 004: ID 2109:0812 VIA Labs, Inc. VL812 Hub
Bus 003 Device 003: ID 05dc:a840 Lexar Media, Inc. 
Bus 003 Device 002: ID 2109:0812 VIA Labs, Inc. VL812 Hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 8087:07da Intel Corp. 
Bus 002 Device 004: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 002 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 002 Device 011: ID 04f9:0062 Brother Industries, Ltd 
Bus 002 Device 009: ID 05dc:a81d Lexar Media, Inc. 
Bus 002 Device 008: ID 2109:2812 VIA Labs, Inc. VL812 Hub
Bus 002 Device 021: ID 0e6f:0213 Logic3 
Bus 002 Device 002: ID 2109:2812 VIA Labs, Inc. VL812 Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


rt73usb                31580  0 
rt2x00usb              20742  1 rt73usb
rt2x00lib              55307  2 rt73usb,rt2x00usb
crc_itu_t              12707  1 rt73usb
rtl8192cu              67723  0 
rtl_usb                18448  1 rtl8192cu
rtlwifi                63475  2 rtl_usb,rtl8192cu
rtl8192c_common        53172  1 rtl8192cu
iwldvm                236381  0 
mac80211              638901  6 rtl_usb,rtlwifi,rt2x00lib,rt2x00usb,iwldvm,rtl8192cu
iwlwifi               174028  1 iwldvm
cfg80211              496328  5 iwlwifi,mac80211,rtlwifi,rt2x00lib,iwldvm


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:192.168.1.74  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4193984 errors:0 dropped:122337 overruns:0 frame:0
          TX packets:3652319 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2782485717 (2.7 GB)  TX bytes:1789469434 (1.7 GB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"blue_sky"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'blue_sky' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:109   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 8.8.8.8
nameserver 8.8.4.4


##### network managers ##################


Installed:


    NetworkManager


Running:


root     23482     1  0 11:34 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF1]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: wlan0  [blue_sky] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF2]>


  Capabilities:
    Speed:           72 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    BELL229:         Infra, <MAC 'BELL229' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2
    BELL1166:        Infra, <MAC 'BELL1166' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    BELL1166:        Infra, <MAC 'BELL1166' [AC5]>, Freq 5805 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    BELL113:         Infra, <MAC 'BELL113' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WEP
    *blue_sky:       Infra, <MAC 'blue_sky' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 69 WPA2


  IPv4 Settings:
    Address:         192.168.1.74
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             8.8.8.8
    DNS:             8.8.4.4


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/blue_sky 1]] (600 root)
[connection] id=blue_sky 1 | type=802-11-wireless
[802-11-wireless] ssid=blue_sky | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/blue_sky]] (600 root)
[connection] id=blue_sky | type=802-11-wireless
[802-11-wireless] ssid=blue_sky | bssid=<MAC 'blue_sky' [AC1]> | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=manual
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/blue_sky 2]] (600 root)
[connection] id=blue_sky 2 | type=802-11-wireless
[802-11-wireless] ssid=blue_sky | mac-address=<MAC address>
[ipv4] method=manual
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/grey_sky]] (600 root)
[connection] id=grey_sky | type=802-11-wireless
[802-11-wireless] ssid=grey_sky | bssid=<MAC address> | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=manual
[ipv6] method=ignore


##### iw reg get ########################


Region: America/Toronto (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


wlan0     32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.437 GHz (Channel 6)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.805 GHz


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'blue_sky' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"blue_sky"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ac12ea51f
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'BELL113' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"BELL113"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000008d07b2
                    Extra: Last beacon: 40ms ago
          Cell 03 - Address: <MAC 'BELL229' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-31 dBm  
                    Encryption key:on
                    ESSID:"BELL229"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000099b6d527c
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'BELL1166' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"BELL1166"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003b13ea7e46
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'BELL1166' [AC5]>
                    Channel:161
                    Frequency:5.805 GHz
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"BELL1166"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003b1795303b
                    Extra: Last beacon: 260ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rt73usb]
filename:       /lib/modules/3.13.0-87-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
license:        GPL
firmware:       rt73.bin
description:    Ralink RT73 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     66CCBB24DCA72AAD23E9588
depends:        rt2x00lib,rt2x00usb,crc-itu-t
intree:         Y
vermagic:       3.13.0-87-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:17:8A:95:D5:8F:38:DB:A1:2B:AD:4C:52:C4:25:7E:44:D6:AB:5B
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2x00usb]
filename:       /lib/modules/3.13.0-87-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     C8AA2904FC6A58104E65BCC
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.13.0-87-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:17:8A:95:D5:8F:38:DB:A1:2B:AD:4C:52:C4:25:7E:44:D6:AB:5B
sig_hashalgo:   sha512


[rt2x00lib]
filename:       /lib/modules/3.13.0-87-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     09822BD19555F112E3902D4
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-87-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:17:8A:95:D5:8F:38:DB:A1:2B:AD:4C:52:C4:25:7E:44:D6:AB:5B
sig_hashalgo:   sha512


[rtl8192cu]
filename:       /lib/modules/3.13.0-87-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
srcversion:     503A009BEFC80A2CC32099E
depends:        rtlwifi,rtl8192c-common,rtl_usb,mac80211
intree:         Y
vermagic:       3.13.0-87-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:17:8A:95:D5:8F:38:DB:A1:2B:AD:4C:52:C4:25:7E:44:D6:AB:5B
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


[rtl_usb]
filename:       /lib/modules/3.13.0-87-generic/kernel/drivers/net/wireless/rtlwifi/rtl_usb.ko
description:    USB basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     25A04A53549C90C495EC03F
depends:        rtlwifi,mac80211
intree:         Y
vermagic:       3.13.0-87-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:17:8A:95:D5:8F:38:DB:A1:2B:AD:4C:52:C4:25:7E:44:D6:AB:5B
sig_hashalgo:   sha512


[rtlwifi]
filename:       /lib/modules/3.13.0-87-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     730FEE1A7696EA37A982482
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-87-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:17:8A:95:D5:8F:38:DB:A1:2B:AD:4C:52:C4:25:7E:44:D6:AB:5B
sig_hashalgo:   sha512


[rtl8192c_common]
filename:       /lib/modules/3.13.0-87-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
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
vermagic:       3.13.0-87-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:17:8A:95:D5:8F:38:DB:A1:2B:AD:4C:52:C4:25:7E:44:D6:AB:5B
sig_hashalgo:   sha512


[iwldvm]
filename:       /lib/modules/3.13.0-87-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     9036600D780304CB32B6EF2
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-87-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:17:8A:95:D5:8F:38:DB:A1:2B:AD:4C:52:C4:25:7E:44:D6:AB:5B
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-87-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C31A92A72ADA65F2F8247FB
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-87-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:17:8A:95:D5:8F:38:DB:A1:2B:AD:4C:52:C4:25:7E:44:D6:AB:5B
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.13.0-87-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     F935FAF50D9A6B3215203C9
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-87-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:17:8A:95:D5:8F:38:DB:A1:2B:AD:4C:52:C4:25:7E:44:D6:AB:5B
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)


[cfg80211]
filename:       /lib/modules/3.13.0-87-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     0055529745EF9A8A3E57FC3
depends:        
intree:         Y
vermagic:       3.13.0-87-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:17:8A:95:D5:8F:38:DB:A1:2B:AD:4C:52:C4:25:7E:44:D6:AB:5B
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rt73usb]
nohwcrypt: N


[rtl8192cu]
debug: 0
swenc: N


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
wd_disable: 1


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
options iwlwifi 11n_disable=0


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x088e (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt73usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"


##### dmesg #############################


[201704.365397] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[201733.691495] wlan0: authenticate with <MAC 'blue_sky' [AC1]>
[201733.697162] wlan0: send auth to <MAC 'blue_sky' [AC1]> (try 1/3)
[201733.699901] wlan0: authenticated
[201733.700221] wlan0: associate with <MAC 'blue_sky' [AC1]> (try 1/3)
[201733.704836] wlan0: RX AssocResp from <MAC 'blue_sky' [AC1]> (capab=0x411 status=0 aid=5)
[201733.711116] wlan0: associated
[201733.711182] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[242490.518469] wlan0: authenticate with <MAC 'blue_sky' [AC1]>
[242490.521271] wlan0: send auth to <MAC 'blue_sky' [AC1]> (try 1/3)
[242490.526163] wlan0: authenticated
[242490.530350] wlan0: associate with <MAC 'blue_sky' [AC1]> (try 1/3)
[242490.534236] wlan0: RX AssocResp from <MAC 'blue_sky' [AC1]> (capab=0x411 status=0 aid=2)
[242490.538970] wlan0: associated
[242673.600415] wlan0: authenticate with <MAC 'blue_sky' [AC1]>
[242673.602695] wlan0: send auth to <MAC 'blue_sky' [AC1]> (try 1/3)
[242673.605373] wlan0: authenticated
[242673.606855] wlan0: associate with <MAC 'blue_sky' [AC1]> (try 1/3)
[242673.611203] wlan0: RX AssocResp from <MAC 'blue_sky' [AC1]> (capab=0x411 status=0 aid=2)
[242673.613348] wlan0: associated
[242693.679890] wlan0: authenticate with <MAC 'blue_sky' [AC1]>
[242693.682397] wlan0: send auth to <MAC 'blue_sky' [AC1]> (try 1/3)
[242693.685118] wlan0: authenticated
[242693.687374] wlan0: associate with <MAC 'blue_sky' [AC1]> (try 1/3)
[242693.691410] wlan0: RX AssocResp from <MAC 'blue_sky' [AC1]> (capab=0x411 status=0 aid=2)
[242693.693765] wlan0: associated
[247810.109468] wlan0: deauthenticating from <MAC 'blue_sky' [AC1]> by local choice (reason=3)
[247810.435066] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[247810.466159] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[247810.667640] iwlwifi 0000:02:00.0: L1 Disabled - LTR Disabled
[247810.674389] iwlwifi 0000:02:00.0: Radio type=0x2-0x1-0x0
[247810.947204] iwlwifi 0000:02:00.0: L1 Disabled - LTR Disabled
[247810.953975] iwlwifi 0000:02:00.0: Radio type=0x2-0x1-0x0
[247811.041204] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[247811.087642] r8169 0000:03:00.0 eth0: link down
[247811.087702] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[247814.425522] wlan0: authenticate with <MAC 'blue_sky' [AC1]>
[247814.428195] wlan0: send auth to <MAC 'blue_sky' [AC1]> (try 1/3)
[247814.431102] wlan0: authenticated
[247814.434934] wlan0: associate with <MAC 'blue_sky' [AC1]> (try 1/3)
[247814.438529] wlan0: RX AssocResp from <MAC 'blue_sky' [AC1]> (capab=0x411 status=0 aid=2)
[247814.440734] wlan0: associated
[247814.440804] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############



```

---

### Post by paul261 on 2016-06-13
I picked up a wireless Ethernet bridge ([https://www.iogear.com/product/GWU627/](https://www.iogear.com/product/GWU627/)) to try to bypass the issue entirely (assuming it was a wireless driver issue). But strangely, I get very similar results. The download speed is still a fraction of what it should be... varies between about 3-10mbps down, 8-10mbps up.

---

### Post by jeremy31 on 2016-06-13
Can you change the wifi router to channel 9?  The results show a stronger access point on the same channel

---

### Post by paul261 on 2016-06-13
Well hey now my 5GHz network is showing up... thanks for that. ;) I connected to that and the speed test looked better, however switching back to the g network and running the same test didn't show any real improvement. The results still are quite variable, at around ~10% of what I'm expecting.

---

### Post by jeremy31 on 2016-06-14
If you are going to run on G, see it ```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlopts.conf
```
Helps after a reboot.  If you want to use on N replace the 1 with an 8

---

### Post by paul261 on 2016-06-14
Ys, I have messed with 11n_disable settings, currently have:
```
options iwlwifi bt_coex_active=0 swcrypto=1 11n_disable=8
```

But this really doesn't seem to improve the speed, especially on the g network. The strange thing is how slow the wireless ethernet bridge also is. I assume this must also be related to the ethernet adapter driver (RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller).

Now that I can connect to the N network, speeds are better, but it doesn't really solve any of the mysteries so far.

---

### Post by jeremy31 on 2016-06-14
Do your USB wifi adapters work any better, there were signs of two different USB wifis being used.  Your ethernet might need a different module but the r8168-dkms in the repos doesn't build on 3.19 if I remember correctly.

Your resolv.conf file is different than mine and it is used to resolve hosts.  See if ```
echo "nameserver 127.0.1.1" | sudo tee -a /etc/resolv.conf
``` helps after a reboot

---

### Post by paul261 on 2016-06-15
I'm actually on 3.13.0-88 right now... r8168-dkms installs just fine. Actually can't even communicate with the bridge now, I think I may have messed up the driver or perhaps bricked the bridge, heh.

/etc/resolv.conf is dynamically generated. Changing to 127.0.0.1 results in no DNS resolution at all. Shouldn't affect transfer speed anyway?

---

### Post by jeremy31 on 2016-06-15
I edited the other post, it should be 127.0.1.1 and it might be the google DNS that is slowing things down.  I used them for a while and deleted the entries

---

### Post by paul261 on 2016-06-20
Nope, no change. Can't connect after that change, in fact (I assume you meant 127.0.0.1).

---

