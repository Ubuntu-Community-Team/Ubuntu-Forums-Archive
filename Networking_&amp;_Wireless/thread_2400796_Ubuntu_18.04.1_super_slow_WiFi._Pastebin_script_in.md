---
title: "Ubuntu 18.04.1 super slow WiFi. Pastebin script included"
date: 2018-09-10
forum: Networking &amp; Wireless
---

### Post by carty2 on 2018-09-10
Hello guys! 

I have been browsing this forum since yesterday and tried every solution I can come across. After seeing the pastebin script it seems that everyone has individual solutions to the slow WiFi problem based on their hardware / settings.

Here is my output from the troubleshooting script:

Thanks a lot in advance for any help received! I am genuinely stuck.

```
########## wireless info START ##########

Report from: 10 Sep 2018 14:11 BST +0100

Booted last: 10 Sep 2018 00:00 BST +0100

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 4.15.0-33-generic #36-Ubuntu SMP Wed Aug 15 16:00:05 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168]  (rev 15)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:8330]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:d723]
    Subsystem: Hewlett-Packard Company Device [103c:8319]
    Kernel driver in use: rtl8723de

##### lsusb #############################

Bus 001 Device 004: ID 0bda:b009 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 062a:4101 Creative Labs Wireless Keyboard/Mouse
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 05c8:03ac Cheng Uei Precision Industry Co., Ltd (Foxlink) 
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

rtl8723de              94208  0
btcoexist             434176  1 rtl8723de
phydm_mod             856064  1 rtl8723de
rtl8723_common         24576  1 rtl8723de
rtl_pci                32768  1 rtl8723de
rtlwifi               163840  5 phydm_mod,rtl_pci,btcoexist,rtl8723_common,rtl8723de
mac80211              778240  2 rtl_pci,rtlwifi
cfg80211              622592  2 mac80211,rtlwifi
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
wmi_bmof               16384  0
wmi                    24576  2 wmi_bmof,hp_wmi

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 2923  bytes 316212 (316.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2923  bytes 316212 (316.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.58  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::5d3f:afcc:b4f2:c270  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 10655  bytes 5583161 (5.5 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 11766  bytes 2973747 (2.9 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

wlp3s0    IEEE 802.11  ESSID:"VM1416043"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'VM1416043' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:eek:ff
          Power Management:eek:ff
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1312   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp3s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager

Running:

root       857     1  0 13:15 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         rtl8723de
GENERAL.DRIVER-VERSION:                 4.15.0-33-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.4/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       wlp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     VM1416043
GENERAL.CON-UUID:                       8228552b-e32b-4bd7-93ce-a417e1c95ee3
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     72 Mb/s
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
WIFI-PROPERTIES.5GHZ:                   no
IP4.ADDRESS[1]:                         192.168.0.58/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.0.1, mt = 600
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.ROUTE[3]:                           dst = 192.168.0.0/24, nh = 0.0.0.0, mt = 600
IP4.DNS[1]:                             194.168.4.100
IP4.DNS[2]:                             194.168.8.100
DHCP4.OPTION[1]:                        domain_name_servers = 194.168.4.100 194.168.8.100
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        broadcast_address = 192.168.0.255
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_time_offset = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_domain_name = 1
DHCP4.OPTION[8]:                        requested_netbios_scope = 1
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       host_name = cartylaptop
DHCP4.OPTION[11]:                       expiry = 1537445742
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       dhcp_lease_time = 864000
DHCP4.OPTION[15]:                       routers = 192.168.0.1
DHCP4.OPTION[16]:                       next_server = 192.168.0.1
DHCP4.OPTION[17]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       requested_static_routes = 1
DHCP4.OPTION[20]:                       ip_address = 192.168.0.58
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       requested_domain_name_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_routers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::5d3f:afcc:b4f2:c270/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 600
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   8228552b-e32b-4bd7-93ce-a417e1c95ee3 | VM1416043

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.2/0000:02:00.0/net/enp2s0
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
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

SSID          BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY     ACTIVE  IN-USE 
Virgin Media  <MAC 'Virgin Media' [AC2]>  Infra  1     2412 MHz  130 Mbit/s  49      &#9602;&#9604;__  WPA2 802.1X  no             
VM1416043     <MAC 'VM1416043' [AC1]>  Infra  1     2412 MHz  130 Mbit/s  49      &#9602;&#9604;__  WPA1 WPA2    yes     *      

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

[[/etc/NetworkManager/system-connections/TellYourWifiLoveHer]] (600 root)
[connection] id=TellYourWifiLoveHer | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=TellYourWifiLoveHer
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=AndroidAP
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/VM1416043 1]] (600 root)
[connection] id=VM1416043 1 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=VM1416043
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/VM1416043]] (600 root)
[connection] id=VM1416043 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=VM1416043
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Europe/London (based on set time zone)

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

enp2s0    no frequency information.

lo        no frequency information.

wlp3s0    14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)

wlp3s0    Scan completed :
          Cell 01 - Address: <MAC 'VM1416043' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:eek:n
                    ESSID:"VM1416043"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000175d8b8561b
                    Extra: Last beacon: 32ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Virgin Media' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:eek:n
                    ESSID:"Virgin Media"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000175d8ecf180
                    Extra: Last beacon: 228ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x

##### module infos ######################

[rtl8723de]
filename:       /lib/modules/4.15.0-33-generic/updates/dkms/rtl8723de.ko
firmware:       rtlwifi/rtl8723defw.bin
description:    Realtek 8723DE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     57B1D6F7DC3266BCB31ABDD
depends:        rtlwifi,rtl_pci,btcoexist,rtl8723-common,phydm_mod
retpoline:      Y
name:           rtl8723de
vermagic:       4.15.0-33-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           dma64:bool
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           aspm:Set to 1 to enable ASPM (default 1)
 (int)
parm:           debug_level:Set debug level (0-5) (default 0) (int)
parm:           debug_mask:Set debug mask (default 0) (ullong)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           ant_sel:Set to 1 or 2 to force antenna number (default 0)
 (int)

[rtl8723_common]
filename:       /lib/modules/4.15.0-33-generic/updates/dkms/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     5AAF25B4699EF07310A021A
depends:        rtlwifi
retpoline:      Y
name:           rtl8723_common
vermagic:       4.15.0-33-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[rtl_pci]
filename:       /lib/modules/4.15.0-33-generic/updates/dkms/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     F1DE1F093B181758DE4640E
depends:        mac80211,rtlwifi
retpoline:      Y
name:           rtl_pci
vermagic:       4.15.0-33-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[rtlwifi]
filename:       /lib/modules/4.15.0-33-generic/updates/dkms/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     B7ECEE846CE5B14E0566D06
depends:        mac80211,cfg80211
retpoline:      Y
name:           rtlwifi
vermagic:       4.15.0-33-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[mac80211]
filename:       /lib/modules/4.15.0-33-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1CEA5CF286EDB289C1D0BF8
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-33-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:grin:efault rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.15.0-33-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     AFB624FD5B16A8AA59A9CF7
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-33-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:grin:isable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723de]
ant_sel: 0
aspm: 0
debug_level: 0
debug_mask: 18446744073709551615
disable_watchdog: N
dma64: N
fwlps: N
ips: Y
msi: Y
swenc: N
swlps: N

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
options iwlwifi 11n_disable=1

[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be swenc=1 fwlps=0 ips=0 ant_sel=1

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   30.716873] rtlwifi: loading out-of-tree module taints kernel.
[   30.992172] rtl8723de: Using firmware rtlwifi/rtl8723defw.bin
[   30.998190] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   30.998569] rtlwifi: rtlwifi: wireless switch is on
[   31.000289] rtl8723de 0000:03:00.0 wlp3s0: renamed from wlan0
[   42.264459] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 3 times)
[   45.083841] wlp3s0: authenticate with <MAC 'VM1416043' [AC1]>
[   45.093934] wlp3s0: send auth to <MAC 'VM1416043' [AC1]> (try 1/3)
[   45.096477] wlp3s0: authenticated
[   45.100346] wlp3s0: associate with <MAC 'VM1416043' [AC1]> (try 1/3)
[   45.107202] wlp3s0: RX AssocResp from <MAC 'VM1416043' [AC1]> (capab=0x431 status=0 aid=2)
[   45.383522] wlp3s0: associated
[   46.167664] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[  136.797682] rtlwifi: AP off, try to reconnect now
[  136.797706] wlp3s0: Connection to AP <MAC 'VM1416043' [AC1]> lost
[  144.862539] wlp3s0: authenticate with <MAC 'VM1416043' [AC1]>
[  144.876838] wlp3s0: send auth to <MAC 'VM1416043' [AC1]> (try 1/3)
[  144.881356] wlp3s0: authenticated
[  144.891933] wlp3s0: associate with <MAC 'VM1416043' [AC1]> (try 1/3)
[  144.900819] wlp3s0: RX AssocResp from <MAC 'VM1416043' [AC1]> (capab=0x431 status=0 aid=2)
[  145.176681] wlp3s0: associated

########## wireless info END ############
```

---

### Post by chili555 on 2018-09-10
Most Linux drivers hate hate hate TKIP and auto channel selection. Here is some interesting reading: [https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection](https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection)  [https://en.wikipedia.org/wiki/Temporal_Key_Integrity_Protocol](https://en.wikipedia.org/wiki/Temporal_Key_Integrity_Protocol)

> TKIP uses the same underlying mechanism as WEP, and consequently is vulnerable to a number of similar attacks.I cannot recommend that anyone who is offered two forms of encryption in the router, pick the *least *secure.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:

   ```
 sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

   ```
 sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

    ```
sudo nano /etc/default/crda
```

Change the last line to read:

   ```
 REGDOMAIN=IS
```

Proofread carefully, save and close the text editor.

I also suggest that you experiment with antenna selection. From the terminal:

```
sudo -i
echo "options rtl8723de ant_sel=2"  >  /etc/modprobe.d/rtl8723de.conf
exit
```Reboot. Is there any improvement? If not, repeat the sequence with ant_sel=1 and reboot. One of the two should show a significant improvement in signal quality when you run:```
iwconfig
```Your current reading is:> wlp3s0    IEEE 802.11  ESSID:"VM1416043"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'VM1416043' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:eek:ff
          Power Management:eek:ff
          [COLOR="#FF0000"]Link Quality=**38/70**[/COLOR]  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1312   Missed beacon:0


---

### Post by carty2 on 2018-09-10
> Most Linux drivers hate hate hate TKIP and auto channel selection. Here is some interesting reading: [https://superuser.com/questions/1311...nnel-selection]("https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection")  [https://en.wikipedia.org/wiki/Tempor...grity_Protocol]("https://en.wikipedia.org/wiki/Temporal_Key_Integrity_Protocol")

                                                         TKIP uses the same underlying mechanism as WEP, and consequently is vulnerable to a number of similar attacks.                      
     
 
I cannot recommend that anyone who is offered two forms of encryption in the router, pick the *least *secure.

First, check the settings in the router. WPA2-AES is preferred; not any  WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router  is capable of N speeds, you may have better connectivity with a channel  width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz,  although it is likely to affect N speeds. I also have better luck with a  fixed channel, either 1, 6 or 11, rather than automatic channel  selection. Also, be certain the router is not set to use N speeds only;  auto B, G and N is preferred. After making these changes, reboot the  router. 

I will have to do this part tomorrow. I cannot find the password for the router. It is not the password on the label, and this router is not too old and has never been altered by me.

If i go to WiFi settings on my ubuntu it seems that WPA and WPA2 is being used so I expect it to improve after changing the settings above.

I was able to go through everything else in your answer, and my internet speed is now up from 2-3 mb/s to 10-16 mb/s.



```
 sudo iw reg get
```

This already displayed GB. However, after running:

```
sudo nano /etc/default/crda
```

I saw that REGDOMAIN was UK and not GB like sudo iw reg get displayed. 

I tried 

```


sudo iw reg set UK


```

but then it changed to 00 so I swapped back to GB. Whether regdomain was set to UK or GB made no difference in internet speed so I left it at UK which it was set to at first.


Thank you very much for your assistance. I am happy to see my internet speed close to & at where it should be! Thanks again!


*Carty*



_**PS**_: I saw the code for finding another channel to use and it says: 

```
[INDENT]sudo iwlist wlan0 scan | grep \(Channel

[/INDENT]

```

This returns nothing for me. But after all the troubleshooting i had picked up that maybe I could replace wlan0 with wlp3s0 which I have seen in iwconfig before. Would you mind quickly explaining to me what this is and why mine is wlp3s0 and not wlan0 like the example? I tried googling it but I am really new to this whole system so I did not get any wiser.



EDIT: I just noticed in iwconfig that my link quality is 70/70 now and not 38/70 too. Seems like you got me sorted properly here. Will still look into the recommended router settings tomorrow.

---

