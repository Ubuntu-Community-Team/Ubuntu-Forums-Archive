---
title: "Wifi connected on Ubuntu but not working (mostly)"
date: 2014-10-31
forum: Networking &amp; Wireless
---

### Post by snowflake2 on 2014-10-31
[COLOR=#000000] I have a Win8 and Ubuntu [/COLOR]14.04.1 LTS dualboot, I'm a total Ubuntu newbie . I have no problems with wifi on win8 but Ubuntu connects to the wifi network I have at home the connection runs for a second or two and then no or almost no speed. I dont have this problem on other wifi networks. Hopefully this is the right place for this post, if not I'm sorry and will move it accordingly :-). Posting the results from the wireless script.

Thanks a lot
[COLOR=#000000] 
[/COLOR][B]```


[/B]########## wireless info START ########## 
Report from: 30 Oct 2014 18:35 CET +0100


Booted last: 30 Oct 2014 17:53 CET +0100


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


08:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0888] (rev c4)
	Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN [8086:4262]
	Kernel driver in use: iwlwifi


09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Lenovo Device [17aa:3802]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 8087:07da Intel Corp. 
Bus 001 Device 003: ID 5986:0295 Acer, Inc 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: ideapad_3g: Wireless WAN
	Soft blocked: yes
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
4: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


iwldvm                232285  0 
mac80211              630653  1 iwldvm
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
mxm_wmi                13021  1 nouveau
ideapad_laptop         18216  0 
sparse_keymap          13948  1 ideapad_laptop
wmi                    19177  2 mxm_wmi,nouveau


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
          inet addr:10.0.0.32  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: 2a00:1028:8398:6426:2049:96fc:6393:60c7/64 Scope:Global
          inet6 addr: fe80::6a17:29ff:fe2d:9ec/64 Scope:Link
          inet6 addr: 2a00:1028:8398:6426:6a17:29ff:fe2d:9ec/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13505 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17799 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11117356 (11.1 MB)  TX bytes:2599273 (2.5 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"Internet_F2"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: <MAC 'Internet_F2' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:75  Invalid misc:391   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.138      0.0.0.0         UG    0      0        0 wlan0
10.0.0.0        0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search Home


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


- Device: wlan0  [Internet_F2] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           1 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Krausovaheslo100kc: Infra, <MAC 'Krausovaheslo100kc' [AC7]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 85 WPA
    matas:           Infra, <MAC 'matas' [AC8]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 67 WPA
    hotspot.kostnet.cz: Infra, <MAC 'hotspot.kostnet.cz' [AC3]>, Freq 2422 MHz, Rate 11 Mb/s, Strength 54 WPA
    cejkyn01b.kostnet.cz: Infra, <MAC 'cejkyn01b.kostnet.cz' [AC2]>, Freq 2412 MHz, Rate 11 Mb/s, Strength 44 WPA2
    urban:           Infra, <MAC 'urban' [AN5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA
    husq10-01b.kostnet.cz: Infra, <MAC 'husq10-01b.kostnet.cz' [AN6]>, Freq 2422 MHz, Rate 11 Mb/s, Strength 50 WEP
    M0001V2.hqhk.net:Infra, <MAC 'M0001V2.hqhk.net' [AN7]>, Freq 2432 MHz, Rate 11 Mb/s, Strength 35 WPA2
    www.PCHOSPITAL.cz: Infra, <MAC 'www.PCHOSPITAL.cz' [AC5]>, Freq 2432 MHz, Rate 11 Mb/s, Strength 37
    www.UNISYX.cz:   Infra, <MAC 'www.UNISYX.cz' [AC4]>, Freq 2432 MHz, Rate 11 Mb/s, Strength 37
    hotspot.kostnet.cz: Infra, <MAC 'hotspot.kostnet.cz' [AN10]>, Freq 2467 MHz, Rate 11 Mb/s, Strength 25 WPA
    pavel:           Infra, <MAC 'pavel' [AN11]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA
    DP380:           Infra, <MAC 'DP380' [AN12]>, Freq 2427 MHz, Rate 11 Mb/s, Strength 25 WPA2
    martan10-01b.kostnet.cz: Infra, <MAC 'martan10-01b.kostnet.cz' [AN13]>, Freq 2467 MHz, Rate 11 Mb/s, Strength 25 WEP
    *Internet_F2:    Infra, <MAC 'Internet_F2' [AC1]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 69 WPA2
    tera:            Infra, <MAC 'tera' [AN15]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA


  IPv4 Settings:
    Address:         10.0.0.32
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.138


    DNS:             10.0.0.138


  IPv6 Settings:
    Address:         2a00:1028:8398:6426:2049:96fc:6393:60c7
    Prefix:          64
    Gateway:         fe80::1


    Address:         2a00:1028:8398:6426:6a17:29ff:fe2d:9ec
    Prefix:          64
    Gateway:         fe80::1


    Address:         fe80::6a17:29ff:fe2d:9ec
    Prefix:          64
    Gateway:         fe80::1


    DNS:             fe80::1


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


no-auto-default=<MAC 'eth0' [IF]>,


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Internet_F2]] (600 root)
[connection] id=Internet_F2 | type=802-11-wireless | permissions=user:roland:;
[802-11-wireless] ssid=Internet_F2 | bssid=<MAC 'Internet_F2' [AC1]> | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/CTU-FA-Students]] (600 root)
[connection] id=CTU-FA-Students | type=802-11-wireless
[802-11-wireless] ssid=CTU-FA-Students | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/josh]] (600 root)
[connection] id=josh | type=802-11-wireless
[802-11-wireless] ssid=josh | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[ipv6] method=auto
[connection] id=eduroam | type=802-11-wireless
[802-11-wireless] ssid=eduroam | mac-address=<MAC 'wlan0' [IF]>
[802-1x] system-ca-certs=true
[ipv4] method=auto


##### iw reg get ########################


Region: Europe/Prague (based on set time zone)


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
          Current Frequency:2.452 GHz (Channel 9)


##### iwlist scan #######################


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      2   APs on   Frequency:2.432 GHz (Channel 5)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      1   APs on   Frequency:2.472 GHz (Channel 13)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Internet_F2' [AC1]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"Internet_F2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001ced467fe3c
                    Extra: Last beacon: 353648ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'cejkyn01b.kostnet.cz' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"cejkyn01b.kostnet.cz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=000001d8307fcc6e
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'hotspot.kostnet.cz' [AC3]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"hotspot.kostnet.cz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=000001d82f029ceb
                    Extra: Last beacon: 2424ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'www.UNISYX.cz' [AC4]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:off
                    ESSID:"www.UNISYX.cz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=00000194f5673af4
                    Extra: Last beacon: 2400ms ago
          Cell 05 - Address: <MAC 'www.PCHOSPITAL.cz' [AC5]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"www.PCHOSPITAL.cz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=00000194f5673f64
                    Extra: Last beacon: 2400ms ago
          Cell 06 - Address: <MAC 'Internet_F2' [AC1]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"Internet_F2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001cee96206f1
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'Krausovaheslo100kc' [AC7]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"Krausovaheslo100kc"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001d831bebb76
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'matas' [AC8]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"matas"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000119036f5c8a
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[iwldvm]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     CC4D1BA11C1EF73A6ABDE53
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     C2D0F3DFCA289585C100E36
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
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
filename:       /lib/modules/3.13.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
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
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x0888 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[ 1677.194043] wlan0: authenticate with <MAC 'Internet_F2' [AC1]>
[ 1677.202730] wlan0: send auth to <MAC 'Internet_F2' [AC1]> (try 1/3)
[ 1677.205556] wlan0: authenticated
[ 1677.206306] wlan0: associate with <MAC 'Internet_F2' [AC1]> (try 1/3)
[ 1677.211384] wlan0: RX AssocResp from <MAC 'Internet_F2' [AC1]> (capab=0x411 status=0 aid=1)
[ 1677.214544] wlan0: associated
[ 1743.093506] wlan0: deauthenticating from <MAC 'Internet_F2' [AC1]> by local choice (reason=3)
[ 1743.668982] wlan0: authenticate with <MAC 'Internet_F2' [AC1]>
[ 1743.676461] wlan0: send auth to <MAC 'Internet_F2' [AC1]> (try 1/3)
[ 1743.679179] wlan0: authenticated
[ 1743.682972] wlan0: associate with <MAC 'Internet_F2' [AC1]> (try 1/3)
[ 1743.686559] wlan0: RX AssocResp from <MAC 'Internet_F2' [AC1]> (capab=0x411 status=0 aid=1)
[ 1743.688737] wlan0: associated
[ 1759.122069] wlan0: deauthenticating from <MAC 'Internet_F2' [AC1]> by local choice (reason=3)
[ 1759.725834] wlan0: authenticate with <MAC 'Internet_F2' [AC1]>
[ 1759.733130] wlan0: send auth to <MAC 'Internet_F2' [AC1]> (try 1/3)
[ 1759.735951] wlan0: authenticated
[ 1759.740286] wlan0: associate with <MAC 'Internet_F2' [AC1]> (try 1/3)
[ 1759.743945] wlan0: RX AssocResp from <MAC 'Internet_F2' [AC1]> (capab=0x411 status=0 aid=1)
[ 1759.746733] wlan0: associated
[ 1797.769060] wlan0: deauthenticating from <MAC 'Internet_F2' [AC1]> by local choice (reason=3)
[ 1798.383350] wlan0: authenticate with <MAC 'Internet_F2' [AC1]>
[ 1798.391836] wlan0: send auth to <MAC 'Internet_F2' [AC1]> (try 1/3)
[ 1798.396259] wlan0: authenticated
[ 1798.398242] wlan0: associate with <MAC 'Internet_F2' [AC1]> (try 1/3)
[ 1798.402123] wlan0: RX AssocResp from <MAC 'Internet_F2' [AC1]> (capab=0x411 status=0 aid=1)
[ 1798.404851] wlan0: associated
[ 1862.476161] wlan0: deauthenticating from <MAC 'Internet_F2' [AC1]> by local choice (reason=3)
[ 1863.016883] wlan0: authenticate with <MAC 'Internet_F2' [AC1]>
[ 1863.024455] wlan0: send auth to <MAC 'Internet_F2' [AC1]> (try 1/3)
[ 1863.029623] wlan0: authenticated
[ 1863.030727] wlan0: associate with <MAC 'Internet_F2' [AC1]> (try 1/3)
[ 1863.034330] wlan0: RX AssocResp from <MAC 'Internet_F2' [AC1]> (capab=0x411 status=0 aid=1)
[ 1863.036805] wlan0: associated
[ 2140.530496] wlan0: deauthenticating from <MAC 'Internet_F2' [AC1]> by local choice (reason=3)
[ 2141.294217] wlan0: authenticate with <MAC 'Internet_F2' [AC1]>
[ 2141.301187] wlan0: send auth to <MAC 'Internet_F2' [AC1]> (try 1/3)
[ 2141.322002] wlan0: send auth to <MAC 'Internet_F2' [AC1]> (try 2/3)
[ 2141.343116] wlan0: send auth to <MAC 'Internet_F2' [AC1]> (try 3/3)
[ 2141.364855] wlan0: authentication with <MAC 'Internet_F2' [AC1]> timed out
[ 2141.907359] wlan0: authenticate with <MAC 'Internet_F2' [AC1]>
[ 2141.911229] wlan0: send auth to <MAC 'Internet_F2' [AC1]> (try 1/3)
[ 2141.931561] wlan0: send auth to <MAC 'Internet_F2' [AC1]> (try 2/3)
[ 2141.953592] wlan0: send auth to <MAC 'Internet_F2' [AC1]> (try 3/3)
[ 2141.979949] wlan0: authentication with <MAC 'Internet_F2' [AC1]> timed out
[ 2143.034911] wlan0: authenticate with <MAC 'Internet_F2' [AC1]>
[ 2143.045011] wlan0: send auth to <MAC 'Internet_F2' [AC1]> (try 1/3)
[ 2143.152097] wlan0: send auth to <MAC 'Internet_F2' [AC1]> (try 2/3)
[ 2143.255993] wlan0: send auth to <MAC 'Internet_F2' [AC1]> (try 3/3)
[ 2143.359871] wlan0: authentication with <MAC 'Internet_F2' [AC1]> timed out
[ 2144.872374] wlan0: authenticate with <MAC 'Internet_F2' [AC1]>
[ 2144.875413] wlan0: send auth to <MAC 'Internet_F2' [AC1]> (try 1/3)
[ 2144.887589] wlan0: authenticated
[ 2144.887924] wlan0: waiting for beacon from <MAC 'Internet_F2' [AC1]>
[ 2144.985689] wlan0: associate with <MAC 'Internet_F2' [AC1]> (try 1/3)
[ 2144.989338] wlan0: RX AssocResp from <MAC 'Internet_F2' [AC1]> (capab=0x411 status=0 aid=1)
[ 2145.002194] wlan0: associated


########## wireless info END ############
  **
```**

---

### Post by chili555 on 2014-10-31
I suggest you try a driver parameter: ```
sudo -i
echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Reboot and tell us if performance is improved.

There are a couple of other things we might try if not.

---

### Post by snowflake2 on 2014-10-31
It's working now, thank you very much for the help!

---

### Post by snowflake2 on 2014-11-01
Hi, my reaction seemed to be a bit premature, sorry, yesterday it was working all evening but towards the late night it again stopped working, this morning it also wasnt working and again now I am using ubuntu and am connected to the internet via the wifi.

---

### Post by chili555 on 2014-11-01
Let's take one thing at a time. The apt-get issue is a pretty easy fix but it's a bit over my experience level. They keep me chained up down here in the dungeon (Networking & Wireless) and don't let me play with things that might get me hurt! I suggest you post over on General Help [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331) I'm sure they'll get you fixed up easily.

As for the wireless, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

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

Reboot and tell us if performance is improved.

---

### Post by jeremy31 on 2014-11-01
This might have something to do with the issue ```
[COLOR=#000000][FONT=Ubuntu Mono]Power Management:on[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]

I need to go back and look at Chili555's posts because he likes to sneak things in and make me think I am going blind ;)

The cure might be ```
sudo iwconfig wlan0 power off
``` to disable power management

It is possible that Chili had something else in mind, he is very good at wireless issues[/FONT][/COLOR]

---

### Post by snowflake2 on 2014-11-02
I couldn't find the WPA2-AES option in the settings also to be honest dont know how to set the channel width, but I set the regulatory domain and set IPv6 to ignore. 

Also tried what Jeremy suggested. That seemed to do the trick. 

Will keep this thread open for another day or so to find if it is again only a temporary respite from the issues or if its permanent.

Thanks a lot for now guys!

---

### Post by Bucky Ball on 2014-11-02
Have deleted the update issue from post #4 to save space and avoid confusion as you have, quite rightly, posted a new thread regarding it. Good luck with both. ;)

---

### Post by snowflake2 on 2014-11-03
so... again I come home start up my laptop and no internet connection on Ubuntu, so could you please tell me how to set the  WPA2-AES on the router and the channel width stuff, sorry for being a bit slow :-)

---

### Post by chili555 on 2014-11-03
> **snowflake2 said:**
> so... again I come home start up my laptop and no internet connection on Ubuntu, so could you please tell me how to set the  WPA2-AES on the router and the channel width stuff, sorry for being a bit slow :-)Log in to the administration pages of the router using the IP address of the router in the address bar of your browser. [http://vanilla.co.za/images/dslhelp/linksys/WAG120N/address.gif](http://vanilla.co.za/images/dslhelp/linksys/WAG120N/address.gif) Your router address may or may not be 192.168.1.1.

Once in, look for wireless settings. If there is a setting for Channel Width in the 2.4 GHz band, set it for 20 MHz only, not mixed 20/40 MHz. [http://www8.pcmag.com/media/images/349131-channel-width.jpg?thumb=y](http://www8.pcmag.com/media/images/349131-channel-width.jpg?thumb=y)

Look for Wireless Security and change to WPA2-AES. [http://www.dd-wrt.com/phpBB2/files/wpa2aes_174.jpg](http://www.dd-wrt.com/phpBB2/files/wpa2aes_174.jpg)

Likewise, set a specific channel, ideally 1, 6 or 11 rather than Auto. [http://www.eightforums.com/attachments/general-support/14286d1357480011-irritating-windows-8-wifi-new-problem-urgent-help-need-image14.png](http://www.eightforums.com/attachments/general-support/14286d1357480011-irritating-windows-8-wifi-new-problem-urgent-help-need-image14.png)

Save all changes. Then reboot the router. You can do so with the time-honored method; unplug it, count to ten and plug it back in.

I suspect that when our routers are dancing all around with their 'Auto' and 'Mixed' settings, some Linux drivers have just a bit of trouble hitting a moving target.

I have had quite a few reports that these changes help completely and some that say it makes no difference. It is worthwhile to at least try.

---

### Post by snowflake2 on 2014-11-04
so my IP address is 10.0.0.32, is that weird? it looks weird,anyhow cant connect to it when I type in the address bar.

---

### Post by chili555 on 2014-11-04
It doesn't look weird to me. It is consistent with several numbering schemes used in routers. Trying to connect to that exact address is trying to connect to yourself. What you want is the router itself. Please open a terminal and do:```
route -n
```Look for the Gateway address; it might be 10.0.0.1. That is the address you want to try to get to the administration pages of the router.

---

### Post by snowflake2 on 2014-11-05
so the channel width is set, so is the fixed channel but when I want to choose WPA2 and AES it wants a Radius server ip. Which I don´t have a clue what to set to?

---

### Post by chili555 on 2014-11-05
Are you selecting WPA2-*Personal* and not Enterprise? You want WPA2-Personal. Please see attached.

---

### Post by snowflake2 on 2014-11-06
I only have these choices. Attaching scrshot

---

### Post by chili555 on 2014-11-06
> **snowflake2 said:**
> I only have these choices. Attaching scrshotI recommend you select WPA2-PSK. You already have AES selected. Save, close and reboot the router.

---

### Post by snowflake2 on 2014-11-09
Set and rebooted but unfortunately the issue still persists.

---

### Post by jeremy31 on 2014-11-09
Any MAC address(or other) filtering set up on the router?  And you might want to install updates as the 3.13.0-39 kernel is out and may have the fix

---

### Post by chili555 on 2014-11-10
May we see:```
dmesg | grep iwl
```Thanks.

---

### Post by snowflake2 on 2014-11-10
```

dmesg | grep iwl
[    9.913637] iwlwifi 0000:08:00.0: can't disable ASPM; OS doesn't have ASPM control
[    9.913769] iwlwifi 0000:08:00.0: irq 47 for MSI/MSI-X
[   10.420898] iwlwifi 0000:08:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[   11.189028] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   11.189028] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   11.189029] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   11.189030] iwlwifi 0000:08:00.0: Detected Intel(R) Centrino(R) Wireless-N 2230 BGN, REV=0xC8
[   11.189134] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[   11.377516] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   21.257522] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[   21.265080] iwlwifi 0000:08:00.0: Radio type=0x2-0x0-0x0
[   21.508851] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[   21.516451] iwlwifi 0000:08:00.0: Radio type=0x2-0x0-0x0


```

---

### Post by snowflake2 on 2014-11-10
and Mac filtering is not enabled

---

### Post by praseodym on 2014-11-10
Please run the wireless script again and paste the outputs. What kind of computer is it (brand, model)?

---

### Post by snowflake2 on 2014-11-10
Hi, it's a Lenovo S500

```



########## wireless info START ##########

Report from: 10 Nov 2014 19:38 CET +0100

Booted last: 10 Nov 2014 17:59 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

08:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0888] (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN [8086:4262]
    Kernel driver in use: iwlwifi

09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Lenovo Device [17aa:3802]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 8087:07da Intel Corp. 
Bus 001 Device 003: ID 5986:0295 Acer, Inc 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: ideapad_3g: Wireless WAN
    Soft blocked: yes
    Hard blocked: no
4: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwldvm                232285  0 
mac80211              630653  1 iwldvm
mxm_wmi                13021  1 nouveau
iwlwifi               169932  1 iwldvm
ideapad_laptop         18216  0 
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
sparse_keymap          13948  1 ideapad_laptop
wmi                    19177  2 mxm_wmi,nouveau

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
          inet addr:10.0.0.32  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: 2a00:1028:8398:6426:80d1:5aae:16bf:d09/64 Scope:Global
          inet6 addr: fe80::6a17:29ff:fe2d:9ec/64 Scope:Link
          inet6 addr: 2a00:1028:8398:6426:6a17:29ff:fe2d:9ec/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:841053 errors:0 dropped:0 overruns:0 frame:0
          TX packets:470333 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1156330181 (1.1 GB)  TX bytes:41755138 (41.7 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Internet_F2"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'Internet_F2' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9658   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.138      0.0.0.0         UG    0      0        0 wlan0
10.0.0.0        0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search Home

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

- Device: wlan0  [Internet_F2] -------------------------------------------------
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
    matas:           Infra, <MAC 'matas' [AC5]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 72 WPA
    urban:           Infra, <MAC 'urban' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA
    Krausovaheslo100kc: Infra, <MAC 'Krausovaheslo100kc' [AC4]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 45 WPA
    hotspot.kostnet.cz: Infra, <MAC 'hotspot.kostnet.cz' [AC7]>, Freq 2467 MHz, Rate 11 Mb/s, Strength 30 WPA
    martan10-01b.kostnet.cz: Infra, <MAC 'martan10-01b.kostnet.cz' [AC6]>, Freq 2467 MHz, Rate 11 Mb/s, Strength 32 WEP
    sabaka10-01b.kostnet.cz: Infra, <MAC 'sabaka10-01b.kostnet.cz' [AN6]>, Freq 2467 MHz, Rate 11 Mb/s, Strength 14 WEP
    tera:            Infra, <MAC 'tera' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA
    *Internet_F2:    Infra, <MAC 'Internet_F2' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 69 WPA2
    pavel:           Infra, <MAC 'pavel' [AN9]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA

  IPv4 Settings:
    Address:         10.0.0.32
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.138

    DNS:             10.0.0.138

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

no-auto-default=<MAC 'eth0' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Internet_F2]] (600 root)
[connection] id=Internet_F2 | type=802-11-wireless | permissions=user:roland:;
[802-11-wireless] ssid=Internet_F2 | bssid=<MAC 'Internet_F2' [AC1]> | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/CTU-FA-Students]] (600 root)
[connection] id=CTU-FA-Students | type=802-11-wireless
[802-11-wireless] ssid=CTU-FA-Students | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/josh]] (600 root)
[connection] id=josh | type=802-11-wireless
[802-11-wireless] ssid=josh | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[ipv6] method=auto
[connection] id=eduroam | type=802-11-wireless
[802-11-wireless] ssid=eduroam | mac-address=<MAC 'wlan0' [IF]>
[802-1x] system-ca-certs=true
[ipv4] method=auto

##### iw reg get ########################

Region: Europe/Prague (based on set time zone)

country CZ:
    (2400 - 2483 @ 40), (N/A, 20)
    (5150 - 5250 @ 40), (N/A, 23), NO-OUTDOOR
    (5250 - 5350 @ 40), (N/A, 20), NO-OUTDOOR, DFS
    (5470 - 5725 @ 40), (N/A, 26), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

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

      3   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      2   APs on   Frequency:2.467 GHz (Channel 12)
      1   APs on   Frequency:2.472 GHz (Channel 13)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Internet_F2' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Internet_F2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001873c33cda
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'urban' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"urban"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000315066a937
                    Extra: Last beacon: 52ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'tera' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"tera"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000cce5a6c967
                    Extra: Last beacon: 52ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Krausovaheslo100kc' [AC4]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Krausovaheslo100kc"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002b65edfe165
                    Extra: Last beacon: 60ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'matas' [AC5]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"matas"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000646fbcbc8d
                    Extra: Last beacon: 52ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'martan10-01b.kostnet.cz' [AC6]>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"martan10-01b.kostnet.cz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=000002b65d788181
                    Extra: Last beacon: 312ms ago
          Cell 07 - Address: <MAC 'hotspot.kostnet.cz' [AC7]>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"hotspot.kostnet.cz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=000002b65d788641
                    Extra: Last beacon: 312ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwldvm]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     CC4D1BA11C1EF73A6ABDE53
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     C2D0F3DFCA289585C100E36
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
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
filename:       /lib/modules/3.13.0-39-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
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
11n_disable: 8
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
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=8

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x0888 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   21.257522] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[   21.265080] iwlwifi 0000:08:00.0: Radio type=0x2-0x0-0x0
[   21.508851] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[   21.516451] iwlwifi 0000:08:00.0: Radio type=0x2-0x0-0x0
[   21.590461] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   42.020811] wlan0: authenticate with <MAC 'Internet_F2' [AC1]>
[   42.027916] wlan0: send auth to <MAC 'Internet_F2' [AC1]> (try 1/3)
[   42.030651] wlan0: authenticated
[   42.032957] wlan0: associate with <MAC 'Internet_F2' [AC1]> (try 1/3)
[   42.036542] wlan0: RX AssocResp from <MAC 'Internet_F2' [AC1]> (capab=0x411 status=0 aid=1)
[   42.055310] wlan0: associated
[   42.055357] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  386.797179] wlan0: deauthenticating from <MAC 'Internet_F2' [AC1]> by local choice (reason=3)
[  387.293700] wlan0: authenticate with <MAC 'Internet_F2' [AC1]>
[  387.300115] wlan0: send auth to <MAC 'Internet_F2' [AC1]> (try 1/3)
[  387.302923] wlan0: authenticated
[  387.303439] wlan0: associate with <MAC 'Internet_F2' [AC1]> (try 1/3)
[  387.309211] wlan0: RX AssocResp from <MAC 'Internet_F2' [AC1]> (capab=0x411 status=0 aid=1)
[  387.328171] wlan0: associated

########## wireless info END ############



```

---

### Post by praseodym on 2014-11-10
```
[  386.797179] wlan0: deauthenticating from <MAC 'Internet_F2' [AC1]> by local choice (reason=3)
```
Obviously, a network manager issue. Try setting IPv6 to "Ignore" and reconnect.

---

### Post by snowflake2 on 2014-11-11
I already have it set to ignore.

---

### Post by praseodym on 2014-11-11
> ```
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=8
```
Please change "8" to "1" via
```

gksudo gedit /etc/modprobe.d/iwlwifi.conf
```
save, and reboot.

---

### Post by danbebber on 2015-03-29
You have the dreaded Intel Centrino 2230 card. It has caused people many headaches: [https://communities.intel.com/thread/38676](https://communities.intel.com/thread/38676)
The solution that worked for me was to disable Bluetooth. Now my wifi (on Dell Inspiron 17SE running Linux Mint 17) is nearly as fast as my Macbook Air.

---

