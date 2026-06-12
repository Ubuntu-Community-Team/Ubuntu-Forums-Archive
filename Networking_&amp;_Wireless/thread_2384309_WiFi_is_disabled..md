---
title: "WiFi is disabled."
date: 2018-02-05
forum: Networking &amp; Wireless
---

### Post by rjramos28 on 2018-02-05
Hi,

Today I ran the software updater as usual and it updated some packages, and later while browsing my internet connection went dead. After rebooting the WiFi shows as disabled. Enabling it in the WiFi menu does nothing. I tried running:

```
sudo systemctl restart network
```

But it gives me this message: [B]Failed to restart network.service: Unit network.service not found.

[/B]I tested the WiFi in dual boot and it works fine in Windows, so I guess something got messed up with my WiFi driver in Ubuntu when I updated this morning. My Intel WiFi card worked out of the box and I never had any issues until now. Perhaps someone can help me figure it out?

This is my wireless script results:


```
########## wireless info START ##########


Report from: 05 Feb 2018 10:34 EST -0500


Booted last: 05 Feb 2018 00:00 EST -0500


Script from: 10 Jan 2018 20:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-112-generic #135-Ubuntu SMP Fri Jan 19 11:48:36 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Intel Corporation Wireless 7265 [8086:095a] (rev 59)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7265 [8086:5410]
    Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 0bda:5758 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 0fe6:9700 Kontron (Industrial Computer Source / ICS Advent) DM9601 Fast Ethernet Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


##### lsmod #############################


dell_wmi               16384  0
dell_laptop            20480  0
dcdbas                 16384  1 dell_laptop
iwlmvm                311296  0
snd_soc_rt286          36864  0
mac80211              737280  1 iwlmvm
snd_soc_rl6347a        16384  1 snd_soc_rt286
snd_soc_core          212992  2 snd_soc_ssm4567,snd_soc_rt286
iwlwifi               200704  1 iwlmvm
cfg80211              565248  3 iwlwifi,mac80211,iwlmvm
snd_pcm               106496  7 snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_rt286,snd_pcm_dmaengine,snd_hda_core
sparse_keymap          16384  3 dell_wmi,intel_hid,intel_vbtn
wmi                    20480  1 dell_wmi
video                  40960  3 i915,dell_wmi,dell_laptop


##### interfaces ########################


[/etc/network/interfaces]
auto lo
iface lo inet loopback


##### ifconfig ##########################


enx<IF from MAC [IF1]> Link encap:Ethernet  HWaddr <MAC 'enx<IF from MAC [IF1]>' [IF1]>  
          inet addr:192.168.0.16  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::564b:f6f0:dbe5:240e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1073 errors:19 dropped:3 overruns:3 frame:23
          TX packets:1035 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:657076 (657.0 KB)  TX bytes:262214 (262.2 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:721 errors:0 dropped:0 overruns:0 frame:0
          TX packets:721 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:76408 (76.4 KB)  TX bytes:76408 (76.4 KB)


wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


lo        no wireless extensions.


enx<IF from MAC [IF1]>  no wireless extensions.


wlp2s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enx<IF from MAC [IF1]>
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enx<IF from MAC [IF1]>
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enx<IF from MAC [IF1]>


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       868     1  0 10:32 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enx<IF from MAC [IF1]>
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         0fe6
GENERAL.PRODUCT:                        USB 2.0 10/100M Ethernet Adaptor
GENERAL.DRIVER:                         dm9601
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               Davicom DM96xx USB 10/100 Ether
GENERAL.HWADDR:                         <MAC 'enx<IF from MAC [IF1]>' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/net/enx<IF from MAC [IF1]>
GENERAL.IP-IFACE:                       enx<IF from MAC [IF1]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       312cc56c-8433-3d0a-8231-d8397e139990
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{15}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   312cc56c-8433-3d0a-8231-d8397e139990 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.16/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             201.224.73.162
IP4.DNS[2]:                             201.225.225.226
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        host_name = dellxps
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 192.168.0.1
DHCP4.OPTION[11]:                       expiry = 1517848363
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       dhcp_lease_time = 3600
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.0.16
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       routers = 192.168.0.1
DHCP4.OPTION[20]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       domain_name_servers = 201.224.73.162 201.225.225.226
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::564b:f6f0:dbe5:240e/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 7265 (Dual Band Wireless-AC 7265)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-112-generic
GENERAL.FIRMWARE-VERSION:               17.352738.0
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:02:00.0/net/wlp2s0
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
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 


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


[[/etc/NetworkManager/system-connections/RLink]] (600 root)
[connection] id=RLink | type=wifi | permissions=user:rolando:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=RLink
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Aloft Wi-Fi]] (600 root)
[connection] id=Aloft Wi-Fi | type=wifi | permissions=user:rolando:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=Aloft Wi-Fi
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Aura-5G]] (600 root)
[connection] id=Aura-5G | type=wifi | permissions=user:rolando:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=Aura-5G
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Aura-5G_Ext]] (600 root)
[connection] id=Aura-5G_Ext | type=wifi | permissions=user:rolando:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=Aura-5G_Ext
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ARRIS-0D12]] (600 root)
[connection] id=ARRIS-0D12 | type=wifi | permissions=user:rolando:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=ARRIS-0D12
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/EFP Profesores]] (600 root)
[connection] id=EFP Profesores | type=wifi | permissions=user:rolando:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=EFP Profesores
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Aura]] (600 root)
[connection] id=Aura | type=wifi | permissions=user:rolando:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=Aura
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/EFP Internet]] (600 root)
[connection] id=EFP Internet | type=wifi | permissions=user:rolando:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=EFP Internet
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/MobileAP]] (600 root)
[connection] id=MobileAP | type=wifi | permissions=user:rolando:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=MobileAP
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Lab. Informatica]] (600 root)
[connection] id=Lab. Informatica | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=Lab. Informatica
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Linksys Extender Setup - 9A5]] (600 root)
[connection] id=Linksys Extender Setup - 9A5 | type=wifi | permissions=user:rolando:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=Linksys Extender Setup - 9A5
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ARRIS-0D12_Ext]] (600 root)
[connection] id=ARRIS-0D12_Ext | type=wifi | permissions=user:rolando:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=ARRIS-0D12_Ext
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/RNet]] (600 root)
[connection] id=RNet | type=wifi | permissions=user:rolando:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=RNet
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/PRIVADOSG]] (600 root)
[connection] id=PRIVADOSG | type=wifi | permissions=user:rolando:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=PRIVADOSG
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ARRIS-0D12-5G]] (600 root)
[connection] id=ARRIS-0D12-5G | type=wifi | permissions=user:rolando:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=ARRIS-0D12-5G
[ipv4] method=auto
[ipv6] method=auto


##### Netplan config ####################


##### iw reg get ########################


Region: America/Panama (based on set time zone)


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


enx<IF from MAC [IF1]>  no frequency information.


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
          Channel 14 : 2.484 GHz
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


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enx<IF from MAC [IF1]>  Interface doesn't support scanning.


wlp2s0    Interface doesn't support scanning : Network is down


##### module infos ######################


[iwlmvm]
filename:       /lib/modules/4.4.0-112-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     F44ACBA48177884F8597289
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-112-generic SMP mod_unload modversions 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)


[mac80211]
filename:       /lib/modules/4.4.0-112-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0AD8BFD6BB3C27B3A487221
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-112-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/4.4.0-112-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     B39ECFCC55603BE71F1E3B6
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-112-generic SMP mod_unload modversions 
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
filename:       /lib/modules/4.4.0-112-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D2A8E57424453F0D1BE1DBE
depends:        
intree:         Y
vermagic:       4.4.0-112-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
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


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/psmouse-blacklist.conf]
blacklist psmouse


##### rc.local ##########################


exit 0


##### pm-utils ##########################


[/etc/pm/power.d/disable_wol] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/laptop-mode] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/pci_devices] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/pcie_aspm] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/sched-powersave] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/usb_bluetooth] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/wireless] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/xfs_buffer] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


##### udev rules ########################


##### dmesg #############################


[    1.910937] iwlwifi 0000:02:00.0: enabling device (0000 -> 0002)
[    1.912938] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-19.ucode failed with error -2
[    1.913092] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-18.ucode failed with error -2
[    1.917622] iwlwifi 0000:02:00.0: loaded firmware version 17.352738.0 op_mode iwlmvm
[    1.975128] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7265, REV=0x210
[    1.975242] iwlwifi 0000:02:00.0: L1 Enabled - LTR Disabled (repeated 2 times)
[    2.001251] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    2.164598] iwlwifi 0000:02:00.0 wlp2s0: renamed from wlan0
[    3.883531] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   43.628407] dm9601 2-1:1.0 eth0: register 'dm9601' at usb-0000:00:14.0-1, Davicom DM96xx USB 10/100 Ethernet, <MAC 'enx<IF from MAC [IF1]>' [IF1]>
[   43.637449] dm9601 2-1:1.0 enx<IF from MAC [IF1]>: renamed from eth0
[   43.659328] IPv6: ADDRCONF(NETDEV_UP): enx<IF from MAC [IF1]>: link is not ready
[   43.705912] dm9601 2-1:1.0 enx<IF from MAC [IF1]>: link up, 100Mbps, full-duplex, lpa 0xFFFF
[   44.903068] dm9601 2-1:1.0 enx<IF from MAC [IF1]>: kevent 4 may have been dropped
[   44.935526] dm9601 2-1:1.0 enx<IF from MAC [IF1]>: link up, 100Mbps, full-duplex, lpa 0xFFFF (repeated 2 times)


########## wireless info END ############

```

---

### Post by chili555 on 2018-02-05
Let me just predict for you the next 5-6 posts in this thread. We’ll save some time and some steps.

Your wireless shows this:

 > After rebooting the WiFi shows as disabled. 

Because of this:

> 0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

In this context, *hard blocked: yes *suggests that the hardware switch or key combination is set to disable wireless. 

Chili: “Find that switch and change it.”

R.J.: “Chili, I pressed that switch 300 times and it doesn’t change anything. My wireless is *still *hard blocked.”

Chili: “Hmmm. This is a tough one, but I have an idea. See your loaded modules here?”

```
dell_wmi               16384  0
dell_laptop            20480  0
dcdbas                 16384  1 dell_laptop
iwlmvm                311296  0
snd_soc_rt286          36864  0
mac80211              737280  1 iwlmvm
```

“I think that you need dell_wmi OR dell_laptop but not both. Let’s try blacklisting one and see what happens. Open a terminal and do:”

```
sudo -i 
echo "blacklist dell-laptop"  >>  /etc/modprobe.d/blacklist.conf
exit
```

“Now, R.J., reboot and tell us if the wireless is working or if old Chili needs to get a different, better idea.”

---

### Post by rjramos28 on 2018-02-05
I tried it but it didn't work. I also removed from the blacklist *dell-laptop* and tried instead *dell-wmi* but still no WiFi.
I think we'll need a different idea Chili :-?

Here's the updated wireless script result:

```
########## wireless info START ##########


Report from: 05 Feb 2018 12:16 EST -0500


Booted last: 05 Feb 2018 00:00 EST -0500


Script from: 10 Jan 2018 20:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-112-generic #135-Ubuntu SMP Fri Jan 19 11:48:36 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Intel Corporation Wireless 7265 [8086:095a] (rev 59)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7265 [8086:5410]
    Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 0bda:5758 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 0fe6:9700 Kontron (Industrial Computer Source / ICS Advent) DM9601 Fast Ethernet Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


##### lsmod #############################


dell_wmi               16384  0
iwlmvm                311296  0
mac80211              737280  1 iwlmvm
snd_soc_rt286          36864  0
snd_soc_rl6347a        16384  1 snd_soc_rt286
iwlwifi               200704  1 iwlmvm
snd_soc_core          212992  2 snd_soc_ssm4567,snd_soc_rt286
cfg80211              565248  3 iwlwifi,mac80211,iwlmvm
snd_pcm               106496  7 snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_rt286,snd_pcm_dmaengine,snd_hda_core
sparse_keymap          16384  3 dell_wmi,intel_hid,intel_vbtn
wmi                    20480  1 dell_wmi
video                  40960  2 i915,dell_wmi


##### interfaces ########################


[/etc/network/interfaces]
auto lo
iface lo inet loopback


##### ifconfig ##########################


enx<IF from MAC [IF1]> Link encap:Ethernet  HWaddr <MAC 'enx<IF from MAC [IF1]>' [IF1]>  
          inet addr:192.168.0.16  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::564b:f6f0:dbe5:240e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:247 errors:1 dropped:1 overruns:0 frame:0
          TX packets:243 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:109498 (109.4 KB)  TX bytes:73136 (73.1 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:272 errors:0 dropped:0 overruns:0 frame:0
          TX packets:272 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:38595 (38.5 KB)  TX bytes:38595 (38.5 KB)


wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


lo        no wireless extensions.


enx<IF from MAC [IF1]>  no wireless extensions.


wlp2s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enx<IF from MAC [IF1]>
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enx<IF from MAC [IF1]>
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enx<IF from MAC [IF1]>


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root      1009     1  1 12:15 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enx<IF from MAC [IF1]>
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         0fe6
GENERAL.PRODUCT:                        USB 2.0 10/100M Ethernet Adaptor
GENERAL.DRIVER:                         dm9601
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               Davicom DM96xx USB 10/100 Ether
GENERAL.HWADDR:                         <MAC 'enx<IF from MAC [IF1]>' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/net/enx<IF from MAC [IF1]>
GENERAL.IP-IFACE:                       enx<IF from MAC [IF1]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       312cc56c-8433-3d0a-8231-d8397e139990
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{15}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   312cc56c-8433-3d0a-8231-d8397e139990 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.16/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             201.224.73.162
IP4.DNS[2]:                             201.225.225.226
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        host_name = dellxps
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 192.168.0.1
DHCP4.OPTION[11]:                       expiry = 1517854521
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       dhcp_lease_time = 3600
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.0.16
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       routers = 192.168.0.1
DHCP4.OPTION[20]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       domain_name_servers = 201.224.73.162 201.225.225.226
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::564b:f6f0:dbe5:240e/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 7265 (Dual Band Wireless-AC 7265)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-112-generic
GENERAL.FIRMWARE-VERSION:               17.352738.0
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:02:00.0/net/wlp2s0
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
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 


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


[[/etc/NetworkManager/system-connections/RLink]] (600 root)
[connection] id=RLink | type=wifi | permissions=user:rolando:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=RLink
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Aloft Wi-Fi]] (600 root)
[connection] id=Aloft Wi-Fi | type=wifi | permissions=user:rolando:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=Aloft Wi-Fi
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Aura-5G]] (600 root)
[connection] id=Aura-5G | type=wifi | permissions=user:rolando:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=Aura-5G
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Aura-5G_Ext]] (600 root)
[connection] id=Aura-5G_Ext | type=wifi | permissions=user:rolando:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=Aura-5G_Ext
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ARRIS-0D12]] (600 root)
[connection] id=ARRIS-0D12 | type=wifi | permissions=user:rolando:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=ARRIS-0D12
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/EFP Profesores]] (600 root)
[connection] id=EFP Profesores | type=wifi | permissions=user:rolando:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=EFP Profesores
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Aura]] (600 root)
[connection] id=Aura | type=wifi | permissions=user:rolando:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=Aura
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/EFP Internet]] (600 root)
[connection] id=EFP Internet | type=wifi | permissions=user:rolando:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=EFP Internet
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/MobileAP]] (600 root)
[connection] id=MobileAP | type=wifi | permissions=user:rolando:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=MobileAP
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Lab. Informatica]] (600 root)
[connection] id=Lab. Informatica | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=Lab. Informatica
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Linksys Extender Setup - 9A5]] (600 root)
[connection] id=Linksys Extender Setup - 9A5 | type=wifi | permissions=user:rolando:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=Linksys Extender Setup - 9A5
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ARRIS-0D12_Ext]] (600 root)
[connection] id=ARRIS-0D12_Ext | type=wifi | permissions=user:rolando:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=ARRIS-0D12_Ext
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/RNet]] (600 root)
[connection] id=RNet | type=wifi | permissions=user:rolando:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=RNet
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/PRIVADOSG]] (600 root)
[connection] id=PRIVADOSG | type=wifi | permissions=user:rolando:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=PRIVADOSG
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ARRIS-0D12-5G]] (600 root)
[connection] id=ARRIS-0D12-5G | type=wifi | permissions=user:rolando:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=ARRIS-0D12-5G
[ipv4] method=auto
[ipv6] method=auto


##### Netplan config ####################


##### iw reg get ########################


Region: America/Panama (based on set time zone)


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


enx<IF from MAC [IF1]>  no frequency information.


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
          Channel 14 : 2.484 GHz
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


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enx<IF from MAC [IF1]>  Interface doesn't support scanning.


wlp2s0    Interface doesn't support scanning : Network is down


##### module infos ######################


[iwlmvm]
filename:       /lib/modules/4.4.0-112-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     F44ACBA48177884F8597289
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-112-generic SMP mod_unload modversions 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)


[mac80211]
filename:       /lib/modules/4.4.0-112-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0AD8BFD6BB3C27B3A487221
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-112-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/4.4.0-112-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     B39ECFCC55603BE71F1E3B6
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-112-generic SMP mod_unload modversions 
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
filename:       /lib/modules/4.4.0-112-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D2A8E57424453F0D1BE1DBE
depends:        
intree:         Y
vermagic:       4.4.0-112-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
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
blacklist dell-laptop


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


[/etc/modprobe.d/psmouse-blacklist.conf]
blacklist psmouse


##### rc.local ##########################


exit 0


##### pm-utils ##########################


[/etc/pm/power.d/disable_wol] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/laptop-mode] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/pci_devices] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/pcie_aspm] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/sched-powersave] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/usb_bluetooth] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/wireless] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/xfs_buffer] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


##### udev rules ########################


##### dmesg #############################


[    1.976863] iwlwifi 0000:02:00.0: enabling device (0000 -> 0002)
[    1.977836] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-19.ucode failed with error -2
[    1.977970] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-18.ucode failed with error -2
[    1.982841] iwlwifi 0000:02:00.0: loaded firmware version 17.352738.0 op_mode iwlmvm
[    2.043312] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7265, REV=0x210
[    2.043429] iwlwifi 0000:02:00.0: L1 Enabled - LTR Disabled (repeated 2 times)
[    2.080557] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    2.177875] iwlwifi 0000:02:00.0 wlp2s0: renamed from wlan0
[    3.366826] dm9601 2-1:1.0 eth0: register 'dm9601' at usb-0000:00:14.0-1, Davicom DM96xx USB 10/100 Ethernet, <MAC 'enx<IF from MAC [IF1]>' [IF1]>
[    3.377868] dm9601 2-1:1.0 enx<IF from MAC [IF1]>: renamed from eth0
[    4.055056] IPv6: ADDRCONF(NETDEV_UP): enx<IF from MAC [IF1]>: link is not ready
[    4.103330] dm9601 2-1:1.0 enx<IF from MAC [IF1]>: link up, 100Mbps, full-duplex, lpa 0xFFFF
[    4.170477] dm9601 2-1:1.0 enx<IF from MAC [IF1]>: kevent 4 may have been dropped (repeated 5 times)
[    4.195011] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[    4.195464] dm9601 2-1:1.0 enx<IF from MAC [IF1]>: kevent 4 may have been dropped (repeated 3 times)
[    4.240097] dm9601 2-1:1.0 enx<IF from MAC [IF1]>: link up, 100Mbps, full-duplex, lpa 0xFFFF (repeated 2 times)


########## wireless info END ############
```

---

### Post by rjramos28 on 2018-02-05
I got it working. I'm a bit embarrassed actually, it was the WiFi key in my keyboard that disabled it (I did try it 300 times :( ), my Fn seems to not be working very well. 

Thanks for the quick answer though, and sorry for wasting your time.

---

### Post by praseodym on 2018-02-05
Any other button, switch, key or key combo? Please show

```
lsmod
```

completely. Is it a Dell machine?

---

### Post by wildmanne39 on 2018-02-05
Please use thread tools at the top of the page to mark the thread solved!

Thanks

---

### Post by chili555 on 2018-02-05
> **rjramos28 said:**
> I got it working. I'm a bit embarrassed actually, it was the WiFi key in my keyboard that disabled it (I did try it 300 times :( ), my Fn seems to not be working very well.So your Fn key is not "functioning." Ha ha ha!

We're glad it's working by whatever means.

---

### Post by btindie on 2019-01-25
Just to add to this, I had a very similar problem and this helped me restore my WiFi connection.

I wasn't sure if the problem related to a software update or something else at first.

I'm using a Dell E5470 and yesterday it locked up upon boot. I tried using the Alt+SysReq combination to reboot it, in hindsight I think that's what caused my issue. After rebooting it it started normally but I was using a wired connection. The day before it had been fine on Wifi.

rfkill showed the dell-wifi as being hard blocked even though it's an Intel 8260.
```
rfkill list0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: yes
3: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

Holding the blue Fn key and pressing the PtrScr button (has wifi symbol in blue) a couple of times brought it back to life, I used rfkill to check the status after each press. But when it works you'll see your nm-applet pop into life.

If it shows soft blocked for one of them, you can use 'rfkill unblock 0'.

---

