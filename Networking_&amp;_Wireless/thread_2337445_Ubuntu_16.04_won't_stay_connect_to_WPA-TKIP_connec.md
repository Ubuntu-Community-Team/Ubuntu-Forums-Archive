---
title: "Ubuntu 16.04 won't stay connect to WPA-TKIP connection"
date: 2016-09-18
forum: Networking &amp; Wireless
---

### Post by Adam_Jacobs on 2016-09-18
I have just done a fresh install of Ubuntu 16.04 on a laptop on which the wifi worked just fine on 15.10.

I found when I tried to connect to wifi under 16.04 that it would connect initially, stay connected for a short period of time (typically under a minute), and then disconnect. After a minute or two it would try to connect again, and the process would repeat.

Looking through my syslog, I found the following message:

```
iwlwifi 0000:02:00.0 wlp2s0: disabling HT/VHT due to WEP/TKIP use

```
A little bit of googling told me that WPA-TKIP is a less secure wireless protocol than WPA2-AES, that the latter is what I really should be using, and that Ubuntu 16.04 is a bit picky about such things. I had been using WPA-TKIP, and when I adjusted the settings on my wireless access point to use WPA2-AES, then everything worked just fine.

However, I can see an obvious problem here. Although when I'm at home I can set the wireless security protocol to whatever I like, if I'm out and about I shall have to work with whatever wireless security I'm given.

What happens if I need to connect to a network that uses WPA-TKIP or something else that Ubuntu 16.04 doesn't like? Is there a way of telling it to connect anyway?

---

### Post by wildmanne39 on 2016-09-18
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by Adam_Jacobs on 2016-09-18
Thanks Wild Man. Results of the script attached.

---

### Post by Adam_Jacobs on 2016-09-18
Ah, results apparently not attached. Guess I hadn't figured out how to upload an attachment. Results pasted below instead:

```



########## wireless info START ##########


Report from: 18 Sep 2016 20:41 BST +0100


Booted last: 18 Sep 2016 00:00 BST +0100


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-36-generic #55-Ubuntu SMP Thu Aug 11 18:01:55 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
	Subsystem: CLEVO/KAPOK Computer RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1558:0941]
	Kernel driver in use: r8169


02:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
	Subsystem: Intel Corporation Wireless 8260 [8086:1010]
	Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 5986:068f Acer, Inc 
Bus 001 Device 004: ID 8087:0a2b Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


iwlmvm                311296  0
mac80211              737280  1 iwlmvm
iwlwifi               200704  1 iwlmvm
cfg80211              565248  3 iwlwifi,mac80211,iwlmvm
wmi                    20480  0


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp1s0f1  Link encap:Ethernet  HWaddr <MAC 'enp1s0f1' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4200330 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2165488 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6122146684 (6.1 GB)  TX bytes:266455514 (266.4 MB)


wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF2]>  
          inet addr:172.16.100.53  Bcast:172.16.100.255  Mask:255.255.255.0
          inet6 addr: fe80::9ca4:9b90:f555:a0ea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:67278 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26393 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41518216 (41.5 MB)  TX bytes:9854392 (9.8 MB)


##### iwconfig ##########################


lo        no wireless extensions.


enp1s0f1  no wireless extensions.


wlp2s0    IEEE 802.11abgn  ESSID:"BugNet"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'BugNet' [AC1]>   
          Bit Rate=36 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=40/70  Signal level=-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5004   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.16.100.254  0.0.0.0         UG    600    0        0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0
172.16.100.0    0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0


##### resolv.conf #######################


nameserver 127.0.1.1
search lan


##### network managers ##################


Installed:


	NetworkManager


Running:


root       693     1  0 Sep17 ?        00:00:17 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 8260
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-36-generic
GENERAL.FIRMWARE-VERSION:               16.242414.0
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            0
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
GENERAL.CONNECTION:                     BugNet
GENERAL.CON-UUID:                       a967e905-c15a-4083-b058-a5e1d02c7200
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/21
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     36 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   a967e905-c15a-4083-b058-a5e1d02c7200 | BugNet
IP4.ADDRESS[1]:                         172.16.100.53/24
IP4.GATEWAY:                            172.16.100.254
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             172.16.100.254
IP4.DOMAIN[1]:                          lan
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1474193472
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 172.16.100.254
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 172.16.100.53
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = lan
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 172.16.100.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 4294967295
DHCP4.OPTION[23]:                       domain_name_servers = 172.16.100.254
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 172.16.100.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 172.16.100.254
IP6.ADDRESS[1]:                         fe80::9ca4:9b90:f555:a0ea/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp1s0f1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp1s0f1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         40 (Carrier/link changed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.1/net/enp1s0f1
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
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID                 BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY          ACTIVE  * 
BugNet               <MAC 'BugNet' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  55      &#9602;&#9604;__  WPA1 WPA2         yes     * 
BTWifi-with-FON      <MAC 'BTWifi-with-FON' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  50      &#9602;&#9604;__  --                no        
BTWifi-X             <MAC 'BTWifi-X' [AC4]>  Infra  1     2412 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA1 WPA2 802.1X  no        
BTHub5-SGQX          <MAC 'BTHub5-SGQX' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA2              no        
BTWiFi-with-FON      <MAC 'BTWiFi-with-FON' [AC5]>  Infra  11    2462 MHz  54 Mbit/s  39      &#9602;&#9604;__  --                no        
BTHub3-2Z9S          <MAC 'BTHub3-2Z9S' [AC6]>  Infra  11    2462 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA1 WPA2         no        
EE-BrightBox-5dxmtf  <MAC 'EE-BrightBox-5dxmtf' [AN7]>  Infra  6     2437 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2         no        


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


[[/etc/NetworkManager/system-connections/BugNet]] (600 root)
[connection] id=BugNet | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=BugNet
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/London (based on set time zone)


country 00: DFS-UNSET
	(2402 - 2472 @ 40), (6, 20), (N/A)
	(2457 - 2482 @ 40), (6, 20), (N/A), PASSIVE-SCAN
	(2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 160), (6, 20), (N/A), PASSIVE-SCAN
	(5250 - 5330 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
	(5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
	(5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


lo        no frequency information.


enp1s0f1  no frequency information.


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
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp1s0f1  Interface doesn't support scanning.


Channel occupancy:


      3   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.462 GHz (Channel 11)


wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'BugNet' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"BugNet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000007f3b43c5e
                    Extra: Last beacon: 67804ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'BTHub5-SGQX' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"BTHub5-SGQX"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002f0e4751c4
                    Extra: Last beacon: 684ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'BTWifi-with-FON' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002f0e488b7d
                    Extra: Last beacon: 684ms ago
          Cell 04 - Address: <MAC 'BTWifi-X' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002f0e483014
                    Extra: Last beacon: 680ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 05 - Address: <MAC 'BTWiFi-with-FON' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000127b06c990
                    Extra: Last beacon: 368ms ago
          Cell 06 - Address: <MAC 'BTHub3-2Z9S' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-2Z9S"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000127b06d102
                    Extra: Last beacon: 364ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[iwlmvm]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     49DC02934CB3D8C312FF8E1
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)


[mac80211]
filename:       /lib/modules/4.4.0-36-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B10AF1CD828D26173EA0378
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
vermagic:       4.4.0-36-generic SMP mod_unload modversions 
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
filename:       /lib/modules/4.4.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 
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


[71948.592324] wlp2s0: <MAC 'BugNet' [AC1]> denied association (code=12)
[71959.433213] wlp2s0: authenticate with <MAC 'BugNet' [AC1]>
[71959.439458] wlp2s0: send auth to <MAC 'BugNet' [AC1]> (try 1/3)
[71959.441334] wlp2s0: authenticated
[71959.443671] iwlwifi 0000:02:00.0 wlp2s0: disabling HT/VHT due to WEP/TKIP use
[71959.443687] iwlwifi 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[71959.443697] iwlwifi 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[71959.449504] wlp2s0: associate with <MAC 'BugNet' [AC1]> (try 1/3)
[71959.451979] wlp2s0: RX AssocResp from <MAC 'BugNet' [AC1]> (capab=0x411 status=12 aid=1)
[71959.451995] wlp2s0: <MAC 'BugNet' [AC1]> denied association (code=12)
[71973.039067] wlp2s0: authenticate with <MAC 'BugNet' [AC1]>
[71973.045346] wlp2s0: send auth to <MAC 'BugNet' [AC1]> (try 1/3)
[71973.048166] wlp2s0: authenticated
[71973.048303] iwlwifi 0000:02:00.0 wlp2s0: disabling HT/VHT due to WEP/TKIP use
[71973.048307] iwlwifi 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[71973.048324] iwlwifi 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[71973.049122] wlp2s0: associate with <MAC 'BugNet' [AC1]> (try 1/3)
[71973.051290] wlp2s0: RX AssocResp from <MAC 'BugNet' [AC1]> (capab=0x411 status=12 aid=1)
[71973.051295] wlp2s0: <MAC 'BugNet' [AC1]> denied association (code=12)
[71983.885038] wlp2s0: authenticate with <MAC 'BugNet' [AC1]>
[71983.891280] wlp2s0: send auth to <MAC 'BugNet' [AC1]> (try 1/3)
[71983.893160] wlp2s0: authenticated
[71983.893503] iwlwifi 0000:02:00.0 wlp2s0: disabling HT/VHT due to WEP/TKIP use
[71983.893512] iwlwifi 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[71983.893519] iwlwifi 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[71983.896197] wlp2s0: associate with <MAC 'BugNet' [AC1]> (try 1/3)
[71983.901091] wlp2s0: RX AssocResp from <MAC 'BugNet' [AC1]> (capab=0x411 status=0 aid=1)
[71983.902238] wlp2s0: associated
[71983.902330] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[72000.612868] wlp2s0: deauthenticated from <MAC 'BugNet' [AC1]> (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[72000.640035] wlp2s0: authenticate with <MAC 'BugNet' [AC1]>
[72000.646453] wlp2s0: send auth to <MAC 'BugNet' [AC1]> (try 1/3)
[72000.648330] wlp2s0: authenticated
[72000.648779] iwlwifi 0000:02:00.0 wlp2s0: disabling HT/VHT due to WEP/TKIP use
[72000.648794] iwlwifi 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[72000.648804] iwlwifi 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[72000.650868] wlp2s0: associate with <MAC 'BugNet' [AC1]> (try 1/3)
[72000.653329] wlp2s0: RX AssocResp from <MAC 'BugNet' [AC1]> (capab=0x411 status=12 aid=1)
[72000.653339] wlp2s0: <MAC 'BugNet' [AC1]> denied association (code=12)
[72001.759906] wlp2s0: authenticate with <MAC 'BugNet' [AC1]>
[72001.766218] wlp2s0: send auth to <MAC 'BugNet' [AC1]> (try 1/3)
[72001.768089] wlp2s0: authenticated
[72001.768267] iwlwifi 0000:02:00.0 wlp2s0: disabling HT/VHT due to WEP/TKIP use
[72001.768271] iwlwifi 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[72001.768274] iwlwifi 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[72001.770713] wlp2s0: associate with <MAC 'BugNet' [AC1]> (try 1/3)
[72001.772954] wlp2s0: RX AssocResp from <MAC 'BugNet' [AC1]> (capab=0x411 status=12 aid=1)
[72001.772958] wlp2s0: <MAC 'BugNet' [AC1]> denied association (code=12)
[72003.380364] wlp2s0: authenticate with <MAC 'BugNet' [AC1]>
[72003.386690] wlp2s0: send auth to <MAC 'BugNet' [AC1]> (try 1/3)
[72003.388479] wlp2s0: authenticated
[72003.388643] iwlwifi 0000:02:00.0 wlp2s0: disabling HT/VHT due to WEP/TKIP use
[72003.388648] iwlwifi 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[72003.388650] iwlwifi 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[72003.390516] wlp2s0: associate with <MAC 'BugNet' [AC1]> (try 1/3)
[72003.392699] wlp2s0: RX AssocResp from <MAC 'BugNet' [AC1]> (capab=0x411 status=12 aid=1)
[72003.392703] wlp2s0: <MAC 'BugNet' [AC1]> denied association (code=12)
[72015.983940] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[72016.588836] wlp2s0: authenticate with <MAC 'BugNet' [AC1]>
[72016.595281] wlp2s0: send auth to <MAC 'BugNet' [AC1]> (try 1/3)
[72016.597931] wlp2s0: authenticated
[72016.598700] iwlwifi 0000:02:00.0 wlp2s0: disabling HT/VHT due to WEP/TKIP use
[72016.598719] iwlwifi 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[72016.598730] iwlwifi 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[72016.601667] wlp2s0: associate with <MAC 'BugNet' [AC1]> (try 1/3)
[72016.604070] wlp2s0: RX AssocResp from <MAC 'BugNet' [AC1]> (capab=0x411 status=12 aid=1)
[72016.604086] wlp2s0: <MAC 'BugNet' [AC1]> denied association (code=12)
[72027.338117] wlp2s0: authenticate with <MAC 'BugNet' [AC1]>
[72027.344557] wlp2s0: send auth to <MAC 'BugNet' [AC1]> (try 1/3)
[72027.349007] wlp2s0: authenticated
[72027.350603] iwlwifi 0000:02:00.0 wlp2s0: disabling HT/VHT due to WEP/TKIP use
[72027.350619] iwlwifi 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[72027.350629] iwlwifi 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[72027.353932] wlp2s0: associate with <MAC 'BugNet' [AC1]> (try 1/3)
[72027.356158] wlp2s0: RX AssocResp from <MAC 'BugNet' [AC1]> (capab=0x411 status=12 aid=1)
[72027.356167] wlp2s0: <MAC 'BugNet' [AC1]> denied association (code=12)
[72041.012240] wlp2s0: authenticate with <MAC 'BugNet' [AC1]>
[72041.018453] wlp2s0: send auth to <MAC 'BugNet' [AC1]> (try 1/3)
[72041.020195] wlp2s0: authenticated
[72041.020343] iwlwifi 0000:02:00.0 wlp2s0: disabling HT/VHT due to WEP/TKIP use
[72041.020346] iwlwifi 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[72041.020348] iwlwifi 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[72041.023246] wlp2s0: associate with <MAC 'BugNet' [AC1]> (try 1/3)
[72041.025449] wlp2s0: RX AssocResp from <MAC 'BugNet' [AC1]> (capab=0x411 status=12 aid=1)
[72041.025453] wlp2s0: <MAC 'BugNet' [AC1]> denied association (code=12)
[72054.260340] wlp2s0: authenticate with <MAC 'BugNet' [AC1]>
[72054.267011] wlp2s0: send auth to <MAC 'BugNet' [AC1]> (try 1/3)
[72054.319508] wlp2s0: send auth to <MAC 'BugNet' [AC1]> (try 2/3)
[72054.396065] wlp2s0: send auth to <MAC 'BugNet' [AC1]> (try 3/3)
[72054.467266] wlp2s0: authentication with <MAC 'BugNet' [AC1]> timed out
[72077.296784] wlp2s0: authenticate with <MAC 'BugNet' [AC1]>
[72077.303011] wlp2s0: send auth to <MAC 'BugNet' [AC1]> (try 1/3)
[72077.305057] wlp2s0: authenticated
[72077.305575] iwlwifi 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[72077.305590] iwlwifi 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[72077.311514] wlp2s0: associate with <MAC 'BugNet' [AC1]> (try 1/3)
[72077.324110] wlp2s0: RX AssocResp from <MAC 'BugNet' [AC1]> (capab=0x411 status=0 aid=1)
[72077.327516] wlp2s0: associated
[72077.327581] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[72085.794834] r8169 0000:01:00.1 enp1s0f1: link down


########## wireless info END ############



```

---

### Post by wildmanne39 on 2016-09-18
Please do:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlmvm
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
see if that helps.

---

