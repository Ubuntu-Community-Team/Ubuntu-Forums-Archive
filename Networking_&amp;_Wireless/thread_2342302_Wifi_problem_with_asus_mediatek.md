---
title: "Wifi problem with asus mediatek"
date: 2016-11-05
forum: Networking &amp; Wireless
---

### Post by pierrehitsch on 2016-11-05
Hello everybody,
I'm french and I don't speek very well english so sorry in advance for that.
I'm writing this message because nobody could help me to find the solution of my problem on the french forum.
So I have a ASUS with the network card Mediatek MT7630E 802.11 bgn and I installed Ubuntu 16.04 LTS a few days ago.
My problem is that my wifi connection is working during 5 minutes and then the wifi connection suddenly diappear.
I tried to find a solution on many forums but nothing worked a long time.
I think the driver is correctly installed but It's not working :/
i hope someone will help me 
thank you!!!

---

### Post by ajgreeny on 2016-11-05
See Wireless-Info in my signature below and run the wifi-info-script linked there.
Post back here the output you get as it will help the wifi experts here to help you more than I can.

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by pierrehitsch on 2016-11-05
thank you ajgreeny  for your reply,
This is the result of the wifi-info-script :
```

########## wireless info START ##########

Report from: 05 Nov 2016 21:42 CET +0100

Booted last: 05 Nov 2016 00:00 CET +0100

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-45-generic #66-Ubuntu SMP Wed Oct 19 14:12:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, radeon.audio=1, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: MEDIATEK Corp. MT7630e 802.11bgn Wireless Network Adapter [14c3:7630]
    Subsystem: Foxconn International, Inc. MT7630e 802.11bgn Wireless Network Adapter [105b:e074]
    Kernel driver in use: mt7630e

03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b40a Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0e8d:763f MediaTek Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 1c4f:0034 SiGma Micro 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

mac80211              737280  1 mt7630e
cfg80211              565248  2 mac80211,mt7630e
wmi                    20480  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0f2  Link encap:Ethernet  HWaddr <MAC 'enp3s0f2' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlp2s0f0  Link encap:Ethernet  HWaddr <MAC 'wlp2s0f0' [IF2]>  
          inet addr:10.128.159.237  Bcast:10.128.255.255  Mask:255.255.0.0
          inet6 addr: fe80::61:1c5f:7ea2:3dea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7220 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4581 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2127404 (2.1 MB)  TX bytes:980135 (980.1 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp3s0f2  no wireless extensions.

wlp2s0f0  IEEE 802.11bgn  ESSID:"SmartCampus"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'SmartCampus' [AC1]>   
          Bit Rate=6.5 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:24  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.128.0.1      0.0.0.0         UG    600    0        0 wlp2s0f0
10.128.0.0      0.0.0.0         255.255.0.0     U     600    0        0 wlp2s0f0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0f0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       737     1  0 21:36 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp2s0f0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         MEDIATEK Corp.
GENERAL.PRODUCT:                        MT7630e 802.11bgn Wireless Network Adapter
GENERAL.DRIVER:                         mt7630e
GENERAL.DRIVER-VERSION:                 4.4.0-45-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp2s0f0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlp2s0f0
GENERAL.IP-IFACE:                       wlp2s0f0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     SmartCampus
GENERAL.CON-UUID:                       0965286b-5360-4bdb-9806-5470697ff7b1
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     6 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   0965286b-5360-4bdb-9806-5470697ff7b1 | SmartCampus
IP4.ADDRESS[1]:                         10.128.159.237/16
IP4.GATEWAY:                            10.128.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             10.128.0.1
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        host_name = antoine-X550CA
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 10.128.0.1
DHCP4.OPTION[11]:                       expiry = 1478983003
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 10.128.0.1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 10.128.159.237
DHCP4.OPTION[17]:                       broadcast_address = 10.128.255.255
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 302400
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       requested_routers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 10.128.0.1
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       dhcp_lease_time = 604800
DHCP4.OPTION[25]:                       dhcp_rebinding_time = 529200
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.0.0
DHCP4.OPTION[28]:                       network_number = 10.128.0.0
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 10.128.0.1
IP6.ADDRESS[1]:                         fe80::61:1c5f:7ea2:3dea/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp3s0f2
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0f2' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.2/net/enp3s0f2
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

SSID             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
SmartCampus      <MAC 'SmartCampus' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  --           yes     * 
SmartCampus      <MAC 'SmartCampus' [AC7]>  Infra  1     2412 MHz  54 Mbit/s  61      &#9602;&#9604;&#9606;_  --           no        
freebox_Clement  <MAC 'freebox_Clement' [AC6]>  Infra  1     2412 MHz  54 Mbit/s  61      &#9602;&#9604;&#9606;_  WPA1         no        
FreeWifi_secure  <MAC 'FreeWifi_secure' [AC4]>  Infra  1     2412 MHz  54 Mbit/s  61      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
FreeWifi         <MAC 'FreeWifi' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  --           no        
SmartCampus      <MAC 'SmartCampus' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  --           no        
SmartCampus      <MAC 'SmartCampus' [AN7]>  Infra  11    2462 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  --           no        
SmartCampus      <MAC 'SmartCampus' [AC8]>  Infra  13    2472 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  --           no        
SmartCampus      <MAC 'SmartCampus' [AN9]>  Infra  6     2437 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  --           no        
SmartCampus      <MAC 'SmartCampus' [AN10]>  Infra  9     2452 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  --           no        

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

[[/etc/NetworkManager/system-connections/SmartCampus]] (600 root)
[connection] id=SmartCampus | type=wifi | permissions=user:antoine:;
[wifi] mac-address=<MAC 'wlp2s0f0' [IF2]> | mac-address-blacklist= | ssid=SmartCampus
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-4dc4]] (600 root)
[connection] id=Livebox-4dc4 | type=wifi | permissions=user:antoine:;
[wifi] mac-address=<MAC 'wlp2s0f0' [IF2]> | mac-address-blacklist= | ssid=Livebox-4dc4
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Paris (based on set time zone)

country GB: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp3s0f2  no frequency information.

wlp2s0f0  13 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp3s0f2  Interface doesn't support scanning.

Channel occupancy:

      7   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.472 GHz (Channel 13)

wlp2s0f0  Scan completed :
          Cell 01 - Address: <MAC 'SmartCampus' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=61 dBm  
                    Encryption key:off
                    ESSID:"SmartCampus"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000016415ab
                    Extra: Last beacon: 64ms ago
          Cell 02 - Address: <MAC 'SmartCampus' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=60 dBm  
                    Encryption key:off
                    ESSID:"SmartCampus"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001431d3188
                    Extra: Last beacon: 204ms ago
          Cell 03 - Address: <MAC 'FreeWifi' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=61 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001bfd17d8581
                    Extra: Last beacon: 180ms ago
          Cell 04 - Address: <MAC 'FreeWifi_secure' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=60 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001bfd17d815f
                    Extra: Last beacon: 148ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 05 - Address: <MAC 'AH-d8eac0_ac' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=62 dBm  
                    Encryption key:on
                    ESSID:"AH-d8eac0_ac"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000042de8c522f8
                    Extra: Last beacon: 64ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'freebox_Clement' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=60 dBm  
                    Encryption key:on
                    ESSID:"freebox_Clement"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001bfd17d815f
                    Extra: Last beacon: 216ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'SmartCampus' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=60 dBm  
                    Encryption key:off
                    ESSID:"SmartCampus"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000123509180
                    Extra: Last beacon: 236ms ago
          Cell 08 - Address: <MAC 'SmartCampus' [AC8]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=70/70  Signal level=60 dBm  
                    Encryption key:off
                    ESSID:"SmartCampus"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000e94df9e6
                    Extra: Last beacon: 64ms ago

##### module infos ######################

[mac80211]
filename:       /lib/modules/4.4.0-45-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F1176862D12ECD05A1066CF
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-45-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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
blacklist asus_nb_wmi

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

[/etc/modprobe.d/iwlmvm.conf]
options iwlmvm power_scheme=1

[/etc/modprobe.d/iwlwifi.conf]
options iwlwifi bt_coex_active=N swcrypto=1 11n_disable=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be fwlps=N ips=N

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[  166.669123] wlp2s0f0: send auth to <MAC 'SmartCampus' [AC7]> (try 2/3)
[  166.773130] wlp2s0f0: send auth to <MAC 'SmartCampus' [AC7]> (try 3/3)
[  166.877150] wlp2s0f0: authentication with <MAC 'SmartCampus' [AC7]> timed out
[  167.435421] wlp2s0f0: authenticate with <MAC 'SmartCampus' [AN10]>
[  167.449194] wlp2s0f0: send auth to <MAC 'SmartCampus' [AN10]> (try 1/3)
[  167.450581] wlp2s0f0: authenticated
[  167.453196] wlp2s0f0: associate with <MAC 'SmartCampus' [AN10]> (try 1/3)
[  167.456491] wlp2s0f0: RX AssocResp from <MAC 'SmartCampus' [AN10]> (capab=0x21 status=0 aid=5)
[  167.456508] ===>rt2800_sta_add:MT7630
[  167.456532] ===>rt2800_sta_add:MT7630   wcid=33
[  167.467098] wlp2s0f0: associated
[  249.228145] ===>rt2800_sta_remove:MT7630
[  249.233137] ===>rt2800_sta_remove:MT7630   0x80100 = 0x0 (repeated 2 times)
[  249.240082] wlp2s0f0: authenticate with <MAC 'SmartCampus' [AC1]>
[  249.248095] wlp2s0f0: send auth to <MAC 'SmartCampus' [AC1]> (try 1/3)
[  249.249264] wlp2s0f0: authenticated
[  249.259980] wlp2s0f0: associate with <MAC 'SmartCampus' [AC1]> (try 1/3)
[  249.261881] wlp2s0f0: RX AssocResp from <MAC 'SmartCampus' [AC1]> (capab=0x421 status=0 aid=3)
[  249.261895] ===>rt2800_sta_add:MT7630
[  249.261917] ===>rt2800_sta_add:MT7630   wcid=33
[  249.273376] wlp2s0f0: associated

########## wireless info END ############

```

I hope that someone will be able to solve my problem.
Thanks for all!!!

---

### Post by pierrehitsch on 2016-11-06
i deactivated secure boot in my bios and edited /etc/network/interfaces to remove all the lines except 
```

auto lo
iface lo inet loopback

```
It worked during 10 minutes and then wifi connection diappeared
any ideas?

---

### Post by jeremy31 on 2016-11-06
Lets see if it isn't power management causing the problem ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot

---

### Post by pierrehitsch on 2016-11-06
Than you for your reply :)
Unfortunately, it didn't work for me. 
I hope someone will find a solution for me...

---

### Post by pierrehitsch on 2016-11-06
I think that the problem comes from my laptop. my brother uses ubuntu too with the same wifi-connection but it worked on his laptop !
The driver is correctly installed. 
Is someone have any track to find an issue?

---

### Post by jeremy31 on 2016-11-06
The next time wifi disappears open terminal ```
./wireless-info
```
Post the results from the new wireless-info.txt

---

### Post by pierrehitsch on 2016-11-07
Thank you jeremy31 for your reply. Sorry I didn't have the time to come on the forum until now.
I uses w10 to work (just because my wifi connection on Ubuntu isn't working). 
Tomorrow, I will come back on Ubuntu to post the new results of wireless-info.
I hope it will make things evolve!!!

---

### Post by pierrehitsch on 2016-11-08
Here is the result of wireless-info when my pc doesn't have wifi :
```


########## wireless info START ##########

Report from: 08 Nov 2016 19:50 CET +0100

Booted last: 08 Nov 2016 00:00 CET +0100

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-45-generic #66-Ubuntu SMP Wed Oct 19 14:12:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, radeon.audio=1

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: MEDIATEK Corp. MT7630e 802.11bgn Wireless Network Adapter [14c3:7630]
    Subsystem: Foxconn International, Inc. MT7630e 802.11bgn Wireless Network Adapter [105b:e074]
    Kernel driver in use: mt7630e

03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b40a Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0e8d:763f MediaTek Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID abcd:1234 Unknown 
Bus 003 Device 002: ID 1c4f:0034 SiGma Micro 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

mac80211              737280  1 mt7630e
cfg80211              565248  2 mac80211,mt7630e
wmi                    20480  0

##### interfaces ########################

auto lo
iface lo inet loopback
auto wlp2s0f0
iface wlp2s0f0 inet dhcp

##### ifconfig ##########################

enp3s0f2  Link encap:Ethernet  HWaddr <MAC 'enp3s0f2' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlp2s0f0  Link encap:Ethernet  HWaddr <MAC 'wlp2s0f0' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

enp3s0f2  no wireless extensions.

wlp2s0f0  IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root       768     1  0 19:48 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp3s0f2
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0f2' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.2/net/enp3s0f2
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

GENERAL.DEVICE:                         wlp2s0f0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         MEDIATEK Corp.
GENERAL.PRODUCT:                        MT7630e 802.11bgn Wireless Network Adapter
GENERAL.DRIVER:                         mt7630e
GENERAL.DRIVER-VERSION:                 4.4.0-45-generic
GENERAL.FIRMWARE-VERSION:               112.3
GENERAL.HWADDR:                         <MAC 'wlp2s0f0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /virtual/device/placeholder/2
GENERAL.IP-IFACE:                       wlp2s0f0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     no
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
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
IP4.GATEWAY:                            
IP6.GATEWAY:                            

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

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

[[/etc/NetworkManager/system-connections/SmartCampus]] (600 root)
[connection] id=SmartCampus | type=wifi | permissions=user:antoine:;
[wifi] mac-address=<MAC 'wlp2s0f0' [IF2]> | mac-address-blacklist= | ssid=SmartCampus
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-4dc4]] (600 root)
[connection] id=Livebox-4dc4 | type=wifi | permissions=user:antoine:;
[wifi] mac-address=<MAC 'wlp2s0f0' [IF2]> | mac-address-blacklist= | ssid=Livebox-4dc4
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Paris (based on set time zone)

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

enp3s0f2  no frequency information.

wlp2s0f0  14 channels in total; available frequencies :
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

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp3s0f2  Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.432 GHz (Channel 5)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:2.472 GHz (Channel 13)

wlp2s0f0  Scan completed :
          Cell 01 - Address: <MAC 'SmartCampus' [AC1]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=70/70  Signal level=56 dBm  
                    Encryption key:off
                    ESSID:"SmartCampus"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000025feef041
                    Extra: Last beacon: 88ms ago
          Cell 02 - Address: <MAC 'SmartCampus' [AC2]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=70/70  Signal level=50 dBm  
                    Encryption key:off
                    ESSID:"SmartCampus"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000004ef01436
                    Extra: Last beacon: 88ms ago
          Cell 03 - Address: <MAC 'SmartCampus' [AC3]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=70/70  Signal level=50 dBm  
                    Encryption key:off
                    ESSID:"SmartCampus"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004444c2180
                    Extra: Last beacon: 308ms ago

##### module infos ######################

[mac80211]
filename:       /lib/modules/4.4.0-45-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F1176862D12ECD05A1066CF
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-45-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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
blacklist asus_nb_wmi

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

[/etc/modprobe.d/iwlmvm.conf]
options iwlmvm power_scheme=1

[/etc/modprobe.d/iwlwifi.conf]
options iwlwifi bt_coex_active=N swcrypto=1 11n_disable=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be fwlps=N ips=N

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   13.960882] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 7630, rev 0002 detected
[   13.962882] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 7630 detected
[   15.306788] mt7630e 0000:02:00.0 wlp2s0f0: renamed from wlan0
[   40.331743] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'MT7650E234.bin'
[   41.035066] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 112.3
[   41.117678] IPv6: ADDRCONF(NETDEV_UP): wlp2s0f0: link is not ready
[   41.608627] IPv6: ADDRCONF(NETDEV_UP): enp3s0f2: link is not ready
[   41.768623] r8169 0000:03:00.2 enp3s0f2: link down
[   41.768682] IPv6: ADDRCONF(NETDEV_UP): enp3s0f2: link is not ready

########## wireless info END ############

```

Thank U ;)

---

### Post by jeremy31 on 2016-11-08
Since you added
```
auto wlp2s0f0
iface wlp2s0f0 inet dhcp
```

To the interface file Network Manager is going to ignore the wlp2s0f0 interface, remove the lines from the file and network manager should work with it

We should set the country code as that could help 
```

sudo iw reg set FR
sudo sed -i 's/^REG.*=$/&FR/' /etc/default/crda

```

Please post results for ```
modinfo mt7630e; grep [[:alnum:]] /sys/module/mt7630e/parameters/*
```

Reboot and see if Network Manager can get you online

---

### Post by pierrehitsch on 2016-11-09
Thank you ;)
I rectified my mistake.
I have a lot of things to do so I hope I will have the time to post the result today of the command but I'm not sure.
My wifi connexion is lagging particulary with "wifirst network" of "Smartcampus". Maybe it can help.
On the french forum, someone said that the problem maybe comes from network manager. He said that I can install wicd to replace Network-manager.
I did it but the wifi is always unstable.
Thank you for your Help

---

### Post by pierrehitsch on 2016-11-09
here is the result :
```

                        filename:       /lib/modules/4.4.0-45-generic/updates/dkms/mt7630e.ko
 license:        GPL
 description:    rt2x00 library
 version:        2.3.8
 author:         http://rt2x00.serialmonkey.com
 license:        GPL
 description:    rt2x00 7630 library
 version:        2.3.8
 author:         http://rt2x00.serialmonkey.com
 license:        GPL
 description:    rt2x00 mmio library
 version:        2.3.8
 author:         http://rt2x00.serialmonkey.com
 license:        GPL
 description:    rt2x00 pci library
 version:        2.3.8
 author:         http://rt2x00.serialmonkey.com
 license:        GPL
 description:    Ralink RT2800 library
 version:        2.3.8
 author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
 license:        GPL
 firmware:       MT7650E234.bin
 description:    Mediatek MT7630 PCI Wireless LAN driver.
 version:        2.3.8
 author:         http://rt2x00.serialmonkey.com
 srcversion:     B0DDDBED7740C133853FE95
 alias:          pci:v000014C3d00007650sv*sd*bc*sc*i*
 alias:          pci:v000014C3d00007630sv*sd*bc*sc*i*
 depends:        mac80211,cfg80211,eeprom_93cx6,crc-ccitt
 vermagic:       4.4.0-45-generic SMP mod_unload modversions  
 parm:           nohwcrypt:Disable hardware encryption. (bool)
 grep: Échec du pairage de [ ou de [^

```
Thanks a lot!!!!

---

### Post by jeremy31 on 2016-11-09
I would try the parameter option the module provides to disable hardware encryption
```
echo "options mt7630e nohwcrypt=Y" | sudo tee /etc/modprobe.d/mt7630e.conf
```

Reboot

---

### Post by pierrehitsch on 2016-11-10
Than you for your help, but my problem...is solved !!!!
Yesterday I installed wicd instead of Network Manager.
Just out of curiosity, I changed the channel. I reboot. And it worked!!!!
Thank you jeremy31 for all and I also thank all the community of ubuntuforums.org for his help.
 I hope this post will help people who have the same problem :-)

---

