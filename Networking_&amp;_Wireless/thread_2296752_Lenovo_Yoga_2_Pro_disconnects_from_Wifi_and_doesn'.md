---
title: "Lenovo Yoga 2 Pro disconnects from Wifi and doesn't reconnect"
date: 2015-09-28
forum: Networking &amp; Wireless
---

### Post by ben177 on 2015-09-28
Hello,


I'm rather new tolinux so sorry if there's any info missing. I'm running 14.04 LTS.
I've been using itfor a few weeks and except for a few minor issues with touchpad etc.everything worked fine. In the last couple of days I've been havingrandom disconnections after turning the computer on. A restart of thewhole computer usually solves it, but sometimes a restart of thenetwork interface through command prompt is enough, it varies. Thedisconnection happens after a few minutes. Restarting the networkinterface through GUI doesn't work, it sees a couple of networks butnot the one I need to connect to, and there's no problem with itsince my phone is connected to it and works perfectly.
I've tried updatingthe drivers as is recommended in the &#8220;Read before posting&#8221; post.Below are the results of the wireless information script.


Thanks,


Ben
EDIT:
I have dual boot, I booted into windows and the problem appeares there as well, what can I do to diagnose this? The computer hasn't fallen oranything similar so I don't see any reason physical damage


```


########## wirelessinfo START ##########


Report from: 28 Sep2015 15:43 IDT +0300


Booted last: 28 Sep2015 15:42 IDT +0300


Script from: 14 Jul2015 17:04 UTC +0000


##### release###########################


DistributorID:	Ubuntu
Description:	Ubuntu14.04.3 LTS
Release:	14.04
Codename:	trusty


##### kernel############################


Linux3.19.0-28-generic #30~14.04.1-Ubuntu SMP Tue Sep 1 09:32:55 UTC 2015x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro,quiet, splash, vt.handoff=7


##### desktop###########################


Ubuntu


##### lspci#############################


01:00.0 Networkcontroller [0280]: Intel Corporation Wireless 7260 [8086:08b2] (rev6b)
	Subsystem: IntelCorporation Wireless-N 7260 [8086:c262]
	Kernel driver inuse: iwlwifi


##### lsusb#############################


Bus 003 Device 002:ID 8087:8000 Intel Corp. 
Bus 003 Device 001:ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001:ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005:ID 1bcf:2c43 Sunplus Innovation Technology Inc. 
Bus 001 Device 004:ID 04f3:040d Elan Microelectronics Corp. 
Bus 001 Device 003:ID 2047:0855 Texas Instruments 
Bus 001 Device 002:ID 8087:07dc Intel Corp. 
Bus 001 Device 001:ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA cardinfo ##################


##### rfkill############################


0: ideapad_wlan:Wireless LAN
	Soft blocked: no
	Hard blocked: no
1:ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: WirelessLAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no


##### lsmod#############################


iwlmvm               278528  0 
mac80211             708608  1 iwlmvm
iwlwifi              188416  1 iwlmvm
cfg80211             524288  3 iwlwifi,mac80211,iwlmvm
ideapad_laptop        20480  0 
sparse_keymap         16384  1 ideapad_laptop


##### interfaces########################


auto lo
iface lo inetloopback


##### ifconfig##########################


wlan0     Linkencap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inetaddr:10.0.0.5  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UPBROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RXpackets:1456 errors:0 dropped:0 overruns:0 frame:0
          TXpackets:562 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000 
          RXbytes:1768168 (1.7 MB)  TX bytes:122518 (122.5 KB)


##### iwconfig##########################


lo        nowireless extensions.


wlan0     IEEE802.11bgn  ESSID:"Dambe 2.4"  
         Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'Dambe 2.4'[AC5]>   
          BitRate=130 Mb/s   Tx-Power=22 dBm   
          Retryshort limit:7   RTS thr:off   Fragment thr:off
          PowerManagement:on
          LinkQuality=67/70  Signal level=-43 dBm  
          Rx invalidnwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Txexcessive retries:0  Invalid misc:50   Missed beacon:0


##### route#############################


Kernel IP routingtable
Destination    Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0        10.0.0.138      0.0.0.0         UG    0      0        0 wlan0
10.0.0.0       0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf#######################


nameserver 127.0.1.1


##### networkmanagers ##################


Installed:


	NetworkManager


Running:


root       723     1 1 15:42 ?        00:00:00 NetworkManager


##### NetworkManagerinfo ###############


NetworkManager Tool


State: connected(global)


- Device: wlan0 [Dambe 2.4] ---------------------------------------------------
  Type:             802.11 WiFi
  Driver:           iwlwifi
  State:            connected
  Default:          yes
  HW Address:       <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:          36 Mb/s


  WirelessProperties
    WEP Encryption: yes
    WPA Encryption: yes
    WPA2 Encryption:yes


  Wireless AccessPoints (* = current AP)
    HOTBOX-3A4E:    Infra, <MAC 'HOTBOX-3A4E' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s,Strength 50 WPA WPA2
    onyim:          Infra, <MAC 'onyim' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s,Strength 42 WPA2
   BezeqNGN_016897_2.4GHz_1: Infra, <MAC 'BezeqNGN_016897_2.4GHz_1'[AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA
    dekelsh:        Infra, <MAC 'dekelsh' [AC4]>, Freq 2442 MHz, Rate 54 Mb/s,Strength 29 WPA2
    Bezeq Free1085DA: Infra, <MAC 'Bezeq Free 1085DA' [AC1]>, Freq 2437 MHz,Rate 54 Mb/s, Strength 40
    HOTBOX-A91A:    Infra, <MAC 'HOTBOX-A91A' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s,Strength 27
    *Dambe 2.4:     Infra, <MAC 'Dambe 2.4' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s,Strength 81 WPA2
    grace_2.4:      Infra, <MAC 'grace_2.4' [AC8]>, Freq 2412 MHz, Rate 54 Mb/s,Strength 39 WEP


  IPv4 Settings:
    Address:        10.0.0.5
    Prefix:         24 (255.255.255.0)
    Gateway:        10.0.0.138


    DNS:            10.0.0.138


#####NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


#####NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManagerprofiles ###########


[[/etc/NetworkManager/system-connections/BezeqNGN_016897_2.4GHz_1]](600 root)
[connection]id=BezeqNGN_016897_2.4GHz_1 | type=802-11-wireless
[802-11-wireless]ssid=BezeqNGN_016897_2.4GHz_1 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Hiro-Guests]](600 root)
[connection]id=Hiro-Guests | type=802-11-wireless
[802-11-wireless]ssid=Hiro-Guests | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/eduroam]](600 root)
[ipv6] method=auto
[connection]id=eduroam | type=802-11-wireless
[802-11-wireless]ssid=eduroam | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Dambe2.4]] (600 root)
[connection]id=Dambe 2.4 | type=802-11-wireless
[802-11-wireless]ssid=Dambe 2.4 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Ben]](600 root)
[connection] id=Ben| type=802-11-wireless
[802-11-wireless]ssid=Ben | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/yvonne-2.4]](600 root)
[connection]id=yvonne-2.4 | type=802-11-wireless
[802-11-wireless]ssid=yvonne-2.4 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Wallach]](600 root)
[connection]id=Wallach | type=802-11-wireless
[802-11-wireless]ssid=Wallach | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HOTBOX-3A4E]](600 root)
[connection]id=HOTBOX-3A4E | type=802-11-wireless
[802-11-wireless]ssid=HOTBOX-3A4E | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ISRAEL-RAILWAYS]](600 root)
[connection]id=ISRAEL-RAILWAYS | type=802-11-wireless
[802-11-wireless]ssid=ISRAEL-RAILWAYS | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


##### iw reg get########################


Region:Asia/Jerusalem (based on set time zone)


country 00:
	(2402 - 2472 @ 40),(3, 20)
	(2457 - 2482 @ 40),(3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20),(3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40),(3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40),(3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlistchannels ###################


lo        nofrequency information.


wlan0     13channels in total; available frequencies :
          Channel 01: 2.412 GHz
          Channel 02: 2.417 GHz
          Channel 03: 2.422 GHz
          Channel 04: 2.427 GHz
          Channel 05: 2.432 GHz
          Channel 06: 2.437 GHz
          Channel 07: 2.442 GHz
          Channel 08: 2.447 GHz
          Channel 09: 2.452 GHz
          Channel 10: 2.457 GHz
          Channel 11: 2.462 GHz
          Channel 12: 2.467 GHz
          Channel 13: 2.472 GHz
          CurrentFrequency:2.462 GHz (Channel 11)


##### iwlist scan#######################


lo        Interfacedoesn't support scanning.


Channel occupancy:


      1   APs on  Frequency:2.412 GHz (Channel 1)
      3   APs on  Frequency:2.437 GHz (Channel 6)
      1   APs on  Frequency:2.442 GHz (Channel 7)
      4   APs on  Frequency:2.462 GHz (Channel 11)


wlan0     Scancompleted :
          Cell 01 -Address: <MAC 'Bezeq Free 1085DA' [AC1]>
                   Channel:6
                   Frequency:2.437 GHz (Channel 6)
                   Quality=34/70  Signal level=-76 dBm  
                   Encryption key:off
                   ESSID:"Bezeq Free 1085DA"
                   Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                             24 Mb/s; 36 Mb/s; 54 Mb/s
                   Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                   Mode:Master
                   Extra:tsf=00000053a19ac1af
                   Extra: Last beacon: 60ms ago
          Cell 02 -Address: <MAC 'onyim' [AC2]>
                   Channel:6
                   Frequency:2.437 GHz (Channel 6)
                   Quality=34/70  Signal level=-76 dBm  
                   Encryption key:on
                   ESSID:"onyim"
                   Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                             24 Mb/s; 36 Mb/s; 54 Mb/s
                   Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                   Mode:Master
                   Extra:tsf=00000053a19ac9c9
                   Extra: Last beacon: 60ms ago
                   IE: IEEE 802.11i/WPA2 Version 1
                       Group Cipher : CCMP
                       Pairwise Ciphers (1) : CCMP
                       Authentication Suites (1) : PSK
          Cell 03 -Address: <MAC 'BezeqNGN_016897_2.4GHz_1' [AC3]>
                   Channel:6
                   Frequency:2.437 GHz (Channel 6)
                   Quality=29/70  Signal level=-81 dBm  
                   Encryption key:on
                   ESSID:"BezeqNGN_016897_2.4GHz_1"
                   Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                             24 Mb/s; 36 Mb/s; 54 Mb/s
                   Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                   Mode:Master
                   Extra:tsf=0000013c8603eb33
                   Extra: Last beacon: 60ms ago
                   IE: WPA Version 1
                       Group Cipher : TKIP
                       Pairwise Ciphers (2) : CCMP TKIP
                       Authentication Suites (1) : PSK
          Cell 04 -Address: <MAC 'dekelsh' [AC4]>
                   Channel:7
                   Frequency:2.442 GHz (Channel 7)
                   Quality=26/70  Signal level=-84 dBm  
                   Encryption key:on
                   ESSID:"dekelsh"
                   Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                             9 Mb/s; 12 Mb/s; 18 Mb/s
                   Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                   Mode:Master
                   Extra:tsf=000001973c616180
                   Extra: Last beacon: 620ms ago
                   IE: IEEE 802.11i/WPA2 Version 1
                       Group Cipher : CCMP
                       Pairwise Ciphers (1) : CCMP
                       Authentication Suites (1) : PSK
          Cell 05 -Address: <MAC 'Dambe 2.4' [AC5]>
                   Channel:11
                   Frequency:2.462 GHz (Channel 11)
                   Quality=70/70  Signal level=-37 dBm  
                   Encryption key:on
                   ESSID:"Dambe 2.4"
                   Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                             24 Mb/s; 36 Mb/s; 54 Mb/s
                   Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                   Mode:Master
                   Extra:tsf=00000042cf1b3265
                   Extra: Last beacon: 60ms ago
                   IE: IEEE 802.11i/WPA2 Version 1
                       Group Cipher : CCMP
                       Pairwise Ciphers (1) : CCMP
                       Authentication Suites (1) : PSK
          Cell 06 -Address: <MAC 'HOTBOX-3A4E' [AC6]>
                   Channel:11
                   Frequency:2.462 GHz (Channel 11)
                   Quality=40/70  Signal level=-70 dBm  
                   Encryption key:on
                   ESSID:"HOTBOX-3A4E"
                   Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                             24 Mb/s; 36 Mb/s; 54 Mb/s
                   Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                   Mode:Master
                   Extra:tsf=00000034e2d21d55
                   Extra: Last beacon: 60ms ago
                   IE: IEEE 802.11i/WPA2 Version 1
                       Group Cipher : TKIP
                       Pairwise Ciphers (2) : CCMP TKIP
                       Authentication Suites (1) : PSK
                   IE: WPA Version 1
                       Group Cipher : TKIP
                       Pairwise Ciphers (2) : CCMP TKIP
                       Authentication Suites (1) : PSK
          Cell 07 -Address: <MAC 'HOTBOX-A91A' [AC7]>
                   Channel:11
                   Frequency:2.462 GHz (Channel 11)
                   Quality=26/70  Signal level=-84 dBm  
                   Encryption key:off
                   ESSID:"HOTBOX-A91A"
                   Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                             24 Mb/s; 36 Mb/s; 54 Mb/s
                   Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                   Mode:Master
                   Extra:tsf=000001bfbdefc157
                   Extra: Last beacon: 14576ms ago
          Cell 08 -Address: <MAC 'grace_2.4' [AC8]>
                   Channel:1
                   Frequency:2.412 GHz (Channel 1)
                   Quality=34/70  Signal level=-76 dBm  
                   Encryption key:on
                   ESSID:"grace_2.4"
                   Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                             24 Mb/s; 36 Mb/s; 54 Mb/s
                   Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                   Mode:Master
                   Extra:tsf=0000023739ae1e11
                   Extra: Last beacon: 60ms ago
          Cell 09 -Address: <MAC 'HOTBOX-ED68' [AC9]>
                   Channel:11
                   Frequency:2.462 GHz (Channel 11)
                   Quality=26/70  Signal level=-84 dBm  
                   Encryption key:on
                   ESSID:"HOTBOX-ED68"
                   Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                             24 Mb/s; 36 Mb/s; 54 Mb/s
                   Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s


##### module infos######################


[iwlmvm]
filename:      /lib/modules/3.19.0-28-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:        Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:       in-tree:
description:    Thenew Intel(R) wireless AGN driver for Linux
srcversion:    03499C43751395EB809E042
depends:       iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:      3.19.0-28-generic SMP mod_unload modversions 
signer:        Magrathea: Glacier signing key
sig_key:       29:4D:C0:12:70:6F:48:B7:CD:DF:63:74:E2:D7:9F:E1:B0:60:92:69
sig_hashalgo:  sha512
parm:          init_dbg:set to true to debug an ASSERT in INIT fw (default: false(bool)
parm:          power_scheme:power management scheme: 1-active, 2-balanced, 3-lowpower, default: 2 (int)


[mac80211]
filename:      /lib/modules/3.19.0-28-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE802.11 subsystem
srcversion:    DF4E06FB15FF0707074A816
depends:       cfg80211
intree:         Y
vermagic:      3.19.0-28-generic SMP mod_unload modversions 
signer:        Magrathea: Glacier signing key
sig_key:       29:4D:C0:12:70:6F:48:B7:CD:DF:63:74:E2:D7:9F:E1:B0:60:92:69
sig_hashalgo:  sha512
parm:          minstrel_vht_only:Use only VHT rates when VHT is supported by sta.(bool)
parm:          max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting(reason 4). (int)
parm:          max_probe_tries:Maximum probe tries before disconnecting (reason 4).(int)
parm:          beacon_loss_count:Number of beacon intervals before we decide beaconwas lost. (int)
parm:          probe_wait_ms:Maximum time(ms) to wait for probe response beforedisconnecting (reason 4). (int)
parm:          ieee80211_default_rc_algo:Default rate control algorithm for mac80211to use (charp)


[iwlwifi]
filename:      /lib/modules/3.19.0-28-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:        Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:       in-tree:
description:   Intel(R) Wireless WiFi driver for Linux
firmware:      iwlwifi-100-5.ucode
firmware:      iwlwifi-1000-5.ucode
firmware:      iwlwifi-135-6.ucode
firmware:      iwlwifi-105-6.ucode
firmware:      iwlwifi-2030-6.ucode
firmware:      iwlwifi-2000-6.ucode
firmware:      iwlwifi-5150-2.ucode
firmware:      iwlwifi-5000-5.ucode
firmware:      iwlwifi-6000g2b-6.ucode
firmware:      iwlwifi-6000g2a-5.ucode
firmware:      iwlwifi-6050-5.ucode
firmware:      iwlwifi-6000-4.ucode
firmware:      iwlwifi-7265D-10.ucode
firmware:      iwlwifi-7265-10.ucode
firmware:      iwlwifi-3165-10.ucode
firmware:      iwlwifi-3160-10.ucode
firmware:      iwlwifi-7260-10.ucode
firmware:      iwlwifi-8000-10.ucode
srcversion:    19A5C735A79087003D53D6A
depends:       cfg80211
intree:         Y
vermagic:      3.19.0-28-generic SMP mod_unload modversions 
signer:        Magrathea: Glacier signing key
sig_key:       29:4D:C0:12:70:6F:48:B7:CD:DF:63:74:E2:D7:9F:E1:B0:60:92:69
sig_hashalgo:  sha512
parm:          swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:          11n_disable:disable 11n functionality, bitmap: 1: full, 2: disableagg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:          amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:          fw_restart:restart firmware in case of error (default true) (bool)
parm:          antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:          wd_disable:Disable stuck queue watchdog timer 0=system default,1=disable (default: 1) (int)
parm:          nvm_file:NVM file name (charp)
parm:          uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:          bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:          led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off(default: 0) (int)
parm:          power_save:enable WiFi power management (default: disable) (bool)
parm:          power_level:default power save level (range from 1 - 5, default: 1)(int)
parm:          fw_monitor:firmware monitor - to debug FW (default: false - needslots of memory) (bool)


[cfg80211]
filename:      /lib/modules/3.19.0-28-generic/kernel/net/wireless/cfg80211.ko
description:   wireless configuration support
license:        GPL
author:        Johannes Berg
srcversion:    F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:      3.19.0-28-generic SMP mod_unload modversions 
signer:        Magrathea: Glacier signing key
sig_key:       29:4D:C0:12:70:6F:48:B7:CD:DF:63:74:E2:D7:9F:E1:B0:60:92:69
sig_hashalgo:  sha512
parm:          ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:          cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band(bool)


##### moduleparameters #################


[iwlmvm]
init_dbg: N
power_scheme: 2


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo:minstrel_ht
max_nullfunc_tries:2
max_probe_tries: 5
minstrel_vht_only: Y
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
cfg80211_disable_40mhz_24ghz:N
ieee80211_regdom: 00


##### /etc/modules######################


lp
rtc


##### modprobeoptions ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklistsnd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklistamd76x_edac


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
(/sbin/lsmod | grep-o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&&/sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_corepost: mlx4_en


##### rc.local##########################


exit 0


##### pm-utils##########################


##### udev rules########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device0x8086:0x08b2 (iwlwifi)
SUBSYSTEM=="net",ACTION=="add", DRIVERS=="?*",ATTR{address}=="<MAC 'wlan0' [IF]>",ATTR{dev_id}=="0x0", ATTR{type}=="1",KERNEL=="wlan*", NAME="wlan0"


##### dmesg#############################


[    2.118654]ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   13.013440]iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[   13.034039] IPv6:ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.128856]wlan0: authenticate with <MAC 'Dambe 2.4' [AC5]>
[   14.136905]wlan0: send auth to <MAC 'Dambe 2.4' [AC5]> (try 1/3)
[   14.175880]wlan0: authenticated
[   14.178660]wlan0: associate with <MAC 'Dambe 2.4' [AC5]> (try 1/3)
[   14.191556]wlan0: RX AssocResp from <MAC 'Dambe 2.4' [AC5]> (capab=0x411status=0 aid=1)
[   14.192763]wlan0: associated
[   14.192796] IPv6:ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   14.247047]wlan0: deauthenticating from <MAC 'Dambe 2.4' [AC5]> by localchoice (Reason: 2=PREV_AUTH_NOT_VALID)
[   14.260191]wlan0: authenticate with <MAC 'Dambe 2.4' [AC5]>
[   14.265129]wlan0: send auth to <MAC 'Dambe 2.4' [AC5]> (try 1/3)
[   14.271765]wlan0: authenticated
[   14.274717]wlan0: associate with <MAC 'Dambe 2.4' [AC5]> (try 1/3)
[   14.287385]wlan0: RX AssocResp from <MAC 'Dambe 2.4' [AC5]> (capab=0x411status=0 aid=1)
[   14.300475]wlan0: associated


########## wirelessinfo END ############

```

---

### Post by ben177 on 2015-09-29
Hi, just an update, it's getting much worse, usually internet stops working a minute or two after boot but now the WiFi stays connected, internet simply doesn't work (tried multiple browsers, programs etc.)
Thanks!

---

