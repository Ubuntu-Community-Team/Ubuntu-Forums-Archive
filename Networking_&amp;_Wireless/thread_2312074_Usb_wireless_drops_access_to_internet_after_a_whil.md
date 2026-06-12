---
title: "Usb wireless drops access to internet after a while (still connected) info after drop"
date: 2016-02-01
forum: Networking &amp; Wireless
---

### Post by witmolii42 on 2016-02-01
Here is info after dropped internet (status still connected). Please help or suggest a usb wireless stick that works with ubuntu. Thanks.



########## wireless info START ##########


Report from: 02 Feb 2016 01:02 EET +0200


Booted last: 02 Feb 2016 00:00 EET +0200


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.19.0-47-generic #53~14.04.1-Ubuntu SMP Mon Jan 18 16:09:14 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash


##### desktop ###########################


Ubuntu


##### lspci #############################


04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 01)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:379c]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 001 Device 006: ID 07b8:e004 AboCom Systems Inc Mass Storage Device
Bus 001 Device 005: ID 0bf8:100f Fujitsu Siemens Computers miniCard D2301 802.11bg Wireless Module [SiS 163U]
Bus 001 Device 002: ID 2001:3308 D-Link Corp. DWA-121 802.11n Wireless N 150 Pico Adapter [Realtek RTL8188CUS]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0b05:17cb ASUSTek Computer, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 003 Device 002: ID 04ca:008e Lite-On Technology Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


rtl8192cu              69632  0 
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        53248  1 rtl8192cu
rtlwifi                73728  3 rtl_usb,rtl8192c_common,rtl8192cu
mac80211              708608  3 rtl_usb,rtlwifi,rtl8192cu
cfg80211              524288  2 mac80211,rtlwifi


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


virbr0    Link encap:Ethernet  HWaddr <MAC 'virbr0' [IF]>  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44149 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45048 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33261332 (33.2 MB)  TX bytes:7807718 (7.8 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


virbr0    no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"Koalaverkko"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: <MAC 'Koalaverkko' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thrff
          Power Managementff
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:62   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root      1040     1  0 Feb01 ?        00:00:02 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: wlan0  [Koalaverkko] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           72 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *Koalaverkko:    Infra, <MAC 'Koalaverkko' [AC1]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 56 WPA WPA2
    N300:            Infra, <MAC 'N300' [AN2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA


  IPv4 Settings:
    Address:         192.168.0.11
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             62.241.198.246
    DNS:             62.241.198.245


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


[[/etc/NetworkManager/system-connections/Koalaverkko]] (600 root)
[connection] id=Koalaverkko | type=802-11-wireless
[802-11-wireless] ssid=Koalaverkko | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Helsinki (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


virbr0    no frequency information.


lo        no frequency information.


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
          Current Frequency:2.457 GHz (Channel 10)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


virbr0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:2.457 GHz (Channel 10)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Koalaverkko' [AC1]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption keyn
                    ESSID:"Koalaverkko"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f18ec8a6f6
                    Extra: Last beacon: 128ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'SuWiFi' [AC2]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption keyn
                    ESSID:"SuWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000014ca37c8154
                    Extra: Last beacon: 364ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Kotiffc0' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption keyn
                    ESSID:"Kotiffc0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003b0c151741
                    Extra: Last beacon: 964ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rtl8192cu]
filename:       /lib/modules/3.19.0-47-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
srcversion:     378B7DF8E269A40CAC1B9F2
depends:        rtlwifi,rtl8192c-common,rtl_usb,mac80211
intree:         Y
vermagic:       3.19.0-47-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        83:35:C3:0C:F4:5A:C8:87:4B:83:81:61:92:BF:33DC:B5:32:B6
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


[rtl_usb]
filename:       /lib/modules/3.19.0-47-generic/kernel/drivers/net/wireless/rtlwifi/rtl_usb.ko
description:    USB basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     814A6FB8DBFFB696F45B316
depends:        rtlwifi,mac80211
intree:         Y
vermagic:       3.19.0-47-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        83:35:C3:0C:F4:5A:C8:87:4B:83:81:61:92:BF:33DC:B5:32:B6
sig_hashalgo:   sha512


[rtl8192c_common]
filename:       /lib/modules/3.19.0-47-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     134BAE300AAF914967D6C6C
depends:        rtlwifi
intree:         Y
vermagic:       3.19.0-47-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        83:35:C3:0C:F4:5A:C8:87:4B:83:81:61:92:BF:33DC:B5:32:B6
sig_hashalgo:   sha512


[rtlwifi]
filename:       /lib/modules/3.19.0-47-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     35016235A31CEB1854418E1
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-47-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        83:35:C3:0C:F4:5A:C8:87:4B:83:81:61:92:BF:33DC:B5:32:B6
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.19.0-47-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     47672A7084D52DFBE51E2D2
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-47-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        83:35:C3:0C:F4:5A:C8:87:4B:83:81:61:92:BF:33DC:B5:32:B6
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algoefault rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.19.0-47-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-47-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        83:35:C3:0C:F4:5A:C8:87:4B:83:81:61:92:BF:33DC:B5:32:B6
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghzisable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


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


[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[ 3897.008405] wlan0: authenticate with <MAC 'Koalaverkko' [AC1]>
[ 3897.031285] wlan0: send auth to <MAC 'Koalaverkko' [AC1]> (try 1/3)
[ 3897.054856] wlan0: authenticated
[ 3897.056025] wlan0: associate with <MAC 'Koalaverkko' [AC1]> (try 1/3)
[ 3897.062971] wlan0: RX AssocResp from <MAC 'Koalaverkko' [AC1]> (capab=0x411 status=0 aid=5)
[ 3897.063607] wlan0: associated
[15263.013687] wlan0: deauthenticating from <MAC 'Koalaverkko' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[15263.804417] wlan0: authenticate with <MAC 'Koalaverkko' [AC1]>
[15263.831227] wlan0: send auth to <MAC 'Koalaverkko' [AC1]> (try 1/3)
[15263.862042] wlan0: authenticated
[15263.864018] wlan0: associate with <MAC 'Koalaverkko' [AC1]> (try 1/3)
[15263.879278] wlan0: RX AssocResp from <MAC 'Koalaverkko' [AC1]> (capab=0x411 status=0 aid=5)
[15263.879906] wlan0: associated
[15535.904430] wlan0: deauthenticating from <MAC 'Koalaverkko' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[15536.708388] wlan0: authenticate with <MAC 'Koalaverkko' [AC1]>
[15536.731712] wlan0: send auth to <MAC 'Koalaverkko' [AC1]> (try 1/3)
[15536.749184] wlan0: authenticated
[15536.752351] wlan0: associate with <MAC 'Koalaverkko' [AC1]> (try 1/3)
[15536.778811] wlan0: RX AssocResp from <MAC 'Koalaverkko' [AC1]> (capab=0x411 status=0 aid=5)
[15536.779525] wlan0: associated
[16103.921774] wlan0: deauthenticating from <MAC 'Koalaverkko' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[16104.792485] wlan0: authenticate with <MAC 'Koalaverkko' [AC1]>
[16104.815524] wlan0: send auth to <MAC 'Koalaverkko' [AC1]> (try 1/3)
[16104.825593] wlan0: authenticated
[16104.828028] wlan0: associate with <MAC 'Koalaverkko' [AC1]> (try 1/3)
[16104.873707] wlan0: RX AssocResp from <MAC 'Koalaverkko' [AC1]> (capab=0x411 status=0 aid=5)
[16104.874344] wlan0: associated
[16761.864809] wlan0: deauthenticating from <MAC 'Koalaverkko' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[16762.644524] wlan0: authenticate with <MAC 'Koalaverkko' [AC1]>
[16762.667491] wlan0: send auth to <MAC 'Koalaverkko' [AC1]> (try 1/3)
[16762.683819] wlan0: authenticated
[16762.688012] wlan0: associate with <MAC 'Koalaverkko' [AC1]> (try 1/3)
[16762.710197] wlan0: RX AssocResp from <MAC 'Koalaverkko' [AC1]> (capab=0x411 status=0 aid=5)
[16762.710949] wlan0: associated
[16762.766181] wlan0: deauthenticating from <MAC 'Koalaverkko' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[16762.778436] wlan0: authenticate with <MAC 'Koalaverkko' [AC1]>
[16762.789618] wlan0: send auth to <MAC 'Koalaverkko' [AC1]> (try 1/3)
[16762.791707] wlan0: authenticated
[16762.792034] wlan0: associate with <MAC 'Koalaverkko' [AC1]> (try 1/3)
[16762.817077] wlan0: RX AssocResp from <MAC 'Koalaverkko' [AC1]> (capab=0x411 status=0 aid=5)
[16762.817810] wlan0: associated


########## wireless info END ############

---

