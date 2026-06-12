---
title: "ATH9K - I cant get wifi connected after clean install of Ubuntu 18."
date: 2018-10-19
forum: Networking &amp; Wireless
---

### Post by prototempus on 2018-10-19
Hello all, thanks for your help.

I've been trying in vain to get Wifi working on my server. It uses ATH9K and can scan okay but I can't seem to get it connected. I had it working before when I removed it from /etc/interfaces and used nmtui, but can do it with netplan.

I've tried all different setups in my netplan config and nothing seems to get it working. I'm new-ish to Ubuntu so maybe there is just something I am not seeing.

Here is the results of wireless-info script:
```

########## wireless info START ##########

Report from: 19 Oct 2018 16:21 PDT -0700

Booted last: 19 Oct 2018 00:00 PDT -0700

Script from: 06 Oct 2018 06:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 4.15.0-36-generic #39-Ubuntu SMP Mon Sep 24 16:19:09 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro

##### desktop ###########################

sed: can't read /home/chris/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

02:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
    Subsystem: Lite-On Communications Inc AR9462 Wireless Network Adapter [11ad:6621]
    Kernel driver in use: ath9k

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: Micro-Star International Co., Ltd. [MSI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1462:7596]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 04ca:3006 Lite-On Technology Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
6: phy5: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

'mokutil' is not installed (package "mokutil").

##### lsmod #############################

ath9k                 151552  0
ath3k                  20480  0
ath9k_common           36864  1 ath9k
ath9k_hw              471040  2 ath9k,ath9k_common
ath                    28672  3 ath9k_hw,ath9k,ath9k_common
mac80211              778240  1 ath9k
bluetooth             548864  6 btrtl,btintel,btbcm,ath3k,btusb
wmi_bmof               16384  0
cfg80211              622592  4 mac80211,ath9k,ath,ath9k_common
wmi                    24576  1 wmi_bmof

##### interfaces ########################

##### ifconfig ##########################

enp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.137.34  netmask 255.255.255.0  broadcast 192.168.137.255
        inet6 fe80::6e62:6dff:fe9c:d6e3  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 5669  bytes 1614332 (1.6 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 7090  bytes 1472340 (1.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 746  bytes 48216 (48.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 746  bytes 48216 (48.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp2s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

lo        no wireless extensions.

enp3s0    no wireless extensions.

wlp2s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=3 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.137.1   0.0.0.0         UG    100    0        0 enp3s0
192.168.137.0   0.0.0.0         255.255.255.0   U     0      0        0 enp3s0
192.168.137.1   0.0.0.0         255.255.255.255 UH    100    0        0 enp3s0

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
search mshome.net

##### network managers ##################

Installed:

    None found.

Running:

root       808     1  0 Oct17 ?        00:00:10 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

NetworkManager is not installed (package "network-manager").

##### NetworkManager.state ##############

cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory

##### NetworkManager config #############

[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3

[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile
[ifupdown]
managed=false
[device]
wifi.scan-rand-mac-address=0

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=Telus6118
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-netcfg.yaml]
network:
  version: 2
  renderer: networkd
  ethernets:
    enp3s0:
      dhcp4: true
      dhcp6: true

[/etc/netplan/03-wireless.yaml]
network:
  version: 2
  renderer: networkd
  
  wifis:
    wlp2s0:
      dhcp4: true
      dhcp6: false
      access-points:
        "Telus6118": 
          password: "f843crkcbr"

##### iw reg get ########################

Region: America/Vancouver (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp3s0    no frequency information.

wlp2s0    32 channels in total; available frequencies :
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

enp3s0    Interface doesn't support scanning.

Channel occupancy:

      3   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.18 GHz (Channel 36)
      2   APs on   Frequency:5.765 GHz

wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'junglejim' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"junglejim"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007ba06e7f8a
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'junglejim-guest' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:off
                    ESSID:"junglejim-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007ba06e4424
                    Extra: Last beacon: 28ms ago
          Cell 03 - Address: <MAC 'rpm' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"rpm"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003b6cda6238
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'TELUS6118' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"TELUS6118"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009eeb5ad8ba
                    Extra: Last beacon: 2772ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'TELUS6118' [AC5]>
                    Channel:153
                    Frequency:5.765 GHz
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"TELUS6118"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004994fa82389
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC '' [AC6]>
                    Channel:153
                    Frequency:5.765 GHz
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004994fa85009
                    Extra: Last beacon: 388ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'TELUS5028' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"TELUS5028"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000087fdf785b
                    Extra: Last beacon: 2872ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'junglejim-guest' [AC8]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:"junglejim-guest"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007ba08a9006
                    Extra: Last beacon: 7104ms ago

##### module infos ######################

[ath9k]
filename:       /lib/modules/4.15.0-36-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     F4328CE52BA6067DD4EDE7B
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
retpoline:      Y
intree:         Y
name:           ath9k
vermagic:       4.15.0-36-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           led_active_high:Invert LED polarity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)
parm:           use_msi:Use MSI instead of INTx if possible (int)

[ath3k]
filename:       /lib/modules/4.15.0-36-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     36C0F7AEF3B569F1798216D
depends:        bluetooth
retpoline:      Y
intree:         Y
name:           ath3k
vermagic:       4.15.0-36-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[ath9k_common]
filename:       /lib/modules/4.15.0-36-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     0340C3244B71A3EDEF1E37E
depends:        ath9k_hw,cfg80211,ath
retpoline:      Y
intree:         Y
name:           ath9k_common
vermagic:       4.15.0-36-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[ath9k_hw]
filename:       /lib/modules/4.15.0-36-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     D5984DFEF6457DDB060988E
depends:        ath
retpoline:      Y
intree:         Y
name:           ath9k_hw
vermagic:       4.15.0-36-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[ath]
filename:       /lib/modules/4.15.0-36-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     555BBBB9D4FCA58A05E7C0D
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           ath
vermagic:       4.15.0-36-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[mac80211]
filename:       /lib/modules/4.15.0-36-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     76870094CC01F4AC06240B7
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-36-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.15.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     62FD05DCC5AEEA290640C3D
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-36-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
led_active_high: -1
nohwcrypt: 0
ps_enable: 0
use_chanctx: 0
use_msi: 0

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mdadm.conf]
options md_mod start_ro=1

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   21.310160] ath: EEPROM regdomain: 0x6a
[   21.310162] ath: EEPROM indicates we should expect a direct regpair map
[   21.310164] ath: Country alpha2 being used: 00
[   21.310164] ath: Regpair used: 0x6a
[   21.658893] ath9k 0000:02:00.0 wlp2s0: renamed from wlan0
[   21.696480] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[150333.086584] ath: EEPROM regdomain: 0x6a
[150333.086586] ath: EEPROM indicates we should expect a direct regpair map
[150333.086588] ath: Country alpha2 being used: 00
[150333.086589] ath: Regpair used: 0x6a
[150333.098148] ath9k 0000:02:00.0 wlp2s0: renamed from wlan0
[150333.125819] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 3 times)
[150502.677580] ath: EEPROM regdomain: 0x6a
[150502.677582] ath: EEPROM indicates we should expect a direct regpair map
[150502.677584] ath: Country alpha2 being used: 00
[150502.677584] ath: Regpair used: 0x6a
[150502.690275] ath9k 0000:02:00.0 wlp2s0: renamed from wlan0
[150502.717199] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 3 times)
[151152.659359] ath: EEPROM regdomain: 0x6a
[151152.659361] ath: EEPROM indicates we should expect a direct regpair map
[151152.659363] ath: Country alpha2 being used: 00
[151152.659364] ath: Regpair used: 0x6a
[151152.674368] ath9k 0000:02:00.0 wlp2s0: renamed from wlan0
[151152.702099] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 3 times)
[151220.737110] ath: EEPROM regdomain: 0x6a
[151220.737112] ath: EEPROM indicates we should expect a direct regpair map
[151220.737114] ath: Country alpha2 being used: 00
[151220.737114] ath: Regpair used: 0x6a
[151220.741120] ath9k 0000:02:00.0 wlp2s0: renamed from wlan0
[151220.771994] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 3 times)
[152131.172165] ath: EEPROM regdomain: 0x6a
[152131.172167] ath: EEPROM indicates we should expect a direct regpair map
[152131.172169] ath: Country alpha2 being used: 00
[152131.172170] ath: Regpair used: 0x6a
[152131.180721] ath9k 0000:02:00.0 wlp2s0: renamed from wlan0
[152131.201679] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 3 times)

########## wireless info END ############
```

Here is the results of another command that was helpful in other thread I found with similar issues:
```

chris@serverr:~$ systemctl list-units | grep -iE 'net|dhcp|wicd|conn'
  sys-devices-pci0000:00-0000:00:04.0-0000:02:00.0-net-wlp2s0.device                       loaded active plugged   AR9462 Wireless Network Adapter
  sys-devices-pci0000:00-0000:00:05.0-0000:03:00.0-net-enp3s0.device                       loaded active plugged   RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
  sys-subsystem-net-devices-enp3s0.device                                                  loaded active plugged   RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
  sys-subsystem-net-devices-wlp2s0.device                                                  loaded active plugged   AR9462 Wireless Network Adapter
  sys-fs-fuse-connections.mount                                                            loaded active mounted   FUSE Control File System
&#9679; netplan-wpa@wlp2s0.service                                                               loaded failed failed    WPA supplicant for netplan wlp2s0
  networkd-dispatcher.service                                                              loaded active running   Dispatcher daemon for systemd-networkd
&#9679; NetworkManager.service                                                                   masked active running   NetworkManager.service
&#9679; systemd-networkd-wait-online.service                                                     loaded failed failed    Wait for Network to be Configured
  systemd-networkd.service                                                                 loaded active running   Network Service
  systemd-resolved.service                                                                 loaded active running   Network Name Resolution
  systemd-timesyncd.service                                                                loaded active running   Network Time Synchronization
  system-netplan\x2dwpa.slice                                                              loaded active active    system-netplan\x2dwpa.slice
  network-online.target                                                                    loaded active active    Network is Online
  network-pre.target                                                                       loaded active active    Network (Pre)
  network.target                                                                           loaded active active    Network
  nss-lookup.target                                                                        loaded active active    Host and Network Name Lookups

```

Please let me know if you'd like me to try anything and i'll get back to you right away!

---

### Post by chili555 on 2018-10-19
> Cell 04 - Address: <MAC '[COLOR="#FF0000"]TELUS6118'[/COLOR] [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"TELUS6118"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009eeb5ad8ba
                    Extra: Last beacon: 2772ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSKAnd also see:> [/etc/netplan/03-wireless.yaml]
network:
  version: 2
  renderer: networkd
  
  wifis:
    wlp2s0:
      dhcp4: true
      dhcp6: false
      access-points:
        "[COLOR="#FF0000"]Telus6118[/COLOR]": 
          password: "f843crkcbr"In the wide world of Linux and especially networking, those are not the same.

Please try:```
[/etc/netplan/03-wireless.yaml]
network:
  version: 2
  renderer: networkd
  
  wifis:
    wlp2s0:
      dhcp4: true
      dhcp6: false
      access-points:
        "TELUS6118": 
          password: "f843crkcbr"
```

---

### Post by prototempus on 2018-10-19
Haha, oh my gosh! I KNEW it'd be something stupid!

Thank you. I feel so silly.

---

### Post by chili555 on 2018-10-19
Glad it's working by whatever means.

I was glad to get lobbed an easy one once in a while!

---

