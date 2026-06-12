---
title: "Slow wifi with broadcom after ubuntu fresh install"
date: 2016-01-24
forum: Networking &amp; Wireless
---

### Post by juan_loo_kung on 2016-01-24
Hi! i have a broadcom 43142 i have already installed the correct driver which is bcmwl-kernel-source and still slow
also sorry for my bad english im from peru

---

### Post by Hadaka on 2016-01-24
Hi, please run and post the wireless-info.txt file this creates in your home directory.
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
thanks.

---

### Post by juan_loo_kung on 2016-01-24
hi thanks for the reply

```
########## wireless info START ##########

Report from: 24 Jan 2016 13:17 PET -0500

Booted last: 24 Jan 2016 00:00 PET -0500

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-25-generic #30-Ubuntu SMP Mon Jan 18 12:31:50 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    DeviceName: NAMI
    Subsystem: Hewlett-Packard Company Device [103c:804a]

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:80cc]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 004 Device 003: ID 05c8:0382 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 004 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0a5c:216d Broadcom Corp. 
Bus 003 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6365184  0
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
cfg80211              548864  1 wl
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF]>  
          inet addr:192.168.1.38  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2001:1388:2:d2c0:58fd:99ea:f212:d38b/64 Scope:Global
          inet6 addr: fd4b:c23f:5941:1:58fd:99ea:f212:d38b/64 Scope:Global
          inet6 addr: fd4b:c23f:5941:1:<IP6 'enp3s0' [IF]>/64 Scope:Global
          inet6 addr: fe80::<IP6 'enp3s0' [IF]>/64 Scope:Link
          inet6 addr: 2001:1388:2:d2c0:<IP6 'enp3s0' [IF]>/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1867 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2212 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:709802 (709.8 KB)  TX bytes:256605 (256.6 KB)

wlo1      Link encap:Ethernet  HWaddr <MAC 'wlo1' [IF]>  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2001:1388:2:d2c0:<IP6 'wlo1' [IF]>/64 Scope:Global
          inet6 addr: fd4b:c23f:5941:1:<IP6 'wlo1' [IF]>/64 Scope:Global
          inet6 addr: fe80::<IP6 'wlo1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27826 errors:0 dropped:0 overruns:0 frame:38252
          TX packets:22559 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22422529 (22.4 MB)  TX bytes:2965059 (2.9 MB)
          Interrupt:41 

##### iwconfig ##########################

enp3s0    no wireless extensions.

lo        no wireless extensions.

wlo1      IEEE 802.11abg  ESSID:"WLAN_5269"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'WLAN_5269' [AC1]>   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp3s0
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlo1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlo1
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp3s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlo1

##### resolv.conf #######################

nameserver 127.0.1.1
search home

##### network managers ##################

Installed:

    NetworkManager

Running:

root       624     1  0 12:31 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.5/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       enp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       b4e116b3-759a-49d3-85a0-3b224b2625da
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   b4e116b3-759a-49d3-85a0-3b224b2625da | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.38/24
IP4.GATEWAY:                            192.168.1.1
IP4.DNS[1]:                             200.48.225.130
IP4.DNS[2]:                             200.48.225.146
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 200.48.225.130 200.48.225.146
DHCP4.OPTION[5]:                        ip_address = 192.168.1.38
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        time_offset = 0
DHCP4.OPTION[10]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       routers = 192.168.1.1
DHCP4.OPTION[17]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       domain_name = home
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1453745730
DHCP4.OPTION[22]:                       host_name = LudwingVB-Notebook
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_wpad = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       requested_domain_search = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_ntp_servers = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
DHCP4.OPTION[32]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         2001:1388:2:d2c0:58fd:99ea:f212:d38b/64
IP6.ADDRESS[2]:                         fd4b:c23f:5941:1:58fd:99ea:f212:d38b/64
IP6.ADDRESS[3]:                         2001:1388:2:d2c0:<IP6 'enp3s0' [IF]>/64
IP6.ADDRESS[4]:                         fd4b:c23f:5941:1:<IP6 'enp3s0' [IF]>/64
IP6.ADDRESS[5]:                         fe80::<IP6 'enp3s0' [IF]>/64
IP6.GATEWAY:                            fe80::feb4:e6ff:fe7a:5269
IP6.DNS[1]:                             fd4b:c23f:5941:1:feb4:e6ff:fe7a:5269
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:82:97:a9:99:1e:db:be:97:78:8a:55:e:6e:a5:71:a7
DHCP6.OPTION[2]:                        dhcp6_name_servers = fd4b:c23f:5941:1:feb4:e6ff:fe7a:5269
DHCP6.OPTION[3]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[4]:                        vsio_unknown_3561 = 0:1:0:28:68:74:74:70:3a:2f:2f:32:30:30:2e:34:38:2e:32:32:39:2e:32:33:3a:37:30:30:33:2f:63:77:6d:70:57:65:62:2f:43:50:45:4d:67:74
DHCP6.OPTION[5]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[6]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[7]:                        dhcp6_domain_search = home.
DHCP6.OPTION[8]:                        dhcp6_server_id = 0:1:0:1:38:6d:43:80:fc:b4:e6:7a:52:69

GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM43142 802.11b/g/n
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.248 (r487574)
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlo1' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.4/0000:02:00.0/net/wlo1
GENERAL.IP-IFACE:                       wlo1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     WLAN_5269 1
GENERAL.CON-UUID:                       f33aa26d-0eec-4928-a9ea-e7d86bea0bef
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     65 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   f33aa26d-0eec-4928-a9ea-e7d86bea0bef | WLAN_5269 1
IP4.ADDRESS[1]:                         192.168.1.33/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             200.48.225.130
IP4.DNS[2]:                             200.48.225.146
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 200.48.225.130 200.48.225.146
DHCP4.OPTION[5]:                        ip_address = 192.168.1.33
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        time_offset = 0
DHCP4.OPTION[10]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       routers = 192.168.1.1
DHCP4.OPTION[17]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       domain_name = home
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1453743080
DHCP4.OPTION[22]:                       host_name = LudwingVB-Notebook
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_wpad = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       requested_domain_search = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_ntp_servers = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
DHCP4.OPTION[32]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         2001:1388:2:d2c0:<IP6 'wlo1' [IF]>/64
IP6.ADDRESS[2]:                         fd4b:c23f:5941:1:<IP6 'wlo1' [IF]>/64
IP6.ADDRESS[3]:                         fe80::<IP6 'wlo1' [IF]>/64
IP6.GATEWAY:                            fe80::feb4:e6ff:fe7a:5269
IP6.ROUTE[1]:                           dst = 2001:1388:2:d2c0::/64, nh = ::, mt = 600
IP6.ROUTE[2]:                           dst = fd4b:c23f:5941:1::/64, nh = ::, mt = 600
IP6.DNS[1]:                             fd4b:c23f:5941:1:feb4:e6ff:fe7a:5269
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:82:97:a9:99:1e:db:be:97:78:8a:55:e:6e:a5:71:a7
DHCP6.OPTION[2]:                        dhcp6_name_servers = fd4b:c23f:5941:1:feb4:e6ff:fe7a:5269
DHCP6.OPTION[3]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[4]:                        vsio_unknown_3561 = 0:1:0:28:68:74:74:70:3a:2f:2f:32:30:30:2e:34:38:2e:32:32:39:2e:32:33:3a:37:30:30:33:2f:63:77:6d:70:57:65:62:2f:43:50:45:4d:67:74
DHCP6.OPTION[5]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[6]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[7]:                        dhcp6_domain_search = home.
DHCP6.OPTION[8]:                        dhcp6_server_id = 0:1:0:1:38:6d:43:80:fc:b4:e6:7a:52:69

SSID       BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
WLAN_5269  <MAC 'WLAN_5269' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  71      &#9602;&#9604;&#9606;_  WPA2      yes     * 
DENISS     <MAC 'DENISS' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA1      no        

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

Sorry, try again.
[[/etc/NetworkManager/system-connections/WLAN_5269 1]] (600 root)
[connection] id=WLAN_5269 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlo1' [IF]> | mac-address-blacklist= | ssid=WLAN_5269
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WLAN_5269]] (600 root)
[connection] id=WLAN_5269 | type=wifi | permissions=user:guest-rERvVH:;
[wifi] mac-address=<MAC 'wlo1' [IF]> | mac-address-blacklist= | ssid=WLAN_5269
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Lima (based on set time zone)

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

enp3s0    no frequency information.

lo        no frequency information.

wlo1      32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
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
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

enp3s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.462 GHz (Channel 11)

wlo1      Scan completed :
          Cell 01 - Address: <MAC 'WLAN_5269' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"WLAN_5269"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'DENISS' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"DENISS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 14328ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[wl]
filename:       /lib/modules/4.2.0-25-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     3F8570547EE3A2BA3D5D734
depends:        cfg80211
vermagic:       4.2.0-25-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/4.2.0-25-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-25-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        A4:10:30:FB:DF:1D:C9:62:B4:BB:7D:16:44:C3:33:7E:C4:16:DB:86
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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
blacklist brcmsmac
blacklist bcma
blacklist acer_wmi

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/broadcom-sta-common.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb
install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS

[/etc/modprobe.d/broadcom-sta-dkms.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb

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

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[    9.812054] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[    9.812066] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[   10.140188] wlan0: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[   10.183583] wl 0000:02:00.0 wlo1: renamed from wlan0
[   20.205750] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   20.465938] r8169 0000:03:00.0 enp3s0: link down
[   20.466017] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   20.470682] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 2668.035179] r8169 0000:03:00.0 enp3s0: link up
[ 2668.035212] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[ 2809.824679] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############
```

---

### Post by Hadaka on 2016-01-24
Hi, please open a terminal and do..
```
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&IUS/' /etc/default/crda
```
Then please access your router configuration and change the
setting TKIP to WPA2 AES
thanks.

---

### Post by juan_loo_kung on 2016-01-24
the same thing

---

### Post by Hadaka on 2016-01-24
Please re run the wireless script and post
a new wireless-info.txt file.
thanks

---

### Post by juan_loo_kung on 2016-01-24
should i run the script when connected to internet or when the problem happens

---

### Post by Hadaka on 2016-01-24
Both would be nice, but either way will be fine.
thanks

---

### Post by juan_loo_kung on 2016-01-25
########## wireless info START ##########

Report from: 24 Jan 2016 13:17 PET -0500

Booted last: 24 Jan 2016 00:00 PET -0500

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-25-generic #30-Ubuntu SMP Mon Jan 18 12:31:50 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    DeviceName: NAMI
    Subsystem: Hewlett-Packard Company Device [103c:804a]

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136]  (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:80cc]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 004 Device 003: ID 05c8:0382 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 004 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0a5c:216d Broadcom Corp. 
Bus 003 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6365184  0
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
cfg80211              548864  1 wl
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF]>  
          inet addr:192.168.1.38  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2001:1388:2:d2c0:58fd:99ea:f212:d38b/64 Scope:Global
          inet6 addr: fd4b:c23f:5941:1:58fd:99ea:f212:d38b/64 Scope:Global
          inet6 addr: fd4b:c23f:5941:1:<IP6 'enp3s0' [IF]>/64 Scope:Global
          inet6 addr: fe80::<IP6 'enp3s0' [IF]>/64 Scope:Link
          inet6 addr: 2001:1388:2:d2c0:<IP6 'enp3s0' [IF]>/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1867 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2212 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:709802 (709.8 KB)  TX bytes:256605 (256.6 KB)

wlo1      Link encap:Ethernet  HWaddr <MAC 'wlo1' [IF]>  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2001:1388:2:d2c0:<IP6 'wlo1' [IF]>/64 Scope:Global
          inet6 addr: fd4b:c23f:5941:1:<IP6 'wlo1' [IF]>/64 Scope:Global
          inet6 addr: fe80::<IP6 'wlo1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27826 errors:0 dropped:0 overruns:0 frame:38252
          TX packets:22559 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22422529 (22.4 MB)  TX bytes:2965059 (2.9 MB)
          Interrupt:41 

##### iwconfig ##########################

enp3s0    no wireless extensions.

lo        no wireless extensions.

wlo1      IEEE 802.11abg  ESSID:"WLAN_5269"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'WLAN_5269' [AC1]>   
          Retry short limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
          Power Management:eek:ff
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp3s0
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlo1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlo1
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp3s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlo1

##### resolv.conf #######################

nameserver 127.0.1.1
search home

##### network managers ##################

Installed:

    NetworkManager

Running:

root       624     1  0 12:31 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.5/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       enp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       b4e116b3-759a-49d3-85a0-3b224b2625da
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   b4e116b3-759a-49d3-85a0-3b224b2625da | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.38/24
IP4.GATEWAY:                            192.168.1.1
IP4.DNS[1]:                             200.48.225.130
IP4.DNS[2]:                             200.48.225.146
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 200.48.225.130 200.48.225.146
DHCP4.OPTION[5]:                        ip_address = 192.168.1.38
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        time_offset = 0
DHCP4.OPTION[10]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       routers = 192.168.1.1
DHCP4.OPTION[17]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       domain_name = home
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1453745730
DHCP4.OPTION[22]:                       host_name = LudwingVB-Notebook
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_wpad = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       requested_domain_search = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_ntp_servers = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
DHCP4.OPTION[32]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         2001:1388:2:d2c0:58fd:99ea:f212:d38b/64
IP6.ADDRESS[2]:                         fd4b:c23f:5941:1:58fd:99ea:f212:d38b/64
IP6.ADDRESS[3]:                         2001:1388:2:d2c0:<IP6 'enp3s0' [IF]>/64
IP6.ADDRESS[4]:                         fd4b:c23f:5941:1:<IP6 'enp3s0' [IF]>/64
IP6.ADDRESS[5]:                         fe80::<IP6 'enp3s0' [IF]>/64
IP6.GATEWAY:                            fe80::feb4:e6ff:fe7a:5269
IP6.DNS[1]:                             fd4b:c23f:5941:1:feb4:e6ff:fe7a:5269
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:82:97:a9:99:1e:db:be:97:78:8a:55:e:6e:a5:71:a7
DHCP6.OPTION[2]:                        dhcp6_name_servers = fd4b:c23f:5941:1:feb4:e6ff:fe7a:5269
DHCP6.OPTION[3]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[4]:                        vsio_unknown_3561 =  0:1:0:28:68:74:74:70:3a:2f:2f:32:30:30:2e:34:38:2e:32:32:39:2e:32:33:3a:37:30:30:33:2f:63:77:6d:70:57:65:62:2f:43:50:45:4d:67:74
DHCP6.OPTION[5]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[6]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[7]:                        dhcp6_domain_search = home.
DHCP6.OPTION[8]:                        dhcp6_server_id = 0:1:0:1:38:6d:43:80:fc:b4:e6:7a:52:69

GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM43142 802.11b/g/n
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.248 (r487574)
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlo1' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.4/0000:02:00.0/net/wlo1
GENERAL.IP-IFACE:                       wlo1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     WLAN_5269 1
GENERAL.CON-UUID:                       f33aa26d-0eec-4928-a9ea-e7d86bea0bef
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     65 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   f33aa26d-0eec-4928-a9ea-e7d86bea0bef | WLAN_5269 1
IP4.ADDRESS[1]:                         192.168.1.33/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             200.48.225.130
IP4.DNS[2]:                             200.48.225.146
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 200.48.225.130 200.48.225.146
DHCP4.OPTION[5]:                        ip_address = 192.168.1.33
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        time_offset = 0
DHCP4.OPTION[10]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       routers = 192.168.1.1
DHCP4.OPTION[17]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       domain_name = home
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1453743080
DHCP4.OPTION[22]:                       host_name = LudwingVB-Notebook
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_wpad = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       requested_domain_search = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_ntp_servers = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
DHCP4.OPTION[32]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         2001:1388:2:d2c0:<IP6 'wlo1' [IF]>/64
IP6.ADDRESS[2]:                         fd4b:c23f:5941:1:<IP6 'wlo1' [IF]>/64
IP6.ADDRESS[3]:                         fe80::<IP6 'wlo1' [IF]>/64
IP6.GATEWAY:                            fe80::feb4:e6ff:fe7a:5269
IP6.ROUTE[1]:                           dst = 2001:1388:2:d2c0::/64, nh = ::, mt = 600
IP6.ROUTE[2]:                           dst = fd4b:c23f:5941:1::/64, nh = ::, mt = 600
IP6.DNS[1]:                             fd4b:c23f:5941:1:feb4:e6ff:fe7a:5269
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:82:97:a9:99:1e:db:be:97:78:8a:55:e:6e:a5:71:a7
DHCP6.OPTION[2]:                        dhcp6_name_servers = fd4b:c23f:5941:1:feb4:e6ff:fe7a:5269
DHCP6.OPTION[3]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[4]:                        vsio_unknown_3561 =  0:1:0:28:68:74:74:70:3a:2f:2f:32:30:30:2e:34:38:2e:32:32:39:2e:32:33:3a:37:30:30:33:2f:63:77:6d:70:57:65:62:2f:43:50:45:4d:67:74
DHCP6.OPTION[5]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[6]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[7]:                        dhcp6_domain_search = home.
DHCP6.OPTION[8]:                        dhcp6_server_id = 0:1:0:1:38:6d:43:80:fc:b4:e6:7a:52:69

SSID       BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
WLAN_5269  <MAC 'WLAN_5269' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  71      &#9602;&#9604;&#9606;_  WPA2      yes     * 
DENISS     <MAC 'DENISS' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA1      no        

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

Sorry, try again.
[[/etc/NetworkManager/system-connections/WLAN_5269 1]] (600 root)
[connection] id=WLAN_5269 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlo1' [IF]> | mac-address-blacklist= | ssid=WLAN_5269
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WLAN_5269]] (600 root)
[connection] id=WLAN_5269 | type=wifi | permissions=user:guest-rERvVH:;
[wifi] mac-address=<MAC 'wlo1' [IF]> | mac-address-blacklist= | ssid=WLAN_5269
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Lima (based on set time zone)

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

enp3s0    no frequency information.

lo        no frequency information.

wlo1      32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
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
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

enp3s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.462 GHz (Channel 11)

wlo1      Scan completed :
          Cell 01 - Address: <MAC 'WLAN_5269' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:eek:n
                    ESSID:"WLAN_5269"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'DENISS' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:eek:n
                    ESSID:"DENISS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 14328ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[wl]
filename:       /lib/modules/4.2.0-25-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     3F8570547EE3A2BA3D5D734
depends:        cfg80211
vermagic:       4.2.0-25-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/4.2.0-25-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-25-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        A4:10:30:FB:grin:F:1D:C9:62:B4:BB:7D:16:44:C3:33:7E:C4:16:grin:B:86
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:grin:isable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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
blacklist brcmsmac
blacklist bcma
blacklist acer_wmi

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/broadcom-sta-common.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb
install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS

[/etc/modprobe.d/broadcom-sta-dkms.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb

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

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[    9.812054] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[    9.812066] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[   10.140188] wlan0: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[   10.183583] wl 0000:02:00.0 wlo1: renamed from wlan0
[   20.205750] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   20.465938] r8169 0000:03:00.0 enp3s0: link down
[   20.466017] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   20.470682] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 2668.035179] r8169 0000:03:00.0 enp3s0: link up
[ 2668.035212] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[ 2809.824679] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############



when working

---

### Post by juan_loo_kung on 2016-01-25
```
########## wireless info START ##########

Report from: 24 Jan 2016 13:17 PET -0500

Booted last: 24 Jan 2016 00:00 PET -0500

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-25-generic #30-Ubuntu SMP Mon Jan 18 12:31:50 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    DeviceName: NAMI
    Subsystem: Hewlett-Packard Company Device [103c:804a]

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.   RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136]   (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:80cc]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 004 Device 003: ID 05c8:0382 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 004 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0a5c:216d Broadcom Corp. 
Bus 003 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6365184  0
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
cfg80211              548864  1 wl
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF]>  
          inet addr:192.168.1.38  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2001:1388:2:d2c0:58fd:99ea:f212:d38b/64 Scope:Global
          inet6 addr: fd4b:c23f:5941:1:58fd:99ea:f212:d38b/64 Scope:Global
          inet6 addr: fd4b:c23f:5941:1:<IP6 'enp3s0' [IF]>/64 Scope:Global
          inet6 addr: fe80::<IP6 'enp3s0' [IF]>/64 Scope:Link
          inet6 addr: 2001:1388:2:d2c0:<IP6 'enp3s0' [IF]>/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1867 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2212 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:709802 (709.8 KB)  TX bytes:256605 (256.6 KB)

wlo1      Link encap:Ethernet  HWaddr <MAC 'wlo1' [IF]>  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2001:1388:2:d2c0:<IP6 'wlo1' [IF]>/64 Scope:Global
          inet6 addr: fd4b:c23f:5941:1:<IP6 'wlo1' [IF]>/64 Scope:Global
          inet6 addr: fe80::<IP6 'wlo1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27826 errors:0 dropped:0 overruns:0 frame:38252
          TX packets:22559 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22422529 (22.4 MB)  TX bytes:2965059 (2.9 MB)
          Interrupt:41 

##### iwconfig ##########################

enp3s0    no wireless extensions.

lo        no wireless extensions.

wlo1      IEEE 802.11abg  ESSID:"WLAN_5269"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'WLAN_5269' [AC1]>   
          Retry short limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
          Power Management:eek:ff
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp3s0
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlo1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlo1
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp3s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlo1

##### resolv.conf #######################

nameserver 127.0.1.1
search home

##### network managers ##################

Installed:

    NetworkManager

Running:

root       624     1  0 12:31 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.5/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       enp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       b4e116b3-759a-49d3-85a0-3b224b2625da
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   b4e116b3-759a-49d3-85a0-3b224b2625da | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.38/24
IP4.GATEWAY:                            192.168.1.1
IP4.DNS[1]:                             200.48.225.130
IP4.DNS[2]:                             200.48.225.146
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 200.48.225.130 200.48.225.146
DHCP4.OPTION[5]:                        ip_address = 192.168.1.38
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        time_offset = 0
DHCP4.OPTION[10]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       routers = 192.168.1.1
DHCP4.OPTION[17]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       domain_name = home
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1453745730
DHCP4.OPTION[22]:                       host_name = LudwingVB-Notebook
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_wpad = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       requested_domain_search = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_ntp_servers = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
DHCP4.OPTION[32]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         2001:1388:2:d2c0:58fd:99ea:f212:d38b/64
IP6.ADDRESS[2]:                         fd4b:c23f:5941:1:58fd:99ea:f212:d38b/64
IP6.ADDRESS[3]:                         2001:1388:2:d2c0:<IP6 'enp3s0' [IF]>/64
IP6.ADDRESS[4]:                         fd4b:c23f:5941:1:<IP6 'enp3s0' [IF]>/64
IP6.ADDRESS[5]:                         fe80::<IP6 'enp3s0' [IF]>/64
IP6.GATEWAY:                            fe80::feb4:e6ff:fe7a:5269
IP6.DNS[1]:                             fd4b:c23f:5941:1:feb4:e6ff:fe7a:5269
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:82:97:a9:99:1e:db:be:97:78:8a:55:e:6e:a5:71:a7
DHCP6.OPTION[2]:                        dhcp6_name_servers = fd4b:c23f:5941:1:feb4:e6ff:fe7a:5269
DHCP6.OPTION[3]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[4]:                        vsio_unknown_3561 =   0:1:0:28:68:74:74:70:3a:2f:2f:32:30:30:2e:34:38:2e:32:32:39:2e:32:33:3a:37:30:30:33:2f:63:77:6d:70:57:65:62:2f:43:50:45:4d:67:74
DHCP6.OPTION[5]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[6]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[7]:                        dhcp6_domain_search = home.
DHCP6.OPTION[8]:                        dhcp6_server_id = 0:1:0:1:38:6d:43:80:fc:b4:e6:7a:52:69

GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM43142 802.11b/g/n
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.248 (r487574)
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlo1' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.4/0000:02:00.0/net/wlo1
GENERAL.IP-IFACE:                       wlo1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     WLAN_5269 1
GENERAL.CON-UUID:                       f33aa26d-0eec-4928-a9ea-e7d86bea0bef
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     65 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   f33aa26d-0eec-4928-a9ea-e7d86bea0bef | WLAN_5269 1
IP4.ADDRESS[1]:                         192.168.1.33/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             200.48.225.130
IP4.DNS[2]:                             200.48.225.146
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 200.48.225.130 200.48.225.146
DHCP4.OPTION[5]:                        ip_address = 192.168.1.33
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        time_offset = 0
DHCP4.OPTION[10]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       routers = 192.168.1.1
DHCP4.OPTION[17]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       domain_name = home
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1453743080
DHCP4.OPTION[22]:                       host_name = LudwingVB-Notebook
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_wpad = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       requested_domain_search = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_ntp_servers = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
DHCP4.OPTION[32]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         2001:1388:2:d2c0:<IP6 'wlo1' [IF]>/64
IP6.ADDRESS[2]:                         fd4b:c23f:5941:1:<IP6 'wlo1' [IF]>/64
IP6.ADDRESS[3]:                         fe80::<IP6 'wlo1' [IF]>/64
IP6.GATEWAY:                            fe80::feb4:e6ff:fe7a:5269
IP6.ROUTE[1]:                           dst = 2001:1388:2:d2c0::/64, nh = ::, mt = 600
IP6.ROUTE[2]:                           dst = fd4b:c23f:5941:1::/64, nh = ::, mt = 600
IP6.DNS[1]:                             fd4b:c23f:5941:1:feb4:e6ff:fe7a:5269
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:82:97:a9:99:1e:db:be:97:78:8a:55:e:6e:a5:71:a7
DHCP6.OPTION[2]:                        dhcp6_name_servers = fd4b:c23f:5941:1:feb4:e6ff:fe7a:5269
DHCP6.OPTION[3]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[4]:                        vsio_unknown_3561 =   0:1:0:28:68:74:74:70:3a:2f:2f:32:30:30:2e:34:38:2e:32:32:39:2e:32:33:3a:37:30:30:33:2f:63:77:6d:70:57:65:62:2f:43:50:45:4d:67:74
DHCP6.OPTION[5]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[6]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[7]:                        dhcp6_domain_search = home.
DHCP6.OPTION[8]:                        dhcp6_server_id = 0:1:0:1:38:6d:43:80:fc:b4:e6:7a:52:69

SSID       BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
WLAN_5269  <MAC 'WLAN_5269' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  71      &#9602;&#9604;&#9606;_  WPA2      yes     * 
DENISS     <MAC 'DENISS' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA1      no        

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

Sorry, try again.
[[/etc/NetworkManager/system-connections/WLAN_5269 1]] (600 root)
[connection] id=WLAN_5269 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlo1' [IF]> | mac-address-blacklist= | ssid=WLAN_5269
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WLAN_5269]] (600 root)
[connection] id=WLAN_5269 | type=wifi | permissions=user:guest-rERvVH:;
[wifi] mac-address=<MAC 'wlo1' [IF]> | mac-address-blacklist= | ssid=WLAN_5269
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Lima (based on set time zone)

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

enp3s0    no frequency information.

lo        no frequency information.

wlo1      32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
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
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

enp3s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.462 GHz (Channel 11)

wlo1      Scan completed :
          Cell 01 - Address: <MAC 'WLAN_5269' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:eek:n
                    ESSID:"WLAN_5269"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'DENISS' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:eek:n
                    ESSID:"DENISS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 14328ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[wl]
filename:       /lib/modules/4.2.0-25-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     3F8570547EE3A2BA3D5D734
depends:        cfg80211
vermagic:       4.2.0-25-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/4.2.0-25-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-25-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        A4:10:30:FB:grin:F:1D:C9:62:B4:BB:7D:16:44:C3:33:7E:C4:16:grin:B:86
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:grin:isable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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
blacklist brcmsmac
blacklist bcma
blacklist acer_wmi

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/broadcom-sta-common.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb
install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS

[/etc/modprobe.d/broadcom-sta-dkms.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb

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

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[    9.812054] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[    9.812066] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[   10.140188] wlan0: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[   10.183583] wl 0000:02:00.0 wlo1: renamed from wlan0
[   20.205750] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   20.465938] r8169 0000:03:00.0 enp3s0: link down
[   20.466017] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   20.470682] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 2668.035179] r8169 0000:03:00.0 enp3s0: link up
[ 2668.035212] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[ 2809.824679] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############

```
when not working

---

### Post by Hadaka on 2016-01-25
Hi, please open a Terminal..ctrl/alt/t.. then COPY and paste
one line at a time. it is crucial these are accurate so please
copy and paste.
```
sudo iw reg set PE
sudo sed -i '/^REG*/ d' /etc/default/crda
echo "REGDOMAIN=PE" | sudo tee -a /etc/default/crda
```
Then as suggested in my last post..TKIP is known to cause drops
and disconnects, please access your router configuration and remove
the TKIP  setting and select WPA2 instead.
then *While connected with a wired connection please do.
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source
```
and finally please post the output of,
```
cat /etc/default/crda
```
thanks.

---

### Post by juan_loo_kung on 2016-01-25
```
# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.

REGDOMAIN=PE
```

this is the output

---

### Post by Hadaka on 2016-01-25
Thanks, ok lets do this. From a working wired connection -ethernet -
please COPY and paste.
```
sudo sed -i 's/install/#install/g' /etc/modprobe.d/broadcom-sta-common.conf
```
then do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe -rf wl
sudo modprobe -vv wl
```
then do.
```
echo wl | sudo tee -a /etc/modules
```
boot
disconnect wired connection and test wireless
thanks.

---

### Post by juan_loo_kung on 2016-01-26
hi it worked for almost an hour and a half but now its the same :(

---

### Post by Hadaka on 2016-01-26
Hi, sounds like we are making progress, please run the wireless
report yet once again .
thanks.

---

### Post by juan_loo_kung on 2016-01-26
hii 

########## wireless info START ##########

Report from: 26 Jan 2016 20:08 PET -0500

Booted last: 26 Jan 2016 00:00 PET -0500

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-25-generic #30-Ubuntu SMP Mon Jan 18 12:31:50 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################


02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    DeviceName: NAMI
    Subsystem: Hewlett-Packard Company Device [103c:804a]

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:80cc]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 004 Device 003: ID 05c8:0382 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 004 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0a5c:216d Broadcom Corp. 
Bus 003 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################


##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
wl                   6365184  0
cfg80211              548864  1 wl
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0    Link encap:Ethernet  HWaddr 58:20:b1:7a:60:98  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:12868 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8315 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18326898 (18.3 MB)  TX bytes:549674 (549.6 KB)

wlo1      Link encap:Ethernet  HWaddr d8:5d:e2:ab:a0:87  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2001:1388:3:1bd2:da5d:e2ff:feab:a087/64 Scope:Global
          inet6 addr: fd4b:c23f:5941:1:38b0:7c2a:cc88:9b0c/64 Scope:Global
          inet6 addr: fd4b:c23f:5941:1:da5d:e2ff:feab:a087/64 Scope:Global
          inet6 addr: fe80::da5d:e2ff:feab:a087/64 Scope:Link
          inet6 addr: 2001:1388:3:1bd2:38b0:7c2a:cc88:9b0c/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:981216 errors:0 dropped:0 overruns:0 frame:127493
          TX packets:643528 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1265414849 (1.2 GB)  TX bytes:67414071 (67.4 MB)
          Interrupt:34 

##### iwconfig ##########################

enp3s0    no wireless extensions.

lo        no wireless extensions.

wlo1      IEEE 802.11abg  ESSID:"FLKB"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: FC:B4:E6:7A:52:6B   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlo1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlo1
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlo1

##### resolv.conf #######################

nameserver 127.0.1.1
search home

##### network managers ##################

Installed:

    NetworkManager

Running:

root       659     1  0 15:35 ?        00:00:08 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM43142 802.11b/g/n
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.248 (r487574)
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         D8:5D:E2:AB:A0:87
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.4/0000:02:00.0/net/wlo1
GENERAL.IP-IFACE:                       wlo1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     FLKB
GENERAL.CON-UUID:                       6e8b1fe8-8a23-47a7-a38f-3210a99af1f0
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/4
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     52 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
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
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   6e8b1fe8-8a23-47a7-a38f-3210a99af1f0 | FLKB
IP4.ADDRESS[1]:                         192.168.1.33/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             200.48.225.130
IP4.DNS[2]:                             200.48.225.146
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 200.48.225.130 200.48.225.146
DHCP4.OPTION[5]:                        ip_address = 192.168.1.33
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        time_offset = 0
DHCP4.OPTION[10]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       routers = 192.168.1.1
DHCP4.OPTION[17]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       domain_name = home
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1453943282
DHCP4.OPTION[22]:                       host_name = LudwingVB-Notebook
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_wpad = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       requested_domain_search = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_ntp_servers = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
DHCP4.OPTION[32]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         2001:1388:3:1bd2:38b0:7c2a:cc88:9b0c/64
IP6.ADDRESS[2]:                         fd4b:c23f:5941:1:38b0:7c2a:cc88:9b0c/64
IP6.ADDRESS[3]:                         2001:1388:3:1bd2:da5d:e2ff:feab:a087/64
IP6.ADDRESS[4]:                         fd4b:c23f:5941:1:da5d:e2ff:feab:a087/64
IP6.ADDRESS[5]:                         fe80::da5d:e2ff:feab:a087/64
IP6.GATEWAY:                            fe80::feb4:e6ff:fe7a:5269
IP6.ROUTE[1]:                           dst = 2001:1388:3:1bd2::/64, nh = ::, mt = 600
IP6.ROUTE[2]:                           dst = fd4b:c23f:5941:1::/64, nh = ::, mt = 600
IP6.DNS[1]:                             fd4b:c23f:5941:1:feb4:e6ff:fe7a:5269
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:82:97:a9:99:1e:db:be:97:78:8a:55:e:6e:a5:71:a7
DHCP6.OPTION[2]:                        dhcp6_name_servers = fd4b:c23f:5941:1:feb4:e6ff:fe7a:5269
DHCP6.OPTION[3]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[4]:                        vsio_unknown_3561 = 0:1:0:28:68:74:74:70:3a:2f:2f:32:30:30:2e:34:38:2e:32:32:39:2e:32:33:3a:37:30:30:33:2f:63:77:6d:70:57:65:62:2f:43:50:45:4d:67:74
DHCP6.OPTION[5]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[6]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[7]:                        dhcp6_domain_search = home.
DHCP6.OPTION[8]:                        dhcp6_server_id = 0:1:0:1:38:6d:43:80:fc:b4:e6:7a:52:69

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         58:20:B1:7A:60:98
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         40 (Carrier/link changed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.5/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID       BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
REINALDO1  3C:75:4A:A5:E3:D9  Infra  11    2462 MHz  54 Mbit/s  35      &#9602;&#9604;__  WEP        no        
gatanina   CC:03:FA:47:40:9B  Infra  1     2412 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA1       no        
WiFi EIB   00:02:6F:63:F2:8C  Infra  1     2412 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA1       no        
DENISS     EC:0E:C4:77:1F:59  Infra  1     2412 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA1       no        
ERNESTO    F0:97:00:FE:CE:F1  Infra  6     2437 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA1       no        
FLKB       FC:B4:E6:7A:52:6B  Infra  6     2437 MHz  54 Mbit/s  58      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     * 

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

here is the output
also there is something weird now instead of being slow it disconetcs but the top of the screen says "conected" 
also when i am disconected i cant run the wireless report
pd: now the problem happens less times

---

### Post by Hadaka on 2016-01-26
You were connected to a different AP ssid = FLKB
before you were connect to ssid = WLAN_5269
The problem seems to now be in how you have your access points configures.
I suggest you configure them like the attached for IPv4 and IPv6.
[ATTACH=CONFIG]266975[/ATTACH][ATTACH=CONFIG]266974[/ATTACH]
and also access your router settings and remove the TKIP
and replace it with WPA2.
Beyond that, I am out of ideas and have no further suggestions.
good luck.

---

### Post by juan_loo_kung on 2016-01-27
Hi do you think a usb wifi adapter would solve this problem?

---

