---
title: "QCA9377 and ath10k on Ubuntu 15.04 (Apparently now it's supported)"
date: 2015-10-28
forum: Networking &amp; Wireless
---

### Post by dr-cono on 2015-10-28
Hi, I bought an Acer Aspire E5 laptop with an **Atheros Qualcomm QCA9377 168c:0042** which didn't work and i found a bunch of threads saying just that.
I found today a mailing list saying that now it's supported on ath10k 
[http://www.spinics.net/lists/linux-wireless/msg143027.html](http://www.spinics.net/lists/linux-wireless/msg143027.html)
and it was added on the ath10k github
[https://github.com/kvalo/ath10k-firmware](https://github.com/kvalo/ath10k-firmware)
I don't know how to install it from github, any help will be appreciated (by me and many others with this card)
here's my wireless-info.txt 

```
########## wireless info START ##########


Report from: 28 Oct 2015 22:33 ART -0300


Booted last: 28 Oct 2015 18:49 ART -0300


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid


##### kernel ############################


Linux 3.19.0-31-generic #36-Ubuntu SMP Wed Oct 7 15:04:02 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash


##### desktop ###########################


GNOME


##### lspci #############################


02:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: Acer Incorporated [ALI] Device [1025:096a]
    Kernel driver in use: r8169


03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)
    Subsystem: Foxconn International, Inc. Device [105b:e09a]


04:00.0 3D controller [0302]: NVIDIA Corporation Device [10de:1299] (rev a1)


##### lsusb #############################


Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b520 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0489:e09c Foxconn / Hon Hai 
Bus 001 Device 004: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


rt2800usb              28672  0 
rt2x00usb              24576  1 rt2800usb
rt2800lib              94208  1 rt2800usb
rt2x00lib              57344  3 rt2x00usb,rt2800lib,rt2800usb
crc_ccitt              16384  1 rt2800lib
ath10k_pci             40960  0 
ath10k_core           192512  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              724992  4 rt2x00lib,rt2x00usb,rt2800lib,ath10k_core
cfg80211              540672  4 ath,mac80211,rt2x00lib,ath10k_core
acer_wmi               20480  0 
sparse_keymap          16384  1 acer_wmi
snd_soc_rt5640         94208  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  1 snd_soc_rt5640
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
wmi                    20480  1 acer_wmi
video                  20480  2 i915_bpo,acer_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.117  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:144551 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106477 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:196359234 (196.3 MB)  TX bytes:13006488 (13.0 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"liniers"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'liniers' [AC1]>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:419  Invalid misc:2517   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    400    0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     400    0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       693     1  0 21:49 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Ralink
GENERAL.PRODUCT:                        802.11 n WLAN
GENERAL.DRIVER:                         rt2800usb
GENERAL.DRIVER-VERSION:                 3.19.0-31-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     liniers
GENERAL.CON-UUID:                       136ccb20-3034-49b6-9f89-d53f86159b0c
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     48 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   136ccb20-3034-49b6-9f89-d53f86159b0c | liniers
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
IP4.ADDRESS[1]:                         ip = 192.168.0.117/24, gw = 192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        network_number = 192.168.0.0
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_time_offset = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_host_name = 1
DHCP4.OPTION[8]:                        host_name = ubentu
DHCP4.OPTION[9]:                        expiry = 1446166555
DHCP4.OPTION[10]:                       requested_wpad = 1
DHCP4.OPTION[11]:                       requested_domain_name = 1
DHCP4.OPTION[12]:                       next_server = 192.168.0.1
DHCP4.OPTION[13]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_subnet_mask = 1
DHCP4.OPTION[16]:                       routers = 192.168.0.1
DHCP4.OPTION[17]:                       ip_address = 192.168.0.117
DHCP4.OPTION[18]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[19]:                       requested_static_routes = 1
DHCP4.OPTION[20]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[21]:                       dhcp_lease_time = 86400
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[23]:                       requested_domain_name_servers = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[27]:                       requested_interface_mtu = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       requested_netbios_scope = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         ip = fe80::<IP6 'wlan0' [IF]>/64, gw = ::


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.1/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIRED-PROPERTIES.CARRIER:               off


SSID     BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
JM       <MAC 'JM' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA1 WPA2  no        
liniers  <MAC 'liniers' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA2       yes     * 


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


[[/etc/NetworkManager/system-connections/Fibertel WiFi477]] (600 root)
[connection] id=Fibertel WiFi477 | type=wifi
[wifi] ssid=Fibertel WiFi477 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/liniers]] (600 root)
[connection] id=liniers | type=wifi
[wifi] ssid=liniers | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/PHI Desarrollo]] (600 root)
[connection] id=PHI Desarrollo | type=wifi
[wifi] ssid=PHI Desarrollo | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ATTEL]] (600 root)
[connection] id=ATTEL | type=wifi
[wifi] ssid=ATTEL | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=manual
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ATTEL3]] (600 root)
[connection] id=ATTEL3 | type=wifi
[wifi] ssid=ATTEL3 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=manual
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/McDonalds FREE]] (600 root)
[connection] id=McDonalds FREE | type=wifi
[wifi] ssid=McDonalds FREE | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/WLAN_3]] (600 root)
[connection] id=WLAN_3 | type=wifi
[wifi] ssid=WLAN_3 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Argentina/Cordoba (based on set time zone)


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


eth0      no frequency information.


lo        no frequency information.


wlan0     14 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'liniers' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"liniers"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003cbfe9584a
                    Extra: Last beacon: 140ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'JM' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"JM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000097649bdc7a
                    Extra: Last beacon: 2644ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rt2800usb]
filename:       /lib/modules/3.19.0-31-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     CDB4A56A88AAEC3126F6347
depends:        rt2x00lib,rt2800lib,rt2x00usb
intree:         Y
vermagic:       3.19.0-31-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B4:BA:13:D5:CE:C9:3E:1A:F4:B3:4D:36:DA:1B:D4:FC:FF:A5:44:10
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2x00usb]
filename:       /lib/modules/3.19.0-31-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     B51D09F4F13F9196B61EBE4
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.19.0-31-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B4:BA:13:D5:CE:C9:3E:1A:F4:B3:4D:36:DA:1B:D4:FC:FF:A5:44:10
sig_hashalgo:   sha512


[rt2800lib]
filename:       /lib/modules/3.19.0-31-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     491D0D9622C1740D95E8041
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.19.0-31-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B4:BA:13:D5:CE:C9:3E:1A:F4:B3:4D:36:DA:1B:D4:FC:FF:A5:44:10
sig_hashalgo:   sha512


[rt2x00lib]
filename:       /lib/modules/3.19.0-31-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     7C3B03973B59C2A2A136B6C
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-31-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B4:BA:13:D5:CE:C9:3E:1A:F4:B3:4D:36:DA:1B:D4:FC:FF:A5:44:10
sig_hashalgo:   sha512


[ath10k_pci]
filename:       /lib/modules/3.19.0-31-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
srcversion:     43DC2B7B76ADD3C9899062A
depends:        ath10k_core
intree:         Y
vermagic:       3.19.0-31-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B4:BA:13:D5:CE:C9:3E:1A:F4:B3:4D:36:DA:1B:D4:FC:FF:A5:44:10
sig_hashalgo:   sha512
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)


[ath10k_core]
filename:       /lib/modules/3.19.0-31-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     9FA596B97B37F20B0E1DE44
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       3.19.0-31-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B4:BA:13:D5:CE:C9:3E:1A:F4:B3:4D:36:DA:1B:D4:FC:FF:A5:44:10
sig_hashalgo:   sha512
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           p2p:Enable ath10k P2P support (uint)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)


[ath]
filename:       /lib/modules/3.19.0-31-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     D89F916A5E804AF040C4D29
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-31-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B4:BA:13:D5:CE:C9:3E:1A:F4:B3:4D:36:DA:1B:D4:FC:FF:A5:44:10
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.19.0-31-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     6AE775D26377F997426A49D
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-31-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B4:BA:13:D5:CE:C9:3E:1A:F4:B3:4D:36:DA:1B:D4:FC:FF:A5:44:10
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.19.0-31-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-31-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B4:BA:13:D5:CE:C9:3E:1A:F4:B3:4D:36:DA:1B:D4:FC:FF:A5:44:10
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rt2800usb]
nohwcrypt: N


[ath10k_pci]
irq_mode: 0
reset_mode: 0


[ath10k_core]
debug_mask: 0
p2p: 0
skip_otp: N
uart_print: N


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


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   24.238934] r8169 0000:02:00.1 eth0: link down
[  379.302035] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5390, rev 0502 detected
[  379.311788] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5370 detected
[  405.328651] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  405.344194] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  406.596156] wlan0: authenticate with <MAC 'liniers' [AC1]>
[  406.608588] wlan0: send auth to <MAC 'liniers' [AC1]> (try 1/3)
[  406.610040] wlan0: authenticated
[  406.610184] rt2800usb 1-3:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  406.613578] wlan0: associate with <MAC 'liniers' [AC1]> (try 1/3)
[  406.615887] wlan0: RX AssocResp from <MAC 'liniers' [AC1]> (capab=0x411 status=0 aid=5)
[  406.618662] wlan0: associated


########## wireless info END ############}


```


**Note: Im using an USB Wireless card 148f:5370 Ralink**

---

### Post by praseodym on 2015-10-29
Hi, the firmware is already there, please try

```
sudo iwconfig wlan0 power off
```

---

### Post by jeremy31 on 2015-10-29
I think this is what will work for now
```
sudo apt-get install build-essential linux-headers-$(uname -r) git
echo "options ath10k_core skip_otp=y" | sudo tee /etc/modprobe.d/ath10k_core.conf
wget https://www.dropbox.com/s/6hl52r0krq3wpxf/backports-20150903b.tar.gz
tar -zxvf backports-20150903b.tar.gz
cd backports-20150903
make defconfig-ath10k
make
sudo make install
git clone https://github.com/kvalo/ath10k-firmware.git
sudo cp -r ath10k-firmware/ath10k/ /lib/firmware/
sudo cp -r ath10k-firmware/QCA9377 /lib/firmware/ath10k/
```

Reboot

If it doesn't work, run the wireless script again

---

### Post by dr-cono on 2015-10-29
Thanks for the replies. I tried what jeremy said and didn't work. Also, i cant use the USB Wireless Dongle.
Here's the wireless-info.txt
```



########## wireless info START ##########


Report from: 29 Oct 2015 14:10 ART -0300


Booted last: 29 Oct 2015 11:01 ART -0300


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid


##### kernel ############################


Linux 3.19.0-31-generic #36-Ubuntu SMP Wed Oct 7 15:04:02 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, --verbose, nosplash, debug


##### desktop ###########################


sed: can't read /home/cono/.dmrc: No such file or directory


Could not be determined.


##### lspci #############################


02:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: Acer Incorporated [ALI] Device [1025:096a]
    Kernel driver in use: r8169


03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)
    Subsystem: Foxconn International, Inc. Device [105b:e09a]
    Kernel driver in use: ath10k_pci


##### lsusb #############################


Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b520 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0489:e09c Foxconn / Hon Hai 
Bus 001 Device 004: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


ath10k_pci             45056  0 
ath10k_core           290816  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              655360  1 ath10k_core
cfg80211              548864  3 ath,mac80211,ath10k_core
compat                 28672  4 cfg80211,mac80211,ath10k_pci,ath10k_core
acer_wmi               20480  0 
sparse_keymap          16384  1 acer_wmi
snd_soc_rt5640         94208  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  1 snd_soc_rt5640
snd_pcm               106496  8 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
video                  20480  2 i915_bpo,acer_wmi
wmi                    20480  1 acer_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:408 errors:0 dropped:0 overruns:0 frame:0
          TX packets:372 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:68085 (68.0 KB)  TX bytes:44405 (44.4 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       614     1  0 14:01 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         40 (Carrier/link changed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.1/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIRED-PROPERTIES.CARRIER:               off


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


[[/etc/NetworkManager/system-connections/Fibertel WiFi477]] (600 root)
[connection] id=Fibertel WiFi477 | type=wifi
[wifi] ssid=Fibertel WiFi477 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/liniers]] (600 root)
[connection] id=liniers | type=wifi
[wifi] ssid=liniers | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/PHI Desarrollo]] (600 root)
[connection] id=PHI Desarrollo | type=wifi
[wifi] ssid=PHI Desarrollo | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ATTEL]] (600 root)
[connection] id=ATTEL | type=wifi
[wifi] ssid=ATTEL | mac-address=<MAC address>
[ipv4] method=manual
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ATTEL3]] (600 root)
[connection] id=ATTEL3 | type=wifi
[wifi] ssid=ATTEL3 | mac-address=<MAC address>
[ipv4] method=manual
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/McDonalds FREE]] (600 root)
[connection] id=McDonalds FREE | type=wifi
[wifi] ssid=McDonalds FREE | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/WLAN_3]] (600 root)
[connection] id=WLAN_3 | type=wifi
[wifi] ssid=WLAN_3 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Argentina/Cordoba (based on set time zone)


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


eth0      no frequency information.


lo        no frequency information.


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[ath10k_pci]
filename:       /lib/modules/3.19.0-31-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
srcversion:     0318FD37FAE113D949B6EEB
depends:        ath10k_core,compat
vermagic:       3.19.0-31-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)


[ath10k_core]
filename:       /lib/modules/3.19.0-31-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     96FF163DFC19D168839BAB9
depends:        mac80211,cfg80211,compat,ath
vermagic:       3.19.0-31-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)


[ath]
filename:       /lib/modules/3.19.0-31-generic/updates/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     599C4ECEE9D167A7F2EDD5C
depends:        cfg80211
vermagic:       3.19.0-31-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/3.19.0-31-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
srcversion:     BEF453E7AC487F911F8EDBF
depends:        cfg80211,compat
vermagic:       3.19.0-31-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.19.0-31-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F6775E4370E54D5795E4BE2
depends:        compat
vermagic:       3.19.0-31-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath10k_pci]
irq_mode: 0
reset_mode: 0


[ath10k_core]
cryptmode: 0
debug_mask: 0
skip_otp: Y
uart_print: N


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/ath10k_core.conf]
options ath10k_core skip_otp=y


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


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   23.171290] r8169 0000:02:00.1 eth0: link down (repeated 2 times)
[   24.855638] r8169 0000:02:00.1 eth0: link up
[  357.472760] r8169 0000:02:00.1 eth0: link down
[  558.100552] rt2x00lib: disagrees about version of symbol ieee80211_register_hw
[  558.100557] rt2x00lib: Unknown symbol ieee80211_register_hw (err -22)
[  558.100563] rt2x00lib: disagrees about version of symbol ieee80211_get_hdrlen_from_skb
[  558.100565] rt2x00lib: Unknown symbol ieee80211_get_hdrlen_from_skb (err -22)
[  558.100571] rt2x00lib: disagrees about version of symbol ieee80211_wake_queue
[  558.100572] rt2x00lib: Unknown symbol ieee80211_wake_queue (err -22)
[  558.100583] rt2x00lib: disagrees about version of symbol ieee80211_get_buffered_bc
[  558.100585] rt2x00lib: Unknown symbol ieee80211_get_buffered_bc (err -22)
[  558.100591] rt2x00lib: disagrees about version of symbol wiphy_rfkill_set_hw_state
[  558.100592] rt2x00lib: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[  558.100602] rt2x00lib: disagrees about version of symbol ieee80211_queue_delayed_work
[  558.100604] rt2x00lib: Unknown symbol ieee80211_queue_delayed_work (err -22)
[  558.100607] rt2x00lib: disagrees about version of symbol wiphy_rfkill_stop_polling
[  558.100609] rt2x00lib: Unknown symbol wiphy_rfkill_stop_polling (err -22)
[  558.100612] rt2x00lib: disagrees about version of symbol ieee80211_ctstoself_get
[  558.100614] rt2x00lib: Unknown symbol ieee80211_ctstoself_get (err -22)
[  558.100647] rt2x00lib: Unknown symbol ieee80211_rx (err 0)
[  558.100666] rt2x00lib: Unknown symbol ieee80211_iterate_active_interfaces (err 0)
[  558.100671] rt2x00lib: disagrees about version of symbol ieee80211_free_txskb
[  558.100673] rt2x00lib: Unknown symbol ieee80211_free_txskb (err -22)
[  558.100680] rt2x00lib: disagrees about version of symbol ieee80211_tx_status
[  558.100681] rt2x00lib: Unknown symbol ieee80211_tx_status (err -22)
[  558.100684] rt2x00lib: disagrees about version of symbol ieee80211_stop_queue
[  558.100686] rt2x00lib: Unknown symbol ieee80211_stop_queue (err -22)
[  558.100690] rt2x00lib: disagrees about version of symbol ieee80211_stop_queues
[  558.100691] rt2x00lib: Unknown symbol ieee80211_stop_queues (err -22)
[  558.100697] rt2x00lib: disagrees about version of symbol wiphy_rfkill_start_polling
[  558.100699] rt2x00lib: Unknown symbol wiphy_rfkill_start_polling (err -22)
[  558.100702] rt2x00lib: disagrees about version of symbol ieee80211_iterate_active_interfaces_atomic
[  558.100703] rt2x00lib: Unknown symbol ieee80211_iterate_active_interfaces_atomic (err -22)
[  558.100715] rt2x00lib: disagrees about version of symbol ieee80211_unregister_hw
[  558.100716] rt2x00lib: Unknown symbol ieee80211_unregister_hw (err -22)
[  558.100720] rt2x00lib: disagrees about version of symbol ieee80211_beacon_get_tim
[  558.100722] rt2x00lib: Unknown symbol ieee80211_beacon_get_tim (err -22)
[  558.100725] rt2x00lib: disagrees about version of symbol ieee80211_rts_get
[  558.100726] rt2x00lib: Unknown symbol ieee80211_rts_get (err -22)
[  558.100735] rt2x00lib: disagrees about version of symbol ieee80211_queue_work
[  558.100737] rt2x00lib: Unknown symbol ieee80211_queue_work (err -22)


########## wireless info END ############



```

notice that
```

ubentu@cono: dmesg | grep 0042
[   20.922408] ath10k_pci 0000:03:00.0: device 0042 with chip_id 003820ff isn't supported

```

---

### Post by jeremy31 on 2015-10-29
Might have to wait on another patch and firmware for your version

Too uninstall the backports so you can use the other wifi
```
cd backports-20150903
sudo make uninstall
```

Reboot

---

### Post by dr-cono on 2015-10-29
Thanks, the wireless dongle is working now. I'll try to contact the developer. Thanks a lot.

---

### Post by rinfinity on 2015-10-31
The patch developer talks of the presence of two different versions of QCA9377 and the patch is for V1.0.

Seems, either the fw is broken (very improbable) or your QCA9377 is V2.0.
When support for V1.0 is available, V2.0 shouldn't take long.

BTW, the QCA9377 is a WL-BT combination chip and the wl part is NFA 435.
[https://wikidevi.com/wiki/Qualcomm_Atheros](https://wikidevi.com/wiki/Qualcomm_Atheros)

Could you please tell us the date of manufacturing of your device. If it's earlier than August 2015AD, it has to be QCA9377 V1.0 and kvolo's patch and firmware 'should' work. If it doesn't work despite being manufactured earlier than Aug. 15, I suggest making it known to kvolo.

The V1.1 was released on or after Nov. 21, 2014AD.
[http://certifications.prod.wi-fi.org/pdf/certificate/public/download?cid=WFA57190](http://certifications.prod.wi-fi.org/pdf/certificate/public/download?cid=WFA57190)

The V2.0 was released on or after August 6, 2015AD.

[http://certifications.prod.wi-fi.org/pdf/certificate/public/download?cid=WFA61568](http://certifications.prod.wi-fi.org/pdf/certificate/public/download?cid=WFA61568)

---

### Post by dr-cono on 2015-11-01
Thanks for the reply.


Found "MFG Date: 2015/04/24" on the bottom of the laptop.

---

### Post by rinfinity on 2015-11-03
Device having mfg month 4 of 2015AD should be V1.0 and 'should' work with the given driver/fw. I'll check with kvolo and fw developer to see what the issue can be.
Now that we've come so far, I think we have the good new waiting around the corner. ;)

What we call QCA9377 is actually a 'series' of wifi ac devices. There are a total of 11 different chips.

[http://www.wi-fi.org/product-finder-results?keywords=qca9377](http://www.wi-fi.org/product-finder-results?keywords=qca9377)

---

### Post by dr-cono on 2015-11-04
I see, i guess im going to have to wait for it.
WIll post here once i get it working so people googling find it.
Thank you for the support.

---

### Post by jeremy31 on 2015-11-04
I see there is a new post about the QCA9377 [http://www.spinics.net/lists/linux-wireless/msg143412.html](http://www.spinics.net/lists/linux-wireless/msg143412.html)

I might try to patch backports with it when I get the time

---

### Post by dr-cono on 2015-11-05
> **jeremy31 said:**
> I see there is a new post about the QCA9377 [http://www.spinics.net/lists/linux-wireless/msg143412.html](http://www.spinics.net/lists/linux-wireless/msg143412.html)

I might try to patch backports with it when I get the time
Great! I'll test it

---

### Post by jeremy31 on 2015-11-05
Try the commands from post #3 again.  You can skip the commands after "sudo make install" as you should still have the firmware
I updated the code using the patch and I am not sure if it is going to work but it compiled fine on my computer

---

### Post by xbarmar on 2015-11-05
> **jeremy31 said:**
> Try the commands from post #3 again.  You can skip the commands after "sudo make install" as you should still have the firmware
I updated the code using the patch and I am not sure if it is going to work but it compiled fine on my computer

By checking your backports package content (backports-20150903b.tar.gz) I see there're some code parts missing from my patch-set, e.g. the whole section of ath10k_hw_params_list for ".id = QCA9377_HW_1_0_DEV_VERSION ".

If you look at the line "chip_id 003820ff" from the "[   20.922408] ath10k_pci 0000:03:00.0: device 0042 with chip_id 003820ff isn't supported" dr-cono posted, it seems the qca9377 NIC he has is a hw1.0 rev, hence this is releavant and won't work without the full patchset posted on [http://lists.infradead.org/pipermail/ath10k/2015-November/006401.html](http://lists.infradead.org/pipermail/ath10k/2015-November/006401.html)

---

### Post by xbarmar on 2015-11-05
I've put a backports package* generated from Linux 4.3-rc7 + 5 patches adding qca9377 support to ath10k.

* [http://lists.infradead.org/pipermail/ath10k/2015-November/006401.html](http://lists.infradead.org/pipermail/ath10k/2015-November/006401.html)
* [http://lists.infradead.org/pipermail/ath10k/2015-October/006324.html](http://lists.infradead.org/pipermail/ath10k/2015-October/006324.html)

I was rather hoping to create it on top of master branch of ath.git - to not loose the recent ath10k patches - but for some reason I did not mange to create a working backports - looks like there're some deps on top of -rc7 ..

*) it's here:
wget [http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2](http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2)

---

### Post by lmatiolis on 2015-11-05
Hi everyone! I'm also having the same issues on a notebook i just bought...
 
I've tried the solutions here and I'm still not being able to get my wireless to work. If somebody else got it working let me know, cause maybe I've already screwed something here when trying a lot of different solutions... I've checked the manufacture date on the bottom of my machine too and it says 2015/08, so i'm guessing mine is v2.

Anyway, just wanted to drop by and say thanks for the efforts to fix this! :)

---

### Post by rinfinity on 2015-11-06
Welcome **xbarmar**. The developer himself comes to the forum to make the QCA9377 work for us. We couldn't have asked for more. :)
**dr-cono**, maybe you should try  xbarmar's backports and let's know.

[**[COLOR=#000000]lmatiolis[/COLOR]**]("http://ubuntuforums.org/member.php?u=2008278"), have you used xbarmar's backport? xbarmar has found something wrong with the backport Jeremi31 pointed towards. Please report after using the backport in #17.
Moreover, there are four different boards in QCA9377 (Source: [http://www.wi-fi.org/product-finder-results?keywords=qca9377](http://www.wi-fi.org/product-finder-results?keywords=qca9377) )
NFA455
NFA435A
NFA435
NFA425A
A look into the windows driver installer folder in the driver CD provided with your machine would confirm which of these boards is yours. The NFA435A is labeled as QCA9377(v 1.1) and going by xbarmar's statements here and elsewhere NFA435 and NFA435A should be supported by his recent patch.

---

### Post by dr-cono on 2015-11-06
Hi everyone,

Thanks **xbarmar **and everyone else for taking the time with this.

I tried the backport and i got this
```

~ dmesg | grep 0042
 [   23.697020] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/board-pci-168c:0042:105b:e09a.bin failed with error -2

```

my kernel is 3.19.0-31-generic.

---

### Post by rinfinity on 2015-11-06
[I][B] [   23.697020] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/board-pci-168c:0042:105b:e09a.bin failed with error -2

[/B][/I]The firmware required by the driver (viz. ***board-pci-168c:0042:105b:e09a.bin***) is not present (error -2 is simple ENOENT, i.e. file not found).
****
Let's see what xbarmar and jeremy31 have to offer.

---

### Post by jeremy31 on 2015-11-06
That seems to be a normal error as the only firmware needed by the cards is a board.bin and a firmware-5.bin

I think the result of ```
dmesg | grep ath10k
``` would tell us more

---

### Post by dr-cono on 2015-11-06
Sure, here's the output of dmesg | grep ath10k
> 
[   23.341990] ath10k_pci 0000:03:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[   23.850876] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/cal-pci-0000:03:00.0.bin failed with error -2
[   23.908468] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/board-pci-168c:0042:105b:e09a.bin failed with error -2
[   23.908472] ath10k_pci 0000:03:00.0: failed to load spec board file, falling back to generic: -2
[   23.932615] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-5.bin failed with error -2
[   23.932619] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-5.bin': -2
[   23.932658] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-4.bin failed with error -2
[   23.932660] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-4.bin': -2
[   23.932695] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-3.bin failed with error -2
[   23.932696] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-3.bin': -2
[   23.932731] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-2.bin failed with error -2
[   23.932732] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-2.bin': -2
[   23.932768] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware.bin failed with error -2
[   23.932770] ath10k_pci 0000:03:00.0: could not fetch firmware (-2)
[   23.932793] ath10k_pci 0000:03:00.0: could not fetch firmware files (-2)
[   23.932815] ath10k_pci 0000:03:00.0: could not probe fw (-2)


---

### Post by jeremy31 on 2015-11-07
Strange ```
ls /lib/firmware/ath10k/QCA9377/hw1.0/
```

---

### Post by dr-cono on 2015-11-07
> 
board.bin
firmware-5.bin_WLAN.TF.1.0-00267-1
notice.txt_WLAN.TF.1.0-00267-1


maybe rename firmware-5.bin_WLAN.TF.1.0-00267-1 to firmware-5.bin?

edit: changed the name and **it worked!** thanks a lot!.. :p:p

Posting what i did to make it work: Notebook Model: Acer Aspire e5-473g.
```

sudo apt-get install build-essential linux-headers-$(uname -r) git
echo "options ath10k_core skip_otp=y" | sudo tee /etc/modprobe.d/ath10k_core.conf
wget [http://filebin.ca/2LVgpjSgiT56/backp...-11-05.tar.bz2]("http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2")
unzip [backp...-11-05.tar.bz2]("http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2")
cd backports-ath10k-2015-11-05
make defconfig-ath10k
make
sudo make install
git clone [https://github.com/kvalo/ath10k-firmware.git](https://github.com/kvalo/ath10k-firmware.git)
sudo cp -r ath10k-firmware/ath10k/ /lib/firmware/
sudo cp -r ath10k-firmware/QCA9377 /lib/firmware/ath10k/
cp firmware-5.bin_WLAN.TF.1.0-00267-1 firmware-5.bin
Reboot

```
Thanks a lot!

---

### Post by rinfinity on 2015-11-07
Ah! Finally it works. Thanks dr-cono for your patience with testing, jeremy31and xbarmar for your valuable input. Hope you'll keep on checking back this thread to help people out.
For the record, dr-cono's QCA9377 is a NFA435 according to documentation available at Acer website.

xbarmar, could you please sort out the fw naming issue?

---

### Post by mojayu on 2015-11-07
Yes!!! It woks for my Aspire E 15! Thanks!

---

### Post by rinfinity on 2015-11-07
> **mojayu said:**
> Yes!!! It woks for my Aspire E 15! Thanks!

Nice to know that it's working for  you. As there are many versions of QCA9377, it'd be of some help to the developer in further development, if you could share the wireless info.txt here. Here's how to generate  it: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

I wish to report success with a QCA9377, particulars whereof are:
[B]Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)
    Subsystem: Lite-On Communications Inc Device [11ad:0806]
[/B]
Please note the different subsystem; dr-cono's was a Foxconn:
       [B]*"Subsystem: Foxconn International, Inc. Device [105b:e09a]"*
[/B]
So, apparentely, the subsystem manufacturer/make has no bearing on the provided module backport as long as the device is:
        Qualcomm Atheros Device [168c:0042] (rev 30)

And oh! Since I made an issue of it, the machine(Acer Aspire E15 E5-573-32JT) was manufactured in September, 2015AD. ;):D

---

### Post by lmatiolis on 2015-11-07
Awesome! Mine here is working too now! :D

I had the same problem dr-cono had. After renaming firmware-5.bin_WLAN.TF.1.0-00267-1 to firmware-5.bin and rebooting it started working! 

For the record, I checked the drivers on Windows and it says it's a NFA455.

Thanks a lot guys, I can't really express in words how great this was! o/

---

### Post by rinfinity on 2015-11-07
NFA455 works? :rolleyes: The plot thickens, my dear Watson!

Can we have a look at your wirelessinfo.txt. Here's how to generate it: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
What's of great interest is the device ID and the subsystem device ID and manufacturer. This information might be of some help to xbarmar (the original developer).

For the record again, here's the manual (with board diagram) for Samsung's implementation of NFA455 called A3LNFA455 (A3L is FCC's shorthand for Samsung)
[https://fccid.io/document.php?id=2606121](https://fccid.io/document.php?id=2606121)

Aah! The only QCA9377 NFA455 with ID 168C:0042 (Rev 30)***** was made for Samsung. This means yours is a Samsung machine. Right?
In that case, this means this patch is good for (at least) all QCA9377 till the device ID is 168c:0042 (Rev 30)

* There's another one too, but it's rev 31.

[IMG]http://ibin.co/2LnmQBTf3jXY[/IMG]

---

### Post by tizo_rh on 2015-11-08
Excelent! Mine is working on Ubuntu 14.04. My laptop: Acer Aspire E5-573-5148. Based on post [http://ubuntuforums.org/showthread.php?t=2300861&page=3&p=13386625#post13386625]("http://ubuntuforums.org/showthread.php?t=2300861&page=3&p=13386625#post13386625") from dr-cono, what I did was:

```
sudo apt-get install build-essential linux-headers-$(uname -r) git
echo "options ath10k_core skip_otp=y" | sudo tee /etc/modprobe.d/ath10k_core.conf

```

In a temoporary directory (on a new Kernel installation, only repeat the following steps):

```

wget http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2
tar -vxf backports-ath-2015-11-05.tar.bz2
cd backports-ath10k-2015-11-05
make defconfig-ath10k
make
sudo make install
```

Again in the temporary directory:

```

git clone https://github.com/kvalo/ath10k-firmware.git
sudo cp -r ath10k-firmware/ath10k/ /lib/firmware/
sudo cp -r ath10k-firmware/QCA9377 /lib/firmware/ath10k/
sudo mv /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin_WLAN.TF.1.0-00267-1 /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin
```

Then reboot.

---

### Post by lmatiolis on 2015-11-08
rinfinity: Yep, my notebook is Samsung! :)

I've attached the wireless info... hope it helps!

Just for the record, I've also tried it on an Ubuntu 15.10 and it's also working.

---

### Post by erjanmx on 2015-11-09
Wow, my wifi is now working!!! 
Thanks a lot
acer e15 e5-573g ubuntu 14.04

---

### Post by tizo_rh on 2015-11-09
Mine is working, but not so well. After a while, the connection turns very slowly. If I make a ping, it lost some packets and the times are really high. I know that the router is not the problem, because other devices works good.

What I did is on post 29 [http://ubuntuforums.org/showthread.php?t=2300861&p=13387334#post13387334]("http://ubuntuforums.org/showthread.php?t=2300861&p=13387334#post13387334").

Any help is appreciated. Thanks.

JFTR: after a reboot, it works acceptably for some minutes, and then the problem appears again.

---

### Post by rinfinity on 2015-11-09
tizo_rh could u pls let us have a look at the wireless info.text?

Have you pinged "other devices" exactly when u pinged this one?
Once getting slow, does the speed return after sometime?

---

### Post by tizo_rh on 2015-11-11
rinfinity, I am sending wireless-info.txt when back at home.

I have not made pings from other devices when the problem is happening, but I have tried Internet without any problem at that time from other devices. In the laptop with the problem at that time, Internet is really slowly, or does not work at all.

I am not sure, but I think that the speed does not return until I reboot the laptop. I have even tried to deactivate Wi-Fi, and then activate it again, and the problem persist. Indeed, one of those time, my router was not seen anymore.

Thanks very much.

---

### Post by fabio-arezi on 2015-11-11
It's work for me on my Samsung Expert X30, in this sequence:

```


mkdir tmp-ath10k
cd tmp-ath10k

sudo apt-get install build-essential linux-headers-$(uname -r) git
echo "options ath10k_core skip_otp=y" | sudo tee /etc/modprobe.d/ath10k_core.conf

wget http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2
tar -vxf backports-ath-2015-11-05.tar.bz2
cd backports-ath10k-2015-11-05
make defconfig-ath10k
make
sudo make install

cd ..

git clone https://github.com/kvalo/ath10k-firmware.git
sudo cp -r ath10k-firmware/ath10k/ /lib/firmware/
sudo cp -r ath10k-firmware/QCA9377 /lib/firmware/ath10k/
sudo mv /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin_WLAN.TF.1.0-00267-1 /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin


```

thanks a lot!!

---

### Post by whizzkid-raj5 on 2015-11-11
Hello all. First of all thank you coz I had the same problem and then I came across this forum thread and from then on, after following the steps and entering the commands, wifi is working on my laptop Acer Apsire E5-573G-563K with ubuntu 14.04.3 LTS installed on it. Actually I have installed 4 OSes on my laptop. Windows 10 pro x64, ubuntu, Fedora 23 and Kali Linux 2.0.
So, now that I have got wifi working on ubuntu, can anyone please help me to get my wifi working on fedora and kali linux. I have the same wifi driver atheros 0042 (rev 30). Please anyone help.. like what changes should I make to the commands above for fedora and for kali linux. I'm new to linux but I'm an advanced level user when it comes to using computer. In Windows, I can do it all. But I have just installed these 4 Oses especially to learn linux and hacking. Please post the commands for fedora and kali. I tried YUM instead of apt-get but yum doesn't work in new fedora version so I installed yum package, switched to root user and still, the first command doesn't work i.e - 
sudo apt-get install build-essential linux-headers-$(uname -r) git

and it shows following output -  Last metadata expiration check performed 2:01:25 ago on Wed Nov 11 18:51:09 2015.
No package build-essential available.
No package linux-headers-4.2.3-300.fc23.x86_64 available.
Package git-2.5.0-1.fc23.x86_64 is already installed, skipping.
Error: Unable to find a match.

Please post the commands for fedora and kali linux. Thank you :)

---

### Post by rinfinity on 2015-11-12
whizzkid-raj5,

Right now, I'll concentrate on getting QCA9377 to work on fedora.

[U][B][SIZE=4]Analysis[/SIZE]
[/B][/U]
1. build-essential is a debian meta-package (a package of packages) that are essential for compilation and install from source. It consists of 

[LIST=1]
[*]dpkg-dev (>= 1.13.5) 
[*]g++ (>= 4:4.4.3) 
[*]gcc (>= 4:4.4.3) 
[*]libc6-dev 
[*]make 
[/LIST]
There are ways to get that (except no.1) on fedora.

2. In fedora linux-headers are called kernel-headers

So, just replace 'linux' with 'kernel', and you should be fine.

3. git is already installed, so you don't need to do anything extra.:D

[SIZE=4]_**Solutions**_[/SIZE]
[B]
Issue 1

[/B]Tthere are two ways:

a. ```
sudo dnf install make [FONT=century gothic]automake[/FONT] gcc gcc-c++ kernel-devel
```

T[FONT=book antiqua]his will install only the "essential" packages (in the spirit of build-essential"
[/FONT][FONT=book antiqua]However, if you are ok with  pulling in a lot of packages you can install_** all**_ the development tools  and libraries with the below command.[/FONT]

  b. ```
sudo dnf groupinstall "Development Tools and Libraries"
```

You can choose between a and b, but I'd recommend method a, so we can test ourselves if method a is really equivalent to build-essential.

**Issue 2**

```
sudo dnf install **kernel**-headers-$(uname -r) git
```

_[SIZE=5]Conclusion:[/SIZE]_

Replace the previous code: ```
sudo apt-get install build-essential linux-headers-$(uname -r) git 

```

with: ```
**sudo dnf install make [FONT=century gothic]automake[/FONT] gcc gcc-c++ kernel-devel kernel-headers-$(uname -r) git**
```

and proceed with other commands verbatim as the last time.

---

### Post by tizo_rh on 2015-11-12
rinfinity, here is my wireless-info.txt:

---

### Post by ganesh-udhayasankar-4 on 2015-11-13
Hi rinfinity

Here is wireless-info.txt file I own an Acer Aspire E5-573-33YS with the same network controller. Please help me out. I am a novice on Ubuntu or any Linux platforms for that matter.



########## wireless info START ##########

Report from: 13 Nov 2015 11:28 IST +0530

Booted last: 13 Nov 2015 10:57 IST +0530

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-33-generic #38~14.04.1-Ubuntu SMP Fri Nov 6 18:17:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Acer Incorporated [ALI] Device [1025:098a]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)
    Subsystem: Lite-On Communications Inc Device [11ad:0806]

##### lsusb #############################

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 005: ID 04f2:b51f Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 04ca:3015 Lite-On Technology Corp. 
Bus 001 Device 003: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 002: ID 058f:9380 Alcor Micro Corp. Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

acer_wmi               20480  0 
sparse_keymap          16384  1 acer_wmi
video                  20480  2 i915_bpo,acer_wmi
wmi                    20480  1 acer_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fd8a:1924:cddf:0:b199:e667:d7fd:851b/64 Scope:Global
          inet6 addr: fd8a:1924:cddf:0:<IP6 'eth0' [IF]>/64 Scope:Global
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:58961 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52909 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:44421867 (44.4 MB)  TX bytes:12167458 (12.1 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       779     1  0 10:57 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.110
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             202.83.21.24
    DNS:             202.83.21.28
    DNS:             192.168.1.1

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

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/ath10k_core.conf]
options ath10k_core skip_otp=y

[/etc/modprobe.d/ath10k-dkms.conf]
options ath10k_core skip_otp=1

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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

########## wireless info END ############

---

### Post by rinfinity on 2015-11-13
ganesh-udayashankar-4,

Indeed, your card is supported. Just follow the steps.

#1 Create a temporary directory

mkdir tmp-ath10k

#2 And then,
cd tmp-ath10k

#3 this is to install some necessary softwares, as we need to install from source from git repository

sudo apt-get install build-essential linux-headers-$(uname -r) git

#4
echo "options ath10k_core skip_otp=y" | sudo tee /etc/modprobe.d/ath10k_core.conf

#5 we'll download patched backports in the directory we're working from

wget [http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2](http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2)

#6 extract the downloaded file
tar -vxf backports-ath-2015-11-05.tar.bz2

#7Get into the extracted folder, and enter these commands one by one, to install the backport.

cd backports-ath10k-2015-11-05
make defconfig-ath10k
make
sudo make install

#8 Now that we've got the backport installed, we'll get the appropriate firmware files and place them in their proper location (which is: /lib/firmware)

git clone [https://github.com/kvalo/ath10k-firmware.git](https://github.com/kvalo/ath10k-firmware.git)
sudo cp -r ath10k-firmware/ath10k/ /lib/firmware/
sudo cp -r ath10k-firmware/QCA9377 /lib/firmware/ath10k/

#9 For some reasons, the firmware files are not named properly, we fix that.
sudo mv /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin_WLAN.TF.1.0-00267-1 /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin

#10 reboot.

---

### Post by whizzkid-raj5 on 2015-11-13
First of all, thank you so much, mate, for the reply and for explaining all of the commands step wise.

But, in terminal

[whizkidraj@localhost backports-ath-2015-11-05]$ make defconfig-ath10k
/--------------
| Your kernel headers are incomplete/not installed.
| Please install kernel headers, including a .config
| file or use the KLIB/KLIB_BUILD make variables to
| set the kernel to build against, e.g.
|   make KLIB=/lib/modules/3.1.7/
| to compile/install for the installed kernel 3.1.7
| (that isn't currently running.)
\--
Makefile:40: recipe for target 'defconfig-ath10k' failed
make: *** [defconfig-ath10k] Error 1

Here it shows error.
I've copied everything that I did in the terminal with the output. Please do have a look and hope we can work it out.

```
[whizkidraj@localhost ~]$ sudo dnf install make automake gcc gcc-c++
[sudo] password for whizkidraj: 
Fedora 23 - x86_64 - Updates                    215 kB/s | 6.1 MB     00:29    
Last metadata expiration check performed 0:00:16 ago on Fri Nov 13 18:22:11 2015.
Package make-1:4.0-5.1.fc23.x86_64 is already installed, skipping.
Dependencies resolved.
================================================================================
 Package                 Arch         Version               Repository     Size
================================================================================
Installing:
 autoconf                noarch       2.69-21.fc23          fedora        709 k
 automake                noarch       1.15-4.fc23           fedora        695 k
 binutils                x86_64       2.25-15.fc23          fedora        5.6 M
 cpp                     x86_64       5.1.1-4.fc23          fedora        8.5 M
 gcc                     x86_64       5.1.1-4.fc23          fedora         19 M
 gcc-c++                 x86_64       5.1.1-4.fc23          fedora         10 M
 glibc-devel             x86_64       2.22-3.fc23           fedora        909 k
 glibc-headers           x86_64       2.22-3.fc23           fedora        493 k
 isl                     x86_64       0.14-4.fc23           fedora        490 k
 kernel-headers          x86_64       4.2.5-300.fc23        updates       988 k
 libmpc                  x86_64       1.0.2-4.fc23          fedora         55 k
 libstdc++-devel         x86_64       5.1.1-4.fc23          fedora        1.6 M
 m4                      x86_64       1.4.17-8.fc23         fedora        266 k
 perl-Thread-Queue       noarch       3.07-1.fc23           updates        22 k

Transaction Summary
================================================================================
Install  14 Packages

Total download size: 50 M
Installed size: 135 M
Is this ok [y/N]: y
Downloading Packages:
(1/14): automake-1.15-4.fc23.noarch.rpm          76 kB/s | 695 kB     00:09    
(2/14): autoconf-2.69-21.fc23.noarch.rpm         73 kB/s | 709 kB     00:09    
^CThe downloaded packages were saved in cache till the next successful transaction.
You can remove cached packages by executing 'dnf clean packages'.
Terminated.
[whizkidraj@localhost ~]$ dnf clean packages
Cleaning repos: updates fedora
0 package files removed
[whizkidraj@localhost ~]$ sudo dnf install make automake gcc gcc-c++ kernel-devel
Last metadata expiration check performed 0:03:25 ago on Fri Nov 13 18:22:11 2015.
Package make-1:4.0-5.1.fc23.x86_64 is already installed, skipping.
Dependencies resolved.
================================================================================
 Package                 Arch         Version               Repository     Size
================================================================================
Installing:
 autoconf                noarch       2.69-21.fc23          fedora        709 k
 automake                noarch       1.15-4.fc23           fedora        695 k
 binutils                x86_64       2.25-15.fc23          fedora        5.6 M
 cpp                     x86_64       5.1.1-4.fc23          fedora        8.5 M
 gcc                     x86_64       5.1.1-4.fc23          fedora         19 M
 gcc-c++                 x86_64       5.1.1-4.fc23          fedora         10 M
 glibc-devel             x86_64       2.22-3.fc23           fedora        909 k
 glibc-headers           x86_64       2.22-3.fc23           fedora        493 k
 isl                     x86_64       0.14-4.fc23           fedora        490 k
 kernel-devel            x86_64       4.2.5-300.fc23        updates       9.8 M
 kernel-headers          x86_64       4.2.5-300.fc23        updates       988 k
 libmpc                  x86_64       1.0.2-4.fc23          fedora         55 k
 libstdc++-devel         x86_64       5.1.1-4.fc23          fedora        1.6 M
 m4                      x86_64       1.4.17-8.fc23         fedora        266 k
 perl-Thread-Queue       noarch       3.07-1.fc23           updates        22 k

Transaction Summary
================================================================================
Install  15 Packages

Total size: 59 M
Total download size: 58 M
Installed size: 171 M
Is this ok [y/N]: y
Downloading Packages:
[SKIPPED] automake-1.15-4.fc23.noarch.rpm: Already downloaded                  
[SKIPPED] autoconf-2.69-21.fc23.noarch.rpm: Already downloaded                 
(3/15): binutils-2.25-15.fc23.x86_64.rpm        166 kB/s | 5.6 MB     00:34    
(4/15): libmpc-1.0.2-4.fc23.x86_64.rpm           21 kB/s |  55 kB     00:02    
(5/15): m4-1.4.17-8.fc23.x86_64.rpm              53 kB/s | 266 kB     00:04    
(6/15): cpp-5.1.1-4.fc23.x86_64.rpm              86 kB/s | 8.5 MB     01:41    
(7/15): gcc-5.1.1-4.fc23.x86_64.rpm             170 kB/s |  19 MB     01:56    
(8/15): libstdc++-devel-5.1.1-4.fc23.x86_64.rpm 180 kB/s | 1.6 MB     00:09    
(9/15): glibc-devel-2.22-3.fc23.x86_64.rpm       95 kB/s | 909 kB     00:09    
(10/15): gcc-c++-5.1.1-4.fc23.x86_64.rpm        103 kB/s |  10 MB     01:39    
(11/15): isl-0.14-4.fc23.x86_64.rpm              74 kB/s | 490 kB     00:06    
(12/15): glibc-headers-2.22-3.fc23.x86_64.rpm   246 kB/s | 493 kB     00:02    
(13/15): perl-Thread-Queue-3.07-1.fc23.noarch.r 7.2 kB/s |  22 kB     00:03    
(14/15): kernel-headers-4.2.5-300.fc23.x86_64.r 9.5 kB/s | 988 kB     01:44    
(15/15): kernel-devel-4.2.5-300.fc23.x86_64.rpm 9.7 kB/s | 9.8 MB     17:15    
--------------------------------------------------------------------------------
Total                                            52 kB/s |  58 MB     18:59     
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Installing  : libmpc-1.0.2-4.fc23.x86_64                                 1/15 
  Installing  : cpp-5.1.1-4.fc23.x86_64                                    2/15 
  Installing  : kernel-headers-4.2.5-300.fc23.x86_64                       3/15 
  Installing  : glibc-headers-2.22-3.fc23.x86_64                           4/15 
  Installing  : glibc-devel-2.22-3.fc23.x86_64                             5/15 
  Installing  : perl-Thread-Queue-3.07-1.fc23.noarch                       6/15 
  Installing  : isl-0.14-4.fc23.x86_64                                     7/15 
  Installing  : libstdc++-devel-5.1.1-4.fc23.x86_64                        8/15 
  Installing  : m4-1.4.17-8.fc23.x86_64                                    9/15 
  Installing  : autoconf-2.69-21.fc23.noarch                              10/15 
  Installing  : binutils-2.25-15.fc23.x86_64                              11/15 
  Installing  : gcc-5.1.1-4.fc23.x86_64                                   12/15 
  Installing  : gcc-c++-5.1.1-4.fc23.x86_64                               13/15 
  Installing  : automake-1.15-4.fc23.noarch                               14/15 
  Installing  : kernel-devel-4.2.5-300.fc23.x86_64                        15/15 
  Verifying   : automake-1.15-4.fc23.noarch                                1/15 
  Verifying   : gcc-5.1.1-4.fc23.x86_64                                    2/15 
  Verifying   : autoconf-2.69-21.fc23.noarch                               3/15 
  Verifying   : binutils-2.25-15.fc23.x86_64                               4/15 
  Verifying   : cpp-5.1.1-4.fc23.x86_64                                    5/15 
  Verifying   : libmpc-1.0.2-4.fc23.x86_64                                 6/15 
  Verifying   : m4-1.4.17-8.fc23.x86_64                                    7/15 
  Verifying   : gcc-c++-5.1.1-4.fc23.x86_64                                8/15 
  Verifying   : kernel-devel-4.2.5-300.fc23.x86_64                         9/15 
  Verifying   : libstdc++-devel-5.1.1-4.fc23.x86_64                       10/15 
  Verifying   : glibc-devel-2.22-3.fc23.x86_64                            11/15 
  Verifying   : isl-0.14-4.fc23.x86_64                                    12/15 
  Verifying   : perl-Thread-Queue-3.07-1.fc23.noarch                      13/15 
  Verifying   : glibc-headers-2.22-3.fc23.x86_64                          14/15 
  Verifying   : kernel-headers-4.2.5-300.fc23.x86_64                      15/15 

Installed:
  autoconf.noarch 2.69-21.fc23            automake.noarch 1.15-4.fc23          
  binutils.x86_64 2.25-15.fc23            cpp.x86_64 5.1.1-4.fc23              
  gcc.x86_64 5.1.1-4.fc23                 gcc-c++.x86_64 5.1.1-4.fc23          
  glibc-devel.x86_64 2.22-3.fc23          glibc-headers.x86_64 2.22-3.fc23     
  isl.x86_64 0.14-4.fc23                  kernel-devel.x86_64 4.2.5-300.fc23   
  kernel-headers.x86_64 4.2.5-300.fc23    libmpc.x86_64 1.0.2-4.fc23           
  libstdc++-devel.x86_64 5.1.1-4.fc23     m4.x86_64 1.4.17-8.fc23              
  perl-Thread-Queue.noarch 3.07-1.fc23   

Complete!
[whizkidraj@localhost ~]$ sudo dnf install make automake gcc gcc-c++ kernel-devel kernel-headers-$(uname -r) git
[sudo] password for whizkidraj: 
Sorry, try again.
[sudo] password for whizkidraj: 
Last metadata expiration check performed 0:24:39 ago on Fri Nov 13 18:22:11 2015.
Package make-1:4.0-5.1.fc23.x86_64 is already installed, skipping.
Package automake-1.15-4.fc23.noarch is already installed, skipping.
Package gcc-5.1.1-4.fc23.x86_64 is already installed, skipping.
Package gcc-c++-5.1.1-4.fc23.x86_64 is already installed, skipping.
Package kernel-devel-4.2.5-300.fc23.x86_64 is already installed, skipping.
Package git-2.5.0-2.fc23.x86_64 is already installed, skipping.
Dependencies resolved.
================================================================================
 Package               Arch          Version                Repository     Size
================================================================================
Downgrading:
 kernel-headers        x86_64        4.2.3-300.fc23         fedora        987 k

Transaction Summary
================================================================================
Downgrade  1 Package

Total download size: 987 k
Is this ok [y/N]: y
Downloading Packages:
kernel-headers-4.2.3-300.fc23.x86_64.rpm        288 kB/s | 987 kB     00:03    
--------------------------------------------------------------------------------
Total                                           211 kB/s | 987 kB     00:04     
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Downgrading : kernel-headers-4.2.3-300.fc23.x86_64                        1/2 
  Erasing     : kernel-headers-4.2.5-300.fc23.x86_64                        2/2 
  Verifying   : kernel-headers-4.2.3-300.fc23.x86_64                        1/2 
  Verifying   : kernel-headers-4.2.5-300.fc23.x86_64                        2/2 

Downgraded:
  kernel-headers.x86_64 4.2.3-300.fc23                                          

Complete!
[whizkidraj@localhost ~]$ echo "options ath10k_core skip_otp=y" | sudo tee /etc/modprobe.d/ath10k_core.conf
options ath10k_core skip_otp=y
[whizkidraj@localhost ~]$ wget [http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2](http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2)
--2015-11-13 18:48:45--  [http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2](http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2)
Resolving filebin.ca (filebin.ca)... 23.23.121.233, 2406:da00:ff00::1717:79e9
Connecting to filebin.ca (filebin.ca)|23.23.121.233|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2666523 (2.5M) [application/x-bzip2]
Saving to: ‘backports-ath-2015-11-05.tar.bz2.1’

backports-ath-2015- 100%[=====================>]   2.54M   352KB/s   in 8.0s   

2015-11-13 18:48:54 (325 KB/s) - ‘backports-ath-2015-11-05.tar.bz2.1’ saved [2666523/2666523]

[whizkidraj@localhost ~]$ wget [http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2](http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2)
--2015-11-13 18:49:43--  [http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2](http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2)
Resolving filebin.ca (filebin.ca)... 23.23.121.233, 2406:da00:ff00::1717:79e9
Connecting to filebin.ca (filebin.ca)|23.23.121.233|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2666523 (2.5M) [application/x-bzip2]
Saving to: ‘backports-ath-2015-11-05.tar.bz2’

backports-ath-2015- 100%[=====================>]   2.54M   350KB/s   in 7.9s   

2015-11-13 18:49:51 (329 KB/s) - ‘backports-ath-2015-11-05.tar.bz2’ saved [2666523/2666523]

[whizkidraj@localhost ~]$ tar -vxf backports-ath-2015-11-05.tar.bz2
backports-ath-2015-11-05/
backports-ath-2015-11-05/Makefile.build
backports-ath-2015-11-05/Kconfig.sources
backports-ath-2015-11-05/net/
backports-ath-2015-11-05/net/Makefile
backports-ath-2015-11-05/net/mac802154/
backports-ath-2015-11-05/net/mac802154/tx.c
backports-ath-2015-11-05/net/mac802154/iface.c
backports-ath-2015-11-05/net/mac802154/driver-ops.h
backports-ath-2015-11-05/net/mac802154/trace.c
backports-ath-2015-11-05/net/mac802154/llsec.h
backports-ath-2015-11-05/net/mac802154/rx.c
backports-ath-2015-11-05/net/mac802154/Makefile
backports-ath-2015-11-05/net/mac802154/trace.h
backports-ath-2015-11-05/net/mac802154/llsec.c
backports-ath-2015-11-05/net/mac802154/ieee802154_i.h
backports-ath-2015-11-05/net/mac802154/cfg.h
backports-ath-2015-11-05/net/mac802154/util.c
backports-ath-2015-11-05/net/mac802154/mib.c
backports-ath-2015-11-05/net/mac802154/cfg.c
backports-ath-2015-11-05/net/mac802154/mac_cmd.c
backports-ath-2015-11-05/net/mac802154/main.c
backports-ath-2015-11-05/net/mac802154/Kconfig
backports-ath-2015-11-05/net/mac80211/
backports-ath-2015-11-05/net/mac80211/ieee80211_i.h
backports-ath-2015-11-05/net/mac80211/spectmgmt.c
backports-ath-2015-11-05/net/mac80211/tx.c
backports-ath-2015-11-05/net/mac80211/tkip.h
backports-ath-2015-11-05/net/mac80211/iface.c
backports-ath-2015-11-05/net/mac80211/offchannel.c
backports-ath-2015-11-05/net/mac80211/driver-ops.h
backports-ath-2015-11-05/net/mac80211/trace.c
backports-ath-2015-11-05/net/mac80211/aes_gmac.h
backports-ath-2015-11-05/net/mac80211/rc80211_minstrel_ht_debugfs.c
backports-ath-2015-11-05/net/mac80211/led.c
backports-ath-2015-11-05/net/mac80211/sta_info.h
backports-ath-2015-11-05/net/mac80211/rate.c
backports-ath-2015-11-05/net/mac80211/debugfs_netdev.h
backports-ath-2015-11-05/net/mac80211/rx.c
backports-ath-2015-11-05/net/mac80211/aes_ccm.c
backports-ath-2015-11-05/net/mac80211/debugfs.c
backports-ath-2015-11-05/net/mac80211/Makefile
backports-ath-2015-11-05/net/mac80211/trace_msg.h
backports-ath-2015-11-05/net/mac80211/aes_cmac.h
backports-ath-2015-11-05/net/mac80211/led.h
backports-ath-2015-11-05/net/mac80211/debugfs_sta.c
backports-ath-2015-11-05/net/mac80211/aes_gcm.h
backports-ath-2015-11-05/net/mac80211/tkip.c
backports-ath-2015-11-05/net/mac80211/rc80211_minstrel_ht.c
backports-ath-2015-11-05/net/mac80211/trace.h
backports-ath-2015-11-05/net/mac80211/ibss.c
backports-ath-2015-11-05/net/mac80211/aes_cmac.c
backports-ath-2015-11-05/net/mac80211/wep.c
backports-ath-2015-11-05/net/mac80211/debug.h
backports-ath-2015-11-05/net/mac80211/rc80211_minstrel_debugfs.c
backports-ath-2015-11-05/net/mac80211/debugfs_netdev.c
backports-ath-2015-11-05/net/mac80211/scan.c
backports-ath-2015-11-05/net/mac80211/mesh_pathtbl.c
backports-ath-2015-11-05/net/mac80211/mesh.h
backports-ath-2015-11-05/net/mac80211/driver-ops.c
backports-ath-2015-11-05/net/mac80211/debugfs_key.c
backports-ath-2015-11-05/net/mac80211/ht.c
backports-ath-2015-11-05/net/mac80211/michael.h
backports-ath-2015-11-05/net/mac80211/debugfs_key.h
backports-ath-2015-11-05/net/mac80211/rc80211_minstrel_ht.h
backports-ath-2015-11-05/net/mac80211/mlme.c
backports-ath-2015-11-05/net/mac80211/status.c
backports-ath-2015-11-05/net/mac80211/tdls.c
backports-ath-2015-11-05/net/mac80211/wpa.h
backports-ath-2015-11-05/net/mac80211/mesh_sync.c
backports-ath-2015-11-05/net/mac80211/cfg.h
backports-ath-2015-11-05/net/mac80211/rc80211_minstrel.c
backports-ath-2015-11-05/net/mac80211/util.c
backports-ath-2015-11-05/net/mac80211/vht.c
backports-ath-2015-11-05/net/mac80211/pm.c
backports-ath-2015-11-05/net/mac80211/mesh.c
backports-ath-2015-11-05/net/mac80211/ethtool.c
backports-ath-2015-11-05/net/mac80211/mesh_plink.c
backports-ath-2015-11-05/net/mac80211/aes_gmac.c
backports-ath-2015-11-05/net/mac80211/event.c
backports-ath-2015-11-05/net/mac80211/michael.c
backports-ath-2015-11-05/net/mac80211/cfg.c
backports-ath-2015-11-05/net/mac80211/agg-tx.c
backports-ath-2015-11-05/net/mac80211/key.h
backports-ath-2015-11-05/net/mac80211/key.c
backports-ath-2015-11-05/net/mac80211/chan.c
backports-ath-2015-11-05/net/mac80211/debugfs.h
backports-ath-2015-11-05/net/mac80211/aes_ccm.h
backports-ath-2015-11-05/net/mac80211/wep.h
backports-ath-2015-11-05/net/mac80211/wme.h
backports-ath-2015-11-05/net/mac80211/wme.c
backports-ath-2015-11-05/net/mac80211/debugfs_sta.h
backports-ath-2015-11-05/net/mac80211/rc80211_minstrel.h
backports-ath-2015-11-05/net/mac80211/mesh_ps.c
backports-ath-2015-11-05/net/mac80211/agg-rx.c
backports-ath-2015-11-05/net/mac80211/mesh_hwmp.c
backports-ath-2015-11-05/net/mac80211/rate.h
backports-ath-2015-11-05/net/mac80211/sta_info.c
backports-ath-2015-11-05/net/mac80211/ocb.c
backports-ath-2015-11-05/net/mac80211/aes_gcm.c
backports-ath-2015-11-05/net/mac80211/main.c
backports-ath-2015-11-05/net/mac80211/Kconfig
backports-ath-2015-11-05/net/mac80211/wpa.c
backports-ath-2015-11-05/net/nfc/
backports-ath-2015-11-05/net/nfc/llcp_sock.c
backports-ath-2015-11-05/net/nfc/core.c
backports-ath-2015-11-05/net/nfc/Makefile
backports-ath-2015-11-05/net/nfc/nci/
backports-ath-2015-11-05/net/nfc/nci/spi.c
backports-ath-2015-11-05/net/nfc/nci/rsp.c
backports-ath-2015-11-05/net/nfc/nci/core.c
backports-ath-2015-11-05/net/nfc/nci/Makefile
backports-ath-2015-11-05/net/nfc/nci/data.c
backports-ath-2015-11-05/net/nfc/nci/hci.c
backports-ath-2015-11-05/net/nfc/nci/lib.c
backports-ath-2015-11-05/net/nfc/nci/ntf.c
backports-ath-2015-11-05/net/nfc/nci/uart.c
backports-ath-2015-11-05/net/nfc/nci/Kconfig
backports-ath-2015-11-05/net/nfc/netlink.c
backports-ath-2015-11-05/net/nfc/rawsock.c
backports-ath-2015-11-05/net/nfc/digital_core.c
backports-ath-2015-11-05/net/nfc/af_nfc.c
backports-ath-2015-11-05/net/nfc/llcp.h
backports-ath-2015-11-05/net/nfc/digital.h
backports-ath-2015-11-05/net/nfc/digital_technology.c
backports-ath-2015-11-05/net/nfc/llcp_commands.c
backports-ath-2015-11-05/net/nfc/digital_dep.c
backports-ath-2015-11-05/net/nfc/nfc.h
backports-ath-2015-11-05/net/nfc/llcp_core.c
backports-ath-2015-11-05/net/nfc/Kconfig
backports-ath-2015-11-05/net/nfc/hci/
backports-ath-2015-11-05/net/nfc/hci/llc_shdlc.c
backports-ath-2015-11-05/net/nfc/hci/core.c
backports-ath-2015-11-05/net/nfc/hci/Makefile
backports-ath-2015-11-05/net/nfc/hci/command.c
backports-ath-2015-11-05/net/nfc/hci/llc.h
backports-ath-2015-11-05/net/nfc/hci/llc_nop.c
backports-ath-2015-11-05/net/nfc/hci/hci.h
backports-ath-2015-11-05/net/nfc/hci/hcp.c
backports-ath-2015-11-05/net/nfc/hci/llc.c
backports-ath-2015-11-05/net/nfc/hci/Kconfig
backports-ath-2015-11-05/net/ieee802154/
backports-ath-2015-11-05/net/ieee802154/nl_policy.c
backports-ath-2015-11-05/net/ieee802154/trace.c
backports-ath-2015-11-05/net/ieee802154/header_ops.c
backports-ath-2015-11-05/net/ieee802154/core.c
backports-ath-2015-11-05/net/ieee802154/nl802154.c
backports-ath-2015-11-05/net/ieee802154/Makefile
backports-ath-2015-11-05/net/ieee802154/nl802154.h
backports-ath-2015-11-05/net/ieee802154/netlink.c
backports-ath-2015-11-05/net/ieee802154/trace.h
backports-ath-2015-11-05/net/ieee802154/nl-mac.c
backports-ath-2015-11-05/net/ieee802154/nl-phy.c
backports-ath-2015-11-05/net/ieee802154/socket.c
backports-ath-2015-11-05/net/ieee802154/rdev-ops.h
backports-ath-2015-11-05/net/ieee802154/core.h
backports-ath-2015-11-05/net/ieee802154/6lowpan/
backports-ath-2015-11-05/net/ieee802154/6lowpan/tx.c
backports-ath-2015-11-05/net/ieee802154/6lowpan/reassembly.c
backports-ath-2015-11-05/net/ieee802154/6lowpan/rx.c
backports-ath-2015-11-05/net/ieee802154/6lowpan/core.c
backports-ath-2015-11-05/net/ieee802154/6lowpan/Makefile
backports-ath-2015-11-05/net/ieee802154/6lowpan/6lowpan_i.h
backports-ath-2015-11-05/net/ieee802154/6lowpan/Kconfig
backports-ath-2015-11-05/net/ieee802154/sysfs.h
backports-ath-2015-11-05/net/ieee802154/sysfs.c
backports-ath-2015-11-05/net/ieee802154/ieee802154.h
backports-ath-2015-11-05/net/ieee802154/Kconfig
backports-ath-2015-11-05/net/wireless/
backports-ath-2015-11-05/net/wireless/db.txt
backports-ath-2015-11-05/net/wireless/regdb.h
backports-ath-2015-11-05/net/wireless/lib80211_crypt_tkip.c
backports-ath-2015-11-05/net/wireless/trace.c
backports-ath-2015-11-05/net/wireless/nl80211.c
backports-ath-2015-11-05/net/wireless/wext-compat.c
backports-ath-2015-11-05/net/wireless/wext-proc.c
backports-ath-2015-11-05/net/wireless/debugfs.c
backports-ath-2015-11-05/net/wireless/core.c
backports-ath-2015-11-05/net/wireless/.gitignore
backports-ath-2015-11-05/net/wireless/Makefile
backports-ath-2015-11-05/net/wireless/lib80211_crypt_ccmp.c
backports-ath-2015-11-05/net/wireless/genregdb.awk
backports-ath-2015-11-05/net/wireless/wext-spy.c
backports-ath-2015-11-05/net/wireless/trace.h
backports-ath-2015-11-05/net/wireless/ibss.c
backports-ath-2015-11-05/net/wireless/wext-compat.h
backports-ath-2015-11-05/net/wireless/wext-priv.c
backports-ath-2015-11-05/net/wireless/scan.c
backports-ath-2015-11-05/net/wireless/nl80211.h
backports-ath-2015-11-05/net/wireless/rdev-ops.h
backports-ath-2015-11-05/net/wireless/wext-core.c
backports-ath-2015-11-05/net/wireless/mlme.c
backports-ath-2015-11-05/net/wireless/wext-sme.c
backports-ath-2015-11-05/net/wireless/ap.c
backports-ath-2015-11-05/net/wireless/core.h
backports-ath-2015-11-05/net/wireless/util.c
backports-ath-2015-11-05/net/wireless/sysfs.h
backports-ath-2015-11-05/net/wireless/mesh.c
backports-ath-2015-11-05/net/wireless/sysfs.c
backports-ath-2015-11-05/net/wireless/ethtool.c
backports-ath-2015-11-05/net/wireless/lib80211.c
backports-ath-2015-11-05/net/wireless/reg.h
backports-ath-2015-11-05/net/wireless/chan.c
backports-ath-2015-11-05/net/wireless/reg.c
backports-ath-2015-11-05/net/wireless/debugfs.h
backports-ath-2015-11-05/net/wireless/lib80211_crypt_wep.c
backports-ath-2015-11-05/net/wireless/ocb.c
backports-ath-2015-11-05/net/wireless/radiotap.c
backports-ath-2015-11-05/net/wireless/sme.c
backports-ath-2015-11-05/net/wireless/Kconfig
backports-ath-2015-11-05/net/bluetooth/
backports-ath-2015-11-05/net/bluetooth/6lowpan.c
backports-ath-2015-11-05/net/bluetooth/selftest.c
backports-ath-2015-11-05/net/bluetooth/selftest.h
backports-ath-2015-11-05/net/bluetooth/mgmt.c
backports-ath-2015-11-05/net/bluetooth/ecc.c
backports-ath-2015-11-05/net/bluetooth/a2mp.h
backports-ath-2015-11-05/net/bluetooth/Makefile
backports-ath-2015-11-05/net/bluetooth/hci_event.c
backports-ath-2015-11-05/net/bluetooth/hidp/
backports-ath-2015-11-05/net/bluetooth/hidp/core.c
backports-ath-2015-11-05/net/bluetooth/hidp/Makefile
backports-ath-2015-11-05/net/bluetooth/hidp/hidp.h
backports-ath-2015-11-05/net/bluetooth/hidp/sock.c
backports-ath-2015-11-05/net/bluetooth/hidp/Kconfig
backports-ath-2015-11-05/net/bluetooth/ecc.h
backports-ath-2015-11-05/net/bluetooth/bnep/
backports-ath-2015-11-05/net/bluetooth/bnep/core.c
backports-ath-2015-11-05/net/bluetooth/bnep/Makefile
backports-ath-2015-11-05/net/bluetooth/bnep/netdev.c
backports-ath-2015-11-05/net/bluetooth/bnep/sock.c
backports-ath-2015-11-05/net/bluetooth/bnep/bnep.h
backports-ath-2015-11-05/net/bluetooth/bnep/Kconfig
backports-ath-2015-11-05/net/bluetooth/smp.h
backports-ath-2015-11-05/net/bluetooth/smp.c
backports-ath-2015-11-05/net/bluetooth/hci_debugfs.h
backports-ath-2015-11-05/net/bluetooth/l2cap_core.c
backports-ath-2015-11-05/net/bluetooth/af_bluetooth.c
backports-ath-2015-11-05/net/bluetooth/amp.h
backports-ath-2015-11-05/net/bluetooth/hci_debugfs.c
backports-ath-2015-11-05/net/bluetooth/amp.c
backports-ath-2015-11-05/net/bluetooth/hci_request.h
backports-ath-2015-11-05/net/bluetooth/hci_request.c
backports-ath-2015-11-05/net/bluetooth/hci_sock.c
backports-ath-2015-11-05/net/bluetooth/sco.c
backports-ath-2015-11-05/net/bluetooth/mgmt_util.c
backports-ath-2015-11-05/net/bluetooth/rfcomm/
backports-ath-2015-11-05/net/bluetooth/rfcomm/core.c
backports-ath-2015-11-05/net/bluetooth/rfcomm/Makefile
backports-ath-2015-11-05/net/bluetooth/rfcomm/tty.c
backports-ath-2015-11-05/net/bluetooth/rfcomm/sock.c
backports-ath-2015-11-05/net/bluetooth/rfcomm/Kconfig
backports-ath-2015-11-05/net/bluetooth/hci_sysfs.c
backports-ath-2015-11-05/net/bluetooth/mgmt_util.h
backports-ath-2015-11-05/net/bluetooth/lib.c
backports-ath-2015-11-05/net/bluetooth/a2mp.c
backports-ath-2015-11-05/net/bluetooth/l2cap_sock.c
backports-ath-2015-11-05/net/bluetooth/hci_conn.c
backports-ath-2015-11-05/net/bluetooth/cmtp/
backports-ath-2015-11-05/net/bluetooth/cmtp/core.c
backports-ath-2015-11-05/net/bluetooth/cmtp/Makefile
backports-ath-2015-11-05/net/bluetooth/cmtp/cmtp.h
backports-ath-2015-11-05/net/bluetooth/cmtp/capi.c
backports-ath-2015-11-05/net/bluetooth/cmtp/sock.c
backports-ath-2015-11-05/net/bluetooth/cmtp/Kconfig
backports-ath-2015-11-05/net/bluetooth/hci_core.c
backports-ath-2015-11-05/net/bluetooth/Kconfig
backports-ath-2015-11-05/net/Kconfig
backports-ath-2015-11-05/.gitignore
backports-ath-2015-11-05/Makefile
backports-ath-2015-11-05/compat/
backports-ath-2015-11-05/compat/backport-3.12.c
backports-ath-2015-11-05/compat/backport-3.19.c
backports-ath-2015-11-05/compat/backport-3.2.c
backports-ath-2015-11-05/compat/Makefile
backports-ath-2015-11-05/compat/hid-ids.h
backports-ath-2015-11-05/compat/backport-3.13.c
backports-ath-2015-11-05/compat/backport-3.18.c
backports-ath-2015-11-05/compat/backport-4.0.c
backports-ath-2015-11-05/compat/backport-3.17.c
backports-ath-2015-11-05/compat/backport-3.10.c
backports-ath-2015-11-05/compat/compat-3.8.c
backports-ath-2015-11-05/compat/backport-3.14.c
backports-ath-2015-11-05/compat/compat-3.6.c
backports-ath-2015-11-05/compat/crypto-ccm.c
backports-ath-2015-11-05/compat/backport-4.3.c
backports-ath-2015-11-05/compat/user_namespace.c
backports-ath-2015-11-05/compat/dma-shared-helpers.c
backports-ath-2015-11-05/compat/backport-4.2.c
backports-ath-2015-11-05/compat/backport-3.15.c
backports-ath-2015-11-05/compat/compat-3.4.c
backports-ath-2015-11-05/compat/compat-3.5.c
backports-ath-2015-11-05/compat/compat-3.1.c
backports-ath-2015-11-05/compat/backport-4.1.c
backports-ath-2015-11-05/compat/compat-3.7.c
backports-ath-2015-11-05/compat/compat-3.0.c
backports-ath-2015-11-05/compat/compat-3.3.c
backports-ath-2015-11-05/compat/main.c
backports-ath-2015-11-05/compat/backports.h
backports-ath-2015-11-05/compat/Kconfig
backports-ath-2015-11-05/compat/compat-3.9.c
backports-ath-2015-11-05/compat/lib-rhashtable.c
backports-ath-2015-11-05/kconf/
backports-ath-2015-11-05/kconf/mconf.c
backports-ath-2015-11-05/kconf/lxdialog/
backports-ath-2015-11-05/kconf/lxdialog/check-lxdialog.sh
backports-ath-2015-11-05/kconf/lxdialog/inputbox.c
backports-ath-2015-11-05/kconf/lxdialog/yesno.c
backports-ath-2015-11-05/kconf/lxdialog/dialog.h
backports-ath-2015-11-05/kconf/lxdialog/textbox.c
backports-ath-2015-11-05/kconf/lxdialog/checklist.c
backports-ath-2015-11-05/kconf/lxdialog/util.c
backports-ath-2015-11-05/kconf/lxdialog/menubox.c
backports-ath-2015-11-05/kconf/expr.c
backports-ath-2015-11-05/kconf/menu.c
backports-ath-2015-11-05/kconf/Makefile
backports-ath-2015-11-05/kconf/zconf.tab.c
backports-ath-2015-11-05/kconf/zconf.hash.c
backports-ath-2015-11-05/kconf/conf.c
backports-ath-2015-11-05/kconf/util.c
backports-ath-2015-11-05/kconf/symbol.c
backports-ath-2015-11-05/kconf/lkc_proto.h
backports-ath-2015-11-05/kconf/zconf.lex.c
backports-ath-2015-11-05/kconf/expr.h
backports-ath-2015-11-05/kconf/list.h
backports-ath-2015-11-05/kconf/lkc.h
backports-ath-2015-11-05/kconf/confdata.c
backports-ath-2015-11-05/Makefile.kernel
backports-ath-2015-11-05/versions
backports-ath-2015-11-05/MAINTAINERS
backports-ath-2015-11-05/Kconfig.package.hacks
backports-ath-2015-11-05/include/
backports-ath-2015-11-05/include/media/
backports-ath-2015-11-05/include/media/v4l2-fh.h
backports-ath-2015-11-05/include/media/videobuf2-memops.h
backports-ath-2015-11-05/include/media/tea575x.h
backports-ath-2015-11-05/include/media/v4l2-dev.h
backports-ath-2015-11-05/include/media/smiapp.h
backports-ath-2015-11-05/include/media/ir-rx51.h
backports-ath-2015-11-05/include/media/s5p_hdmi.h
backports-ath-2015-11-05/include/media/soc_camera.h
backports-ath-2015-11-05/include/media/tvp514x.h
backports-ath-2015-11-05/include/media/atmel-isi.h
backports-ath-2015-11-05/include/media/mt9v022.h
backports-ath-2015-11-05/include/media/adv7604.h
backports-ath-2015-11-05/include/media/adv7343.h
backports-ath-2015-11-05/include/media/sr030pc30.h
backports-ath-2015-11-05/include/media/tvp7002.h
backports-ath-2015-11-05/include/media/ir-kbd-i2c.h
backports-ath-2015-11-05/include/media/adv7511.h
backports-ath-2015-11-05/include/media/omap1_camera.h
backports-ath-2015-11-05/include/media/noon010pc30.h
backports-ath-2015-11-05/include/media/gpio-ir-recv.h
backports-ath-2015-11-05/include/media/tvp5150.h
backports-ath-2015-11-05/include/media/ov2659.h
backports-ath-2015-11-05/include/media/s5k6aa.h
backports-ath-2015-11-05/include/media/mt9t001.h
backports-ath-2015-11-05/include/media/sh_mobile_csi2.h
backports-ath-2015-11-05/include/media/tuner.h
backports-ath-2015-11-05/include/media/saa7127.h
backports-ath-2015-11-05/include/media/saa7146.h
backports-ath-2015-11-05/include/media/mt9t112.h
backports-ath-2015-11-05/include/media/adv7393.h
backports-ath-2015-11-05/include/media/exynos-fimc.h
backports-ath-2015-11-05/include/media/saa7146_vv.h
backports-ath-2015-11-05/include/media/s5k4ecgx.h
backports-ath-2015-11-05/include/media/si4713.h
backports-ath-2015-11-05/include/media/upd64083.h
backports-ath-2015-11-05/include/media/v4l2-mediabus.h
backports-ath-2015-11-05/include/media/media-device.h
backports-ath-2015-11-05/include/media/v4l2-clk.h
backports-ath-2015-11-05/include/media/tveeprom.h
backports-ath-2015-11-05/include/media/videobuf2-dvb.h
backports-ath-2015-11-05/include/media/tvaudio.h
backports-ath-2015-11-05/include/media/sii9234.h
backports-ath-2015-11-05/include/media/cx25840.h
backports-ath-2015-11-05/include/media/rc-map.h
backports-ath-2015-11-05/include/media/videobuf-dma-contig.h
backports-ath-2015-11-05/include/media/adv7842.h
backports-ath-2015-11-05/include/media/videobuf2-core.h
backports-ath-2015-11-05/include/media/davinci/
backports-ath-2015-11-05/include/media/davinci/ccdc_types.h
backports-ath-2015-11-05/include/media/davinci/isif.h
backports-ath-2015-11-05/include/media/davinci/dm644x_ccdc.h
backports-ath-2015-11-05/include/media/davinci/vpbe_display.h
backports-ath-2015-11-05/include/media/davinci/dm355_ccdc.h
backports-ath-2015-11-05/include/media/davinci/vpbe.h
backports-ath-2015-11-05/include/media/davinci/vpbe_types.h
backports-ath-2015-11-05/include/media/davinci/vpbe_osd.h
backports-ath-2015-11-05/include/media/davinci/vpbe_venc.h
backports-ath-2015-11-05/include/media/davinci/vpif_types.h
backports-ath-2015-11-05/include/media/davinci/vpss.h
backports-ath-2015-11-05/include/media/davinci/vpfe_capture.h
backports-ath-2015-11-05/include/media/davinci/vpfe_types.h
backports-ath-2015-11-05/include/media/mmp-camera.h
backports-ath-2015-11-05/include/media/mt9v011.h
backports-ath-2015-11-05/include/media/videobuf-dvb.h
backports-ath-2015-11-05/include/media/omap4iss.h
backports-ath-2015-11-05/include/media/upd64031a.h
backports-ath-2015-11-05/include/media/ov9650.h
backports-ath-2015-11-05/include/media/ov7670.h
backports-ath-2015-11-05/include/media/msp3400.h
backports-ath-2015-11-05/include/media/videobuf2-dma-sg.h
backports-ath-2015-11-05/include/media/s5c73m3.h
backports-ath-2015-11-05/include/media/videobuf-vmalloc.h
backports-ath-2015-11-05/include/media/ak881x.h
backports-ath-2015-11-05/include/media/as3645a.h
backports-ath-2015-11-05/include/media/saa6588.h
backports-ath-2015-11-05/include/media/si476x.h
backports-ath-2015-11-05/include/media/tw9910.h
backports-ath-2015-11-05/include/media/cs5345.h
backports-ath-2015-11-05/include/media/timb_video.h
backports-ath-2015-11-05/include/media/videobuf-dma-sg.h
backports-ath-2015-11-05/include/media/adv7183.h
backports-ath-2015-11-05/include/media/mt9m032.h
backports-ath-2015-11-05/include/media/m52790.h
backports-ath-2015-11-05/include/media/tc358743.h
backports-ath-2015-11-05/include/media/v4l2-subdev.h
backports-ath-2015-11-05/include/media/rj54n1cb0c.h
backports-ath-2015-11-05/include/media/uda1342.h
backports-ath-2015-11-05/include/media/v4l2-common.h
backports-ath-2015-11-05/include/media/rc-core.h
backports-ath-2015-11-05/include/media/sh_mobile_ceu.h
backports-ath-2015-11-05/include/media/soc_mediabus.h
backports-ath-2015-11-05/include/media/mt9p031.h
backports-ath-2015-11-05/include/media/ad9389b.h
backports-ath-2015-11-05/include/media/videobuf-core.h
backports-ath-2015-11-05/include/media/lirc.h
backports-ath-2015-11-05/include/media/v4l2-flash-led-class.h
backports-ath-2015-11-05/include/media/bt819.h
backports-ath-2015-11-05/include/media/s3c_camif.h
backports-ath-2015-11-05/include/media/lm3646.h
backports-ath-2015-11-05/include/media/media-devnode.h
backports-ath-2015-11-05/include/media/v4l2-async.h
backports-ath-2015-11-05/include/media/v4l2-image-sizes.h
backports-ath-2015-11-05/include/media/wm8775.h
backports-ath-2015-11-05/include/media/tuner-types.h
backports-ath-2015-11-05/include/media/blackfin/
backports-ath-2015-11-05/include/media/blackfin/ppi.h
backports-ath-2015-11-05/include/media/blackfin/bfin_capture.h
backports-ath-2015-11-05/include/media/videobuf2-vmalloc.h
backports-ath-2015-11-05/include/media/timb_radio.h
backports-ath-2015-11-05/include/media/ov772x.h
backports-ath-2015-11-05/include/media/m5mols.h
backports-ath-2015-11-05/include/media/v4l2-device.h
backports-ath-2015-11-05/include/media/saa7115.h
backports-ath-2015-11-05/include/media/soc_camera_platform.h
backports-ath-2015-11-05/include/media/v4l2-dv-timings.h
backports-ath-2015-11-05/include/media/lm3560.h
backports-ath-2015-11-05/include/media/v4l2-mem2mem.h
backports-ath-2015-11-05/include/media/v4l2-of.h
backports-ath-2015-11-05/include/media/v4l2-event.h
backports-ath-2015-11-05/include/media/videobuf2-dma-contig.h
backports-ath-2015-11-05/include/media/ths7303.h
backports-ath-2015-11-05/include/media/media-entity.h
backports-ath-2015-11-05/include/media/lirc_dev.h
backports-ath-2015-11-05/include/media/cs53l32a.h
backports-ath-2015-11-05/include/media/v4l2-ctrls.h
backports-ath-2015-11-05/include/media/i2c-addr.h
backports-ath-2015-11-05/include/media/sh_vou.h
backports-ath-2015-11-05/include/media/v4l2-ioctl.h
backports-ath-2015-11-05/include/media/cx2341x.h
backports-ath-2015-11-05/include/media/adp1653.h
backports-ath-2015-11-05/include/media/mt9v032.h
backports-ath-2015-11-05/include/net/
backports-ath-2015-11-05/include/net/netns/
backports-ath-2015-11-05/include/net/netns/ieee802154_6lowpan.h
backports-ath-2015-11-05/include/net/regulatory.h
backports-ath-2015-11-05/include/net/nl802154.h
backports-ath-2015-11-05/include/net/ieee80211_radiotap.h
backports-ath-2015-11-05/include/net/mac802154.h
backports-ath-2015-11-05/include/net/lib80211.h
backports-ath-2015-11-05/include/net/nfc/
backports-ath-2015-11-05/include/net/nfc/nci.h
backports-ath-2015-11-05/include/net/nfc/llc.h
backports-ath-2015-11-05/include/net/nfc/digital.h
backports-ath-2015-11-05/include/net/nfc/hci.h
backports-ath-2015-11-05/include/net/nfc/nfc.h
backports-ath-2015-11-05/include/net/nfc/nci_core.h
backports-ath-2015-11-05/include/net/mac80211.h
backports-ath-2015-11-05/include/net/cfg80211.h
backports-ath-2015-11-05/include/net/cfg80211-wext.h
backports-ath-2015-11-05/include/net/ieee802154_netdev.h
backports-ath-2015-11-05/include/net/af_ieee802154.h
backports-ath-2015-11-05/include/net/bluetooth/
backports-ath-2015-11-05/include/net/bluetooth/hci_mon.h
backports-ath-2015-11-05/include/net/bluetooth/hci_core.h
backports-ath-2015-11-05/include/net/bluetooth/bluetooth.h
backports-ath-2015-11-05/include/net/bluetooth/l2cap.h
backports-ath-2015-11-05/include/net/bluetooth/rfcomm.h
backports-ath-2015-11-05/include/net/bluetooth/hci_sock.h
backports-ath-2015-11-05/include/net/bluetooth/mgmt.h
backports-ath-2015-11-05/include/net/bluetooth/hci.h
backports-ath-2015-11-05/include/net/bluetooth/sco.h
backports-ath-2015-11-05/include/net/6lowpan.h
backports-ath-2015-11-05/include/linux/
backports-ath-2015-11-05/include/linux/rhashtable.h
backports-ath-2015-11-05/include/linux/ath9k_platform.h
backports-ath-2015-11-05/include/linux/nl802154.h
backports-ath-2015-11-05/include/linux/platform_data/
backports-ath-2015-11-05/include/linux/platform_data/camera-rcar.h
backports-ath-2015-11-05/include/linux/platform_data/lp8755.h
backports-ath-2015-11-05/include/linux/platform_data/brcmfmac-sdio.h
backports-ath-2015-11-05/include/linux/platform_data/net-cw1200.h
backports-ath-2015-11-05/include/linux/platform_data/pn544.h
backports-ath-2015-11-05/include/linux/mpls.h
backports-ath-2015-11-05/include/linux/regulator/
backports-ath-2015-11-05/include/linux/regulator/ab8500.h
backports-ath-2015-11-05/include/linux/regulator/tps6507x.h
backports-ath-2015-11-05/include/linux/regulator/db8500-prcmu.h
backports-ath-2015-11-05/include/linux/regulator/pfuze100.h
backports-ath-2015-11-05/include/linux/regulator/act8865.h
backports-ath-2015-11-05/include/linux/regulator/userspace-consumer.h
backports-ath-2015-11-05/include/linux/regulator/max8952.h
backports-ath-2015-11-05/include/linux/regulator/gpio-regulator.h
backports-ath-2015-11-05/include/linux/regulator/max8649.h
backports-ath-2015-11-05/include/linux/regulator/max8660.h
backports-ath-2015-11-05/include/linux/regulator/lp3971.h
backports-ath-2015-11-05/include/linux/regulator/tps51632-regulator.h
backports-ath-2015-11-05/include/linux/regulator/tps62360.h
backports-ath-2015-11-05/include/linux/regulator/max8973-regulator.h
backports-ath-2015-11-05/include/linux/regulator/fan53555.h
backports-ath-2015-11-05/include/linux/regulator/max1586.h
backports-ath-2015-11-05/include/linux/regulator/lp872x.h
backports-ath-2015-11-05/include/linux/regulator/lp3972.h
backports-ath-2015-11-05/include/linux/pci_ids.h
backports-ath-2015-11-05/include/linux/videodev2.h
backports-ath-2015-11-05/include/linux/usb/
backports-ath-2015-11-05/include/linux/usb/usbnet.h
backports-ath-2015-11-05/include/linux/usb/rndis_host.h
backports-ath-2015-11-05/include/linux/usb/cdc_ncm.h
backports-ath-2015-11-05/include/linux/usb/cdc-wdm.h
backports-ath-2015-11-05/include/linux/backport-rhashtable.h
backports-ath-2015-11-05/include/linux/rndis.h
backports-ath-2015-11-05/include/linux/bcm47xx_wdt.h
backports-ath-2015-11-05/include/linux/ieee80211.h
backports-ath-2015-11-05/include/linux/wl12xx.h
backports-ath-2015-11-05/include/linux/unaligned/
backports-ath-2015-11-05/include/linux/unaligned/le_memmove.h
backports-ath-2015-11-05/include/linux/unaligned/packed_struct.h
backports-ath-2015-11-05/include/linux/unaligned/le_struct.h
backports-ath-2015-11-05/include/linux/unaligned/be_memmove.h
backports-ath-2015-11-05/include/linux/unaligned/le_byteshift.h
backports-ath-2015-11-05/include/linux/unaligned/generic.h
backports-ath-2015-11-05/include/linux/unaligned/memmove.h
backports-ath-2015-11-05/include/linux/unaligned/access_ok.h
backports-ath-2015-11-05/include/linux/unaligned/be_struct.h
backports-ath-2015-11-05/include/linux/unaligned/be_byteshift.h
backports-ath-2015-11-05/include/linux/fixp-arith.h
backports-ath-2015-11-05/include/linux/spi/
backports-ath-2015-11-05/include/linux/spi/at86rf230.h
backports-ath-2015-11-05/include/linux/spi/libertas_spi.h
backports-ath-2015-11-05/include/linux/mmc/
backports-ath-2015-11-05/include/linux/mmc/sdio_ids.h
backports-ath-2015-11-05/include/linux/wireless.h
backports-ath-2015-11-05/include/linux/hashtable.h
backports-ath-2015-11-05/include/uapi/
backports-ath-2015-11-05/include/uapi/linux/
backports-ath-2015-11-05/include/uapi/linux/mpls.h
backports-ath-2015-11-05/include/uapi/linux/v4l2-controls.h
backports-ath-2015-11-05/include/uapi/linux/videodev2.h
backports-ath-2015-11-05/include/uapi/linux/v4l2-mediabus.h
backports-ath-2015-11-05/include/uapi/linux/usb/
backports-ath-2015-11-05/include/uapi/linux/usb/cdc.h
backports-ath-2015-11-05/include/uapi/linux/usb/cdc-wdm.h
backports-ath-2015-11-05/include/uapi/linux/nl80211.h
backports-ath-2015-11-05/include/uapi/linux/vsp1.h
backports-ath-2015-11-05/include/uapi/linux/v4l2-subdev.h
backports-ath-2015-11-05/include/uapi/linux/v4l2-common.h
backports-ath-2015-11-05/include/uapi/linux/wil6210_uapi.h
backports-ath-2015-11-05/include/uapi/linux/pci_regs.h
backports-ath-2015-11-05/include/uapi/linux/v4l2-dv-timings.h
backports-ath-2015-11-05/include/uapi/linux/media.h
backports-ath-2015-11-05/include/uapi/linux/nfc.h
backports-ath-2015-11-05/include/uapi/linux/wireless.h
backports-ath-2015-11-05/include/uapi/linux/dvb/
backports-ath-2015-11-05/include/uapi/linux/dvb/video.h
backports-ath-2015-11-05/include/uapi/linux/dvb/dmx.h
backports-ath-2015-11-05/include/uapi/linux/dvb/frontend.h
backports-ath-2015-11-05/include/uapi/linux/dvb/net.h
backports-ath-2015-11-05/include/uapi/linux/dvb/ca.h
backports-ath-2015-11-05/include/uapi/linux/dvb/audio.h
backports-ath-2015-11-05/include/uapi/linux/dvb/version.h
backports-ath-2015-11-05/include/uapi/linux/dvb/Kbuild
backports-ath-2015-11-05/include/uapi/linux/dvb/osd.h
backports-ath-2015-11-05/include/trace/
backports-ath-2015-11-05/include/trace/events/
backports-ath-2015-11-05/include/trace/events/v4l2.h
backports-ath-2015-11-05/defconfigs/
backports-ath-2015-11-05/defconfigs/ath6kl
backports-ath-2015-11-05/defconfigs/ar5523
backports-ath-2015-11-05/defconfigs/hwsim
backports-ath-2015-11-05/defconfigs/ath9k
backports-ath-2015-11-05/defconfigs/ath5k
backports-ath-2015-11-05/defconfigs/wcn36xx
backports-ath-2015-11-05/defconfigs/wil6210
backports-ath-2015-11-05/defconfigs/ath9k-debug
backports-ath-2015-11-05/defconfigs/ath10k
backports-ath-2015-11-05/defconfigs/carl9170
backports-ath-2015-11-05/gitlog
backports-ath-2015-11-05/drivers/
backports-ath-2015-11-05/drivers/net/
backports-ath-2015-11-05/drivers/net/wireless/
backports-ath-2015-11-05/drivers/net/wireless/Makefile
backports-ath-2015-11-05/drivers/net/wireless/ath/
backports-ath-2015-11-05/drivers/net/wireless/ath/debug.c
backports-ath-2015-11-05/drivers/net/wireless/ath/dfs_pattern_detector.h
backports-ath-2015-11-05/drivers/net/wireless/ath/trace.c
backports-ath-2015-11-05/drivers/net/wireless/ath/Makefile
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/debug.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/trace.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/hif.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/target.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/core.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/Makefile
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/wmi.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/common.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/sdio.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/trace.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/htc-ops.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/wmi.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/debug.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/cfg80211.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/hif.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/hif-ops.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/core.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/htc.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/recovery.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/cfg80211.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/htc_mbox.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/init.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/htc_pipe.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/usb.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/bmi.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/testmode.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/testmode.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/bmi.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/txrx.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/main.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath6kl/Kconfig
backports-ath-2015-11-05/drivers/net/wireless/ath/regd.c
backports-ath-2015-11-05/drivers/net/wireless/ath/trace.h
backports-ath-2015-11-05/drivers/net/wireless/ath/regd.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ar5523/
backports-ath-2015-11-05/drivers/net/wireless/ath/ar5523/ar5523.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ar5523/ar5523_hw.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ar5523/Makefile
backports-ath-2015-11-05/drivers/net/wireless/ath/ar5523/ar5523.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ar5523/Kconfig
backports-ath-2015-11-05/drivers/net/wireless/ath/regd_common.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath.h
backports-ath-2015-11-05/drivers/net/wireless/ath/spectral_common.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/phy.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/btcoex.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/debug.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9002_phy.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/channel.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/btcoex.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9003_eeprom.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/htc_drv_main.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/htc_drv_debug.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9003_paprd.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/dfs.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/dfs.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9002_initvals.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ahb.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/hif_usb.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/hw-ops.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9003_eeprom.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/Makefile
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar5008_phy.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9565_1p0_initvals.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9003_2p2_initvals.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/common-beacon.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/wmi.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9001_initvals.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar5008_initvals.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9002_hw.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/mac.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/eeprom.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/common.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/pci.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9003_aic.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/wow.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9003_phy.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/eeprom_9287.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/hw.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9003_rtt.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/wmi.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/common-debug.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9003_calib.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/htc_drv_init.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/debug.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9003_hw.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9580_1p0_initvals.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9002_phy.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/gpio.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/htc_drv_gpio.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/common-init.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9340_initvals.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/common-beacon.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9003_rtt.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/mci.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/mac.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9003_phy.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9003_mci.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9002_calib.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/recv.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9002_mac.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/htc_hst.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/reg_wow.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/dynack.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ani.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/reg_mci.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/calib.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/common-spectral.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/common-init.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/htc.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/dynack.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/dfs_debug.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9330_1p2_initvals.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ani.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9003_wow.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/common-spectral.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9003_aic.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/htc_drv_txrx.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/init.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/reg.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/mci.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/hw.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/common-debug.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/beacon.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9565_1p1_initvals.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/htc_hst.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9485_initvals.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9003_mac.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/reg_aic.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/dfs_debug.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/htc_drv_beacon.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/calib.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9003_mci.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9003_mac.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar956x_initvals.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9003_buffalo_initvals.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/eeprom.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/hif_usb.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/common.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/antenna.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/eeprom_def.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9462_2p1_initvals.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar955x_1p0_initvals.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/link.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/eeprom_4k.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9330_1p1_initvals.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar953x_initvals.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/main.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ar9462_2p0_initvals.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/ath9k.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/xmit.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/Kconfig
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/tx99.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath9k/debug_sta.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/debug.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/attach.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/ath5k.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/rfgain.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/led.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/ahb.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/rfbuffer.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/Makefile
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/eeprom.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/pci.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/caps.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/trace.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/pcu.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/debug.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/gpio.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/qcu.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/ani.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/dma.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/rfkill.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/sysfs.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/base.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/ani.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/mac80211-ops.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/base.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/reg.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/desc.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/initvals.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/desc.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/eeprom.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/phy.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/reset.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath5k/Kconfig
backports-ath-2015-11-05/drivers/net/wireless/ath/wcn36xx/
backports-ath-2015-11-05/drivers/net/wireless/ath/wcn36xx/debug.c
backports-ath-2015-11-05/drivers/net/wireless/ath/wcn36xx/pmc.h
backports-ath-2015-11-05/drivers/net/wireless/ath/wcn36xx/Makefile
backports-ath-2015-11-05/drivers/net/wireless/ath/wcn36xx/wcn36xx.h
backports-ath-2015-11-05/drivers/net/wireless/ath/wcn36xx/smd.c
backports-ath-2015-11-05/drivers/net/wireless/ath/wcn36xx/debug.h
backports-ath-2015-11-05/drivers/net/wireless/ath/wcn36xx/smd.h
backports-ath-2015-11-05/drivers/net/wireless/ath/wcn36xx/dxe.h
backports-ath-2015-11-05/drivers/net/wireless/ath/wcn36xx/dxe.c
backports-ath-2015-11-05/drivers/net/wireless/ath/wcn36xx/hal.h
backports-ath-2015-11-05/drivers/net/wireless/ath/wcn36xx/txrx.h
backports-ath-2015-11-05/drivers/net/wireless/ath/wcn36xx/txrx.c
backports-ath-2015-11-05/drivers/net/wireless/ath/wcn36xx/pmc.c
backports-ath-2015-11-05/drivers/net/wireless/ath/wcn36xx/main.c
backports-ath-2015-11-05/drivers/net/wireless/ath/wcn36xx/Kconfig
backports-ath-2015-11-05/drivers/net/wireless/ath/dfs_pattern_detector.c
backports-ath-2015-11-05/drivers/net/wireless/ath/dfs_pri_detector.c
backports-ath-2015-11-05/drivers/net/wireless/ath/reg.h
backports-ath-2015-11-05/drivers/net/wireless/ath/hw.c
backports-ath-2015-11-05/drivers/net/wireless/ath/key.c
backports-ath-2015-11-05/drivers/net/wireless/ath/wil6210/
backports-ath-2015-11-05/drivers/net/wireless/ath/wil6210/fw_inc.c
backports-ath-2015-11-05/drivers/net/wireless/ath/wil6210/debug.c
backports-ath-2015-11-05/drivers/net/wireless/ath/wil6210/trace.c
backports-ath-2015-11-05/drivers/net/wireless/ath/wil6210/debugfs.c
backports-ath-2015-11-05/drivers/net/wireless/ath/wil6210/pmc.h
backports-ath-2015-11-05/drivers/net/wireless/ath/wil6210/Makefile
backports-ath-2015-11-05/drivers/net/wireless/ath/wil6210/wmi.h
backports-ath-2015-11-05/drivers/net/wireless/ath/wil6210/boot_loader.h
backports-ath-2015-11-05/drivers/net/wireless/ath/wil6210/trace.h
backports-ath-2015-11-05/drivers/net/wireless/ath/wil6210/wil_platform.c
backports-ath-2015-11-05/drivers/net/wireless/ath/wil6210/wmi.c
backports-ath-2015-11-05/drivers/net/wireless/ath/wil6210/cfg80211.c
backports-ath-2015-11-05/drivers/net/wireless/ath/wil6210/interrupt.c
backports-ath-2015-11-05/drivers/net/wireless/ath/wil6210/rx_reorder.c
backports-ath-2015-11-05/drivers/net/wireless/ath/wil6210/netdev.c
backports-ath-2015-11-05/drivers/net/wireless/ath/wil6210/fw.h
backports-ath-2015-11-05/drivers/net/wireless/ath/wil6210/wil6210.h
backports-ath-2015-11-05/drivers/net/wireless/ath/wil6210/pcie_bus.c
backports-ath-2015-11-05/drivers/net/wireless/ath/wil6210/wil_platform.h
backports-ath-2015-11-05/drivers/net/wireless/ath/wil6210/pm.c
backports-ath-2015-11-05/drivers/net/wireless/ath/wil6210/ethtool.c
backports-ath-2015-11-05/drivers/net/wireless/ath/wil6210/txrx.h
backports-ath-2015-11-05/drivers/net/wireless/ath/wil6210/txrx.c
backports-ath-2015-11-05/drivers/net/wireless/ath/wil6210/ioctl.c
backports-ath-2015-11-05/drivers/net/wireless/ath/wil6210/fw.c
backports-ath-2015-11-05/drivers/net/wireless/ath/wil6210/pmc.c
backports-ath-2015-11-05/drivers/net/wireless/ath/wil6210/main.c
backports-ath-2015-11-05/drivers/net/wireless/ath/wil6210/Kconfig
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/debug.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/thermal.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/trace.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/wmi-tlv.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/wmi-ops.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/ce.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/core.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/Makefile
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/wmi.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/mac.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/pci.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/wmi-tlv.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/wow.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/htt_tx.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/rx_desc.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/wow.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/debugfs_sta.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/hw.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/trace.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/wmi.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/debug.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/htt.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/spectral.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/hif.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/testmode_i.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/mac.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/spectral.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/core.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/htt.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/swap.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/htc.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/thermal.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/htt_rx.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/ce.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/htc.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/hw.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/bmi.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/testmode.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/p2p.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/testmode.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/bmi.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/txrx.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/txrx.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/pci.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/swap.c
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/targaddrs.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/p2p.h
backports-ath-2015-11-05/drivers/net/wireless/ath/ath10k/Kconfig
backports-ath-2015-11-05/drivers/net/wireless/ath/carl9170/
backports-ath-2015-11-05/drivers/net/wireless/ath/carl9170/phy.h
backports-ath-2015-11-05/drivers/net/wireless/ath/carl9170/debug.c
backports-ath-2015-11-05/drivers/net/wireless/ath/carl9170/tx.c
backports-ath-2015-11-05/drivers/net/wireless/ath/carl9170/wlan.h
backports-ath-2015-11-05/drivers/net/wireless/ath/carl9170/fwdesc.h
backports-ath-2015-11-05/drivers/net/wireless/ath/carl9170/led.c
backports-ath-2015-11-05/drivers/net/wireless/ath/carl9170/rx.c
backports-ath-2015-11-05/drivers/net/wireless/ath/carl9170/Makefile
backports-ath-2015-11-05/drivers/net/wireless/ath/carl9170/mac.c
backports-ath-2015-11-05/drivers/net/wireless/ath/carl9170/fwcmd.h
backports-ath-2015-11-05/drivers/net/wireless/ath/carl9170/hw.h
backports-ath-2015-11-05/drivers/net/wireless/ath/carl9170/carl9170.h
backports-ath-2015-11-05/drivers/net/wireless/ath/carl9170/debug.h
backports-ath-2015-11-05/drivers/net/wireless/ath/carl9170/version.h
backports-ath-2015-11-05/drivers/net/wireless/ath/carl9170/usb.c
backports-ath-2015-11-05/drivers/net/wireless/ath/carl9170/cmd.h
backports-ath-2015-11-05/drivers/net/wireless/ath/carl9170/cmd.c
backports-ath-2015-11-05/drivers/net/wireless/ath/carl9170/eeprom.h
backports-ath-2015-11-05/drivers/net/wireless/ath/carl9170/phy.c
backports-ath-2015-11-05/drivers/net/wireless/ath/carl9170/fw.c
backports-ath-2015-11-05/drivers/net/wireless/ath/carl9170/main.c
backports-ath-2015-11-05/drivers/net/wireless/ath/carl9170/Kconfig
backports-ath-2015-11-05/drivers/net/wireless/ath/dfs_pri_detector.h
backports-ath-2015-11-05/drivers/net/wireless/ath/main.c
backports-ath-2015-11-05/drivers/net/wireless/ath/Kconfig
backports-ath-2015-11-05/drivers/net/wireless/Kconfig
backports-ath-2015-11-05/.local-symbols
backports-ath-2015-11-05/.blacklist.map
backports-ath-2015-11-05/Makefile.real
backports-ath-2015-11-05/scripts/
backports-ath-2015-11-05/scripts/blacklist.sh
backports-ath-2015-11-05/scripts/check_depmod.sh
backports-ath-2015-11-05/scripts/mod_helpers.sh
backports-ath-2015-11-05/scripts/uninstall.sh
backports-ath-2015-11-05/scripts/update-initramfs.sh
backports-ath-2015-11-05/scripts/compress_modules.sh
backports-ath-2015-11-05/backport-include/
backports-ath-2015-11-05/backport-include/sound/
backports-ath-2015-11-05/backport-include/sound/core.h
backports-ath-2015-11-05/backport-include/sound/pcm.h
backports-ath-2015-11-05/backport-include/crypto/
backports-ath-2015-11-05/backport-include/crypto/aead.h
backports-ath-2015-11-05/backport-include/pcmcia/
backports-ath-2015-11-05/backport-include/pcmcia/ds.h
backports-ath-2015-11-05/backport-include/pcmcia/device_id.h
backports-ath-2015-11-05/backport-include/net/
backports-ath-2015-11-05/backport-include/net/ipv6.h
backports-ath-2015-11-05/backport-include/net/genetlink.h
backports-ath-2015-11-05/backport-include/net/inet_frag.h
backports-ath-2015-11-05/backport-include/net/addrconf.h
backports-ath-2015-11-05/backport-include/net/sock.h
backports-ath-2015-11-05/backport-include/net/sch_generic.h
backports-ath-2015-11-05/backport-include/net/net_namespace.h
backports-ath-2015-11-05/backport-include/net/ip.h
backports-ath-2015-11-05/backport-include/net/ip6_fib.h
backports-ath-2015-11-05/backport-include/net/flow_keys.h
backports-ath-2015-11-05/backport-include/net/codel.h
backports-ath-2015-11-05/backport-include/net/iw_handler.h
backports-ath-2015-11-05/backport-include/net/netlink.h
backports-ath-2015-11-05/backport-include/linux/
backports-ath-2015-11-05/backport-include/linux/export.h
backports-ath-2015-11-05/backport-include/linux/time.h
backports-ath-2015-11-05/backport-include/linux/pkt_sched.h
backports-ath-2015-11-05/backport-include/linux/phy.h
backports-ath-2015-11-05/backport-include/linux/compat.h
backports-ath-2015-11-05/backport-include/linux/i2c-mux.h
backports-ath-2015-11-05/backport-include/linux/genetlink.h
backports-ath-2015-11-05/backport-include/linux/gpio.h
backports-ath-2015-11-05/backport-include/linux/irqdomain.h
backports-ath-2015-11-05/backport-include/linux/irq.h
backports-ath-2015-11-05/backport-include/linux/pm_qos.h
backports-ath-2015-11-05/backport-include/linux/security.h
backports-ath-2015-11-05/backport-include/linux/etherdevice.h
backports-ath-2015-11-05/backport-include/linux/kconfig.h
backports-ath-2015-11-05/backport-include/linux/socket.h
backports-ath-2015-11-05/backport-include/linux/completion.h
backports-ath-2015-11-05/backport-include/linux/rtnetlink.h
backports-ath-2015-11-05/backport-include/linux/dma-mapping.h
backports-ath-2015-11-05/backport-include/linux/if_ether.h
backports-ath-2015-11-05/backport-include/linux/proc_fs.h
backports-ath-2015-11-05/backport-include/linux/list_nulls.h
backports-ath-2015-11-05/backport-include/linux/acpi.h
backports-ath-2015-11-05/backport-include/linux/leds.h
backports-ath-2015-11-05/backport-include/linux/jiffies.h
backports-ath-2015-11-05/backport-include/linux/input.h
backports-ath-2015-11-05/backport-include/linux/regmap.h
backports-ath-2015-11-05/backport-include/linux/platform_device.h
backports-ath-2015-11-05/backport-include/linux/mei_cl_bus.h
backports-ath-2015-11-05/backport-include/linux/net.h
backports-ath-2015-11-05/backport-include/linux/mii.h
backports-ath-2015-11-05/backport-include/linux/freezer.h
backports-ath-2015-11-05/backport-include/linux/hid.h
backports-ath-2015-11-05/backport-include/linux/regulator/
backports-ath-2015-11-05/backport-include/linux/regulator/driver.h
backports-ath-2015-11-05/backport-include/linux/moduleparam.h
backports-ath-2015-11-05/backport-include/linux/pm.h
backports-ath-2015-11-05/backport-include/linux/skbuff.h
backports-ath-2015-11-05/backport-include/linux/bcm47xx_nvram.h
backports-ath-2015-11-05/backport-include/linux/firmware.h
backports-ath-2015-11-05/backport-include/linux/mdio.h
backports-ath-2015-11-05/backport-include/linux/timecounter.h
backports-ath-2015-11-05/backport-include/linux/string.h
backports-ath-2015-11-05/backport-include/linux/usb/
backports-ath-2015-11-05/backport-include/linux/usb/ch9.h
backports-ath-2015-11-05/backport-include/linux/pnp.h
backports-ath-2015-11-05/backport-include/linux/printk.h
backports-ath-2015-11-05/backport-include/linux/if_vlan.h
backports-ath-2015-11-05/backport-include/linux/kernel.h
backports-ath-2015-11-05/backport-include/linux/watchdog.h
backports-ath-2015-11-05/backport-include/linux/i2c.h
backports-ath-2015-11-05/backport-include/linux/uidgid.h
backports-ath-2015-11-05/backport-include/linux/nl80211.h
backports-ath-2015-11-05/backport-include/linux/average.h
backports-ath-2015-11-05/backport-include/linux/time64.h
backports-ath-2015-11-05/backport-include/linux/rfkill.h
backports-ath-2015-11-05/backport-include/linux/cred.h
backports-ath-2015-11-05/backport-include/linux/mm.h
backports-ath-2015-11-05/backport-include/linux/hwmon.h
backports-ath-2015-11-05/backport-include/linux/poll.h
backports-ath-2015-11-05/backport-include/linux/compiler-gcc5.h
backports-ath-2015-11-05/backport-include/linux/kfifo.h
backports-ath-2015-11-05/backport-include/linux/device.h
backports-ath-2015-11-05/backport-include/linux/ioport.h
backports-ath-2015-11-05/backport-include/linux/crc7.h
backports-ath-2015-11-05/backport-include/linux/ptp_clock_kernel.h
backports-ath-2015-11-05/backport-include/linux/netdev_features.h
backports-ath-2015-11-05/backport-include/linux/dma-buf.h
backports-ath-2015-11-05/backport-include/linux/version.h
backports-ath-2015-11-05/backport-include/linux/sysfs.h
backports-ath-2015-11-05/backport-include/linux/wait.h
backports-ath-2015-11-05/backport-include/linux/scatterlist.h
backports-ath-2015-11-05/backport-include/linux/ethtool.h
backports-ath-2015-11-05/backport-include/linux/tty.h
backports-ath-2015-11-05/backport-include/linux/mod_devicetable.h
backports-ath-2015-11-05/backport-include/linux/workqueue.h
backports-ath-2015-11-05/backport-include/linux/netdevice.h
backports-ath-2015-11-05/backport-include/linux/fs.h
backports-ath-2015-11-05/backport-include/linux/random.h
backports-ath-2015-11-05/backport-include/linux/tracepoint.h
backports-ath-2015-11-05/backport-include/linux/clk.h
backports-ath-2015-11-05/backport-include/linux/eeprom_93cx6.h
backports-ath-2015-11-05/backport-include/linux/debugfs.h
backports-ath-2015-11-05/backport-include/linux/init.h
backports-ath-2015-11-05/backport-include/linux/module.h
backports-ath-2015-11-05/backport-include/linux/compiler.h
backports-ath-2015-11-05/backport-include/linux/bitops.h
backports-ath-2015-11-05/backport-include/linux/miscdevice.h
backports-ath-2015-11-05/backport-include/linux/slab.h
backports-ath-2015-11-05/backport-include/linux/list.h
backports-ath-2015-11-05/backport-include/linux/rcupdate.h
backports-ath-2015-11-05/backport-include/linux/dynamic_debug.h
backports-ath-2015-11-05/backport-include/linux/of_platform.h
backports-ath-2015-11-05/backport-include/linux/timekeeping.h
backports-ath-2015-11-05/backport-include/linux/ktime.h
backports-ath-2015-11-05/backport-include/linux/if_arp.h
backports-ath-2015-11-05/backport-include/linux/spi/
backports-ath-2015-11-05/backport-include/linux/spi/spi.h
backports-ath-2015-11-05/backport-include/linux/idr.h
backports-ath-2015-11-05/backport-include/linux/cordic.h
backports-ath-2015-11-05/backport-include/linux/u64_stats_sync.h
backports-ath-2015-11-05/backport-include/linux/mmc/
backports-ath-2015-11-05/backport-include/linux/mmc/sdio_func.h
backports-ath-2015-11-05/backport-include/linux/mmc/host.h
backports-ath-2015-11-05/backport-include/linux/mmc/sdio_ids.h
backports-ath-2015-11-05/backport-include/linux/mmc/sdio.h
backports-ath-2015-11-05/backport-include/linux/lockdep.h
backports-ath-2015-11-05/backport-include/linux/rculist.h
backports-ath-2015-11-05/backport-include/linux/seq_file.h
backports-ath-2015-11-05/backport-include/linux/pci.h
backports-ath-2015-11-05/backport-include/linux/olpc-ec.h
backports-ath-2015-11-05/backport-include/linux/err.h
backports-ath-2015-11-05/backport-include/linux/usb.h
backports-ath-2015-11-05/backport-include/linux/hashtable.h
backports-ath-2015-11-05/backport-include/linux/netlink.h
backports-ath-2015-11-05/backport-include/linux/of.h
backports-ath-2015-11-05/backport-include/linux/static_key.h
backports-ath-2015-11-05/backport-include/linux/tty_flip.h
backports-ath-2015-11-05/backport-include/uapi/
backports-ath-2015-11-05/backport-include/uapi/linux/
backports-ath-2015-11-05/backport-include/uapi/linux/sockios.h
backports-ath-2015-11-05/backport-include/asm/
backports-ath-2015-11-05/backport-include/asm/dma-mapping.h
backports-ath-2015-11-05/backport-include/asm/errno.h
backports-ath-2015-11-05/backport-include/asm/barrier.h
backports-ath-2015-11-05/backport-include/asm/ioctls.h
backports-ath-2015-11-05/backport-include/asm/atomic.h
backports-ath-2015-11-05/backport-include/asm-generic/
backports-ath-2015-11-05/backport-include/asm-generic/barrier.h
backports-ath-2015-11-05/backport-include/asm-generic/bug.h
backports-ath-2015-11-05/backport-include/asm-generic/pci-dma-compat.h
backports-ath-2015-11-05/backport-include/generated/
backports-ath-2015-11-05/backport-include/generated/utsrelease.h
backports-ath-2015-11-05/backport-include/backport/
backports-ath-2015-11-05/backport-include/backport/checks.h
backports-ath-2015-11-05/backport-include/backport/magic.h
backports-ath-2015-11-05/backport-include/backport/backport.h
backports-ath-2015-11-05/backport-include/backport/leds-disabled.h
backports-ath-2015-11-05/COPYING
backports-ath-2015-11-05/Kconfig
[whizkidraj@localhost ~]$ cd backports-ath10k-2015-11-05
bash: cd: backports-ath10k-2015-11-05: No such file or directory
[whizkidraj@localhost ~]$ cd backports-ath-2015-11-05
[whizkidraj@localhost backports-ath-2015-11-05]$ make defconfig-ath10k
/--------------
| Your kernel headers are incomplete/not installed.
| Please install kernel headers, including a .config
| file or use the KLIB/KLIB_BUILD make variables to
| set the kernel to build against, e.g.
|   make KLIB=/lib/modules/3.1.7/
| to compile/install for the installed kernel 3.1.7
| (that isn't currently running.)
\--
Makefile:40: recipe for target 'defconfig-ath10k' failed
make: *** [defconfig-ath10k] Error 1
[whizkidraj@localhost backports-ath-2015-11-05]$ cd ..
[whizkidraj@localhost ~]$ sudo dnf groupinstall "Development Tools and Libraries"
Last metadata expiration check performed 0:29:18 ago on Fri Nov 13 18:22:11 2015.
Warning: Group 'Development Tools and Libraries' does not exist.
Error: Nothing to do.
[whizkidraj@localhost ~]$ cd backports-ath-2015-11-05
[whizkidraj@localhost backports-ath-2015-11-05]$ make defconfig-ath10k
/--------------
| Your kernel headers are incomplete/not installed.
| Please install kernel headers, including a .config
| file or use the KLIB/KLIB_BUILD make variables to
| set the kernel to build against, e.g.
|   make KLIB=/lib/modules/3.1.7/
| to compile/install for the installed kernel 3.1.7
| (that isn't currently running.)
\--
Makefile:40: recipe for target 'defconfig-ath10k' failed
make: *** [defconfig-ath10k] Error 1
[whizkidraj@localhost backports-ath-2015-11-05]$ ^C
[whizkidraj@localhost backports-ath-2015-11-05]$ make uninstall
/--------------
| Your kernel headers are incomplete/not installed.
| Please install kernel headers, including a .config
| file or use the KLIB/KLIB_BUILD make variables to
| set the kernel to build against, e.g.
|   make KLIB=/lib/modules/3.1.7/
| to compile/install for the installed kernel 3.1.7
| (that isn't currently running.)
\--
Makefile:40: recipe for target 'uninstall' failed
make: *** [uninstall] Error 1
[whizkidraj@localhost backports-ath-2015-11-05]$ make uninstall
/--------------
| Your kernel headers are incomplete/not installed.
| Please install kernel headers, including a .config
| file or use the KLIB/KLIB_BUILD make variables to
| set the kernel to build against, e.g.
|   make KLIB=/lib/modules/3.1.7/
| to compile/install for the installed kernel 3.1.7
| (that isn't currently running.)
\--
Makefile:40: recipe for target 'uninstall' failed
make: *** [uninstall] Error 1
[whizkidraj@localhost backports-ath-2015-11-05]$ cd ..
[whizkidraj@localhost ~]$ make uninstall
make: *** No rule to make target 'uninstall'.  Stop.
[whizkidraj@localhost ~]$ cd backports-ath-2015-11-05
[whizkidraj@localhost backports-ath-2015-11-05]$ make defconfig-ath10k
/--------------
| Your kernel headers are incomplete/not installed.
| Please install kernel headers, including a .config
| file or use the KLIB/KLIB_BUILD make variables to
| set the kernel to build against, e.g.
|   make KLIB=/lib/modules/3.1.7/
| to compile/install for the installed kernel 3.1.7
| (that isn't currently running.)
\--
Makefile:40: recipe for target 'defconfig-ath10k' failed
make: *** [defconfig-ath10k] Error 1
[whizkidraj@localhost backports-ath-2015-11-05]$ make defconfig-ath10k
/--------------
| Your kernel headers are incomplete/not installed.
| Please install kernel headers, including a .config
| file or use the KLIB/KLIB_BUILD make variables to
| set the kernel to build against, e.g.
|   make KLIB=/lib/modules/3.1.7/
| to compile/install for the installed kernel 3.1.7
| (that isn't currently running.)
\--
Makefile:40: recipe for target 'defconfig-ath10k' failed
make: *** [defconfig-ath10k] Error 1
[whizkidraj@localhost backports-ath-2015-11-05]$ make
/--------------
| Your kernel headers are incomplete/not installed.
| Please install kernel headers, including a .config
| file or use the KLIB/KLIB_BUILD make variables to
| set the kernel to build against, e.g.
|   make KLIB=/lib/modules/3.1.7/
| to compile/install for the installed kernel 3.1.7
| (that isn't currently running.)
\--
Makefile:40: recipe for target 'modules' failed
make[1]: *** [modules] Error 1
Makefile:30: recipe for target 'default' failed
make: *** [default] Error 2
[whizkidraj@localhost backports-ath-2015-11-05]$

```

---

### Post by rinfinity on 2015-11-13
@whiz-kid
Kali Linux is ubuntu based. So, the original codes can be used with it without/minimal modification. While, we're sorting out the issue with Fedora, it's be nice if u could check if it works with Kali.

---

### Post by rinfinity on 2015-11-13
whizkid-raj,

You just needed to replace:
sudo apt-get install build-essential linux-headers-$(uname -r) git
with 
```
**sudo dnf install make [FONT=century gothic]automake[/FONT] gcc gcc-c++ kernel-devel kernel-headers-$(uname -r) git**
```

and all that you did before executing the above-mentioned code was unnecessary (but shouln't harm). But, still it should've worked. Let me look at it closely.

---

### Post by whizzkid-raj5 on 2015-11-14
Thanks, mate. Tried the same commands of ubuntu for Kali and got the same error at the same step as Fedora i.e at make defconfig-ath10k...............
Do u want some more information about my system or kernel version or anything of that sort, then do let me know (although, I haven't done anything to my kernel version...like upgrading it or installing some other patches...Nothing. Just normal installation of all 4 OSes). I hope this problem gets fixed easily. Dunno when are they going to include an automatic support for this driver.

---

### Post by rinfinity on 2015-11-14
@whizzkid-raj5
I too can replicate the issue on Fedora 23 (Kernel V 3.2). Since, Kali is Ubuntu based I'd have expected it to work.

Can u execute this on fedora?
 
```
sudo dnf groupinstall "Development Tools and Libraries"
**sudo dnf install kernel-headers-$(uname -r) git**
echo "options ath10k_core skip_otp=y" | sudo tee /etc/modprobe.d/ath10k_core.conf

wget [http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2](http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2)
tar -vxf backports-ath-2015-11-05.tar.bz2
cd backports-ath10k-2015-11-05
make defconfig-ath10k
make
sudo make install

cd ..

git clone [https://github.com/kvalo/ath10k-firmware.git](https://github.com/kvalo/ath10k-firmware.git)
sudo cp -r ath10k-firmware/ath10k/ /lib/firmware/
sudo cp -r ath10k-firmware/QCA9377 /lib/firmware/ath10k/
sudo mv /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin_WLAN.TF.1.0-00267-1 /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin
```

---

### Post by whizzkid-raj5 on 2015-11-14
```
[whizkidraj@localhost ~]$ sudo dnf groupinstall "Development Tools and Libraries"
[sudo] password for whizkidraj: 
Fedora 23 - x86_64 - Updates                    311 kB/s | 6.3 MB     00:20    
Last metadata expiration check performed 0:00:09 ago on Sat Nov 14 18:49:22 2015.
Warning: Group 'Development Tools and Libraries' does not exist.
Error: Nothing to do.
[whizkidraj@localhost ~]$ sudo dnf install kernel-headers-$(uname -r) git
Last metadata expiration check performed 0:00:35 ago on Sat Nov 14 18:49:22 2015.
Package kernel-headers-4.2.3-300.fc23.x86_64 is already installed, skipping.
Package git-2.5.0-2.fc23.x86_64 is already installed, skipping.
Dependencies resolved.
Nothing to do.
Complete!
[whizkidraj@localhost ~]$ echo "options ath10k_core skip_otp=y" | sudo tee /etc/modprobe.d/ath10k_core.conf
options ath10k_core skip_otp=y


```

:( And then, the same error at make defconfig-ath10k :(

---

### Post by jeremy31 on 2015-11-14
You might need
```
[COLOR=#424242][FONT=Tahoma]yum install git cmake rpm-build gcc-c++ libstdc++-devel gtk2-devel wxGTK-devel mesa-libGLU-devel mesa-libGL-devel gettext bzip2-devel portaudio-devel
```
[/FONT][/COLOR][COLOR=#424242][FONT=Tahoma]for fedora[/FONT][/COLOR]

---

### Post by whizzkid-raj5 on 2015-11-14
Thanks mate I tried the command and it downloaded and successfully installed some packages but still the same error at make defconfig-ath10k :(
Btw, I use Fedora Workstation on my laptop. There were three editions on the website of it i.e workstation, server and cloud, so I downloaded workstation edition of Fedora and installed it. 
Also, I tried this command, sudo dnf grouplist by googling a little bit about this command and this was the output.

```
[whizkidraj@localhost backports-ath-2015-11-05]$ sudo dnf grouplist
Last metadata expiration check performed 0:33:44 ago on Sat Nov 14 18:49:22 2015.
Available environment groups:
   Minimal Install
   Fedora Server
   Fedora Workstation
   Fedora Cloud Server
   KDE Plasma Workspaces
   Xfce Desktop
   LXDE Desktop
   LXQt Desktop
   Cinnamon Desktop
   MATE Desktop
   Sugar Desktop Environment
   Development and Creative Workstation
   Web Server
   Infrastructure Server
   Basic Desktop
Installed groups:
   C Development Tools and Libraries
   D Development Tools and Libraries
Available groups:
   Administration Tools
   Audio Production
   Authoring and Publishing
   Books and Guides
   Cloud Infrastructure
   Cloud Management Tools
   Container Management
   Design Suite
   Development Tools
   Domain Membership
   Fedora Eclipse
   Editors
   Educational Software
   Electronic Lab
   Engineering and Scientific
   FreeIPA Server
   Games and Entertainment
   Headless Management
   LibreOffice
   MATE Applications
   MATE Compiz
   Medical Applications
   Milkymist
   Network Servers
   Office/Productivity
   Robotics
   RPM Development Tools
   Security Lab
   Sound and Video
   System Tools
   Text-based Internet
   3D Printing
   Window Managers
[whizkidraj@localhost backports-ath-2015-11-05]$ 
```

So I did install D Development Tools and Libraries and C Development Tools and Libraries since the name "Development and Libraries" wasn't mentioned here, but I did try that too as I have posted in my above comment.

---

### Post by jeremy31 on 2015-11-14
What is the contents of ```
ls /usr/src/
```

---

### Post by whizzkid-raj5 on 2015-11-14
```
[whizkidraj@localhost ~]$ ls /usr/src/
debug  kernels
[whizkidraj@localhost ~]$ 
```

---

### Post by rinfinity on 2015-11-14
[**[COLOR=#000000]@tizo_rh[/COLOR]**]("http://ubuntuforums.org/member.php?u=590332")

I've discovered an anomalous behaviour too; though it's not slow-down as in your case, but the wl connection gets dropped frequently if BT is switched off. I turned BT on and the issue got resolved.

If your BT is turned off too, you might want to try turning it on to see if that makes any difference.

---

### Post by jeremy31 on 2015-11-14
Lets try this way ```
locate .config | grep /usr/
```

---

### Post by whizzkid-raj5 on 2015-11-14
```
[whizkidraj@localhost ~]$ locate .config | grep /usr/
/usr/share/dbus-1/interfaces/com.redhat.problems.configuration.abrt.xml
/usr/share/dbus-1/interfaces/com.redhat.problems.configuration.bugzilla.xml
/usr/share/dbus-1/interfaces/com.redhat.problems.configuration.ccpp.xml
/usr/share/dbus-1/interfaces/com.redhat.problems.configuration.oops.xml
/usr/share/dbus-1/interfaces/com.redhat.problems.configuration.python.xml
/usr/share/dbus-1/interfaces/com.redhat.problems.configuration.ureport.xml
/usr/share/dbus-1/interfaces/com.redhat.problems.configuration.vmcore.xml
/usr/share/dbus-1/interfaces/com.redhat.problems.configuration.xml
/usr/share/dbus-1/interfaces/com.redhat.problems.configuration.xorg.xml
/usr/share/dbus-1/system-services/com.redhat.problems.configuration.service
/usr/share/doc/git-core-doc/contrib/mw-to-git/t/test.config
/usr/share/doc/libmng/README.config
/usr/share/doc/xkeyboard-config/README.config
/usr/share/man/man5/Xwrapper.config.5.gz
/usr/share/man/man8/dnf.plugin.config_manager.8.gz
/usr/src/kernels/4.2.5-300.fc23.x86_64/.config
[whizkidraj@localhost ~]$ 

```

---

### Post by jeremy31 on 2015-11-15
It may be easier if you update your kernel to 4.2.5-300.fc23.x86_64 as it appears you have the headers for that kernel

---

### Post by whizzkid-raj5 on 2015-11-15
Thank you, mate. Commands and instructions please :)

---

### Post by jeremy31 on 2015-11-15
I have no idea how to update a kernel in Fedora but this command might get you the headers you need
```
sudo dnf install kernel-devel-$(uname -r)
```

Then see if ```
ls /usr/src/kernels/
``` has a 4.2.3-300.fc23.x86_64 folder

---

### Post by whizzkid-raj5 on 2015-11-15
ok yep, the command executed successfully and installed some packages. And after that, I did ran the second command & it did showed that folder..
```

[whizkidraj@localhost ~]$ ls /usr/src/kernels/
4.2.3-300.fc23.x86_64  4.2.5-300.fc23.x86_64
[whizkidraj@localhost ~]$ 
```

---

### Post by jeremy31 on 2015-11-15
Now see if the backports will compile

---

### Post by whizzkid-raj5 on 2015-11-15
Yep. Now I followed the old steps as mentioned here by my friend, rinfinity [URL="http://ubuntuforums.org/showthread.php?t=2300861&page=4&p=13390092#post13390092"]http://ubuntuforums.org/showthread.php?t=2300861&page=4&p=13390092#post13390092




[/URL]

---

### Post by whizzkid-raj5 on 2015-11-15
And everything executed successfully. Now my wifi is ON. Thank yoo my friend jeremy31, rinfinity and also another friend of mine that I contacted through gmail, but actually I found him on github. His name is Robert Marius Avram. Thanks my friend.
Now, last mission : to activate wifi on kali linux.

[EDIT] - I have exams from November 18th of this month to Dec 11th. So, cya all after December 11th.

Thank you all. Lots of love :)

---

### Post by rinfinity on 2015-11-15
@Jeremy31,
Do you think the issue with compiling the backport on fedora was due to the fact that the kernel-headers and kernel had a version mismatch?

@Whizz-kid,
Good to know it's working. BTW, you mentioned that u've a quad-boot setup just to "learn linux". May I know as to what were the reasons you chose to quad-boot rather than using Virtual Box  to run other OSes from your favorite OS?

---

### Post by jeremy31 on 2015-11-15
> **rinfinity said:**
> @Jeremy31,
Do you think the issue with compiling the backport on fedora was due to the fact that the kernel-headers and kernel had a version mismatch?

@Whizz-kid,
Good to know it's working. BTW, you mentioned that u've a quad-boot setup just to "learn linux". May I know as to what were the reasons you chose to quad-boot rather than using Virtual Box  to run other OSes from your favorite OS?

It was the headers as we call them in Ubuntu, for Fedora it is kernel-devel is what the issue was

---

### Post by whizzkid-raj5 on 2015-11-15
Dunno mate. First I dual booted my PC by installing Windows 10 and Ubuntu coz Ubuntu is the Linux distro that we use in our college. Then I thought to do something more challenging, so I started thinking which Linux distro to install next. So I researched a lot and then I read about Linus Torvalds using Fedora and also it's enterprise version i.e Redhat Linux enterprise (RHLE) being used all over the world and that it was the most used Linux distro for enterprises, even used by NASA. So, I decided that I should learn this distro too, if I'm to do anything at the enterprise level and also coz Linus Torvalds used it :) And the fourth OS was the obvious choice i.e Kali Linux coz after watching the tv show Mr. Robot and also coz I always thought that it would be badass to be a part-time hacker, so I chose to install Kali. Now, to learn about all these OSes, I had to first learn how to install them. So I thought never mind virtual box or VMWare, I'm doing this just like we normally install our OSes. Windows 10 Pro was already installed & dual-booted with Ubuntu by me, so next I installed Fedora and then Kali.

And about WiFi issue, so next time I reinstall Fedora, I should follow the same sequence as ubuntu but just the one line that Jeremy said to put at the start in place of that Ubuntu first line, right? I was like saying to myself to not ask this stupid question and just try it myself and see. But thought to let u all know what I would expect to work the next time I would try.

---

### Post by tizo_rh on 2015-11-15
rinfinity, I think that when I test it, I tried with BT turned on as I usually use it for sound. Anyway, I will test again and try to figure out if it is BT related. I'll let you know.

---

### Post by rinfinity on 2015-11-16
I wish to confirm that the following is working solution to make QCA9377 work on Fedora 23:
```

sudo dnf install kernel-devel-$(uname -r) make automake gcc gcc-c++ git
echo "options ath10k_core skip_otp=y" | sudo tee /etc/modprobe.d/ath10k_core.conf
wget http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2
tar -vxf backports-ath-2015-11-05.tar.bz2
cd backports-ath-2015-11-05
make defconfig-ath10k
make
sudo make install
git clone https://github.com/kvalo/ath10k-firmware.git
sudo cp -r ath10k-firmware/ath10k/ /lib/firmware/
sudo cp -r ath10k-firmware/QCA9377 /lib/firmware/ath10k/
sudo mv /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin_WLAN.TF.1.0-00267-1 /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin

```

---

### Post by rinfinity on 2015-11-16
@whizkid
> "...and also coz Linus Torvalds used it"

Praise the Lord, you didn't choose to use the OS and machine Richard Stallman uses. :lolflag:

> And about WiFi issue, so next time I reinstall Fedora, I should follow  the same sequence as ubuntu but just the one line that Jeremy said to  put at the start in place of that Ubuntu first line, right?


post #65 answers it. I reinstalled fedora from scratch and tested it.

---

### Post by celeryz on 2015-11-16
where is ath10k? it is not 
ath10k-firmware/ath10k/

---

### Post by rinfinity on 2015-11-16
> **celeryz said:**
> where is ath10k? it is not 
ath10k-firmware/ath10k/
  Could you please explain your problem a little bit?

---

### Post by celeryz on 2015-11-16
> **rinfinity said:**
> Could you please explain your problem a little bit?

am I blind or is there no folder (ath10k-firmware/ath10k/) folder...? look [https://github.com/kvalo/ath10k-firmware](https://github.com/kvalo/ath10k-firmware)

as mentioned in this command
sudo cp -r ath10k-firmware/ath10k/ /lib/firmware/

---

### Post by jeremy31 on 2015-11-16
He changed his directory structure on github
```

sudo cp -r ath10k-firmware/QCA9377 /lib/firmware/ath10k/
```

---

### Post by whizzkid-raj5 on 2015-11-16
Thanks mate, rinfinity :D and hehe, I have no idea what he uses. I googled a bit and this is what I found [https://stallman.org/stallman-computing.html](https://stallman.org/stallman-computing.html). Again,... clueless :P But yep, this is how I summed it up, to quadruple-boot my laptop.
Ubuntu - most used desktop OS of Linux and also coz our college, too, has only Ubuntu installed on their PCs along with Windows 7.
Fedora - most used enterprise OS of Linux i.e it's enterprise edition RHEL and also coz Linus Torvalds uses it :P and Kali....coz it's Kali ;) just like batman :)

---

### Post by Anish_Nair on 2015-11-16
> **jeremy31 said:**
> He changed his directory structure on github
```

sudo cp -r ath10k-firmware/QCA9377 /lib/firmware/ath10k/
```

thanks a lot guys , it works.

---

### Post by rinfinity on 2015-11-16
> Thanks mate, rinfinity :grin: and hehe, I have no idea what he uses. I googled a bit and this is what I found [https://stallman.org/stallman-computing.html](https://stallman.org/stallman-computing.html). Again,... clueless :razz:

Seems it's been a while I checked that page. The last I checked, he was still on that "Lemote Yeeloong" computer with gnewSense GNU/Linux OS. He uses a special Linux kernel called "linux-libre" which is usual linux kernel-minus-all the binary, non-free blobs and he previously opted for the "Lemote Yeeloong" machine because that was the only machine in the world that used a Free BIOS.

BTW, if you want to use RHEL, you might want to use CentOS, which is bit-by-bit RHEL except for the RedHat logo. (The CentOS people take the RHEL source-code, remove all the logo/trademarks etc. of it and recompile it). To put it simply, Fedora is alpha-version RHEL, while CentOS is real RHEL without the logo.

Another thing, you might also want to look at "LinuxFromScratch" and "Gentoo"- but please install them in VB. :p:D
I'm using Gentoo as I plan to install it on my phone so that it runs on top of the stock-kernel and in parallel to Dalvik. (Android= Dalvik/Linux while other "Linux OSes" =GNU/Linux) Thanks to Android, people now understand better why RMS insists on using the term GNU/Linux rather than Linux.;)
Here's what I plan to do with my phone: [https://wiki.gentoo.org/wiki/Project:Android](https://wiki.gentoo.org/wiki/Project:Android) .Wish me luck.:D

---

### Post by rinfinity on 2015-11-16
@[**[COLOR=#000000]Anish_Nair[/COLOR]**]("http://ubuntuforums.org/member.php?u=2009779") Good to know it works for you.

---

### Post by celeryz on 2015-11-16
I still get network unclaimed. after reboot :(
I'm using an aspire r3-131t. Oddly the acer drivers mentioned on their official website says QCA9377 thought maybe I missed something

how can I uninstall QCA9377 using the steps outlined in this thread?

---

### Post by rinfinity on 2015-11-16
[**[COLOR=#000000]@celeryz[/COLOR]**]("http://ubuntuforums.org/member.php?u=2009757")
kindly provide your wireless info.txt

This's how to generate it:
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```

Moreover, have you taken note of the fact that the directory structure of git repository where the firmware file had been made available has changed, so there's a small modification needed in the code previously provided.

---

### Post by celeryz on 2015-11-16
> **rinfinity said:**
> [**[COLOR=#000000]@celeryz[/COLOR]**]("http://ubuntuforums.org/member.php?u=2009757")
kindly provide your wireless info.txt

This's how to generate it:
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```

[ATTACH]265629[/ATTACH]

looks like I have an intel driver. Do I need to install kernel 4.2?

---

### Post by rinfinity on 2015-11-16
> **celeryz said:**
> [ATTACH]265629[/ATTACH]

looks like I have an intel driver. Do I need to install kernel 4.2?

If you know that the kernel 4.2 has the relevant driver module, you can either upgrade the kernel or backport the driver module to your present kernel.

Edit: Yes, The kernel in 15.10 does have it. So, you can either, upgrade OS, upgrade kernel, or backport the module.

---

### Post by evandrolkot on 2015-11-21
wget [http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2](http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2)
--2015-11-21 03:44:17--  [http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2](http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2)
Resolving filebin.ca (filebin.ca)... 107.20.159.237, 2406:da00:ff00::6b14:9fed
Connecting to filebin.ca (filebin.ca)|107.20.159.237|:80... connected.
HTTP request sent, awaiting response... 403 Forbidden
2015-11-21 03:44:18 ERROR 403: Forbidden.

---

### Post by evandrolkot on 2015-11-21
upload backports-ath-2015-11-05 again please!

---

### Post by evandrolkot on 2015-11-21
We're sorry, but the file you are requesting has exceeded its maximum download bandwidth allowance.
 					As a result, we are unable to provide the file to you.
 					

please, update again!

---

### Post by rinfinity on 2015-11-21
[**[COLOR=#000000]@evandrolkot[/COLOR]**]("http://ubuntuforums.org/member.php?u=2010088") 	 

[URL="http://filebin.ca/2NIiTdhPm2Q2/backports-ath-2015-11-05.tar.bz2"]

http://filebin.ca/2NIiTdhPm2Q2/backports-ath-2015-11-05.tar.bz2[/URL]

---

### Post by evandrolkot on 2015-11-21
thank you very much :D

---

### Post by jettcalleja on 2015-11-24
is it only me that filebin.ca is down?

---

### Post by jettcalleja on 2015-11-24
Still no luck :(

[ATTACH]265757[/ATTACH]

---

### Post by jettcalleja on 2015-11-24
please help guys :(

---

### Post by manu23 on 2015-11-25
> **jettcalleja said:**
> is it only me that filebin.ca is down?


 It's down. Me too.... :-( 

 Please, re-upload the file...!

---

### Post by yakubskiy2002 on 2015-11-25
Hi All, 
Also have a problem downloading the file.

yuriy@yuriy-Aspire-E5-573G:~$ wget [http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2](http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2)
--2015-11-25 13:33:51--  [http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2](http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2)
Resolving filebin.ca (filebin.ca)... 54.243.64.100, 2406:da00:ff00::36f3:4064
Connecting to filebin.ca (filebin.ca)|54.243.64.100|:80... connected.
HTTP request sent, awaiting response... 503 Service Unavailable: Back-end server is at capacity
2015-11-25 13:33:51 ERROR 503: Service Unavailable: Back-end server is at capacity.

---

### Post by Mohit_Gianani on 2015-11-25
Hi. Does this mean that Ubuntu will work fine on Acer E5-573G-52G3 now? I'm looking to buy it from newegg for the black friday deal but just want to confirm if I should go ahead with the purchase, since a non-working Ubuntu is a deal breaker for me

---

### Post by manu23 on 2015-11-25
First, You need the Unavailable file, like Us... :-)

---

### Post by chili555 on 2015-11-25
Please see: [http://ubuntuforums.org/showthread.php?t=2304250](http://ubuntuforums.org/showthread.php?t=2304250)

Especially this part:> WOW Thank you so much!! It works now!

---

### Post by manu23 on 2015-11-25
> **chili555 said:**
> Please see: [http://ubuntuforums.org/showthread.php?t=2304250](http://ubuntuforums.org/showthread.php?t=2304250)

Especially this part:

 Now it's working! :-)

 You're my heroe..! :lolflag:


 A LOT of thanks.

---

### Post by rinfinity on 2015-11-25
It's not that filebin.ca is down. Actually the file u r trying to download has exceeded the download limit. You can get the updated liknk on page 9 itself as my reply to evaldelcrot.

---

### Post by rinfinity on 2015-11-25
@Chili555

Thanks for helping people out while i was a bit busy to check the forum. Anyways, i can see that yours is a more elegant solution as we get the backport from none other than kernel.org

Thanks again.

---

### Post by rinfinity on 2015-11-25
updated url.[http://filebin.ca/2NIiTdhPm2Q2/backports-ath-2015-11-05.tar.bz2](http://filebin.ca/2NIiTdhPm2Q2/backports-ath-2015-11-05.tar.bz2)

---

### Post by victor01-exe on 2015-12-01
I can't seem to access the previous links or filebin.ca whatshowever, maybe it's temporarily down :/

---

### Post by chili555 on 2015-12-02
> **victor01-exe said:**
> I can't seem to access the previous links or filebin.ca whatshowever, maybe it's temporarily down :/Please see my post #91 above.

---

### Post by victor01-exe on 2015-12-02
**Actually, I tried the solution you gave, but it didn't seem to work for me :/**

  INSTALL /home/chocho/backports-20151120/compat/compat.ko
Can't read private key
  INSTALL /home/chocho/backports-20151120/drivers/net/wireless/ath/ath.ko
Can't read private key
  INSTALL /home/chocho/backports-20151120/drivers/net/wireless/ath/ath10k/ath10k_core.ko
Can't read private key
  INSTALL /home/chocho/backports-20151120/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
Can't read private key
  INSTALL /home/chocho/backports-20151120/net/mac80211/mac80211.ko
Can't read private key
  INSTALL /home/chocho/backports-20151120/net/wireless/cfg80211.ko
Can't read private key
  DEPMOD  4.2.0-18-generic
depmod will prefer updates/ over kernel/ -- OK!
Note:
You may or may not need to update your initramfs, you should if
any of the modules installed are part of your initramfs. To add
support for your distribution to do this automatically send a
patch against "update-initramfs.sh". If your distribution does not
require this send a patch with the '/usr/bin/lsb_release -i -s'
("Ubuntu") tag for your distribution to avoid this warning.
Your backported driver modules should be installed now.

**After something like this appeared I restarted and nothing changed, so I proceeded to do the following:**

cd backports-20151120
[COLOR=#FF0000]make clean[/COLOR]
make defconfig-ath10k
make
sudo make installbut with no luck.

---

### Post by chili555 on 2015-12-02
Actually, nothing about this looks so bad. I suspect you need but lack firmware. Let's check:```
dmesg | grep ath
```

---

### Post by victor01-exe on 2015-12-02
Wow thanks for such a quick reply you're awesome, here's the output:

[    0.858118] Loaded X.509 cert 'Magrathea: Glacier signing key: 4bb43fbaf12fd3a0265773e00e22f4399f634b16'
[   13.276830] ath10k_pci 0000:03:00.0: pci irq msi interrupts 1 irq_mode 0 reset_mode 0
[   13.573022] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/cal-pci-0000:03:00.0.bin failed with error -2
[   13.636395] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-5.bin failed with error -2
[   13.636408] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-5.bin': -2
[   13.636440] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-4.bin failed with error -2
[   13.636444] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-4.bin': -2
[   13.636458] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-3.bin failed with error -2
[   13.636462] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-3.bin': -2
[   13.636476] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-2.bin failed with error -2
[   13.636479] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-2.bin': -2
[   13.636493] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware.bin failed with error -2
[   13.636496] ath10k_pci 0000:03:00.0: could not fetch firmware (-2)
[   13.636500] ath10k_pci 0000:03:00.0: could not fetch firmware files (-2)
[   13.636503] ath10k_pci 0000:03:00.0: could not probe fw (-2)

BTW using ubuntu 14.04 LTS

---

### Post by chili555 on 2015-12-02
It looks like you need some firmware. Please open a terminal and do:
```
sudo mkdir /lib/firmware/ath10k/QCA9377/
sudo mkdir /lib/firmware/ath10k/QCA9377/hw1.0
```
If it reports that the file already exists, that's fine, just continue.

With a temporary working internet connection:

```
sudo apt-get install git
git clone https://github.com/kvalo/ath10k-firmware.git
cd ath10k-firmware/QCA9377/hw1.0
sudo cp board.bin  /lib/firmware/ath10k/QCA9377/hw1.0
sudo cp firmware-5.bin_WLAN.TF.1.0-00267-1   /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin
sudo modprobe -r ath10k_pci
sudo modprobe ath10k_pci
```
Your wireless should be working; if not, try a reboot.

---

### Post by victor01-exe on 2015-12-02
wow! it worked, thanks a lot I can finally migrate to Ubuntu.
You're awesome ^_^

---

### Post by nomad642 on 2015-12-03
The filebin.ca links are broken for me. It seems to redirect to an empty page. Can someone upload the package somewhere else?

---

### Post by chili555 on 2015-12-03
> **nomad642 said:**
> The filebin.ca links are broken for me. It seems to redirect to an empty page. Can someone upload the package somewhere else?Please see my post #91 above.

---

### Post by Ajith_Kumar on 2015-12-08
> **chili555 said:**
> It looks like you need some firmware. Please open a terminal and do:
```
sudo mkdir /lib/firmware/ath10k/QCA9377/
sudo mkdir /lib/firmware/ath10k/QCA9377/hw1.0
```
If it reports that the file already exists, that's fine, just continue.

With a temporary working internet connection:

```
sudo apt-get install git
git clone https://github.com/kvalo/ath10k-firmware.git
cd ath10k-firmware/QCA9377/hw1.0
sudo cp board.bin  /lib/firmware/ath10k/QCA9377/hw1.0
sudo cp firmware-5.bin_WLAN.TF.1.0-00267-1   /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin
sudo modprobe -r ath10k_pci
sudo modprobe ath10k_pci
```
Your wireless should be working; if not, try a reboot.



Thanks man! @chili555. You rock!

I confirm that this solution worked on Acer Aspire E15 (E5-573G-56RG)

---

### Post by victor01-exe on 2015-12-08
I ran into a little problem with the driver (or maybe the firmware), it just stopped working, no wireless after a successful installation following chili555's help, has anyone experienced something like that while using his solution?

(edit)
It was an update that messed up what was previously installed, doing everything again fixed it.

---

### Post by jhamba on 2015-12-10
Just posting this in case anyone has the same problem as me. I did most of these things, and it still didn't work, and I found out that the best thing to do was to copy the whole git in /lib/firmware, instead of the subdirectories. So, in a fresh install of ubuntu, this is what I did.
```

[SIZE=2][FONT=courier new]sudo apt-get install build-essential linux-headers-generic
sudo apt-get install git
cd /lib/firmware 
sudo rm -r ath10k
sudo git clone [https://github.com/kvalo/ath10k-firmware.git](https://github.com/kvalo/ath10k-firmware.git)
sudo mv ath10k-firmware/ ath10k/ 
cd /lib/firmware/ath10k/QCA9377/hw1.0/
sudo mv firmware-5.bin_WLAN.TF.1.0-00267-1 firmware-5.bin
wget [https://www.kernel.org/pub/linux/kernel/projects/backports/2015/03/13/backports-20150313.tar.xz](https://www.kernel.org/pub/linux/kernel/projects/backports/2015/03/13/backports-20150313.tar.xz)
tar xvfJ backports-20150313.tar.xz
cd backports-20150313
make defconfig-ath10k
make
sudo make install[/FONT][/SIZE]

```[FONT=arial]
[/FONT][FONT=arial]and it finally started working. I have an acer E5-573-32JT, if you're curious. I'm not quite sure which particular wireless card I have.
EDIT: So, the reason this worked is because I needed firmware for QCA988X and QCA6174 in addition to QCA9337. So, The other directories are unnecessary for me, but keeping them in is harmless, from what I can see.[/FONT]

---

### Post by tizo_rh on 2015-12-13
Rinfinity, I haven't been having problems for the last two weeks. I think (but I am not sure) that the problem was related to an "advanced" function of the touchpad that was activated in the bios. I have to deactivated it to solve a problem of the touchpad in a Debian installed on the same laptop, and apparently that resolve the wifi problem on Ubuntu too.

---

### Post by rinfinity on 2015-12-24
@Tizo_rh Good to know it works now. :)

@whizkidraj you might want to check your PM. :)

---

### Post by joucoski on 2016-01-01
I tried using the procedures in this discussion, but I could not run my wifi card. Part of the file "wireless-info.txt" is here (the complete file is attached):

```
##### lspci #############################

01:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)
    Subsystem: Samsung Electronics Co Ltd Device [144d:412b]

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c757]
    Kernel driver in use: r8169
```

Could someone show me how I can fix the device to work?

wireless-info.txt: [ATTACH]266505[/ATTACH]

---

### Post by praseodym on 2016-01-02
Obviously, its trying to load a Broadcom module:
```

sudo modprobe -rfv wl
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -v ath10k_pci
dmesg | grep ath
```

---

### Post by jeremy31 on 2016-01-02
And post ```
dkms status
``` as the script result shows signs of Adam Lee's dkms package

---

### Post by joucoski on 2016-01-02
Sorry, but I did not understand the suggestion. The answer is to my problem or another user? Thanks.

---

### Post by joucoski on 2016-01-02
This is the result:  

> $ dkms status
backath10k, 2.0, 3.13.0-74-generic, x86_64: installed
backath10k, 2.0, 3.19.0-25-generic, x86_64: installed (WARNING! Diff between built and installed module!)
backath10k, 2.0, 3.19.0-42-generic, x86_64: installed
bbswitch, 0.7, 3.13.0-74-generic, x86_64: installed
bbswitch, 0.7, 3.19.0-25-generic, x86_64: installed
bbswitch, 0.7, 3.19.0-42-generic, x86_64: installed
ndiswrapper, 1.59, 3.19.0-42-generic, x86_64: installed
nvidia-352, 352.63, 3.19.0-42-generic, x86_64: installed
rtl8188C_8192C_8192D_usb_linux, v3.3.0_2971.20111128: added

is this?

---

### Post by jeremy31 on 2016-01-02
```
sudo dkms remove backath10k/2.0 --all
```

Reboot and try reinstalling backports
```
cd backports-20151120
make clean
make defconfig-ath10k
make
sudo make install
```

Reboot, if it doesn't work, post ```
dmesg | grep ath10k
```

---

### Post by joucoski on 2016-01-02
I just ran the command:

> sudo dkms remove backath10k/2.0 --all

I restarted the notebook and the network card began to work! I do not know what has been done, but thank you very much for your help !!!

---

### Post by Omar_Eduardo on 2016-01-04
File Unavailable   [http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2](http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2) 

Already downloaded as rinfinity (#82) shared and wireless working, but it would be great if someone can reupload.

Thanks

Aspire E 14 
Model: E5-473-52IC

---

### Post by chili555 on 2016-01-04
> **Omar_Eduardo said:**
> File Unavailable   [http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2](http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2) 

Already downloaded as rinfinity (#82) shared and wireless working, but it would be great if someone can reupload.

Thanks

Aspire E 14 
Model: E5-473-52ICYou may have better luck with the more current instructions here: [http://ubuntuforums.org/showthread.php?t=2304250](http://ubuntuforums.org/showthread.php?t=2304250)

---

### Post by Nerdie on 2016-03-28
> **fabio-arezi said:**
> It's work for me on my Samsung Expert X30, in this sequence:

```


mkdir tmp-ath10k
cd tmp-ath10k

sudo apt-get install build-essential linux-headers-$(uname -r) git
echo "options ath10k_core skip_otp=y" | sudo tee /etc/modprobe.d/ath10k_core.conf

wget http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2
tar -vxf backports-ath-2015-11-05.tar.bz2
cd backports-ath10k-2015-11-05
make defconfig-ath10k
make
sudo make install

cd ..

git clone https://github.com/kvalo/ath10k-firmware.git
sudo cp -r ath10k-firmware/ath10k/ /lib/firmware/
sudo cp -r ath10k-firmware/QCA9377 /lib/firmware/ath10k/
sudo mv /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin_WLAN.TF.1.0-00267-1 /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin


```

thanks a lot!!

Mine too after some minor changes, due 403 issues.

   **Ath10k QCA9377 on Ubuntu 15.10 (Apparently now it's supported)**

[INDENT]#1 Create a temporary directory

mkdir tmp-ath10k

#2 And then,
cd tmp-ath10k

#3 this is to install some necessary softwares, as we need to install from source from git repository

sudo apt-get install build-essential linux-headers-$(uname -r) git

#4
echo "options ath10k_core skip_otp=y" | sudo tee /etc/modprobe.d/ath10k_core.conf

#5 we'll download patched backports in the directory we're working from[/INDENT]
[INDENT](stopped following this [advice]("http://ubuntuforums.org/showthread.php?t=2300861&page=4") from **[[COLOR=#000000]rinfinity[/COLOR]]("http://ubuntuforums.org/member.php?u=1470464")** due 403 issues and continued with this [post]("http://ubuntuforums.org/showthread.php?t=2304250") from **[[COLOR=#dd4814][B]chili555**[/COLOR]]("http://ubuntuforums.org/member.php?u=35909")[/B])

wget [https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/20/backports-20151120.tar.gz](https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/20/backports-20151120.tar.gz)

#6 extract the downloaded file
tar -zxvf backports-20151120.tar.gz

#7Get into the extracted folder, and enter these commands one by one, to install the backport.

cd backports-20151120
make defconfig-ath10k
make
sudo make install

#10 reboot

No need of renaming files …
[/INDENT]
[INDENT]Guys, thanks a lot!!!

My acer E5-573-P83X runs now fine w/ WiFi ac.
[/INDENT]

---

### Post by joucoski on 2016-04-09
Thanks! This work for me!

---

### Post by tizo_rh on 2016-05-27
This is working for me. But I have a problem when bluetooth is activated too. When bluetooth is transmitting audio for example, the wi-fi connection really slows down. For instance, I can't see a video on Internet when listening the audio via blueetooh, because it works for some seconds, then stops several more seconds to load, and so on. 

Both things (wi-fi and bluetooh) works perfectly if used without the other.

Any idea?.

---

