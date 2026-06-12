---
title: "Can't Connect to 5GHZ wifi 16.10"
date: 2016-11-25
forum: Networking &amp; Wireless
---

### Post by bkach on 2016-11-25
[COLOR=#111111][FONT=Ubuntu]I currently have a Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter and am unable to connect to my 5GHZ wifi.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I never seem to have this problem when first installing Ubuntu 16.10, but after about a week of use, i can never seem to connect to the 5GHZ wifi.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I can still see it in my list of wireless connections, but sadly am unable to connect :(.

Here's a copy of the wireless info text:

[/FONT][/COLOR]```



########## wireless info START ##########


Report from: 25 Nov 2016 22:58 CET +0100


Booted last: 25 Nov 2016 00:00 CET +0100


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.10
Release:    16.10
Codename:    yakkety


##### kernel ############################


Linux 4.8.0-27-generic #29-Ubuntu SMP Thu Oct 20 21:03:13 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-V [8086:15b8] (rev 31)
    Subsystem: ASUSTeK Computer Inc. Ethernet Connection (2) I219-V [1043:8672]
    Kernel driver in use: e1000e


05:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
    Subsystem: ASUSTeK Computer Inc. QCA6174 802.11ac Wireless Network Adapter [1043:86e0]
    Kernel driver in use: ath10k_pci


##### lsusb #############################


Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 045e:0719 Microsoft Corp. Xbox 360 Wireless Adapter
Bus 003 Device 002: ID 28de:1142  
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1af3:0001  
Bus 001 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 005: ID 0b05:1825 ASUSTek Computer, Inc. 
Bus 001 Device 004: ID 04d9:0141 Holtek Semiconductor, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: hci1: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
mxm_wmi                16384  0
ath10k_pci             45056  0
ath10k_core           335872  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              757760  1 ath10k_core
cfg80211              581632  3 mac80211,ath,ath10k_core
wmi                    16384  2 asus_wmi,mxm_wmi
video                  40960  1 asus_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp0s31f6: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  memory 0xf7100000-f7120000  


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 82  bytes 9580 (9.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 82  bytes 9580 (9.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlp5s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.3  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::f415:c7a4:6b:4a7f  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 16849  bytes 7757285 (7.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 18467  bytes 3429670 (3.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


lo        no wireless extensions.


enp0s31f6  no wireless extensions.


wlp5s0    IEEE 802.11  ESSID:"MyWifi"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'MyWifi' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=23/70  Signal level=-87 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:79   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp5s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp5s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp5s0


##### resolv.conf #######################


nameserver 209.222.18.222
nameserver 209.222.18.218


##### network managers ##################


Installed:


    NetworkManager


Running:


root      5477     1  0 22:55 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp5s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA6174 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.8.0-27-generic
GENERAL.FIRMWARE-VERSION:               WLAN.RM.2.0-00180-QCARMSWPZ-1
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.1/0000:05:00.0/net/wlp5s0
GENERAL.IP-IFACE:                       wlp5s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     MyWifi
GENERAL.CON-UUID:                       9cf42b23-9a04-4f3f-85cf-c5e268ed8808
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0,1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   9cf42b23-9a04-4f3f-85cf-c5e268ed8808 | MyWifi
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   67b7a315-fa0b-4200-8b04-72dafc519e90 | MyWifi-5G
IP4.ADDRESS[1]:                         192.168.0.3/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             83.255.255.2
IP4.DNS[2]:                             83.255.255.1
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 83.255.255.2 83.255.255.1
DHCP4.OPTION[5]:                        ip_address = 192.168.0.3
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[8]:                        default_ip_ttl = 64
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       time_offset = 0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_rebinding_time = 9450
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       requested_broadcast_address = 1
DHCP4.OPTION[17]:                       routers = 192.168.0.1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 5400
DHCP4.OPTION[19]:                       requested_domain_name = 1
DHCP4.OPTION[20]:                       domain_name = home
DHCP4.OPTION[21]:                       requested_routers = 1
DHCP4.OPTION[22]:                       expiry = 1480121728
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_netbios_scope = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.0.0
DHCP4.OPTION[28]:                       requested_domain_search = 1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       next_server = 192.168.0.1
DHCP4.OPTION[31]:                       dhcp_lease_time = 10800
DHCP4.OPTION[32]:                       requested_host_name = 1
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp0s31f6
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (2) I219-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.8-4
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1f.6/net/enp0s31f6
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
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID              BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
MyWifi-5G      <MAC 'MyWifi-5G' [AC3]>  Infra  100   5500 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA2      no        
MyWifi         <MAC 'MyWifi' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA2      yes     * 
otherwifi  <MAC 'otherwifi' [AC2]>  Infra  36    5180 MHz  54 Mbit/s  30      &#9602;___  WPA2      no        


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


[[/etc/NetworkManager/system-connections/MyWifi]] (600 root)
[connection] id=MyWifi | type=wifi | permissions=user:boris:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=MyWifi
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/MyWifi-5G]] (600 root)
[connection] id=MyWifi-5G | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=MyWifi-5G
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Stockholm (based on set time zone)


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


enp0s31f6  no frequency information.


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
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp0s31f6  Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:5.18 GHz (Channel 36)
      1   APs on   Frequency:5.5 GHz (Channel 100)


wlp5s0    Scan completed :
          Cell 01 - Address: <MAC 'MyWifi' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"MyWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000001c0c45d9
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'otherwifi' [AC2]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"otherwifi"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004cab49f04f
                    Extra: Last beacon: 5148ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'MyWifi-5G' [AC3]>
                    Channel:100
                    Frequency:5.5 GHz (Channel 100)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"MyWifi-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000527fa8d042
                    Extra: Last beacon: 3472ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ath10k_pci]
filename:       /lib/modules/4.8.0-27-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
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
srcversion:     D5C1D197B1BB08AC45E6566
depends:        ath10k_core
intree:         Y
vermagic:       4.8.0-27-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)


[ath10k_core]
filename:       /lib/modules/4.8.0-27-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for Qualcomm Atheros 802.11ac wireless LAN cards.
author:         Qualcomm Atheros
srcversion:     B60553BE2B6B3F262752ADD
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.8.0-27-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)


[ath]
filename:       /lib/modules/4.8.0-27-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     5C13C1638BE3EDB7B93F6A7
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-27-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.8.0-27-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     BDE5CB0CC0A980B65D19934
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-27-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.8.0-27-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F170FED576AF12B070D2E69
depends:        
intree:         Y
vermagic:       4.8.0-27-generic SMP mod_unload modversions 
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


##### udev rules ########################


##### dmesg #############################


[  447.921969] wlp5s0: associated
[  714.335800] wlp5s0: deauthenticating from <MAC 'MyWifi' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  718.828295] wlp5s0: authenticate with <MAC 'MyWifi-5G' [AC3]>
[  718.861838] wlp5s0: send auth to <MAC 'MyWifi-5G' [AC3]> (try 1/3)
[  718.863169] wlp5s0: send auth to <MAC 'MyWifi-5G' [AC3]> (try 2/3)
[  718.864500] wlp5s0: send auth to <MAC 'MyWifi-5G' [AC3]> (try 3/3)
[  718.865923] wlp5s0: authentication with <MAC 'MyWifi-5G' [AC3]> timed out
[  723.418209] wlp5s0: authenticate with <MAC 'MyWifi-5G' [AC3]>
[  723.451024] wlp5s0: send auth to <MAC 'MyWifi-5G' [AC3]> (try 1/3)
[  723.452137] wlp5s0: authenticated
[  723.459312] wlp5s0: associate with <MAC 'MyWifi-5G' [AC3]> (try 1/3)
[  723.460767] wlp5s0: RX AssocResp from <MAC 'MyWifi-5G' [AC3]> (capab=0x1011 status=0 aid=2)
[  723.464171] wlp5s0: associated
[  723.469955] ath: EEPROM regdomain: 0x8114
[  723.469957] ath: EEPROM indicates we should expect a country code
[  723.469959] ath: doing EEPROM country->regdmn map search
[  723.469961] ath: country maps to regdmn code: 0x37
[  723.469963] ath: Country alpha2 being used: DE
[  723.469964] ath: Regpair used: 0x37
[  723.469966] ath: regdomain 0x8114 dynamically updated by country IE
[  723.498191] wlp5s0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC 'MyWifi-5G' [AC3]>
[  749.522867] wlp5s0: deauthenticating from <MAC 'MyWifi-5G' [AC3]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  756.996025] wlp5s0: authenticate with <MAC 'MyWifi' [AC1]>
[  757.067582] wlp5s0: send auth to <MAC 'MyWifi' [AC1]> (try 1/3)
[  757.072684] wlp5s0: send auth to <MAC 'MyWifi' [AC1]> (try 2/3)
[  757.077539] wlp5s0: send auth to <MAC 'MyWifi' [AC1]> (try 3/3)
[  757.082418] wlp5s0: authentication with <MAC 'MyWifi' [AC1]> timed out
[  774.671486] IPv6: ADDRCONF(NETDEV_UP): wlp5s0: link is not ready
[  779.106680] wlp5s0: authenticate with <MAC 'MyWifi-5G' [AC3]>
[  779.140614] wlp5s0: send auth to <MAC 'MyWifi-5G' [AC3]> (try 1/3)
[  779.142065] wlp5s0: send auth to <MAC 'MyWifi-5G' [AC3]> (try 2/3)
[  779.143468] wlp5s0: send auth to <MAC 'MyWifi-5G' [AC3]> (try 3/3)
[  779.144760] wlp5s0: authentication with <MAC 'MyWifi-5G' [AC3]> timed out
[  784.104023] wlp5s0: authenticate with <MAC 'MyWifi-5G' [AC3]>
[  784.136987] wlp5s0: send auth to <MAC 'MyWifi-5G' [AC3]> (try 1/3)
[  784.138530] wlp5s0: authenticated
[  784.141052] wlp5s0: associate with <MAC 'MyWifi-5G' [AC3]> (try 1/3)
[  784.142428] wlp5s0: RX AssocResp from <MAC 'MyWifi-5G' [AC3]> (capab=0x1011 status=0 aid=2)
[  784.145540] wlp5s0: associated
[  784.145554] IPv6: ADDRCONF(NETDEV_CHANGE): wlp5s0: link becomes ready
[  784.147335] ath: EEPROM regdomain: 0x8114
[  784.147336] ath: EEPROM indicates we should expect a country code
[  784.147337] ath: doing EEPROM country->regdmn map search
[  784.147337] ath: country maps to regdmn code: 0x37
[  784.147337] ath: Country alpha2 being used: DE
[  784.147338] ath: Regpair used: 0x37
[  784.147338] ath: regdomain 0x8114 dynamically updated by country IE
[  784.222515] wlp5s0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC 'MyWifi-5G' [AC3]>
[  789.568572] wlp5s0: deauthenticating from <MAC 'MyWifi-5G' [AC3]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  792.691860] wlp5s0: authenticate with <MAC 'MyWifi' [AC1]>
[  792.763678] wlp5s0: send auth to <MAC 'MyWifi' [AC1]> (try 1/3)
[  792.768461] wlp5s0: send auth to <MAC 'MyWifi' [AC1]> (try 2/3)
[  792.773240] wlp5s0: send auth to <MAC 'MyWifi' [AC1]> (try 3/3)
[  792.778137] wlp5s0: authentication with <MAC 'MyWifi' [AC1]> timed out
[  797.339630] wlp5s0: authenticate with <MAC 'MyWifi' [AC1]>
[  797.409770] wlp5s0: send auth to <MAC 'MyWifi' [AC1]> (try 1/3)
[  797.411926] wlp5s0: authenticated
[  797.412366] wlp5s0: associate with <MAC 'MyWifi' [AC1]> (try 1/3)
[  797.416445] wlp5s0: RX AssocResp from <MAC 'MyWifi' [AC1]> (capab=0x1411 status=0 aid=1)
[  797.419672] wlp5s0: associated
[  915.087613] wlp5s0: deauthenticating from <MAC 'MyWifi' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  968.693189] IPv6: ADDRCONF(NETDEV_UP): wlp5s0: link is not ready (repeated 2 times)
[  977.658079] wlp5s0: authenticate with <MAC 'MyWifi-5G' [AC3]>
[  977.691659] wlp5s0: send auth to <MAC 'MyWifi-5G' [AC3]> (try 1/3)
[  977.693065] wlp5s0: send auth to <MAC 'MyWifi-5G' [AC3]> (try 2/3)
[  977.694494] wlp5s0: send auth to <MAC 'MyWifi-5G' [AC3]> (try 3/3)
[  977.695914] wlp5s0: authentication with <MAC 'MyWifi-5G' [AC3]> timed out
[  980.841375] IPv6: ADDRCONF(NETDEV_UP): wlp5s0: link is not ready
[  982.264933] wlp5s0: authenticate with <MAC 'MyWifi' [AC1]>
[  982.337364] wlp5s0: send auth to <MAC 'MyWifi' [AC1]> (try 1/3)
[  982.342328] wlp5s0: send auth to <MAC 'MyWifi' [AC1]> (try 2/3)
[  982.347242] wlp5s0: send auth to <MAC 'MyWifi' [AC1]> (try 3/3)
[  982.352044] wlp5s0: authentication with <MAC 'MyWifi' [AC1]> timed out
[  986.912886] wlp5s0: authenticate with <MAC 'MyWifi' [AC1]>
[  986.983084] wlp5s0: send auth to <MAC 'MyWifi' [AC1]> (try 1/3)
[  986.986346] wlp5s0: authenticated
[  986.989723] wlp5s0: associate with <MAC 'MyWifi' [AC1]> (try 1/3)
[  986.994040] wlp5s0: RX AssocResp from <MAC 'MyWifi' [AC1]> (capab=0x1411 status=0 aid=1)
[  986.997087] wlp5s0: associated
[  986.997165] IPv6: ADDRCONF(NETDEV_CHANGE): wlp5s0: link becomes ready


########## wireless info END ############



```[COLOR=#111111][FONT=Ubuntu]

Note that MyWifi is 2.4GHZ (connecting fine) and MyWifi-5G is the 5ghz wifi with issues. What could be the issue?
[/FONT][/COLOR]

---

### Post by jeremy31 on 2016-11-25
It might be wifi power management causing issues, in terminal
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot

---

### Post by bkach on 2016-11-25
So just to be clear - the above script changes a power save option located in the network manager's conf.d from 3 to 2?

What does this change? How does 3 differ from 2? Also - Is there a place can I find relevant documentation about the power save settings?

---

### Post by Hadaka on 2016-11-25
Hi, the reason jeremy31 is suggesting that change is due to a known Network Manager issue
with ubuntu 16.04 and 16.10. A simple search will show you that he is very experienced with
this issue and many members have corrected their problem by making the power save change.
Your wireless report shows Power Management [COLOR=#ff0000]ON[/COLOR] it should be OFF.
```
wlp5s0    IEEE 802.11  ESSID:"MyWifi"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'MyWifi' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management-[COLOR=#ff0000]on[/COLOR]
          Link Quality=[COLOR=#ff0000]23/70[/COLOR]  Signal level=-87 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:79   Missed beacon:0
```
You also have VERY low signal quality..23/70
so between these two issues alone,its not likely you will have a solid connection.

As you can also see from the dmesg section of the wireless diagnostic report.
```
wlp5s0: deauthenticating from <MAC 'MyWifi' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)

 wlp5s0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC 'MyWifi-5G' [AC3]>
wlp5s0: deauthenticating from <MAC 'MyWifi-5G' [AC3]> by local choice (Reason: 3=DEAUTH_LEAVING
```

The Power Management ON is causing the access point connection to leave and try the next possible connection,
and that is why you toggle between the 2.4 Ghz and 5Ghz connections....AC1...AC3

Then to further confuse the connection the EEPROM chip on your wireless card has been set to a code that = DE...Germany
DE    +5230+01322    Europe/Berlin    Germany (most areas)
yet per your isp region input you show,,, Europe/Stockholm  =  SE
*System setting to DE
```
[  723.469955] ath: EEPROM regdomain: 0x8114
[  723.469957] ath: EEPROM indicates we should expect a country code
[  723.469959] ath: doing EEPROM country->regdmn map search
[  723.469961] ath: country maps to regdmn code: 0x37
[  723.469963] ath: Country alpha2 being used: DE
[  723.469964] ath: Regpair used: 0x37

```
To correct this if you are in fact in Stockholm ..SE    +5920+01803    Europe/Stockholm
Copy and paste the following to set to SE
```
sudo iw reg set SE
sudo sed -i 's/^REG.*=$/&SE/' /etc/default/crda
```
```
sudo sed -i '/^exit/ d' /etc/rc.local
echo -e "sudo iw reg set SE\nexit 0" | sudo tee -a /etc/rc.local
```
Hope this gives you a better understanding as to why the suggested commands were given.
I suggest you start with the ones jeremy31 gave you and these, using a working wired connection and
then remove the wired connection, boot and test wireless.
thanks.

---

### Post by jeremy31 on 2016-11-26
> **bkach said:**
> So just to be clear - the above script changes a power save option located in the network manager's conf.d from 3 to 2?

What does this change? How does 3 differ from 2? Also - Is there a place can I find relevant documentation about the power save settings?

I don't know where documentation might be found, but here is part of the source code
```
/**
 * NMSettingWirelessPowersave:
 * @NM_SETTING_WIRELESS_POWERSAVE_DEFAULT: use the default value
 * @NM_SETTING_WIRELESS_POWERSAVE_IGNORE: don't touch existing setting
 * @NM_SETTING_WIRELESS_POWERSAVE_DISABLE: disable powersave
 * @NM_SETTING_WIRELESS_POWERSAVE_ENABLE: enable powersave
 *
 * These flags indicate whether wireless powersave must be enabled.
 **/
typedef enum {
	NM_SETTING_WIRELESS_POWERSAVE_DEFAULT       = 0,
	NM_SETTING_WIRELESS_POWERSAVE_IGNORE        = 1,
	NM_SETTING_WIRELESS_POWERSAVE_DISABLE       = 2,
	NM_SETTING_WIRELESS_POWERSAVE_ENABLE        = 3,
```

There are some posts that say changing it to 0 works but it doesn't as I found out on a laptop with an Intel wifi card

---

### Post by bkach on 2016-11-26
Thanks for the documentation! I'm pretty new to Linux, and love the fact that you can kust check the source at any time if you're unsure of something :).

I've tried all the above options - and while they didn't fix the problem, i feel we are getting warmer.

With respect to the power saving option, i set it to 2 but still seem to be getting the same line, namely:

```

wlp5s0: Limiting TX power to 30 (30 - 0) dBm as advertised by dc:53:7c:c6:b6:8b

```

Which i'm guessing results in:

```

wlp5s0: deauthenticating from dc:53:7c:c6:b6:8b by local choice (Reason: 3=DEAUTH_LEAVING)

```

Does this mean it is somehow still on? Is there another way to reset the power saving options?

With respect to the Country Code, I am currently in Sweden - so I changed it to SE via reg set and in the rc.local (which did not already exist, so i created a new file). Still I seem to run into these issues:

```

[  819.682134] ath: EEPROM regdomain: 0x8114
[  819.682136] ath: EEPROM indicates we should expect a country code
[  819.682138] ath: doing EEPROM country->regdmn map search
[  819.682139] ath: country maps to regdmn code: 0x37
[  819.682141] ath: Country alpha2 being used: DE
[  819.682142] ath: Regpair used: 0x37
[  819.682144] ath: regdomain 0x8114 dynamically updated by country IE

```

Would leaving it blank means that this issue would resolve itself? What use is the country code?

Here's my current Network Script:

```



########## wireless info START ##########


Report from: 26 Nov 2016 16:34 CET +0100


Booted last: 26 Nov 2016 00:00 CET +0100


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.10
Release:    16.10
Codename:    yakkety


##### kernel ############################


Linux 4.8.0-27-generic #29-Ubuntu SMP Thu Oct 20 21:03:13 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-V [8086:15b8] (rev 31)
    Subsystem: ASUSTeK Computer Inc. Ethernet Connection (2) I219-V [1043:8672]
    Kernel driver in use: e1000e


05:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
    Subsystem: ASUSTeK Computer Inc. QCA6174 802.11ac Wireless Network Adapter [1043:86e0]
    Kernel driver in use: ath10k_pci


##### lsusb #############################


Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 045e:0719 Microsoft Corp. Xbox 360 Wireless Adapter
Bus 003 Device 002: ID 28de:1142  
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1af3:0001  
Bus 001 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 005: ID 0b05:1825 ASUSTek Computer, Inc. 
Bus 001 Device 004: ID 04d9:0141 Holtek Semiconductor, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: hci1: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
mxm_wmi                16384  0
sparse_keymap          16384  1 asus_wmi
ath10k_pci             45056  0
ath10k_core           335872  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              757760  1 ath10k_core
cfg80211              581632  3 mac80211,ath,ath10k_core
wmi                    16384  2 asus_wmi,mxm_wmi
video                  40960  1 asus_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp0s31f6: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  memory 0xf7100000-f7120000  


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 287  bytes 29352 (29.3 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 287  bytes 29352 (29.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlp5s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.3  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::f415:c7a4:6b:4a7f  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 2645  bytes 2163677 (2.1 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 3123  bytes 567021 (567.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


lo        no wireless extensions.


enp0s31f6  no wireless extensions.


wlp5s0    IEEE 802.11  ESSID:"MyWifi"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'MyWifi' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=22/70  Signal level=-88 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:40  Invalid misc:26   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp5s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp5s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp5s0


##### resolv.conf #######################


nameserver 209.222.18.222
nameserver 209.222.18.218


##### network managers ##################


Installed:


    NetworkManager


Running:


root       904     1  0 16:29 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp5s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA6174 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.8.0-27-generic
GENERAL.FIRMWARE-VERSION:               WLAN.RM.2.0-00180-QCARMSWPZ-1
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.1/0000:05:00.0/net/wlp5s0
GENERAL.IP-IFACE:                       wlp5s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     MyWifi
GENERAL.CON-UUID:                       9cf42b23-9a04-4f3f-85cf-c5e268ed8808
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1,0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   67b7a315-fa0b-4200-8b04-72dafc519e90 | MyWifi-5G
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   9cf42b23-9a04-4f3f-85cf-c5e268ed8808 | MyWifi
IP4.ADDRESS[1]:                         192.168.0.3/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             83.255.255.2
IP4.DNS[2]:                             83.255.255.1
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 83.255.255.2 83.255.255.1
DHCP4.OPTION[5]:                        ip_address = 192.168.0.3
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[8]:                        default_ip_ttl = 64
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       time_offset = 0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_rebinding_time = 9450
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       requested_broadcast_address = 1
DHCP4.OPTION[17]:                       routers = 192.168.0.1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 5400
DHCP4.OPTION[19]:                       requested_domain_name = 1
DHCP4.OPTION[20]:                       domain_name = home
DHCP4.OPTION[21]:                       requested_routers = 1
DHCP4.OPTION[22]:                       expiry = 1480185234
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_netbios_scope = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.0.0
DHCP4.OPTION[28]:                       requested_domain_search = 1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       next_server = 192.168.0.1
DHCP4.OPTION[31]:                       dhcp_lease_time = 10800
DHCP4.OPTION[32]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         fe80::f415:c7a4:6b:4a7f/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp0s31f6
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (2) I219-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.8-4
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1f.6/net/enp0s31f6
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
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID               BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
MyWifi-5G       <MAC 'MyWifi-5G' [AC3]>  Infra  100   5500 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA2      no        
MyWifi          <MAC 'MyWifi' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA2      yes     * 
otherwifi   <MAC 'otherwifi' [AC2]>  Infra  36    5180 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA2      no        
belkin.a55         <MAC 'belkin.a55' [AN4]>  Infra  6     2437 MHz  54 Mbit/s  25      &#9602;___  WPA2      no        
belkin.a55.guests  <MAC 'belkin.a55.guests' [AN5]>  Infra  6     2437 MHz  54 Mbit/s  24      &#9602;___  --        no        


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


[[/etc/NetworkManager/system-connections/MyWifi]] (600 root)
[connection] id=MyWifi | type=wifi | permissions=user:boris:;
[wifi] bssid=<MAC 'MyWifi' [AC1]> | mac-address=<MAC address> | mac-address-blacklist= | ssid=MyWifi
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/MyWifi-5G]] (600 root)
[connection] id=MyWifi-5G | type=wifi | permissions=
[wifi] bssid=<MAC 'MyWifi-5G' [AC3]> | mac-address=<MAC address> | mac-address-blacklist= | ssid=MyWifi-5G
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Stockholm (based on set time zone)


country SE: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


lo        no frequency information.


enp0s31f6  no frequency information.


wlp5s0    31 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp0s31f6  Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:5.18 GHz (Channel 36)
      1   APs on   Frequency:5.5 GHz (Channel 100)


wlp5s0    Scan completed :
          Cell 01 - Address: <MAC 'MyWifi' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"MyWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000edca47912
                    Extra: Last beacon: 3512ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'otherwifi' [AC2]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"otherwifi"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005b6beb203a
                    Extra: Last beacon: 4052ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'MyWifi-5G' [AC3]>
                    Channel:100
                    Frequency:5.5 GHz (Channel 100)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"MyWifi-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000614045504d
                    Extra: Last beacon: 2296ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ath10k_pci]
filename:       /lib/modules/4.8.0-27-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
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
srcversion:     D5C1D197B1BB08AC45E6566
depends:        ath10k_core
intree:         Y
vermagic:       4.8.0-27-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)


[ath10k_core]
filename:       /lib/modules/4.8.0-27-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for Qualcomm Atheros 802.11ac wireless LAN cards.
author:         Qualcomm Atheros
srcversion:     B60553BE2B6B3F262752ADD
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.8.0-27-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)


[ath]
filename:       /lib/modules/4.8.0-27-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     5C13C1638BE3EDB7B93F6A7
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-27-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.8.0-27-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     BDE5CB0CC0A980B65D19934
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-27-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.8.0-27-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F170FED576AF12B070D2E69
depends:        
intree:         Y
vermagic:       4.8.0-27-generic SMP mod_unload modversions 
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


sudo iw reg set SE
exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[    4.295966] ath10k_pci 0000:05:00.0: htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[    4.382499] ath: EEPROM regdomain: 0x69
[    4.382499] ath: EEPROM indicates we should expect a direct regpair map
[    4.382500] ath: Country alpha2 being used: 00
[    4.382501] ath: Regpair used: 0x69
[    4.385721] ath10k_pci 0000:05:00.0 wlp5s0: renamed from wlan0
[    4.413644] IPv6: ADDRCONF(NETDEV_UP): wlp5s0: link is not ready (repeated 3 times)
[   13.784880] wlp5s0: authenticate with <MAC 'MyWifi-5G' [AC3]>
[   13.821154] wlp5s0: send auth to <MAC 'MyWifi-5G' [AC3]> (try 1/3)
[   13.822620] wlp5s0: send auth to <MAC 'MyWifi-5G' [AC3]> (try 2/3)
[   13.823888] wlp5s0: send auth to <MAC 'MyWifi-5G' [AC3]> (try 3/3)
[   13.825202] wlp5s0: authentication with <MAC 'MyWifi-5G' [AC3]> timed out
[   17.479908] wlp5s0: authenticate with <MAC 'MyWifi-5G' [AC3]>
[   17.513275] wlp5s0: send auth to <MAC 'MyWifi-5G' [AC3]> (try 1/3)
[   17.514652] wlp5s0: authenticated
[   17.517975] wlp5s0: associate with <MAC 'MyWifi-5G' [AC3]> (try 1/3)
[   17.521833] wlp5s0: RX AssocResp from <MAC 'MyWifi-5G' [AC3]> (capab=0x1011 status=0 aid=1)
[   17.525170] wlp5s0: associated
[   17.525254] IPv6: ADDRCONF(NETDEV_CHANGE): wlp5s0: link becomes ready
[   17.530778] ath: EEPROM regdomain: 0x8114
[   17.530780] ath: EEPROM indicates we should expect a country code
[   17.530782] ath: doing EEPROM country->regdmn map search
[   17.530784] ath: country maps to regdmn code: 0x37
[   17.530785] ath: Country alpha2 being used: DE
[   17.530787] ath: Regpair used: 0x37
[   17.530789] ath: regdomain 0x8114 dynamically updated by country IE
[   17.565910] wlp5s0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC 'MyWifi-5G' [AC3]>
[   63.054800] wlp5s0: deauthenticating from <MAC 'MyWifi-5G' [AC3]> by local choice (Reason: 3=DEAUTH_LEAVING)
[   66.610679] wlp5s0: authenticate with <MAC 'MyWifi-5G' [AC3]>
[   66.644072] wlp5s0: send auth to <MAC 'MyWifi-5G' [AC3]> (try 1/3)
[   66.645414] wlp5s0: send auth to <MAC 'MyWifi-5G' [AC3]> (try 2/3)
[   66.646753] wlp5s0: send auth to <MAC 'MyWifi-5G' [AC3]> (try 3/3)
[   66.648096] wlp5s0: authentication with <MAC 'MyWifi-5G' [AC3]> timed out
[   70.288623] wlp5s0: authenticate with <MAC 'MyWifi-5G' [AC3]>
[   70.321587] wlp5s0: send auth to <MAC 'MyWifi-5G' [AC3]> (try 1/3)
[   70.323896] wlp5s0: authenticated
[   70.326221] wlp5s0: associate with <MAC 'MyWifi-5G' [AC3]> (try 1/3)
[   70.328106] wlp5s0: RX AssocResp from <MAC 'MyWifi-5G' [AC3]> (capab=0x1011 status=0 aid=1)
[   70.331376] wlp5s0: associated
[   70.337580] ath: EEPROM regdomain: 0x8114
[   70.337582] ath: EEPROM indicates we should expect a country code
[   70.337584] ath: doing EEPROM country->regdmn map search
[   70.337585] ath: country maps to regdmn code: 0x37
[   70.337587] ath: Country alpha2 being used: DE
[   70.337588] ath: Regpair used: 0x37
[   70.337591] ath: regdomain 0x8114 dynamically updated by country IE
[   70.405430] wlp5s0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC 'MyWifi-5G' [AC3]>
[  252.370625] wlp5s0: deauthenticating from <MAC 'MyWifi-5G' [AC3]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  256.130721] wlp5s0: authenticate with <MAC 'MyWifi' [AC1]>
[  256.203195] wlp5s0: send auth to <MAC 'MyWifi' [AC1]> (try 1/3)
[  256.208058] wlp5s0: send auth to <MAC 'MyWifi' [AC1]> (try 2/3)
[  256.212974] wlp5s0: send auth to <MAC 'MyWifi' [AC1]> (try 3/3)
[  256.217972] wlp5s0: authentication with <MAC 'MyWifi' [AC1]> timed out
[  259.873282] wlp5s0: authenticate with <MAC 'MyWifi' [AC1]>
[  259.945004] wlp5s0: send auth to <MAC 'MyWifi' [AC1]> (try 1/3)
[  259.949886] wlp5s0: send auth to <MAC 'MyWifi' [AC1]> (try 2/3)
[  259.954610] wlp5s0: send auth to <MAC 'MyWifi' [AC1]> (try 3/3)
[  259.959632] wlp5s0: authenticated
[  259.963220] wlp5s0: associate with <MAC 'MyWifi' [AC1]> (try 1/3)
[  259.974078] wlp5s0: associate with <MAC 'MyWifi' [AC1]> (try 2/3)
[  259.987428] wlp5s0: associate with <MAC 'MyWifi' [AC1]> (try 3/3)
[  260.000067] wlp5s0: association with <MAC 'MyWifi' [AC1]> timed out
[  264.045817] wlp5s0: authenticate with <MAC 'MyWifi' [AC1]>
[  264.116773] wlp5s0: send auth to <MAC 'MyWifi' [AC1]> (try 1/3)
[  264.121623] wlp5s0: send auth to <MAC 'MyWifi' [AC1]> (try 2/3)
[  264.126648] wlp5s0: send auth to <MAC 'MyWifi' [AC1]> (try 3/3)
[  264.131549] wlp5s0: authentication with <MAC 'MyWifi' [AC1]> timed out
[  268.678558] wlp5s0: authenticate with <MAC 'MyWifi' [AC1]>
[  268.750302] wlp5s0: send auth to <MAC 'MyWifi' [AC1]> (try 1/3)
[  268.754530] wlp5s0: authenticated
[  268.755334] wlp5s0: associate with <MAC 'MyWifi' [AC1]> (try 1/3)
[  268.766373] wlp5s0: associate with <MAC 'MyWifi' [AC1]> (try 2/3)
[  268.775100] wlp5s0: RX AssocResp from <MAC 'MyWifi' [AC1]> (capab=0x1411 status=0 aid=2)
[  268.778087] wlp5s0: associated


########## wireless info END ############

```

One curious thing i happened to see in the demesg. It looks like my firmware hasn't loaded.

```

[    2.111620] ath10k_pci 0000:05:00.0: Direct firmware load for ath10k/pre-cal-pci-0000:05:00.0.bin failed with error -2
[    2.111625] ath10k_pci 0000:05:00.0: Direct firmware load for ath10k/cal-pci-0000:05:00.0.bin failed with error -2
[    2.111834] ath10k_pci 0000:05:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[    2.111835] ath10k_pci 0000:05:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2

```

Could this be the issue?

Interestingly enough, i manage now to sometimes connect to the 5ghz network and sometimes to the 2.4ghz, but never for too long.

Any idea on what else might be the issue?

---

### Post by jeremy31 on 2016-11-26
Did you buy your router in Germany or have the country set to Germany in the router settings?

Limiting the TX power is coming from the router and the info it transmits and your report shows Tx-Power=20 dBm  which should work but the signal from the router is a bit weak and that could be an issue of antenna orientation.

I don't think those firmware files have ever existed for your wifi chip and it might be something that will be implemented later.  If you ```
cat /lib/firmware/ath10k/QCA6174/hw3.0
```
You will likely see board.bin, board-2.bin, and firmware-4.bin

You may have to see if you can increase the output power on the router, move the laptop closer to the router, or use a booster/repeater for the wifi.

You could look up the ath10k developers mailing list and ask them if there is a way to increase the RX side of the wifi chip as there is likely an amplifier circuit on the input

---

