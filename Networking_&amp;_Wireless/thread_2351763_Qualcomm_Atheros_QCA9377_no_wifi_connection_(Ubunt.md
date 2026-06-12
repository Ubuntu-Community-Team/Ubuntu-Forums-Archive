---
title: "Qualcomm Atheros QCA9377 no wifi connection (Ubuntu 16.10)"
date: 2017-02-06
forum: Networking &amp; Wireless
---

### Post by p-dambrauskas on 2017-02-06
Hello,

I'm using Lenovo Thinkpad e470 with  Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter Kubuntu 16.10 (also tried ubuntu 16.04 LTS) and have some problems with my old router (D-Link DI-504). While Security type is set to WPA2, ubuntu is unable to connect and keeps asking for password, so I've changed it to WEP. With WEP it connects to router, but internet still does not work. It is worth mentioning, that wifi works fine, with other routers and my previous laptop (old dell with ubuntu 15.04) worked fine with the same router.

I've tired using different kernels, disabling wifi power management, using different firmware versions ([https://github.com/kvalo/ath10k-firmware](https://github.com/kvalo/ath10k-firmware)) and some other suggestions, which i've manged to find on the internet, nothing seems to work.

Are there any solutions for my problem or I should just replace my ancient router?

There is wireliss-script output:
```


########## wireless info START ##########


Report from: 06 Feb 2017 20:52 EET +0200


Booted last: 06 Feb 2017 00:00 EET +0200


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.10
Release:    16.10
Codename:    yakkety


##### kernel ############################


Linux 4.8.0-37-generic #39-Ubuntu SMP Thu Jan 26 02:27:07 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, noprompt, persistent, quiet, splash, vt.handoff=7


##### desktop ###########################


/usr/share/xsessions/plasma


##### lspci #############################


04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:505b]
    Kernel driver in use: r8169


05:00.0 Network controller [0280]: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter [168c:0042] (rev 31)
    Subsystem: Lenovo QCA9377 802.11ac Wireless Network Adapter [17aa:0901]
    Kernel driver in use: ath10k_pci


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 138a:0011 Validity Sensors, Inc. VFS5011 Fingerprint Reader
Bus 001 Device 003: ID 5986:2109 Acer, Inc 
Bus 001 Device 002: ID 0cf3:e500 Atheros Communications, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


ath10k_pci             45056  0
ath10k_core           335872  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              757760  1 ath10k_core
cfg80211              581632  3 mac80211,ath,ath10k_core
wmi                    16384  0


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp4s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.178  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::71f7:4052:df5b:da87  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 23264  bytes 16918595 (16.9 MB)
        RX errors 0  dropped 660  overruns 0  frame 0
        TX packets 20198  bytes 3560651 (3.5 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 61932  bytes 3470816 (3.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 61932  bytes 3470816 (3.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlp5s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.171  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::5a00:e3ff:feb6:8347  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 2449  bytes 902372 (902.3 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2988  bytes 367941 (367.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


lo        no wireless extensions.


enp4s0    no wireless extensions.


wlp5s0    IEEE 802.11  ESSID:"FreeWifi"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: <MAC 'FreeWifi' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:519   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp4s0
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp5s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp4s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp4s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp5s0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root      4320     1  0 20:26 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp4s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               rtl8168g-3_0.0.1 04/23/13
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.2/0000:04:00.0/net/enp4s0
GENERAL.IP-IFACE:                       enp4s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       17cd25a3-1719-31ea-9413-0146319a654e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/10
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   17cd25a3-1719-31ea-9413-0146319a654e | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.178/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             217.147.34.15
IP4.DNS[2]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        server_name = FreeWifi
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 192.168.0.1
DHCP4.OPTION[11]:                       expiry = 1487011524
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.0.1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.0.178
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 604780
DHCP4.OPTION[20]:                       dhcp_lease_time = 604800
DHCP4.OPTION[21]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[22]:                       domain_name_servers = 217.147.34.15 192.168.0.1
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       dhcp_rebinding_time = 604780
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[28]:                       network_number = 192.168.0.0
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::71f7:4052:df5b:da87/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlp5s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA9377 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.8.0-37-generic
GENERAL.FIRMWARE-VERSION:               WLAN.TF.1.0-00267-1
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.3/0000:05:00.0/net/wlp5s0
GENERAL.IP-IFACE:                       wlp5s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     FreeWifi
GENERAL.CON-UUID:                       befa8737-ec1c-4252-9817-b723b51cab14
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/7
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     1 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   befa8737-ec1c-4252-9817-b723b51cab14 | FreeWifi
IP4.ADDRESS[1]:                         192.168.0.171/24
IP4.GATEWAY:                            192.168.0.1
IP4.DNS[1]:                             217.147.34.15
IP4.DNS[2]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        server_name = FreeWifi
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 192.168.0.1
DHCP4.OPTION[11]:                       expiry = 1487011276
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.0.1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.0.171
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 604780
DHCP4.OPTION[20]:                       dhcp_lease_time = 604800
DHCP4.OPTION[21]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[22]:                       domain_name_servers = 217.147.34.15 192.168.0.1
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       dhcp_rebinding_time = 604780
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[28]:                       network_number = 192.168.0.0
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::5a00:e3ff:feb6:8347/64
IP6.GATEWAY:                            


SSID      BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
FreeWifi  <MAC 'FreeWifi' [AC1]>  Infra  5     2432 MHz  54 Mbit/s  68      &#9602;&#9604;&#9606;_  WEP       yes     * 


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/FreeWifi]] (600 root)
[connection] id=FreeWifi | type=wifi | permissions=
[wifi] bssid=<MAC 'FreeWifi' [AC1]> | mac-address=<MAC address> | mac-address-blacklist= | ssid=FreeWifi
[ipv4] method=auto
[ipv6] method=ignore


##### iw reg get ########################


Region: Europe/Vilnius (based on set time zone)


country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


lo        no frequency information.


enp4s0    no frequency information.


wlp5s0    32 channels in total; available frequencies :
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
          Current Frequency:2.432 GHz (Channel 5)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp4s0    Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.432 GHz (Channel 5)


wlp5s0    Scan completed :
          Cell 01 - Address: <MAC 'FreeWifi' [AC1]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000015e417a658
                    Extra: Last beacon: 28ms ago


##### module infos ######################


[ath10k_pci]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
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
srcversion:     8DB6E266EF9D63EC5C2B007
depends:        ath10k_core
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)


[ath10k_core]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for Qualcomm Atheros 802.11ac wireless LAN cards.
author:         Qualcomm Atheros
srcversion:     663DAB23AD4CFA103833EE1
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)


[ath]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     5C13C1638BE3EDB7B93F6A7
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.8.0-37-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C63473656FCDBBDA56E12DA
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.8.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     5F9AB87008B83E8D5117A0B
depends:        
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 
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


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


[/etc/pm/config.d/blacklist] (644 root)
HOOK_BLACKLIST="wireless"


##### udev rules ########################


##### dmesg #############################


[   25.721301] wlp5s0: authenticate with <MAC 'FreeWifi' [AC1]>
[   25.758224] wlp5s0: send auth to <MAC 'FreeWifi' [AC1]> (try 1/3)
[   25.766716] wlp5s0: authenticated
[   25.766862] ath10k_pci 0000:05:00.0 wlp5s0: disabling HT/VHT due to WEP/TKIP use
[   25.766864] ath10k_pci 0000:05:00.0 wlp5s0: disabling HT as WMM/QoS is not supported by the AP
[   25.766865] ath10k_pci 0000:05:00.0 wlp5s0: disabling VHT as WMM/QoS is not supported by the AP
[   25.773020] wlp5s0: associate with <MAC 'FreeWifi' [AC1]> (try 1/3)
[   25.774929] wlp5s0: RX AssocResp from <MAC 'FreeWifi' [AC1]> (capab=0x431 status=0 aid=1)
[   25.776693] wlp5s0: associated
[   25.776725] IPv6: ADDRCONF(NETDEV_CHANGE): wlp5s0: link becomes ready
[  862.370865] wlp5s0: deauthenticating from <MAC 'FreeWifi' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  872.441963] wlp5s0: authenticate with <MAC 'FreeWifi' [AC1]>
[  872.478118] wlp5s0: send auth to <MAC 'FreeWifi' [AC1]> (try 1/3)
[  872.484862] wlp5s0: authenticated
[  872.485016] ath10k_pci 0000:05:00.0 wlp5s0: disabling HT/VHT due to WEP/TKIP use
[  872.485017] ath10k_pci 0000:05:00.0 wlp5s0: disabling HT as WMM/QoS is not supported by the AP
[  872.485018] ath10k_pci 0000:05:00.0 wlp5s0: disabling VHT as WMM/QoS is not supported by the AP
[  872.486835] wlp5s0: associate with <MAC 'FreeWifi' [AC1]> (try 1/3)
[  872.488768] wlp5s0: RX AssocResp from <MAC 'FreeWifi' [AC1]> (capab=0x431 status=0 aid=3)
[  872.492051] wlp5s0: associated
[  922.100086] wlp5s0: deauthenticating from <MAC 'FreeWifi' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  922.385658] IPv6: ADDRCONF(NETDEV_UP): wlp5s0: link is not ready
[  922.512212] ath10k_pci 0000:05:00.0: no channel configured; ignoring frame(s)!
[  922.516160] IPv6: ADDRCONF(NETDEV_UP): wlp5s0: link is not ready
[  931.850175] wlp5s0: authenticate with <MAC 'FreeWifi' [AC1]>
[  931.886186] wlp5s0: send auth to <MAC 'FreeWifi' [AC1]> (try 1/3)
[  931.892979] wlp5s0: authenticated
[  931.893092] ath10k_pci 0000:05:00.0 wlp5s0: disabling HT/VHT due to WEP/TKIP use
[  931.893093] ath10k_pci 0000:05:00.0 wlp5s0: disabling HT as WMM/QoS is not supported by the AP
[  931.893094] ath10k_pci 0000:05:00.0 wlp5s0: disabling VHT as WMM/QoS is not supported by the AP
[  931.896456] wlp5s0: associate with <MAC 'FreeWifi' [AC1]> (try 1/3)
[  931.898415] wlp5s0: RX AssocResp from <MAC 'FreeWifi' [AC1]> (capab=0x431 status=0 aid=1)
[  931.901474] wlp5s0: associated
[  931.901572] IPv6: ADDRCONF(NETDEV_CHANGE): wlp5s0: link becomes ready
[ 1795.626870] wlp5s0: deauthenticating from <MAC 'FreeWifi' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1804.982923] wlp5s0: authenticate with <MAC 'FreeWifi' [AC1]>
[ 1805.019275] wlp5s0: send auth to <MAC 'FreeWifi' [AC1]> (try 1/3)
[ 1805.026042] wlp5s0: authenticated
[ 1805.026156] ath10k_pci 0000:05:00.0 wlp5s0: disabling HT/VHT due to WEP/TKIP use
[ 1805.026157] ath10k_pci 0000:05:00.0 wlp5s0: disabling HT as WMM/QoS is not supported by the AP
[ 1805.026158] ath10k_pci 0000:05:00.0 wlp5s0: disabling VHT as WMM/QoS is not supported by the AP
[ 1805.029804] wlp5s0: associate with <MAC 'FreeWifi' [AC1]> (try 1/3)
[ 1805.031879] wlp5s0: RX AssocResp from <MAC 'FreeWifi' [AC1]> (capab=0x431 status=0 aid=1)
[ 1805.033907] wlp5s0: associated


########## wireless info END ############



```

---

### Post by praseodym on 2017-02-06
Check if the MAC address filter is turned off. Router firmware is up to date? Also use a fixed channel.

---

### Post by jeremy31 on 2017-02-06
Also change the encryption on the router to WPA2-PSK, WPA2-AES, as right now it appears to be using WEP/TKIP and the wifi card isn't liking it

```
ath10k_pci 0000:05:00.0 wlp5s0: disabling HT/VHT due to WEP/TKIP use
```

---

### Post by chili555 on 2017-02-06
Is the result the same with the ethernet detached? You seem to have two IP addresses.

---

### Post by p-dambrauskas on 2017-02-07
Hey, thanks for responding.

> 
Check if the MAC address filter is turned off. Router firmware is up to date? Also use a fixed channel.[RIGHT][/RIGHT]



Mac filters are disabled, router is using latest firmware. Dynamic channels are not supported on this router, I'm using Channel 5.

> 
Also change the encryption on the router to WPA2-PSK, WPA2-AES, as right now it appears to be using WEP/TKIP and the wifi card isn't liking it


I tied all possible encryption options. With WPA2-PSK it is not even able to connect :( (keeps asking for password every few seconds, even if entered password is correct). With WEP or disabled security, it connects to router, but I still cant access internet (ping 8.8.8.8 results in [FONT=monospace][COLOR=#000000]Destination Host Unreachable[/COLOR][/FONT])

> 
Is the result the same with the ethernet detached? You seem to have two IP addresses.


Ran the script with ethernet disconnected. Results:
```



########## wireless info START ##########


Report from: 07 Feb 2017 18:06 EET +0200


Booted last: 07 Feb 2017 00:00 EET +0200


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.10
Release:	16.10
Codename:	yakkety


##### kernel ############################


Linux 4.8.0-37-generic #39-Ubuntu SMP Thu Jan 26 02:27:07 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, noprompt, persistent, quiet, splash, vt.handoff=7


##### desktop ###########################


/usr/share/xsessions/plasma


##### lspci #############################


04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:505b]
	Kernel driver in use: r8169


05:00.0 Network controller [0280]: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter [168c:0042] (rev 31)
	Subsystem: Lenovo QCA9377 802.11ac Wireless Network Adapter [17aa:0901]
	Kernel driver in use: ath10k_pci


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 138a:0011 Validity Sensors, Inc. VFS5011 Fingerprint Reader
Bus 001 Device 003: ID 5986:2109 Acer, Inc 
Bus 001 Device 002: ID 0cf3:e500 Atheros Communications, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


ath10k_pci             45056  0
ath10k_core           335872  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              757760  1 ath10k_core
cfg80211              581632  3 mac80211,ath,ath10k_core
wmi                    16384  0


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp4s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 299458  bytes 386829775 (386.8 MB)
        RX errors 0  dropped 660  overruns 0  frame 0
        TX packets 188462  bytes 33216105 (33.2 MB)
        TX errors 0  dropped 1 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 188776  bytes 10019239 (10.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 188776  bytes 10019239 (10.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlp5s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.171  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::5a00:e3ff:feb6:8347  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 3283  bytes 1050214 (1.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 3976  bytes 490135 (490.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


lo        no wireless extensions.


enp4s0    no wireless extensions.


wlp5s0    IEEE 802.11  ESSID:"FreeWifi"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: <MAC 'FreeWifi' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:200   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp5s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp5s0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root      4320     1  0 Feb06 ?        00:00:04 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp5s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA9377 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.8.0-37-generic
GENERAL.FIRMWARE-VERSION:               WLAN.TF.1.0-00267-1
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.3/0000:05:00.0/net/wlp5s0
GENERAL.IP-IFACE:                       wlp5s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     FreeWifi
GENERAL.CON-UUID:                       befa8737-ec1c-4252-9817-b723b51cab14
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/12
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     1 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   befa8737-ec1c-4252-9817-b723b51cab14 | FreeWifi
IP4.ADDRESS[1]:                         192.168.0.171/24
IP4.GATEWAY:                            192.168.0.1
IP4.DNS[1]:                             217.147.34.15
IP4.DNS[2]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        server_name = FreeWifi
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 192.168.0.1
DHCP4.OPTION[11]:                       expiry = 1487087715
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.0.1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.0.171
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 604780
DHCP4.OPTION[20]:                       dhcp_lease_time = 604800
DHCP4.OPTION[21]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[22]:                       domain_name_servers = 217.147.34.15 192.168.0.1
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       dhcp_rebinding_time = 604780
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[28]:                       network_number = 192.168.0.0
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::5a00:e3ff:feb6:8347/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp4s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               rtl8168g-3_0.0.1 04/23/13
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         40 (Carrier/link changed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.2/0000:04:00.0/net/enp4s0
GENERAL.IP-IFACE:                       
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
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID      BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
FreeWifi  <MAC 'FreeWifi' [AC1]>  Infra  5     2432 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WEP       yes     * 


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


Sorry, try again.
[[/etc/NetworkManager/system-connections/FreeWifi]] (600 root)
[connection] id=FreeWifi | type=wifi | permissions=
[wifi] bssid=<MAC 'FreeWifi' [AC1]> | mac-address=<MAC address> | mac-address-blacklist= | ssid=FreeWifi
[ipv4] method=auto
[ipv6] method=ignore


##### iw reg get ########################


Region: Europe/Vilnius (based on set time zone)


country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
	(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


lo        no frequency information.


enp4s0    no frequency information.


wlp5s0    32 channels in total; available frequencies :
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
          Current Frequency:2.432 GHz (Channel 5)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp4s0    Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.432 GHz (Channel 5)


wlp5s0    Scan completed :
          Cell 01 - Address: <MAC 'FreeWifi' [AC1]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000027b08651e7
                    Extra: Last beacon: 80ms ago


##### module infos ######################


[ath10k_pci]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
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
srcversion:     8DB6E266EF9D63EC5C2B007
depends:        ath10k_core
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)


[ath10k_core]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for Qualcomm Atheros 802.11ac wireless LAN cards.
author:         Qualcomm Atheros
srcversion:     663DAB23AD4CFA103833EE1
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)


[ath]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     5C13C1638BE3EDB7B93F6A7
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.8.0-37-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C63473656FCDBBDA56E12DA
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.8.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     5F9AB87008B83E8D5117A0B
depends:        
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 
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


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


[/etc/pm/config.d/blacklist] (644 root)
HOOK_BLACKLIST="wireless"


##### udev rules ########################


##### dmesg #############################


[ 7279.906653] [drm] GuC firmware load skipped
[ 7281.276759] IPv6: ADDRCONF(NETDEV_UP): wlp5s0: link is not ready (repeated 3 times)
[ 7292.659536] wlp5s0: authenticate with <MAC 'FreeWifi' [AC1]>
[ 7292.695768] wlp5s0: send auth to <MAC 'FreeWifi' [AC1]> (try 1/3)
[ 7292.702545] wlp5s0: authenticated
[ 7292.702664] ath10k_pci 0000:05:00.0 wlp5s0: disabling HT/VHT due to WEP/TKIP use
[ 7292.702665] ath10k_pci 0000:05:00.0 wlp5s0: disabling HT as WMM/QoS is not supported by the AP
[ 7292.702666] ath10k_pci 0000:05:00.0 wlp5s0: disabling VHT as WMM/QoS is not supported by the AP
[ 7292.703384] wlp5s0: associate with <MAC 'FreeWifi' [AC1]> (try 1/3)
[ 7292.705278] wlp5s0: RX AssocResp from <MAC 'FreeWifi' [AC1]> (capab=0x431 status=0 aid=3)
[ 7292.707157] wlp5s0: associated
[ 7292.707194] IPv6: ADDRCONF(NETDEV_CHANGE): wlp5s0: link becomes ready


########## wireless info END ############



```

---

