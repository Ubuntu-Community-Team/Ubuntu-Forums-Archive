---
title: "Samsung R580 Laptop Wireless issues. Kubuntu 15.04 Kernel 4.1.6"
date: 2015-08-23
forum: Networking &amp; Wireless
---

### Post by Jonathan_Carr on 2015-08-23
Hi,

first post. I have Samsung R580 i3 4gb ram etc.. it's 5 years old. Shipped with Win7 32 bit.

Last  year I installed Mint 17 64bit as I was new to Linux, so duel booted.  However I didn't use it much because the wireless connection would drop  to a few mbit connection speed after a few minutes, making it unusable.

I did Google and forum searches for answers, but nothing seemed either easy to implement, or work.

But,  I wanted to use linux after using Win 10 since Feb on the insider  program, so I did a complete clean install of Kubuntu 15.04 64bit  on  the laptop last week, no duel booting, just linux.

After having  the same wireless issues, I upgraded the Kernel to 4.1.6, but to no  avail. Everything works, but again, wireless connects, but drops to a  few mbits speed after 2 minutes or so.  I do have a Texet wireless usb  as back up but cannot fathom how to install it as its not plug-and-play  like windows, It does have Makefiles, but I'm new to Linux.

I would rather get the native wifi card to work.

03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192E/RTL8192SE Wireless LAN Controller (rev 01)

Subsystem: Askey Computer Corp. Device 7160
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort+ <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: I/O ports at 3000 [size=256]
        Region 1: Memory at f0700000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: rtl819xE

Connected to ethernet/ wifi off when i did this:

jonathan@Laptop:~$ iwconfig
eth0      no wireless extensions.

wlan0     802.11bgn  Nickname:"rtl8192E"
          Mode:Managed  Frequency=2.462 GHz  Access Point: Not-Associated   
          Bit Rate:135 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.


jonathan@Laptop:~$ sudo lshw -class network
[sudo] password for jonathan: 
  *-network               
       description: Wireless interface
       product: RTL8192E/RTL8192SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:e0:4c:00:00:01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xE  driverversion=0014.0401.2010 latency=0 link=no multicast=yes  wireless=802.11bgn
       resources: irq:16 ioport:3000(size=256) memory:f0700000-f0703fff
  *-network
       description: Ethernet interface
       product: Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB]
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 11
       serial: 00:24:54:60:e5:ef
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet  physical tp 10bt 10bt-fd 100bt 100bt-fd  1000bt 1000bt-fd  autonegotiation
       configuration: autonegotiation=on  broadcast=yes driver=sky2 driverversion=1.30 duplex=full ip=192.168.1.2  latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:25 memory:f0800000-f0803fff ioport:5000(size=256) memory:f0820000-f083ffff



Wireless-info .txt


```
 
########## wireless info START ##########

Report from: 23 Aug 2015 15:46 BST +0100

Booted last: 23 Aug 2015 14:44 BST +0100

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 4.1.6-040106-generic #201508170230 SMP Mon Aug 17 06:32:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Plasma

##### lspci #############################

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192E/RTL8192SE Wireless LAN Controller [10ec:8192] (rev 01)
    Subsystem: Askey Computer Corp. Device [144f:7160]
    Kernel driver in use: rtl819xE

07:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB] [11ab:4381] (rev 11)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c06a]
    Kernel driver in use: sky2

##### lsusb #############################

Bus 002 Device 003: ID 0e8f:0021 GreenAsia Inc. Multimedia Keyboard Controller
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0a5c:219b Broadcom Corp. Bluetooth 2.1 Device
Bus 001 Device 004: ID 1d57:0008 Xenta 
Bus 001 Device 003: ID 0ac8:c342 Z-Star Microelectronics Corp. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: samsung-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtllib_crypt_tkip      20480  -1 
rtllib_crypt_ccmp      16384  -1 
r8192e_pci            163840  0 
rtllib                147456  1 r8192e_pci
lib80211               16384  3 rtllib,rtllib_crypt_ccmp,rtllib_crypt_tkip
rtl8192se              65536  0 
rtl_pci                28672  1 rtl8192se
rtlwifi                73728  2 rtl_pci,rtl8192se
mac80211              745472  3 rtl_pci,rtlwifi,rtl8192se
cfg80211              552960  2 mac80211,rtlwifi
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15313 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14666 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9489989 (9.4 MB)  TX bytes:2093807 (2.0 MB)
          Interrupt:19 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:7748 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5873 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9266571 (9.2 MB)  TX bytes:562287 (562.2 KB)
          Interrupt:16 Memory:ffffc90000848000-ffffc90000848100 

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     802.11bgn  Nickname:"rtl8192E"
          Mode:Managed  Frequency=2.462 GHz  Access Point: Not-Associated   
          Bit Rate:135 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    1024   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       621     1  0 14:44 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Marvell Technology Group Ltd.
GENERAL.PRODUCT:                        Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB]
GENERAL.DRIVER:                         sky2
GENERAL.DRIVER-VERSION:                 1.30
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:07:00.0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       df17a03d-51f0-48dc-ba28-b2c7da0a0262
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   df17a03d-51f0-48dc-ba28-b2c7da0a0262 | Wired connection 1
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         ip = 192.168.1.2/24, gw = 192.168.1.1
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        expiry = 1440424277
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.1.1
DHCP4.OPTION[15]:                       dhcp_lease_time = 86400
DHCP4.OPTION[16]:                       ip_address = 192.168.1.2
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       domain_name_servers = 192.168.1.1 192.168.1.1
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       requested_ntp_servers = 1
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         ip = fe80::<IP6 'eth0' [IF]>/64, gw = ::

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8192E/RTL8192SE Wireless LAN Controller
GENERAL.DRIVER:                         rtl819xE
GENERAL.DRIVER-VERSION:                 0014.0401.2010
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         39 (Device disconnected by user or client)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:03:00.0/net/wlan0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    no
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   9bdf3bfb-2486-4033-9887-5fcc548c18eb | TALKTALK-
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes

SSID             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
TALKTALK-  <MAC 'TALKTALK-' [AC2]>  Infra  11    2462 MHz  7 Mbit/s   86      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
SKY6B991         <MAC 'SKY6B991' [AC1]>  Infra  1     2412 MHz  16 Mbit/s  72      &#9602;&#9604;&#9606;_  WPA2       no        

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

[[/etc/NetworkManager/system-connections/TALKTALK-]] (600 root)
[connection] id=TALKTALK- | type=wifi | permissions=user:jonathan:;
[wifi] ssid=TALKTALK- | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20), (N/A)
    (2457 - 2482 @ 40), (3, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (3, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), (N/A), NO-IR
    (5735 - 5835 @ 40), (3, 20), (N/A), NO-IR

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
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
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'SKY6B991' [AC1]>
                    ESSID:"SKY6B991"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:144.5 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=84/100  Signal level=-59 dBm  Noise level=-112 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 215ms ago
          Cell 02 - Address: <MAC 'TALKTALK-' [AC2]>
                    ESSID:"TALKTALK-"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:135 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality=82/100  Signal level=-59 dBm  Noise level=-111 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 69ms ago

##### module infos ######################

[rtllib_crypt_tkip]
filename:       /lib/modules/4.1.6-040106-generic/kernel/drivers/staging/rtl8192e/rtllib_crypt_tkip.ko
license:        GPL
srcversion:     B726A96584A88A42BA83BC1
depends:        lib80211
staging:        Y
intree:         Y
vermagic:       4.1.6-040106-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        35:54:79:EA:57:2B:A7:36:1F:E0:C7:5A:06:C6:1F:90:AE:79:79:1E
sig_hashalgo:   sha512

[rtllib_crypt_ccmp]
filename:       /lib/modules/4.1.6-040106-generic/kernel/drivers/staging/rtl8192e/rtllib_crypt_ccmp.ko
license:        GPL
srcversion:     D5BFCF63CB7A826842B8A0C
depends:        lib80211
staging:        Y
intree:         Y
vermagic:       4.1.6-040106-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        35:54:79:EA:57:2B:A7:36:1F:E0:C7:5A:06:C6:1F:90:AE:79:79:1E
sig_hashalgo:   sha512

[r8192e_pci]
filename:       /lib/modules/4.1.6-040106-generic/kernel/drivers/staging/rtl8192e/rtl8192e/r8192e_pci.ko
firmware:       RTL8192E/data.img
firmware:       RTL8192E/main.img
firmware:       RTL8192E/boot.img
license:        GPL
version:        0014.0401.2010
author:         Copyright(c) 2008 - 2010 Realsil Semiconductor Corporation <wlanfae@realtek.com>
description:    Linux driver for Realtek RTL819x WiFi cards
srcversion:     76FB908BD068785304B875A
depends:        rtllib
staging:        Y
intree:         Y
vermagic:       4.1.6-040106-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        35:54:79:EA:57:2B:A7:36:1F:E0:C7:5A:06:C6:1F:90:AE:79:79:1E
sig_hashalgo:   sha512
parm:           ifname: Net interface name, wlan%d=default (charp)
parm:           hwwep: Try to use hardware WEP support(default use hw. set 0 to use software security) (int)
parm:           channels: Channel bitmask for specific locales. NYI (int)

[rtllib]
filename:       /lib/modules/4.1.6-040106-generic/kernel/drivers/staging/rtl8192e/rtllib.ko
license:        GPL
srcversion:     76BFB26B7C56E5521FBEAEF
depends:        lib80211
staging:        Y
intree:         Y
vermagic:       4.1.6-040106-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        35:54:79:EA:57:2B:A7:36:1F:E0:C7:5A:06:C6:1F:90:AE:79:79:1E
sig_hashalgo:   sha512

[rtl8192se]
filename:       /lib/modules/4.1.6-040106-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
firmware:       rtlwifi/rtl8192sefw.bin
description:    Realtek 8192S/8191S 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     88D9E1FA1620EA40DCE1E08
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       4.1.6-040106-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        35:54:79:EA:57:2B:A7:36:1F:E0:C7:5A:06:C6:1F:90:AE:79:79:1E
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_pci]
filename:       /lib/modules/4.1.6-040106-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     E253EFB9827FAB2AD210719
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.1.6-040106-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        35:54:79:EA:57:2B:A7:36:1F:E0:C7:5A:06:C6:1F:90:AE:79:79:1E
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/4.1.6-040106-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     936040588290528C68F15CB
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.1.6-040106-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        35:54:79:EA:57:2B:A7:36:1F:E0:C7:5A:06:C6:1F:90:AE:79:79:1E
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/4.1.6-040106-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     74E30AABABDE7CAEA5C2EFE
depends:        cfg80211
intree:         Y
vermagic:       4.1.6-040106-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        35:54:79:EA:57:2B:A7:36:1F:E0:C7:5A:06:C6:1F:90:AE:79:79:1E
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.1.6-040106-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7A34537645016AD6A2B4091
depends:        
intree:         Y
vermagic:       4.1.6-040106-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        35:54:79:EA:57:2B:A7:36:1F:E0:C7:5A:06:C6:1F:90:AE:79:79:1E
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[r8192e_pci]
channels: 16383
hwwep: 1
ifname: wlan%d

[rtl8192se]
debug: 0
fwlps: N
ips: Y
swenc: N
swlps: Y

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

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x11ab:0x4381 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8192 (rtl819xE)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[ 3678.497651] rtl819xE:MgntActSet_RF_State(): Wait too logn to set RF (repeated 26 times)
[ 3729.494182] rtl819xE 0000:03:00.0 wlan0: softmac_mgmt_xmit():insert to waitqueue, queue_index:6! (repeated 22 times)
[ 3732.581095] rtl819xE:MgntActSet_RF_State(): Wait too logn to set RF (repeated 2 times)
[ 3736.443069] rtl819xE 0000:03:00.0 wlan0: softmac_mgmt_xmit():insert to waitqueue, queue_index:6! (repeated 22 times)

########## wireless info END ############

 
``` 

All help welcome

Thanks

Jonathan.

---

### Post by praseodym on 2015-08-23
Hi,

change the encryption mode to pure WPA2-AES (CCMP), check the router manual. Second, there are two drivers loaded rtl8192se and r8192e_pci.

Check them one after another
```

sudo modprobe -rfv rtl8192se r8192e_pci #unloads them
sudo modprobe -v rtl8192se #loads one of them
```

---

### Post by Jonathan_Carr on 2015-08-25
Hi,

thanks for the advice.  I tried that,it still connects, but the speed drops to a few mbits in speed.  After I did what you suggested I rebooted and immediatley did a download speed test (speedtest.net). Halfway through the download speed gradually dropped until the page froze.

My ethernet ping is 31 and download speed is 12.5 Mbps. The wireless test started well and then grounds to a halt very quickly.

Bugger!

---

### Post by praseodym on 2015-08-26
Try setting the mode in the router to b/g only, not b/g/n or so.

---

