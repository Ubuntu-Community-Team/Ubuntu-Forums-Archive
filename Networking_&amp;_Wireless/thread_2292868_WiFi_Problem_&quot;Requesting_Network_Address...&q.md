---
title: "WiFi Problem: &quot;Requesting Network Address...&quot; loop and disconnect"
date: 2015-08-31
forum: Networking &amp; Wireless
---

### Post by Juaness on 2015-08-31
Hello,

I would like to have your opinion on this problem:
I have installed Lubuntu 15.04 on an old Benq Joybook A33e and the WiFi can not connect to the Networks.
The Wifi is enabled and i can see all the networks available. But when I set a connection with the password to access to my router (or an android shared connection), it loops a few minutes on "Requesting Network Address..." and it fails.

The OS is up to date, i really dont know what to do now.

Here are my wireless info :

```

########## wireless info START ##########

Report from: 25 Aug 2015 19:20 CEST +0200

Booted last: 25 Aug 2015 18:56 CEST +0200

Script from: 30 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 3.19.0-26-generic #28-Ubuntu SMP Tue Aug 11 14:16:45 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

01:04.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
    Subsystem: Mitac Device [1071:8048]
    Kernel driver in use: 8139too

01:05.0 Network controller [0280]: Ralink corp. RT2500 Wireless 802.11bg [1814:0201] (rev 01)
    Subsystem: Ralink corp. RT2500 Wireless 802.11bg [1814:2560]
    Kernel driver in use: rt2500pci

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1d57:2400 Xenta Wireless Mouse Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rt2500pci              28672  0 
rt2x00pci              16384  1 rt2500pci
rt2x00mmio             16384  1 rt2500pci
rt2x00lib              49152  3 rt2x00pci,rt2500pci,rt2x00mmio
mac80211              626688  2 rt2x00lib,rt2x00pci
cfg80211              462848  2 mac80211,rt2x00lib
eeprom_93cx6           16384  1 rt2500pci

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.20  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::240:d0ff:fe91:7e6a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5606 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3263 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6305821 (6.3 MB)  TX bytes:344196 (344.1 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:137 errors:0 dropped:0 overruns:0 frame:0
          TX packets:215 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22439 (22.4 KB)  TX bytes:35040 (35.0 KB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    1024   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
GENERAL.DRIVER:                         8139too
GENERAL.DRIVER-VERSION:                 0.9.28
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:01:04.0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       c3f3ddc0-e54d-4b24-a374-02f8e5ebcdd6
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/7
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   c3f3ddc0-e54d-4b24-a374-02f8e5ebcdd6 | Wired connection 1
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         ip = 192.168.0.20/24, gw = 192.168.0.1
IP4.DNS[1]:                             89.2.0.1
IP4.DNS[2]:                             89.2.0.2
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 89.2.0.1 89.2.0.2
DHCP4.OPTION[5]:                        ip_address = 192.168.0.20
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[8]:                        default_ip_ttl = 64
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       time_offset = 0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       requested_broadcast_address = 1
DHCP4.OPTION[17]:                       routers = 192.168.0.1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[19]:                       requested_domain_name = 1
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1440609227
DHCP4.OPTION[22]:                       requested_wpad = 1
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 192.168.0.1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         ip = fe80::240:d0ff:fe91:7e6a/64, gw = ::

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT2500 Wireless 802.11bg
GENERAL.DRIVER:                         rt2500pci
GENERAL.DRIVER-VERSION:                 3.19.0-26-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:01:05.0/net/wlan0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   af14002c-fa10-4b9b-ab6e-920a2eb4286b | NUMERICABLE-60CF
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes

SSID              BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
FreeWifi_secure   <MAC 'FreeWifi_secure' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
freebox_GREGGWEN  <MAC 'freebox_GREGGWEN' [AC2]>  Infra  11    2462 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA1         no        
FreeWifi_secure   <MAC 'FreeWifi_secure' [AN3]>  Infra  3     2422 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA2 802.1X  no        
freebox_QJOQKR    <MAC 'freebox_QJOQKR' [AN4]>  Infra  3     2422 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA1         no        
FreeWifi          <MAC 'FreeWifi' [AC3]>  Infra  11    2462 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  --           no        
FreeWifi          <MAC 'FreeWifi' [AN6]>  Infra  3     2422 MHz  54 Mbit/s  34      &#9602;&#9604;__  --           no        
NUMERICABLE-60CF  <MAC 'NUMERICABLE-60CF' [AC4]>  Infra  1     2412 MHz  54 Mbit/s  69      &#9602;&#9604;&#9606;_  WPA1 WPA2    no        

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

[[/etc/NetworkManager/system-connections/NUMERICABLE-60CF]] (600 root)
[connection] id=NUMERICABLE-60CF | type=wifi
[wifi] ssid=NUMERICABLE-60CF | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: Europe/Madrid (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20), (N/A)
    (2457 - 2482 @ 40), (3, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (3, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), (N/A), NO-IR
    (5735 - 5835 @ 40), (3, 20), (N/A), NO-IR

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

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

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'FreeWifi_secure' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001de5c49d2c7
                    Extra: Last beacon: 368ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 02 - Address: <MAC 'freebox_GREGGWEN' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"freebox_GREGGWEN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001de5c4aaade
                    Extra: Last beacon: 356ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'FreeWifi' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001de5c4a4b48
                    Extra: Last beacon: 372ms ago
          Cell 04 - Address: <MAC 'NUMERICABLE-60CF' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=61/70  Signal level=-49 dBm  
   lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

                 Encryption key:on
                    ESSID:"NUMERICABLE-60CF"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000c432bdaf
                    Extra: Last beacon: 1020ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rt2500pci]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
license:        GPL
description:    Ralink RT2500 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     3B97C04F8F237B66EEECB4D
depends:        rt2x00lib,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        1E:7D:A8:46:AE:BD:BF:C8:50:6E:6F:42:F1:B8:77:2A:EF:79:1D:79
sig_hashalgo:   sha512

[rt2x00pci]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     F2A3F87D3DBCA573A6F6E05
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        1E:7D:A8:46:AE:BD:BF:C8:50:6E:6F:42:F1:B8:77:2A:EF:79:1D:79
sig_hashalgo:   sha512

[rt2x00mmio]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     879F1B5CBAAA72A33F68B51
depends:        rt2x00lib
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        1E:7D:A8:46:AE:BD:BF:C8:50:6E:6F:42:F1:B8:77:2A:EF:79:1D:79
sig_hashalgo:   sha512

[rt2x00lib]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     7C3B03973B59C2A2A136B6C
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        1E:7D:A8:46:AE:BD:BF:C8:50:6E:6F:42:F1:B8:77:2A:EF:79:1D:79
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.19.0-26-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     DF4E06FB15FF0707074A816
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        1E:7D:A8:46:AE:BD:BF:C8:50:6E:6F:42:F1:B8:77:2A:EF:79:1D:79
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-26-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        1E:7D:A8:46:AE:BD:BF:C8:50:6E:6F:42:F1:B8:77:2A:EF:79:1D:79
sig_hashalgo:   sha512
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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x1814:0x0201 (rt2500pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[  988.681496] wlan0: authenticate with <MAC 'NUMERICABLE-60CF' [AC4]>
[  988.696556] wlan0: send auth to <MAC 'NUMERICABLE-60CF' [AC4]> (try 1/3)
[  988.700741] wlan0: authenticated
[  988.704124] wlan0: associate with <MAC 'NUMERICABLE-60CF' [AC4]> (try 1/3)
[  988.709470] wlan0: RX AssocResp from <MAC 'NUMERICABLE-60CF' [AC4]> (capab=0x1411 status=0 aid=3)
[  988.709528] wlan0: associated
[  992.520054] ieee80211 phy0: wlan0: No probe response from AP <MAC 'NUMERICABLE-60CF' [AC4]> after 500ms, disconnecting.
[  993.680746] wlan0: authenticate with <MAC 'NUMERICABLE-60CF' [AC4]>
[  993.696543] wlan0: send auth to <MAC 'NUMERICABLE-60CF' [AC4]> (try 1/3)
[  993.704132] wlan0: authenticated
[  993.708343] wlan0: associate with <MAC 'NUMERICABLE-60CF' [AC4]> (try 1/3)
[  993.715014] wlan0: RX AssocResp from <MAC 'NUMERICABLE-60CF' [AC4]> (capab=0x1411 status=0 aid=3)
[  993.715068] wlan0: associated
[  997.520054] ieee80211 phy0: wlan0: No probe response from AP <MAC 'NUMERICABLE-60CF' [AC4]> after 500ms, disconnecting.
[  998.680756] wlan0: authenticate with <MAC 'NUMERICABLE-60CF' [AC4]>
[  998.696544] wlan0: send auth to <MAC 'NUMERICABLE-60CF' [AC4]> (try 1/3)
[  998.702145] wlan0: authenticated
[  998.704364] wlan0: associate with <MAC 'NUMERICABLE-60CF' [AC4]> (try 1/3)
[  998.706743] wlan0: RX AssocResp from <MAC 'NUMERICABLE-60CF' [AC4]> (capab=0x1411 status=0 aid=3)
[  998.706791] wlan0: associated
[ 1002.520055] ieee80211 phy0: wlan0: No probe response from AP <MAC 'NUMERICABLE-60CF' [AC4]> after 500ms, disconnecting.
[ 1003.681532] wlan0: authenticate with <MAC 'NUMERICABLE-60CF' [AC4]>
[ 1003.696540] wlan0: send auth to <MAC 'NUMERICABLE-60CF' [AC4]> (try 1/3)
[ 1003.700783] wlan0: authenticated
[ 1003.704192] wlan0: associate with <MAC 'NUMERICABLE-60CF' [AC4]> (try 1/3)
[ 1003.712647] wlan0: RX AssocResp from <MAC 'NUMERICABLE-60CF' [AC4]> (capab=0x1411 status=0 aid=3)
[ 1003.712703] wlan0: associated
[ 1007.520056] ieee80211 phy0: wlan0: No probe response from AP <MAC 'NUMERICABLE-60CF' [AC4]> after 500ms, disconnecting.
[ 1008.680736] wlan0: authenticate with <MAC 'NUMERICABLE-60CF' [AC4]>
[ 1008.696545] wlan0: send auth to <MAC 'NUMERICABLE-60CF' [AC4]> (try 1/3)
[ 1008.700491] wlan0: authenticated
[ 1008.704347] wlan0: associate with <MAC 'NUMERICABLE-60CF' [AC4]> (try 1/3)
[ 1008.709283] wlan0: RX AssocResp from <MAC 'NUMERICABLE-60CF' [AC4]> (capab=0x1411 status=0 aid=3)
[ 1008.709340] wlan0: associated
[ 1012.520050] ieee80211 phy0: wlan0: No probe response from AP <MAC 'NUMERICABLE-60CF' [AC4]> after 500ms, disconnecting.
[ 1013.680765] wlan0: authenticate with <MAC 'NUMERICABLE-60CF' [AC4]>
[ 1013.696542] wlan0: send auth to <MAC 'NUMERICABLE-60CF' [AC4]> (try 1/3)
[ 1013.701129] wlan0: authenticated
[ 1013.704311] wlan0: associate with <MAC 'NUMERICABLE-60CF' [AC4]> (try 1/3)
[ 1013.706792] wlan0: RX AssocResp from <MAC 'NUMERICABLE-60CF' [AC4]> (capab=0x1411 status=0 aid=3)
[ 1013.706848] wlan0: associated
[ 1014.011750] wlan0: deauthenticating from <MAC 'NUMERICABLE-60CF' [AC4]> by local choice (Reason: 3=DEAUTH_LEAVING)

########## wireless info END ############


```

Thank you for your help

---

