---
title: "RTL8723be WiFi drops constantly after Ubuntu 18.04 install"
date: 2018-08-27
forum: Networking &amp; Wireless
---

### Post by matanjonas on 2018-08-27
Hi to all.
I used to run Ubuntu 16.04 for a couple of years and due to some specific reasons I had to format and install a dual boot with Win10 and Ubuntu 18.04 on my HP laptop.
Previously on 16.04 I would occasionally have random network disconnects but usually restarting the network manager would solve it with no sweat.

Since installing 18.04 I've experienced relentless WiFi connection drops. After booting the system it will usually connect, and then every 30 seconds to 10 minutes, connection will invariably drop. Then I would have to turn WiFi off an on again, which will sometimes work, until it won't anymore and I have to resort to rebooting the system. On the Win10 partition there are no problems at all. 

A few days of googling this problem, I have tried updating everything, I've tried installing "rtlwifi_new" from github, I've tried setting the ant_sel=1 and ant_sel=2, to no avail. I've gone through countless threads on this forum and askubuntu and others, most offering some version of the above solutions, but nothing solves it.

Here's the pastebin of my wireless info script:
[http://paste.ubuntu.com/p/fhc6GdS928/](http://paste.ubuntu.com/p/fhc6GdS928/)

```
########## wireless info START ##########

Report from: 27 Aug 2018 20:39 IDT +0300

Booted last: 27 Aug 2018 00:00 IDT +0300

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 4.15.0-33-generic #36-Ubuntu SMP Wed Aug 15 16:00:05 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company RTL810xE PCI Express Fast Ethernet controller [103c:2337]
    Kernel driver in use: r8169

0a:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:2231]
    Kernel driver in use: rtl8723be

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b40e Chicony Electronics Co., Ltd HP Truevision HD camera
Bus 001 Device 002: ID 0bda:b001 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8723be              98304  0
btcoexist             172032  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
rtl_pci                32768  1 rtl8723be
rtlwifi                98304  3 rtl_pci,btcoexist,rtl8723be
mac80211              778240  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              622592  2 mac80211,rtlwifi
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
wmi_bmof               16384  0
mxm_wmi                16384  1 nouveau
wmi                    24576  4 wmi_bmof,mxm_wmi,nouveau,hp_wmi

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
2: enp8s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'enp8s0' [IF1]> brd <MAC address>
4: wlp10s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether <MAC 'wlp10s0' [IF2]> brd <MAC address>
    inet 10.0.0.8/24 brd 10.0.0.255 scope global dynamic noprefixroute wlp10s0
       valid_lft 3398sec preferred_lft 3398sec
    inet6 fe80::d020:c68d:1b7:3acf/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

enp8s0    no wireless extensions.

lo        no wireless extensions.

wlp10s0   IEEE 802.11  ESSID:"TP-LINK_96AA8E"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: <MAC 'TP-LINK_96AA8E' [AC2]>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:11   Missed beacon:0

##### route #############################

default via 10.0.0.138 dev wlp10s0 proto dhcp metric 600 
10.0.0.0/24 dev wlp10s0 proto kernel scope link src 10.0.0.8 metric 600 
169.254.0.0/16 dev wlp10s0 scope link metric 1000 

##### resolv.conf #######################

nameserver 127.0.0.53
search Home

##### network managers ##################

Installed:

    NetworkManager

Running:

root       841     1  0 20:24 ?        00:00:04 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp10s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8723BE PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8723be
GENERAL.DRIVER-VERSION:                 4.15.0-33-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp10s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:0a:00.0/net/wlp10s0
GENERAL.IP-IFACE:                       wlp10s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     TP-LINK_96AA8E
GENERAL.CON-UUID:                       c15bd3f2-3e88-4656-89ae-87017a6a78a3
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/7
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     150 Mb/s
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
IP4.ADDRESS[1]:                         10.0.0.8/24
IP4.GATEWAY:                            10.0.0.138
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 10.0.0.138, mt = 600
IP4.ROUTE[2]:                           dst = 10.0.0.0/24, nh = 0.0.0.0, mt = 600
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             10.0.0.138
IP4.DOMAIN[1]:                          Home
DHCP4.OPTION[1]:                        requested_ntp_servers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        expiry = 1535394964
DHCP4.OPTION[8]:                        requested_netbios_scope = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       broadcast_address = 10.0.0.255
DHCP4.OPTION[11]:                       dhcp_message_type = 5
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       requested_wpad = 1
DHCP4.OPTION[14]:                       ip_address = 10.0.0.8
DHCP4.OPTION[15]:                       requested_static_routes = 1
DHCP4.OPTION[16]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       dhcp_lease_time = 3600
DHCP4.OPTION[19]:                       domain_name = Home
DHCP4.OPTION[20]:                       domain_name_servers = 10.0.0.138
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       routers = 10.0.0.138
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       requested_interface_mtu = 1
DHCP4.OPTION[26]:                       network_number = 10.0.0.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 10.0.0.138
IP6.ADDRESS[1]:                         fe80::d020:c68d:1b7:3acf/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 600
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   c15bd3f2-3e88-4656-89ae-87017a6a78a3 | TP-LINK_96AA8E

GENERAL.DEVICE:                         enp8s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL810xE PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp8s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:08:00.0/net/enp8s0
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

SSID                              BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY   ACTIVE  IN-USE 
--                                <MAC '' [AC3]>  Infra  4     2427 MHz  65 Mbit/s   84      &#9602;&#9604;&#9606;&#9608;  --         no             
TP-LINK_96AA8E                    <MAC 'TP-LINK_96AA8E' [AC2]>  Infra  4     2427 MHz  270 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     *      
Ben.Haim                          <MAC 'Ben.Haim' [AC6]>  Infra  10    2457 MHz  130 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA2       no             
Ben.Haim.Mother                   <MAC 'Ben.Haim.Mother' [AC1]>  Infra  1     2412 MHz  270 Mbit/s  57      &#9602;&#9604;&#9606;_  --         no             
AEH-W4A1-b0411d28a1e8             <MAC 'AEH-W4A1-b0411d28a1e8' [AC4]>  Infra  7     2442 MHz  65 Mbit/s   57      &#9602;&#9604;&#9606;_  WPA2       no             
--                                <MAC '' [AC7]>  Infra  10    2457 MHz  65 Mbit/s   54      &#9602;&#9604;__  --         no             
DIRECT-BD-HP DeskJet 4670 series  <MAC 'DIRECT-BD-HP DeskJet 4670 series' [AC5]>  Infra  10    2457 MHz  65 Mbit/s   50      &#9602;&#9604;__  WPA2       no             

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

[[/etc/NetworkManager/system-connections/OnePlus5]] (600 root)
[connection] id=OnePlus5 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp10s0' [IF2]> | mac-address-blacklist= | ssid=OnePlus5
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/TP-LINK_96AA8E]] (600 root)
[connection] id=TP-LINK_96AA8E | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp10s0' [IF2]> | mac-address-blacklist= | ssid=TP-LINK_96AA8E
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Asia/Jerusalem (based on set time zone)

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

enp8s0    no frequency information.

lo        no frequency information.

wlp10s0   13 channels in total; available frequencies :
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
          Current Frequency:2.427 GHz (Channel 4)

##### iwlist scan #######################

enp8s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.427 GHz (Channel 4)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      3   APs on   Frequency:2.457 GHz (Channel 10)

wlp10s0   Scan completed :
          Cell 01 - Address: <MAC 'Ben.Haim.Mother' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:off
                    ESSID:"Ben.Haim.Mother"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000017ff121859
                    Extra: Last beacon: 68ms ago
          Cell 02 - Address: <MAC 'TP-LINK_96AA8E' [AC2]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_96AA8E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000049f1d6964
                    Extra: Last beacon: 68ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC '' [AC3]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000049f3d6140
                    Extra: Last beacon: 240ms ago
          Cell 04 - Address: <MAC 'AEH-W4A1-b0411d28a1e8' [AC4]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"AEH-W4A1-b0411d28a1e8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000017fe1e2852
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'DIRECT-BD-HP DeskJet 4670 series' [AC5]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-BD-HP DeskJet 4670 series"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000017fd933dd4
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Ben.Haim' [AC6]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Ben.Haim"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000017f87061f2
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC '' [AC7]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000017f75b9142
                    Extra: Last beacon: 19100ms ago

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw_36.bin
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     1B45BB96576F0C4D6674527
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
retpoline:      Y
name:           rtl8723be
vermagic:       4.15.0-33-generic SMP mod_unload 
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
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           ant_sel:Set to 1 or 2 to force antenna number (default 0)
 (int)

[rtl8723_common]
filename:       /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     0A27C1EE329AC6FD4630C03
depends:        
retpoline:      Y
name:           rtl8723_common
vermagic:       4.15.0-33-generic SMP mod_unload 

[rtl_pci]
filename:       /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     6081DC1832010BD0C4C8DDC
depends:        mac80211,rtlwifi
retpoline:      Y
name:           rtl_pci
vermagic:       4.15.0-33-generic SMP mod_unload 

[rtlwifi]
filename:       /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     C3D6C55583BFB4BF0EE61E2
depends:        mac80211,cfg80211
retpoline:      Y
name:           rtlwifi
vermagic:       4.15.0-33-generic SMP mod_unload 

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
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

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
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
ant_sel: 0
debug: 0
disable_watchdog: N
fwlps: N
ips: Y
msi: N
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
options iwlwifi 11n_disable=1

[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be fwlps=0 ant_sel=1

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[  130.324251] rtlwifi: AP off, try to reconnect now
[  130.324285] wlp10s0: Connection to AP <MAC 'TP-LINK_96AA8E' [AC2]> lost
[  140.402773] rtlwifi: AP off, try to reconnect now
[  147.143112] wlp10s0: Connection to AP <MAC address> lost
[  162.928672] IPv6: ADDRCONF(NETDEV_UP): wlp10s0: link is not ready
[  185.519851] rtl8723be: Failed to polling write LLT done at address 0!
[  185.519854] rtl8723be: Init MAC failed
[  185.970285] IPv6: ADDRCONF(NETDEV_UP): wlp10s0: link is not ready (repeated 2 times)
[  187.034197] wlp10s0: authenticate with <MAC 'TP-LINK_96AA8E' [AC2]>
[  187.044375] wlp10s0: send auth to <MAC 'TP-LINK_96AA8E' [AC2]> (try 1/3)
[  187.147793] wlp10s0: send auth to <MAC 'TP-LINK_96AA8E' [AC2]> (try 2/3)
[  187.251928] wlp10s0: send auth to <MAC 'TP-LINK_96AA8E' [AC2]> (try 3/3)
[  187.355912] wlp10s0: authentication with <MAC 'TP-LINK_96AA8E' [AC2]> timed out
[  188.433379] wlp10s0: authenticate with <MAC 'TP-LINK_96AA8E' [AC2]>
[  188.452307] wlp10s0: send auth to <MAC 'TP-LINK_96AA8E' [AC2]> (try 1/3)
[  188.555768] wlp10s0: send auth to <MAC 'TP-LINK_96AA8E' [AC2]> (try 2/3)
[  188.659721] wlp10s0: send auth to <MAC 'TP-LINK_96AA8E' [AC2]> (try 3/3)
[  188.763809] wlp10s0: authentication with <MAC 'TP-LINK_96AA8E' [AC2]> timed out
[  190.236760] wlp10s0: authenticate with <MAC 'TP-LINK_96AA8E' [AC2]>
[  190.256181] wlp10s0: send auth to <MAC 'TP-LINK_96AA8E' [AC2]> (try 1/3)
[  191.691573] wlp10s0: send auth to <MAC 'TP-LINK_96AA8E' [AC2]> (try 2/3)
[  192.683525] wlp10s0: send auth to <MAC 'TP-LINK_96AA8E' [AC2]> (try 3/3)
[  193.707500] wlp10s0: authentication with <MAC 'TP-LINK_96AA8E' [AC2]> timed out
[  195.672037] wlp10s0: authenticate with <MAC 'TP-LINK_96AA8E' [AC2]>
[  195.691795] wlp10s0: send auth to <MAC 'TP-LINK_96AA8E' [AC2]> (try 1/3)
[  196.683284] wlp10s0: send auth to <MAC 'TP-LINK_96AA8E' [AC2]> (try 2/3)
[  197.707221] wlp10s0: send auth to <MAC 'TP-LINK_96AA8E' [AC2]> (try 3/3)
[  198.699224] wlp10s0: authentication with <MAC 'TP-LINK_96AA8E' [AC2]> timed out
[  208.670332] wlp10s0: authenticate with <MAC 'TP-LINK_96AA8E' [AC2]>
[  208.680606] wlp10s0: send auth to <MAC 'TP-LINK_96AA8E' [AC2]> (try 1/3)
[  209.706569] wlp10s0: send auth to <MAC 'TP-LINK_96AA8E' [AC2]> (try 2/3)
[  210.730377] wlp10s0: send auth to <MAC 'TP-LINK_96AA8E' [AC2]> (try 3/3)
[  211.722411] wlp10s0: authentication with <MAC 'TP-LINK_96AA8E' [AC2]> timed out
[  211.891592] IPv6: ADDRCONF(NETDEV_UP): wlp10s0: link is not ready
[  212.883727] wlp10s0: authenticate with <MAC 'TP-LINK_96AA8E' [AC2]>
[  212.893904] wlp10s0: send auth to <MAC 'TP-LINK_96AA8E' [AC2]> (try 1/3)
[  213.706305] wlp10s0: send auth to <MAC 'TP-LINK_96AA8E' [AC2]> (try 2/3)
[  214.698243] wlp10s0: send auth to <MAC 'TP-LINK_96AA8E' [AC2]> (try 3/3)
[  215.690156] wlp10s0: authentication with <MAC 'TP-LINK_96AA8E' [AC2]> timed out
[  228.796794] IPv6: ADDRCONF(NETDEV_UP): wlp10s0: link is not ready (repeated 2 times)
[  229.830699] wlp10s0: authenticate with <MAC 'TP-LINK_96AA8E' [AC2]>
[  229.840891] wlp10s0: send auth to <MAC 'TP-LINK_96AA8E' [AC2]> (try 1/3)
[  229.941291] wlp10s0: send auth to <MAC 'TP-LINK_96AA8E' [AC2]> (try 2/3)
[  230.045298] wlp10s0: send auth to <MAC 'TP-LINK_96AA8E' [AC2]> (try 3/3)
[  230.149291] wlp10s0: authentication with <MAC 'TP-LINK_96AA8E' [AC2]> timed out
[  231.214426] wlp10s0: authenticate with <MAC 'TP-LINK_96AA8E' [AC2]>
[  231.233650] wlp10s0: send auth to <MAC 'TP-LINK_96AA8E' [AC2]> (try 1/3)
[  231.316630] wlp10s0: authenticated
[  231.317123] wlp10s0: associate with <MAC 'TP-LINK_96AA8E' [AC2]> (try 1/3)
[  231.418110] wlp10s0: RX AssocResp from <MAC 'TP-LINK_96AA8E' [AC2]> (capab=0x411 status=0 aid=2)
[  231.418354] wlp10s0: associated
[  231.428992] IPv6: ADDRCONF(NETDEV_CHANGE): wlp10s0: link becomes ready
[  301.576057] rtlwifi: AP off, try to reconnect now
[  301.576075] wlp10s0: Connection to AP <MAC 'TP-LINK_96AA8E' [AC2]> lost
[  311.655519] rtlwifi: AP off, try to reconnect now
[  318.448181] wlp10s0: Connection to AP <MAC address> lost
[  362.560355] rtl8723be: Using firmware rtlwifi/rtl8723befw_36.bin
[  362.562275] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[  362.562722] rtlwifi: rtlwifi: wireless switch is on
[  362.571322] rtl8723be 0000:0a:00.0 wlp10s0: renamed from wlan0
[  362.618809] IPv6: ADDRCONF(NETDEV_UP): wlp10s0: link is not ready (repeated 3 times)
[  371.206388] wlp10s0: authenticate with <MAC 'TP-LINK_96AA8E' [AC2]>
[  371.216580] wlp10s0: send auth to <MAC 'TP-LINK_96AA8E' [AC2]> (try 1/3)
[  371.219236] wlp10s0: authenticated
[  371.220796] wlp10s0: associate with <MAC 'TP-LINK_96AA8E' [AC2]> (try 1/3)
[  371.224331] wlp10s0: RX AssocResp from <MAC 'TP-LINK_96AA8E' [AC2]> (capab=0x411 status=0 aid=2)
[  371.224656] wlp10s0: associated
[  371.231576] IPv6: ADDRCONF(NETDEV_CHANGE): wlp10s0: link becomes ready
[  395.809973] wlp10s0: deauthenticating from <MAC 'TP-LINK_96AA8E' [AC2]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  398.391386] IPv6: ADDRCONF(NETDEV_UP): wlp10s0: link is not ready (repeated 2 times)
[  399.426261] wlp10s0: authenticate with <MAC 'TP-LINK_96AA8E' [AC2]>
[  399.436429] wlp10s0: send auth to <MAC 'TP-LINK_96AA8E' [AC2]> (try 1/3)
[  399.539095] wlp10s0: send auth to <MAC 'TP-LINK_96AA8E' [AC2]> (try 2/3)
[  399.541243] wlp10s0: authenticated
[  399.543124] wlp10s0: associate with <MAC 'TP-LINK_96AA8E' [AC2]> (try 1/3)
[  399.555298] wlp10s0: RX AssocResp from <MAC 'TP-LINK_96AA8E' [AC2]> (capab=0x411 status=0 aid=2)
[  399.555613] wlp10s0: associated
[  399.565750] IPv6: ADDRCONF(NETDEV_CHANGE): wlp10s0: link becomes ready
[  682.705441] rtlwifi: AP off, try to reconnect now
[  682.705469] wlp10s0: Connection to AP <MAC 'TP-LINK_96AA8E' [AC2]> lost
[  692.784816] rtlwifi: AP off, try to reconnect now
[  699.549361] wlp10s0: Connection to AP <MAC address> lost
[  728.564497] IPv6: ADDRCONF(NETDEV_UP): wlp10s0: link is not ready (repeated 3 times)
[  735.907561] wlp10s0: authenticate with <MAC 'TP-LINK_96AA8E' [AC2]>
[  735.917747] wlp10s0: send auth to <MAC 'TP-LINK_96AA8E' [AC2]> (try 1/3)
[  735.919408] wlp10s0: authenticated
[  735.927082] wlp10s0: associate with <MAC 'TP-LINK_96AA8E' [AC2]> (try 1/3)
[  735.940190] wlp10s0: RX AssocResp from <MAC 'TP-LINK_96AA8E' [AC2]> (capab=0x411 status=0 aid=2)
[  735.940502] wlp10s0: associated
[  735.955887] IPv6: ADDRCONF(NETDEV_CHANGE): wlp10s0: link becomes ready

########## wireless info END ############
```


I am completely overwhelmed by this problem. It is impossible to do anything at all, just running the script right now required me like 3 resets of the network manager and a complete reboot. Not to mention doing anything more substantial like watching Netflix or anything like that.

My eternal gratitude to anyone helping on this

---

### Post by firefox_user2 on 2018-08-27
Sorry for your wifi problem. I had a similar problem as well as slower wifi speed after upgrading my laptop which also had a RTL 8723 BE wifi card in it. Out of desperation, I replaced it with an Intel 7260 AC dual band card and added a second antenna on it. It cured my problem as well as increased my download speed from 5 mps to 34 mps using speedtest.net  I'm not saying that this will also work on your laptop. Perhaps one of the experts can help you out. Just thought I'd pass along what I did to fix my problem. Don't give up, these guys are good.

---

### Post by jeremy31 on 2018-08-28
I would change some settings on the wifi router, change channel from auto to 6 or 11, change encryption to WPA2 only, no WEP or TKIP, save the settings and reboot the router
Then ```
sudo rm /etc/modprobe.d/rtl8723be.conf
```
Then test the ant_sel parameter with ```
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=1
iwlist scan | egrep -i 'SSID|level'
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=2
iwlist scan | egrep -i 'SSID|level'
```
See what setting is better

---

