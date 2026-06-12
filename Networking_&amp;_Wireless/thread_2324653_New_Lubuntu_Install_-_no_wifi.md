---
title: "New Lubuntu Install - no wifi"
date: 2016-05-15
forum: Networking &amp; Wireless
---

### Post by jeduke02 on 2016-05-15
I read the sticky.  I followed it.  It didn't work.

Its an old Dell system.  Broadcom card.  ID:  14e4:170c

I also have three other USB wifi cards...none worked with this system.

What do I do?  Cable plug in works fine.

---

### Post by mörgæs on 2016-05-15
> **jeduke02 said:**
> I followed it.

Please post exactly what you have tried and the results.

---

### Post by jeduke02 on 2016-05-15
I tried all sorts of stuff.  probably need to start from scratch.  I followed a few threads, no idea which ones now, and then just started shotgunning.

So...I don't know.  Ill tell you what I did with the sticky.  If this was Windows, Id have this up and running in seconds....but this is out of my area of knowledge.


I did exactly this:

[COLOR=#000000]For example, if you previously installed the bcmwl-kernel-source package, you will need to remove it by using the purge method:[/COLOR]
[COLOR=#000000]Code:
sudo apt-get purge bcmwl-kernel-source[/COLOR]
[COLOR=#000000]If you have just installed Ubuntu, you will need to build an index of available packages before we can install your driver:[/COLOR]
[COLOR=#000000]Code:
sudo apt-get update[/COLOR]
[COLOR=#000000]Now use the pci.id you found in the grid below to find the method to install your driver. This applies with all cases, except as noted. The installation procedure is done in terminal and while connected to the internet with a temporary wired ethernet connection or USB modem or whatever means possible:[/COLOR]
[COLOR=#000000]Code:
sudo apt-get install [/COLOR][COLOR=#000000]14e4:170c[/COLOR][COLOR=#000000]


[/COLOR]It did stuff.  Then I restarted.  Nothing changed.  No wifi networks are listed anywhere.

When I click on the network icon in the corner, I see my card listed.  But its grayed out.  It says disabled.

---

### Post by wildmanne39 on 2016-05-15
Please click on the wireless script in my signature and post the info file here between code tags.
Thanks

---

### Post by jeduke02 on 2016-05-15
```

########## wireless info START ##########

Report from: 15 May 2016 13:01 CDT -0500

Booted last: 15 May 2016 00:00 CDT -0500

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-22-generic #39-Ubuntu SMP Thu May 5 16:52:40 UTC 2016 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Inspiron 6000 laptop [1028:0188]
    Kernel driver in use: b44

03:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
    Subsystem: Intel Corporation Dell B130 laptop integrated WLAN [8086:2721]
    Kernel driver in use: ipw2200

##### lsusb #############################

Bus 001 Device 003: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath9k_htc              69632  0
ath9k_common           36864  1 ath9k_htc
ath9k_hw              458752  2 ath9k_common,ath9k_htc
ath                    24576  3 ath9k_common,ath9k_htc,ath9k_hw
mac80211              659456  1 ath9k_htc
dell_laptop            24576  0
dcdbas                 16384  1 dell_laptop
ipw2200               143360  0
libipw                 36864  1 ipw2200
cfg80211              499712  6 ath,ath9k_common,mac80211,libipw,ath9k_htc,ipw2200
ssb                    57344  1 b44
video                  36864  1 dell_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.152  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::e487:876d:6a87:1be0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1724 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1525 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1093453 (1.0 MB)  TX bytes:170177 (170.1 KB)
          Interrupt:18 

wlp3s3    Link encap:Ethernet  HWaddr <MAC 'wlp3s3' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlxf8d111b48662 Link encap:Ethernet  HWaddr <MAC 'wlxf8d111b48662' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlxf8d111b48662  IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlp3s3    IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search local.tld

##### network managers ##################

Installed:

    NetworkManager

Running:

root       513     1  0 12:23 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4401-B0 100Base-TX (Inspiron 6000 laptop)
GENERAL.DRIVER:                         b44
GENERAL.DRIVER-VERSION:                 2.0
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0/ssb0:0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       5fd85a05-eb2a-4e32-983c-23809851da16
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   5fd85a05-eb2a-4e32-983c-23809851da16 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.152/24
IP4.GATEWAY:                            192.168.0.1
IP4.DNS[1]:                             192.168.0.1
IP4.DOMAIN[1]:                          local.tld
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.0.1
DHCP4.OPTION[5]:                        ip_address = 192.168.0.152
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.0.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 37800
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.0.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 21600
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = local.tld
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1463378399
DHCP4.OPTION[21]:                       host_name = jasduk-Inspiron-6000
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 192.168.0.1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 43200
IP6.ADDRESS[1]:                         fe80::e487:876d:6a87:1be0/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp3s3
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        PRO/Wireless 2200BG [Calexico2] Network Connection (Dell B130 laptop integrated WLAN)
GENERAL.DRIVER:                         ipw2200
GENERAL.DRIVER-VERSION:                 1.2.2kmprq
GENERAL.FIRMWARE-VERSION:               ABG:9.0.5.27 (Dec 12 2007)
GENERAL.HWADDR:                         <MAC 'wlp3s3' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:03:03.0/net/wlp3s3
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
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

GENERAL.DEVICE:                         wlxf8d111b48662
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         ATHEROS
GENERAL.PRODUCT:                        USB2.0 WLAN
GENERAL.DRIVER:                         ath9k_htc
GENERAL.DRIVER-VERSION:                 4.4.0-22-generic
GENERAL.FIRMWARE-VERSION:               1.4
GENERAL.HWADDR:                         <MAC 'wlxf8d111b48662' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/net/wlxf8d111b48662
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

[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s3' [IF]> | mac-address-blacklist= | ssid=UNITE-6628
[ipv4] method=shared
[ipv6] method=ignore

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

country CN: DFS-FCC
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 23), (N/A)
    (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
    (57240 - 59400 @ 2160), (N/A, 28), (N/A)
    (59400 - 63720 @ 2160), (N/A, 44), (N/A)
    (63720 - 65880 @ 2160), (N/A, 28), (N/A)

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

wlxf8d111b48662  13 channels in total; available frequencies :
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
wlp3s3    11 channels in total; available frequencies :
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
          Current Channel=0

##### iwlist scan #######################

wlxf8d111b48662  Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlp3s3    No scan results

##### module infos ######################

[ath9k_htc]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
firmware:       ath9k_htc/htc_9271-1.4.0.fw
firmware:       ath9k_htc/htc_7010-1.4.0.fw
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     D97AA41EF63133F707BAA44
depends:        mac80211,ath9k_hw,ath9k_common,ath,cfg80211
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_dev_fw:Use development FW version (int)
parm:           blink:Enable LED blink on activity (int)

[ath9k_common]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     6FBD9F8A613FDFA282AB4FE
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 686 

[ath9k_hw]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     0151AF8061D8EE7CE15E1A9
depends:        ath
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 686 

[ath]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 686 

[mac80211]
filename:       /lib/modules/4.4.0-22-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     018D8EE375DD4919CA4D4B8
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 686 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[ipw2200]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
firmware:       ipw2200-bss.fw
firmware:       ipw2200-sniffer.fw
firmware:       ipw2200-ibss.fw
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        1.2.2kmprq
description:    Intel(R) PRO/Wireless 2200/2915 Network Driver
srcversion:     D9FB7ADDAA0ED935D9DF2BF
depends:        cfg80211,libipw
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 686 
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           associate:auto associate when scanning (default off) (int)
parm:           auto_create:auto create adhoc network (default on) (int)
parm:           led:enable led control on some systems (default 1 on) (int)
parm:           debug:debug output mask (int)
parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
parm:           rtap_iface:create the rtap interface (1 - create, default 0) (int)
parm:           qos_enable:enable all QoS functionalitis (int)
parm:           qos_burst_enable:enable QoS burst mode (int)
parm:           qos_no_ack_mask:mask Tx_Queue to no ack (int)
parm:           burst_duration_CCK:set CCK burst value (int)
parm:           burst_duration_OFDM:set OFDM burst value (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)
parm:           bt_coexist:enable bluetooth coexistence (default off) (int)
parm:           hwcrypto:enable hardware crypto (default off) (int)
parm:           cmdlog:allocate a ring buffer for logging firmware commands (int)
parm:           roaming:enable roaming support (default on) (int)
parm:           antenna:select antenna 1=Main, 3=Aux, default 0 [both], 2=slow_diversity (choose the one with lower background noise) (int)

[cfg80211]
filename:       /lib/modules/4.4.0-22-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     00D8DA6D3B739DDD31FFF50
depends:        
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 686 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     E5F0C2CF8244682FABB35A4
depends:        
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 686 

##### module parameters #################

[ath9k_htc]
blink: 1
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0
use_dev_fw: 0

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[ipw2200]
antenna: 0
associate: 0
auto_create: 1
bt_coexist: 0
burst_duration_CCK: 0
burst_duration_OFDM: 0
channel: 0
cmdlog: 0
debug: 0
disable: 0
hwcrypto: 0
led: 1
mode: 0
qos_burst_enable: 0
qos_enable: 0
qos_no_ack_mask: 0
roaming: 1
rtap_iface: 0

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

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[   13.250942] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   13.250948] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   13.251207] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   13.900977] ipw2200: Radio Frequency Kill Switch is On:
Kill switch must be turned off for wireless networking to work.
[   13.905904] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   14.576327] ipw2200 0000:03:03.0 wlp3s3: renamed from eth1
[   16.232397] usb 1-8: ath9k_htc: Firmware ath9k_htc/htc_9271-1.4.0.fw requested
[   16.233130] usbcore: registered new interface driver ath9k_htc
[   16.880861] usb 1-8: ath9k_htc: Transferred FW: ath9k_htc/htc_9271-1.4.0.fw, size: 51008
[   17.133099] ath9k_htc 1-8:1.0: ath9k_htc: HTC initialized with 33 credits
[   17.399605] ath9k_htc 1-8:1.0: ath9k_htc: FW Version: 1.4
[   17.399611] ath9k_htc 1-8:1.0: FW RMW support: On
[   17.399614] ath: EEPROM regdomain: 0x809c
[   17.399616] ath: EEPROM indicates we should expect a country code
[   17.399618] ath: doing EEPROM country->regdmn map search
[   17.399620] ath: country maps to regdmn code: 0x52
[   17.399622] ath: Country alpha2 being used: CN
[   17.399623] ath: Regpair used: 0x52
[   17.554433] ath9k_htc 1-8:1.0 wlxf8d111b48662: renamed from wlan0
[   28.302346] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[   28.453133] IPv6: ADDRCONF(NETDEV_UP): wlp3s3: link is not ready
[   28.460226] IPv6: ADDRCONF(NETDEV_UP): wlxf8d111b48662: link is not ready
[ 2238.000220] b44 ssb0:0 eth0: Link is up at 100 Mbps, full duplex
[ 2238.000229] b44 ssb0:0 eth0: Flow control is off for TX and off for RX
[ 2238.000338] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############


```

---

### Post by jeduke02 on 2016-05-15
Wierd....its working.  Ill monitor.

---

### Post by mörgæs on 2016-05-16
Good. If it keeps working please mark the thread solved.

---

