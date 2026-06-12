---
title: "Intel wifi card (mobile) disconnects after a while"
date: 2015-03-31
forum: Networking &amp; Wireless
---

### Post by ppas-facebook on 2015-03-31
Hey guys, looking for a bit of help here.

I just installed a fresh copy of Ubuntu 14.10 (after messing up my previous system), and I'm having a weird wifi issue. Basically, what happens is that I am able to use the wifi absolutely fine and as expected for about an half an hour to an hour (time varies and I haven't specifically timed it) at which point it stops working (ie, Chrome and other programs say 'not connected to the internet'), but the wifi icon still shows full strength. I can toggle the hardware switch on the side of my laptop, I can toggle the keyboard shortcut (fn+F2) and I can toggle the switch in Ubuntu's network settings but none of them have any effect. I have to reboot to regain wifi.

I have seen a few similar problems here, but none of their solutions seem to help me.
Here is the output from running the wireless script (with my wifi name replaced by "***" for obvious reasons!):

```
########## wireless info START ##########


Report from: 31 Mar 2015 10:46 BST +0100


Booted last: 31 Mar 2015 10:42 BST +0100


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic


##### kernel ############################


Linux 3.16.0-33-generic #44-Ubuntu SMP Thu Mar 12 12:19:35 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [Condor Peak] [8086:0083]
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1305]
    Kernel driver in use: iwlwifi


05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. U6V/U31J laptop [1043:16d5]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 174f:1718 Syntek 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no


##### lsmod #############################


asus_nb_wmi            21128  0 
asus_wmi               24094  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
mxm_wmi                13021  0 
iwldvm                236430  0 
mac80211              660592  1 iwldvm
iwlwifi               183038  1 iwldvm
cfg80211              510218  3 iwlwifi,mac80211,iwldvm
wmi                    19193  2 mxm_wmi,asus_wmi
video                  20128  2 i915,asus_wmi


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
          inet addr:192.168.0.14  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::8ea9:82ff:fea1:a7d2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4691 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3223 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2634727 (2.6 MB)  TX bytes:843987 (843.9 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"***"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC '***' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=14 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:8  Invalid misc:48   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


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


- Device: wlan0  [***] ------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
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
    VM143316-2G:     Infra, <MAC 'VM143316-2G' [AC6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    ***: Infra, <MAC '***' [AN2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    TALKTALK-0C7251: Infra, <MAC 'TALKTALK-0C7251' [AC7]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    BTWifi-X:        Infra, <MAC 'BTWifi-X' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2 Enterprise
    BTHub4-GX2S:     Infra, <MAC 'BTHub4-GX2S' [AN5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    BTHub3-ZCJW:     Infra, <MAC 'BTHub3-ZCJW' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    BTWifi-X:        Infra, <MAC 'BTWifi-X' [AN7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2 Enterprise
    ***: Infra, <MAC '***' [AN8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    BTWifi-with-FON: Infra, <MAC 'BTWifi-with-FON' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42
    BTWifi-with-FON: Infra, <MAC 'BTWifi-with-FON' [AN10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40
    BTWiFi-with-FON: Infra, <MAC 'BTWiFi-with-FON' [AN11]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27
    ****: Infra, <MAC '***' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 84 WPA WPA2
    BTHub3-SXTG:     Infra, <MAC 'BTHub3-SXTG' [AN13]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2


  IPv4 Settings:
    Address:         192.168.0.14
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             194.168.4.100
    DNS:             194.168.8.100


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


[[/etc/NetworkManager/system-connections/***]] (600 root)
[connection] id=*** | type=802-11-wireless
[802-11-wireless] ssid=*** | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/London (based on set time zone)


country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), NO-IR
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), NO-IR
    (5735 - 5835 @ 40), (3, 20), NO-IR


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


      4   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.457 GHz (Channel 10)


eth0      Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC '***' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"***"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000019636ff5fa2
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'BTHub3-ZCJW' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-ZCJW"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000749138c87
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'BTWifi-with-FON' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000749139cc3
                    Extra: Last beacon: 80ms ago
          Cell 04 - Address: <MAC 'BTWifi-X' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000074912de17
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 05 - Address: <MAC 'BTWiFi' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006d1a378e38
                    Extra: Last beacon: 1116ms ago
          Cell 06 - Address: <MAC 'VM143316-2G' [AC6]>
                    Channlo        Interface doesn't support scanning.


el:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"VM143316-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000980d781f779
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'TALKTALK-0C7251' [AC7]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"TALKTALK-0C7251"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000003464e5a1
                    Extra: Last beacon: 80ms ago


##### module infos ######################


[iwldvm]
filename:       /lib/modules/3.16.0-33-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     716426034C9E4259C23DEDA
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        27:43:73:00:F8:EE:18:3C:88:11:43:4F:EB:7F:D9:5F:C6:87:82:EC
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.16.0-33-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     5410C94462FA26A0A3F256C
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        27:43:73:00:F8:EE:18:3C:88:11:43:4F:EB:7F:D9:5F:C6:87:82:EC
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.16.0-33-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
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
firmware:       iwlwifi-7265-9.ucode
firmware:       iwlwifi-3160-9.ucode
firmware:       iwlwifi-7260-9.ucode
firmware:       iwlwifi-8000-8.ucode
srcversion:     7F17406EFFE91762CB15EEE
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        27:43:73:00:F8:EE:18:3C:88:11:43:4F:EB:7F:D9:5F:C6:87:82:EC
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)


[cfg80211]
filename:       /lib/modules/3.16.0-33-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     4A525D9D32B0C6D120CA547
depends:        
intree:         Y
vermagic:       3.16.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        27:43:73:00:F8:EE:18:3C:88:11:43:4F:EB:7F:D9:5F:C6:87:82:EC
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


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
fw_monitor: N
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y
wd_disable: 1


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
# PCI device 0x8086:0x0083 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[    4.016143] iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled
[    4.027197] iwlwifi 0000:03:00.0: Radio type=0x0-0x0-0x3
[    4.063435] iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled
[    4.070867] iwlwifi 0000:03:00.0: Radio type=0x0-0x0-0x3
[    4.103118] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    5.236731] wlan0: authenticate with <MAC '***' [AC1]>
[    5.249479] wlan0: send auth to <MAC '***' [AC1]> (try 1/3)
[    5.256081] wlan0: authenticated
[    5.256230] wlan0: waiting for beacon from <MAC '***' [AC1]>
[    5.302546] wlan0: associate with <MAC '***' [AC1]> (try 1/3)
[    5.308155] wlan0: RX AssocResp from <MAC '***' [AC1]> (capab=0x411 status=0 aid=8)
[    5.311544] wlan0: associated
[    5.311573] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[    5.402917] wlan0: deauthenticating from <MAC '***' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[    5.405605] wlan0: authenticate with <MAC '***' [AC1]>
[    5.409276] wlan0: send auth to <MAC '***' [AC1]> (try 1/3)
[    5.413367] wlan0: authenticated
[    5.414488] wlan0: associate with <MAC '***' [AC1]> (try 1/3)
[    5.418054] wlan0: RX AssocResp from <MAC '***' [AC1]> (capab=0x411 status=0 aid=8)
[    5.420353] wlan0: associated


########## wireless info END ############



```

I seem to remember noticing this issue once or twice before reinstalling, but I always used my laptop plugged into ethernet previously (with wifi disabled via hardware switch), so I didn't really worry.
This issue may be related to slow-downs (symptoms being very laggy trackpad input) and lock-ups that I have been experiencing, usually just as the wifi starts acting up.
Also, if I switch to ctrl-alt-F1, I see a scrolling string of error messages about the wifi card, whether I am logged in to the terminal or not.

---

### Post by chili555 on 2015-03-31
> Also, if I switch to ctrl-alt-F1, I see a scrolling string of error messages about the wifi card,Seeing the exact message would be most helpful. Is it in dmesg?```
dmesg | grep -e wlan -e iwl | tail -n20
```...ideally run right after a dropout.

I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

Then please report back your findings; is the performance better, worse or the same?

---

### Post by ppas-facebook on 2015-04-01
Thanks for the detailed reply!

Fortunately, this has not happened again (yet), despite happening three or four times the other morning. It's one of those annoying glitches where it's not easily reproducible, so you never know if it is fixed or if it is just gone into hiding.

However, if it happens again, I will do what you say in these instructions and let you know the results! Thanks again for taking the time to reply, I really appreciate it!

---

### Post by ppas-facebook on 2015-04-02
Ok, @chili555, I had another failure last night, so I'm trying out some of the solutions here, but I have a few questions:
Do I have to do all of the things above in that order? Because I can easily switch off IPv6 any time but the other things require me to be properly sitting down and concentrating...

My router has "WPS auto" by default. What exactly will be changed if I change it to WPA2-PSK[AES] (the closest available option to what you suggested)? The thing is, this is a family router, so my dad's phone, PC, tablet, my brothers phone and PC, my mum's PC, my sister's phone and PC, my phone and tablet etc all still need to be able to connect without significant issues. (Same question applies to the other router tweaks)
Next, would I have to apply the same tweaks to the router at my house at university? Likewise, I would not want to stop any of my housemates from connecting...(this one's not such a big issue as I usually use a powerline ethernet kit).
Finally, would I have to apply this to *every* router I wanted to connect to? Obviously I can't change the settings of the free wifi routers at my university!

---

### Post by chili555 on 2015-04-02
> My router has "WPS auto" by default. Surely not! WPS is very, very insecure: [https://en.wikipedia.org/wiki/Wi-Fi_Protected_Setup](https://en.wikipedia.org/wiki/Wi-Fi_Protected_Setup)> In December 2011, researcher Stefan Viehböck reported a design and implementation flaw that makes brute-force attacks against PIN-based WPS feasible to be performed on WPS-enabled Wi-Fi networks. A successful attack on WPS allows unauthorized parties to gain access to the network, and the only effective workaround is to disable WPS.WPA2-AES, on the other hand, is quite secure. [https://en.wikipedia.org/wiki/Advanced_Encryption_Standard](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard)> As for now, there are no known practical attacks that would allow anyone to read correctly implemented AES encrypted data.I recommend that you disable WPS immediately and adopt WPA2-AES.> The thing is, this is a family router, so my dad's phone, PC, tablet, my brothers phone and PC, my mum's PC, my sister's phone and PC, my phone and tablet etc all still need to be able to connect without significant issues. (Same question applies to the other router tweaks)Unless the devices are quite old, they will be able to connect to WPA2-AES easily. They will simply be challenged for a password, supply it and connect. 

[ATTACH=CONFIG]261054[/ATTACH]Please be sure the password is not guess-able; that is, not your last name, address, cat's name, etc.

Obviously, you can't change the router settings at the Uni. I'd change evrything you can on your computer and, as well, for severe security risk reasons, change the router encryption to WPA2-AES immediately.

If the original problem persists, report back and we'll proceed from there.

---

### Post by ppas-facebook on 2015-04-02
Whoops. Stupid typo on my part! "WPS auto" should have been "WPA auto"! (A and S being right next to each other on the keyboard...) Either way I can still change it...

---

### Post by ppas-facebook on 2015-04-02
Ok. Router stuff changed. I'll wait for the next dropout (if dropout there be) and post the error messages etc.

---

### Post by chili555 on 2015-04-02
>  "WPA auto"Whew! You had me scared there for a bit.

I am beginning to suspect that the 'auto' part is a problem. When the router decides, for whatever reason, that it needs to switch from WPA to WPA2 on the fly, the Intel driver can't or won't keep up. I suspect the same is true for auto channel selection; hence my recommendation for a fixed channel.

---

### Post by ppas-facebook on 2015-04-02
Thanks for the explanation! I'll let you know how I get on!

If it's to do with the router switching, that might explain why it doesn't seem to occur frequently or with any respect to the time since my computer has been turned on. I suppose it would also explain why only rebooting fixes it, as that re-loads the driver...

It would be interesting to know what 'stimulus' would cause the router to 'decide' to switch, as well. Maybe something to do with the number/type of devices attached? Amount of network traffic? I have no idea, as network stuff isn't really my area! (Well, none of this is really my 'area' - it's all very much a hobby...)

---

### Post by ppas-facebook on 2015-04-09
Well, it's been about a week since I changed the router settings and no further issues, so I'd tentatively call that a solution. Thanks very much for your help, chilli555!

---

