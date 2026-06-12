---
title: "Lenovo Y40 - Connection Drops Constantly - Ubuntu 14.04"
date: 2015-07-11
forum: Networking &amp; Wireless
---

### Post by josueortc on 2015-07-11
Hello I have a Lenovo Y40 with dual boot between Windows 7 and Ubuntu 14.04. The Wireless connection is constantly dropping and then reconnecting by itself in Ubuntu but in Windows it's working fine.

Is there anyway to solve this problem, I will include the wireless-info.

```
########## wireless info START ##########

Report from: 11 Jul 2015 11:26 PET -0500


Booted last: 11 Jul 2015 11:13 PET -0500


Script from: 21 May 2015 09:10 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.16.0-43-generic #58~14.04.1-Ubuntu SMP Mon Jun 22 10:21:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Lenovo Device [17aa:3809]
	Kernel driver in use: r8169


04:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b4] (rev 93)
	Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8270]
	Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 8087:07dc Intel Corp. 
Bus 002 Device 002: ID 174f:14b1 Syntek 
Bus 002 Device 004: ID 413c:3016 Dell Computer Corp. Optical 5-Button Wheel Mouse
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


iwlmvm                217725  0 
mac80211              652777  1 iwlmvm
iwlwifi               179412  1 iwlmvm
cfg80211              494362  3 iwlwifi,mac80211,iwlmvm
snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          200204  1 snd_soc_rt5640
ideapad_laptop         18278  0 
snd_pcm               104112  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
sparse_keymap          13948  1 ideapad_laptop


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
          inet addr:192.168.1.38  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2001:1388:7:ba10:fc58:c24e:5402:d4b9/64 Scope:Global
          inet6 addr: fe80::d27e:35ff:fe1d:7734/64 Scope:Link
          inet6 addr: 2001:1388:7:ba10:d27e:35ff:fe1d:7734/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22876 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18937 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24689999 (24.6 MB)  TX bytes:2562268 (2.5 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"REDCARO"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'REDCARO' [AC1]>   
          Bit Rate=18 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:70   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search Home


##### network managers ##################


Installed:


	NetworkManager


Running:


root       766     1  0 11:13 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: wlan0  [REDCARO] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           11 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    CLAUDIO:         Infra, <MAC 'CLAUDIO' [AN1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    patricio:        Infra, <MAC 'patricio' [AN2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA2
    LUISAMARIA:      Infra, <MAC 'LUISAMARIA' [AN3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA2
    JSMS-1:          Infra, <MAC 'JSMS-1' [AN4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    JSMS-IMP:        Infra, <MAC 'JSMS-IMP' [AN5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    ChromecastCoca:  Infra, <MAC 'ChromecastCoca' [AN6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14
    CARMELA:         Infra, <MAC 'CARMELA' [AC10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WPA
    MILENE:          Infra, <MAC 'MILENE' [AN8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 10 WPA
    DELFO 1:         Infra, <MAC 'DELFO 1' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA
    alfredo:         Infra, <MAC 'alfredo' [AN10]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA2
    RiveroLuna:      Infra, <MAC 'RiveroLuna' [AN11]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 9 WPA WPA2
    laura:           Infra, <MAC 'laura' [AN12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA
    Tweddle 1:       Infra, <MAC 'Tweddle 1' [AN13]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 10 WPA WPA2
    ABRIL:           Infra, <MAC 'ABRIL' [AN14]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA2
    *REDCARO:        Infra, <MAC 'REDCARO' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 66 WPA2


  IPv4 Settings:
    Address:         192.168.1.38
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             200.48.225.130
    DNS:             200.48.225.146


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


[[/etc/NetworkManager/system-connections/REDCARO]] (600 root)
[connection] id=REDCARO | type=802-11-wireless
[802-11-wireless] ssid=REDCARO | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Lima (based on set time zone)


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
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      3   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      2   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.5 GHz (Channel 100)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'REDCARO' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"REDCARO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001ba72be8496
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'DELFO 1' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"DELFO 1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001d046a8baf
                    Extra: Last beacon: 64ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'eic-tab' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"eic-tab"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000293ff7f985
                    Extra: Last beacon: 64ms ago
          Cell 04 - Address: <MAC 'Kinder_Wrlss' [AC4]>
                    Channel:100
                    Frequency:5.5 GHz (Channel 100)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Kinder_Wrlss"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000028e374605e
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'CHARLES' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:"CHARLES"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000007bbff4a717c
                    Extra: Last beacon: 4912ms ago
          Cell 06 - Address: <MAC 'eic-tab' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:off
                    ESSID:"eic-tab"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002940032b85
                    Extra: Last beacon: 64ms ago
          Cell 07 - Address: <MAC 'Catherine' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"Catherine"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000293ed2048a
                    Extra: Last beacon: 64ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'BRUNELLA' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"BRUNELLA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000293f6e119c
                    Extra: Last beacon: 4660ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'CuartO' [AC9]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"CuartO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000040f17c9ec
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'CARMELA' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"CARMELA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000aaed255d09
                    Extra: Last beacon: 64ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[iwlmvm]
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     C3CE81DD94553577D83E97E
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)


[mac80211]
filename:       /lib/modules/3.16.0-43-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     315DCE1E2614AE1F38132D3
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     93D664267873827B22C4309
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
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
filename:       /lib/modules/3.16.0-43-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     33ED2C1448F5AEDBE7AF59E
depends:        
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[iwlmvm]
init_dbg: N
power_scheme: 2


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
# PCI device 0x8086:0x08b4 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[  261.932265] wlan0: authenticate with <MAC 'REDCARO' [AC1]>
[  261.939274] wlan0: send auth to <MAC 'REDCARO' [AC1]> (try 1/3)
[  261.941175] wlan0: authenticated
[  261.942038] wlan0: associate with <MAC 'REDCARO' [AC1]> (try 1/3)
[  261.946855] wlan0: RX AssocResp from <MAC 'REDCARO' [AC1]> (capab=0x411 status=0 aid=1)
[  261.947424] wlan0: associated
[  364.527981] wlan0: deauthenticating from <MAC 'REDCARO' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  368.152737] wlan0: authenticate with <MAC 'REDCARO' [AC1]>
[  368.158446] wlan0: send auth to <MAC 'REDCARO' [AC1]> (try 1/3)
[  368.160388] wlan0: authenticated
[  368.162067] wlan0: associate with <MAC 'REDCARO' [AC1]> (try 1/3)
[  368.165501] wlan0: RX AssocResp from <MAC 'REDCARO' [AC1]> (capab=0x411 status=0 aid=1)
[  368.166109] wlan0: associated
[  489.182739] wlan0: deauthenticating from <MAC 'REDCARO' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  492.808612] wlan0: authenticate with <MAC 'REDCARO' [AC1]>
[  492.813839] wlan0: send auth to <MAC 'REDCARO' [AC1]> (try 1/3)
[  492.815759] wlan0: authenticated
[  492.818474] wlan0: associate with <MAC 'REDCARO' [AC1]> (try 1/3)
[  492.823940] wlan0: RX AssocResp from <MAC 'REDCARO' [AC1]> (capab=0x411 status=0 aid=1)
[  492.824589] wlan0: associated
[  570.611923] wlan0: deauthenticating from <MAC 'REDCARO' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  574.248496] wlan0: authenticate with <MAC 'REDCARO' [AC1]>
[  574.255032] wlan0: send auth to <MAC 'REDCARO' [AC1]> (try 1/3)
[  574.257068] wlan0: authenticated
[  574.259469] wlan0: associate with <MAC 'REDCARO' [AC1]> (try 1/3)
[  574.263129] wlan0: RX AssocResp from <MAC 'REDCARO' [AC1]> (capab=0x411 status=0 aid=1)
[  574.263947] wlan0: associated
[  709.307365] wlan0: deauthenticating from <MAC 'REDCARO' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  712.931190] wlan0: authenticate with <MAC 'REDCARO' [AC1]>
[  712.937231] wlan0: send auth to <MAC 'REDCARO' [AC1]> (try 1/3)
[  712.939169] wlan0: authenticated
[  712.939358] wlan0: associate with <MAC 'REDCARO' [AC1]> (try 1/3)
[  712.947032] wlan0: RX AssocResp from <MAC 'REDCARO' [AC1]> (capab=0x411 status=0 aid=1)
[  712.947879] wlan0: associated
[  713.008200] wlan0: deauthenticating from <MAC 'REDCARO' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[  713.028362] wlan0: authenticate with <MAC 'REDCARO' [AC1]>
[  713.034433] wlan0: send auth to <MAC 'REDCARO' [AC1]> (try 1/3)
[  713.044042] wlan0: authenticated
[  713.047495] wlan0: associate with <MAC 'REDCARO' [AC1]> (try 1/3)
[  713.051007] wlan0: RX AssocResp from <MAC 'REDCARO' [AC1]> (capab=0x411 status=0 aid=1)
[  713.054226] wlan0: associated


########## wireless info END ############



```

---

