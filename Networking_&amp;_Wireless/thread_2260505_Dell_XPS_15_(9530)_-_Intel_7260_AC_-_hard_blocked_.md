---
title: "Dell XPS 15 (9530) - Intel 7260 AC - hard blocked on startup"
date: 2015-01-12
forum: Networking &amp; Wireless
---

### Post by christian49 on 2015-01-12
Hi!


I just posted this issue to [https://askubuntu.com/questions/562263/xps-15-9530-intel-7260-ac-not-working-hard-blocked](https://askubuntu.com/questions/562263/xps-15-9530-intel-7260-ac-not-working-hard-blocked) but did not get a reply, so I'm searching for help here now :)


My Wifi seems to be hard blocked when powering my notebook and could not unblocked via keyboard switch (Fn + print_screen) nor any other hardware key. Only if I go to suspend mode and waking up the Wifi is unblocked.
Also I noticed that the Bluetooth module has not been deteced when Wifi is hard blocked. After waking up from suspend Bluetooth is deteced. There is a similar thread about the Bluetooth problem ([http://ubuntuforums.org/showthread.php?t=2229997&page=2](http://ubuntuforums.org/showthread.php?t=2229997&page=2)). While the reason there was a broken card, I don't think the card is defective as Wifi and BT are working flawless in Windows 8.1.


Output of wireless-script after logon:
```



########## wireless info START ##########


Report from: 12 Jan 2015 18:14 CET +0100


Booted last: 12 Jan 2015 18:12 CET +0100


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


06:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c470]
    Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 06cb:0ac3 Synaptics, Inc. 
Bus 003 Device 003: ID 0bda:573c Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: nfc0: NFC
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


dell_laptop            18168  0 
dcdbas                 14928  1 dell_laptop
dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
iwlmvm                189813  0 
mac80211              630653  1 iwlmvm
iwlwifi               169932  1 iwlmvm
mxm_wmi                13021  1 nouveau
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
wmi                    19177  3 dell_wmi,mxm_wmi,nouveau


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


##### nm-tool ###########################


NetworkManager Tool


State: disconnected


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 


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


[[/etc/NetworkManager/system-connections/NETGEAR39]] (600 root)
[connection] id=NETGEAR39 | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR39 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Berlin (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


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


lo        Interface doesn't support scanning.


wlan0     Interface doesn't support scanning : Network is down


##### module infos ######################


[iwlmvm]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     D028925649B62FC6CDB3FDB
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)


[mac80211]
filename:       /lib/modules/3.13.0-43-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     446B3604A9C5461044DD691
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     72E4ECE7C2CBAA62E552DCE
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
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
filename:       /lib/modules/3.13.0-43-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
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
# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[    4.190827] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


########## wireless info END ############



```



Output of Wireless-Info after waking up from suspend mode:



```
########## wireless info START ##########


Report from: 12 Jan 2015 18:11 CET +0100


Booted last: 12 Jan 2015 18:09 CET +0100


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


06:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c470]
    Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 8087:07dc Intel Corp. 
Bus 003 Device 002: ID 06cb:0ac3 Synaptics, Inc. 
Bus 003 Device 003: ID 0bda:573c Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: nfc0: NFC
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


dell_laptop            18168  0 
dcdbas                 14928  1 dell_laptop
iwlmvm                189813  0 
mac80211              630653  1 iwlmvm
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
mxm_wmi                13021  1 nouveau
wmi                    19177  3 dell_wmi,mxm_wmi,nouveau


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7e7a:91ff:fe14:d0e8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:95 errors:0 dropped:0 overruns:0 frame:0
          TX packets:129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47306 (47.3 KB)  TX bytes:19191 (19.1 KB)


##### iwconfig ##########################


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"NETGEAR39"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: <MAC 'NETGEAR39' [AC1]>   
          Bit Rate=162 Mb/s   Tx-Power=22 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:25   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: wlan0  [NETGEAR39] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           121 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    NETGEAR39-5G:    Infra, <MAC 'NETGEAR39-5G' [AC6]>, Freq 5220 MHz, Rate 54 Mb/s, Strength 82 WPA2
    KDG-4BDB2:       Infra, <MAC 'KDG-4BDB2' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 85 WPA WPA2
    fgss:            Infra, <MAC 'fgss' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    AtelierWLAN:     Infra, <MAC 'AtelierWLAN' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    IndoorNet:       Infra, <MAC 'IndoorNet' [AC3]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 42 WPA2
    *NETGEAR39:      Infra, <MAC 'NETGEAR39' [AC1]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 75 WPA2
    HITRON-0710:     Infra, <MAC 'HITRON-0710' [AN7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    Dieter Zurwehme: Infra, <MAC 'Dieter Zurwehme' [AC7]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 39 WPA2
    Wurstfabrik:     Infra, <MAC 'Wurstfabrik' [AN9]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 7 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.8
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


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


[[/etc/NetworkManager/system-connections/NETGEAR39]] (600 root)
[connection] id=NETGEAR39 | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR39 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Berlin (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


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
          Current Frequency:2.422 GHz (Channel 3)


##### iwlist scan #######################


Channel occupancy:


      1   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      2   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.22 GHz (Channel 44)


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'NETGEAR39' [AC1]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR39"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009d8726ae27
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'fgss' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"fgss"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000038df00ef8
                    Extra: Last beacon: 5396ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'IndoorNet' [AC3]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"IndoorNet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000011f5bf842
                    Extra: Last beacon: 5176ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'KDG-4BDB2' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"KDG-4BDB2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002739bb8a85
                    Extra: Last beacon: 4992ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'AtelierWLAN' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"AtelierWLAN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000bcf4eebb1c6
                    Extra: Last beacon: 5132ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'NETGEAR39-5G' [AC6]>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR39-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000009d86e69023
                    Extra: Last beacon: 3724ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'Dieter Zurwehme' [AC7]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Dieter Zurwehme"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000371e6b558d
                    Extra: Last beacon: 5228ms ago


##### module infos ######################


[iwlmvm]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     D028925649B62FC6CDB3FDB
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)


[mac80211]
filename:       /lib/modules/3.13.0-43-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     446B3604A9C5461044DD691
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     72E4ECE7C2CBAA62E552DCE
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
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
filename:       /lib/modules/3.13.0-43-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
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
# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   66.585666] iwlwifi 0000:06:00.0: no hotplug settings from platform
[   66.586803] iwlwifi 0000:06:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[   66.744763] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[   66.801968] iwlwifi 0000:06:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[   66.814616] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   66.884968] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[   74.022806] wlan0: authenticate with <MAC 'NETGEAR39' [AC1]>
[   74.025062] wlan0: send auth to <MAC 'NETGEAR39' [AC1]> (try 1/3)
[   74.026879] wlan0: authenticated
[   74.028935] wlan0: associate with <MAC 'NETGEAR39' [AC1]> (try 1/3)
[   74.032668] wlan0: RX AssocResp from <MAC 'NETGEAR39' [AC1]> (capab=0x411 status=0 aid=6)
[   74.036271] wlan0: associated
[   74.036298] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   74.052751] wlan0: deauthenticating from <MAC 'NETGEAR39' [AC1]> by local choice (reason=2)
[   74.055578] wlan0: authenticate with <MAC 'NETGEAR39' [AC1]>
[   74.057163] wlan0: send auth to <MAC 'NETGEAR39' [AC1]> (try 1/3)
[   74.058975] wlan0: authenticated
[   74.060965] wlan0: associate with <MAC 'NETGEAR39' [AC1]> (try 1/3)
[   74.066851] wlan0: RX AssocResp from <MAC 'NETGEAR39' [AC1]> (capab=0x411 status=0 aid=6)
[   74.067865] wlan0: associated


########## wireless info END ############



```


I'm thankful for any reply.

---

### Post by jeremy31 on 2015-01-12
What does ```
modprobe -p dell_laptop
``` return?

---

### Post by christian49 on 2015-01-12
Hi,
thanks for your message. modprobe -p seems to be an invalid parameter, but I ran:

```
christian@christian-XPS-15-9530:~$ modprobe -p dell_laptopmodprobe: invalid option -- 'p'
christian@christian-XPS-15-9530:~$ sudo modinfo dell_laptop
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/platform/x86/dell-laptop.ko
license:        GPL
description:    Dell laptop driver
author:         Matthew Garrett <mjg@redhat.com>
srcversion:     A4E7D6B3072A8D8EE5E8FC7
alias:          dmi*:svn*DellComputerCorporation*:ct*8*:
alias:          dmi*:svn*DellInc.*:ct*9*:
alias:          dmi*:svn*DellInc.*:ct*8*:
depends:        dcdbas
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
sig_hashalgo:   sha512
parm:           force_rfkill:enable rfkill on non whitelisted models (bool)
christian@christian-XPS-15-9530:~$ sudo modprobe -r dell_laptop
christian@christian-XPS-15-9530:~$ sudo modprobe -v dell_laptop
insmod /lib/modules/3.13.0-43-generic/kernel/drivers/firmware/dcdbas.ko 
insmod /lib/modules/3.13.0-43-generic/kernel/drivers/platform/x86/dell-laptop.ko 
christian@christian-XPS-15-9530:~$ sudo modprobe --show-depends dell_laptop
insmod /lib/modules/3.13.0-43-generic/kernel/drivers/firmware/dcdbas.ko 
insmod /lib/modules/3.13.0-43-generic/kernel/drivers/platform/x86/dell-laptop.ko



```

Maybe this line is the issue?

parm:           force_rfkill:enable rfkill on non whitelisted models (bool)

---

### Post by jeremy31 on 2015-01-12
Try this when it is hard blocked```
sudo modprobe -r dell_laptop
``````
sudo rfkill unblock all
```

---

### Post by christian49 on 2015-01-12
It remains hard blocked :(

```
christian@christian-XPS-15-9530:~$ sudo modprobe -r dell_laptop[sudo] password for christian: 
christian@christian-XPS-15-9530:~$ sudo rfkill unblock all
christian@christian-XPS-15-9530:~$ sudo rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: nfc0: NFC
	Soft blocked: no
	Hard blocked: no



```

---

### Post by jeremy31 on 2015-01-12
Have you gone into BIOS and tried resetting to default?

---

### Post by christian49 on 2015-01-13
Yes, also done CMOS reset but still the same problem :(

---

### Post by christian49 on 2015-01-14
The odd thing is that Wifi is working after waking up from suspend mode. Does anyone know where to find the commands which run when waking up from suspend?

---

### Post by chili555 on 2015-01-14
Please try an experiment for me. Restart the machine and when the wireless doesn't work, do:```
sudo modprobe -r iwlmvm
sudo modprobe iwlmvm
rfkill list all
```Any change?

---

### Post by christian49 on 2015-01-14
Hi chili and thank you for your reply :)

Also no luck, wifi remains hard blocked. I also tried modprobe -r dell_wmi and tried to toggle Wifi with FN + Print-Screen but no change...

---

### Post by christian49 on 2015-02-04
Any other things I could try? Is there a way to find out what happens when waking up the notebook to filter the command which unblocks Wifi and run that at startup?

I know it's not a "serious" issue but it's very annoying to suspend and wake up every time I boot Ubuntu...

---

### Post by chili555 on 2015-02-04
> Also I noticed that the Bluetooth module has not been deteced when Wifi is hard blocked.Let's work on this and see if we help it at all. Reboot so that the wireless and bluetooth is not working. Run:```
echo before: > wifi.txt
lsmod >> wifi.txt
```Suspend and resume so that wireless is working and run:```
echo after: >> wifi.txt
lsmod >> wifi.txt
```Find the text file wifi.txt and paste it here and give us the link in your reply: [http://paste.ubuntu.com](http://paste.ubuntu.com)

Thanks.

---

### Post by christian49 on 2015-02-04
Here we go :) [http://paste.ubuntu.com/10061478/](http://paste.ubuntu.com/10061478/)

---

### Post by chili555 on 2015-02-04
We see that the module *btusb* is loaded after suspend but not before. Let's get it to load on boot and see if it helps:```
sudo -i
echo btusb  >>  /etc/modules
exit
```Reboot and let us hear your report.

EDIT: I also note that the modules *ccm* and *ctr *are loaded after but not before. While I am tempted to load them in to /etc/modules also, I know nothing whatever about either of them. Let's see how it goes before we take further steps.

---

### Post by christian49 on 2015-02-05
First I did that with btusb, rebooted - no change. Then I also inserted ccm and ctr to /etc/modules and rebooted - also no change. Wifi is still not working, also Bluetooth is not available (nor in rfkill list ). 
Report after inserting the three modules: [http://paste.ubuntu.com/10070709/](http://paste.ubuntu.com/10070709/) 

Now the same modules are loaded but I realized there are some differences in the "Used" column. There are these modules:

[TABLE="width: 336"]
[TR]
[TD]Module[/TD]
[TD]Used[/TD]
[TD]Used after[/TD]
[/TR]
[TR]
[TD]aesni_intel[/TD]
[TD="align: right"]0[/TD]
[TD="align: right"]5[/TD]
[/TR]
[TR]
[TD]bluetooth[/TD]
[TD="align: right"]11[/TD]
[TD="align: right"]22[/TD]
[/TR]
[TR]
[TD]ccm[/TD]
[TD="align: right"]0[/TD]
[TD="align: right"]2[/TD]
[/TR]
[TR]
[TD]ctr[/TD]
[TD="align: right"]0[/TD]
[TD="align: right"]2[/TD]
[/TR]
[TR]
[TD]rfcomm[/TD]
[TD="align: right"]0[/TD]
[TD="align: right"]8[/TD]
[/TR]
[/TABLE]

Does this help?

---

### Post by chili555 on 2015-02-05
I have worked on many issues over the years where wireless won't start upon resume. The solution I offer is to tell the system to load the driver on resuming. As a matter of fact, the driver in question is quite often iwlwifi: [http://ubuntuforums.org/showthread.php?t=2004690&highlight=resume](http://ubuntuforums.org/showthread.php?t=2004690&highlight=resume)

I wonder if there is something about the module being dropped (upon suspend) and reloaded (upon resume) that gets your wireless going. Let's ask the system to drop the driver and reload it during the boot process and see if it helps:```
gksudo gedit /etc/rc.local
```Use nano or kate or leafpad if you don't have the text editor gedit. Add these lines right above exit 0:```
modprobe -r iwlwifi
sleep 3
modprobe iwlwifi
```Proofread carefully, save and close the text editor. Reboot and show us:```
rfkill list all
```

---

### Post by christian49 on 2015-02-05
Added these lines above exit 0, rebooted - and it's still hard blocked :(

```

christian@christian-XPS-15-9530:~$ rfkill list
1: nfc0: NFC
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

dmesg output:
```

[   44.112150] usb 1-9: new full-speed USB device number 4 using xhci_hcd
[   44.209847] iwlwifi 0000:06:00.0: L1 Enabled - LTR Enabled
[   44.210114] iwlwifi 0000:06:00.0: L1 Enabled - LTR Enabled
[   44.224482] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   44.241459] usb 1-9: New USB device found, idVendor=8087, idProduct=07dc
[   44.241462] usb 1-9: New USB device strings: Mfr=0, Product=0, SerialNumber=0

```

I believe it has something to do with this XHCI thing. I read something about this as a BIOS setting but in an unlocked BIOS. Maybe I will try some experiments on this one if there is no more thing I could try in Ubuntu

---

### Post by jeremy31 on 2015-02-05
> **christian49 said:**
> Added these lines above exit 0, rebooted - and it's still hard blocked :(

```

christian@christian-XPS-15-9530:~$ rfkill list
1: nfc0: NFC
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

dmesg output:
```

[   44.112150] usb 1-9: new full-speed USB device number 4 using xhci_hcd
[   44.209847] iwlwifi 0000:06:00.0: L1 Enabled - LTR Enabled
[   44.210114] iwlwifi 0000:06:00.0: L1 Enabled - LTR Enabled
[   44.224482] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   44.241459] usb 1-9: New USB device found, idVendor=8087, idProduct=07dc
[   44.241462] usb 1-9: New USB device strings: Mfr=0, Product=0, SerialNumber=0

```

I believe it has something to do with this XHCI thing. I read something about this as a BIOS setting but in an unlocked BIOS. Maybe I will try some experiments on this one if there is no more thing I could try in Ubuntu

I doubt it has anything to do with XHCI but if you want to try something ```
echo "blacklist btusb" | sudo tee /etc/modprobe.d/btusb.conf
``` as btusb will load firmware to the intel bluetooth device 8087:07dc and that device likely uses XHCI, reboot to see.  If nothing is gained you can reverse with ```
sudo rm /etc/modprobe.d/btusb.conf
```

---

### Post by chili555 on 2015-02-05
Did you notice this, young Jeremy?```
christian@christian-XPS-15-9530:~$ sudo modinfo dell_laptop
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/platform/x86/dell-laptop.ko
license:        GPL
description:    Dell laptop driver
author:         Matthew Garrett <mjg@redhat.com>
srcversion:     A4E7D6B3072A8D8EE5E8FC7
alias:          dmi*:svn*DellComputerCorporation*:ct*8*:
alias:          dmi*:svn*DellInc.*:ct*9*:
alias:          dmi*:svn*DellInc.*:ct*8*:
depends:        dcdbas
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
sig_hashalgo:   sha512
[COLOR="#FF0000"]parm:           force_rfkill:enable rfkill on non whitelisted models (bool)[/COLOR]
```Let's see what the parameter is now and reverse it:```
cat /sys/module/dell_laptop/parameters/force_rfkill
```I've been scanning the .c code and am a bit unsure what does what. Usually 'bool' for boolean means TRUE or FALSE or Y or N or... Let's see what it is now and reverse it.

---

### Post by christian49 on 2015-02-06
Blacklisting btusb did not do the trick :(

cat /sys/module/dell_laptop/parameters/force_rfkill returns "N" before and "N" after suspending

---

### Post by jeremy31 on 2015-02-06
Can you try FN + ALT + PRTSC to see if it can be enabled or possibly just PRTSC
The developers trashed the whole rfkill thing a few years ago but reverted the changes, it may be possible to build dell_laptop without the rfkill [http://kernel.ubuntu.com/git?p=ubuntu/linux.git;a=commitdiff;h=a6c2390cd6d2083d27a2359658e08f2d3df375ac](http://kernel.ubuntu.com/git?p=ubuntu/linux.git;a=commitdiff;h=a6c2390cd6d2083d27a2359658e08f2d3df375ac)

---

### Post by chili555 on 2015-02-06
Please try:```
sudo -i
echo "options dell_laptop force_rfkill=Y"  >  /etc/modprobe.d/dell_laptop.conf
exit 
```Reboot with your fingers crossed!```
rfkill list all
```

---

### Post by christian49 on 2015-02-06
I tried all possible key-combinations with Fn, printscreen and all other F-Keys but none unblocked Wifi.
Adding the force_rfkill=Y option to dell_laptop configuration make two new entries in rfkill list appear: dell-wifi and dell-bluetooth. Both are hard blocked, too, and can not be activated doing unblock all or any key-combination.

So the state is now:

```
christian@christian-XPS-15-9530:~$ rfkill list
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
3: nfc0: NFC
    Soft blocked: no
    Hard blocked: no
4: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

After suspend and waking up the Wireless LAN option then is not hard blocked anymore but both dell-options still are: 

```
christian@christian-XPS-15-9530:~$ rfkill list
4: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
5: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
6: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
7: nfc0: NFC
    Soft blocked: no
    Hard blocked: no
8: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

and could not be unblocked so I did rmmod dell-laptop and the Wifi worked...but only after suspending, again.

---

### Post by chili555 on 2015-02-07
Certainly, our experimental driver parameter is not helping, so let's remove it:```
sudo rm /etc/modprobe.d/dell_laptop.conf
```Unload and reload the module:```
sudo modprobe -r dell_laptop
sudo modprobe dell_laptop
```I have suggested every method or option that Google and I can conceive. Aside from two more steps, I regret that I have no other suggestions.

First, download and burn the DVD for the latest build of Ubuntu 15.04: [http://cdimage.ubuntu.com/daily-live/20150207/](http://cdimage.ubuntu.com/daily-live/20150207/) Run the live session and see if the wireless key combination now works as expected. If so, I'd see if the newest version meets your needs otherwise and install it.

Second, I suggest you register and file a bug against* dell_laptop*: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

I regret I haven't any other suggestions.

---

### Post by jeremy31 on 2015-02-07
If you file a bug against dell_laptop, then info from ```
sudo cat /sys/kernel/debug/dell_laptop/rfkill
``` before and after suspend might help

---

### Post by christian49 on 2015-02-07
Chili and Jeremy, let me say Thank you for your continous help.

I will try the new Ubuntu version with a Live-Build and see if it will work. If not I will try to reset the CMOS again (not an easy operation when the battery is not detachable). 
If there is no solution I will file a bug against dell_laptop, call Dell and/or wait for a BIOS update that may solve the problem (I saw that the Precision M3800 which is mainly the same build like my XPS 15 is now supported with Ubuntu so maybe they will support me ;) ).

Next two weeks are full of exams for me, so the next reply of mine will take a month or more ;)

---

### Post by DiCon on 2015-03-23
I am seeing the same problem on an XPS 12 (9Q33, "2nd gen", the Haswell version). Blacklisting modules or adding module parameters leads to exactly the same changes as reported for the XPS 15. So, I'll add my story, hoping that some detail might give somebody an idea...

I am living with this problem for over a year now. Strangely, WiFi was working at first, but stopped working when I updated my BIOS to A03 and since then the only way to enable WiFi is by going to standby first. I have tried every BIOS version up to the recent A07, but cannot downgrade. The WiFi (and its switch) is working great in Win 8.1.

Additionally, I can report that the same issue exists on Console OS (Android for PC). On a fresh install I have to go to standby and enable airplane mode. The latter might be to trigger some Android stuff as it might not be expecting the "sudden appearance" of a WiFi device, but who knows...

Although the problem first occured after a BIOS update, I do not believe that it is the BIOS itself as the XPS 12 is one of few convertibles supported by Console OS and they actually recommend updating to A07 before installing. So maybe the update to A03 changed the boot-up state of the WiFi and there is just no option to set it back?

---

### Post by stefano27 on 2015-04-03
Hi guys, i have a Dell XPS 15 9530, and the wifi on my pc doesn't work before suspend and resume. I started with A05 bios version and now i have A07, but the problem is the same. I tried many solutions without result and now i hope in you and in the community to resolve my problem. I contacted Dell, but the machine has no official support of Linux System and i did not receive support.


I am sorry for my not brilliant english


I wait for your answer, Thank

---

### Post by chili555 on 2015-04-03
> **stefano27 said:**
> Hi guys, i have a Dell XPS 15 9530, and the wifi on my pc doesn't work before suspend and resume. I started with A05 bios version and now i have A07, but the problem is the same. I tried many solutions without result and now i hope in you and in the community to resolve my problem. I contacted Dell, but the machine has no official support of Linux System and i did not receive support.


I am sorry for my not brilliant english


I wait for your answer, ThankYour English is very understandable; there is no problem.

Did you try this technique? [http://ubuntuforums.org/showthread.php?t=2004690&p=12031410#post12031410](http://ubuntuforums.org/showthread.php?t=2004690&p=12031410#post12031410) This assumes your driver is iwlwifi. You can confirm it with:```
sudo lshw -C network
```

---

### Post by stefano27 on 2015-04-03
thank very much for the answer.
I tried your posted solution, but that did not work for me.
I don't understand why...](*,)](*,)

---

### Post by chili555 on 2015-04-03
> **stefano27 said:**
> thank very much for the answer.
I tried your posted solution, but that did not work for me.
I don't understand why...](*,)](*,)Is your driver iwlwifi? What is it?

---

### Post by stefano27 on 2015-04-11
Yes, my loaded driver is iwlwifi. I tried with other linux distribution, but the problem is the same. I have lost all hope :(:(

---

### Post by christian49 on 2015-04-14
Hi stefano,

maybe you could post the output of the wireless script so we have a better view on your case ;) see [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) 

To update my case: I ran sudo cat /sys/kernel/debug/dell_laptop/rfkill before and after suspending, output: [http://paste.ubuntu.com/10821094/](http://paste.ubuntu.com/10821094/) 

It's exactly the same - oddly after resuming it says that Wifi is still blocked, but it isn't.

Also tried Ubuntu 15.04 but same issue. I will file a bug against dell_laptop and see what happens. Thanks so far!

---

### Post by stefano27 on 2015-04-20
> **christian49 said:**
> Hi stefano,

maybe you could post the output of the wireless script so we have a better view on your case ;) see [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) 

To update my case: I ran sudo cat /sys/kernel/debug/dell_laptop/rfkill before and after suspending, output: [http://paste.ubuntu.com/10821094/](http://paste.ubuntu.com/10821094/) 

It's exactly the same - oddly after resuming it says that Wifi is still blocked, but it isn't.

Also tried Ubuntu 15.04 but same issue. I will file a bug against dell_laptop and see what happens. Thanks so far!

Thank Christian for your help!
I followed your instructions, but the wifi is blocked!
This is the result of command: cat /sys/kernel/debug/dell_laptop/rfkill before and after suspending: [http://paste.ubuntu.com/10856681/](http://paste.ubuntu.com/10856681/)
This is the result of script wireless_script. I tried on fedora 21, the result is the same of ubuntu 15.04: [http://paste.ubuntu.com/10856727/](http://paste.ubuntu.com/10856727/)
I am waiting for your new solution, thanks for all.

---

### Post by DiCon on 2015-11-03
After 2 years (t-w-o!) living with this bug on my XPS 12, it has finally been resolved for me by the 4.2 kernel. I suspect, that the new dell_rbtn module for the air plane switch did the trick!

After dancing and singing for a while, I thought I should share this on all the rfkill-before-standby threads. Maybe some of you have already found this (why did nobody report it then?), but to those stuck with an older kernel: Try updating!

---

### Post by jeremy31 on 2015-11-03
File a bug report, start @ [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Do all the initial things from an Ubuntu kernel, then state it is fixed upstream in 4.2 and the fix might get merged into an Ubuntu kernel and help others

---

