---
title: "Wireless intermittently disconnects"
date: 2018-06-20
forum: Networking &amp; Wireless
---

### Post by tri++ on 2018-06-20
I used to have to restart my network manager every 5 minutes to get my wifi to stay on. Dmesg would say "failed to remove key from hardware" until I updated my kernel to 4.17. I no longer get the "failed to remove key" messages, but I still have to restart my network manager every 5 minutes to get anything to work. I also attached the output of the wireless debug script.

I have already tried adding wlp2s0 to SUSPEND_MODULES.

---

### Post by tri++ on 2018-10-05
Bump, I still have this problem and still have no idea what to do about it

---

### Post by QIII on 2018-10-05
Hello!

Leaving a thread for several months to sink beneath the muck at the bottom of the ocean is a sure path to receiving no help.  Nobody goes looking for threads there.

If you do not receive a reply withing about 12 hours, feel free to bump your post.

Cheers!

---

### Post by EmilyRose on 2018-10-05
I am also having this problem, running Ubuntu 18.04 on a Lenovo L540 with Intel wifi. Sometimes running sudo services network-manager restart will fix it, but at least 1/2 the time a reset is required. It seems that the wifi card simply turns off and becomes unavailble - or thats what network manager says (Wifi unavailble - no wifi card; sometimes at first it will say Unavailable - 802.1x supplicant failed)

lspci:
```
02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6235 [8086:088f] (rev 24)
	Subsystem: Intel Corporation Centrino Advanced-N 6235 [8086:5260]
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi
0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

wireless-info script:
```
########## wireless info START ##########

Report from: 05 Oct 2018 15:30 EDT -0400

Booted last: 05 Oct 2018 00:00 EDT -0400

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.1 LTS
Release:	18.04
Codename:	bionic

##### kernel ############################

Linux 4.15.0-36-generic #39-Ubuntu SMP Mon Sep 24 16:19:09 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

GNOME on Xorg

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-LM [8086:153a] (rev 05)
	Subsystem: Lenovo Ethernet Connection I217-LM [17aa:501e]
	Kernel driver in use: e1000e

02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6235 [8086:088f] (rev 24)
	Subsystem: Intel Corporation Centrino Advanced-N 6235 [8086:5260]
	Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 138a:0011 Validity Sensors, Inc. VFS5011 Fingerprint Reader
Bus 003 Device 004: ID 04f2:b398 Chicony Electronics Co., Ltd 
Bus 003 Device 003: ID 8087:07da Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

iwldvm                229376  0
mac80211              778240  1 iwldvm
iwlwifi               282624  1 iwldvm
wmi_bmof               16384  0
cfg80211              622592  3 iwlwifi,mac80211,iwldvm
wmi                    24576  1 wmi_bmof

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s25: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xf2500000-f2520000  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 77  bytes 6752 (6.7 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 77  bytes 6752 (6.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.87.120  netmask 255.255.255.0  broadcast 192.168.87.255
        inet6 fe80::c719:fb71:86ab:278  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 64396  bytes 92219682 (92.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 34948  bytes 3760017 (3.7 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

enp0s25   no wireless extensions.

lo        no wireless extensions.

wlp2s0    IEEE 802.11  ESSID:"linksys"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'linksys' [AC1]>   
          Bit Rate=48 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:620   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.87.1    0.0.0.0         UG    600    0        0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0
192.168.87.0    0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

	NetworkManager
	Wicd

Running:

root       812     1  0 15:17 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Centrino Advanced-N 6235
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.15.0-36-generic
GENERAL.FIRMWARE-VERSION:               18.168.6.1
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     linksys 4
GENERAL.CON-UUID:                       e81256d6-a5dd-4f67-9c6a-b2f247420740
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     54 Mb/s
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
IP4.ADDRESS[1]:                         192.168.87.120/24
IP4.GATEWAY:                            192.168.87.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.87.1, mt = 600
IP4.ROUTE[2]:                           dst = 192.168.87.0/24, nh = 0.0.0.0, mt = 600
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             8.8.8.8
IP4.DNS[2]:                             8.8.4.4
DHCP4.OPTION[1]:                        network_number = 192.168.87.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        expiry = 1538853453
DHCP4.OPTION[8]:                        requested_netbios_scope = 1
DHCP4.OPTION[9]:                        next_server = 192.168.87.1
DHCP4.OPTION[10]:                       broadcast_address = 192.168.87.255
DHCP4.OPTION[11]:                       dhcp_message_type = 5
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.87.1
DHCP4.OPTION[14]:                       ip_address = 192.168.87.120
DHCP4.OPTION[15]:                       dhcp_lease_time = 86400
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       requested_wpad = 1
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       domain_name_servers = 8.8.8.8 8.8.4.4
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       requested_interface_mtu = 1
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.87.1
IP6.ADDRESS[1]:                         fe80::c719:fb71:86ab:278/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 600
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{24}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   e81256d6-a5dd-4f67-9c6a-b2f247420740 | linksys 4

GENERAL.DEVICE:                         enp0s25
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection I217-LM
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.13-3
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/enp0s25
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

SSID     BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  IN-USE 
linksys  <MAC 'linksys' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  56      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     *      

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

[[/etc/NetworkManager/system-connections/linksys 1]] (600 root)
[connection] id=linksys 1 | type=wifi | permissions=
[wifi] bssid=<MAC 'linksys3' [AC2]> | mac-address=<MAC address> | mac-address-blacklist= | ssid=linksys
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/akgenwifi]] (600 root)
[connection] id=akgenwifi | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=akgenwifi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/linksys]] (600 root)
[connection] id=linksys | type=wifi | permissions=
[wifi] bssid=<MAC 'linksys' [AC1]> | mac-address=<MAC address> | mac-address-blacklist= | ssid=linksys
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/linksys 3]] (600 root)
[connection] id=linksys 3 | type=wifi | permissions=
[wifi] bssid=<MAC 'linksys3' [AC2]> | mac-address=<MAC address> | mac-address-blacklist= | ssid=linksys
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/linksys3]] (600 root)
[connection] id=linksys3 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=linksys3
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/linksys 4]] (600 root)
[connection] id=linksys 4 | type=wifi | permissions=
[wifi] bssid=<MAC 'linksys' [AC1]> | mac-address=<MAC address> | mac-address-blacklist= | ssid=linksys
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Loudon Motors Ford - Guest]] (600 root)
[connection] id=Loudon Motors Ford - Guest | type=wifi | permissions=user:andros:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Loudon Motors Ford - Guest
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/linksys 2]] (600 root)
[connection] id=linksys 2 | type=wifi | permissions=
[wifi] bssid=<MAC 'linksys3' [AC2]> | mac-address=<MAC address> | mac-address-blacklist= | ssid=linksys
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/agmccisco]] (600 root)
[connection] id=agmccisco | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=agmccisco
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Insight_wifi_0D4A]] (600 root)
[connection] id=Insight_wifi_0D4A | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Insight_wifi_0D4A
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: America/New_York (based on set time zone)

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

enp0s25   no frequency information.

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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

enp0s25   Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)

wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'linksys' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000253cad3e7e
                    Extra: Last beacon: 100ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'linksys3' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"linksys3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ce0b9dec54
                    Extra: Last beacon: 5512ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwldvm]
filename:       /lib/modules/4.15.0-36-generic/kernel/drivers/net/wireless/intel/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     5144A889CD9311D5F87BAC3
depends:        mac80211,iwlwifi,cfg80211
retpoline:      Y
intree:         Y
name:           iwldvm
vermagic:       4.15.0-36-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           force_cam:force continuously aware mode (no power saving at all) (bool)

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

[iwlwifi]
filename:       /lib/modules/4.15.0-36-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
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
firmware:       iwlwifi-6000g2a-6.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-6.ucode
firmware:       iwlwifi-7265D-29.ucode
firmware:       iwlwifi-7265-17.ucode
firmware:       iwlwifi-3168-29.ucode
firmware:       iwlwifi-3160-17.ucode
firmware:       iwlwifi-7260-17.ucode
firmware:       iwlwifi-8265-34.ucode
firmware:       iwlwifi-8000C-34.ucode
firmware:       iwlwifi-9260-th-b0-jf-b0-34.ucode
firmware:       iwlwifi-9260-th-a0-jf-a0-34.ucode
firmware:       iwlwifi-9000-pu-a0-jf-b0-34.ucode
firmware:       iwlwifi-9000-pu-b0-jf-b0-34.ucode
firmware:       iwlwifi-9000-pu-a0-jf-a0-34.ucode
firmware:       iwlwifi-QuQnj-a0-hr-a0-34.ucode
firmware:       iwlwifi-QuQnj-a0-jf-b0-34.ucode
firmware:       iwlwifi-QuQnj-f0-hr-a0-34.ucode
firmware:       iwlwifi-Qu-a0-jf-b0-34.ucode
firmware:       iwlwifi-Qu-a0-hr-a0-34.ucode
srcversion:     C57A4F9C9842C4EC8599634
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           iwlwifi
vermagic:       4.15.0-36-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size:amsdu size 0: 12K for multi Rx queue devices, 4K for other devices 1:4K 2:8K 3:12K (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality bitmap 1: BSS 2: P2P Client (default: 3) (uint)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)
parm:           d0i3_timeout:Timeout to D0i3 entry when idle (ms) (uint)
parm:           disable_11ac:Disable VHT capabilities (default: false) (bool)

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

[iwldvm]
force_cam: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
d0i3_timeout: 1000
disable_11ac: N
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: 3

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

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   17.984409] iwlwifi 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[   18.491325] iwlwifi 0000:02:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[   18.504570] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   18.504573] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   18.504574] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   18.504576] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Advanced-N 6235 AGN, REV=0xB0
[   18.540914] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   18.542011] iwlwifi 0000:02:00.0 wlp2s0: renamed from wlan0
[   28.052449] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   28.064222] iwlwifi 0000:02:00.0: Radio type=0x2-0x1-0x0 (repeated 2 times)
[   28.445528] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[   31.861640] wlp2s0: authenticate with <MAC 'linksys' [AC1]>
[   31.862739] wlp2s0: send auth to <MAC 'linksys' [AC1]> (try 1/3)
[   31.867094] wlp2s0: authenticated
[   31.867253] iwlwifi 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[   31.867254] iwlwifi 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[   31.867983] wlp2s0: associate with <MAC 'linksys' [AC1]> (try 1/3)
[   31.870492] wlp2s0: RX AssocResp from <MAC 'linksys' [AC1]> (capab=0x411 status=0 aid=8)
[   31.872953] wlp2s0: associated
[   32.051536] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready

########## wireless info END ############
 
```

---

### Post by EmilyRose on 2018-10-06
So, I just got home, and when I turned my laptop on was met with:

```
1802 Unauthorized network card is plugged in - Power off and remove the network card (0A12/001). 
System is halted
```

After a bit of googling, it sounded as though my wifi/network card may have been dead... so I pulled it and sure enough, it turned on just fine. Luckily I have a spare dying Thinkpad and I was able to pull its network  card and am now back up and running. We'll see if I continue to get randomly disconnected. Also tried the pulled one in the other laptop and have the same error on it (it simply turns off at random, and sometimes won't boot...).

---

