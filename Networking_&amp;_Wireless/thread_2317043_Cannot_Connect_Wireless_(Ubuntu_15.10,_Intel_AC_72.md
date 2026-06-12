---
title: "Cannot Connect Wireless (Ubuntu 15.10, Intel AC 7260)"
date: 2016-03-12
forum: Networking &amp; Wireless
---

### Post by Louis11 on 2016-03-12
I can't seem to get my wireless card working. I have an Intel AC 7260 (rev bb). I've tried everything, and nothing seems to work. Here is the output from the wireless script:

```

########## wireless info START ##########

Report from: 12 Mar 2016 22:23 CST -0600

Booted last: 12 Mar 2016 00:00 CST -0600

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 15.10
Release:	15.10
Codename:	wily

##### kernel ############################

Linux 4.2.0-30-generic #36-Ubuntu SMP Fri Feb 26 00:58:07 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I218-V [8086:15a1]
	DeviceName:  Onboard LAN
	Subsystem: ASUSTeK Computer Inc. Device [1043:85c4]

03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev bb)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4070]
	Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 004 Device 002: ID 8087:8001 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8009 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 1532:0502 Razer USA, Ltd 
Bus 001 Device 005: ID 0b38:0010 Gear Head 107-Key Keyboard
Bus 001 Device 004: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 003: ID 8087:07dc Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no

##### lsmod #############################

eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
mxm_wmi                16384  0
sparse_keymap          16384  1 asus_wmi
iwlmvm                294912  0
mac80211              733184  1 iwlmvm
iwlwifi               200704  1 iwlmvm
cfg80211              548864  3 iwlwifi,mac80211,iwlmvm
wmi                    20480  2 mxm_wmi,asus_wmi
video                  40960  1 asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eno1      Link encap:Ethernet  HWaddr <MAC 'eno1' [IF]>  
          inet addr:192.168.2.8  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eno1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6611 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4230 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7938370 (7.9 MB)  TX bytes:454242 (454.2 KB)
          Interrupt:20 Memory:f7200000-f7220000 

wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eno1      no wireless extensions.

lo        no wireless extensions.

wlp3s0    IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 eno1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eno1
192.168.2.0     0.0.0.0         255.255.255.0   U     100    0        0 eno1

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root      1055     1  0 22:05 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (2) I218-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.5-k
GENERAL.FIRMWARE-VERSION:               0.1-4
GENERAL.HWADDR:                         <MAC 'eno1' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/eno1
GENERAL.IP-IFACE:                       eno1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       aa19ee46-28b9-46c6-bb79-49ba0e10e5b6
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   aa19ee46-28b9-46c6-bb79-49ba0e10e5b6 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.2.8/24
IP4.GATEWAY:                            192.168.2.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.2.1
DHCP4.OPTION[1]:                        requested_host_name = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        server_name = Computer-2.local
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_time_offset = 1
DHCP4.OPTION[8]:                        expiry = 1457927493
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       next_server = 192.168.2.1
DHCP4.OPTION[11]:                       broadcast_address = 192.168.2.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.2.1
DHCP4.OPTION[15]:                       dhcp_lease_time = 85536
DHCP4.OPTION[16]:                       ip_address = 192.168.2.8
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       domain_name_servers = 192.168.2.1
DHCP4.OPTION[21]:                       requested_netbios_scope = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       network_number = 192.168.2.0
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.2.1
IP6.ADDRESS[1]:                         fe80::<IP6 'eno1' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 7260 (Dual Band Wireless-AC 7260)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.2.0-30-generic
GENERAL.FIRMWARE-VERSION:               25.30.13.0
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID                   BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
NETGEAR02-arlo_247004  <MAC 'NETGEAR02-arlo_247004' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  27      &#9602;___  WPA2       no        
belkin.0fc.media       <MAC 'belkin.0fc.media' [AC3]>  Infra  40    5200 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2  no        
ATT5w9n2T7             <MAC 'ATT5w9n2T7' [AC2]>  Infra  11    2462 MHz  54 Mbit/s  20      &#9602;___  WPA1 WPA2  no        

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

[[/etc/NetworkManager/system-connections/Ministry of Magic]] (600 root)
[connection] id=Ministry of Magic | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF]> | mac-address-blacklist= | ssid=Ministry of Magic
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Foobar]] (600 root)
[connection] id=Foobar | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF]> | mac-address-blacklist= | ssid=Foobar
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

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

eno1      no frequency information.

lo        no frequency information.

wlp3s0    32 channels in total; available frequencies :
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

eno1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.417 GHz (Channel 2)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.2 GHz (Channel 40)
      1   APs on   Frequency:5.765 GHz

wlp3s0    Scan completed :
          Cell 01 - Address: <MAC 'NETGEAR02-arlo_247004' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR02-arlo_247004"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000004745b4124
                    Extra: Last beacon: 3024ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'ATT5w9n2T7' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"ATT5w9n2T7"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000016d0b1df183
                    Extra: Last beacon: 9296ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'belkin.0fc.media' [AC3]>
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"belkin.0fc.media"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000163368ad
                    Extra: Last beacon: 88ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'belkin.0fc' [AC4]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"belkin.0fc"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000015a1817c
                    Extra: Last beacon: 10468ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Foobar' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Foobar"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000004745b4454
                    Extra: Last beacon: 3024ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'AT<MAC address>T' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"AT&T"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000016d0ae744fe
                    Extra: Last beacon: 9280ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'Ministry of Magic' [AC7]>
                    Channel:153
                    Frequency:5.765 GHz
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"Ministry of Magic"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000474249040
                    Extra: Last beacon: 6540ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     AB0A216C6A2C8AD07166628
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        AA:46:91:2A:20:E4:E1:7B:1E:4A:6C:CC:08:BD:3C:70:D4:D8:F4:64
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/4.2.0-30-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     292BCC26A10EA884DF6B5FF
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        AA:46:91:2A:20:E4:E1:7B:1E:4A:6C:CC:08:BD:3C:70:D4:D8:F4:64
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
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
firmware:       iwlwifi-7265D-12.ucode
firmware:       iwlwifi-7265-12.ucode
firmware:       iwlwifi-3160-12.ucode
firmware:       iwlwifi-7260-12.ucode
firmware:       iwlwifi-8000-12.ucode
srcversion:     2AFF7BF1EB0D33D3ACDC867
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        AA:46:91:2A:20:E4:E1:7B:1E:4A:6C:CC:08:BD:3C:70:D4:D8:F4:64
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/4.2.0-30-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        AA:46:91:2A:20:E4:E1:7B:1E:4A:6C:CC:08:BD:3C:70:D4:D8:F4:64
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2
tfd_q_hang_detect: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[iwlwifi]
11n_disable: 1
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 1
uapsd_disable: Y

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
options iwlwifi 11n_disable=1 swcrypto=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[    2.270930] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    2.298831] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
[    4.194458] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[    4.194544] iwlwifi 0000:03:00.0: L1 Disabled - LTR Enabled (repeated 4 times)
[    4.412674] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[    4.448773] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready (repeated 2 times)
[    4.859425] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[    7.866024] e1000e: eno1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[    7.866054] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready
[  179.245181] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 3 times)
[  896.457788] wlp3s0: authenticate with <MAC 'Foobar' [AC5]>
[  896.460845] wlp3s0: direct probe to <MAC 'Foobar' [AC5]> (try 1/3)
[  896.661974] wlp3s0: direct probe to <MAC 'Foobar' [AC5]> (try 2/3)
[  896.866334] wlp3s0: direct probe to <MAC 'Foobar' [AC5]> (try 3/3)
[  897.069765] wlp3s0: authentication with <MAC 'Foobar' [AC5]> timed out
[  901.844665] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready

########## wireless info END ############

```

The card seems to be functioning in that it can actually scan for networks. Earlier today I was running Ubuntu 14.04. I was able to successfully connect the card when the machine was about 3ft away from the router. When I moved the machine further I was no longer able to connect. It was suggested to me that the problem may be corrected with a newer kernel/driver so I went ahead and upgraded the machine to 15.10 (clean install). This did not seem to resolve the issue, and I still cannot seem to get the wireless working. I've tried disabling wireless N, as is suggested in several other forums... nothing.

I've also tried getting the newest firmware (and placing it in /lib/firmware) as suggested in a few other posts... still nothing.

Any ideas on what else I can try?

---

### Post by Hadaka on 2016-03-13
Hi,please try this gift from chili555.
Download this file to your desktop: [https://www.kernel.org/pub/linux/ker...4-rc2-1.tar.gz](https://www.kernel.org/pub/linux/ker...4-rc2-1.tar.gz) Right click it and select 'Extract Here.' Now, in the terminal:

cd ~/Desktop/backports-4.4-rc2-1
make defconfig-iwlwifi
make
sudo make install

Now, let's get the firmware:

sudo apt-get update
sudo apt-get install git
git clone [https://github.com/OpenELEC/iwlwifi-firmware.git](https://github.com/OpenELEC/iwlwifi-firmware.git)
cd linux-firmware/firmware
sudo cp iwlwifi-7260* /lib/firmware

Reboot and check:

dmesg | grep iwl

You should see the 17.xx firmware loaded as well as a better, more stable connection.

After a newer kernel version is installed, after the requested restart, you must recompile:

cd ~/Desktop/backports-4.4-rc2-1
make clean
make defconfig-iwlwifi
make
sudo make install 

Then please copy and paste..
```
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
and..
```
echo "options iwlwifi 11n_disable=8" | sudo tee -a  /etc/modprobe.d/iwlwifi.conf
```
thanks.

---

### Post by Louis11 on 2016-03-13
Oddly enough, I found the post that came from and just finished trying it out. I now see 17.xx firmware loaded:
```

[    1.886777] iwlwifi: unknown parameter 'auto_agg' ignored
[    1.887218] iwlwifi 0000:03:00.0: enabling device (0000 -> 0002)
[    1.899158] iwlwifi 0000:03:00.0: loaded firmware version 17.265642.0 op_mode iwlmvm
```

But still can't seem to connect. The card looks like it's trying to connect, but never actually does...

---

### Post by Louis11 on 2016-03-13
For completeness sake, here is the new output from wireless-info:

```


########## wireless info START ##########

Report from: 12 Mar 2016 23:34 CST -0600

Booted last: 12 Mar 2016 00:00 CST -0600

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 15.10
Release:	15.10
Codename:	wily

##### kernel ############################

Linux 4.2.0-30-generic #36-Ubuntu SMP Fri Feb 26 00:58:07 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I218-V [8086:15a1]
	DeviceName:  Onboard LAN
	Subsystem: ASUSTeK Computer Inc. Device [1043:85c4]

03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev bb)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4070]
	Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 004 Device 002: ID 8087:8001 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8009 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 1532:0502 Razer USA, Ltd 
Bus 001 Device 005: ID 0b38:0010 Gear Head 107-Key Keyboard
Bus 001 Device 004: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 003: ID 8087:07dc Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
mxm_wmi                16384  0
iwlmvm                315392  0
mac80211              634880  1 iwlmvm
iwlwifi               196608  1 iwlmvm
cfg80211              548864  3 iwlwifi,mac80211,iwlmvm
compat                 16384  4 cfg80211,iwlwifi,mac80211,iwlmvm
wmi                    20480  2 mxm_wmi,asus_wmi
video                  40960  1 asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eno1      Link encap:Ethernet  HWaddr <MAC 'eno1' [IF]>  
          inet addr:192.168.2.8  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eno1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2667 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2378 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2317420 (2.3 MB)  TX bytes:355753 (355.7 KB)
          Interrupt:20 Memory:f7200000-f7220000 

wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eno1      no wireless extensions.

lo        no wireless extensions.

wlp3s0    IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 eno1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eno1
192.168.2.0     0.0.0.0         255.255.255.0   U     100    0        0 eno1

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root      1012     1  0 23:28 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (2) I218-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.5-k
GENERAL.FIRMWARE-VERSION:               0.1-4
GENERAL.HWADDR:                         <MAC 'eno1' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/eno1
GENERAL.IP-IFACE:                       eno1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       ea92a100-3c0b-4c2d-aaec-8290e2c1f3ab
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/4
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   ea92a100-3c0b-4c2d-aaec-8290e2c1f3ab | Wired connection 1
IP4.ADDRESS[1]:                         192.168.2.8/24
IP4.GATEWAY:                            192.168.2.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.2.1
DHCP4.OPTION[1]:                        requested_host_name = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        server_name = Computer-2.local
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_time_offset = 1
DHCP4.OPTION[8]:                        expiry = 1457932796
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       next_server = 192.168.2.1
DHCP4.OPTION[11]:                       broadcast_address = 192.168.2.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.2.1
DHCP4.OPTION[15]:                       dhcp_lease_time = 85536
DHCP4.OPTION[16]:                       ip_address = 192.168.2.8
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       domain_name_servers = 192.168.2.1
DHCP4.OPTION[21]:                       requested_netbios_scope = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       network_number = 192.168.2.0
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.2.1
IP6.ADDRESS[1]:                         fe80::<IP6 'eno1' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 7260 (Dual Band Wireless-AC 7260)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.2.0-30-generic
GENERAL.FIRMWARE-VERSION:               17.265642.0
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
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
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   c112d800-ad0f-4f58-8a13-9ea9ea174489 | Ministry of Magic

SSID                   BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
NETGEAR02-arlo_247004  <MAC 'NETGEAR02-arlo_247004' [AN1]>  Infra  2     2417 MHz  54 Mbit/s  22      &#9602;___  WPA2       no        
ATT5w9n2T7             <MAC 'ATT5w9n2T7' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  17      &#9602;___  WPA1 WPA2  no        
Ministry of Magic      <MAC 'Ministry of Magic' [AC3]>  Infra  153   5765 MHz  54 Mbit/s  29      &#9602;___  WPA2       no        
AT&T                   <MAC 'AT<MAC 'AT<MAC address>T' [AN4]>T' [AC2]>  Infra  11    2462 MHz  54 Mbit/s  25      &#9602;___  WPA1 WPA2  no        

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

[[/etc/NetworkManager/system-connections/Ministry of Magic]] (600 root)
[connection] id=Ministry of Magic | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF]> | mac-address-blacklist= | ssid=Ministry of Magic
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/Foobar]] (600 root)
[connection] id=Foobar | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF]> | mac-address-blacklist= | ssid=Foobar
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

country US: DFS-FCC
	(2402 - 2472 @ 40), (N/A, 30), (N/A)
	(5170 - 5250 @ 80), (N/A, 17), (N/A)
	(5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
	(5735 - 5835 @ 80), (N/A, 30), (N/A)
	(57240 - 63720 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

eno1      no frequency information.

lo        no frequency information.

wlp3s0    24 channels in total; available frequencies :
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

eno1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.765 GHz (Channel 153)

wlp3s0    Scan completed :
          Cell 01 - Address: <MAC 'ATT5w9n2T7' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"ATT5w9n2T7"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000016e07d3b183
                    Extra: Last beacon: 17340ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'AT<MAC 'AT<MAC address>T' [AN4]>T' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"AT&T"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000016e079d0ee5
                    Extra: Last beacon: 17316ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Ministry of Magic' [AC3]>
                    Channel:153
                    Frequency:5.765 GHz (Channel 153)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Ministry of Magic"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000005211603a
                    Extra: Last beacon: 3296ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/4.2.0-30-generic/updates/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
version:        backported from Linux (v4.4-rc2-0-g1ec2183) using backports v4.4-rc2-1-0-g005b70f
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     37C3C24B043ECA1CD6BE5EB
depends:        iwlwifi,mac80211,compat,cfg80211
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/4.2.0-30-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (v4.4-rc2-0-g1ec2183) using backports v4.4-rc2-1-0-g005b70f
srcversion:     A4993DB5CEA23914A8B62C4
depends:        cfg80211,compat
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.2.0-30-generic/updates/drivers/net/wireless/iwlwifi/iwlwifi.ko
version:        backported from Linux (v4.4-rc2-0-g1ec2183) using backports v4.4-rc2-1-0-g005b70f
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
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
firmware:       iwlwifi-7265D-13.ucode
firmware:       iwlwifi-7265-13.ucode
firmware:       iwlwifi-3160-13.ucode
firmware:       iwlwifi-7260-13.ucode
firmware:       iwlwifi-8000-13.ucode
srcversion:     C2E4907878C7E74620FA64A
depends:        compat,cfg80211
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
parm:           debug:debug output mask (uint)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/4.2.0-30-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (v4.4-rc2-0-g1ec2183) using backports v4.4-rc2-1-0-g005b70f
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     B589D7668D395EB899EF231
depends:        compat
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2
tfd_q_hang_detect: Y

[mac80211]
beacon_loss_count: 7
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[iwlwifi]
11n_disable: 1
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: N
d0i3_disable: Y
debug: 0
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 1
uapsd_disable: Y

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
options iwlwifi 11n_disable=8

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[    2.304657] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    2.368034] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
[    4.503549] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[    4.503631] iwlwifi 0000:03:00.0: L1 Disabled - LTR Enabled (repeated 4 times)
[    4.868764] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[    4.974895] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready (repeated 2 times)
[    5.228186] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[    8.446870] e1000e: eno1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[    8.446900] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready
[   50.364033] wlp3s0: authenticate with <MAC 'Ministry of Magic' [AC3]>
[   50.369072] wlp3s0: send auth to <MAC 'Ministry of Magic' [AC3]> (try 1/3)
[   50.426739] wlp3s0: send auth to <MAC 'Ministry of Magic' [AC3]> (try 2/3)
[   50.486702] wlp3s0: send auth to <MAC 'Ministry of Magic' [AC3]> (try 3/3)
[   50.537319] wlp3s0: authentication with <MAC 'Ministry of Magic' [AC3]> timed out
[   53.954413] wlp3s0: authenticate with <MAC 'Ministry of Magic' [AC3]>
[   53.956615] wlp3s0: send auth to <MAC 'Ministry of Magic' [AC3]> (try 1/3)
[   54.018413] wlp3s0: send auth to <MAC 'Ministry of Magic' [AC3]> (try 2/3)
[   54.070861] wlp3s0: send auth to <MAC 'Ministry of Magic' [AC3]> (try 3/3)
[   54.121445] wlp3s0: authentication with <MAC 'Ministry of Magic' [AC3]> timed out
[   64.052114] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[  318.368605] wlp3s0: authenticate with <MAC 'Ministry of Magic' [AC3]>
[  318.371044] wlp3s0: send auth to <MAC 'Ministry of Magic' [AC3]> (try 1/3)
[  318.433053] wlp3s0: send auth to <MAC 'Ministry of Magic' [AC3]> (try 2/3)
[  318.488591] wlp3s0: send auth to <MAC 'Ministry of Magic' [AC3]> (try 3/3)
[  318.523513] wlp3s0: authentication with <MAC 'Ministry of Magic' [AC3]> timed out
[  322.880688] wlp3s0: authenticate with <MAC 'Ministry of Magic' [AC3]>
[  322.883542] wlp3s0: send auth to <MAC 'Ministry of Magic' [AC3]> (try 1/3)
[  322.935219] wlp3s0: send auth to <MAC 'Ministry of Magic' [AC3]> (try 2/3)
[  322.993100] wlp3s0: send auth to <MAC 'Ministry of Magic' [AC3]> (try 3/3)
[  323.059538] wlp3s0: authentication with <MAC 'Ministry of Magic' [AC3]> timed out
[  328.269705] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready

########## wireless info END ############

```

---

### Post by Hadaka on 2016-03-13
Hi , the signal strength from your ac is on the low side
how far are you from this router? also the ssid 'Ministry of Magic'
having spaces in it is not advisable. better to be 'Ministry_of_Magic'
You might consider deleting this connection and adding it back in as it
looks like its trying to connect. also please set IPv6 to Ignore in network mgr.
```
Cell 03 - Address: <MAC 'Ministry of Magic' [AC3]>
                    Channel:153
                    Frequency:5.765 GHz (Channel 153)
                    Quality=[COLOR=#ff0000]29/70[/COLOR]  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Ministry of Magic"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
```

---

### Post by Louis11 on 2016-03-13
I'm literally in the same room as the router. If I took the card out, I could throw it at the router without much hassle. I'm currently using my laptop to get internet on this machine; I've shared my laptops wifi over ethernet. So my laptop can connect to the same network, from an equal distance...

Is there anyway I can try and improve the strength of the card? In network manager it simply says "Out of Range".

Trying to update the name of the router. I'll report back and see if it did anything. I disabled IPv6 last night with no obvious improvement.

**Edit** Just tried updating SSID - no change.

Also tried fiddling with various settings on my router (and tried moving my router closer to the machine) - no change. I noticed that for every network I see when I do a `iwlist  wlp3s0 scan` the signal is about 20-30. Doesn't seem to matter the distance to the router.

---

### Post by Hadaka on 2016-03-13
Hi, If this Intel 7260 card is a recent install, i would suggest
checking that the antenna wire is a solid connection and on the correct
connection post. The card has 2 places to connect..A..and B
A- is the main connection point and  B- is the auxillary connection point.
visual
[http://www.intel.com/content/www/us/en/wireless-products/dual-band-wireless-ac-7260-bluetooth.html](http://www.intel.com/content/www/us/en/wireless-products/dual-band-wireless-ac-7260-bluetooth.html)
Let us know what you find
thanks.

---

### Post by Hadaka on 2016-03-13
Here is a pic of an actual AC7260 card installed, notice this machine
has both wires connected.
[ATTACH=CONFIG]267795[/ATTACH]

---

### Post by goofprog on 2016-03-13
..I have a Dell E4300 laptop with intel 5300 wireless.  the iwlwifi drivers did not work so I used some broadcom driver and it got it working.  It was a special wireless driver that had to use this "cutter" thing to get it working.

---

### Post by Louis11 on 2016-03-13
Yup this was it. Antennas weren't properly connected! Thanks for the help!

---

### Post by Hadaka on 2016-03-13
You are welcome, glad it's working now.
Please take the time to mark your thread solved
by going to your first post then clicking Thread TOOLS
then mark as solved.
thanks.

---

