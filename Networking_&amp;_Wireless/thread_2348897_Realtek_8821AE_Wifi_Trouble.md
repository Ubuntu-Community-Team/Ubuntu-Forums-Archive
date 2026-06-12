---
title: "Realtek 8821AE Wifi Trouble"
date: 2017-01-08
forum: Networking &amp; Wireless
---

### Post by bzpnut on 2017-01-08
Hi, I recently purchased an Asus X555DA and ever since I installed Ubuntu on it the wifi has been cutting out randomly. It works fine on all my other devices and I tried installing Linux Mint and Antergos just in case it was an Ubuntu specific issue, but no luck. I've updated all my drivers, os, etc yet nothing seems to work.

```
--2017-01-08 18:59:31--  [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info)
Resolving [github.com]("http://github.com") ([github.com]("http://github.com"))... 192.30.253.113, 192.30.253.112
Connecting to [github.com]("http://github.com") ([github.com]("http://github.com"))|192.30.253.113|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info) [following]
--2017-01-08 18:59:32--  [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info)
Resolving [raw.githubusercontent.com]("http://raw.githubusercontent.com") ([raw.githubusercontent.com]("http://raw.githubusercontent.com"))... 151.101.44.133
Connecting to [raw.githubusercontent.com]("http://raw.githubusercontent.com") ([raw.githubusercontent.com]("http://raw.githubusercontent.com"))|151.101.44.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16156 (16K) [text/plain]
Saving to: ‘wireless-info’

wireless-info       100%[===================>]  15.78K  --.-KB/s    in 0.06s

```
Any help you can give would be appreciated.

---

### Post by chili555 on 2017-01-09
> Saving to: ‘wireless-info’That's the data we need to see, please. Find the text file in your home directory and post it here. Thanks.

---

### Post by bzpnut on 2017-01-09
```

########## wireless info START ##########

Report from: 08 Jan 2017 18:59 CST -0600

Booted last: 08 Jan 2017 00:00 CST -0600

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-57-generic #78-Ubuntu SMP Fri Dec 9 23:50:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################


01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: XAVi Technologies Corp. RTL8821AE 802.11ac PCIe Wireless Network Adapter [1b9a:2482]
    Kernel driver in use: rtl8821ae

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 004: ID 0bda:57b5 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID b49a:04f2  
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################


##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

asus_nb_wmi            24576  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
rtl8821ae             225280  0
btcoexist              53248  1 rtl8821ae
rtl_pci                28672  1 rtl8821ae
rtlwifi                77824  2 rtl_pci,rtl8821ae
mac80211              737280  3 rtl_pci,rtlwifi,rtl8821ae
cfg80211              565248  2 mac80211,rtlwifi
wmi                    20480  1 asus_wmi
video                  40960  1 asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr 38:d5:47:97:e7:ac  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::c992:6e4c:2d81:b5b2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12220 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3520 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6949244 (6.9 MB)  TX bytes:412969 (412.9 KB)

wlp1s0    Link encap:Ethernet  HWaddr b0:c0:90:be:40:e3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1686 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1351 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1378489 (1.3 MB)  TX bytes:171250 (171.2 KB)

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

wlp1s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=30 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp2s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       971     1  0 18:25 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         38:D5:47:97:E7:AC
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.3/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       42195781-0dd8-3789-bd15-19c4abf9a6e4
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   42195781-0dd8-3789-bd15-19c4abf9a6e4 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.10/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             97.64.148.90
IP4.DNS[2]:                             97.64.209.37
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 97.64.148.90 97.64.209.37
DHCP4.OPTION[5]:                        ip_address = 192.168.0.10
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[8]:                        default_ip_ttl = 64
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       time_offset = 0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       requested_broadcast_address = 1
DHCP4.OPTION[17]:                       routers = 192.168.0.1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[19]:                       requested_domain_name = 1
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1483925916
DHCP4.OPTION[22]:                       requested_wpad = 1
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 192.168.0.1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 3600
IP6.ADDRESS[1]:                         fe80::c992:6e4c:2d81:b5b2/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8821AE 802.11ac PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8821ae
GENERAL.DRIVER-VERSION:                 4.4.0-57-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         B0:C0:90:BE:40:E3
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.2/0000:01:00.0/net/wlp1s0
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

```

---

### Post by chili555 on 2017-01-09
May we also see:```
sudo iwlist scan
dmesg | grep rtl
```

---

### Post by bzpnut on 2017-01-09
```
enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlp1s0    Scan completed :
          Cell 01 - Address: 00:25:9C:69:54:AF
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"GATOR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000010f6b847ac6
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 00054741544F52
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: DD6F0050F204104A00011010440001021041000100103B000103104700107C8FCF6D2973FDABDD87F6BF2A3A5A68102100074C696E6B737973102300075752543136304E102400063132333435361042000234321054000800060050F2040001101100075752543136304E100800020084
                    IE: Unknown: DD090010180202F4050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406080400000000000000000000000000000000000000
          Cell 02 - Address: FA:8F:CA:51:61:B7
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-22 dBm  
                    Encryption key:off
                    ESSID:"Grayson's Chromecast"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c1b945476
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 001447726179736F6E2773204368726F6D6563617374
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C1103FF00000000000000000000000000000000000000000000
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: FA:8F:CA:7D:1A:E3
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:off
                    ESSID:"Living Room"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000cd60d02a2
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 000B4C6976696E6720526F6F6D
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C1103FF00000000000000000000000000000000000000000000
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: 20:25:64:32:CA:B7
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"Kindred1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000239d168523
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 00084B696E6472656431
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 0B0500001E0000
                    IE: Unknown: 2D1ABC191BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080500080000000040
                    IE: Unknown: DD790050F204104A0001101044000102103B00010310470010346D13921D190C891191D84EE5DE3B4510210005436973636F10230005436973636F1024000631323334353610420007303030303030311054000800060050F204000110110006386434336366100800022008103C0001031049000600372A000120
                    IE: Unknown: DD090010180200000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: 46057208010000
          Cell 05 - Address: 8C:57:9B:12:8F:20
                    Channel:112
                    Frequency:5.56 GHz (Channel 112)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"DIRECTV_WVB_13E31FF6"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000331f65ecc0c
                    Extra: Last beacon: 1176ms ago
                    IE: Unknown: 0014444952454354565F5756425F3133453331464636
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030170
                    IE: Unknown: 050400030000
                    IE: Unknown: 2D1ACF0117FFFFFFFFFEFFFFFFFF1F000001000000000018E6E71900
                    IE: Unknown: 3D16700F0400000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0B002686010300DD00000101
                    IE: Unknown: DD220050F204104A00011010440001011049000600372A00012010490006002686000101
          Cell 06 - Address: 20:25:64:4C:48:63
                    Channel:161
                    Frequency:5.805 GHz
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"Kindred1"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000239d048c96
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 00084B696E6472656431
                    IE: Unknown: 01088C129824B048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0B050400020000
                    IE: Unknown: 2D1AFE091BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16A10F1600000000000000000000000000000000000000
                    IE: Unknown: 7F080400080000000040
                    IE: Unknown: DD790050F204104A0001101044000102103B00010310470010346D13921D190C891191D84EE5DE3B4510210005436973636F10230005436973636F1024000631323334353610420007303030303030311054000800060050F204000110110006386434336366100800022008103C0001031049000600372A000120
                    IE: Unknown: DD090010180204000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: 46057208010000
          Cell 07 - Address: E2:88:5D:83:CD:7F
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007342d60a68
                    Extra: Last beacon: 2940ms ago
                    IE: Unknown: 000C000000000000000000000000
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32048C129860
                    IE: Unknown: 2D1ABD181BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: DD090010180200001C0000
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
          Cell 08 - Address: 60:FE:20:3C:DB:0A
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"ATT350"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000073428ce39e
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 0006415454333530
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180203F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00
          Cell 09 - Address: E0:88:5D:83:CD:7E
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"TheGasGuys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007342d61177
                    Extra: Last beacon: 2936ms ago
                    IE: Unknown: 000A54686547617347757973
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32048C129860
                    IE: Unknown: 2D1ABD181BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
                    IE: Unknown: DD090010180202001C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
          Cell 10 - Address: 08:86:3B:83:62:14
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"belkin.214"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003bf9cf176
                    Extra: Last beacon: 2880ms ago
                    IE: Unknown: 000A62656C6B696E2E323134
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: Unknown: 050400010004
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1603050000000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3403050000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
                    IE: Unknown: DD0E0050F204104A0001101044000102


```

```
[    3.171032] rtl8821ae 0000:01:00.0: enabling device (0000 -> 0003)
[    3.268670] rtl8821ae: Using firmware rtlwifi/rtl8821aefw.bin
[    3.268681] rtl8821ae: Using firmware rtlwifi/rtl8821aefw_wowlan.bin
[    3.293877] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    3.294612] rtlwifi: rtlwifi: wireless switch is on
[    3.985346] rtl8821ae 0000:01:00.0 wlp1s0: renamed from wlan0
```

My ethernet has also started giving me the same problem, although not as bad.

---

### Post by chili555 on 2017-01-09
> My ethernet has also started giving me the same problem, although not as bad.Is it possible it is the router?

Which of these several access points are you having trouble with? We are going to hate to see it's one with TKIP!

---

### Post by bzpnut on 2017-01-10
I don't think so, as all my other devices work fine on my wifi. Also, the access point I'm having trouble with is "Kindred1".

---

### Post by chili555 on 2017-01-10
> Cell 04 - Address: 20:25:64:32:CA:B7
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"Kindred1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000239d168523
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 00084B696E6472656431
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher :[COLOR="#FF0000"] TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 0B0500001E0000
                    IE: Unknown: 2D1ABC191BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080500080000000040
                    IE: Unknown: DD790050F204104A0001101044000102103B00010310470010346D13921D190C891191D84EE5DE3B4510210005436973636F10230005436973636F1024000631323334353610420007303030303030311054000800060050F204000110110006386434336366100800022008103C0001031049000600372A000120
                    IE: Unknown: DD090010180200000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: 46057208010000Please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

---

### Post by bzpnut on 2017-01-10
I did as you instructed and got this as the output for "gksudo gedit /etc/default/crda":

```
(gksudo:17982): GConf-CRITICAL **: gconf_value_free: assertion 'value != NULL' failed

** (gedit:17998): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-spell-enabled not supported

** (gedit:17998): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-encoding not supported

** (gedit:17998): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported

```

I set my location to US and it APPEARS to have saved.

---

### Post by chili555 on 2017-01-10
The warnings are harmless.> I set my location to US and it APPEARS to have saved.Check:```
cat /etc/default/crda
```It should say:```
# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.

REGDOMAIN=US
```If so, it is set as requested.

So is the connectivity now improved?

---

### Post by bzpnut on 2017-01-10
Not really. I had a connection for a moment but it's gone now.

---

### Post by chili555 on 2017-01-10
> **bzpnut said:**
> Not really. I had a connection for a moment but it's gone now.With the router changes I suggested and the router rebooted?

May we see:```
dmesg | grep rtl | tail -n15
```

---

### Post by bzpnut on 2017-01-10
When I try to connect to wifi it now says:
> **Failed to add/activate connection**

(7) The access point /org/freedesktop/NetworkManager/AccessPoint/24 was not in the scan list.
```
[    3.576672] rtl8821ae 0000:01:00.0: enabling device (0000 -> 0003)
[    3.593295] rtl8821ae: Using firmware rtlwifi/rtl8821aefw.bin
[    3.593304] rtl8821ae: Using firmware rtlwifi/rtl8821aefw_wowlan.bin
[    3.612385] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    3.612686] rtlwifi: rtlwifi: wireless switch is on
[    4.256846] rtl8821ae 0000:01:00.0 wlp1s0: renamed from wlan0
[ 1547.947895] Modules linked in: hid_generic hidp hid drbg ansi_cprng ctr ccm rfcomm bnep nls_iso8859_1 asus_nb_wmi asus_wmi sparse_keymap kvm_amd kvm irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel arc4 rtl8821ae snd_hda_codec_conexant aesni_intel snd_hda_codec_generic aes_x86_64 snd_hda_codec_hdmi lrw gf128mul snd_hda_intel glue_helper snd_hda_codec uvcvideo btcoexist snd_hda_core ablk_helper rtl_pci videobuf2_vmalloc cryptd rtlwifi videobuf2_memops snd_hwdep mac80211 videobuf2_v4l2 videobuf2_core v4l2_common videodev snd_pcm btusb snd_seq_midi btrtl media btbcm snd_seq_midi_event cfg80211 btintel snd_rawmidi bluetooth snd_seq snd_seq_device snd_timer joydev input_leds snd serio_raw edac_mce_amd soundcore k10temp fam15h_power edac_core i2c_piix4 shpchp 8250_dw mac_hid i2c_designware_platform

```

---

### Post by chili555 on 2017-01-10
The 'modules linked in' usually follows a kernel oops or crash. I recommend that you investigate and fix the cause. Look around at the time-stamp just before the 'modules linked in'; in your case, 1547.xxx. Scroll back and forth in the log with:```
dmesg | less
```Get out of *less* with q.> (7) The access point /org/freedesktop/NetworkManager/AccessPoint/24 was not in the scan list.Does your access point no longer show up in scan?```
sudo iwlist scan
```Did you inadvertantly make a change in the router that makes your SSID no longer visible? For example, setting the wireless to 5 gHz will make it invisible to wireless cards that are incapable of 5 gHz. Making the SSID not broadcast will make it, obviously, invisible. Setting the router to 802.11N and AC only will make it invisible to cards that only do 802.11B and G.

---

### Post by bzpnut on 2017-01-10
Here is everything listed as "1547.XX":
```
[ 1547.947870] ------------[ cut here ]------------
[ 1547.947889] WARNING: CPU: 2 PID: 1114 at /build/linux-EO9xOi/linux-4.4.0/net/sched/sch_generic.c:
306 dev_watchdog+0x237/0x240()
[ 1547.947893] NETDEV WATCHDOG: enp2s0 (r8169): transmit queue 0 timed out
[ 1547.947895] Modules linked in: hid_generic hidp hid drbg ansi_cprng ctr ccm rfcomm bnep nls_iso88
59_1 asus_nb_wmi asus_wmi sparse_keymap kvm_amd kvm irqbypass crct10dif_pclmul crc32_pclmul ghash_cl
mulni_intel arc4 rtl8821ae snd_hda_codec_conexant aesni_intel snd_hda_codec_generic aes_x86_64 snd_h
da_codec_hdmi lrw gf128mul snd_hda_intel glue_helper snd_hda_codec uvcvideo btcoexist snd_hda_core a
blk_helper rtl_pci videobuf2_vmalloc cryptd rtlwifi videobuf2_memops snd_hwdep mac80211 videobuf2_v4
l2 videobuf2_core v4l2_common videodev snd_pcm btusb snd_seq_midi btrtl media btbcm snd_seq_midi_eve
nt cfg80211 btintel snd_rawmidi bluetooth snd_seq snd_seq_device snd_timer joydev input_leds snd serio_raw edac_mce_amd soundcore k10temp fam15h_power edac_core i2c_piix4 shpchp 8250_dw mac_hid i2c_designware_platform
[ 1547.947972]  tpm_crb i2c_designware_core parport_pc ppdev lp parport autofs4 amdkfd amd_iommu_v2 amdgpu i2c_algo_bit ttm drm_kms_helper psmouse syscopyarea sysfillrect r8169 sysimgblt fb_sys_fops ahci drm libahci mii wmi fjes video
[ 1547.948002] CPU: 2 PID: 1114 Comm: Xorg Not tainted 4.4.0-59-generic #80-Ubuntu
[ 1547.948006] Hardware name: ASUSTeK COMPUTER INC. X555DA/X555DA, BIOS X555DA.520 09/02/2016
[ 1547.948009]  0000000000000286 00000000a1402919 ffff8801fed03d98 ffffffff813f7583
[ 1547.948014]  ffff8801fed03de0 ffffffff81d6afc8 ffff8801fed03dd0 ffffffff810812d2
[ 1547.948019]  0000000000000000 ffff8801f14b9e80 0000000000000002 ffff8801f5628000
[ 1547.948023] Call Trace:
[ 1547.948027]  <IRQ>  [<ffffffff813f7583>] dump_stack+0x63/0x90
[ 1547.948063]  [<ffffffff810812d2>] warn_slowpath_common+0x82/0xc0
[ 1547.948068]  [<ffffffff8108136c>] warn_slowpath_fmt+0x5c/0x80
[ 1547.948092]  [<ffffffff810ac189>] ? try_to_wake_up+0x49/0x3f0
[ 1547.948098]  [<ffffffff81753947>] dev_watchdog+0x237/0x240
[ 1547.948103]  [<ffffffff81753710>] ? qdisc_rcu_free+0x40/0x40
[ 1547.948109]  [<ffffffff810ecda5>] call_timer_fn+0x35/0x120
[ 1547.948113]  [<ffffffff81753710>] ? qdisc_rcu_free+0x40/0x40
[ 1547.948118]  [<ffffffff810ed75a>] run_timer_softirq+0x23a/0x2f0
[ 1547.948124]  [<ffffffff81085db1>] __do_softirq+0x101/0x290
[ 1547.948129]  [<ffffffff810860b3>] irq_exit+0xa3/0xb0
[ 1547.948135]  [<ffffffff8183afa2>] smp_apic_timer_interrupt+0x42/0x50
[ 1547.948140]  [<ffffffff81839262>] apic_timer_interrupt+0x82/0x90
[ 1547.948142]  <EOI>  [<ffffffff8170f990>] ? sock_unregister+0x60/0x60
[ 1547.948153]  [<ffffffff8170f9af>] ? sock_poll+0x1f/0x120
[ 1547.948157]  [<ffffffff8170fa97>] ? sock_poll+0x107/0x120
[ 1547.948163]  [<ffffffff812239d3>] do_select+0x383/0x810
[ 1547.948169]  [<ffffffff810b3a3a>] ? select_idle_sibling+0x2a/0x120
[ 1547.948173]  [<ffffffff81223420>] ? poll_select_copy_remaining+0x140/0x140
[ 1547.948177]  [<ffffffff81223420>] ? poll_select_copy_remaining+0x140/0x140
[ 1547.948181]  [<ffffffff81223420>] ? poll_select_copy_remaining+0x140/0x140
[ 1547.948185]  [<ffffffff81223420>] ? poll_select_copy_remaining+0x140/0x140
[ 1547.948189]  [<ffffffff81223420>] ? poll_select_copy_remaining+0x140/0x140
[ 1547.948192]  [<ffffffff81223420>] ? poll_select_copy_remaining+0x140/0x140
[ 1547.948196]  [<ffffffff81223420>] ? poll_select_copy_remaining+0x140/0x140
[ 1547.948200]  [<ffffffff81223420>] ? poll_select_copy_remaining+0x140/0x140
[ 1547.948204]  [<ffffffff81223420>] ? poll_select_copy_remaining+0x140/0x140
[ 1547.948208]  [<ffffffff8122402f>] core_sys_select+0x1cf/0x2f0
[ 1547.948215]  [<ffffffff8120ed46>] ? do_readv_writev+0x146/0x230
[ 1547.948221]  [<ffffffff81400429>] ? timerqueue_add+0x59/0xb0
[ 1547.948225]  [<ffffffff814004c4>] ? timerqueue_del+0x24/0x70
[ 1547.948228]  [<ffffffff810ef94c>] ? __remove_hrtimer+0x3c/0x90
[ 1547.948232]  [<ffffffff810efa71>] ? hrtimer_try_to_cancel+0xd1/0x130
[ 1547.948237]  [<ffffffff810f52ba>] ? ktime_get_ts64+0x4a/0xf0
[ 1547.948241]  [<ffffffff8122420a>] SyS_select+0xba/0x110
[ 1547.948246]  [<ffffffff818384f2>] entry_SYSCALL_64_fastpath+0x16/0x71
[ 1547.948250] ---[ end trace 797a6411c423bab1 ]---
[ 1547.966214] r8169 0000:02:00.0 enp2s0: link up

```
And the output for sudo iwlist scan:
```
enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlp1s0    No scan results

```
As far as I'm aware, I simply followed your instructions and made no other changes.

**EDIT:** Well, my network is once again listed, and I can connect to wifi again, but it's still very slow and constantly dropping my connection. Idk why it disappeared or why it came back, but it did.

---

