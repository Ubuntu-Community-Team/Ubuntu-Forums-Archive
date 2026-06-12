---
title: "Can not connect to WiFi anymore: Authentication timed out, Intel 5100, Vostro 1220"
date: 2017-12-29
forum: Networking &amp; Wireless
---

### Post by superuser on 2017-12-29
Hi folks!

I had this laptop running Ubuntu beautifully for almost the entire past 10 years, when my wireless connection started to hick-up in September 2017 or so. 
What's weird is that occassionally, I can connect to the wifi without changing anything, and once I am logged-in, it seems to work for a while, even after a reboot or hibernate. I got about 15 devices using my wifi without any issues, including another Ubuntu 17.10 laptop. The issue existed on a 16.10.3 installation, a fresh re-install of that, and now 17.10. At the moment, I can't connect to my Wifi at all, but I can always scan for it (and find it). Dmesg outputs that the connection has timed out.

```

########## wireless info START ##########

Report from: 30 Dec 2017 00:54 CET +0100

Booted last: 30 Dec 2017 00:00 CET +0100

Script from: 05 Dec 2017 03:13 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 17.10
Release:	17.10
Codename:	artful

##### kernel ############################

Linux 4.13.0-16-generic #19-Ubuntu SMP Wed Oct 11 18:35:14 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

ubuntu

##### lspci #############################

09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
	Subsystem: Dell RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1028:02d8]
	Kernel driver in use: r8169

0c:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
	Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1321]
	Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 064e:a128 Suyin Corp. 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

dell_laptop            20480  0
dell_wmi               16384  0
dell_smbios            16384  2 dell_wmi,dell_laptop
sparse_keymap          16384  1 dell_wmi
iwldvm                229376  0
mac80211              778240  1 iwldvm
iwlwifi               249856  1 iwldvm
wmi_bmof               16384  0
cfg80211              610304  3 iwlwifi,mac80211,iwldvm
wmi                    24576  2 dell_wmi,wmi_bmof
video                  40960  3 dell_wmi,dell_laptop,i915

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp9s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether <MAC 'enp9s0' [IF1]> brd <MAC address>
    inet 192.168.178.33/24 brd 192.168.178.255 scope global dynamic enp9s0
       valid_lft 863938sec preferred_lft 863938sec
    inet6 2003:d2:53df:d300:31d4:a266:ffb0:53e7/64 scope global temporary dynamic 
       valid_lft 7140sec preferred_lft 1740sec
    inet6 2003:d2:53df:d300:1185:1ed9:8884:6e04/64 scope global mngtmpaddr noprefixroute dynamic 
       valid_lft 7140sec preferred_lft 1740sec
    inet6 fe80::582b:22ac:5174:7e84/64 scope link 
       valid_lft forever preferred_lft forever
3: wlp12s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether <MAC 'wlp12s0' [IF2]> brd <MAC address>

##### iwconfig ##########################

lo        no wireless extensions.

enp9s0    no wireless extensions.

wlp12s0   IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

default via 192.168.178.1 dev enp9s0 proto static metric 100 
169.254.0.0/16 dev enp9s0 scope link metric 1000 
192.168.178.0/24 dev enp9s0 proto kernel scope link src 192.168.178.33 metric 100 

##### resolv.conf #######################

nameserver 127.0.0.53

search fritz.box

##### network managers ##################

Installed:

	NetworkManager

Running:

root       613     1  0 00:49 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp9s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp9s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:09:00.0/net/enp9s0
GENERAL.IP-IFACE:                       enp9s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Kabelgebundene Verbindung 1
GENERAL.CON-UUID:                       a35fc3ac-20ed-3c30-903b-e526b2d4815c
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/5
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   a35fc3ac-20ed-3c30-903b-e526b2d4815c | Kabelgebundene Verbindung 1
IP4.ADDRESS[1]:                         192.168.178.33/24
IP4.GATEWAY:                            192.168.178.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.178.1
IP4.DOMAIN[1]:                          fritz.box
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.178.1
DHCP4.OPTION[5]:                        ip_address = 192.168.178.33
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.178.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.178.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 756000
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.178.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 432000
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = fritz.box
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1515455595
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.178.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       next_server = 192.168.178.1
DHCP4.OPTION[28]:                       ntp_servers = 192.168.178.1
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 864000
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
IP6.ADDRESS[1]:                         2003:d2:53df:d300:31d4:a266:ffb0:53e7/64
IP6.ADDRESS[2]:                         2003:d2:53df:d300:1185:1ed9:8884:6e04/64
IP6.ADDRESS[3]:                         fe80::582b:22ac:5174:7e84/64
IP6.GATEWAY:                            fe80::e228:6dff:fe26:736c
IP6.ROUTE[1]:                           dst = 2003:d2:53df:d300::/56, nh = fe80::e228:6dff:fe26:736c, mt = 100
IP6.ROUTE[2]:                           dst = 2003:d2:53df:d300::/64, nh = ::, mt = 100
IP6.DNS[1]:                             fd00::e228:6dff:fe26:736c
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = fd00::e228:6dff:fe26:736c
DHCP6.OPTION[3]:                        dhcp6_server_id = 0:3:0:1:<MAC address>
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        dhcp6_unknown_86 = 20:3:0:d2:53:df:d3:0:e2:28:6d:ff:fe:26:73:6c
DHCP6.OPTION[7]:                        dhcp6_client_id = 0:4:c4:27:c6:97:2c:19:e6:d1:be:63:43:32:4a:bd:1:d1

GENERAL.DEVICE:                         wlp12s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        WiFi Link 5100 (AGN)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.13.0-16-generic
GENERAL.FIRMWARE-VERSION:               8.83.5.1 build 33692
GENERAL.HWADDR:                         <MAC 'wlp12s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/wlp12s0
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
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   64ab2959-d630-4aaa-b3ed-77164d2683a7 | FRITZ!Box 7490

SSID                 BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
FRITZ!Box 7490       <MAC 'FRITZ!Box 7490' [AC1]>  Infra  52    5260 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no        
Vodafone Homespot    <MAC 'Vodafone Homespot' [AN2]>  Infra  1     2412 MHz  54 Mbit/s  49      &#9602;&#9604;__  --         no        
FRITZ!Box 7490       <MAC 'FRITZ!Box 7490' [AN3]>  Infra  3     2422 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA1 WPA2  no        
KabelBox-BA34        <MAC 'KabelBox-BA34' [AN4]>  Infra  6     2437 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA2       no        
Vodafone Hotspot     <MAC 'Vodafone Hotspot' [AC4]>  Infra  6     2437 MHz  54 Mbit/s  39      &#9602;&#9604;__  --         no        
Vodafone Homespot    <MAC 'Vodafone Homespot' [AN6]>  Infra  6     2437 MHz  54 Mbit/s  39      &#9602;&#9604;__  --         no        
Vodafone Hotspot     <MAC 'Vodafone Hotspot' [AN7]>  Infra  1     2412 MHz  54 Mbit/s  35      &#9602;&#9604;__  --         no        
devolo-bcf2afb5ae2a  <MAC 'devolo-bcf2afb5ae2a' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  27      &#9602;___  WPA2       no        
Vodafone Hotspot     <MAC 'Vodafone Hotspot' [AN9]>  Infra  1     2412 MHz  54 Mbit/s  25      &#9602;___  --         no        
KabelBox-BA34        <MAC 'KabelBox-BA34' [AN10]>  Infra  36    5180 MHz  54 Mbit/s  25      &#9602;___  WPA2       no        

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

[[/etc/NetworkManager/system-connections/FRITZ!Box 7490]] (600 root)
[connection] id=FRITZ!Box 7490 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp12s0' [IF2]> | mac-address-blacklist= | ssid=FRITZ!Box 7490
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

global
country DE: DFS-ETSI
	(2400 - 2483 @ 40), (N/A, 20), (N/A)
	(5150 - 5250 @ 80), (N/A, 20), (N/A), NO-OUTDOOR, AUTO-BW
	(5250 - 5350 @ 80), (N/A, 20), (0 ms), NO-OUTDOOR, DFS, AUTO-BW
	(5470 - 5725 @ 160), (N/A, 26), (0 ms), DFS
	(5725 - 5875 @ 80), (N/A, 13), (N/A)
	(57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp9s0    no frequency information.

wlp12s0   32 channels in total; available frequencies :
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

enp9s0    Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:5.26 GHz (Channel 52)

wlp12s0   Scan completed :
          Cell 01 - Address: <MAC 'FRITZ!Box 7490' [AC1]>
                    Channel:52
                    Frequency:5.26 GHz (Channel 52)
                    Quality=70/70  Signal level=-27 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 7490"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000cb74603b
                    Extra: Last beacon: 2236ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'devolo-bcf2afb5ae2a' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"devolo-bcf2afb5ae2a"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002b6c3c0e180
                    Extra: Last beacon: 3160ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'KabelBox-BFE0' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"KabelBox-BFE0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000aa01d3980
                    Extra: Last beacon: 3144ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Vodafone Hotspot' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"Vodafone Hotspot"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000290b5b98c04
                    Extra: Last beacon: 3096ms ago

##### module infos ######################

[iwldvm]
filename:       /lib/modules/4.13.0-16-generic/kernel/drivers/net/wireless/intel/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     247533358E1675610AB8991
depends:        mac80211,iwlwifi,cfg80211
intree:         Y
name:           iwldvm
vermagic:       4.13.0-16-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           force_cam:force continuously aware mode (no power saving at all) (bool)

[mac80211]
filename:       /lib/modules/4.13.0-16-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     66E288B8743878C5423A01E
depends:        cfg80211
intree:         Y
name:           mac80211
vermagic:       4.13.0-16-generic SMP mod_unload 
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
filename:       /lib/modules/4.13.0-16-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-8265-33.ucode
firmware:       iwlwifi-8000C-33.ucode
firmware:       iwlwifi-9260-th-b0-jf-b0--33.ucode
firmware:       iwlwifi-9260-th-a0-jf-a0--33.ucode
firmware:       iwlwifi-9000-pu-a0-jf-b0--33.ucode
firmware:       iwlwifi-9000-pu-a0-jf-a0--33.ucode
firmware:       iwlwifi-Qu-a0-jf-b0--33.ucode
firmware:       iwlwifi-Qu-a0-hr-a0--33.ucode
srcversion:     339D7D3BD0DD2A9C7FE616F
depends:        cfg80211
intree:         Y
name:           iwlwifi
vermagic:       4.13.0-16-generic SMP mod_unload 
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
filename:       /lib/modules/4.13.0-16-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A854863B536C70273DE73A5
depends:        
intree:         Y
name:           cfg80211
vermagic:       4.13.0-16-generic SMP mod_unload 
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
blacklist rtl8xxxu

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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    9.685714] iwlwifi 0000:0c:00.0 wlp12s0: renamed from wlan0
[   18.433418] IPv6: ADDRCONF(NETDEV_UP): enp9s0: link is not ready
[   18.553371] r8169 0000:09:00.0 enp9s0: link down
[   18.553490] IPv6: ADDRCONF(NETDEV_UP): enp9s0: link is not ready
[   18.566447] IPv6: ADDRCONF(NETDEV_UP): wlp12s0: link is not ready
[   18.575245] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0 (repeated 2 times)
[   18.733158] IPv6: ADDRCONF(NETDEV_UP): wlp12s0: link is not ready (repeated 2 times)
[   25.486007] wlp12s0: authenticate with <MAC 'FRITZ!Box 7490' [AC1]>
[   25.489414] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AC1]> (try 1/3)
[   25.559556] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AC1]> (try 2/3)
[   25.569117] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AC1]> (try 3/3)
[   25.577687] wlp12s0: authentication with <MAC 'FRITZ!Box 7490' [AC1]> timed out
[   25.764921] wlp12s0: authenticate with <MAC address>
[   25.770200] wlp12s0: send auth to <MAC address> (try 1/3)
[   25.791179] wlp12s0: send auth to <MAC address> (try 2/3)
[   25.823115] wlp12s0: send auth to <MAC address> (try 3/3)
[   25.841920] wlp12s0: authentication with <MAC address> timed out
[   26.017214] wlp12s0: authenticate with <MAC 'FRITZ!Box 7490' [AN3]>
[   26.021599] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AN3]> (try 1/3)
[   26.045989] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AN3]> (try 2/3)
[   26.065558] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AN3]> (try 3/3)
[   26.087415] wlp12s0: authentication with <MAC 'FRITZ!Box 7490' [AN3]> timed out
[   29.378867] wlp12s0: authenticate with <MAC 'FRITZ!Box 7490' [AC1]>
[   29.381682] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AC1]> (try 1/3)
[   29.449960] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AC1]> (try 2/3)
[   29.459041] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AC1]> (try 3/3)
[   29.467917] wlp12s0: authentication with <MAC 'FRITZ!Box 7490' [AC1]> timed out
[   30.573840] wlp12s0: authenticate with <MAC 'FRITZ!Box 7490' [AN3]>
[   30.585116] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AN3]> (try 1/3)
[   30.608749] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AN3]> (try 2/3)
[   30.637124] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AN3]> (try 3/3)
[   30.660178] wlp12s0: authentication with <MAC 'FRITZ!Box 7490' [AN3]> timed out
[   34.704000] wlp12s0: authenticate with <MAC 'FRITZ!Box 7490' [AC1]>
[   34.706819] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AC1]> (try 1/3)
[   34.775552] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AC1]> (try 2/3)
[   34.785654] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AC1]> (try 3/3)
[   34.794167] wlp12s0: authentication with <MAC 'FRITZ!Box 7490' [AC1]> timed out
[   44.867212] wlp12s0: authenticate with <MAC 'FRITZ!Box 7490' [AN3]>
[   44.878145] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AN3]> (try 1/3)
[   44.900232] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AN3]> (try 2/3)
[   44.924345] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AN3]> (try 3/3)
[   44.946182] wlp12s0: authentication with <MAC 'FRITZ!Box 7490' [AN3]> timed out
[   48.002905] IPv6: ADDRCONF(NETDEV_UP): wlp12s0: link is not ready
[   54.150025] wlp12s0: authenticate with <MAC 'FRITZ!Box 7490' [AC1]>
[   54.153360] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AC1]> (try 1/3)
[   54.230909] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AC1]> (try 2/3)
[   54.240915] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AC1]> (try 3/3)
[   54.250246] wlp12s0: authentication with <MAC 'FRITZ!Box 7490' [AC1]> timed out
[   67.369656] wlp12s0: authenticate with <MAC 'FRITZ!Box 7490' [AN3]>
[   67.372656] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AN3]> (try 1/3)
[   67.393744] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AN3]> (try 2/3)
[   67.415064] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AN3]> (try 3/3)
[   67.443238] wlp12s0: authentication with <MAC 'FRITZ!Box 7490' [AN3]> timed out
[   79.029506] IPv6: ADDRCONF(NETDEV_UP): wlp12s0: link is not ready
[   83.649166] wlp12s0: authenticate with <MAC 'FRITZ!Box 7490' [AC1]>
[   83.651788] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AC1]> (try 1/3)
[   83.722346] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AC1]> (try 2/3)
[   83.731133] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AC1]> (try 3/3)
[   83.739889] wlp12s0: authentication with <MAC 'FRITZ!Box 7490' [AC1]> timed out
[   93.809927] wlp12s0: authenticate with <MAC 'FRITZ!Box 7490' [AN3]>
[   93.812584] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AN3]> (try 1/3)
[   93.834581] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AN3]> (try 2/3)
[   93.861262] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AN3]> (try 3/3)
[   93.884370] wlp12s0: authentication with <MAC 'FRITZ!Box 7490' [AN3]> timed out
[  106.013176] IPv6: ADDRCONF(NETDEV_UP): wlp12s0: link is not ready
[  110.170287] wlp12s0: authenticate with <MAC 'FRITZ!Box 7490' [AC1]>
[  110.172809] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AC1]> (try 1/3)
[  110.243595] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AC1]> (try 2/3)
[  110.252124] wlp12s0: send auth to <MAC 'FRITZ!Box 7490' [AC1]> (try 3/3)
[  110.261169] wlp12s0: authentication with <MAC 'FRITZ!Box 7490' [AC1]> timed out
[  120.377196] wlp12s0: authenticate with <MAC address>
[  120.379934] wlp12s0: send auth to <MAC address> (try 1/3)
[  120.403442] wlp12s0: send auth to <MAC address> (try 2/3)
[  120.427852] wlp12s0: send auth to <MAC address> (try 3/3)
[  120.455935] wlp12s0: authentication with <MAC address> timed out
[  132.011217] IPv6: ADDRCONF(NETDEV_UP): wlp12s0: link is not ready
[  243.864368] r8169 0000:09:00.0 enp9s0: link up
[  243.864390] IPv6: ADDRCONF(NETDEV_CHANGE): enp9s0: link becomes ready

########## wireless info END ############

```

I've tried every possible combination of option parameters to iwlwifi, to no avail. I'm starting to believe this might be a hardware issue on this old boy, maybe a broken antenna cable or something. Please tell me it's not :-)

Thanks
therealsuperuser

---

### Post by chili555 on 2017-12-30
> this might be a hardware issue on this old boy, maybe a broken antenna cable or something. Please tell me it's not It's not. Your scan results are showing 100% for your preferred network, so we believe that the antenna wires are just fine.

We do see some alarming things in the scan results, namely:```
SSID                 BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
[COLOR="#FF0000"]FRITZ!Box 7490 [/COLOR]      <MAC 'FRITZ!Box 7490' [AC1]>  Infra  52    5260 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no        
Vodafone Homespot    <MAC 'Vodafone Homespot' [AN2]>  Infra  1     2412 MHz  54 Mbit/s  49      &#9602;&#9604;__  --         no        
[COLOR="#FF0000"]FRITZ!Box 7490 [/COLOR]      <MAC 'FRITZ!Box 7490' [AN3]>  Infra  3     2422 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA1 WPA2  no        
KabelBox-BA34        <MAC 'KabelBox-BA34' [AN4]>  Infra  6     2437 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA2       no        
Vodafone Hotspot     <MAC 'Vodafone Hotspot' [AC4]>  Infra  6     2437 MHz  54 Mbit/s  39      &#9602;&#9604;__  --         no        
```You have a double-whammy going on here. First, I assume these are the 2.4 gHz and 5 gHz segments of your router. Because they are named the same, your wireless will always be looking for a better connection (sort of like my old girlfriend!) and drop one and try to connect the other.

Second, I have worked on several cases where a space in the name of the SSID made connections difficult and in some cases, impossible.

I suggest that you rename the SSIDs to something like FRITZ!Box7490-2.4 and FRITZ!Box7490-5. Then ask your wireless to connect to one and stick to it. I'd try both segments to see which performs better. I have the best luck with my Intel with 5 gHz.

In both segments, WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. 

You may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

> I've tried every possible combination of option parameters to iwlwifi, to no avail.Including, it appears, removing the needed conf file altogether! From the terminal, please do:```
sudo nano /etc/modprobe.d/iwlwifi.conf
```Add this exact text to the new empty file:```
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

```Proofread carefully, twice, and save (Ctrl+o followed by Enter) and close the text editor (Ctrl+x).

Please post back and let us hear your report.

PS - Did I say that your driver, your hardware and old Chili hate hate hate TKIP??

---

### Post by superuser on 2017-12-30
Dear Chili,

Thank you so much for your reply.

Unfortunately, I do not have good news. I tried everything you suggested and did not have luck. Thanks to you I noticed that my WIFI configuration was not optimal: My additional AP that was not actually configured in exactly the same manner as the main AP (TKIP + different band). I fixed that, thanks.

However, that did not affect any of the 15 working connected devices, nor my Vostro 1220, which used to be able to connect just fine. As I wrote in the above post, I had the suspicion already that its hardware might be broken -- and I just confirmed it. I got another router with an open WIFI -- I could see it, but I could not even connect to it with my Vostro (other machines, no problem)! So that's very weird. Then, I tried booting from a fresh Ubuntu 17.10 Usb pen drive -- no luck. Next, I installed Windows 7 and tried to connect to the open WIFI or my original WIFI -- guess what, it did not work, either! 

My best guess is that the cable connecting the antenna to the chip is broken where it goes through the display hinge. Occasionally in the past, it connected again (maybe display in the correct angle so the cables connected randomly), and then I could also connect to the WIFI. But that did not work the 300 or so times I tried in the past two days anymore :(

Thanks again!

---

### Post by praseodym on 2017-12-30
Please run

```
echo -e "\n[device]\nwifi.scan-rand-mac-address=no" | sudo tee -a /etc/NetworkManager/NetworkManager.conf
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
and reboot. There is a bug in the network manager in 16.04 (sometimes), 17.04 (confirmed) and 17.10 (still like 17.04)

---

### Post by fazillatheef on 2018-02-02
I also have the same issue with wifi. It used to work for earlier Ubuntu versions.I got this issue with one of the update in Antergos(KDE). It happed after an update in the last three months.

 Thats when I thought to install Ubuntu. And I am having the same issue.

I have raised a question here -  [https://askubuntu.com/questions/1001889/not-able-to-connect-wifi-in-fresh-17-10-install-on-dell-1555](https://askubuntu.com/questions/1001889/not-able-to-connect-wifi-in-fresh-17-10-install-on-dell-1555)
Please let  me know if you get this resolved.

---

