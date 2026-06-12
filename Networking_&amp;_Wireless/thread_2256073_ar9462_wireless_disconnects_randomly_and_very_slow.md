---
title: "ar9462 wireless disconnects randomly and very slow on Ubuntu 14.10"
date: 2014-12-09
forum: Networking &amp; Wireless
---

### Post by raggar on 2014-12-09
Hello, 

Recently I bought myself a Acer aspire v3-371 laptop. This laptop has a AR9462 wireless chip in it, but it cannot stay connected for a long time. Also the connection is very slow, about 70KByte/second. 
I have tried a few things off I found by searching the web and some forums:
/etc/modprobe.d/ath9k.conf ```


#options I tried these together and separetly 
 options ath9k btcoex_enable=1 bt_ant_diversity=1 ps_enable=0 nohwcrypt=1

#I tried to black list these and also without blacklisting
blacklist btusb acer_wmi

```
I have installed the newest ath9k kerneldrivers from backports v3.18-rc1-1-0-g1f4af51

I have tried with and without bluetooth. BTW bluetooth doesn't work either, it looks like it is working but it doesn't show any devices when it should see them

I have tried to make the connection without networkManager. In the terminal (iwconfig) it looks a bit more stable but still very slow. 
With and without IPv6, I turned it off (ignore) in the networkmanager. It looked like it helped a bit, but not much. 

Also in Ubuntu 14.04 I have had the same problems, I tested this from a live usb.

Below I attached the output of wireless-script, what I came across when looking for answers. I think all is in here. 

Hope someone can help me :) Thanks in advance :)

```



########## wireless info START ##########


Report from: 09 Dec 2014 20:26 CET +0100


Booted last: 09 Dec 2014 20:00 CET +0100


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic


##### kernel ############################


Linux 3.16.0-25-generic #33-Ubuntu SMP Tue Nov 4 12:06:54 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Acer Incorporated [ALI] Device [1025:0918]
    Kernel driver in use: r8169


02:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e07d]
    Kernel driver in use: ath9k


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 003: ID 064e:9400 Suyin Corp. 
Bus 002 Device 002: ID 0489:e076 Foxconn / Hon Hai 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
ath9k                  95797  0 
ath9k_common           25637  1 ath9k
ath9k_hw              433659  2 ath9k_common,ath9k
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
mac80211              578980  1 ath9k
cfg80211              508404  4 ath,ath9k_common,ath9k,mac80211
compat                 14427  5 cfg80211,ath9k_common,ath9k,mac80211,ath9k_hw
snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          200108  1 snd_soc_rt5640
snd_pcm               104102  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
wmi                    19193  1 acer_wmi
video                  20128  2 i915,acer_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


auto wlan0
iface wlan0 inet static
address 192.168.178.42
netmask 255.255.255.0
gateway 192.168.178.1


wpa-ssid Ahof131143
wpa-psk <WPA key removed>


dns-nameservers 8.8.8.8


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.178.42  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::3ab1:dbff:feab:a4f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9156 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8467 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8127402 (8.1 MB)  TX bytes:1583898 (1.5 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"Ahof131143"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: <MAC 'Ahof131143' [AC3]>   
          Bit Rate=18 Mb/s   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:68  Invalid misc:258   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.178.1   0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.178.0   0.0.0.0         255.255.255.0   U     0      0        0 wlan0


##### resolv.conf #######################


nameserver 8.8.8.8


##### nm-tool ###########################


** (process:3720): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: Launch helper exited with unknown return code 1


** (process:3720): WARNING **: error: could not connect to NetworkManager


NetworkManager Tool


State: unknown


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


[[/etc/NetworkManager/system-connections/Ahof131143]] (600 root)
[connection] id=Ahof131143 | type=802-11-wireless
[802-11-wireless] ssid=Ahof131143 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=dhcp


##### iw reg get ########################


Region: Europe/Amsterdam (based on set time zone)


country DE: DFS-UNSET
    (2400 - 2483 @ 40), (N/A, 20)
    (5150 - 5250 @ 40), (N/A, 20), NO-OUTDOOR
    (5250 - 5350 @ 40), (N/A, 20), NO-OUTDOOR, DFS
    (5470 - 5725 @ 40), (N/A, 26), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR


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
          Current Frequency:2.417 GHz (Channel 2)


##### iwlist scan #######################


Channel occupancy:


      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      2   APs on   Frequency:2.472 GHz (Channel 13)
      1   APs on   Frequency:5.24 GHz (Channel 48)


eth0      Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'aarde' [AC1]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"aarde"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000231a103ed55
                    Extra: Last beacon: 7264ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Ziggo32764' [AC2]>
                    Channel:48
                    Frequency:5.24 GHz (Channel 48)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Ziggo32764"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000b18bebe9c95
                    Extra: Last beacon: 4868ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Ahof131143' [AC3]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"Ahof131143"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000280a37cbf
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'VGV75192F93A2' [AC4]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"VGV75192F93A2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000010b89821143
                    Extra: Last beacon: 6112ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'KPN Fon' [AC5]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:off
                    ESSID:"KPN Fon"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000010b89821a4d
                    Extra: Last beacon: 6112ms ago


##### module infos ######################


[ath9k]
filename:       /lib/modules/3.16.0-25-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko
version:        backported from Linux (v3.18-rc1-0-gf114040) using backports v3.18-rc1-1-0-g1f4af51
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     5087232EF5DB5031F000AE9
depends:        ath9k_hw,mac80211,ath9k_common,compat,cfg80211,ath
vermagic:       3.16.0-25-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


[ath9k_common]
filename:       /lib/modules/3.16.0-25-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_common.ko
version:        backported from Linux (v3.18-rc1-0-gf114040) using backports v3.18-rc1-1-0-g1f4af51
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     046A6711D0FEE870889EDF1
depends:        compat,cfg80211,ath9k_hw,ath
vermagic:       3.16.0-25-generic SMP mod_unload modversions 


[ath9k_hw]
filename:       /lib/modules/3.16.0-25-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     F7F095B7F220D212248B0BD
depends:        compat,ath
vermagic:       3.16.0-25-generic SMP mod_unload modversions 


[ath]
filename:       /lib/modules/3.16.0-25-generic/updates/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     2CE92AF23062F0EC47012B9
depends:        cfg80211
vermagic:       3.16.0-25-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/3.16.0-25-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (v3.18-rc1-0-gf114040) using backports v3.18-rc1-1-0-g1f4af51
srcversion:     AF8CBE1C3D3AFE9970FDB54
depends:        cfg80211,compat
vermagic:       3.16.0-25-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.16.0-25-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (v3.18-rc1-0-gf114040) using backports v3.18-rc1-1-0-g1f4af51
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     2120A8BE31BF61934639425
depends:        compat
vermagic:       3.16.0-25-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath9k]
blink: 0
bt_ant_diversity: 1
btcoex_enable: 1
nohwcrypt: 0
ps_enable: 0


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


##### modprobe options ##################


[/etc/modprobe.d/ath9k.conf]
options ath9k options ath9k btcoex_enable=1 bt_ant_diversity=1 ps_enable=0
blacklist btusb


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


[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0034 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[ 1080.235939] wlan0: association with <MAC 'Ahof131143' [AC3]> timed out
[ 1084.026200] wlan0: authenticate with <MAC 'Ahof131143' [AC3]>
[ 1084.039782] wlan0: send auth to <MAC 'Ahof131143' [AC3]> (try 1/3)
[ 1084.144240] wlan0: send auth to <MAC 'Ahof131143' [AC3]> (try 2/3)
[ 1084.209424] wlan0: authenticated
[ 1084.209796] wlan0: associate with <MAC 'Ahof131143' [AC3]> (try 1/3)
[ 1084.339938] wlan0: associate with <MAC 'Ahof131143' [AC3]> (try 2/3)
[ 1084.391675] wlan0: associate with <MAC 'Ahof131143' [AC3]> (try 3/3)
[ 1084.416592] wlan0: association with <MAC 'Ahof131143' [AC3]> timed out
[ 1096.997495] wlan0: authenticate with <MAC 'Ahof131143' [AC3]>
[ 1097.011109] wlan0: send auth to <MAC 'Ahof131143' [AC3]> (try 1/3)
[ 1097.013993] wlan0: authenticated
[ 1097.017227] wlan0: associate with <MAC 'Ahof131143' [AC3]> (try 1/3)
[ 1097.084921] wlan0: RX AssocResp from <MAC 'Ahof131143' [AC3]> (capab=0x431 status=0 aid=7)
[ 1097.085004] wlan0: associated
[ 1097.100085] ath: EEPROM regdomain: 0x8114
[ 1097.100088] ath: EEPROM indicates we should expect a country code
[ 1097.100089] ath: doing EEPROM country->regdmn map search
[ 1097.100091] ath: country maps to regdmn code: 0x37
[ 1097.100092] ath: Country alpha2 being used: DE
[ 1097.100093] ath: Regpair used: 0x37
[ 1097.100095] ath: regdomain 0x8114 dynamically updated by country IE
[ 1101.099882] wlan0: disassociated from <MAC 'Ahof131143' [AC3]> (Reason: 2)
[ 1104.663079] wlan0: authenticate with <MAC 'Ahof131143' [AC3]>
[ 1104.676561] wlan0: send auth to <MAC 'Ahof131143' [AC3]> (try 1/3)
[ 1104.680012] wlan0: authenticated
[ 1104.682401] wlan0: associate with <MAC 'Ahof131143' [AC3]> (try 1/3)
[ 1104.687336] wlan0: RX AssocResp from <MAC 'Ahof131143' [AC3]> (capab=0x431 status=0 aid=7)
[ 1104.687413] wlan0: associated
[ 1104.702155] ath: EEPROM regdomain: 0x8114
[ 1104.702158] ath: EEPROM indicates we should expect a country code
[ 1104.702160] ath: doing EEPROM country->regdmn map search
[ 1104.702161] ath: country maps to regdmn code: 0x37
[ 1104.702162] ath: Country alpha2 being used: DE
[ 1104.702163] ath: Regpair used: 0x37
[ 1104.702165] ath: regdomain 0x8114 dynamically updated by country IE
[ 1114.967025] wlan0: authenticate with <MAC 'Ahof131143' [AC3]>
[ 1114.980603] wlan0: send auth to <MAC 'Ahof131143' [AC3]> (try 1/3)
[ 1115.082635] wlan0: send auth to <MAC 'Ahof131143' [AC3]> (try 2/3)
[ 1115.179036] wlan0: send auth to <MAC 'Ahof131143' [AC3]> (try 3/3)
[ 1115.294595] wlan0: authentication with <MAC 'Ahof131143' [AC3]> timed out
[ 1144.148706] wlan0: authenticate with <MAC 'Ahof131143' [AC3]>
[ 1144.162161] wlan0: send auth to <MAC 'Ahof131143' [AC3]> (try 1/3)
[ 1144.164965] wlan0: authenticated
[ 1144.168211] wlan0: associate with <MAC 'Ahof131143' [AC3]> (try 1/3)
[ 1144.173343] wlan0: RX AssocResp from <MAC 'Ahof131143' [AC3]> (capab=0x431 status=0 aid=7)
[ 1144.173409] wlan0: associated
[ 1144.187460] ath: EEPROM regdomain: 0x8114
[ 1144.187463] ath: EEPROM indicates we should expect a country code
[ 1144.187465] ath: doing EEPROM country->regdmn map search
[ 1144.187466] ath: country maps to regdmn code: 0x37
[ 1144.187467] ath: Country alpha2 being used: DE
[ 1144.187468] ath: Regpair used: 0x37
[ 1144.187470] ath: regdomain 0x8114 dynamically updated by country IE


########## wireless info END ############



```

---

### Post by raggar on 2014-12-11
I'm out off options... So I decided to openup the laptop and have a look at the wireless device itself. It is a Qualcomm Atheros QCNFA222. It has a different connection than I'm used to, it uses a M.2 connection to connect to the motherboard. Could this have anything to do with my problem? 
Will it help if I order a intel 7260NGW (has the same connector M.2) to get wireless on my laptop?

---

### Post by jeremy31 on 2014-12-11
From the wireless script info, all available access points are using TKIP encryption which can cause issues with Linux

---

### Post by raggar on 2014-12-11
Hi Jeremy31, thanks for your answer!

I have tried to change this to CCMP (aes) and now it cannot connect at all. It keeps asking the password for the wireless. Any ideas? :?

In /var/log/syslog I found this:

```

Dec 11 16:19:55 raggar NetworkManager[900]: <info> (wlan0): supplicant interface state: inactive -> authenticating
Dec 11 16:19:55 raggar kernel: [  418.704785] wlan0: send auth to 24:65:11:a7:cc:32 (try 1/3)
Dec 11 16:19:55 raggar kernel: [  418.829934] wlan0: send auth to 24:65:11:a7:cc:32 (try 2/3)
Dec 11 16:19:55 raggar kernel: [  418.933867] wlan0: send auth to 24:65:11:a7:cc:32 (try 3/3)
Dec 11 16:19:55 raggar kernel: [  419.037716] wlan0: authentication with 24:65:11:a7:cc:32 timed out
Dec 11 16:19:55 raggar NetworkManager[900]: <info> (wlan0): supplicant interface state: authenticating -> disconnected

```

---

### Post by jeremy31 on 2014-12-11
You might want to see if it is WPA2 and not just WPA on the router.  The connection might need to be deleted from network manager and put back in

---

### Post by raggar on 2014-12-11
Thanks, I've indeed deleted the connection from the networkmanager. And I especialy selected wpa2. Now it is on wpa&wpa2 again (TKIP and CCMP) and connecting does work for a few minutes.
Could it be something with the type of connector on de networkcard?

---

### Post by jeremy31 on 2014-12-11
Just noticed an error in the wireless info in your ath9k.conf```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
``````
sudo modprobe -r ath9k
``````
sudo modprobe ath9k
```
and see if it works better

---

### Post by raggar on 2014-12-11
Hi Jeremy31, thanks! But it was only on this forum. I made sure off it, I tested it a lot of times before posting here. ;) The options I tested were all recognized, because I checked for errors. 

I just tried it once again, just to be sure. But still no luck with this issue... 
I have the feeling that this has something to do with the new type of connector on the wireless card. Could that be???

---

### Post by jeremy31 on 2014-12-11
I don't know if the connector type matters, but I wondered if this was accepted in the ath9k.conf ```
options ath9k options ath9k btcoex_enable=1 bt_ant_diversity=1 ps_enable=0
```
I would think that might cause an issue if ath9k is modprobed.  I might have to look at the ath9k dev mailing list to see if there is anything there about your card

---

### Post by raggar on 2014-12-11
Thank you, if you would like to have a look in to this I would very much appreciate it! 
The double options in the /etc/modprobe.d/ath9k.conf is already been removed. I found this out just after posting here. I had made this change on ath9k.conf just before posting... Sorry about that, I really tested a lot of options in ath9k.conf ;)

Just to be sure, here is a new dump from the wireless-script: 
```



########## wireless info START ##########


Report from: 11 Dec 2014 20:53 CET +0100


Booted last: 11 Dec 2014 16:13 CET +0100


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.10
Release:	14.10
Codename:	utopic


##### kernel ############################


Linux 3.16.0-28-generic #37-Ubuntu SMP Mon Dec 8 17:15:28 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, ipv6.disable=1, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	Subsystem: Acer Incorporated [ALI] Device [1025:0918]
	Kernel driver in use: r8169


02:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e07d]
	Kernel driver in use: ath9k


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 003: ID 064e:9400 Suyin Corp. 
Bus 002 Device 002: ID 0489:e076 Foxconn / Hon Hai 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


2: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


ath9k                 136984  0 
ath9k_common           25638  1 ath9k
ath9k_hw              450664  2 ath9k_common,ath9k
ath                    29052  3 ath9k_common,ath9k,ath9k_hw
mac80211              660592  1 ath9k
cfg80211              510218  4 ath,ath9k_common,ath9k,mac80211
acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          200108  1 snd_soc_rt5640
snd_pcm               104102  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
wmi                    19193  1 acer_wmi
video                  20128  2 i915,acer_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.178.49  Bcast:192.168.178.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:67953 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58372 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:67729264 (67.7 MB)  TX bytes:10582692 (10.5 MB)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.178.1   0.0.0.0         UG    0      0        0 eth0
192.168.178.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1
search fritz.box


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    Ziggo32764:      Infra, <MAC 'Ziggo32764' [AC1]>, Freq 5240 MHz, Rate 54 Mb/s, Strength 30 WPA2
    aarde:           Infra, <MAC 'aarde' [AC2]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    Thomson9ED373:   Infra, <MAC 'Thomson9ED373' [AC4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    Wi-Fi-netwerk van Barend: Infra, <MAC 'Wi-Fi-netwerk van Barend' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 59 WPA2
    Ziggo32764:      Infra, <MAC 'Ziggo32764' [AN5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA2
    Ziggo:           Infra, <MAC 'Ziggo' [AN6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA2 Enterprise
    Ahof131143:      Infra, <MAC 'Ahof131143' [AN7]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.178.49
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.178.1


    DNS:             192.168.178.1


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


[[/etc/NetworkManager/system-connections/Ahof131143]] (600 root)
[connection] id=Ahof131143 | type=802-11-wireless
[802-11-wireless] ssid=Ahof131143 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Amsterdam (based on set time zone)


country 00: DFS-UNSET
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), NO-IR
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, NO-IR
	(5170 - 5250 @ 40), (3, 20), NO-IR
	(5735 - 5835 @ 40), (3, 20), NO-IR


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


##### iwlist scan #######################


Channel occupancy:


      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.24 GHz (Channel 48)


eth0      Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Ziggo32764' [AC1]>
                    Channel:48
                    Frequency:5.24 GHz (Channel 48)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Ziggo32764"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000b4175b0ac31
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'aarde' [AC2]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"aarde"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000025a57ee9ea3
                    Extra: Last beacon: 28ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Wi-Fi-netwerk van Barend' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Wi-Fi-netwerk van Barend"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; lo        Interface doesn't support scanning.


54 Mb/s
                    Mode:Master
                    Extra:tsf=00000b41e07dfc9b
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Thomson9ED373' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"Thomson9ED373"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c7a9e2e9b0
                    Extra: Last beacon: 28ms ago
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
filename:       /lib/modules/3.16.0-28-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     F1B005F210401E25BEA4125
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.16.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        43:ED:39:10:44:31:91:78:75:D2:7B:2C:77:81:33:BB:61:68:4E:D9
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)


[ath9k_common]
filename:       /lib/modules/3.16.0-28-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     50297023DA06CB0C907A2CA
depends:        cfg80211,ath9k_hw,ath
intree:         Y
vermagic:       3.16.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        43:ED:39:10:44:31:91:78:75:D2:7B:2C:77:81:33:BB:61:68:4E:D9
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/3.16.0-28-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     82ED87AB9ED63AE3894F105
depends:        ath
intree:         Y
vermagic:       3.16.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        43:ED:39:10:44:31:91:78:75:D2:7B:2C:77:81:33:BB:61:68:4E:D9
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/3.16.0-28-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     165C1DF76AF8C8B6A45DA4F
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        43:ED:39:10:44:31:91:78:75:D2:7B:2C:77:81:33:BB:61:68:4E:D9
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.16.0-28-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     BEA0C6DE6572AE84C25CD77
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        43:ED:39:10:44:31:91:78:75:D2:7B:2C:77:81:33:BB:61:68:4E:D9
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.16.0-28-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     DEE8EAA48495E392CD51C2D
depends:        
intree:         Y
vermagic:       3.16.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        43:ED:39:10:44:31:91:78:75:D2:7B:2C:77:81:33:BB:61:68:4E:D9
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 1
ps_enable: 0
use_chanctx: 0


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


[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0034 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[ 2721.691766] wlan0: authenticate with <MAC 'Ahof131143' [AN7]>
[ 2721.703032] wlan0: send auth to <MAC 'Ahof131143' [AN7]> (try 1/3)
[ 2721.731615] wlan0: authenticated
[ 2721.735046] wlan0: associate with <MAC 'Ahof131143' [AN7]> (try 1/3)
[ 2721.859064] wlan0: associate with <MAC 'Ahof131143' [AN7]> (try 2/3)
[ 2721.963026] wlan0: associate with <MAC 'Ahof131143' [AN7]> (try 3/3)
[ 2722.066923] wlan0: association with <MAC 'Ahof131143' [AN7]> timed out
[ 2868.630885] ath9k: ath9k: Driver unloaded
[ 2878.203398] ath: EEPROM regdomain: 0x6c
[ 2878.203401] ath: EEPROM indicates we should expect a direct regpair map
[ 2878.203403] ath: Country alpha2 being used: 00
[ 2878.203404] ath: Regpair used: 0x6c
[ 3286.747669] wlan0: authenticate with <MAC 'Ahof131143' [AN7]>
[ 3286.760173] wlan0: direct probe to <MAC 'Ahof131143' [AN7]> (try 1/3)
[ 3286.962162] wlan0: direct probe to <MAC 'Ahof131143' [AN7]> (try 2/3)
[ 3287.166058] wlan0: direct probe to <MAC 'Ahof131143' [AN7]> (try 3/3)
[ 3287.369991] wlan0: authentication with <MAC 'Ahof131143' [AN7]> timed out
[ 3713.574357] wlan0: authenticate with <MAC 'Ahof131143' [AN7]>
[ 3713.586847] wlan0: send auth to <MAC 'Ahof131143' [AN7]> (try 1/3)
[ 3714.307934] wlan0: send auth to <MAC 'Ahof131143' [AN7]> (try 2/3)
[ 3715.319561] wlan0: send auth to <MAC 'Ahof131143' [AN7]> (try 3/3)
[ 3715.587532] wlan0: authentication with <MAC 'Ahof131143' [AN7]> timed out


########## wireless info END ############

```

---

### Post by jeremy31 on 2014-12-11
In network manager for the wifi connection, try changing the IPv6 to ignore

---

### Post by raggar on 2014-12-12
This setting was at 'ignore' before but because I had to re-enter the networksetting into the networkmanager IPv6 went to default again. 

I tested it today and still no luck, it cannot connect at all... :s Also I tried to connect to other (public)networks today, I got connected to a few of them but was disconnected at random again. Also I didn't see a few networks that my phone did see. 

Just to be sure I ordered a new networkcard today, a intel Wireless ac 7260NGW. It has the right connector and I read a few good reviews about it working on Ubuntu. If you still have some good ideas about fixing this, I would like to try it! :) Also for testing and for other people having the same laptop / wifi card. 
And it doesn't feel good to me, ordering a new card because I cannot get it to work... :S I work about 7 years with various linux distro's and have never done this before... (maybe once in 7 years is not very bad and the costs are not that high, but still I like to win from my computer problems :D )

---

### Post by Domajno on 2015-01-20
Hi raggar, have you found any solution to your problem? I am experiencing exactly the same. I have Acer V3-371-50AG machine with same AR9462 wireless and haven't managed to find the solution so far.

---

### Post by raggar on 2015-01-21
Hi Domajno,

No, I still haven't fixed this. But I am a few steps further. I have bought a new wifi card, intel 7260NGW and I still experience the same troubles as before. So I decided to test things for myself. What I found out is that there are two antenna's inside the laptop but that the signal is being blocked by the hardware and some kind of copper paint on the innerside of the bottom. So if you play with the position of the laptop the signal is better... :s

I'm now going to buy another antenna and try to get a better signal. If it doesn't work. I will try a outside antenna for places with poor signal. Not the best solution. But at this moment the laptop is worthless to me if wifi doesn't work.
I will keep you posted on this tread about my experiences. Hope it helps you and others a bit.

---

### Post by Domajno on 2015-01-23
Thanks for the answer. Not a good news though.... It seems strange to me because I had no problems with the signal on Windows so I would say that it should be a software problem.

I will try to find an external USB wifi. I dunno which one I should choose now though.

---

### Post by raggar on 2015-01-30
Hi Domajno, 

I have not ordered the new wifi antenna because you said it did work on windows. I haven't tried windows so I'm not sure. If that is the case... I have no idea where to find the problem. I still have the feeling that this has something to do with the M.2 connection instead of mini-pcie. 

For a wifi dongle, you can just pick one very common I think. Most of them work. I have one from my raspberry pi (a very small one) and works fine.

//edit: fix a few spelling misstackies

---

### Post by raggar on 2015-02-01
Hi Domajno, 

I have upgrade to kernel version 3.18.4 and this greatly improves the networkstability. Although I have changed my networkcard to a intel 7260NGW. Maybe you can try this as well. 
I use this kernel: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.18.4-vivid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.18.4-vivid/)

Download the generic headers en image. And install with:
```

sudo dpkg -i linux-headers-3.18.4* linux-image-3.18.4*

```

Hope this helps you as well

---

### Post by raggar on 2015-03-30
Recently I did some work on the laptop. And I found out a few things to make this laptop work a lot better. 

If you have trouble with the touchpad, check out this link: [http://www.iq-tm.de/TP%20freeze.htm](http://www.iq-tm.de/TP%20freeze.htm)
It helped me a lot!

Also to make the wireless work a lot faster I used some sanding paper and a knive to remove some of the copperpaint on the bottom inside the laptop. If you open up the laptop you takeoff the bottom, there you find in the left corner two places without copperpaint. This is specialy done for the wifi signal, but it is very limited. What I did was take a lot of this paint off in the left corner and I took out the screw on the left side (right if you look from the bottom ;) ). 
No I have a wifi signal that is stronger and have speeds that fits my routersspeed. 

You have to do some work on it, but then it is a very nice laptop for a good price ;) But I will never ever buy an acer again!!! :s

---

