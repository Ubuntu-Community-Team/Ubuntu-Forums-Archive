---
title: "WiFi adapter card not working"
date: 2018-05-21
forum: Networking &amp; Wireless
---

### Post by jcautry on 2018-05-21
Hi, I just put Ubuntu 18.04 on my desktop today, but my WiFi card is not working as is. It shows up with ```
lsusb
``` as ```
 Bus 005 Device 005: ID 13b1:003f Linksys WUSB6300 802.11a/b/g/n/ac Wireless Adapter [Realtek RTL8812AU] 
```.

The output from
```
iwconfig
```
is
```

enp6s0    no wireless extensions.

lo        no wireless extensions.

```

Thanks,
any help would be greatly appreciated.

---

### Post by howefield on 2018-05-21
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by jeremy31 on 2018-05-21
In terminal do ```
sudo apt-get update && sudo apt install rtl8812au-dkms
```
Reboot

The do ```
sudo -H gedit /usr/src/rtl8812au-4.3.8.12175.20140902+dfsg/dkms.conf
```
And change line 4 from ```
MAKE="'make' all"
```
to
```
MAKE="'make' all KVER=${kernelver}"
```
Then it should work after kernel updates

---

### Post by jcautry on 2018-05-21
Fantastic, thank you much. The card is up, but when I try to connect, I get the notification 'activation of network connection failed.' Any luck with this?

---

### Post by jeremy31 on 2018-05-21
See the wireless script link in my signature and post results

---

### Post by jcautry on 2018-05-21
Results from pastebin

```
########## wireless info START ##########

Report from: 21 May 2018 13:16 PDT -0700

Booted last: 21 May 2018 00:00 PDT -0700

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 18.04 LTS
Release:	18.04
Codename:	bionic

##### kernel ############################

Linux 4.15.0-20-generic #21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

06:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
	Subsystem: Gigabyte Technology Co., Ltd AR8161 Gigabit Ethernet [1458:e000]
	Kernel driver in use: alx

##### lsusb #############################

Bus 002 Device 004: ID 057e:0337 Nintendo Co., Ltd 
Bus 002 Device 003: ID 046d:0a5b Logitech, Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 005: ID 13b1:003f Linksys WUSB6300 802.11a/b/g/n/ac Wireless Adapter [Realtek RTL8812AU]
Bus 005 Device 004: ID 0738:1713 Mad Catz, Inc. 
Bus 005 Device 003: ID 0f39:1084 TG3 Electronics 
Bus 005 Device 002: ID 2109:0811 VIA Labs, Inc. Hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

8812au               1298432  0
cfg80211              622592  1 8812au
mxm_wmi                16384  0
wmi                    24576  1 mxm_wmi

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

enp6s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.137.135  netmask 255.255.255.0  broadcast 192.168.137.255
        inet6 fe80::f26b:9b59:4481:8bf9  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 8129  bytes 5137753 (5.1 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 6540  bytes 1163166 (1.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 18  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 2380  bytes 188568 (188.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2380  bytes 188568 (188.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlxc8d719be6cf9: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 111  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

enp6s0    no wireless extensions.

lo        no wireless extensions.

wlxc8d719be6cf9  unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=5.765 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.137.1   0.0.0.0         UG    100    0        0 enp6s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp6s0
192.168.137.0   0.0.0.0         255.255.255.0   U     100    0        0 enp6s0

##### resolv.conf #######################

nameserver 127.0.0.53
search mshome.net

##### network managers ##################

Installed:

	NetworkManager

Running:

root      1043     1  0 13:05 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp6s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR8161 Gigabit Ethernet
GENERAL.DRIVER:                         alx
GENERAL.DRIVER-VERSION:                 --
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.6/0000:06:00.0/net/enp6s0
GENERAL.IP-IFACE:                       enp6s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       04fb7e29-6218-3483-b945-23fe647a0f82
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/5
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.137.135/24
IP4.GATEWAY:                            192.168.137.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.137.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.137.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.137.1
IP4.DOMAIN[1]:                          mshome.net
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.137.1
DHCP4.OPTION[5]:                        ip_address = 192.168.137.135
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.137.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.137.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 453600
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       netbios_node_type = 4
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 300
DHCP4.OPTION[17]:                       routers = 192.168.137.1
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       domain_name = mshome.net
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1527538434
DHCP4.OPTION[22]:                       requested_wpad = 1
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.137.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 0.0.0.0
DHCP4.OPTION[30]:                       dhcp_lease_time = 604800
DHCP4.OPTION[31]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         fe80::f26b:9b59:4481:8bf9/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   04fb7e29-6218-3483-b945-23fe647a0f82 | Wired connection 1

GENERAL.DEVICE:                         wlxc8d719be6cf9
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Linksys
GENERAL.PRODUCT:                        WUSB6300
GENERAL.DRIVER:                         rtl8812au
GENERAL.DRIVER-VERSION:                 --
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.0/usb5/5-1/5-1.3/5-1.3:1.0/net/wlxc8d719be6cf9
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
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3,4,5}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   7c65100a-8564-4c07-845c-327597454634 | NETGEAR77-5G
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   be188f6e-dd8a-4c0e-a588-f518834a95ae | NETGEAR77-5G_Ext
CONNECTIONS.AVAILABLE-CONNECTIONS[3]:   9e87e3e7-b4cd-448e-b6df-b8e78dfe38e1 | NETGEAR77

SSID                  BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 
NETGEAR77_Ext         <MAC 'NETGEAR77_Ext' [AC1]>  Infra  8     2447 MHz  270 Mbit/s  92      &#9602;&#9604;&#9606;&#9608;  WPA2      no             
NETGEAR77-5G_Ext      <MAC 'NETGEAR77-5G_Ext' [AC3]>  Infra  153   5765 MHz  270 Mbit/s  92      &#9602;&#9604;&#9606;&#9608;  WPA2      no             
NETGEAR77-5G          <MAC 'NETGEAR77-5G' [AC4]>  Infra  153   5765 MHz  540 Mbit/s  89      &#9602;&#9604;&#9606;&#9608;  WPA2      no             
NETGEAR77             <MAC 'NETGEAR77' [AC2]>  Infra  8     2447 MHz  195 Mbit/s  75      &#9602;&#9604;&#9606;_  WPA2      no             
MotoVAP_M91343SA0JJR  <MAC 'MotoVAP_M91343SA0JJR' [AN5]>  Infra  56    5280 MHz  540 Mbit/s  44      &#9602;&#9604;__  WPA2      no             

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

[[/etc/NetworkManager/system-connections/NETGEAR77-5G_Ext]] (600 root)
[connection] id=NETGEAR77-5G_Ext | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=NETGEAR77-5G_Ext
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NETGEAR77]] (600 root)
[connection] id=NETGEAR77 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=NETGEAR77
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NETGEAR77-5G]] (600 root)
[connection] id=NETGEAR77-5G | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=NETGEAR77-5G
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

global
country US: DFS-FCC
	(2402 - 2472 @ 40), (N/A, 30), (N/A)
	(5170 - 5250 @ 80), (N/A, 23), (N/A), AUTO-BW
	(5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS, AUTO-BW
	(5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
	(5735 - 5835 @ 80), (N/A, 30), (N/A)
	(57240 - 63720 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

enp6s0    no frequency information.

lo        no frequency information.

wlxc8d719be6cf9  32 channels in total; available frequencies :
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
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:5.765 GHz (Channel 153)

##### iwlist scan #######################

enp6s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.447 GHz (Channel 8)
      2   APs on   Frequency:5.765 GHz (Channel 153)

wlxc8d719be6cf9  Scan completed :
          Cell 01 - Address: <MAC 'NETGEAR77_Ext' [AC1]>
                    ESSID:"NETGEAR77_Ext"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=66/100  Signal level=96/100  
                    Extra:fm=0003
          Cell 02 - Address: <MAC 'NETGEAR77' [AC2]>
                    ESSID:"NETGEAR77"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Encryption key:on
                    Bit Rates:867 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=66/100  Signal level=74/100  
                    Extra:fm=0003
          Cell 03 - Address: <MAC 'NETGEAR77-5G_Ext' [AC3]>
                    ESSID:"NETGEAR77-5G_Ext"
                    Protocol:IEEE 802.11AC
                    Mode:Master
                    Frequency:5.765 GHz (Channel 153)
                    Encryption key:on
                    Bit Rates:867 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=88/100  Signal level=100/100  
                    Extra:fm=0003
          Cell 04 - Address: <MAC 'NETGEAR77-5G' [AC4]>
                    ESSID:"NETGEAR77-5G"
                    Protocol:IEEE 802.11AC
                    Mode:Master
                    Frequency:5.765 GHz (Channel 153)
                    Encryption key:on
                    Bit Rates:867 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=89/100  Signal level=96/100  
                    Extra:fm=0001

##### module infos ######################

[8812au]
filename:       /lib/modules/4.15.0-20-generic/updates/dkms/8812au.ko
version:        v4.3.8_12175.20140902
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     0FE007DE1CB755560C5BB1D
depends:        cfg80211
retpoline:      Y
name:           8812au
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           rtw_usb_rxagg_mode:int
parm:           rtw_qos_opt_enable:int
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_special_rf_path:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_bw_mode:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_vht_enable:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_mc2u_disable:int
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
parm:           rtw_hiq_filter:0:allow all, 1:allow special, 2:deny all (uint)
parm:           rtw_adaptivity_en:0:disable, 1:enable, 2:auto (uint)
parm:           rtw_adaptivity_mode:0:normal, 1:carrier sense (uint)
parm:           rtw_nhm_en:0:disable, 1:enable (uint)
parm:           rtw_amplifier_type_2g:BIT3:2G ext-PA, BIT4:2G ext-LNA (uint)
parm:           rtw_amplifier_type_5g:BIT6:5G ext-PA, BIT7:5G ext-LNA (uint)
parm:           rtw_RFE_type:default init value:64 (uint)
parm:           rtw_TxBBSwing_2G:default init value:0xFF (uint)
parm:           rtw_TxBBSwing_5G:default init value:0xFF (uint)
parm:           rtw_tx_pwr_lmt_enable:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_tx_pwr_by_rate:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_phy_file_path:The path of phy parameter (charp)
parm:           rtw_load_phy_file:PHY File Bit Map (int)
parm:           rtw_decrypt_phy_file:Enable Decrypt PHY File (int)

[cfg80211]
filename:       /lib/modules/4.15.0-20-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D5B0789D4C423C81CCFB437
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[8812au]
if2name: wlan%d
ifname: wlan%d
rtw_80211d: 0
rtw_adaptivity_en: 0
rtw_adaptivity_mode: 0
rtw_ampdu_amsdu: 0
rtw_ampdu_enable: 1
rtw_amplifier_type_2g: 0
rtw_amplifier_type_5g: 0
rtw_antdiv_cfg: 2
rtw_antdiv_type: 0
rtw_busy_thresh: 40
rtw_bw_mode: 33
rtw_channel: 1
rtw_channel_plan: 89
rtw_chip_version: 0
rtw_decrypt_phy_file: 0
rtw_enusbss: 0
rtw_hiq_filter: 1
rtw_ht_enable: 1
rtw_hwpdn_mode: 2
rtw_hwpwrp_detect: 0
rtw_hw_wps_pbc: 1
rtw_initmac: (null)
rtw_ips_mode: 0
rtw_lbkmode: 0
rtw_load_phy_file: 68
rtw_low_power: 0
rtw_lowrate_two_xmit: 1
rtw_max_roaming_times: 2
rtw_mc2u_disable: 0
rtw_mp_mode: 0
rtw_network_mode: 0
rtw_nhm_en: 0
rtw_notch_filter: 0
rtw_power_mgnt: 0
rtw_qos_opt_enable: 0
rtw_rf_config: 5
rtw_RFE_type: 64
rtw_rfintfs: 2
rtw_rx_stbc: 1
rtw_smart_ps: 2
rtw_special_rf_path: 0
rtw_TxBBSwing_2G: 255
rtw_TxBBSwing_5G: 255
rtw_tx_pwr_by_rate: 0
rtw_tx_pwr_lmt_enable: 0
rtw_usb_rxagg_mode: 2
rtw_vcs_type: 1
rtw_vht_enable: 1
rtw_vrtl_carrier_sense: 2
rtw_wifi_spec: 0
rtw_wmm_enable: 1

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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   17.438405] platform regulatory.0: Direct firmware load for regulatory.db failed with error -2
[   17.510130] 8812au: loading out-of-tree module taints kernel.
[   17.520551] 8812au: module verification failed: signature and/or required key missing - tainting kernel
[   17.525257] RTL871X: rtl8812au v4.3.8_12175.20140902
[   17.647915] RTL871X: rtw_ndev_init(wlan0)
[   17.658660] rtl8812au 5-1.3:1.0 wlxc8d719be6cf9: renamed from wlan0
[   18.509210] IPv6: ADDRCONF(NETDEV_UP): wlxc8d719be6cf9: link is not ready (repeated 3 times)
[   54.689579] RTL871X: rtw_set_802_11_connect(wlxc8d719be6cf9)  fw_state=0x00000008
[   56.155296] RTL871X: rtw_aes_decrypt(wlxc8d719be6cf9) no_gkey_bc_cnt:4, no_gkey_mc_cnt:0
[   57.178169] RTL871X: rtw_aes_decrypt(wlxc8d719be6cf9) no_gkey_bc_cnt:3, no_gkey_mc_cnt:0
[   58.202188] RTL871X: rtw_aes_decrypt(wlxc8d719be6cf9) no_gkey_bc_cnt:4, no_gkey_mc_cnt:0
[   59.226196] RTL871X: rtw_aes_decrypt(wlxc8d719be6cf9) no_gkey_bc_cnt:3, no_gkey_mc_cnt:0
[   60.250413] RTL871X: rtw_aes_decrypt(wlxc8d719be6cf9) no_gkey_bc_cnt:2, no_gkey_mc_cnt:0
[   61.990977] RTL871X: rtw_aes_decrypt(wlxc8d719be6cf9) no_gkey_bc_cnt:4, no_gkey_mc_cnt:0
[   63.219754] RTL871X: rtw_aes_decrypt(wlxc8d719be6cf9) no_gkey_bc_cnt:2, no_gkey_mc_cnt:0
[   64.448574] RTL871X: rtw_aes_decrypt(wlxc8d719be6cf9) no_gkey_bc_cnt:5, no_gkey_mc_cnt:0
[  113.827844] IPv6: ADDRCONF(NETDEV_UP): wlxc8d719be6cf9: link is not ready (repeated 5 times)

########## wireless info END ############
```

---

### Post by jeremy31 on 2018-05-21
Is the password correct for the wifi AP?

---

### Post by jcautry on 2018-05-21
My apologies, I didn't see the edit you made previously. I have it up now. Thank you so much, I appreciate it!

---

### Post by jeremy31 on 2018-05-21
Please use the thread tools menu near the top right of the page to "mark as solved"

---

### Post by BillaSong on 2018-06-09
Hi @jeremy31, I have same problem with same wifi adapter. I've followed  your instructions, but I still can't get it to work. Here is my wireless  script. Can you please check it?

```
########## wireless info START ##########

Report from: 09 Jun 2018 20:38 CEST +0200

Booted last: 09 Jun 2018 00:00 CEST +0200

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 4.15.0-22-generic #24-Ubuntu SMP Wed May 16 12:15:17 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-V [8086:15b8]
    Subsystem: ASUSTeK Computer Inc. Ethernet Connection (2) I219-V [1043:8672]
    Kernel driver in use: e1000e

03:00.0 Ethernet controller [0200]: Intel Corporation I211 Gigabit Network Connection [8086:1539] (rev 03)
    Subsystem: ASUSTeK Computer Inc. I211 Gigabit Network Connection [1043:85f0]
    Kernel driver in use: igb

##### lsusb #############################

Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 13b1:003f Linksys WUSB6300 802.11a/b/g/n/ac Wireless Adapter [Realtek RTL8812AU]
Bus 001 Device 010: ID 04e8:6863 Samsung Electronics Co., Ltd GT-I9500 [Galaxy S4] / GT-I9250 [Galaxy Nexus] (network tethering)
Bus 001 Device 006: ID 058f:6364 Alcor Micro Corp. AU6477 Card Reader Controller
Bus 001 Device 004: ID 1532:001e Razer USA, Ltd 
Bus 001 Device 007: ID 046d:c227 Logitech, Inc. G15 Refresh Keyboard
Bus 001 Device 005: ID 046d:c226 Logitech, Inc. G15 Refresh Keyboard
Bus 001 Device 003: ID 046d:c223 Logitech, Inc. G11/G15 Keyboard / USB Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
wmi_bmof               16384  0
intel_wmi_thunderbolt    16384  0
mxm_wmi                16384  1 nouveau
cfg80211              622592  0
wmi                    24576  5 asus_wmi,wmi_bmof,intel_wmi_thunderbolt,mxm_wmi,nouveau
video                  40960  2 asus_wmi,nouveau

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
2: enp3s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether <MAC 'enp3s0' [IF1]> brd <MAC address>
3: enp0s31f6: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'enp0s31f6' [IF2]> brd <MAC address>
4: enp0s20f0u2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 1000
    link/ether <MAC 'enp0s20f0u2' [IF3]> brd <MAC address>
    inet 192.168.42.240/24 brd 192.168.42.255 scope global dynamic noprefixroute enp0s20f0u2
       valid_lft 3251sec preferred_lft 3251sec
    inet6 fe80::1115:486:8f94:9057/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

enp0s20f0u2  no wireless extensions.

lo        no wireless extensions.

enp0s31f6  no wireless extensions.

enp3s0    no wireless extensions.

##### route #############################

default via 192.168.42.129 dev enp0s20f0u2 proto dhcp metric 100 
169.254.0.0/16 dev enp0s20f0u2 scope link metric 1000 
192.168.42.0/24 dev enp0s20f0u2 proto kernel scope link src 192.168.42.240 metric 100 

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager

Running:

root       840     1  0 20:31 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s20f0u2
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         SAMSUNG
GENERAL.PRODUCT:                        SAMSUNG_Android
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'enp0s20f0u2' [IF3]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/net/enp0s20f0u2
GENERAL.IP-IFACE:                       enp0s20f0u2
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 3
GENERAL.CON-UUID:                       bad183b7-400b-3d48-b4d7-7654e75082af
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.42.240/24
IP4.GATEWAY:                            192.168.42.129
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.42.129, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.42.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[5]:                        ip_address = 192.168.42.240
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.42.129
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.42.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[16]:                       routers = 192.168.42.129
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1528572781
DHCP4.OPTION[20]:                       host_name = Slaven-home
DHCP4.OPTION[21]:                       requested_netbios_scope = 1
DHCP4.OPTION[22]:                       requested_wpad = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.42.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       next_server = 192.168.42.129
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 3600
IP6.ADDRESS[1]:                         fe80::1115:486:8f94:9057/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   bad183b7-400b-3d48-b4d7-7654e75082af | Wired connection 3

GENERAL.DEVICE:                         enp0s31f6
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (2) I219-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.2-4
GENERAL.HWADDR:                         <MAC 'enp0s31f6' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1f.6/net/enp0s31f6
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

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        I211 Gigabit Network Connection
GENERAL.DRIVER:                         igb
GENERAL.DRIVER-VERSION:                 5.4.0-k
GENERAL.FIRMWARE-VERSION:                0. 6-1
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/enp3s0
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

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Europe/Ljubljana (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp0s20f0u2  no frequency information.

lo        no frequency information.

enp0s31f6  no frequency information.

enp3s0    no frequency information.

##### iwlist scan #######################

enp0s20f0u2  Interface doesn't support scanning.

lo        Interface doesn't support scanning.

enp0s31f6  Interface doesn't support scanning.

enp3s0    Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/4.15.0-22-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D5B0789D4C423C81CCFB437
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-22-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    4.049123] IPv6: ADDRCONF(NETDEV_UP): enp0s31f6: link is not ready (repeated 2 times)
[    4.241875] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready (repeated 2 times)
[   81.684157] rndis_host 1-2:1.0 enp0s20f0u2: renamed from usb0
[   81.715507] IPv6: ADDRCONF(NETDEV_UP): enp0s20f0u2: link is not ready

########## wireless info END ############


```

---

### Post by jeremy31 on 2018-06-09
Does ```
mokutil --sb-state
```
Show Secure Boot is enabled?  Disable in BIOS/UEFI settings

---

### Post by BillaSong on 2018-06-09
You're right! Thank you very much! I've used all day for that :D

---

### Post by louisavs on 2019-03-13
Hey @jeremy31, I also have the same wifi usb. In following your directions, after editing 
```
MAKE = " 'make' all" 
```
to 
```
MAKE="'make' all KVER=${kernelver}"
```

and save the file, I get this error message
```
** (gedit:2223): WARNING **: 23:48:27.324: Set document metadata failed: Setting attribute metadata::gedit-spell-language not supported

** (gedit:2223): WARNING **: 23:48:27.324: Set document metadata failed: Setting attribute metadata::gedit-encoding not supported

```

and the wifi doesn't work. Secure boot is disabled

Any thoughts?

---

### Post by louisavs on 2019-03-15
Got it working...this helped: [https://askubuntu.com/questions/642794/how-do-i-get-the-linksys-wusb6300-wireless-adapter-to-work-on-linux](https://askubuntu.com/questions/642794/how-do-i-get-the-linksys-wusb6300-wireless-adapter-to-work-on-linux)

---

