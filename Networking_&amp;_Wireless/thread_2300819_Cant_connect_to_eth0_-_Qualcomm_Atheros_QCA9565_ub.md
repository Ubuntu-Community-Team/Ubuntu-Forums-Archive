---
title: "Cant connect to eth0 - Qualcomm Atheros QCA9565 ubuntu 15.10"
date: 2015-10-28
forum: Networking &amp; Wireless
---

### Post by alef3 on 2015-10-28
I cant connect to other wifis, i have to stand by the router otherwise it doesnt work, and my eth0 seem to be not configured

```


########## wireless info START ##########


Report from: 28 Oct 2015 14:12 BRST -0200


Booted last: 28 Oct 2015 00:00 BRST -0200


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 15.10
Release:	15.10
Codename:	wily


##### kernel ############################


Linux 4.2.0-17-generic #21-Ubuntu SMP Fri Oct 23 19:56:16 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


06:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
	Subsystem: Dell Device [1028:020c]
	Kernel driver in use: ath9k


07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 08)
	Subsystem: Dell Device [1028:05f3]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 003 Device 015: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 003 Device 003: ID 248a:8564  
Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no


##### lsmod #############################


ath3k                  20480  0
ath9k                 147456  0
ath9k_common           36864  1 ath9k
ath9k_hw              471040  2 ath9k_common,ath9k
bluetooth             516096  30 bnep,ath3k,btbcm,btrtl,btusb,rfcomm,btintel
dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
dell_laptop            20480  0
snd_soc_rt5640        114688  0
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
snd_soc_rl6231         16384  1 snd_soc_rt5640
dcdbas                 16384  1 dell_laptop
mac80211              733184  1 ath9k
snd_soc_core          196608  1 snd_soc_rt5640
cfg80211              548864  4 ath,ath9k_common,ath9k,mac80211
snd_pcm               102400  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core
mxm_wmi                16384  1 nouveau
wmi                    20480  4 dell_led,dell_wmi,mxm_wmi,nouveau
video                  36864  4 i915,dell_wmi,nouveau,dell_laptop


##### interfaces ########################


auto lo
iface lo inet loopback


auto eth0
iface eth0 inet dhcp


auto ethX
iface ethX inet dhcp


auto p4p1
iface p4p1 inet dhcp


##### ifconfig ##########################


enp7s0    Link encap:Ethernet  HWaddr <MAC 'enp7s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


vboxnet0  Link encap:Ethernet  HWaddr <MAC 'vboxnet0' [IF]>  
          inet addr:192.168.56.1  Bcast:192.168.56.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'vboxnet0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:252 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:22611 (22.6 KB)


wlp6s0    Link encap:Ethernet  HWaddr <MAC 'wlp6s0' [IF]>  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlp6s0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49850 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34269 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60281520 (60.2 MB)  TX bytes:4189079 (4.1 MB)


##### iwconfig ##########################


enp7s0    no wireless extensions.


lo        no wireless extensions.


vboxnet0  no wireless extensions.


wlp6s0    IEEE 802.11bgn  ESSID:"Descartes"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Descartes' [AC1]>   
          Bit Rate=120 Mb/s   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:116   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp6s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp6s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp6s0
192.168.56.0    0.0.0.0         255.255.255.0   U     0      0        0 vboxnet0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       808     1  0 12:58 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         vboxnet0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         unknown
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'vboxnet0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/vboxnet0
GENERAL.IP-IFACE:                       vboxnet0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    no
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     vboxnet0
GENERAL.CON-UUID:                       55925a5c-1fe9-4f73-827a-c2154b46425f
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{4}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   55925a5c-1fe9-4f73-827a-c2154b46425f | vboxnet0
IP4.ADDRESS[1]:                         192.168.56.1/24
IP4.GATEWAY:                            
IP6.ADDRESS[1]:                         fe80::<IP6 'vboxnet0' [IF]>/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlp6s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA9565 / AR9565 Wireless Network Adapter
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.2.0-17-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp6s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:06:00.0/net/wlp6s0
GENERAL.IP-IFACE:                       wlp6s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Descartes
GENERAL.CON-UUID:                       c9ccdb00-d04c-4f97-9600-22ecc344f302
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     120 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0,2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   0039f621-5950-4e75-b136-dc4a528c3c74 | Alunos
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   c9ccdb00-d04c-4f97-9600-22ecc344f302 | Descartes
IP4.ADDRESS[1]:                         192.168.0.103/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_host_name = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_broadcast_address = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_time_offset = 1
DHCP4.OPTION[7]:                        expiry = 1446054377
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[11]:                       dhcp_message_type = 5
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.0.1
DHCP4.OPTION[14]:                       dhcp_lease_time = 7200
DHCP4.OPTION[15]:                       ip_address = 192.168.0.103
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_interface_mtu = 1
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[20]:                       requested_netbios_scope = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_routers = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::<IP6 'wlp6s0' [IF]>/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp7s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp7s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:07:00.0/net/enp7s0
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
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID       BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Descartes  <MAC 'Descartes' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA1 WPA2  yes     * 


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


[[/etc/NetworkManager/system-connections/Star]] (600 root)
[connection] id=Star | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp6s0' [IF]> | mac-address-blacklist= | ssid=Star
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Alunos]] (600 root)
[connection] id=Alunos | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp6s0' [IF]> | mac-address-blacklist= | ssid=Alunos
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Descartes]] (600 root)
[connection] id=Descartes | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp6s0' [IF]> | mac-address-blacklist= | ssid=Descartes
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Sao_Paulo (based on set time zone)


country BR: DFS-FCC
	(2402 - 2482 @ 40), (N/A, 20), (N/A)
	(5170 - 5250 @ 80), (N/A, 17), (N/A)
	(5250 - 5330 @ 80), (N/A, 24), (0 ms), DFS
	(5490 - 5730 @ 160), (N/A, 24), (0 ms), DFS
	(5735 - 5835 @ 80), (N/A, 30), (N/A)


##### iwlist channels ###################


enp7s0    no frequency information.


lo        no frequency information.


vboxnet0  no frequency information.


wlp6s0    13 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)


##### iwlist scan #######################


enp7s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


vboxnet0  Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.437 GHz (Channel 6)


wlp6s0    Scan completed :
          Cell 01 - Address: <MAC 'Descartes' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Descartes"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004fe900e86a
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ath3k]
filename:       /lib/modules/4.2.0-17-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     BC24BEB84AA8FE42E66C237
depends:        bluetooth
intree:         Y
vermagic:       4.2.0-17-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        8A:A8:7E:56:80:81:D5:83:A1:82:B3:AF:48:3C:67:E7:4C:E0:9F:4E
sig_hashalgo:   sha512


[ath9k]
filename:       /lib/modules/4.2.0-17-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     E5B6C8C8DD5FD6F7AEB5C66
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       4.2.0-17-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        8A:A8:7E:56:80:81:D5:83:A1:82:B3:AF:48:3C:67:E7:4C:E0:9F:4E
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)


[ath9k_common]
filename:       /lib/modules/4.2.0-17-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     619327754B562F78060585E
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.2.0-17-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        8A:A8:7E:56:80:81:D5:83:A1:82:B3:AF:48:3C:67:E7:4C:E0:9F:4E
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/4.2.0-17-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     F987BF2735D3EF13C4E4E3D
depends:        ath
intree:         Y
vermagic:       4.2.0-17-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        8A:A8:7E:56:80:81:D5:83:A1:82:B3:AF:48:3C:67:E7:4C:E0:9F:4E
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/4.2.0-17-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     F1417AD8012BEEF1598B307
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-17-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        8A:A8:7E:56:80:81:D5:83:A1:82:B3:AF:48:3C:67:E7:4C:E0:9F:4E
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/4.2.0-17-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C9DB66EC5B332CC610F266D
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-17-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        8A:A8:7E:56:80:81:D5:83:A1:82:B3:AF:48:3C:67:E7:4C:E0:9F:4E
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.2.0-17-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-17-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        8A:A8:7E:56:80:81:D5:83:A1:82:B3:AF:48:3C:67:E7:4C:E0:9F:4E
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0
use_chanctx: 0


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


grep: /etc/udev/rules.d/*net*.rules: No such file or directory


##### dmesg #############################


[  973.181744] wlp6s0: authenticate with <MAC 'Descartes' [AC1]>
[  973.199090] wlp6s0: send auth to <MAC 'Descartes' [AC1]> (try 1/3)
[  973.201516] wlp6s0: authenticated
[  973.205140] wlp6s0: associate with <MAC 'Descartes' [AC1]> (try 1/3)
[  973.211404] wlp6s0: RX AssocResp from <MAC 'Descartes' [AC1]> (capab=0x31 status=0 aid=3)
[  973.211462] wlp6s0: associated
[  973.213927] ath: EEPROM regdomain: 0x804c
[  973.213930] ath: EEPROM indicates we should expect a country code
[  973.213932] ath: doing EEPROM country->regdmn map search
[  973.213934] ath: country maps to regdmn code: 0x3b
[  973.213935] ath: Country alpha2 being used: BR
[  973.213937] ath: Regpair used: 0x3b
[  973.213939] ath: regdomain 0x804c dynamically updated by country IE
[  978.153907] wlp6s0: authenticate with <MAC 'Descartes' [AC1]>
[  978.171218] wlp6s0: send auth to <MAC 'Descartes' [AC1]> (try 1/3)
[  978.173705] wlp6s0: authenticated
[  978.177445] wlp6s0: associate with <MAC 'Descartes' [AC1]> (try 1/3)
[  978.181706] wlp6s0: RX AssocResp from <MAC 'Descartes' [AC1]> (capab=0x31 status=0 aid=3)
[  978.181765] wlp6s0: associated
[  978.184131] ath: EEPROM regdomain: 0x804c
[  978.184134] ath: EEPROM indicates we should expect a country code
[  978.184135] ath: doing EEPROM country->regdmn map search
[  978.184136] ath: country maps to regdmn code: 0x3b
[  978.184137] ath: Country alpha2 being used: BR
[  978.184137] ath: Regpair used: 0x3b
[  978.184139] ath: regdomain 0x804c dynamically updated by country IE
[ 2093.432805] VBoxNetFlt: attached to 'vboxnet0' / <MAC 'vboxnet0' [IF]>
[ 2093.432854] device vboxnet0 entered promiscuous mode
[ 2548.558134] device vboxnet0 left promiscuous mode


########## wireless info END ############



```

---

### Post by praseodym on 2015-10-28
Hi,

why is the /etc/network/interfaces changed? Re-set it to default and deactivate the hardware encryption of the wifi driver:
```

echo -e "auto lo\niface lo inet loopback" | sudo tee /etc/network/interfaces
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```
Reboot and change the encryption mode in your router to pure WPA2-AES (CCMP). Check the manual

---

