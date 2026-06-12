---
title: "rtl8192cu suddenly stoped working on Ubuntu 14.10"
date: 2015-04-13
forum: Networking &amp; Wireless
---

### Post by markohrastovec on 2015-04-13
Hi,

I have strange problems with my rtl8192cu usb dongle. I used one of many fixed 8192cu fixed driver versions ([https://github.com/dz0ny/rt8192cu](https://github.com/dz0ny/rt8192cu)) for months without any problem. Then one day the wireless stopped working without a warning. I don't remember whether I have upgraded the kernel at that time, but I think I didn't. I suspected broken usb dongle and bought another one. To my disappointment the new dongle has a bad reception and speed (lowest price :mad:). So I bought another one via internet and the new one has rtl8192cu chipset again. The problems with the new dongle are identical to the previous one so I believe hardware works.

Here is the output from the troubleshooting script:
```

########## wireless info START ##########


Report from: 13 Apr 2015 06:20 CEST +0200


Booted last: 13 Apr 2015 06:10 CEST +0200


Script from: 06 Apr 2015 17:23 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic


##### kernel ############################


Linux 3.16.0-34-generic #45-Ubuntu SMP Mon Mar 23 17:21:27 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


GNOME


##### lspci #############################


00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Hewlett-Packard Company Device [103c:1495]
    Kernel driver in use: e1000e


03:00.0 Ethernet controller [0200]: Intel Corporation 82574L Gigabit Network Connection [8086:10d3]
    Subsystem: Intel Corporation Gigabit CT Desktop Adapter [8086:a01f]
    Kernel driver in use: e1000e


##### lsusb #############################


Bus 002 Device 004: ID 1058:0704 Western Digital Technologies, Inc. Passport External HDD
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 003: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


r8188eu               703161  0 
cfg80211              510218  0 
ndiswrapper           288024  0 
hp_wmi                 14109  0 
sparse_keymap          13948  1 hp_wmi
mxm_wmi                13021  1 nouveau
wmi                    19193  3 hp_wmi,mxm_wmi,nouveau


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:172.20.46.61  Bcast:172.20.46.255  Mask:255.255.255.0
          inet6 addr: fe80::a2e:5fff:fe15:5d30/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:368 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47012 (47.0 KB)  TX bytes:36171 (36.1 KB)
          Interrupt:20 Memory:fb500000-fb520000 


eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:fb4c0000-fb4e0000 


wlan4     Link encap:Ethernet  HWaddr <MAC 'wlan4' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:5 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


eth0      no wireless extensions.


eth1      no wireless extensions.


lo        no wireless extensions.


wlan4     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        172.20.46.1     255.0.0.0       UG    0      0        0 eth0
172.20.1.16     172.20.46.1     255.255.255.255 UGH   0      0        0 eth0
172.20.38.0     172.20.46.1     255.255.255.0   UG    0      0        0 eth0
172.20.46.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth1' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: wlan4  [intguest] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connecting (configuring)
  Default:           no
  HW Address:        <MAC 'wlan4' [IF]>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    pubguest:        Infra, <MAC 'pubguest' [AC1]>, Freq 2437 MHz, Rate 16 Mb/s, Strength 76 WPA2
    intguest:        Infra, <MAC 'intguest' [AC2]>, Freq 2437 MHz, Rate 16 Mb/s, Strength 75 WPA2 Enterprise
    pubguest:        Infra, <MAC 'pubguest' [AN3]>, Freq 2462 MHz, Rate 16 Mb/s, Strength 44 WPA2
    intguest:        Infra, <MAC 'intguest' [AN4]>, Freq 2462 MHz, Rate 16 Mb/s, Strength 43 WPA2 Enterprise
    intguest:        Infra, <MAC 'intguest' [AN5]>, Freq 2462 MHz, Rate 16 Mb/s, Strength 46 WPA2 Enterprise


- Device: eth0  [dev static] ---------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         172.20.46.61
    Prefix:          24 (255.255.255.0)
    Gateway:         172.20.46.1


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


[[/etc/NetworkManager/system-connections/intguest]] (600 root)
[ipv6] method=auto
[connection] id=intguest | type=802-11-wireless | permissions=user:xxxx:;
[802-11-wireless] ssid=intguest
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/pubguest]] (600 root)
[connection] id=pubguest | type=802-11-wireless
[802-11-wireless] ssid=pubguest | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/pubguest 1]] (600 root)
[connection] id=pubguest 1 | type=802-11-wireless
[802-11-wireless] ssid=pubguest | mac-address=<MAC 'wlan4' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Ljubljana (based on set time zone)


country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), NO-IR
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), NO-IR
    (5735 - 5835 @ 40), (3, 20), NO-IR


##### iwlist channels ###################


eth0      no frequency information.


eth1      no frequency information.


lo        no frequency information.


wlan4     13 channels in total; available frequencies :
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


      4   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)


eth0      Interface doesn't support scanning.


eth1      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan4     Scan completed :
          Cell 01 - Address: <MAC 'pubguest' [AC1]>
                    ESSID:"pubguest"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=20/100  Signal level=70/100  
          Cell 02 - Address: <MAC 'intguest' [AC2]>
                    ESSID:"intguest"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac012800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Quality=20/100  Signal level=73/100  
          Cell 03 - Address: <MAC '' [AC3]>
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac012800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Quality=41/100  Signal level=73/100  
          Cell 04 - Address: <MAC '' [AC4]>
                    ESSID:""
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Quality=20/100  Signal level=47/100  
          Cell 05 - Address: <MAC 'pubguest' [AC5]>
                    ESSID:"pubguest"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=47/100  


##### module infos ######################


[r8188eu]
filename:       /lib/modules/3.16.0-34-generic/kernel/drivers/staging/rtl8188eu/r8188eu.ko
version:        v4.1.4_6773.20130222
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     B39C03DECEDF449BE84019E
depends:        
staging:        Y
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B5:E4:B3:53:3B:47:25:9E:0A:1A:97:8F:5B:0C:60:07:EF:6E:33:E7
sig_hashalgo:   sha512
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_cbw40_enable:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_fw_iol:FW IOL (int)
parm:           rtw_mc2u_disable:int
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
parm:           debug:Set debug level (1-9) (default 1) (int)


[cfg80211]
filename:       /lib/modules/3.16.0-34-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     4A525D9D32B0C6D120CA547
depends:        
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B5:E4:B3:53:3B:47:25:9E:0A:1A:97:8F:5B:0C:60:07:EF:6E:33:E7
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[ndiswrapper]
filename:       /lib/modules/3.16.0-34-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     DC1EFD919FDF2DB80D424C6
depends:        
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)


##### module parameters #################


[r8188eu]
debug: 1
if2name: wlan%d
ifname: wlan%d
rtw_80211d: 0
rtw_ampdu_amsdu: 0
rtw_ampdu_enable: 1
rtw_antdiv_cfg: 2
rtw_antdiv_type: 0
rtw_busy_thresh: 40
rtw_cbw40_enable: 3
rtw_channel: 1
rtw_channel_plan: 66
rtw_chip_version: 0
rtw_enusbss: 0
rtw_fw_iol: 1
rtw_ht_enable: 1
rtw_hwpdn_mode: 2
rtw_hwpwrp_detect: 0
rtw_hw_wps_pbc: 1
rtw_initmac: (null)
rtw_ips_mode: 1
rtw_lbkmode: 0
rtw_low_power: 0
rtw_lowrate_two_xmit: 1
rtw_max_roaming_times: 2
rtw_mc2u_disable: 0
rtw_mp_mode: 0
rtw_network_mode: 0
rtw_notch_filter: 0
rtw_power_mgnt: 1
rtw_rf_config: 5
rtw_rfintfs: 2
rtw_rx_stbc: 1
rtw_smart_ps: 2
rtw_vcs_type: 1
rtw_vrtl_carrier_sense: 2
rtw_wifi_spec: 0
rtw_wmm_enable: 1


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]


##### /etc/modules ######################


loop
lp
8192cu


##### modprobe options ##################


[/etc/modprobe.d/8192cu.conf]
options 8192cu rtw_power_mgnt=0 rtw_enusbss=0


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
blacklist rtl8192cu


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


[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1


[/etc/modprobe.d/ndiswrapper.conf]
alias usb:v0409p0408d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0411p0242d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v04BBp094Cd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v04BBp0950d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v04BBp0952d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v04BBp0953d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v04F2pAFF7d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v04F2pAFF8d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v04F2pAFF9d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v04F2pAFFAd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v04F2pAFFBd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v04F2pAFFCd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp1004d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp1102d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp1105d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp1109d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp110Ad*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp120Ad*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp2102d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp2103d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0586p341Fd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0586p3426d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v06F8pE033d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v06F8pE035d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0789p0019d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0789p016Dd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0789p016Ed*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v07AAp0056d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v07B8p8178d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v07B8p8179d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v07B8p8189d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v07B8p8193d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9051d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9052d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0B05p17ABd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0B05p17BAd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0B05p17C0d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0B05p17D2d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp0179d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp018Ad*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp0193d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp0723d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp0724d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp0811d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp0820d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp1724d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp317Fd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp8111d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp8170d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp8176d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp8177d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp8178d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp8179d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp817Ad*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp817Bd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp817Cd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp817Ed*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp817Fd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp818Ad*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp818Bd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp818Cd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp8192d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp8193d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp8194d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp819Ad*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp8725d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp872Bd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp8812d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDApA179d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDApA724d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDApE194d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BFFp8160d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0DF6p0052d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0DF6p005Cd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0DF6p0061d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0DF6p0074d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0E66p0019d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0E66p0020d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0E66p0022d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0EB0p9071d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v103Cp1629d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v1058p0632d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v13B1p003Fd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v13D3p3357d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v13D3p3358d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v13D3p3359d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v148Fp9097d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v1740p0100d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2001p3307d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2001p3308d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2001p3309d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2001p330Ad*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2001p330Bd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2001p330Cd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2001p330Ed*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2001p3313d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2001p3314d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2001p3315d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2001p3316d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2019p1201d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2019p4902d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2019p4903d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2019p4904d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2019pAB2Ad*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2019pAB2Bd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2019pAB2Cd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2019pAB2Dd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2019pAB2Ed*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2019pED17d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v20F4p624Dd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v20F4p648Bd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v20F4p664Bd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v20F4p804Bd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v20F4p805Bd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2357p0100d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2357p0101d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v4855p0090d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v4855p0091d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v4856p0091d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v7392p7811d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v7392p7822d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v7392pA811d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v7392pA822d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:vCDABp8010d*dc*dsc*dp*ic*isc*ip* ndiswrapper


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# USB device 0x:0x (asix)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rtl8192eu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"
# USB device 0x:0x (r8188eu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan3"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan4' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan4"


##### dmesg #############################


[  660.386944] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[  664.793544] ==> rtl8192cu_hal_deinit 
[  667.366933] rtl8192cu_hal_init in 564ms
[  669.407694] ==> rtl8192cu_hal_deinit 
[  670.636548] rtl8192cu_hal_init in 568ms


########## wireless info END ############

```

The problem I have now is that the dongle does not want to connect to wireless network any more. The behaviour seems random because sometimes it succeeds. Here are the log outputs from an unsuccessful attempt, which repeats over and over:

```

Apr 13 06:20:55 markoh-HP NetworkManager[1239]: <info> Activation (wlan4) Stage 1 of 5 (Device Prepare) scheduled...
Apr 13 06:20:55 markoh-HP NetworkManager[1239]: <info> Activation (wlan4) Stage 1 of 5 (Device Prepare) started...
Apr 13 06:20:55 markoh-HP NetworkManager[1239]: <info> (wlan4): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Apr 13 06:20:55 markoh-HP NetworkManager[1239]: <info> Activation (wlan4) Stage 2 of 5 (Device Configure) scheduled...
Apr 13 06:20:55 markoh-HP NetworkManager[1239]: <info> Activation (wlan4) Stage 1 of 5 (Device Prepare) complete.
Apr 13 06:20:55 markoh-HP NetworkManager[1239]: <info> Activation (wlan4) Stage 2 of 5 (Device Configure) starting...
Apr 13 06:20:55 markoh-HP NetworkManager[1239]: <info> (wlan4): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 13 06:20:55 markoh-HP NetworkManager[1239]: <info> Activation (wlan4/wireless): connection 'intguest' has security, and secrets exist.  No new secrets needed.
Apr 13 06:20:55 markoh-HP NetworkManager[1239]: <info> Config: added 'ssid' value 'intguest'
Apr 13 06:20:55 markoh-HP NetworkManager[1239]: <info> Config: added 'scan_ssid' value '1'
Apr 13 06:20:55 markoh-HP NetworkManager[1239]: <info> Config: added 'key_mgmt' value 'WPA-EAP'
Apr 13 06:20:55 markoh-HP NetworkManager[1239]: <info> Config: added 'password' value '<omitted>'
Apr 13 06:20:55 markoh-HP NetworkManager[1239]: <info> Config: added 'eap' value 'PEAP'
Apr 13 06:20:55 markoh-HP NetworkManager[1239]: <info> Config: added 'fragment_size' value '1300'
Apr 13 06:20:55 markoh-HP NetworkManager[1239]: <info> Config: added 'phase2' value 'auth=MSCHAPV2'
Apr 13 06:20:55 markoh-HP NetworkManager[1239]: <info> Config: added 'identity' value 'xxxx\xxxx'
Apr 13 06:20:55 markoh-HP NetworkManager[1239]: <info> Config: added 'bgscan' value 'simple:30:-65:300'
Apr 13 06:20:55 markoh-HP NetworkManager[1239]: <info> Config: added 'proactive_key_caching' value '1'
Apr 13 06:20:55 markoh-HP NetworkManager[1239]: <info> Activation (wlan4) Stage 2 of 5 (Device Configure) complete.
Apr 13 06:20:55 markoh-HP NetworkManager[1239]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Apr 13 06:20:55 markoh-HP NetworkManager[1239]: <info> Config: set interface ap_scan to 1
Apr 13 06:20:56 markoh-HP wpa_supplicant[1827]: wlan4: Trying to associate with b4:e9:b0:b3:80:e2 (SSID='intguest' freq=2437 MHz)
Apr 13 06:20:56 markoh-HP wpa_supplicant[1827]: wlan4: Association request to the driver failed
Apr 13 06:20:56 markoh-HP kernel: [  682.278961] survey done event(15) band:0 for wlan4
Apr 13 06:20:56 markoh-HP kernel: [  682.279247] wpa_set_auth_algs, AUTH_ALG_OPEN_SYSTEM
Apr 13 06:20:56 markoh-HP kernel: [  682.279251] set_mode = IW_MODE_INFRA
Apr 13 06:20:56 markoh-HP kernel: [  682.279259] 
Apr 13 06:20:56 markoh-HP kernel: [  682.279259]  wpa_ie(length:22):
Apr 13 06:20:56 markoh-HP kernel: [  682.279261] 0x30 0x14 0x01 0x00 0x00 0x0f 0xac 0x04 
Apr 13 06:20:56 markoh-HP kernel: [  682.279262] 0x01 0x00 0x00 0x0f 0xac 0x04 0x01 0x00 
Apr 13 06:20:56 markoh-HP kernel: [  682.279264] 0x00 0x0f 0xac 0x01 0x00 0x00 0x00 0x00 
Apr 13 06:20:56 markoh-HP kernel: [  682.279839] hw_var_set_opmode()-4234 mode = 2
Apr 13 06:20:56 markoh-HP kernel: [  682.280216] SetHwReg8192CU, 5130, RCR= 700060ca 
Apr 13 06:20:56 markoh-HP kernel: [  682.280247] =>rtw_wx_set_essid
Apr 13 06:20:56 markoh-HP kernel: [  682.280249] ssid=intguest, len=8
Apr 13 06:20:56 markoh-HP kernel: [  682.280251] Set SSID under fw_state=0x00000008
Apr 13 06:20:56 markoh-HP kernel: [  682.280255] [by_bssid:0][assoc_ssid:intguest][to_roaming:0] new candidate: intguest(b4:e9:b0:b3:80:e2, ch6) rssi:-64
Apr 13 06:20:56 markoh-HP kernel: [  682.280257] rtw_select_and_join_from_scanned_queue: candidate: intguest(b4:e9:b0:b3:80:e2, ch:6)
Apr 13 06:20:56 markoh-HP kernel: [  682.280262] link to Cisco AP
Apr 13 06:20:56 markoh-HP kernel: [  682.280264] <=rtw_wx_set_essid, ret 0
Apr 13 06:20:56 markoh-HP kernel: [  682.280276] Set BSSID under fw_state=0x00000088
Apr 13 06:20:56 markoh-HP kernel: [  682.280587] start_join_set_ch_bw: ch=6, bwmode=0, ch_offset=0
Apr 13 06:20:56 markoh-HP NetworkManager[1239]: <info> (wlan4): supplicant interface state: scanning -> associating
Apr 13 06:20:56 markoh-HP kernel: [  682.797197] rtw_ack_tx_polling timeout
Apr 13 06:20:57 markoh-HP kernel: [  683.413478] rtw_ack_tx_polling timeout
Apr 13 06:20:57 markoh-HP kernel: [  684.029760] rtw_ack_tx_polling timeout
Apr 13 06:20:58 markoh-HP kernel: [  684.646043] rtw_ack_tx_polling timeout
Apr 13 06:20:59 markoh-HP kernel: [  685.262327] rtw_ack_tx_polling timeout
Apr 13 06:20:59 markoh-HP kernel: [  685.262331] issue_deauth_ex(wlan4) to b4:e9:b0:b3:80:e2, ch:6, 5/5 in 2976 ms
Apr 13 06:21:00 markoh-HP kernel: [  686.053063] link to Cisco AP
Apr 13 06:21:00 markoh-HP kernel: [  686.350824] link_timer_hdl: auth timeout and try again
Apr 13 06:21:00 markoh-HP kernel: [  686.650957] link_timer_hdl: auth timeout and try again
Apr 13 06:21:00 markoh-HP kernel: [  686.951096] link_timer_hdl: auth timeout and try again
Apr 13 06:21:01 markoh-HP kernel: [  687.251236] link_timer_hdl: auth timeout and try again
Apr 13 06:21:01 markoh-HP wpa_supplicant[1827]: wlan4: Authentication with b4:e9:b0:b3:80:e2 timed out.
Apr 13 06:21:01 markoh-HP wpa_supplicant[1827]: wlan4: CTRL-EVENT-DISCONNECTED bssid=b4:e9:b0:b3:80:e2 reason=3 locally_generated=1
Apr 13 06:21:01 markoh-HP wpa_supplicant[1827]: wlan4: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="intguest" auth_failures=1 duration=10
Apr 13 06:21:01 markoh-HP kernel: [  687.287062] rtw_wx_set_mlme
Apr 13 06:21:01 markoh-HP kernel: [  687.287065] rtw_wx_set_mlme, cmd=0, reason=3
Apr 13 06:21:01 markoh-HP kernel: [  687.287117] =>rtw_wx_set_essid
Apr 13 06:21:01 markoh-HP kernel: [  687.287119] ssid=^B^Z<FE>C<FB><FA><AA>:<FB>)<D1><E6>^E<|<94>u<U+063E>a<89><F9>\<BB><A8><99>^O<95><B1><EB><F1><B3>, len=32
Apr 13 06:21:01 markoh-HP kernel: [  687.287122] Set SSID under fw_state=0x00000088
Apr 13 06:21:01 markoh-HP kernel: [  687.287124] <=rtw_wx_set_essid, ret 0
Apr 13 06:21:01 markoh-HP NetworkManager[1239]: <warn> Connection disconnected (reason -3)
Apr 13 06:21:01 markoh-HP NetworkManager[1239]: <info> (wlan4): supplicant interface state: associating -> disconnected
Apr 13 06:21:01 markoh-HP kernel: [  687.551372] report_join_res(-1)
Apr 13 06:21:01 markoh-HP kernel: [  687.552387] HW_VAR_BASIC_RATE: BrateCfg(0x15d)
Apr 13 06:21:01 markoh-HP kernel: [  687.552981] =>mlmeext_joinbss_event_callback
Apr 13 06:21:01 markoh-HP kernel: [  687.555369] _rtw_join_timeout_handler, fw_state=8
Apr 13 06:21:01 markoh-HP kernel: [  687.555417] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
Apr 13 06:21:01 markoh-HP NetworkManager[1239]: <info> (wlan4): supplicant interface state: disconnected -> scanning
Apr 13 06:21:01 markoh-HP NetworkManager[1239]: <info> (wlan4): supplicant interface state: scanning -> disconnected
Apr 13 06:21:05 markoh-HP kernel: [  691.277087] ==>rtw_ps_processor .fw_state(8)
Apr 13 06:21:05 markoh-HP kernel: [  691.277089] ==>ips_enter cnts:21
Apr 13 06:21:05 markoh-HP kernel: [  691.277098] ===> rtw_ips_pwr_down...................
Apr 13 06:21:05 markoh-HP kernel: [  691.277337] ====> rtw_ips_dev_unload...
Apr 13 06:21:05 markoh-HP kernel: [  691.300608] usb_read_port_cancel
Apr 13 06:21:05 markoh-HP kernel: [  691.300811] usb_read_port_complete()-1284: RX Warning! bDriverStopped(0) OR bSurpriseRemoved(0) bReadPortCancel(1)
Apr 13 06:21:05 markoh-HP kernel: [  691.301062] usb_read_port_complete()-1284: RX Warning! bDriverStopped(0) OR bSurpriseRemoved(0) bReadPortCancel(1)
Apr 13 06:21:05 markoh-HP kernel: [  691.301332] usb_read_port_complete()-1284: RX Warning! bDriverStopped(0) OR bSurpriseRemoved(0) bReadPortCancel(1)
Apr 13 06:21:05 markoh-HP kernel: [  691.301560] usb_read_port_complete()-1284: RX Warning! bDriverStopped(0) OR bSurpriseRemoved(0) bReadPortCancel(1)
Apr 13 06:21:05 markoh-HP kernel: [  691.301563] usb_write_port_cancel 
Apr 13 06:21:05 markoh-HP kernel: [  691.301573] ==> rtl8192cu_hal_deinit 
Apr 13 06:21:05 markoh-HP kernel: [  691.301574] bkeepfwalive(0)
Apr 13 06:21:05 markoh-HP kernel: [  691.301574] card disble without HWSM...........
Apr 13 06:21:05 markoh-HP kernel: [  691.306582] <=== rtw_ips_pwr_down..................... in 28ms
Apr 13 06:21:06 markoh-HP kernel: [  692.570071] _rtw_pwr_wakeup call ips_leave....
Apr 13 06:21:06 markoh-HP kernel: [  692.570074] ==>ips_leave cnts:21
Apr 13 06:21:06 markoh-HP kernel: [  692.570075] ===>  rtw_ips_pwr_up..............
Apr 13 06:21:06 markoh-HP kernel: [  692.570077] ===> ips_netdrv_open.........
Apr 13 06:21:06 markoh-HP kernel: [  692.574891]  ===> FirmwareDownload91C() fw:Rtl819XFwImageArray_TSMC
Apr 13 06:21:06 markoh-HP kernel: [  692.574893] FirmwareDownload92C accquire FW from embedded image
Apr 13 06:21:06 markoh-HP kernel: [  692.574895] fw_ver=v88, fw_subver=2, sig=0x88c0
Apr 13 06:21:06 markoh-HP kernel: [  692.600157] fw download ok!
Apr 13 06:21:06 markoh-HP kernel: [  692.600159] Set RF Chip ID to RF_6052 and RF type to 2.
Apr 13 06:21:06 markoh-HP kernel: [  692.978822] IQK:Start!!!
Apr 13 06:21:06 markoh-HP kernel: [  692.990577] Path A IQK Success!!
Apr 13 06:21:06 markoh-HP kernel: [  692.995389] Path B IQK Success!!
Apr 13 06:21:06 markoh-HP kernel: [  693.003833] Path A IQK Success!!
Apr 13 06:21:06 markoh-HP kernel: [  693.008585] Path B IQK Success!!
Apr 13 06:21:06 markoh-HP kernel: [  693.021217] Path A IQK Success!!
Apr 13 06:21:06 markoh-HP kernel: [  693.025969] Path B IQK Success!!
Apr 13 06:21:06 markoh-HP kernel: [  693.030721] IQK: final_candidate is 1
Apr 13 06:21:06 markoh-HP kernel: [  693.030723] IQK: RegE94=100 RegE9C=3fa RegEA4=fb RegEAC=3fe RegEB4=101 RegEBC=9 RegEC4=fe RegECC=0
Apr 13 06:21:06 markoh-HP kernel: [  693.030723]  Path A IQ Calibration Success !
Apr 13 06:21:06 markoh-HP kernel: [  693.032849] Path B IQ Calibration Success !
Apr 13 06:21:07 markoh-HP kernel: [  693.146174] pdmpriv->TxPowerTrackControl = 1
Apr 13 06:21:07 markoh-HP kernel: [  693.150776] rtl8192cu_hal_init in 580ms
Apr 13 06:21:07 markoh-HP NetworkManager[1239]: <info> (wlan4): supplicant interface state: disconnected -> scanning
Apr 13 06:21:07 markoh-HP kernel: [  693.163411] <===  rtw_ips_pwr_up.............. in 592ms
Apr 13 06:21:07 markoh-HP kernel: [  693.163531] ==> ips_leave.....LED(0x00028080)...
Apr 13 06:21:08 markoh-HP kernel: [  694.472509] survey done event(f) band:0 for wlan4
Apr 13 06:21:09 markoh-HP kernel: [  695.166873] ==>rtw_ps_processor .fw_state(8)
Apr 13 06:21:09 markoh-HP kernel: [  695.166876] ==>ips_enter cnts:22
Apr 13 06:21:09 markoh-HP kernel: [  695.166877] ===> rtw_ips_pwr_down...................
Apr 13 06:21:09 markoh-HP kernel: [  695.167099] ====> rtw_ips_dev_unload...
Apr 13 06:21:09 markoh-HP kernel: [  695.190374] usb_read_port_cancel
Apr 13 06:21:09 markoh-HP kernel: [  695.190578] usb_read_port_complete()-1284: RX Warning! bDriverStopped(0) OR bSurpriseRemoved(0) bReadPortCancel(1)
Apr 13 06:21:09 markoh-HP kernel: [  695.190828] usb_read_port_complete()-1284: RX Warning! bDriverStopped(0) OR bSurpriseRemoved(0) bReadPortCancel(1)
Apr 13 06:21:09 markoh-HP kernel: [  695.191078] usb_read_port_complete()-1284: RX Warning! bDriverStopped(0) OR bSurpriseRemoved(0) bReadPortCancel(1)
Apr 13 06:21:09 markoh-HP kernel: [  695.191331] usb_read_port_complete()-1284: RX Warning! bDriverStopped(0) OR bSurpriseRemoved(0) bReadPortCancel(1)
Apr 13 06:21:09 markoh-HP kernel: [  695.191362] usb_write_port_cancel 
Apr 13 06:21:09 markoh-HP kernel: [  695.191372] ==> rtl8192cu_hal_deinit 
Apr 13 06:21:09 markoh-HP kernel: [  695.191373] bkeepfwalive(0)
Apr 13 06:21:09 markoh-HP kernel: [  695.191374] card disble without HWSM...........
Apr 13 06:21:09 markoh-HP kernel: [  695.196329] <=== rtw_ips_pwr_down..................... in 28ms
Apr 13 06:21:13 markoh-HP kernel: [  699.480172] _rtw_pwr_wakeup call ips_leave....
Apr 13 06:21:13 markoh-HP kernel: [  699.480175] ==>ips_leave cnts:22
Apr 13 06:21:13 markoh-HP kernel: [  699.480176] ===>  rtw_ips_pwr_up..............
Apr 13 06:21:13 markoh-HP kernel: [  699.480178] ===> ips_netdrv_open.........
Apr 13 06:21:13 markoh-HP kernel: [  699.485033]  ===> FirmwareDownload91C() fw:Rtl819XFwImageArray_TSMC
Apr 13 06:21:13 markoh-HP kernel: [  699.485035] FirmwareDownload92C accquire FW from embedded image
Apr 13 06:21:13 markoh-HP kernel: [  699.485036] fw_ver=v88, fw_subver=2, sig=0x88c0
Apr 13 06:21:13 markoh-HP kernel: [  699.510793] fw download ok!
Apr 13 06:21:13 markoh-HP kernel: [  699.510794] Set RF Chip ID to RF_6052 and RF type to 2.
Apr 13 06:21:13 markoh-HP kernel: [  699.889964] IQK:Start!!!
Apr 13 06:21:13 markoh-HP kernel: [  699.901718] Path A IQK Success!!
Apr 13 06:21:13 markoh-HP kernel: [  699.906470] Path B IQK Success!!
Apr 13 06:21:13 markoh-HP kernel: [  699.914974] Path A IQK Success!!
Apr 13 06:21:13 markoh-HP kernel: [  699.919726] Path B IQK Success!!
Apr 13 06:21:13 markoh-HP kernel: [  699.924478] IQK: final_candidate is 0
Apr 13 06:21:13 markoh-HP kernel: [  699.924479] IQK: RegE94=100 RegE9C=3fa RegEA4=fb RegEAC=3fe RegEB4=101 RegEBC=9 RegEC4=ff RegECC=0
Apr 13 06:21:13 markoh-HP kernel: [  699.924479]  Path A IQ Calibration Success !
Apr 13 06:21:13 markoh-HP kernel: [  699.926604] Path B IQ Calibration Success !
Apr 13 06:21:13 markoh-HP kernel: [  700.037281] pdmpriv->TxPowerTrackControl = 1
Apr 13 06:21:13 markoh-HP kernel: [  700.041908] rtl8192cu_hal_init in 564ms
Apr 13 06:21:13 markoh-HP kernel: [  700.054542] <===  rtw_ips_pwr_up.............. in 576ms
Apr 13 06:21:13 markoh-HP kernel: [  700.054662] ==> ips_leave.....LED(0x00028080)...
Apr 13 06:21:15 markoh-HP wpa_supplicant[1827]: wlan4: CTRL-EVENT-SSID-REENABLED id=0 ssid="intguest"
Apr 13 06:21:15 markoh-HP wpa_supplicant[1827]: wlan4: Trying to associate with b4:e9:b0:b3:80:e2 (SSID='intguest' freq=2437 MHz)
Apr 13 06:21:15 markoh-HP wpa_supplicant[1827]: wlan4: Association request to the driver failed
Apr 13 06:21:15 markoh-HP kernel: [  701.363759] survey done event(19) band:0 for wlan4
Apr 13 06:21:15 markoh-HP kernel: [  701.364099] wpa_set_auth_algs, AUTH_ALG_OPEN_SYSTEM
Apr 13 06:21:15 markoh-HP kernel: [  701.364102] set_mode = IW_MODE_INFRA
Apr 13 06:21:15 markoh-HP kernel: [  701.364110] 
Apr 13 06:21:15 markoh-HP kernel: [  701.364110]  wpa_ie(length:22):
Apr 13 06:21:15 markoh-HP kernel: [  701.364111] 0x30 0x14 0x01 0x00 0x00 0x0f 0xac 0x04 
Apr 13 06:21:15 markoh-HP kernel: [  701.364113] 0x01 0x00 0x00 0x0f 0xac 0x04 0x01 0x00 
Apr 13 06:21:15 markoh-HP kernel: [  701.364113] 0x00 0x0f 0xac 0x01 0x00 0x00 0x00 0x00 
Apr 13 06:21:15 markoh-HP kernel: [  701.364766] hw_var_set_opmode()-4234 mode = 2
Apr 13 06:21:15 markoh-HP kernel: [  701.365140] SetHwReg8192CU, 5130, RCR= 700060ca 
Apr 13 06:21:15 markoh-HP kernel: [  701.365171] =>rtw_wx_set_essid
Apr 13 06:21:15 markoh-HP kernel: [  701.365173] ssid=intguest, len=8
Apr 13 06:21:15 markoh-HP kernel: [  701.365175] Set SSID under fw_state=0x00000008
Apr 13 06:21:15 markoh-HP kernel: [  701.365179] [by_bssid:0][assoc_ssid:intguest][to_roaming:0] new candidate: intguest(b4:e9:b0:b3:80:e2, ch6) rssi:-62
Apr 13 06:21:15 markoh-HP kernel: [  701.365180] rtw_select_and_join_from_scanned_queue: candidate: intguest(b4:e9:b0:b3:80:e2, ch:6)
Apr 13 06:21:15 markoh-HP kernel: [  701.365185] <=rtw_wx_set_essid, ret 0
Apr 13 06:21:15 markoh-HP kernel: [  701.365189] Set BSSID under fw_state=0x00000088
Apr 13 06:21:15 markoh-HP kernel: [  701.365635] start_join_set_ch_bw: ch=6, bwmode=0, ch_offset=0
Apr 13 06:21:15 markoh-HP NetworkManager[1239]: <info> (wlan4): supplicant interface state: scanning -> associating
Apr 13 06:21:15 markoh-HP kernel: [  701.881951] rtw_ack_tx_polling timeout
Apr 13 06:21:16 markoh-HP kernel: [  702.498226] rtw_ack_tx_polling timeout
Apr 13 06:21:17 markoh-HP kernel: [  703.114546] rtw_ack_tx_polling timeout
Apr 13 06:21:17 markoh-HP kernel: [  703.730795] rtw_ack_tx_polling timeout
Apr 13 06:21:18 markoh-HP kernel: [  704.347073] rtw_ack_tx_polling timeout
Apr 13 06:21:18 markoh-HP kernel: [  704.347078] issue_deauth_ex(wlan4) to b4:e9:b0:b3:80:e2, ch:6, 5/5 in 2976 ms
Apr 13 06:21:18 markoh-HP kernel: [  704.548869] link to Cisco AP
Apr 13 06:21:18 markoh-HP kernel: [  704.847308] link_timer_hdl: auth timeout and try again
Apr 13 06:21:19 markoh-HP kernel: [  705.147441] link_timer_hdl: auth timeout and try again
Apr 13 06:21:19 markoh-HP kernel: [  705.447575] link_timer_hdl: auth timeout and try again
Apr 13 06:21:19 markoh-HP kernel: [  705.747763] link_timer_hdl: auth timeout and try again
Apr 13 06:21:19 markoh-HP kernel: [  706.047852] report_join_res(-1)
Apr 13 06:21:19 markoh-HP kernel: [  706.048921] HW_VAR_BASIC_RATE: BrateCfg(0x15d)
Apr 13 06:21:19 markoh-HP kernel: [  706.049513] =>mlmeext_joinbss_event_callback
Apr 13 06:21:19 markoh-HP kernel: [  706.051850] _rtw_join_timeout_handler, fw_state=8
Apr 13 06:21:19 markoh-HP kernel: [  706.051864] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
Apr 13 06:21:19 markoh-HP wpa_supplicant[1827]: wlan4: CTRL-EVENT-DISCONNECTED bssid=b4:e9:b0:b3:80:e2 reason=0
Apr 13 06:21:19 markoh-HP wpa_supplicant[1827]: wlan4: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="intguest" auth_failures=2 duration=20
Apr 13 06:21:19 markoh-HP NetworkManager[1239]: <info> (wlan4): supplicant interface state: associating -> disconnected
Apr 13 06:21:20 markoh-HP kernel: [  706.152206] IW_SCAN_THIS_ESSID, ssid=intguest, len=8
Apr 13 06:21:20 markoh-HP NetworkManager[1239]: <info> (wlan4): supplicant interface state: disconnected -> scanning
Apr 13 06:21:20 markoh-HP NetworkManager[1239]: <warn> Activation (wlan4/wireless): association took too long.
Apr 13 06:21:20 markoh-HP NetworkManager[1239]: <info> (wlan4): device state change: config -> failed (reason 'no-secrets') [50 120 7]
Apr 13 06:21:20 markoh-HP NetworkManager[1239]: <info> Marking connection 'intguest' invalid.
Apr 13 06:21:20 markoh-HP NetworkManager[1239]: <warn> Activation (wlan4) failed for connection 'intguest'
Apr 13 06:21:20 markoh-HP NetworkManager[1239]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Apr 13 06:21:20 markoh-HP NetworkManager[1239]: <info> (wlan4): device state change: failed -> disconnected (reason 'none') [120 30 0]
Apr 13 06:21:20 markoh-HP NetworkManager[1239]: <info> (wlan4): deactivating device (reason 'none') [0]
Apr 13 06:21:20 markoh-HP wpa_supplicant[1827]: wlan4: Reject scan trigger since one is already pending
Apr 13 06:21:20 markoh-HP NetworkManager[1239]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Apr 13 06:21:21 markoh-HP kernel: [  707.462531] survey done event(1f) band:0 for wlan4
Apr 13 06:21:21 markoh-HP NetworkManager[1239]: <info> (wlan4): supplicant interface state: scanning -> inactive
Apr 13 06:21:24 markoh-HP kernel: [  710.607961] survey done event(15) band:0 for wlan4
Apr 13 06:21:26 markoh-HP kernel: [  712.366757] ==>rtw_ps_processor .fw_state(8)
Apr 13 06:21:26 markoh-HP kernel: [  712.366760] ==>ips_enter cnts:23




``` 

Even when I do not try to connect to wifi with 8192cu dongle, the logs are repeatedly filled with lines from 8192cu driver. I noticed the lines with
"usb_read_port_complete()-1284: RX Warning! bDriverStopped(0) OR bSurpriseRemoved(0) bReadPortCancel(1)" among others.

If and when the 8192cu driver manages to connect to WIFI it still writes to the log all the time. At first it was like this:
```

Apr  9 07:44:08 markoh-HP kernel: [  434.748860] rtw_wx_get_rts, rts_thresh=2347
Apr  9 07:44:08 markoh-HP kernel: [  434.748866] rtw_wx_get_frag, frag_len=2346
Apr  9 07:44:11 markoh-HP kernel: [  436.890253] rtw_set_ps_mode(): Busy Traffic , Leave 802.11 power save..
Apr  9 07:44:11 markoh-HP kernel: [  436.890375] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
Apr  9 07:44:13 markoh-HP kernel: [  438.893291] rtw_set_ps_mode(): Enter 802.11 power save mode...
Apr  9 07:44:13 markoh-HP kernel: [  438.893297] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
Apr  9 07:44:15 markoh-HP kernel: [  440.896331] rtw_set_ps_mode(): Busy Traffic , Leave 802.11 power save..
Apr  9 07:44:15 markoh-HP kernel: [  440.896466] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0

```

Then I found the information about the power saving problem on [http://linux-sunxi.org/Wifi](http://linux-sunxi.org/Wifi). After that only three lines repeat in the logs:
```

Apr  9 07:52:29 markoh-HP kernel: [  934.955655] rtw_wx_get_rts, rts_thresh=2347
Apr  9 07:52:29 markoh-HP kernel: [  934.955658] rtw_wx_get_frag, frag_len=2346
Apr  9 07:52:30 markoh-HP kernel: [  935.880437] rtl8192c_sreset_xmit_status_check tx hang
Apr  9 07:52:32 markoh-HP kernel: [  937.884808] rtl8192c_sreset_xmit_status_check tx hang
Apr  9 07:52:34 markoh-HP kernel: [  939.889394] rtl8192c_sreset_xmit_status_check tx hang
Apr  9 07:52:36 markoh-HP kernel: [  941.893791] rtl8192c_sreset_xmit_status_check tx hang
Apr  9 07:52:38 markoh-HP kernel: [  943.898374] rtl8192c_sreset_xmit_status_check tx hang
Apr  9 07:52:39 markoh-HP kernel: [  944.961406] rtw_wx_get_rts, rts_thresh=2347
Apr  9 07:52:39 markoh-HP kernel: [  944.961410] rtw_wx_get_frag, frag_len=2346
Apr  9 07:52:40 markoh-HP kernel: [  945.902715] rtl8192c_sreset_xmit_status_check tx hang

```


The problem is that the line is still very unstable and practically unusable. I believe the "tx hang" reported in the logs has something to do with it.

I am out of ideas what to do. I tried different 8192cu fixed drivers. I may have made mistakes installing them but I have a feeling that with all of them I have the same or very similar problems. I don't want to buy new dongles any more until I find one with a decent reception and driver. Any ideas what should I do?

---

### Post by markohrastovec on 2015-04-14
After the latest kernel upgrade "Linux 3.16.0-34-generic #47-Ubuntu SMP Fri Apr 10 18:02:58 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux" the problems have gone away. So the solution is upgrade Ubuntu.

---

### Post by markohrastovec on 2016-01-29
The problem re-appeared and I was having a lot of problems with it. I think, I have finally found the solution. I had a low cost USB hub connected to the computer. I was testing the connection on another computer the problem was not observable there. So I started to look for differencies. Maybe it is to soon to tell but after I unplugged the USB hub, the connection works without problems. It will take some time to be sure, but so far so good.

---

