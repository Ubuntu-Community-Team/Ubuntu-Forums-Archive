---
title: "wifi connects, but no internet - Intel 2200"
date: 2016-07-26
forum: Networking &amp; Wireless
---

### Post by ding47 on 2016-07-26
> **Wild Man said:**
> Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

I am having this problem also.  I have done what is suggested here, on youtube, on help.ubuntu, to no avail.  I have been struggling with this for almost a week.  I have a Lenovo x230 with the only operating system being Ubuntu 16.04
The laptop sees and connects to wifi, but I am unable to get on the internet wirelessly.  Other devices (windows, android) have no trouble.  I have to use a wired connection.  
Please help.  I tried to make sense of the output, but I'm a newbie to linux.  Here are the results from the wireless script:

```



########## wireless info START ##########

Report from: 26 Jul 2016 15:47 EDT -0400

Booted last: 26 Jul 2016 00:00 EDT -0400

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo 82579LM Gigabit Network Connection [17aa:21f3]
    Kernel driver in use: e1000e

03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2200 [8086:0891] (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2200 BGN [8086:4222]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b2ea Chicony Electronics Co., Ltd Integrated Camera [ThinkPad]
Bus 001 Device 003: ID 147e:2020 Upek TouchChip Fingerprint Coprocessor (WBF advanced mode)
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwldvm                233472  0
mac80211              737280  1 iwldvm
iwlwifi               200704  1 iwldvm
cfg80211              565248  3 iwlwifi,mac80211,iwldvm
wmi                    20480  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s25   Link encap:Ethernet  HWaddr <MAC 'enp0s25' [IF1]>  
          inet addr:10.0.0.16  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::eec4:d0c6:9ce5:6bb4/64 Scope:Link
          inet6 addr: 2601:18d:300:4c70:258d:2924:8d1:3839/64 Scope:Global
          inet6 addr: 2601:18d:300:4c70:f01:1754:4412:bf4e/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45038 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19457 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:51424838 (51.4 MB)  TX bytes:2237517 (2.2 MB)
          Interrupt:20 Memory:f2500000-f2520000 

wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF2]>  
          inet addr:10.0.0.10  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::990c:13fe:33ab:13d9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:89 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1511 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8178 (8.1 KB)  TX bytes:179948 (179.9 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp0s25   no wireless extensions.

wlp3s0    IEEE 802.11bgn  ESSID:"HOME-E342"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'HOME-E342' [AC1]>   
          Bit Rate=78 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:73   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    100    0        0 enp0s25
0.0.0.0         10.0.0.1        0.0.0.0         UG    600    0        0 wlp3s0
10.0.0.0        0.0.0.0         255.255.255.0   U     100    0        0 enp0s25
10.0.0.0        0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp3s0

##### resolv.conf #######################

nameserver 127.0.1.1
search hsd1.ma.comcast.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root      2414     1  0 15:11 ?        00:00:03 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s25
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82579LM Gigabit Network Connection
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.13-3
GENERAL.HWADDR:                         <MAC 'enp0s25' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/enp0s25
GENERAL.IP-IFACE:                       enp0s25
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       b40c9f36-0d2c-4935-ba92-d30c507966e0
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/4
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{4}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   b40c9f36-0d2c-4935-ba92-d30c507966e0 | Wired connection 1
IP4.ADDRESS[1]:                         10.0.0.16/24
IP4.GATEWAY:                            10.0.0.1
IP4.DNS[1]:                             75.75.75.75
IP4.DNS[2]:                             75.75.76.76
IP4.DOMAIN[1]:                          hsd1.ma.comcast.net.
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        host_name = murph-ThinkPad-X230
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 10.0.0.1
DHCP4.OPTION[11]:                       expiry = 1470166474
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 10.0.0.1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 10.0.0.16
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       domain_name = hsd1.ma.comcast.net.
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       broadcast_address = 10.0.0.255
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       dhcp_lease_time = 604800
DHCP4.OPTION[24]:                       domain_name_servers = 75.75.75.75 75.75.76.76
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       network_number = 10.0.0.0
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 10.0.0.1
IP6.ADDRESS[1]:                         2601:18d:300:4c70:258d:2924:8d1:3839/64
IP6.ADDRESS[2]:                         2601:18d:300:4c70:f01:1754:4412:bf4e/64
IP6.ADDRESS[3]:                         fe80::eec4:d0c6:9ce5:6bb4/64
IP6.GATEWAY:                            fe80::200:caff:fe11:2233
IP6.DNS[1]:                             2001:558:feed::1
IP6.DNS[2]:                             2001:558:feed::2
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2001:558:feed::1 2001:558:feed::2
DHCP6.OPTION[3]:                        dhcp6_preference = 0
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        dhcp6_server_id = 0:1:0:1:1f:7:47:85:0:0:ca:11:22:33
DHCP6.OPTION[7]:                        dhcp6_client_id = 0:4:97:b:42:2:91:b:da:a2:93:e5:d0:a8:9f:56:f1:46

GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Centrino Wireless-N 2200 (BGN)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-31-generic
GENERAL.FIRMWARE-VERSION:               18.168.6.1
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       wlp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     HOME-E342
GENERAL.CON-UUID:                       691287a6-420f-4bfe-a84b-b11fd38940e7
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     78 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2,0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   691287a6-420f-4bfe-a84b-b11fd38940e7 | HOME-E342
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   f618e52e-5817-4b88-a734-56f615cb9831 | xfinitywifi
IP4.ADDRESS[1]:                         10.0.0.10/24
IP4.GATEWAY:                            10.0.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             75.75.75.75
IP4.DNS[2]:                             75.75.76.76
IP4.DOMAIN[1]:                          hsd1.ma.comcast.net.
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        host_name = murph-ThinkPad-X230
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 10.0.0.1
DHCP4.OPTION[11]:                       expiry = 1470165699
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 10.0.0.1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 10.0.0.10
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       domain_name = hsd1.ma.comcast.net.
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       broadcast_address = 10.0.0.255
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       dhcp_lease_time = 604800
DHCP4.OPTION[24]:                       domain_name_servers = 75.75.75.75 75.75.76.76
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       network_number = 10.0.0.0
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 10.0.0.1
IP6.ADDRESS[1]:                         fe80::990c:13fe:33ab:13d9/64
IP6.GATEWAY:                            

SSID           BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
xfinitywifi    <MAC 'xfinitywifi' [AN1]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  --         no        
HOME-E342      <MAC 'HOME-E342' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  79      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     * 
xfinitywifi    <MAC 'xfinitywifi' [AN3]>  Infra  6     2437 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  --         no        
CarlosHome2.4  <MAC 'CarlosHome2.4' [AN4]>  Infra  6     2437 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
--             <MAC '--' [AN5]>  Infra  6     2437 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        

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

[[/etc/NetworkManager/system-connections/US_Guest]] (600 root)
[connection] id=US_Guest | type=wifi | permissions=user:murph:;
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=US_Guest
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/xfinitywifi]] (600 root)
[connection] id=xfinitywifi | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=xfinitywifi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HOME-E342]] (600 root)
[connection] id=HOME-E342 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=HOME-E342
[ipv4] method=shared
[ipv6] method=ignore

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country US: DFS-FCC
    (2402 - 2472 @ 40), (N/A, 30), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A)
    (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
    (5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp0s25   no frequency information.

wlp3s0    11 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp0s25   Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)

wlp3s0    Scan completed :
          Cell 01 - Address: <MAC 'HOME-E342' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"HOME-E342"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006dafff18d3
                    Extra: Last beacon: 38480ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwldvm]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     6A40B68AAA6792A5BDEA010
depends:        mac80211,iwlwifi,cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           force_cam:force continuously aware mode (no power saving at all) (bool)

[mac80211]
filename:       /lib/modules/4.4.0-31-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     651BF6CBF283F6F817B8F3A
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
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
filename:       /lib/modules/4.4.0-31-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
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
swcrypto: 0
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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   10.739758] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   10.739760] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   10.739761] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   10.739763] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 2200 BGN, REV=0x104
[   10.739866] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   10.973880] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   11.134468] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
[   21.429491] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   21.429632] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled (repeated 2 times)
[   21.437387] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[   21.683713] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled (repeated 2 times)
[   21.691474] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[   21.750142] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   21.754046] IPv6: ADDRCONF(NETDEV_UP): enp0s25: link is not ready (repeated 2 times)
[   22.602862] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   23.132990] wlp3s0: authenticate with <MAC 'HOME-E342' [AC1]>
[   23.135119] wlp3s0: send auth to <MAC 'HOME-E342' [AC1]> (try 1/3)
[   23.137798] wlp3s0: authenticated
[   23.140859] wlp3s0: associate with <MAC 'HOME-E342' [AC1]> (try 1/3)
[   23.157215] wlp3s0: RX AssocResp from <MAC 'HOME-E342' [AC1]> (capab=0x411 status=0 aid=4)
[   23.160001] wlp3s0: associated
[   23.160075] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[   25.010894] e1000e: enp0s25 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   25.010930] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s25: link becomes ready
[  613.710384] wlp3s0: deauthenticating from <MAC 'HOME-E342' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  614.197653] wlp3s0: authenticate with <MAC 'HOME-E342' [AC1]>
[  614.199049] wlp3s0: send auth to <MAC 'HOME-E342' [AC1]> (try 1/3)
[  614.201023] wlp3s0: authenticated
[  614.204940] wlp3s0: associate with <MAC 'HOME-E342' [AC1]> (try 1/3)
[  614.226405] wlp3s0: RX AssocResp from <MAC 'HOME-E342' [AC1]> (capab=0x411 status=0 aid=4)
[  614.230676] wlp3s0: associated
[ 1211.937246] e1000e: enp0s25 NIC Link is Down
[ 1382.085810] e1000e: enp0s25 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx

########## wireless info END ############

```

---

### Post by jeremy31 on 2016-07-26
Moved to it's own thread from [https://ubuntuforums.org/showthread.php?t=2317960](https://ubuntuforums.org/showthread.php?t=2317960) that deals with an Atheros wifi issue

You may want to disable power management with ```
sudo iwconfig wlp3s0 power off
```
If you can change the encryption used on the wifi router to WPA2-AES, WPA2-PSK, or WPA2 only as you are currently using a mixed mode with TKIP that may be causing the issue and move it to channel 9.

In network manager disable IPv6

---

### Post by ding47 on 2016-07-27
Thanks for replying so fast!

I'll let you know how it goes.  I'm going to restart and see how it works.

---

### Post by ding47 on 2016-07-27
Okay, I disabled power management as above.  
I changed the encryption of the wifi router to WPA2-AES and moved to channel 9
I was unable to disable IPv6, but it did give me the option to ignore, so I chose that.  
I am still having the same issues after restarting laptop and router.  I ran the wireless script again and the results are below.  Is there anything else I can do?  I still have wifi recognized but no internet

```


########## wireless info START ##########

Report from: 27 Jul 2016 22:03 EDT -0400

Booted last: 27 Jul 2016 00:00 EDT -0400

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo 82579LM Gigabit Network Connection [17aa:21f3]
    Kernel driver in use: e1000e

03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2200 [8086:0891] (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2200 BGN [8086:4222]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b2ea Chicony Electronics Co., Ltd Integrated Camera [ThinkPad]
Bus 001 Device 003: ID 147e:2020 Upek TouchChip Fingerprint Coprocessor (WBF advanced mode)
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

iwldvm                233472  0
mac80211              737280  1 iwldvm
iwlwifi               200704  1 iwldvm
cfg80211              565248  3 iwlwifi,mac80211,iwldvm
wmi                    20480  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s25   Link encap:Ethernet  HWaddr <MAC 'enp0s25' [IF1]>  
          inet addr:10.0.0.16  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::db62:ef9c:390c:6553/64 Scope:Link
          inet6 addr: 2601:18d:300:4c70::c070/128 Scope:Global
          inet6 addr: 2601:18d:300:4c70:1dfb:79c:18bb:462/64 Scope:Global
          inet6 addr: 2601:18d:300:4c70:d99c:6aa0:f659:80d8/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22778 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15618 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23125426 (23.1 MB)  TX bytes:2266181 (2.2 MB)
          Interrupt:20 Memory:f2500000-f2520000 

wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3481 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3903 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1023056 (1.0 MB)  TX bytes:469744 (469.7 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp0s25   no wireless extensions.

wlp3s0    IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    100    0        0 enp0s25
10.0.0.0        0.0.0.0         255.255.255.0   U     100    0        0 enp0s25
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp0s25

##### resolv.conf #######################

nameserver 127.0.1.1
search hsd1.ma.comcast.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root      2452     1  0 20:07 ?        00:00:09 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s25
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82579LM Gigabit Network Connection
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.13-3
GENERAL.HWADDR:                         <MAC 'enp0s25' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/enp0s25
GENERAL.IP-IFACE:                       enp0s25
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       1e0f5328-d26e-4c53-8d22-f3f6446ea950
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/5
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   1e0f5328-d26e-4c53-8d22-f3f6446ea950 | Wired connection 1
IP4.ADDRESS[1]:                         10.0.0.16/24
IP4.GATEWAY:                            10.0.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             75.75.75.75
IP4.DNS[2]:                             75.75.76.76
IP4.DOMAIN[1]:                          hsd1.ma.comcast.net.
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        host_name = murph-ThinkPad-X230
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 10.0.0.1
DHCP4.OPTION[11]:                       expiry = 1470534052
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 10.0.0.1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 10.0.0.16
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       domain_name = hsd1.ma.comcast.net.
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       broadcast_address = 10.0.0.255
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       dhcp_lease_time = 864000
DHCP4.OPTION[24]:                       domain_name_servers = 75.75.75.75 75.75.76.76
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       network_number = 10.0.0.0
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 10.0.0.1
IP6.ADDRESS[1]:                         2601:18d:300:4c70::c070/128
IP6.ADDRESS[2]:                         2601:18d:300:4c70:1dfb:79c:18bb:462/64
IP6.ADDRESS[3]:                         2601:18d:300:4c70:d99c:6aa0:f659:80d8/64
IP6.ADDRESS[4]:                         fe80::db62:ef9c:390c:6553/64
IP6.GATEWAY:                            fe80::200:caff:fe11:2233
IP6.DNS[1]:                             2001:558:feed::1
IP6.DNS[2]:                             2001:558:feed::2
IP6.DNS[3]:                             2601:18d:300:4c70::
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:97:b:42:2:91:b:da:a2:93:e5:d0:a8:9f:56:f1:46
DHCP6.OPTION[2]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[3]:                        rebind = 483840
DHCP6.OPTION[4]:                        max_life = 604800
DHCP6.OPTION[5]:                        preferred_life = 604800
DHCP6.OPTION[6]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[7]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[8]:                        life_starts = 1469670021
DHCP6.OPTION[9]:                        dhcp6_status_code = success Assigned an address.
DHCP6.OPTION[10]:                       ip6_address = 2601:18d:300:4c70::c070
DHCP6.OPTION[11]:                       ip6_prefixlen = 64
DHCP6.OPTION[12]:                       renew = 302400
DHCP6.OPTION[13]:                       starts = 1469670021
DHCP6.OPTION[14]:                       iaid = 0e:6c:33:14
DHCP6.OPTION[15]:                       dhcp6_server_id = 0:1:0:1:1f:2b:c6:45:0:0:ca:11:22:33

GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Centrino Wireless-N 2200 (BGN)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-31-generic
GENERAL.FIRMWARE-VERSION:               18.168.6.1
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlp3s0
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
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/US_Guest]] (600 root)
[connection] id=US_Guest | type=wifi | permissions=user:murph:;
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=US_Guest
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/xfinitywifi]] (600 root)
[connection] id=xfinitywifi | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=xfinitywifi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HOME-E342]] (600 root)
[connection] id=HOME-E342 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=HOME-E342
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: America/New_York (based on set time zone)

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

enp0s25   no frequency information.

wlp3s0    13 channels in total; available frequencies :
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

##### iwlist scan #######################

wlp3s0    Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

enp0s25   Interface doesn't support scanning.

##### module infos ######################

[iwldvm]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     6A40B68AAA6792A5BDEA010
depends:        mac80211,iwlwifi,cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           force_cam:force continuously aware mode (no power saving at all) (bool)

[mac80211]
filename:       /lib/modules/4.4.0-31-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     651BF6CBF283F6F817B8F3A
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
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
filename:       /lib/modules/4.4.0-31-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
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
swcrypto: 0
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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[ 3011.417369] wlp3s0: authenticate with <MAC address>
[ 3011.418669] wlp3s0: send auth to <MAC address> (try 1/3)
[ 3011.423038] wlp3s0: authenticated
[ 3011.423991] wlp3s0: associate with <MAC address> (try 1/3)
[ 3011.440244] wlp3s0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=1)
[ 3011.442402] wlp3s0: associated
[ 3289.669320] e1000e: enp0s25 NIC Link is Down
[ 4734.877173] e1000e: enp0s25 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[ 5555.302605] wlp3s0: deauthenticated from <MAC address> (Reason: 3=DEAUTH_LEAVING)
[ 5562.045367] e1000e: enp0s25 NIC Link is Down
[ 5565.007381] e1000e: enp0s25 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[ 5570.962406] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 5571.468551] wlp3s0: authenticate with <MAC address>
[ 5571.474114] wlp3s0: send auth to <MAC address> (try 1/3)
[ 5571.476228] wlp3s0: authenticated
[ 5571.477921] wlp3s0: associate with <MAC address> (try 1/3)
[ 5571.510981] wlp3s0: associate with <MAC address> (try 2/3)
[ 5571.516245] wlp3s0: RX AssocResp from <MAC address> (capab=0x421 status=0 aid=1)
[ 5571.518800] wlp3s0: associated
[ 5571.518817] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[ 5584.443692] e1000e: enp0s25 NIC Link is Down
[ 5587.409709] e1000e: enp0s25 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[ 5592.676501] e1000e: enp0s25 NIC Link is Down
[ 5596.562780] e1000e: enp0s25 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[ 5613.321129] wlp3s0: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 5619.709143] wlp3s0: authenticate with <MAC address>
[ 5619.711839] wlp3s0: send auth to <MAC address> (try 1/3)
[ 5619.717741] wlp3s0: authenticated
[ 5619.718847] wlp3s0: associate with <MAC address> (try 1/3)
[ 5619.735137] wlp3s0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=3)
[ 5619.741791] wlp3s0: associated
[ 6302.955772] wlp3s0: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)

########## wireless info END ############

```

Thanks again

---

### Post by jeremy31 on 2016-07-28
Seems power management has been enabled again, see [http://askubuntu.com/a/614245/300665](http://askubuntu.com/a/614245/300665) and susbstitute wlp3s0 for wlan0 so your file would contain
```
[Unit]
Description=Turn of wlan power management
After=suspend.target

[Service]
Type=simple
ExecStartPre= /bin/sleep 10
ExecStart= /sbin/iwconfig wlp3s0 power off

[Install]
WantedBy=suspend.target
```

I also see that wireless is disabled in a file, so
```
gksudo gedit /var/lib/NetworkManager/NetworkManager.state
```

Find where it says ```
WirelessEnabled=false
```
and change to ```
WirelessEnabled=true
```
Save, exit gedit, and reboot

---

### Post by ding47 on 2016-07-29
Okay, I followed that link.  I edited the rc.local file, and created the wireless and root-resume files.  I went into the networkmanager.state file and changed it to true.  I rebooted and no luck.

I went through and triple checked all the files to make sure that they were saved and there were no errors, and referred to wlp3s0 instead of wlan.  rebooted again and still no luck

I ran iwconfig, and it is showing that Power Management is on again.  So, do you think that is what the issue is here, definitely the Power Management for wifi?  What else can I try to turn it off?


Update, I just turned off Power Management  by    sudo iwconfig wlp3s0 power off
then I ran iwconfig   and it showed Power Management off

so I unplugged and tried to connect to the internet again and no luck.

Newest results:
```


########## wireless info START ##########

Report from: 29 Jul 2016 21:36 EDT -0400

Booted last: 29 Jul 2016 00:00 EDT -0400

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo 82579LM Gigabit Network Connection [17aa:21f3]
    Kernel driver in use: e1000e

03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2200 [8086:0891] (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2200 BGN [8086:4222]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b2ea Chicony Electronics Co., Ltd Integrated Camera [ThinkPad]
Bus 001 Device 003: ID 147e:2020 Upek TouchChip Fingerprint Coprocessor (WBF advanced mode)
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwldvm                233472  0
mac80211              737280  1 iwldvm
iwlwifi               200704  1 iwldvm
cfg80211              565248  3 iwlwifi,mac80211,iwldvm
wmi                    20480  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s25   Link encap:Ethernet  HWaddr <MAC 'enp0s25' [IF1]>  
          inet addr:10.0.0.16  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::6343:6dc7:a2b3:6ade/64 Scope:Link
          inet6 addr: 2601:18d:300:4c70:4fb5:fb7a:fbcc:de39/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7468 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5440 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6271005 (6.2 MB)  TX bytes:610939 (610.9 KB)
          Interrupt:20 Memory:f2500000-f2520000 

wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF2]>  
          inet addr:10.0.0.10  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: 2601:18d:300:4c70:<IP6 'wlp3s0' [IF2]>/64 Scope:Global
          inet6 addr: 2601:18d:300:4c70:bc2c:58c0:c159:9705/64 Scope:Global
          inet6 addr: fe80::<IP6 'wlp3s0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:507 errors:0 dropped:0 overruns:0 frame:0
          TX packets:362 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60509 (60.5 KB)  TX bytes:47274 (47.2 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp0s25   no wireless extensions.

wlp3s0    IEEE 802.11bgn  ESSID:"HOME-E342"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: <MAC 'HOME-E342' [AC1]>   
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:27   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    100    0        0 enp0s25
0.0.0.0         10.0.0.1        0.0.0.0         UG    600    0        0 wlp3s0
10.0.0.0        0.0.0.0         255.255.255.0   U     100    0        0 enp0s25
10.0.0.0        0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp3s0

##### resolv.conf #######################

nameserver 127.0.1.1
search hsd1.ma.comcast.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root      2492     1  0 21:17 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s25
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82579LM Gigabit Network Connection
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.13-3
GENERAL.HWADDR:                         <MAC 'enp0s25' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/enp0s25
GENERAL.IP-IFACE:                       enp0s25
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       30b4ac52-55f2-4770-9ceb-6756f6b65116
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   30b4ac52-55f2-4770-9ceb-6756f6b65116 | Wired connection 1
IP4.ADDRESS[1]:                         10.0.0.16/24
IP4.GATEWAY:                            10.0.0.1
IP4.DNS[1]:                             75.75.75.75
IP4.DNS[2]:                             75.75.76.76
IP4.DOMAIN[1]:                          hsd1.ma.comcast.net.
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        host_name = murph-ThinkPad-X230
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 10.0.0.1
DHCP4.OPTION[11]:                       expiry = 1470705827
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 10.0.0.1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 10.0.0.16
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       domain_name = hsd1.ma.comcast.net.
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       broadcast_address = 10.0.0.255
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       dhcp_lease_time = 864000
DHCP4.OPTION[24]:                       domain_name_servers = 75.75.75.75 75.75.76.76
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       network_number = 10.0.0.0
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 10.0.0.1
IP6.ADDRESS[1]:                         2601:18d:300:4c70:4fb5:fb7a:fbcc:de39/64
IP6.ADDRESS[2]:                         fe80::6343:6dc7:a2b3:6ade/64
IP6.GATEWAY:                            fe80::200:caff:fe11:2233
IP6.ROUTE[1]:                           dst = 2601:18d:300:4c70::/64, nh = ::, mt = 100
IP6.DNS[1]:                             2601:18d:300:4c70::

GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Centrino Wireless-N 2200 (BGN)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-31-generic
GENERAL.FIRMWARE-VERSION:               18.168.6.1
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       wlp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     HOME-E342
GENERAL.CON-UUID:                       691287a6-420f-4bfe-a84b-b11fd38940e7
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
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
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   691287a6-420f-4bfe-a84b-b11fd38940e7 | HOME-E342
IP4.ADDRESS[1]:                         10.0.0.10/24
IP4.GATEWAY:                            10.0.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             75.75.75.75
IP4.DNS[2]:                             75.75.76.76
IP4.DOMAIN[1]:                          hsd1.ma.comcast.net.
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        host_name = murph-ThinkPad-X230
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 10.0.0.1
DHCP4.OPTION[11]:                       expiry = 1470705441
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 10.0.0.1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 10.0.0.10
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       domain_name = hsd1.ma.comcast.net.
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       broadcast_address = 10.0.0.255
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       dhcp_lease_time = 864000
DHCP4.OPTION[24]:                       domain_name_servers = 75.75.75.75 75.75.76.76
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       network_number = 10.0.0.0
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 10.0.0.1
IP6.ADDRESS[1]:                         2601:18d:300:4c70:<IP6 'wlp3s0' [IF2]>/64
IP6.ADDRESS[2]:                         2601:18d:300:4c70:bc2c:58c0:c159:9705/64
IP6.ADDRESS[3]:                         fe80::<IP6 'wlp3s0' [IF2]>/64
IP6.GATEWAY:                            fe80::200:caff:fe11:2233

SSID       BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
HOME-E342  <MAC 'HOME-E342' [AC1]>  Infra  9     2452 MHz  54 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  WPA2      yes     * 

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

[[/etc/NetworkManager/system-connections/US_Guest]] (600 root)
[connection] id=US_Guest | type=wifi | permissions=user:murph:;
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=US_Guest
[ipv4] method=auto
[ipv6] method=dhcp

[[/etc/NetworkManager/system-connections/xfinitywifi]] (600 root)
[connection] id=xfinitywifi | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=xfinitywifi
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/HOME-E342]] (600 root)
[connection] id=HOME-E342 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=HOME-E342
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country US: DFS-FCC
    (2402 - 2472 @ 40), (N/A, 30), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A)
    (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
    (5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp0s25   no frequency information.

wlp3s0    11 channels in total; available frequencies :
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
          Current Frequency:2.452 GHz (Channel 9)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp0s25   Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.452 GHz (Channel 9)

wlp3s0    Scan completed :
          Cell 01 - Address: <MAC 'HOME-E342' [AC1]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=70/70  Signal level=-31 dBm  
                    Encryption key:on
                    ESSID:"HOME-E342"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000027f8d35cee
                    Extra: Last beacon: 836752ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwldvm]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     6A40B68AAA6792A5BDEA010
depends:        mac80211,iwlwifi,cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           force_cam:force continuously aware mode (no power saving at all) (bool)

[mac80211]
filename:       /lib/modules/4.4.0-31-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     651BF6CBF283F6F817B8F3A
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
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
filename:       /lib/modules/4.4.0-31-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
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
swcrypto: 0
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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

sleep 10
iwconfig wlp3s0 power off
exit 0

##### pm-utils ##########################

[/etc/pm/power.d/root-resume.service] (755 root)
[Unit]
Description=Turn of wlan power management
After=suspend.target
[Service]
Type=simple
ExecStartPre= /bin/sleep 10
ExecStart= /sbin/iwconfig wlp3s0 power off
[Install]
WantedBy=suspend.target

[/etc/pm/power.d/wireless] (755 root)
/sbin/iwconfig wlp3s0  power off

##### udev rules ########################

##### dmesg #############################

[   10.415533] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   10.415536] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   10.415537] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   10.415539] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 2200 BGN, REV=0x104
[   10.415645] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   10.508155] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   10.585520] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
[   19.638561] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   19.638738] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled (repeated 2 times)
[   19.646503] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[   19.891997] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled (repeated 2 times)
[   19.899764] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[   19.956812] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   19.959494] IPv6: ADDRCONF(NETDEV_UP): enp0s25: link is not ready (repeated 2 times)
[   20.821622] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   21.374580] wlp3s0: authenticate with <MAC 'HOME-E342' [AC1]>
[   21.378021] wlp3s0: send auth to <MAC 'HOME-E342' [AC1]> (try 1/3)
[   21.380629] wlp3s0: authenticated
[   21.380792] wlp3s0: associate with <MAC 'HOME-E342' [AC1]> (try 1/3)
[   21.397096] wlp3s0: RX AssocResp from <MAC 'HOME-E342' [AC1]> (capab=0x411 status=0 aid=4)
[   21.399770] wlp3s0: associated
[   21.399826] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[   23.586863] e1000e: enp0s25 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[   23.586902] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s25: link becomes ready

########## wireless info END ############

```

---

### Post by jeremy31 on 2016-07-30
Reboot with the ethernet cable unplugged and see if you can
```
ping -c3 google.com
```

Then try ```
ping -c3 8.8.8.8
```

We are making progress as it looks like the wireless is enabled and can connect to your network.  Just testing if DNS is working

---

### Post by ding47 on 2016-07-30
Unknown host Google.com
ping 8.8.8.8 3 packets transmitted, 0 received

Yes all along the laptop has recognized my router, but it won't get onto the internet.  
Also other devices connect to the internet fine.

Thanks again

---

### Post by ding47 on 2016-08-01
Alright, so I'm taking it this means I have no connectivity at all?  Any idea of what I can do or where I can look for help on this.  I'm going round in circles.  

Thanks

---

### Post by jeremy31 on 2016-08-02
It almost seems the router may be blocking access.  Can you look at the router logs?
Do you use UFW?

---

### Post by ding47 on 2016-08-02
I'm not sure if I use UFW, I just figured out what it was when you said it.  If I do, should I disable it?

Also I only figured out how to get into my router when you told me to change my encryption.  I remember seeing logs, what should I be looking for when I get back in?

As always, thank you!  This should keep me busy for a while!

---

### Post by jeremy31 on 2016-08-03
Check the logs for DHCP requests from your computer, it might use IP or MAC address of the computer, ```
ifconfig
``` will show you the MAC under HWaddr

If you have UFW enabled, disable it as it will sometimes cause issues by blocking things it shouldn't

---

### Post by ding47 on 2016-08-06
Hi Jeremy,
UFW was not enabled.  There are firewalls on the router, I tried disabling those and it didn't help.  So I re-enabled them.

I didn't find any errors when searching for the MAC address in the router logs, but when I searched DHCP I found a lot of these: 
20160806 171609[ERROR] [ARRIS.SYS(pid=445)]: CLIENTDB: can't open /nvram/8/dhcpd/udhcpd.10.0.0.1.static_leases

Does that give any clue?

---

### Post by jeremy31 on 2016-08-07
Might be worth enabling aggressive TX on the wifi with ```
echo "options iwlwifi 11n_disable=8" | sudo tee /etc/modprobe.d/iwlopt.conf
```
Reboot with ethernet disconnected

---

### Post by ding47 on 2016-08-08
Well, that didn't work either.  Then I noticed that power management had turned back on, so I turned it off and tried again.  Still no luck.



I appreciate your continued help, I am getting very frustrated, I've been fighting with this for about 3 weeks now.

---

### Post by ding47 on 2016-08-09
Hi Jeremy,

I want to let you know where I stand with this and what I'm working on.  Please keep in mind I'm learning as I go, so I don't 100% understand what I'm saying here.  :) 

1.  While going through other threads, I was prompted to look at /etc/resolv.conf   I saw that nameserver was only set to 127.0.0.1.   So I edited it to include my xfinitys numbers.  I am getting error messages from gedit.  It seems to save it only until I reboot.  So I am working on fixing that. 

**_Question_**:  While I am doing this and adding the 2 other name servers, should I delete the line set to 127.0.0.1?

2.  I was also reading and following [https://help.ubuntu.com/community/WirelessTroubleshootingProcedure](https://help.ubuntu.com/community/WirelessTroubleshootingProcedure)
As part of Step 2, I was given a lot of output.  As I was browsing this, I saw that 
/etc/modprobe.d/iwlopt.conf

said that it was being ignored after "option".  So I reran that b/c typo, and now I can't find that statement, so that may have fixed my
typo, but still isn't connecting on wifi.  

3.  Just now while running that script again, I saw that Wlan said WEP encryption, so I am going to go on my router again and make sure I 
have the WPA encryption set up for wifi.  





**_Question_**:  Should I be trying to learn about the wpa-supplicant?

4.  I ran the wireless-info script again, here are the results, I haven't looked over them yet

```


########## wireless info START ##########

Report from: 09 Aug 2016 13:13 EDT -0400

Booted last: 09 Aug 2016 00:00 EDT -0400

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo 82579LM Gigabit Network Connection [17aa:21f3]
    Kernel driver in use: e1000e

03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2200 [8086:0891] (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2200 BGN [8086:4222]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b2ea Chicony Electronics Co., Ltd Integrated Camera [ThinkPad]
Bus 001 Device 003: ID 147e:2020 Upek TouchChip Fingerprint Coprocessor (WBF advanced mode)
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwldvm                233472  0
mac80211              737280  1 iwldvm
iwlwifi               200704  1 iwldvm
cfg80211              565248  3 iwlwifi,mac80211,iwldvm
wmi                    20480  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s25   Link encap:Ethernet  HWaddr <MAC 'enp0s25' [IF1]>  
          inet addr:10.0.0.16  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::6343:6dc7:a2b3:6ade/64 Scope:Link
          inet6 addr: 2601:18d:300:4c70:4fb5:fb7a:fbcc:de39/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:88653 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42299 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:129198624 (129.1 MB)  TX bytes:4100829 (4.1 MB)
          Interrupt:20 Memory:f2500000-f2520000 

wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF2]>  
          inet addr:10.0.0.10  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: 2601:18d:300:4c70:<IP6 'wlp3s0' [IF2]>/64 Scope:Global
          inet6 addr: fe80::<IP6 'wlp3s0' [IF2]>/64 Scope:Link
          inet6 addr: 2601:18d:300:4c70:f1e6:f20e:e40c:c147/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1731 errors:0 dropped:0 overruns:0 frame:0
          TX packets:159 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:258857 (258.8 KB)  TX bytes:24444 (24.4 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp0s25   no wireless extensions.

wlp3s0    IEEE 802.11bgn  ESSID:"HOME-E342"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: <MAC 'HOME-E342' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:28   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    100    0        0 enp0s25
0.0.0.0         10.0.0.1        0.0.0.0         UG    600    0        0 wlp3s0
10.0.0.0        0.0.0.0         255.255.255.0   U     100    0        0 enp0s25
10.0.0.0        0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp3s0

##### resolv.conf #######################

nameserver 127.0.0.1
search hsd1.ma.comcast.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root      2478     1  0 11:47 ?        00:00:09 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s25
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82579LM Gigabit Network Connection
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.13-3
GENERAL.HWADDR:                         <MAC 'enp0s25' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/enp0s25
GENERAL.IP-IFACE:                       enp0s25
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       30b4ac52-55f2-4770-9ceb-6756f6b65116
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   30b4ac52-55f2-4770-9ceb-6756f6b65116 | Wired connection 1
IP4.ADDRESS[1]:                         10.0.0.16/24
IP4.GATEWAY:                            10.0.0.1
IP4.DNS[1]:                             75.75.75.75
IP4.DNS[2]:                             75.75.76.76
IP4.DOMAIN[1]:                          hsd1.ma.comcast.net.
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        host_name = murph-ThinkPad-X230
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 10.0.0.1
DHCP4.OPTION[11]:                       expiry = 1471362443
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 10.0.0.1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 10.0.0.16
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       domain_name = hsd1.ma.comcast.net.
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       broadcast_address = 10.0.0.255
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       dhcp_lease_time = 604800
DHCP4.OPTION[24]:                       domain_name_servers = 75.75.75.75 75.75.76.76
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       network_number = 10.0.0.0
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 10.0.0.1
IP6.ADDRESS[1]:                         2601:18d:300:4c70:4fb5:fb7a:fbcc:de39/64
IP6.ADDRESS[2]:                         fe80::6343:6dc7:a2b3:6ade/64
IP6.GATEWAY:                            fe80::200:caff:fe11:2233
IP6.ROUTE[1]:                           dst = 2601:18d:300:4c70::/64, nh = ::, mt = 100
IP6.DNS[1]:                             2001:558:feed::1
IP6.DNS[2]:                             2001:558:feed::2
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2001:558:feed::1 2001:558:feed::2
DHCP6.OPTION[3]:                        dhcp6_preference = 0
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        dhcp6_server_id = 0:1:0:1:1f:2b:c6:45:0:0:ca:11:22:33
DHCP6.OPTION[7]:                        dhcp6_client_id = 0:4:97:b:42:2:91:b:da:a2:93:e5:d0:a8:9f:56:f1:46

GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Centrino Wireless-N 2200 (BGN)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-31-generic
GENERAL.FIRMWARE-VERSION:               18.168.6.1
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       wlp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     HOME-E342
GENERAL.CON-UUID:                       27a7f138-dd60-468d-9d72-2c37a2222ab3
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
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
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   27a7f138-dd60-468d-9d72-2c37a2222ab3 | HOME-E342
IP4.ADDRESS[1]:                         10.0.0.10/24
IP4.GATEWAY:                            10.0.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             75.75.75.75
IP4.DNS[2]:                             75.75.76.76
IP4.DOMAIN[1]:                          hsd1.ma.comcast.net.
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        host_name = murph-ThinkPad-X230
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 10.0.0.1
DHCP4.OPTION[11]:                       expiry = 1471362443
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 10.0.0.1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 10.0.0.10
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       domain_name = hsd1.ma.comcast.net.
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       broadcast_address = 10.0.0.255
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       dhcp_lease_time = 604800
DHCP4.OPTION[24]:                       domain_name_servers = 75.75.75.75 75.75.76.76
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       network_number = 10.0.0.0
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 10.0.0.1
IP6.ADDRESS[1]:                         2601:18d:300:4c70:<IP6 'wlp3s0' [IF2]>/64
IP6.ADDRESS[2]:                         2601:18d:300:4c70:f1e6:f20e:e40c:c147/64
IP6.ADDRESS[3]:                         fe80::<IP6 'wlp3s0' [IF2]>/64
IP6.GATEWAY:                            fe80::200:caff:fe11:2233

SSID       BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
HOME-E342  <MAC 'HOME-E342' [AC1]>  Infra  3     2422 MHz  54 Mbit/s  87      &#9602;&#9604;&#9606;&#9608;  WPA2      yes     * 

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

[[/etc/NetworkManager/system-connections/US_Guest]] (600 root)
[connection] id=US_Guest | type=wifi | permissions=user:murph:;
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=US_Guest
[ipv4] method=auto
[ipv6] method=dhcp

[[/etc/NetworkManager/system-connections/xfinitywifi]] (600 root)
[connection] id=xfinitywifi | type=wifi | autoconnect=false | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=xfinitywifi
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/HOME-E342]] (600 root)
[connection] id=HOME-E342 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=HOME-E342
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country US: DFS-FCC
    (2402 - 2472 @ 40), (N/A, 30), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A)
    (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
    (5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp0s25   no frequency information.

wlp3s0    11 channels in total; available frequencies :
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
          Current Frequency:2.422 GHz (Channel 3)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp0s25   Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.422 GHz (Channel 3)

wlp3s0    Scan completed :
          Cell 01 - Address: <MAC 'HOME-E342' [AC1]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"HOME-E342"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000926ef3ea6
                    Extra: Last beacon: 2089596ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwldvm]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     6A40B68AAA6792A5BDEA010
depends:        mac80211,iwlwifi,cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           force_cam:force continuously aware mode (no power saving at all) (bool)

[mac80211]
filename:       /lib/modules/4.4.0-31-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     651BF6CBF283F6F817B8F3A
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
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
filename:       /lib/modules/4.4.0-31-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
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
11n_disable: 8
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
swcrypto: 0
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

[/etc/modprobe.d/iwlopt.conf]
options iwlwifi 11n_disable=8

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

sleep 10
iwconfig wlp3s0 power off
exit 0

##### pm-utils ##########################

[/etc/pm/power.d/root-resume.service] (755 root)
[Unit]
Description=Turn of wlan power management
After=suspend.target
[Service]
Type=simple
ExecStartPre= /bin/sleep 10
ExecStart= /sbin/iwconfig wlp3s0 power off
[Install]
WantedBy=suspend.target

[/etc/pm/power.d/wireless] (755 root)
/sbin/iwconfig wlp3s0  power off

##### udev rules ########################

##### dmesg #############################

[   10.650205] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   10.650209] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   10.650211] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   10.650214] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 2200 BGN, REV=0x104
[   10.650321] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   10.692585] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   10.861845] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
[   23.524805] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   23.524947] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled (repeated 2 times)
[   23.532672] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[   23.778292] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled (repeated 2 times)
[   23.786028] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[   23.843080] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   23.845834] IPv6: ADDRCONF(NETDEV_UP): enp0s25: link is not ready (repeated 2 times)
[   24.707365] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   25.213123] wlp3s0: authenticate with <MAC 'HOME-E342' [AC1]>
[   25.216591] wlp3s0: send auth to <MAC 'HOME-E342' [AC1]> (try 1/3)
[   25.218459] wlp3s0: authenticated
[   25.219414] wlp3s0: associate with <MAC 'HOME-E342' [AC1]> (try 1/3)
[   25.235755] wlp3s0: RX AssocResp from <MAC 'HOME-E342' [AC1]> (capab=0x411 status=0 aid=1)
[   25.238474] wlp3s0: associated
[   25.238509] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[   26.929634] e1000e: enp0s25 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[   26.929670] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s25: link becomes ready

########## wireless info END ############

```

4.  A friend gave me the following page  [https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic](https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic)
but I find that most of that is over my head.  

_**Question**_:  Should I also focus on trying to understand any of that and putting it into play?


Finally, Thank you.  I am trying to keep this going and not just putting the problem in your hands to fix, but I appreciate the guidance.  My goal was to get the wifi set up for fall, but I realize that I'm learning in the meantime, and as long as there is a chance to make progress, I'll stick with it.  I don't want to go back to windows.

~ding

---

### Post by jeremy31 on 2016-08-09
If you want to add additional DNS to the connection use Network Manager, edit connection, IPv4 settings.

The wireless connection looks like it should work as it has an IP address and seems to have the same DNS as the wired.  With the ethernet unplugged can you 
```
ping -c3 8.8.8.8
``` or even
```
ping -c3 google.com
```

Another thing to try is ```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlopt.conf
```

This is somewhat baffling as Intel wireless usually work with Linux.  I actually have an Intel 2200 in my pile and I think I took it out of my Dell and replaced it with a 7260 with bluetooth just so I could play with bluetooth.  I just put my card in my Toshiba and booted it up and it connected with no issue, it doesn't have the exact same ID as yours but the source code shows them using the same settings
```
/* 2x00 Series */
	{IWL_PCI_DEVICE(0x0890, 0x4022, iwl2000_2bgn_cfg)},
	{IWL_PCI_DEVICE(0x0891, 0x4222, iwl2000_2bgn_cfg)},
```

If you look at the lspci results from your wireless script result you will see ```
03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2200 [8086:**0891**] (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2200 BGN [8086:**4222**]
    Kernel driver in use: iwlwifi
```

If you look at the numbers after 8086: they correspond to what is in the source code

The link from your friend has a lot of info that shouldn't be needed in this case and from what I see in the script results makes me think that if you unplug the ethernet the wireless should work

---

### Post by ding47 on 2016-08-10
Still no luck.  I'm really wondering at this point if it's something stupid, like it's not plugged in, lol.  Every other device in the house works fine.  And it does say that it is connecting to my wifi, I'm going to go search the cable company website.  

Oh - the dns numbers show up fine in Network Manager, but they do not stay in /etc/resolv.conf after I reboot.    Could that be causing a problem?

---

### Post by jeremy31 on 2016-08-10
I don't think they ever show in resolv.conf but will be in a file in /etc/NetworkManager/system-connections/{whatever your network name is}

The card is definitely plugged in and I don't see any errors that would indicate a hardware failure.  It might be that the router needs rebooted or BIOS on the computer needs to be reset to defaults

---

### Post by ding47 on 2016-08-10
Jeremy,

I called cable company.  they told me to unplug and reboot the laptop.  I said 'yeah, I've done that 1000 times in the past 4 weeks but okay.'  And now it works.  He swears he didn't do anything on his end to fix it, I am baffled.  

Thank you so much for your patience!  I wonder if it's that last modprobe thing up there that did it.  I'm going to mark this as resolved if it's on my end.  And again, thanks for sticking this out with me.  Now I'm going to start learning about the others things you can do with Linux and may I never have another wifi issue again!

~ding

---

