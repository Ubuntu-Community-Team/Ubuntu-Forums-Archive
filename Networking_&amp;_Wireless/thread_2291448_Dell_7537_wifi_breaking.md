---
title: "Dell 7537 wifi breaking"
date: 2015-08-20
forum: Networking &amp; Wireless
---

### Post by dragan4 on 2015-08-20
[COLOR=#000000]Plaese help me ...[/COLOR]


[COLOR=#000000]I bought a Dell 7537 and decided to finally get to the 14.04 Ununtu system'm

[/COLOR]Now I have a problem already ten days wi connection keeps breaking . 


I check on my phone everything is working normally. 


When do Enable Wi-Fi check to disable and enable check in connection up and running even 10-15 minutes and again it happens breaking


Would it be some advice on how to solve this problem

```



########## wireless info START ##########


Report from: 20 Aug 2015 11:51 CEST +0200


Booted last: 20 Aug 2015 10:32 CEST +0200


Script from: 14 Jul 2015 17:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-52-generic #86-Ubuntu SMP Mon May 4 04:32:59 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)
    Subsystem: Intel Corporation Dual Band Wireless-N 7260 [8086:4460]
    Kernel driver in use: iwlwifi


03:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: Dell Device [1028:05f9]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 04f3:0206 Elan Microelectronics Corp. 
Bus 002 Device 005: ID 8087:07dc Intel Corp. 
Bus 002 Device 004: ID 0c45:6705 Microdia 
Bus 002 Device 003: ID 04f2:0408 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
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


iwlmvm                189852  0 
mac80211              630669  1 iwlmvm
dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
dell_laptop            18168  0 
dcdbas                 14928  1 dell_laptop
wmi                    19177  1 dell_wmi


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
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:77601 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64055 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:76289214 (76.2 MB)  TX bytes:11541802 (11.5 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"Maric"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Maric' [AC1]>   
          Bit Rate=48 Mb/s   Tx-Power=22 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=41/70  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:55   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       827     1  0 10:32 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: <MAC address> ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no


  Capabilities:


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


- Device: wlan0  [Maric] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           36 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *Maric:          Infra, <MAC 'Maric' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA2


  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1
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
dns=dnsmasq


no-auto-default=<MAC 'eth0' [IF]>,


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Maric]] (600 root)
[connection] id=Maric | type=802-11-wireless
[802-11-wireless] ssid=Maric | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore


##### iw reg get ########################


Region: Europe/Belgrade (based on set time zone)


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


      1   APs on   Frequency:2.437 GHz (Channel 6)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Maric' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Maric"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000090a80d319
                    Extra: Last beacon: 100ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[iwlmvm]
filename:       /lib/modules/3.13.0-52-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     2ED88DF9FE06B5CF295C51A
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-52-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        19:81:BC:91:6F:FC:00:59:92:31:EC:56:30:E6:66:E0:25:6F:D6:F1
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)


[mac80211]
filename:       /lib/modules/3.13.0-52-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     29A87AE7782ED3657631C32
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-52-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        19:81:BC:91:6F:FC:00:59:92:31:EC:56:30:E6:66:E0:25:6F:D6:F1
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.13.0-52-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     A45BAACCAD263355629DB7A
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-52-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        19:81:BC:91:6F:FC:00:59:92:31:EC:56:30:E6:66:E0:25:6F:D6:F1
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
filename:       /lib/modules/3.13.0-52-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     176113E009F723E69BE9BAB
depends:        
intree:         Y
vermagic:       3.13.0-52-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        19:81:BC:91:6F:FC:00:59:92:31:EC:56:30:E6:66:E0:25:6F:D6:F1
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
options iwlwifi 11n_disable=8


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


[/etc/pm/power.d/wireless] (644 root)
/sbin/iwconfig wlan0 power off
/sbin/iwconfig wlan0 power off


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


##### dmesg #############################


[ 1886.709688] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1936.747959] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[ 1936.760291] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1940.444461] wlan0: authenticate with <MAC 'Maric' [AC1]>
[ 1940.446108] wlan0: send auth to <MAC 'Maric' [AC1]> (try 1/3)
[ 1940.447865] wlan0: authenticated
[ 1940.447976] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1940.447979] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1940.450443] wlan0: associate with <MAC 'Maric' [AC1]> (try 1/3)
[ 1940.453073] wlan0: RX AssocResp from <MAC 'Maric' [AC1]> (capab=0x411 status=0 aid=2)
[ 1940.453760] wlan0: associated
[ 1940.453775] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2701.008574] wlan0: deauthenticated from <MAC 'Maric' [AC1]> (Reason: 6)
[ 2701.087735] wlan0: authenticate with <MAC 'Maric' [AC1]>
[ 2701.089432] wlan0: send auth to <MAC 'Maric' [AC1]> (try 1/3)
[ 2701.091744] wlan0: authenticated
[ 2701.091962] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2701.091967] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2701.093713] wlan0: associate with <MAC 'Maric' [AC1]> (try 1/3)
[ 2701.096177] wlan0: RX AssocResp from <MAC 'Maric' [AC1]> (capab=0x411 status=0 aid=2)
[ 2701.097041] wlan0: associated
[ 2707.777557] wlan0: deauthenticated from <MAC 'Maric' [AC1]> (Reason: 6)
[ 2723.318360] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2729.995512] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[ 2730.008126] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2733.681354] wlan0: authenticate with <MAC 'Maric' [AC1]>
[ 2733.682994] wlan0: send auth to <MAC 'Maric' [AC1]> (try 1/3)
[ 2733.684838] wlan0: authenticated
[ 2733.684939] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2733.684942] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2733.685903] wlan0: associate with <MAC 'Maric' [AC1]> (try 1/3)
[ 2733.692971] wlan0: RX AssocResp from <MAC 'Maric' [AC1]> (capab=0x411 status=0 aid=2)
[ 2733.694287] wlan0: associated
[ 2733.694311] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3016.637966] wlan0: deauthenticated from <MAC 'Maric' [AC1]> (Reason: 6)
[ 3016.707451] wlan0: authenticate with <MAC 'Maric' [AC1]>
[ 3016.709158] wlan0: send auth to <MAC 'Maric' [AC1]> (try 1/3)
[ 3016.710915] wlan0: authenticated
[ 3016.711198] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 3016.711205] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 3016.712613] wlan0: associate with <MAC 'Maric' [AC1]> (try 1/3)
[ 3016.715755] wlan0: RX AssocResp from <MAC 'Maric' [AC1]> (capab=0x411 status=0 aid=2)
[ 3016.716548] wlan0: associated
[ 3023.872517] wlan0: deauthenticated from <MAC 'Maric' [AC1]> (Reason: 6)
[ 3039.241782] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4559.724580] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[ 4559.737240] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4563.423455] wlan0: authenticate with <MAC 'Maric' [AC1]>
[ 4563.425130] wlan0: send auth to <MAC 'Maric' [AC1]> (try 1/3)
[ 4563.426997] wlan0: authenticated
[ 4563.427105] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 4563.427108] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 4563.429414] wlan0: associate with <MAC 'Maric' [AC1]> (try 1/3)
[ 4563.431974] wlan0: RX AssocResp from <MAC 'Maric' [AC1]> (capab=0x411 status=0 aid=2)
[ 4563.432972] wlan0: associated
[ 4563.432994] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############



```

---

### Post by dragan4 on 2015-08-21
Any help would mean a lot to me ...


thanks

---

### Post by dragan4 on 2015-08-22
whether it might be helpful to buy a usb wireless adapter?

thanks

---

