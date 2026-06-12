---
title: "Ubuntu 14.04 Wifi disconnects"
date: 2015-06-17
forum: Networking &amp; Wireless
---

### Post by meteoros9 on 2015-06-17
Hi, my wifi keeps disconnecting, i've a dual boot ubuntu+win8.1, wifi works great in win 8.1, in ubuntu after a few minutes turns off and the network dissapears from list, i try to disable wifi connections and enable it again and after this works for few minutes again or if i reboot computer wifi is back again, follows the script output, any ideias what is wrong? Thanks
```


########## wireless info START ##########


Report from: 17 Jun 2015 18:24 WEST +0100


Booted last: 17 Jun 2015 18:57 WEST +0100


Script from: 21 May 2015 09:10 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic


##### kernel ############################


Linux 3.16.0-41-generic #55-Ubuntu SMP Sun Jun 14 18:31:10 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: AzureWave Device [1a3b:2161]
    Kernel driver in use: rtl8821ae


04:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:57b4 Realtek Semiconductor Corp. 
Bus 001 Device 006: ID 09da:9066 A4 Tech Co., Ltd 
Bus 001 Device 005: ID 099a:610c Zippy Technology Corp. EL-610 Super Mini Electron luminescent Keyboard
Bus 001 Device 002: ID 1a40:0201 Terminus Technology Inc. FE 2.1 7-port Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


asus_nb_wmi            21128  0 
asus_wmi               24094  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
rtl8821ae             558952  0 
mac80211              660651  1 rtl8821ae
cfg80211              510218  2 mac80211,rtl8821ae
mxm_wmi                13021  1 nouveau
wmi                    19193  3 mxm_wmi,nouveau,asus_wmi
video                  20128  3 i915,nouveau,asus_wmi


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
          inet addr:192.168.1.171  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::42e2:30ff:fe69:5a7b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5856 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4804 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6895317 (6.8 MB)  TX bytes:707283 (707.2 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"ALADINO"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: <MAC 'ALADINO' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search lan


##### network managers ##################


Installed:


    NetworkManager


Running:


root       933     1  0 17:57 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


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


- Device: wlan0  [ALADINO] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8821ae
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
    ZON-9860:        Infra, <MAC 'ZON-9860' [AC4]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2
    MEO-SALETE:      Infra, <MAC 'MEO-SALETE' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 84 WPA WPA2
    Vodafone-351A2F: Infra, <MAC 'Vodafone-351A2F' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    WiFi_9BFA:       Infra, <MAC 'WiFi_9BFA' [AC6]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    Vodafone-EB8EA1: Infra, <MAC 'Vodafone-EB8EA1' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    GOUVEIA:         Infra, <MAC 'GOUVEIA' [AC8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    FON_ZON_FREE_INTERNET: Infra, <MAC 'FON_ZON_FREE_INTERNET' [AC5]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 87
    MEO-WiFi:        Infra, <MAC 'MEO-WiFi' [AN8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54
    MEO-DUARTE:      Infra, <MAC 'MEO-DUARTE' [AN9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    *ALADINO:        Infra, <MAC 'ALADINO' [AC1]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 66 WPA WPA2
    FON_ZON_FREE_INTERNET: Infra, <MAC 'FON_ZON_FREE_INTERNET' [AC10]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 44
    ZON-7AA0:        Infra, <MAC 'ZON-7AA0' [AC9]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.171
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254


    DNS:             192.168.1.254


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


[[/etc/NetworkManager/system-connections/ALADINO]] (600 root)
[connection] id=ALADINO | type=802-11-wireless
[802-11-wireless] ssid=ALADINO | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Familia.Fdasilva]] (600 root)
[connection] id=Familia.Fdasilva | type=802-11-wireless
[802-11-wireless] ssid=Familia.Fdasilva | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/MEO-SALETE]] (600 root)
[connection] id=MEO-SALETE | type=802-11-wireless
[802-11-wireless] ssid=MEO-SALETE | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Lisbon (based on set time zone)


country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), NO-IR
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), NO-IR
    (5735 - 5835 @ 40), (3, 20), NO-IR


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


wlan0     24 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.447 GHz (Channel 8)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      5   APs on   Frequency:2.447 GHz (Channel 8)
      2   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'ALADINO' [AC1]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"ALADINO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c98785f50
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Vodafone-351A2F' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Vodafone-351A2F"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000e02856c1a9
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'MEO-SALETE' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"MEO-SALETE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000087bf74fd7b7
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'ZON-9860' [AC4]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"ZON-9860"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001b6ecb353b
                    Extra: Last beacon: 12ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'FON_ZON_FREE_INTERNET' [AC5]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:off
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001b6d99e3a0
                    Extra: Last beacon: 188ms ago
          Cell 06 - Address: <MAC 'WiFi_9BFA' [AC6]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"WiFi_9BFA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002f1880238d
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'Vodafone-EB8EA1' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"Vodafone-EB8EA1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000003e0d2a41f
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'GOUVEIA' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"GOUVEIA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000033a8a46f5a4
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'ZON-7AA0' [AC9]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"ZON-7AA0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006a3b2a815b
                    Extra: Last beacon: 2492ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'FON_ZON_FREE_INTERNET' [AC10]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006a3b25dbd7
                    Extra: Last beacon: 2796ms ago


##### module infos ######################


[rtl8821ae]
filename:       /lib/modules/3.16.0-41-generic/kernel/drivers/staging/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         Ping Yan<ping_yan@realsil.com.cn>
srcversion:     EA439BC895EA5691716AF12
depends:        mac80211,cfg80211
staging:        Y
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        68:0B:60:38:8A:BA:50:06:28:6B:83:73:99:2B:4D:AA:74:3E:9D:36
sig_hashalgo:   sha512
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)


[mac80211]
filename:       /lib/modules/3.16.0-41-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     376BFDE8E6207B0AAA6339B
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        68:0B:60:38:8A:BA:50:06:28:6B:83:73:99:2B:4D:AA:74:3E:9D:36
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.16.0-41-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     33ED2C1448F5AEDBE7AF59E
depends:        
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        68:0B:60:38:8A:BA:50:06:28:6B:83:73:99:2B:4D:AA:74:3E:9D:36
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8821ae]
fwlps: N
ips: N
swenc: N
swlps: N


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
# PCI device 0x10ec:0x8821 (rtl8821ae)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[ 1641.913955] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[ 1641.913958] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010000 
[ 1641.914013] rtl8821ae-0:rtl_op_sta_remove():<0-0> Remove sta addr is <MAC 'ALADINO' [AC1]>
[ 1641.914099] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_UN_ASSOC
[ 1641.914132] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC address>
[ 1641.933934] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 1, mac: <MAC address>
[ 1641.933942] rtl8821ae-0:rtl_op_set_key():<0-0> alg:TKIP
[ 1641.933945] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 1641.933948] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:1
[ 1641.933955] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[ 1641.933957] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010008 
[ 1642.630574] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1644.036093] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1644.036490] wlan0: authenticate with <MAC 'ALADINO' [AC1]>
[ 1644.036848] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC 'ALADINO' [AC1]>
[ 1644.036928] wlan0: send auth to <MAC 'ALADINO' [AC1]> (try 1/3)
[ 1644.036938] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[ 1644.038502] wlan0: authenticated
[ 1644.040119] wlan0: associate with <MAC 'ALADINO' [AC1]> (try 1/3)
[ 1644.042747] wlan0: RX AssocResp from <MAC 'ALADINO' [AC1]> (capab=0x411 status=0 aid=5)
[ 1644.042760] rtl8821ae-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC 'ALADINO' [AC1]>
[ 1644.042762] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff5
[ 1644.042764] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:4, ratr_val:ff5, 0:6:0:f5:f:0:0
[ 1644.042802] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff5
[ 1644.042804] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:4, ratr_val:ff5, 0:6:0:f5:f:0:0
[ 1644.042830] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[ 1644.042847] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 5c
[ 1644.042872] rtl8821ae: 
[ 1644.042874] rtl8821ae_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL 
[ 1644.042880] rtl8821ae: 
[ 1644.042939] wlan0: associated
[ 1644.050885] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!! (repeated 2 times)
[ 1644.061738] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC 'ALADINO' [AC1]>
[ 1644.061742] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1644.061743] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 1644.061745] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[ 1644.061752] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[ 1644.061756] rtl8821ae-0:rtl_op_set_key():<0-0> set pairwise key
[ 1644.061757] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[ 1644.061758] rtl8821ae-0:rtl8821ae_set_key():<0-0> set Pairwiase key
[ 1644.061760] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC 'ALADINO' [AC1]>
[ 1644.061761] rtl8821ae: 
[ 1644.062406] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[ 1644.062483] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: <MAC address>
[ 1644.062485] rtl8821ae-0:rtl_op_set_key():<0-0> alg:TKIP
[ 1644.062486] rtl8821ae-0:rtl_op_set_key():<0-0> set group key
[ 1644.062487] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[ 1644.062488] rtl8821ae-0:rtl8821ae_set_key():<0-0> set group key
[ 1644.062489] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=2, ulUseDK=0 MacAddr <MAC address>
[ 1644.062491] rtl8821ae: 
[ 1644.063134] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[ 1663.715430] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1663.821912] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1664.083799] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1664.190332] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1664.452192] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1664.558720] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1664.820591] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1664.927125] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1665.189014] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1665.295534] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1665.557423] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1665.663936] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1665.925822] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1666.032340] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1666.294210] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1666.400755] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1666.662674] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1666.769183] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1667.031063] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1667.137591] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1667.399482] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1667.505993] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1667.767876] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1667.874399] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1668.136273] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1668.242800] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G


########## wireless info END ############



```

---

### Post by wildmanne39 on 2015-06-19
Hello, 14.10 is about to have support ended for it in July, I recommend that you upgrade to 15.04 then if you still have wifi issues post a new wireless file.
Thanks

---

### Post by meteoros9 on 2015-06-19
Ok i'll try that.Thank your for help

---

### Post by NoWayWin8 on 2015-06-19
Are you using the same hostname (computer name) in Windows as in Ubuntu? If not it can make a mess of the wlan0 lease renewals for the WiFi access point, resulting in connection issues and constant ipv6 renewal cycles every 15 seconds.  I've never seen this info in any instructions, but setting Windows and Ubuntu to use the same hostname and then resetting the access point makes a lot of wireless issues go away.

---

### Post by meteoros9 on 2015-06-25
Hi, after the update from 14.05 to 15.04 it seems to work fine, it's working for 2 days now.Thank you

---

### Post by wyth on 2015-08-30
> **meteoros9 said:**
> Hi, after the update from 14.05 to 15.04 it seems to work fine, it's working for 2 days now.Thank you

Did it remain fixed for you? I'm having the exact same problem, save for a few differences -- I'm not dual-booting, it's a dedicated ubuntu laptop, I'm on 15.04, and sometimes it cuts off after a few minutes and requires a reboot, while sometimes it cuts out after a few days.

Very mysterious.

---

