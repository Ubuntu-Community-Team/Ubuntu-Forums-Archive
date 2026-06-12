---
title: "Motoraux M7160u USB wifi adaptor not recognized"
date: 2016-04-26
forum: Networking &amp; Wireless
---

### Post by nakshathram on 2016-04-26
Hello,
   I have Ubuntu 16.04 installed. I bought a Motoraux USB wifi adaptor, but Ubuntu won't recognize it. The driver that came along with it indicates that it is an M7160u model.
I am fairly new to Ubuntu. Looking for help on how to make Ubuntu detect this adaptor.
Note: This adaptor works fine with windows 10.

Here's the model I bought: [http://www.amazon.com/Motoraux-600Mbps-wireless-adapter-Windows/dp/B0199FBBRM?ie=UTF8&psc=1&redirect=true&ref_=oh_aui_detailpage_o07_s00](http://www.amazon.com/Motoraux-600Mbps-wireless-adapter-Windows/dp/B0199FBBRM?ie=UTF8&psc=1&redirect=true&ref_=oh_aui_detailpage_o07_s00)

Thanks

---

### Post by jeremy31 on 2016-04-26
"*Thread moved to **Networking & Wireless**.*"
See [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) and post your results from the wireless info script

---

### Post by nakshathram on 2016-04-26
Please note that I am temporarily using another adaptor (Canakit) to connect to internet currently. Both adaptors are plugged in.
Here's the output from wireless-info

```

########## wireless info START ##########

Report from: 26 Apr 2016 19:10 CDT -0500

Booted last: 26 Apr 2016 00:00 CDT -0500

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

Ubuntu

##### lspci #############################

00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-V [8086:15b8] (rev 31)
	Subsystem: ASUSTeK Computer Inc. Ethernet Connection (2) I219-V [1043:8672]
	Kernel driver in use: e1000e

##### lsusb #############################

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 003: ID 0e8d:7610 MediaTek Inc. 
Bus 001 Device 007: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

2: phy2: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

rt2800usb              28672  0
rt2x00usb              24576  1 rt2800usb
rt2800lib              94208  1 rt2800usb
rt2x00lib              57344  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              737280  3 rt2x00lib,rt2x00usb,rt2800lib
crc_ccitt              16384  1 rt2800lib
cfg80211              565248  2 mac80211,rt2x00lib
eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
mxm_wmi                16384  0
wmi                    20480  2 mxm_wmi,asus_wmi
video                  40960  2 i915_bpo,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s31f6 Link encap:Ethernet  HWaddr <MAC 'enp0s31f6' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:df200000-df220000 

ra0       Link encap:Ethernet  HWaddr <MAC 'ra0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlx000f6006e2af Link encap:Ethernet  HWaddr <MAC 'wlx000f6006e2af' [IF]>  
          inet addr:192.168.0.107  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlx000f6006e2af' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1296 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:844761 (844.7 KB)  TX bytes:128701 (128.7 KB)

##### iwconfig ##########################

enp0s31f6  no wireless extensions.

lo        no wireless extensions.

ra0       Ralink STA  
          
wlx000f6006e2af  IEEE 802.11bgn  ESSID:"RISRIM-GUEST"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'RISRIM-GUEST' [AC1]>   
          Bit Rate=21.7 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:23  Invalid misc:43   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlx000f6006e2af
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlx000f6006e2af
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlx000f6006e2af

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root       861     1  0 18:05 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlx000f6006e2af
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink
GENERAL.PRODUCT:                        802.11 n WLAN
GENERAL.DRIVER:                         rt2800usb
GENERAL.DRIVER-VERSION:                 4.4.0-21-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlx000f6006e2af' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/net/wlx000f6006e2af
GENERAL.IP-IFACE:                       wlx000f6006e2af
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     RISRIM-GUEST
GENERAL.CON-UUID:                       c90a6ee4-bf0b-46b6-bd23-c2cb3630b659
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/3
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     19 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   c90a6ee4-bf0b-46b6-bd23-c2cb3630b659 | RISRIM-GUEST
IP4.ADDRESS[1]:                         192.168.0.107/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1461722823
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 7200
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.0.107
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.0.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::<IP6 'wlx000f6006e2af' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp0s31f6
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (2) I219-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.8-4
GENERAL.HWADDR:                         <MAC 'enp0s31f6' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1f.6/net/enp0s31f6
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

SSID                          BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
       
RISRIM-GUEST                  <MAC 'RISRIM-GUEST' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  55        WPA2       yes     * 
     

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

[[/etc/NetworkManager/system-connections/RISRIM-GUEST]] (600 root)
[connection] id=RISRIM-GUEST | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx000f6006e2af' [IF]> | mac-address-blacklist= | ssid=RISRIM-GUEST
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

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

enp0s31f6  no frequency information.

lo        no frequency information.

ra0       0 channels
wlx000f6006e2af  14 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

enp0s31f6  Interface doesn't support scanning.

ra0       Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)

wlx000f6006e2af  Scan completed :
          Cell 01 - Address: <MAC 'RISRIM-GUEST' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"RISRIM-GUEST"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004b156dac88
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'HHHOME' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"HHHOME"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000106d42d743
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'RT2860AP' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:off
                    ESSID:"RT2860AP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ab9eb1617a
                    Extra: Last beacon: 88ms ago
          Cell 04 - Address: <MAC 'belkin.bdd' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"belkin.bdd"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c4ab2b5a9
                    Extra: Last beacon: 1128ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rt2800usb]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     CD175F3067617C23A4A79F3
depends:        rt2x00lib,rt2800lib,rt2x00usb
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2x00usb]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     FADD78F4B0B6C8F4DDFA8E5
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 

[rt2800lib]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com), Bartlomiej Zolnierkiewicz
srcversion:     BB9F48B63A82C3FD3E73BAF
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 

[rt2x00lib]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     72E39180D883A5541F66494
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-21-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     A882F4FE63500846E1C859E
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-21-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     00D8DA6D3B739DDD31FFF50
depends:        
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rt2800usb]
nohwcrypt: N

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

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[  430.491310] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  430.642309] IPv6: ADDRCONF(NETDEV_UP): wlx000f6006e2af: link is not ready (repeated 2 times)
[  431.805273] wlx000f6006e2af: authenticate with <MAC 'RISRIM-GUEST' [AC1]>
[  431.817701] wlx000f6006e2af: send auth to <MAC 'RISRIM-GUEST' [AC1]> (try 1/3)
[  431.819114] wlx000f6006e2af: authenticated
[  431.822958] wlx000f6006e2af: associate with <MAC 'RISRIM-GUEST' [AC1]> (try 1/3)
[  431.826622] wlx000f6006e2af: RX AssocResp from <MAC 'RISRIM-GUEST' [AC1]> (capab=0x1431 status=0 aid=5)
[  431.829588] wlx000f6006e2af: associated
[  431.829605] IPv6: ADDRCONF(NETDEV_CHANGE): wlx000f6006e2af: link becomes ready
[ 3181.882174] wlx000f6006e2af: deauthenticating from <MAC 'RISRIM-GUEST' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 3182.990843] wlx000f6006e2af: authenticate with <MAC 'RISRIM-GUEST' [AC1]>
[ 3183.009702] wlx000f6006e2af: send auth to <MAC 'RISRIM-GUEST' [AC1]> (try 1/3)
[ 3183.013633] wlx000f6006e2af: authenticated
[ 3183.015442] wlx000f6006e2af: associate with <MAC 'RISRIM-GUEST' [AC1]> (try 1/3)
[ 3183.019013] wlx000f6006e2af: RX AssocResp from <MAC 'RISRIM-GUEST' [AC1]> (capab=0x1431 status=0 aid=5)
[ 3183.022181] wlx000f6006e2af: associated
[ 3505.337702] wlx000f6006e2af: deauthenticating from <MAC 'RISRIM-GUEST' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 3521.067527] ieee80211 phy1: rt2x00_set_rt: Info - RT chipset 5390, rev 0502 detected
[ 3521.077849] ieee80211 phy1: rt2x00_set_rf: Info - RF chipset 5370 detected
[ 3522.095528] rt2800usb 1-1:1.0 wlx000f6006e2af: renamed from wlan0
[ 3522.116355] IPv6: ADDRCONF(NETDEV_UP): wlx000f6006e2af: link is not ready
[ 3522.116392] ieee80211 phy1: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[ 3522.116414] ieee80211 phy1: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[ 3522.259580] IPv6: ADDRCONF(NETDEV_UP): wlx000f6006e2af: link is not ready (repeated 2 times)
[ 3523.400404] wlx000f6006e2af: authenticate with <MAC 'RISRIM-GUEST' [AC1]>
[ 3523.411351] wlx000f6006e2af: send auth to <MAC 'RISRIM-GUEST' [AC1]> (try 1/3)
[ 3523.412768] wlx000f6006e2af: authenticated
[ 3523.416491] wlx000f6006e2af: associate with <MAC 'RISRIM-GUEST' [AC1]> (try 1/3)
[ 3523.420023] wlx000f6006e2af: RX AssocResp from <MAC 'RISRIM-GUEST' [AC1]> (capab=0x1431 status=0 aid=5)
[ 3523.422775] wlx000f6006e2af: associated
[ 3523.422796] IPv6: ADDRCONF(NETDEV_CHANGE): wlx000f6006e2af: link becomes ready
[ 3717.950859] wlx000f6006e2af: deauthenticating from <MAC 'RISRIM-GUEST' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 3729.632818] ieee80211 phy2: rt2x00_set_rt: Info - RT chipset 5390, rev 0502 detected
[ 3729.643139] ieee80211 phy2: rt2x00_set_rf: Info - RF chipset 5370 detected
[ 3730.661203] rt2800usb 1-1:1.0 wlx000f6006e2af: renamed from wlan0
[ 3730.684006] IPv6: ADDRCONF(NETDEV_UP): wlx000f6006e2af: link is not ready
[ 3730.684121] ieee80211 phy2: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[ 3730.684182] ieee80211 phy2: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[ 3730.832838] IPv6: ADDRCONF(NETDEV_UP): wlx000f6006e2af: link is not ready (repeated 2 times)
[ 3731.950307] wlx000f6006e2af: authenticate with <MAC 'RISRIM-GUEST' [AC1]>
[ 3731.968739] wlx000f6006e2af: send auth to <MAC 'RISRIM-GUEST' [AC1]> (try 1/3)
[ 3731.971976] wlx000f6006e2af: authenticated
[ 3731.973816] wlx000f6006e2af: associate with <MAC 'RISRIM-GUEST' [AC1]> (try 1/3)
[ 3731.990961] wlx000f6006e2af: RX AssocResp from <MAC 'RISRIM-GUEST' [AC1]> (capab=0x1431 status=0 aid=5)
[ 3731.993939] wlx000f6006e2af: associated
[ 3731.993959] IPv6: ADDRCONF(NETDEV_CHANGE): wlx000f6006e2af: link becomes ready

########## wireless info END ############
```

---

### Post by jeremy31 on 2016-04-26
I edited your results to add code tags, but I think other members know this chipset better than I do

---

### Post by nakshathram on 2016-05-28
Thanks Jeremy.
I am still waiting if someone could help with this.

---

### Post by jeremy31 on 2016-05-29
I can't find a module that I feel comfortable with recommending.  There are some on github but compiling them results in a lot of warnings

---

### Post by gordintoronto on 2016-05-30
The Amazon listing calls the device an AC600. Is that the same as your M7160U?

If you have only the M7160U plugged in, does it appear in the lsusb results? Could you paste that output into a message?

---

### Post by jeremy31 on 2016-05-30
Gordintoronto, I believe it was this device in the lsusb result of the wireless script
```
Bus 001 Device 003: ID 0e8d:7610 MediaTek Inc.
```

---

### Post by gordintoronto on 2016-05-30
Have a look at this:
[http://superuser.com/questions/738096/how-to-install-mediatek-mt7610u-rt2860-driver](http://superuser.com/questions/738096/how-to-install-mediatek-mt7610u-rt2860-driver)

No guarantees.

---

