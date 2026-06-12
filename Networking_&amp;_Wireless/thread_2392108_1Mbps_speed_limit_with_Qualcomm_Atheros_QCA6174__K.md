---
title: "1Mbps speed limit with Qualcomm Atheros QCA6174 | Killer 1435 @ 18.04"
date: 2018-05-16
forum: Networking &amp; Wireless
---

### Post by mika-2nd on 2018-05-16
Hello,

 my **Dell XPS 9370** is a dualboot system with a Killer 1435 (Win 10 and Ubuntu 18.04). WLAN works fine with Win10, but speed is limited with Ubuntu 18.04 to 1Mbps. Ubuntu was updated from 17.10 to 18.04. On  Ubuntu 17.10 WLAN worked also very well. I am not sure, but it might have worked with the very first installation of 18.04 and got like this after an update.  
It was tested with several routers: same results.
Your help is welcome :-)
Thanks & br
*MiKa*

Some info from the system:
```

##### kernel ############################
Linux 4.15.0-20-generic #21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
Parameters: ro, quiet, splash, vt.handoff=1
##### lspci #############################
02:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [732c:026e] (rev 32)
    Subsystem: Bigfoot Networks, Inc. QCA6174 802.11ac Wireless Network Adapter [5f66:112a]
    Kernel driver in use: ath10k_pci
##### rfkill ############################
0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

dell_laptop            20480  0
dell_smbios_wmi        16384  0
dell_wmi               16384  0
dell_smbios            16384  4 dell_wmi,dell_laptop,dell_smbios_wmi,dell_smbios_smm
ath10k_pci             45056  0
intel_wmi_thunderbolt    16384  0
ath10k_core           360448  1 ath10k_pci
dell_wmi_descriptor    16384  2 dell_wmi,dell_smbios_wmi
wmi_bmof               16384  0
ath                    28672  1 ath10k_core
mac80211              778240  1 ath10k_core
cfg80211              622592  3 mac80211,ath,ath10k_core
sparse_keymap          16384  2 dell_wmi,intel_hid
wmi                    24576  5 dell_wmi,wmi_bmof,intel_wmi_thunderbolt,dell_wmi_descriptor,dell_smbios_wmi
video                  40960  3 dell_wmi,dell_laptop,i915

##### interfaces ########################
[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether <MAC 'wlp2s0' [IF1]> brd <MAC address>
    inet 192.168.1.102/24 brd 192.168.1.255 scope global dynamic noprefixroute wlp2s0
       valid_lft 85909sec preferred_lft 85909sec
    inet6 fe80::6a47:d32b:5fc6:6a55/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################
lo        no wireless extensions.
wlp2s0    IEEE 802.11  ESSID:"T Pocket-Fi"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: <MAC 'T Pocket-Fi' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:164   Missed beacon:0

##### route #############################
default via 192.168.1.1 dev wlp2s0 proto dhcp metric 20600 
169.254.0.0/16 dev wlp2s0 scope link metric 1000 
192.168.1.0/24 dev wlp2s0 proto kernel scope link src 192.168.1.102 metric 600 

##### network managers ##################
Installed:
    NetworkManager

Running:
root       858     1  0 07:01 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA6174 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.15.0-20-generic
GENERAL.FIRMWARE-VERSION:               WLAN.RM.4.4.1-00079-QCARMSWPZ-1
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     T Pocket-Fi
GENERAL.CON-UUID:                       47408087-155e-4262-81ec-9cb93f8d8e0f
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     1 Mb/s
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
IP4.ADDRESS[1]:                         192.168.1.104/23
IP4.GATEWAY:                            192.168.1.2
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.1.1, mt = 20600
IP4.ROUTE[2]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 600
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_domain_search = 1
...
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::2a47:532b:5fc6:6a55/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 600
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   47408087-155e-4262-81ec-9cb93e8d8e0f | T Pocket-Fi

SSID                 BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  IN-USE 
T Pocket-Fi  <MAC 'T Pocket-Fi ' [AC1]>  Infra  9     2452 MHz  65 Mbit/s  83      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  yes     *      

##### NetworkManager.state ##############
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############
[main]
plugins=ifupdown,keyfile
[ifupdown]
managed=false
[device]
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########
[[/etc/NetworkManager/system-connections/T Pocket-Fi ]] (600 root)
[connection] id=T Pocket-Fi | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF1]> | mac-address-blacklist= | ssid=T Pocket-Fi 
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################
[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Asia/Seoul (based on set time zone)

global
country KR: DFS-JP
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW
    (5490 - 5710 @ 160), (N/A, 30), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
    (57000 - 66000 @ 2160), (N/A, 43), (N/A)

##### iwlist channels ###################

lo        no frequency information.

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
          Current Frequency:2.452 GHz (Channel 9)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:2.462 GHz (Channel 11)

wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'T Pocket-Fi' [AC1]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"T Pocket-Fi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ada289504
                    Extra: Last beacon: 2984ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.15.0-20-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
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
srcversion:     74C1F2FC14DBB48F398437C
depends:        ath10k_core
retpoline:      Y
intree:         Y
name:           ath10k_pci
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.15.0-20-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for Qualcomm Atheros 802.11ac wireless LAN cards.
author:         Qualcomm Atheros
srcversion:     72B2ED39877B23FC03E0A9B
depends:        mac80211,cfg80211,ath
retpoline:      Y
intree:         Y
name:           ath10k_core
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)

[ath]
filename:       /lib/modules/4.15.0-20-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     555BBBB9D4FCA58A05E7C0D
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           ath
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[mac80211]
filename:       /lib/modules/4.15.0-20-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1CEA5CF286EDB289C1D0BF8
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-20-generic SMP mod_unload 
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
filename:       /lib/modules/4.15.0-20-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D5B0789D4C423C81CCFB437
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-20-generic SMP mod_unload 
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

##### rc.local ##########################
grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

########## wireless info END ############






```

---

### Post by mika-2nd on 2018-05-17
I did now tests with another WLAN router (public) and still get the same wifi settings but the result is much better. Any ideas how to measure the WLAN speed since it looks like the info I get with these commands do not match. All routers are 2,5GHz.
Thanks & br, MiKa

---

