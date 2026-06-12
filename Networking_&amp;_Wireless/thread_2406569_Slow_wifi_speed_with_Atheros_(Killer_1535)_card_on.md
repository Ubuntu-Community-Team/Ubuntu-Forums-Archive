---
title: "Slow wifi speed with Atheros (Killer 1535) card on ubuntu 18.04"
date: 2018-11-22
forum: Networking &amp; Wireless
---

### Post by baydude510 on 2018-11-22
On my 5-year old macbook, and under windows on the same laptop (Dell XPS 15 9570), I can get 80 mbp/s via speedtest.net. But under ubuntu 18.04 with latest 4.18 (also used 4.15, 4.16, 4.17) kernels, I can only get 25 mbp/s max. I've tried several things under different combinations of kernels, kubuntu/manjaro, but no luck. Any help? I've also tried using intel 9260, intel 8265. All same 25 mbp/s max speed. Currently I'm back using the Qualcomm Atheros QCA6174 802.11ac. Any ideas what's wrong? Here's the info...

wireless-info.txt:
```
########## wireless info START ##########

Report from: 22 Nov 2018 08:00 PST -0800

Booted last: 22 Nov 2018 00:00 PST -0800

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 4.18.19-041819-generic #201811131531 SMP Tue Nov 13 20:33:36 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, mem_sleep_default=deep, vt.handoff=1

##### desktop ###########################

Plasma

##### lspci #############################

3b:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
    Subsystem: Bigfoot Networks, Inc. QCA6174 802.11ac Wireless Network Adapter [1a56:1535]
    Kernel driver in use: ath10k_pci

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 27c6:5395  
Bus 001 Device 003: ID 0cf3:e301 Atheros Communications, Inc. 
Bus 001 Device 005: ID 0c45:671d Microdia 
Bus 001 Device 006: ID 154b:009f PNY 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

SecureBoot disabled

##### lsmod #############################

dell_wmi               16384  0
wmi_bmof               16384  0
intel_wmi_thunderbolt    16384  0
mxm_wmi                16384  0
dell_laptop            20480  0
dell_smbios            24576  2 dell_wmi,dell_laptop
dell_wmi_descriptor    16384  2 dell_wmi,dell_smbios
ath10k_pci             40960  0
ath10k_core           417792  1 ath10k_pci
ath                    36864  1 ath10k_core
mac80211              794624  1 ath10k_core
cfg80211              663552  3 ath,mac80211,ath10k_core
wmi                    24576  6 intel_wmi_thunderbolt,dell_wmi,wmi_bmof,dell_smbios,dell_wmi_descriptor,mxm_wmi
sparse_keymap          16384  2 intel_hid,dell_wmi
video                  45056  3 dell_wmi,dell_laptop,i915

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: wlp59s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether <MAC 'wlp59s0' [IF1]> brd <MAC address>
    inet 192.168.1.143/24 brd 192.168.1.255 scope global wlp59s0
       valid_lft forever preferred_lft forever
3: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether <MAC 'docker0' [IF2]> brd <MAC address>

##### iwconfig ##########################

docker0   no wireless extensions.

lo        no wireless extensions.

wlp59s0   IEEE 802.11  ESSID:"ivan_wifi_bgn_2.4GHz"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'ivan_wifi_bgn_2.4GHz' [AC3]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-17 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:172   Missed beacon:0

##### route #############################

default via 192.168.1.1 dev wlp59s0 
192.168.1.0/24 dev wlp59s0 proto kernel scope link src 192.168.1.143 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager
    Wicd

Running:

root       884     1  0 Nov21 ?        00:00:03 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp59s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA6174 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.18.19-041819-generic
GENERAL.FIRMWARE-VERSION:               WLAN.RM.2.0-00180-QCARMSWPZ-1
GENERAL.HWADDR:                         <MAC 'wlp59s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:3b:00.0/net/wlp59s0
GENERAL.IP-IFACE:                       --
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

GENERAL.DEVICE:                         docker0
GENERAL.TYPE:                           bridge
GENERAL.NM-TYPE:                        NMDeviceBridge
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         bridge
GENERAL.DRIVER-VERSION:                 2.3
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'docker0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         41 (The device's existing connection was assumed)
GENERAL.UDI:                            /sys/devices/virtual/net/docker0
GENERAL.IP-IFACE:                       docker0
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     no
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
CAPABILITIES.SRIOV:                     no
BRIDGE.SLAVES:                          --
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager config #############

[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 2

[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile
[ifupdown]
managed=false
[device]
wifi.scan-rand-mac-address=no

[[/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf]]
[main]
dns=systemd-resolved

[[/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf]]
[keyfile]
unmanaged-devices=*,except:type:wifi,except:type:wwan

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/ivan_wifi_bgn_2.4GHz]] (600 root)
[connection] id=ivan_wifi_bgn_2.4GHz | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp59s0' [IF1]> | mac-address-blacklist= | ssid=ivan_wifi_bgn_2.4GHz
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

global
country US: DFS-FCC
    (2402 - 2472 @ 40), (N/A, 30), (N/A)
    (5170 - 5250 @ 80), (N/A, 23), (N/A), AUTO-BW
    (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS, AUTO-BW
    (5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

docker0   no frequency information.

lo        no frequency information.

wlp59s0   32 channels in total; available frequencies :
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
          Channel 144 : 5.72 GHz
          Channel 149 : 5.745 GHz
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

docker0   Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:5.24 GHz (Channel 48)
      2   APs on   Frequency:5.765 GHz
      2   APs on   Frequency:5.805 GHz
      1   APs on   Frequency:5.825 GHz

wlp59s0   Scan completed :
          Cell 01 - Address: <MAC 'ivan_wifi_an_5GHz' [AC1]>
                    Channel:161
                    Frequency:5.805 GHz
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"ivan_wifi_an_5GHz"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000027323a7e925
                    Extra: Last beacon: 220ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'MyExt5' [AC2]>
                    Channel:161
                    Frequency:5.805 GHz
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"MyExt5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000322e349ffa
                    Extra: Last beacon: 236ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'ivan_wifi_bgn_2.4GHz' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-24 dBm  
                    Encryption key:on
                    ESSID:"ivan_wifi_bgn_2.4GHz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000121a0bdefc6
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'hblbnet' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"hblbnet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000009f069774bfb
                    Extra: Last beacon: 5788ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'MyExt2.4' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"MyExt2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000322a94fd0b
                    Extra: Last beacon: 5244ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC '' [AC6]>
                    Channel:48
                    Frequency:5.24 GHz (Channel 48)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:""
                    Mode:Master
                    Extra:tsf=0000007c6f86102b
                    Extra: Last beacon: 4020ms ago
          Cell 07 - Address: <MAC 'hblbnet5' [AC7]>
                    Channel:153
                    Frequency:5.765 GHz
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"hblbnet5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000009f069718834
                    Extra: Last beacon: 508ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'DIRECT-roku-535-09E3BA' [AC8]>
                    Channel:153
                    Frequency:5.765 GHz
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-roku-535-09E3BA"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000009f0697254ec
                    Extra: Last beacon: 544ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC '' [AC9]>
                    Channel:165
                    Frequency:5.825 GHz
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:""
                    Mode:Master
                    Extra:tsf=00000081537875cd
                    Extra: Last beacon: 104ms ago

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.18.19-041819-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-6.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-6.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board-2.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA9887/hw1.0/board-2.bin
firmware:       ath10k/QCA9887/hw1.0/board.bin
firmware:       ath10k/QCA9887/hw1.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
license:        Dual BSD/GPL
description:    Driver support for Qualcomm Atheros 802.11ac WLAN PCIe/AHB devices
author:         Qualcomm Atheros
srcversion:     496197CB61D7EEDCCE920A6
depends:        ath10k_core
retpoline:      Y
intree:         Y
name:           ath10k_pci
vermagic:       4.18.19-041819-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.18.19-041819-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for Qualcomm Atheros 802.11ac wireless LAN cards.
author:         Qualcomm Atheros
srcversion:     037E1CC99C3F2DB678015E9
depends:        mac80211,cfg80211,ath
retpoline:      Y
intree:         Y
name:           ath10k_core
vermagic:       4.18.19-041819-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)
parm:           coredump_mask:Bitfield of what to include in firmware crash file (ulong)

[ath]
filename:       /lib/modules/4.18.19-041819-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     6472C44D3E1911E7AC15723
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           ath
vermagic:       4.18.19-041819-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[mac80211]
filename:       /lib/modules/4.18.19-041819-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C5D73328CD704BB6E363074
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.18.19-041819-generic SMP mod_unload 
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
filename:       /lib/modules/4.18.19-041819-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     BFB309EF7C6C321F605D36E
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.18.19-041819-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath10k_pci]
irq_mode: 0
reset_mode: 0

[ath10k_core]
coredump_mask: 3
cryptmode: 0
debug_mask: 0
rawmode: N
skip_otp: N
uart_print: N

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

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[18714.561254] IPv6: ADDRCONF(NETDEV_UP): wlp59s0: link is not ready (repeated 3 times)
[18837.154839] IPv6: ADDRCONF(NETDEV_UP): docker0: link is not ready
[18879.217608] IPv6: ADDRCONF(NETDEV_UP): wlp59s0: link is not ready
[18881.423151] wlp59s0: authenticate with <MAC 'ivan_wifi_bgn_2.4GHz' [AC3]>
[18881.464027] wlp59s0: send auth to <MAC 'ivan_wifi_bgn_2.4GHz' [AC3]> (try 1/3)
[18881.465858] wlp59s0: authenticated
[18881.465894] ath10k_pci 0000:3b:00.0 wlp59s0: disabling HT as WMM/QoS is not supported by the AP
[18881.465897] ath10k_pci 0000:3b:00.0 wlp59s0: disabling VHT as WMM/QoS is not supported by the AP
[18881.471852] wlp59s0: associate with <MAC 'ivan_wifi_bgn_2.4GHz' [AC3]> (try 1/3)
[18881.474939] wlp59s0: RX AssocResp from <MAC 'ivan_wifi_bgn_2.4GHz' [AC3]> (capab=0x411 status=0 aid=22)
[18881.478342] wlp59s0: associated
[18881.489506] IPv6: ADDRCONF(NETDEV_CHANGE): wlp59s0: link becomes ready

########## wireless info END ############
```

---

### Post by chili555 on 2018-11-23
> ath10k_pci 0000:3b:00.0 wlp59s0: [COLOR="#FF0000"]disabling HT[/COLOR] as WMM/QoS is not supported by the APIn this context, HT refers to high throughput; that is, fast speeds.

Is WMM enabled or disabled in your router? Are the results the same either way?

After each change, please power cycle the router.

By the way, given a choice, I'd prefer the Intel.

---

### Post by baydude510 on 2018-11-23
Oh my god! You fixed the problem, I'm now getting 85 mbp/s instead of 25 mbp/s. Thanks!! :P
Don't know why the killer 1535 requires that setting on the router to go fast.

---

### Post by chili555 on 2018-11-23
> **baydude510 said:**
> Oh my god! You fixed the problem, I'm now getting 85 mbp/s instead of 25 mbp/s. Thanks!! :P
Don't know why the killer 1535 requires that setting on the router to go fast.Evidently, it is Linux generally that requires it:
 ```
I've also tried using intel 9260, intel 8265. All same 25 mbp/s max speed. Currently I'm back using the Qualcomm Atheros QCA6174 802.11ac. Any ideas what's wrong? 

```Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

