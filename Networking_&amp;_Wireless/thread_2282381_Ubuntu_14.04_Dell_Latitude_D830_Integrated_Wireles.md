---
title: "Ubuntu 14.04: Dell Latitude D830 Integrated Wireless Issues"
date: 2015-06-13
forum: Networking &amp; Wireless
---

### Post by daniel_duncan2 on 2015-06-13
Hello, everyone. Before I state the issue, I would like to apologize in advance if I have missed something that would either solve or close this issue for me. I was up very late last night, and everything I tried is a blur.

Now that's out of the way, my problem: I am running **Ubuntu 14.04.2 LTS** with kernel version **3.16.0-40-generic** on a Dell Latitude D830. Whenever I try to use WiFi, it will connect for a few minutes, then disconnect. Sometimes it will reconnect and disconnect repeatedly, but most of the time, it stops completely, as it believes the wireless card is hard-blocked (the physical switch is ON), and will not work again until I reboot the system.  I believe it to be known that there is some kind of issue with the wireless card it has: **Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61). **However, due to my stubbornness, I am intent on being sure that it either can or can not work correctly. Any help would be greatly appreciated.

Wireless information:
```


########## wireless info START ##########


Report from: 13 Jun 2015 20:32 EDT -0400


Booted last: 13 Jun 2015 19:54 EDT -0400


Script from: 21 May 2015 09:10 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.16.0-40-generic #54~14.04.1-Ubuntu SMP Wed Jun 10 17:30:06 UTC 2015 i686 i686 i686 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
    Subsystem: Dell Device [1028:01fe]
    Kernel driver in use: tg3


0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)
    Subsystem: Intel Corporation Device [8086:1120]
    Kernel driver in use: iwl4965


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 003: ID 0483:2016 STMicroelectronics Fingerprint Reader
Bus 007 Device 004: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader
Bus 007 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 413c:0058 Dell Computer Corp. Port Replicator
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 007: ID 413c:8140 Dell Computer Corp. Wireless 360 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


##### rfkill ############################


1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
8: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


dell_wmi               12665  0 
sparse_keymap          13708  1 dell_wmi
dell_laptop            17808  0 
dcdbas                 14448  1 dell_laptop
iwl4965               106879  0 
iwlegacy               87977  1 iwl4965
mac80211              559100  2 iwl4965,iwlegacy
cfg80211              418839  3 iwl4965,iwlegacy,mac80211
mxm_wmi                12893  1 nouveau
wmi                    18689  3 dell_wmi,mxm_wmi,nouveau


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.125  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fe95:2b89/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16208 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27946 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1535108 (1.5 MB)  TX bytes:6213306 (6.2 MB)
          Interrupt:17 


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1189 errors:0 dropped:0 overruns:0 frame:0
          TX packets:121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:82095 (82.0 KB)  TX bytes:20922 (20.9 KB)


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root      1090     1  0 19:54 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.125
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl4965
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


[[/etc/NetworkManager/system-connections/Duncan Network (5 GHz)]] (600 root)
[connection] id=Duncan Network (5 GHz) | type=802-11-wireless
[802-11-wireless] ssid=Duncan Network (5 GHz) | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Duncan Network]] (600 root)
[connection] id=Duncan Network | type=802-11-wireless
[802-11-wireless] ssid=Duncan Network | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/New_York (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


lo        no frequency information.


eth0      no frequency information.


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


##### iwlist scan #######################


wlan0     Interface doesn't support scanning : Network is down


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


##### module infos ######################


[iwl4965]
filename:       /lib/modules/3.16.0-40-generic/kernel/drivers/net/wireless/iwlegacy/iwl4965.ko
firmware:       iwlwifi-4965-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi 4965 driver for Linux
srcversion:     5C873B33796CE1F28CF6FFA
depends:        iwlegacy,cfg80211,mac80211
intree:         Y
vermagic:       3.16.0-40-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        E8:8E:08:C3:A6:C2:C0:B6:35:3A:D2:65:F7:9C:CE:8E:1C:F5:08:4B
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0 [disabled]) (int)
parm:           fw_restart:restart firmware in case of error (int)


[iwlegacy]
filename:       /lib/modules/3.16.0-40-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     1FA10C0B834AAF4AE219899
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-40-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        E8:8E:08:C3:A6:C2:C0:B6:35:3A:D2:65:F7:9C:CE:8E:1C:F5:08:4B
sig_hashalgo:   sha512
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)


[mac80211]
filename:       /lib/modules/3.16.0-40-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     376BFDE8E6207B0AAA6339B
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-40-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        E8:8E:08:C3:A6:C2:C0:B6:35:3A:D2:65:F7:9C:CE:8E:1C:F5:08:4B
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.16.0-40-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     33ED2C1448F5AEDBE7AF59E
depends:        
intree:         Y
vermagic:       3.16.0-40-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        E8:8E:08:C3:A6:C2:C0:B6:35:3A:D2:65:F7:9C:CE:8E:1C:F5:08:4B
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[iwl4965]
11n_disable: 0
amsdu_size_8K: 0
fw_restart: 1
queues_num: 0
swcrypto: 0


[iwlegacy]
bt_coex_active: Y
led_mode: 0


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


lp


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
# PCI device 0x14e4:0x1673 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x4229 (iwl4965)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[  365.952557] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  860.631434] iwl4965 0000:0c:00.0: RF_KILL bit toggled to disable radio.
[  860.634857] wlan0: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)
[  860.635079] iwl4965 0000:0c:00.0: Not sending command - RF KILL
[  860.635088] iwl4965 0000:0c:00.0: Error sending C_REM_STA: enqueue_hcmd failed: -5
[  860.635097] iwl4965 0000:0c:00.0: Error removing station <MAC address>
[  860.635348] iwl4965 0000:0c:00.0: Not sending command - RF KILL
[  860.635356] iwl4965 0000:0c:00.0: Error sending C_QOS_PARAM: enqueue_hcmd failed: -5
[  860.635366] iwl4965 0000:0c:00.0: Not sending command - RF KILL
[  860.635373] iwl4965 0000:0c:00.0: Error sending C_RXON: enqueue_hcmd failed: -5
[  860.635381] iwl4965 0000:0c:00.0: Error setting new RXON (-5)
[  860.635388] iwl4965 0000:0c:00.0: Not sending command - RF KILL
[  860.635394] iwl4965 0000:0c:00.0: Error sending C_RXON_ASSOC: enqueue_hcmd failed: -5
[  860.635406] iwl4965 0000:0c:00.0: Not sending command - RF KILL
[  860.635413] iwl4965 0000:0c:00.0: Error sending C_RXON_ASSOC: enqueue_hcmd failed: -5
[  860.635428] iwl4965 0000:0c:00.0: Not sending command - RF KILL
[  860.635434] iwl4965 0000:0c:00.0: Error sending C_RXON: enqueue_hcmd failed: -5
[  860.635440] iwl4965 0000:0c:00.0: Error setting new RXON (-5)
[  860.635447] iwl4965 0000:0c:00.0: Not sending command - RF KILL
[  860.635453] iwl4965 0000:0c:00.0: Error sending C_QOS_PARAM: enqueue_hcmd failed: -5
[  860.635487] iwl4965 0000:0c:00.0: Not sending command - RF KILL
[  860.635493] iwl4965 0000:0c:00.0: Error sending C_LEDS: enqueue_hcmd failed: -5
[  860.635517] iwl4965 0000:0c:00.0: Not sending command - RF KILL
[  860.635524] iwl4965 0000:0c:00.0: Error sending C_RXON: enqueue_hcmd failed: -5
[  860.635530] iwl4965 0000:0c:00.0: Error setting new RXON (-5)
[  860.637511] iwl4965 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[  860.637520] iwl4965 0000:0c:00.0: On demand firmware reload
[  860.722780] iwl4965 0000:0c:00.0: RF_KILL bit toggled to disable radio.
[  860.726231] iwl4965 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[  860.726236] iwl4965 0000:0c:00.0: On demand firmware reload
[  860.732099] iwl4965 0000:0c:00.0: RF_KILL bit toggled to disable radio.
[  860.736185] iwl4965 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[  860.736189] iwl4965 0000:0c:00.0: On demand firmware reload
[  860.807485] iwl4965 0000:0c:00.0: RF_KILL bit toggled to disable radio.
[  860.814601] iwl4965 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[  860.814613] iwl4965 0000:0c:00.0: On demand firmware reload
[  860.843175] iwl4965 0000:0c:00.0: RF_KILL bit toggled to disable radio.
[  860.848303] iwl4965 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[  860.848307] iwl4965 0000:0c:00.0: On demand firmware reload
[  860.853442] iwl4965 0000:0c:00.0: RF_KILL bit toggled to disable radio.
[  860.858603] iwl4965 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[  860.858609] iwl4965 0000:0c:00.0: On demand firmware reload
[  860.878307] iwl4965 0000:0c:00.0: RF_KILL bit toggled to disable radio.
[  860.882309] iwl4965 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[  860.882315] iwl4965 0000:0c:00.0: On demand firmware reload
[  860.888512] iwl4965 0000:0c:00.0: RF_KILL bit toggled to disable radio.
[  860.893637] iwl4965 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[  860.893642] iwl4965 0000:0c:00.0: On demand firmware reload
[  860.919755] iwl4965 0000:0c:00.0: RF_KILL bit toggled to disable radio.
[  860.924931] iwl4965 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[  860.924939] iwl4965 0000:0c:00.0: On demand firmware reload
[  860.964171] iwl4965 0000:0c:00.0: RF_KILL bit toggled to disable radio.
[  860.970112] iwl4965 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[  860.970119] iwl4965 0000:0c:00.0: On demand firmware reload
[  860.976275] iwl4965 0000:0c:00.0: RF_KILL bit toggled to disable radio.
[  860.981438] iwl4965 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[  860.981442] iwl4965 0000:0c:00.0: On demand firmware reload
[  860.992766] iwl4965 0000:0c:00.0: RF_KILL bit toggled to disable radio.
[  861.039341] iwl4965 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[  861.039374] iwl4965 0000:0c:00.0: On demand firmware reload
[  861.113281] iwl4965 0000:0c:00.0: RF_KILL bit toggled to disable radio.
[  861.118211] iwl4965 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[  861.118215] iwl4965 0000:0c:00.0: On demand firmware reload
[  861.124326] iwl4965 0000:0c:00.0: RF_KILL bit toggled to disable radio.
[  861.129512] iwl4965 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[  861.129517] iwl4965 0000:0c:00.0: On demand firmware reload
[  861.135641] iwl4965 0000:0c:00.0: RF_KILL bit toggled to disable radio.
[  861.136044] iwl4965 0000:0c:00.0: Error sending C_ADD_STA: time out after 500ms.
[  861.136052] wlan0: failed to remove key (1, <MAC address>) from hardware (-110)


########## wireless info END ############
```

EDIT: Attention, those who may be reading: I seem to have solved my issue. The solution was very simple, and I only missed it through my own ignorance. I took the appropriate driver from this page ( [https://wireless.wiki.kernel.org/en/users/drivers/iwlegacy](https://wireless.wiki.kernel.org/en/users/drivers/iwlegacy) ), and even though I believed them to be the same, I replaced the current driver with the downloaded one. After rebooting, my problem seemed to be gone. I hope this helps anyone having a similar problem.

---

