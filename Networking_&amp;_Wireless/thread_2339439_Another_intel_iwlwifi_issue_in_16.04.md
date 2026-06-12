---
title: "Another intel iwlwifi issue in 16.04"
date: 2016-10-08
forum: Networking &amp; Wireless
---

### Post by ross-spencer on 2016-10-08
Wifi kicks in when it boots, and i updated last night to the latest intel drivers from here: [http://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html](http://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html) but the behaviour hasn't changed. Works for an undetermined amount of time before failing. 

lsb_release output:

```
No LSB modules are available.
    Distributor ID:    Ubuntu
    Description:    Ubuntu 16.04.1 LTS
    Release:    16.04
    Codename:    xenial
```

And the output of [https://github.com/UbuntuForums/wireless-info:](https://github.com/UbuntuForums/wireless-info:) 


```



########## wireless info START ##########




Report from: 09 Oct 2016 11:00 NZDT +1300




Booted last: 09 Oct 2016 00:00 NZDT +1300




Script from: 08 Jul 2016 02:16 UTC +0000




##### release ###########################




Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial




##### kernel ############################




Linux 4.4.0-38-generic #57-Ubuntu SMP Tue Sep 6 15:42:33 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux




Parameters: ro, quiet, splash, vt.handoff=7




##### desktop ###########################




Ubuntu




##### lspci #############################




01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:8133]
    Kernel driver in use: r8169




05:00.0 Network controller [0280]: Intel Corporation Wireless 3165 [8086:3165] (rev 81)
    DeviceName:  
    Subsystem: Intel Corporation Dual Band Wireless AC 3165 [8086:4010]




##### lsusb #############################




Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 8087:0a2a Intel Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05c8:0382 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




##### PCMCIA card info ##################




##### rfkill ############################




0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no




##### lsmod #############################




iwlmvm                311296  0
mac80211              737280  1 iwlmvm
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
iwlwifi               200704  1 iwlmvm
cfg80211              565248  3 iwlwifi,mac80211,iwlmvm
wmi                    20480  1 hp_wmi




##### interfaces ########################




auto lo
iface lo inet loopback




##### ifconfig ##########################




enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF1]>  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::3214:e3aa:88a8:3097/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27077 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15445 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38916996 (38.9 MB)  TX bytes:1447130 (1.4 MB)




wlo1      Link encap:Ethernet  HWaddr <MAC 'wlo1' [IF2]>  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:376758 errors:0 dropped:0 overruns:0 frame:0
          TX packets:209846 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:531857387 (531.8 MB)  TX bytes:26367868 (26.3 MB)




##### iwconfig ##########################




lo        no wireless extensions.




enp1s0    no wireless extensions.




wlo1      IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          




##### route #############################




Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp1s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp1s0




##### resolv.conf #######################




nameserver 127.0.1.1
search Home




##### network managers ##################




Installed:




    NetworkManager




Running:




root       836     1  0 00:52 ?        00:00:06 /usr/sbin/NetworkManager --no-daemon




##### NetworkManager info ###############




GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.2/0000:01:00.0/net/enp1s0
GENERAL.IP-IFACE:                       enp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       cb5c1ccd-60fe-4d00-8a26-2d072c03abd2
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/4
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   cb5c1ccd-60fe-4d00-8a26-2d072c03abd2 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.4/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          Home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1476050079
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.1.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.4
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = Home
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 86400
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::3214:e3aa:88a8:3097/64
IP6.GATEWAY:                            




GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 3165 (Dual Band Wireless AC 3165)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-38-generic
GENERAL.FIRMWARE-VERSION:               25.30.14.0
GENERAL.HWADDR:                         <MAC 'wlo1' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.3/0000:05:00.0/net/wlo1
GENERAL.IP-IFACE:                       wlo1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     rsnz
GENERAL.CON-UUID:                       132b1855-f5d5-448a-afb9-0d8a0276bba4
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/3
GENERAL.METERED:                        no (guessed)
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
IP4.ADDRESS[1]:                         192.168.1.2/24
IP4.GATEWAY:                            
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          Home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1476047217
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.1.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.2
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = Home
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 86400
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.1
IP6.GATEWAY:                            




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




[[/etc/NetworkManager/system-connections/rsnz]] (600 root)
[connection] id=rsnz | type=wifi | permissions=user:goatslayer:;
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=rsnz
[ipv4] method=auto
[ipv6] method=auto




##### iw reg get ########################




Region: Pacific/Auckland (based on set time zone)




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




enp1s0    no frequency information.




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




##### iwlist scan #######################




lo        Interface doesn't support scanning.




enp1s0    Interface doesn't support scanning.




wlo1      Interface doesn't support scanning : Network is down




##### module infos ######################




[iwlmvm]
filename:       /lib/modules/4.4.0-38-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     49DC02934CB3D8C312FF8E1
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-38-generic SMP mod_unload modversions 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)




[mac80211]
filename:       /lib/modules/4.4.0-38-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B10AF1CD828D26173EA0378
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-38-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)




[iwlwifi]
filename:       /lib/modules/4.4.0-38-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
vermagic:       4.4.0-38-generic SMP mod_unload modversions 
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
filename:       /lib/modules/4.4.0-38-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-38-generic SMP mod_unload modversions 
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




[ 6124.112348] wlo1: failed to remove key (1, <MAC address>) from hardware (-5)
[ 6124.112608] wlo1:  Failed check-sdata-in-driver check, flags: 0x4
[ 6528.818562] r8169 0000:01:00.0 enp1s0: link up
[ 6528.818600] IPv6: ADDRCONF(NETDEV_CHANGE): enp1s0: link becomes ready




########## wireless info END ############

```
dmesg output: 


```

[   14.439006] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-7265D-19.ucode failed with error -2
[   14.441883] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-7265D-18.ucode failed with error -2
[   14.441912] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-7265D-17.ucode failed with error -2
[   14.441936] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-7265D-16.ucode failed with error -2
[   14.442637] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-7265D-15.ucode failed with error -2
[   14.477914] iwlwifi 0000:05:00.0: loaded firmware version 25.30.14.0 op_mode iwlmvm
[   15.223301] iwlwifi 0000:05:00.0: Detected Intel(R) Dual Band Wireless AC 3165, REV=0x210
[   15.223409] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[   15.223608] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[   15.362788] iwlwifi 0000:05:00.0 wlo1: renamed from wlan0
[   31.070115] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[   31.070313] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[   31.130586] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[   31.130779] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[ 3664.762061] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[ 3664.762261] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[ 3664.822796] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[ 3664.823068] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[ 6119.003900] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: time out after 2000ms.
[ 6119.003921] iwlwifi 0000:05:00.0: Current CMD queue read_ptr 81 write_ptr 82
[ 6119.004007] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[ 6119.004016] iwlwifi 0000:05:00.0: Status: 0x00000000, count: -1
[ 6119.004023] iwlwifi 0000:05:00.0: Loaded firmware version: 25.30.14.0
[ 6119.004033] iwlwifi 0000:05:00.0: 0xFFFFFFFF | ADVANCED_SYSASSERT          
[ 6119.004040] iwlwifi 0000:05:00.0: 0xFFFFFFFF | uPc
[ 6119.004047] iwlwifi 0000:05:00.0: 0xFFFFFFFF | branchlink1
[ 6119.004053] iwlwifi 0000:05:00.0: 0xFFFFFFFF | branchlink2
[ 6119.004059] iwlwifi 0000:05:00.0: 0xFFFFFFFF | interruptlink1
[ 6119.004066] iwlwifi 0000:05:00.0: 0xFFFFFFFF | interruptlink2
[ 6119.004071] iwlwifi 0000:05:00.0: 0xFFFFFFFF | data1
[ 6119.004077] iwlwifi 0000:05:00.0: 0xFFFFFFFF | data2
[ 6119.004083] iwlwifi 0000:05:00.0: 0xFFFFFFFF | data3
[ 6119.004090] iwlwifi 0000:05:00.0: 0xFFFFFFFF | beacon time
[ 6119.004096] iwlwifi 0000:05:00.0: 0xFFFFFFFF | tsf low
[ 6119.004102] iwlwifi 0000:05:00.0: 0xFFFFFFFF | tsf hi
[ 6119.004107] iwlwifi 0000:05:00.0: 0xFFFFFFFF | time gp1
[ 6119.004113] iwlwifi 0000:05:00.0: 0xFFFFFFFF | time gp2
[ 6119.004121] iwlwifi 0000:05:00.0: 0xFFFFFFFF | time gp3
[ 6119.004127] iwlwifi 0000:05:00.0: 0xFFFFFFFF | uCode version
[ 6119.004133] iwlwifi 0000:05:00.0: 0xFFFFFFFF | hw version
[ 6119.004139] iwlwifi 0000:05:00.0: 0xFFFFFFFF | board version
[ 6119.004145] iwlwifi 0000:05:00.0: 0xFFFFFFFF | hcmd
[ 6119.004151] iwlwifi 0000:05:00.0: 0xFFFFFFFF | isr0
[ 6119.004156] iwlwifi 0000:05:00.0: 0xFFFFFFFF | isr1
[ 6119.004162] iwlwifi 0000:05:00.0: 0xFFFFFFFF | isr2
[ 6119.004167] iwlwifi 0000:05:00.0: 0xFFFFFFFF | isr3
[ 6119.004173] iwlwifi 0000:05:00.0: 0xFFFFFFFF | isr4
[ 6119.004178] iwlwifi 0000:05:00.0: 0xFFFFFFFF | isr_pref
[ 6119.004184] iwlwifi 0000:05:00.0: 0xFFFFFFFF | wait_event
[ 6119.004190] iwlwifi 0000:05:00.0: 0xFFFFFFFF | l2p_control
[ 6119.004195] iwlwifi 0000:05:00.0: 0xFFFFFFFF | l2p_duration
[ 6119.004201] iwlwifi 0000:05:00.0: 0xFFFFFFFF | l2p_mhvalid
[ 6119.004207] iwlwifi 0000:05:00.0: 0xFFFFFFFF | l2p_addr_match
[ 6119.004212] iwlwifi 0000:05:00.0: 0xFFFFFFFF | lmpm_pmg_sel
[ 6119.004218] iwlwifi 0000:05:00.0: 0xFFFFFFFF | timestamp
[ 6119.004224] iwlwifi 0000:05:00.0: 0xFFFFFFFF | flow_handler
[ 6119.091129] iwlwifi 0000:05:00.0: L1 Disabled - LTR Disabled
[ 6119.091222] iwlwifi 0000:05:00.0: L1 Disabled - LTR Disabled
[ 6124.086867] iwlwifi 0000:05:00.0: Failed to load firmware chunk!
[ 6124.086883] iwlwifi 0000:05:00.0: Could not load the [0] uCode section
[ 6124.086899] iwlwifi 0000:05:00.0: Failed to start INIT ucode: -110
[ 6124.086906] iwlwifi 0000:05:00.0: Failed to run INIT ucode: -110
[ 6124.087069] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 btusb uvcvideo btrtl btbcm btintel videobuf2_vmalloc videobuf2_memops bluetooth videobuf2_v4l2 videobuf2_core v4l2_common videodev media arc4 iwlmvm amd_freq_sensitivity kvm_amd kvm snd_hda_codec_realtek irqbypass snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec mac80211 snd_hda_core crct10dif_pclmul crc32_pclmul hp_wmi sparse_keymap aesni_intel snd_hwdep aes_x86_64 iwlwifi lrw gf128mul snd_pcm glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event snd_rawmidi edac_mce_amd cfg80211 edac_core snd_seq k10temp fam15h_power snd_seq_device snd_timer input_leds joydev serio_raw shpchp i2c_piix4 snd soundcore wmi hp_wireless
[ 6124.087612] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 btusb uvcvideo btrtl btbcm btintel videobuf2_vmalloc videobuf2_memops bluetooth videobuf2_v4l2 videobuf2_core v4l2_common videodev media arc4 iwlmvm amd_freq_sensitivity kvm_amd kvm snd_hda_codec_realtek irqbypass snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec mac80211 snd_hda_core crct10dif_pclmul crc32_pclmul hp_wmi sparse_keymap aesni_intel snd_hwdep aes_x86_64 iwlwifi lrw gf128mul snd_pcm glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event snd_rawmidi edac_mce_amd cfg80211 edac_core snd_seq k10temp fam15h_power snd_seq_device snd_timer input_leds joydev serio_raw shpchp i2c_piix4 snd soundcore wmi hp_wireless
[ 6124.088312] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 btusb uvcvideo btrtl btbcm btintel videobuf2_vmalloc videobuf2_memops bluetooth videobuf2_v4l2 videobuf2_core v4l2_common videodev media arc4 iwlmvm amd_freq_sensitivity kvm_amd kvm snd_hda_codec_realtek irqbypass snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec mac80211 snd_hda_core crct10dif_pclmul crc32_pclmul hp_wmi sparse_keymap aesni_intel snd_hwdep aes_x86_64 iwlwifi lrw gf128mul snd_pcm glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event snd_rawmidi edac_mce_amd cfg80211 edac_core snd_seq k10temp fam15h_power snd_seq_device snd_timer input_leds joydev serio_raw shpchp i2c_piix4 snd soundcore wmi hp_wireless
[ 6124.089873] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 btusb uvcvideo btrtl btbcm btintel videobuf2_vmalloc videobuf2_memops bluetooth videobuf2_v4l2 videobuf2_core v4l2_common videodev media arc4 iwlmvm amd_freq_sensitivity kvm_amd kvm snd_hda_codec_realtek irqbypass snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec mac80211 snd_hda_core crct10dif_pclmul crc32_pclmul hp_wmi sparse_keymap aesni_intel snd_hwdep aes_x86_64 iwlwifi lrw gf128mul snd_pcm glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event snd_rawmidi edac_mce_amd cfg80211 edac_core snd_seq k10temp fam15h_power snd_seq_device snd_timer input_leds joydev serio_raw shpchp i2c_piix4 snd soundcore wmi hp_wireless
[ 6124.091493] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 btusb uvcvideo btrtl btbcm btintel videobuf2_vmalloc videobuf2_memops bluetooth videobuf2_v4l2 videobuf2_core v4l2_common videodev media arc4 iwlmvm amd_freq_sensitivity kvm_amd kvm snd_hda_codec_realtek irqbypass snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec mac80211 snd_hda_core crct10dif_pclmul crc32_pclmul hp_wmi sparse_keymap aesni_intel snd_hwdep aes_x86_64 iwlwifi lrw gf128mul snd_pcm glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event snd_rawmidi edac_mce_amd cfg80211 edac_core snd_seq k10temp fam15h_power snd_seq_device snd_timer input_leds joydev serio_raw shpchp i2c_piix4 snd soundcore wmi hp_wireless
[ 6124.092810] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 btusb uvcvideo btrtl btbcm btintel videobuf2_vmalloc videobuf2_memops bluetooth videobuf2_v4l2 videobuf2_core v4l2_common videodev media arc4 iwlmvm amd_freq_sensitivity kvm_amd kvm snd_hda_codec_realtek irqbypass snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec mac80211 snd_hda_core crct10dif_pclmul crc32_pclmul hp_wmi sparse_keymap aesni_intel snd_hwdep aes_x86_64 iwlwifi lrw gf128mul snd_pcm glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event snd_rawmidi edac_mce_amd cfg80211 edac_core snd_seq k10temp fam15h_power snd_seq_device snd_timer input_leds joydev serio_raw shpchp i2c_piix4 snd soundcore wmi hp_wireless
[ 6124.094258] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 btusb uvcvideo btrtl btbcm btintel videobuf2_vmalloc videobuf2_memops bluetooth videobuf2_v4l2 videobuf2_core v4l2_common videodev media arc4 iwlmvm amd_freq_sensitivity kvm_amd kvm snd_hda_codec_realtek irqbypass snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec mac80211 snd_hda_core crct10dif_pclmul crc32_pclmul hp_wmi sparse_keymap aesni_intel snd_hwdep aes_x86_64 iwlwifi lrw gf128mul snd_pcm glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event snd_rawmidi edac_mce_amd cfg80211 edac_core snd_seq k10temp fam15h_power snd_seq_device snd_timer input_leds joydev serio_raw shpchp i2c_piix4 snd soundcore wmi hp_wireless
[ 6124.095566] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 btusb uvcvideo btrtl btbcm btintel videobuf2_vmalloc videobuf2_memops bluetooth videobuf2_v4l2 videobuf2_core v4l2_common videodev media arc4 iwlmvm amd_freq_sensitivity kvm_amd kvm snd_hda_codec_realtek irqbypass snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec mac80211 snd_hda_core crct10dif_pclmul crc32_pclmul hp_wmi sparse_keymap aesni_intel snd_hwdep aes_x86_64 iwlwifi lrw gf128mul snd_pcm glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event snd_rawmidi edac_mce_amd cfg80211 edac_core snd_seq k10temp fam15h_power snd_seq_device snd_timer input_leds joydev serio_raw shpchp i2c_piix4 snd soundcore wmi hp_wireless
[ 6124.096799] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 btusb uvcvideo btrtl btbcm btintel videobuf2_vmalloc videobuf2_memops bluetooth videobuf2_v4l2 videobuf2_core v4l2_common videodev media arc4 iwlmvm amd_freq_sensitivity kvm_amd kvm snd_hda_codec_realtek irqbypass snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec mac80211 snd_hda_core crct10dif_pclmul crc32_pclmul hp_wmi sparse_keymap aesni_intel snd_hwdep aes_x86_64 iwlwifi lrw gf128mul snd_pcm glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event snd_rawmidi edac_mce_amd cfg80211 edac_core snd_seq k10temp fam15h_power snd_seq_device snd_timer input_leds joydev serio_raw shpchp i2c_piix4 snd soundcore wmi hp_wireless
[ 6124.098859] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 btusb uvcvideo btrtl btbcm btintel videobuf2_vmalloc videobuf2_memops bluetooth videobuf2_v4l2 videobuf2_core v4l2_common videodev media arc4 iwlmvm amd_freq_sensitivity kvm_amd kvm snd_hda_codec_realtek irqbypass snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec mac80211 snd_hda_core crct10dif_pclmul crc32_pclmul hp_wmi sparse_keymap aesni_intel snd_hwdep aes_x86_64 iwlwifi lrw gf128mul snd_pcm glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event snd_rawmidi edac_mce_amd cfg80211 edac_core snd_seq k10temp fam15h_power snd_seq_device snd_timer input_leds joydev serio_raw shpchp i2c_piix4 snd soundcore wmi hp_wireless
[ 6124.100072] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 btusb uvcvideo btrtl btbcm btintel videobuf2_vmalloc videobuf2_memops bluetooth videobuf2_v4l2 videobuf2_core v4l2_common videodev media arc4 iwlmvm amd_freq_sensitivity kvm_amd kvm snd_hda_codec_realtek irqbypass snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec mac80211 snd_hda_core crct10dif_pclmul crc32_pclmul hp_wmi sparse_keymap aesni_intel snd_hwdep aes_x86_64 iwlwifi lrw gf128mul snd_pcm glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event snd_rawmidi edac_mce_amd cfg80211 edac_core snd_seq k10temp fam15h_power snd_seq_device snd_timer input_leds joydev serio_raw shpchp i2c_piix4 snd soundcore wmi hp_wireless
[ 6124.100899] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 btusb uvcvideo btrtl btbcm btintel videobuf2_vmalloc videobuf2_memops bluetooth videobuf2_v4l2 videobuf2_core v4l2_common videodev media arc4 iwlmvm amd_freq_sensitivity kvm_amd kvm snd_hda_codec_realtek irqbypass snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec mac80211 snd_hda_core crct10dif_pclmul crc32_pclmul hp_wmi sparse_keymap aesni_intel snd_hwdep aes_x86_64 iwlwifi lrw gf128mul snd_pcm glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event snd_rawmidi edac_mce_amd cfg80211 edac_core snd_seq k10temp fam15h_power snd_seq_device snd_timer input_leds joydev serio_raw shpchp i2c_piix4 snd soundcore wmi hp_wireless
[ 6124.101611] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 btusb uvcvideo btrtl btbcm btintel videobuf2_vmalloc videobuf2_memops bluetooth videobuf2_v4l2 videobuf2_core v4l2_common videodev media arc4 iwlmvm amd_freq_sensitivity kvm_amd kvm snd_hda_codec_realtek irqbypass snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec mac80211 snd_hda_core crct10dif_pclmul crc32_pclmul hp_wmi sparse_keymap aesni_intel snd_hwdep aes_x86_64 iwlwifi lrw gf128mul snd_pcm glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event snd_rawmidi edac_mce_amd cfg80211 edac_core snd_seq k10temp fam15h_power snd_seq_device snd_timer input_leds joydev serio_raw shpchp i2c_piix4 snd soundcore wmi hp_wireless
[ 6124.102336] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 btusb uvcvideo btrtl btbcm btintel videobuf2_vmalloc videobuf2_memops bluetooth videobuf2_v4l2 videobuf2_core v4l2_common videodev media arc4 iwlmvm amd_freq_sensitivity kvm_amd kvm snd_hda_codec_realtek irqbypass snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec mac80211 snd_hda_core crct10dif_pclmul crc32_pclmul hp_wmi sparse_keymap aesni_intel snd_hwdep aes_x86_64 iwlwifi lrw gf128mul snd_pcm glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event snd_rawmidi edac_mce_amd cfg80211 edac_core snd_seq k10temp fam15h_power snd_seq_device snd_timer input_leds joydev serio_raw shpchp i2c_piix4 snd soundcore wmi hp_wireless
[ 6124.103093] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 btusb uvcvideo btrtl btbcm btintel videobuf2_vmalloc videobuf2_memops bluetooth videobuf2_v4l2 videobuf2_core v4l2_common videodev media arc4 iwlmvm amd_freq_sensitivity kvm_amd kvm snd_hda_codec_realtek irqbypass snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec mac80211 snd_hda_core crct10dif_pclmul crc32_pclmul hp_wmi sparse_keymap aesni_intel snd_hwdep aes_x86_64 iwlwifi lrw gf128mul snd_pcm glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event snd_rawmidi edac_mce_amd cfg80211 edac_core snd_seq k10temp fam15h_power snd_seq_device snd_timer input_leds joydev serio_raw shpchp i2c_piix4 snd soundcore wmi hp_wireless
[ 6124.104752] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 btusb uvcvideo btrtl btbcm btintel videobuf2_vmalloc videobuf2_memops bluetooth videobuf2_v4l2 videobuf2_core v4l2_common videodev media arc4 iwlmvm amd_freq_sensitivity kvm_amd kvm snd_hda_codec_realtek irqbypass snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec mac80211 snd_hda_core crct10dif_pclmul crc32_pclmul hp_wmi sparse_keymap aesni_intel snd_hwdep aes_x86_64 iwlwifi lrw gf128mul snd_pcm glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event snd_rawmidi edac_mce_amd cfg80211 edac_core snd_seq k10temp fam15h_power snd_seq_device snd_timer input_leds joydev serio_raw shpchp i2c_piix4 snd soundcore wmi hp_wireless
[ 6124.105607] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 btusb uvcvideo btrtl btbcm btintel videobuf2_vmalloc videobuf2_memops bluetooth videobuf2_v4l2 videobuf2_core v4l2_common videodev media arc4 iwlmvm amd_freq_sensitivity kvm_amd kvm snd_hda_codec_realtek irqbypass snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec mac80211 snd_hda_core crct10dif_pclmul crc32_pclmul hp_wmi sparse_keymap aesni_intel snd_hwdep aes_x86_64 iwlwifi lrw gf128mul snd_pcm glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event snd_rawmidi edac_mce_amd cfg80211 edac_core snd_seq k10temp fam15h_power snd_seq_device snd_timer input_leds joydev serio_raw shpchp i2c_piix4 snd soundcore wmi hp_wireless
[ 6124.106292] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 btusb uvcvideo btrtl btbcm btintel videobuf2_vmalloc videobuf2_memops bluetooth videobuf2_v4l2 videobuf2_core v4l2_common videodev media arc4 iwlmvm amd_freq_sensitivity kvm_amd kvm snd_hda_codec_realtek irqbypass snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec mac80211 snd_hda_core crct10dif_pclmul crc32_pclmul hp_wmi sparse_keymap aesni_intel snd_hwdep aes_x86_64 iwlwifi lrw gf128mul snd_pcm glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event snd_rawmidi edac_mce_amd cfg80211 edac_core snd_seq k10temp fam15h_power snd_seq_device snd_timer input_leds joydev serio_raw shpchp i2c_piix4 snd soundcore wmi hp_wireless
[ 6124.107035] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 btusb uvcvideo btrtl btbcm btintel videobuf2_vmalloc videobuf2_memops bluetooth videobuf2_v4l2 videobuf2_core v4l2_common videodev media arc4 iwlmvm amd_freq_sensitivity kvm_amd kvm snd_hda_codec_realtek irqbypass snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec mac80211 snd_hda_core crct10dif_pclmul crc32_pclmul hp_wmi sparse_keymap aesni_intel snd_hwdep aes_x86_64 iwlwifi lrw gf128mul snd_pcm glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event snd_rawmidi edac_mce_amd cfg80211 edac_core snd_seq k10temp fam15h_power snd_seq_device snd_timer input_leds joydev serio_raw shpchp i2c_piix4 snd soundcore wmi hp_wireless
[ 6124.107919] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 btusb uvcvideo btrtl btbcm btintel videobuf2_vmalloc videobuf2_memops bluetooth videobuf2_v4l2 videobuf2_core v4l2_common videodev media arc4 iwlmvm amd_freq_sensitivity kvm_amd kvm snd_hda_codec_realtek irqbypass snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec mac80211 snd_hda_core crct10dif_pclmul crc32_pclmul hp_wmi sparse_keymap aesni_intel snd_hwdep aes_x86_64 iwlwifi lrw gf128mul snd_pcm glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event snd_rawmidi edac_mce_amd cfg80211 edac_core snd_seq k10temp fam15h_power snd_seq_device snd_timer input_leds joydev serio_raw shpchp i2c_piix4 snd soundcore wmi hp_wireless
[ 6124.108646] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 btusb uvcvideo btrtl btbcm btintel videobuf2_vmalloc videobuf2_memops bluetooth videobuf2_v4l2 videobuf2_core v4l2_common videodev media arc4 iwlmvm amd_freq_sensitivity kvm_amd kvm snd_hda_codec_realtek irqbypass snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec mac80211 snd_hda_core crct10dif_pclmul crc32_pclmul hp_wmi sparse_keymap aesni_intel snd_hwdep aes_x86_64 iwlwifi lrw gf128mul snd_pcm glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event snd_rawmidi edac_mce_amd cfg80211 edac_core snd_seq k10temp fam15h_power snd_seq_device snd_timer input_leds joydev serio_raw shpchp i2c_piix4 snd soundcore wmi hp_wireless
[ 6124.109293] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 btusb uvcvideo btrtl btbcm btintel videobuf2_vmalloc videobuf2_memops bluetooth videobuf2_v4l2 videobuf2_core v4l2_common videodev media arc4 iwlmvm amd_freq_sensitivity kvm_amd kvm snd_hda_codec_realtek irqbypass snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec mac80211 snd_hda_core crct10dif_pclmul crc32_pclmul hp_wmi sparse_keymap aesni_intel snd_hwdep aes_x86_64 iwlwifi lrw gf128mul snd_pcm glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event snd_rawmidi edac_mce_amd cfg80211 edac_core snd_seq k10temp fam15h_power snd_seq_device snd_timer input_leds joydev serio_raw shpchp i2c_piix4 snd soundcore wmi hp_wireless
[ 6124.109961] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 btusb uvcvideo btrtl btbcm btintel videobuf2_vmalloc videobuf2_memops bluetooth videobuf2_v4l2 videobuf2_core v4l2_common videodev media arc4 iwlmvm amd_freq_sensitivity kvm_amd kvm snd_hda_codec_realtek irqbypass snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec mac80211 snd_hda_core crct10dif_pclmul crc32_pclmul hp_wmi sparse_keymap aesni_intel snd_hwdep aes_x86_64 iwlwifi lrw gf128mul snd_pcm glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event snd_rawmidi edac_mce_amd cfg80211 edac_core snd_seq k10temp fam15h_power snd_seq_device snd_timer input_leds joydev serio_raw shpchp i2c_piix4 snd soundcore wmi hp_wireless
[ 6124.110645] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 btusb uvcvideo btrtl btbcm btintel videobuf2_vmalloc videobuf2_memops bluetooth videobuf2_v4l2 videobuf2_core v4l2_common videodev media arc4 iwlmvm amd_freq_sensitivity kvm_amd kvm snd_hda_codec_realtek irqbypass snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec mac80211 snd_hda_core crct10dif_pclmul crc32_pclmul hp_wmi sparse_keymap aesni_intel snd_hwdep aes_x86_64 iwlwifi lrw gf128mul snd_pcm glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event snd_rawmidi edac_mce_amd cfg80211 edac_core snd_seq k10temp fam15h_power snd_seq_device snd_timer input_leds joydev serio_raw shpchp i2c_piix4 snd soundcore wmi hp_wireless
[ 6124.111470] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 btusb uvcvideo btrtl btbcm btintel videobuf2_vmalloc videobuf2_memops bluetooth videobuf2_v4l2 videobuf2_core v4l2_common videodev media arc4 iwlmvm amd_freq_sensitivity kvm_amd kvm snd_hda_codec_realtek irqbypass snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec mac80211 snd_hda_core crct10dif_pclmul crc32_pclmul hp_wmi sparse_keymap aesni_intel snd_hwdep aes_x86_64 iwlwifi lrw gf128mul snd_pcm glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event snd_rawmidi edac_mce_amd cfg80211 edac_core snd_seq k10temp fam15h_power snd_seq_device snd_timer input_leds joydev serio_raw shpchp i2c_piix4 snd soundcore wmi hp_wireless
[ 6124.112610] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 btusb uvcvideo btrtl btbcm btintel videobuf2_vmalloc videobuf2_memops bluetooth videobuf2_v4l2 videobuf2_core v4l2_common videodev media arc4 iwlmvm amd_freq_sensitivity kvm_amd kvm snd_hda_codec_realtek irqbypass snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec mac80211 snd_hda_core crct10dif_pclmul crc32_pclmul hp_wmi sparse_keymap aesni_intel snd_hwdep aes_x86_64 iwlwifi lrw gf128mul snd_pcm glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event snd_rawmidi edac_mce_amd cfg80211 edac_core snd_seq k10temp fam15h_power snd_seq_device snd_timer input_leds joydev serio_raw shpchp i2c_piix4 snd soundcore wmi hp_wireless
[ 6124.113031] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 btusb uvcvideo btrtl btbcm btintel videobuf2_vmalloc videobuf2_memops bluetooth videobuf2_v4l2 videobuf2_core v4l2_common videodev media arc4 iwlmvm amd_freq_sensitivity kvm_amd kvm snd_hda_codec_realtek irqbypass snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec mac80211 snd_hda_core crct10dif_pclmul crc32_pclmul hp_wmi sparse_keymap aesni_intel snd_hwdep aes_x86_64 iwlwifi lrw gf128mul snd_pcm glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event snd_rawmidi edac_mce_amd cfg80211 edac_core snd_seq k10temp fam15h_power snd_seq_device snd_timer input_leds joydev serio_raw shpchp i2c_piix4 snd soundcore wmi hp_wireless

```

---

### Post by chili555 on 2016-10-09
> loaded firmware version 25.30.[COLOR="#FF0000"]14[/COLOR].0 op_mode iwlmvmI suggest, at least to start, that you update the firmware:```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.161_all.deb
sudo dpkg -i linux*.deb
```Reboot and let us hear your report. Please include:```
dmesg | grep iwl
```> i updated last night to the latest intel drivers from here: [http://www.intel.com/content/www/us/...000005511.html](http://www.intel.com/content/www/us/...000005511.html) Sadly, that isn't the latest firmware.

---

### Post by ross-spencer on 2016-10-09
Thx for the reply. How would i have checked that wasn't the latest firmware otherwise? 

I've run the command, and rebooted. Here's the dmesg output: 
```

[   14.296800] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-7265D-19.ucode failed with error -2
[   14.299746] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-7265D-18.ucode failed with error -2
[   14.751689] iwlwifi 0000:05:00.0: loaded firmware version 17.352738.0 op_mode iwlmvm
[   15.448032] iwlwifi 0000:05:00.0: Detected Intel(R) Dual Band Wireless AC 3165, REV=0x210
[   15.448162] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[   15.448360] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[   15.531126] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   15.553980] iwlwifi 0000:05:00.0 wlo1: renamed from wlan0
[   31.836537] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[   31.836735] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[   31.896669] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[   31.896860] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[  458.048488] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  458.048623] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
[  458.067046] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  458.067122] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
[  464.048913] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  464.049021] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
[  464.067097] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  464.067175] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
[  464.860315] iwlwifi 0000:05:00.0: Queue 2 stuck for 10000 ms.
[  464.860336] iwlwifi 0000:05:00.0: Current SW read_ptr 110 write_ptr 131
[  464.878183] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/pcie/trans.c:1552 iwl_trans_pcie_grab_nic_access+0xfb/0x110 [iwlwifi]()
[  464.878195] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  464.878522]  [<ffffffffc049a13f>] ? iwl_read32+0x1f/0x90 [iwlwifi]
[  464.878550]  [<ffffffffc04a961b>] iwl_trans_pcie_grab_nic_access+0xfb/0x110 [iwlwifi]
[  464.878576]  [<ffffffffc04a740e>] iwl_trans_pcie_read_mem+0x3e/0xc0 [iwlwifi]
[  464.878602]  [<ffffffffc04a33bc>] iwl_pcie_txq_stuck_timer+0xdc/0x390 [iwlwifi]
[  464.878639]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  464.878677]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  464.878979] iwl data: 00000000: c0 8d a7 15 01 00 00 00 00 dd c8 1e 02 88 ff ff  ................
[  464.896921] iwlwifi 0000:05:00.0: FH TRBs(0) = 0x5a5a5a5a
[  464.914796] iwlwifi 0000:05:00.0: FH TRBs(1) = 0x5a5a5a5a
[  464.932747] iwlwifi 0000:05:00.0: FH TRBs(2) = 0x5a5a5a5a
[  464.950675] iwlwifi 0000:05:00.0: FH TRBs(3) = 0x5a5a5a5a
[  464.968584] iwlwifi 0000:05:00.0: FH TRBs(4) = 0x5a5a5a5a
[  464.986482] iwlwifi 0000:05:00.0: FH TRBs(5) = 0x5a5a5a5a
[  465.004397] iwlwifi 0000:05:00.0: FH TRBs(6) = 0x5a5a5a5a
[  465.022328] iwlwifi 0000:05:00.0: FH TRBs(7) = 0x5a5a5a5a
[  465.058177] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  465.058183] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  465.058468]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  465.058494]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.058530]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.094463] iwlwifi 0000:05:00.0: Q 0 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  465.130263] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  465.130269] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  465.130552]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  465.130578]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.130615]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.166576] iwlwifi 0000:05:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  465.202412] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  465.202417] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  465.202693]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  465.202719]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.202755]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.238722] iwlwifi 0000:05:00.0: Q 2 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  465.274563] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  465.274568] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  465.274843]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  465.274868]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.274906]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.310869] iwlwifi 0000:05:00.0: Q 3 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  465.346677] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  465.346683] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  465.346959]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  465.346984]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.347020]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.382947] iwlwifi 0000:05:00.0: Q 4 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  465.418789] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  465.418795] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  465.419075]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  465.419100]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.419136]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.455075] iwlwifi 0000:05:00.0: Q 5 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  465.490885] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  465.490891] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  465.491168]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  465.491195]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.491232]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.527273] iwlwifi 0000:05:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  465.563119] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  465.563124] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  465.563402]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  465.563427]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.563465]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.599390] iwlwifi 0000:05:00.0: Q 7 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  465.635233] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  465.635239] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  465.635516]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  465.635542]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.635579]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.671482] iwlwifi 0000:05:00.0: Q 8 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  465.707330] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  465.707336] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  465.707610]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  465.707636]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.707672]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.743677] iwlwifi 0000:05:00.0: Q 9 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  465.779505] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  465.779511] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  465.779790]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  465.779816]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.779853]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.815791] iwlwifi 0000:05:00.0: Q 10 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  465.851621] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  465.851627] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  465.851908]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  465.851933]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.851970]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.887927] iwlwifi 0000:05:00.0: Q 11 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  465.923771] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  465.923777] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  465.924052]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  465.924078]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.924114]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.960085] iwlwifi 0000:05:00.0: Q 12 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  465.995899] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  465.995905] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  465.996183]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  465.996208]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.996244]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.032233] iwlwifi 0000:05:00.0: Q 13 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  466.068071] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  466.068077] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  466.068358]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  466.068385]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.068424]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.104415] iwlwifi 0000:05:00.0: Q 14 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  466.140277] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  466.140283] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  466.140645]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  466.140671]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.140723]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.176671] iwlwifi 0000:05:00.0: Q 15 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  466.212520] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  466.212526] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  466.212805]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  466.212831]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.212867]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.248833] iwlwifi 0000:05:00.0: Q 16 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  466.284656] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  466.284662] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  466.284936]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  466.284962]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.284997]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.320934] iwlwifi 0000:05:00.0: Q 17 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  466.356819] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  466.356825] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  466.357101]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  466.357127]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.357163]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.393126] iwlwifi 0000:05:00.0: Q 18 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  466.428922] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  466.428928] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  466.429200]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  466.429226]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.429261]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.465229] iwlwifi 0000:05:00.0: Q 19 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  466.501025] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  466.501031] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  466.501306]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  466.501332]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.501369]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.537304] iwlwifi 0000:05:00.0: Q 20 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  466.573176] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  466.573182] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  466.573459]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  466.573485]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.573521]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.609517] iwlwifi 0000:05:00.0: Q 21 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  466.645343] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  466.645348] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  466.645618]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  466.645644]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.645681]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.681617] iwlwifi 0000:05:00.0: Q 22 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  466.717430] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  466.717435] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  466.717709]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  466.717734]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.717770]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.753741] iwlwifi 0000:05:00.0: Q 23 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  466.789639] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  466.789645] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  466.789920]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  466.789946]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.789981]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.825921] iwlwifi 0000:05:00.0: Q 24 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  466.861764] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  466.861770] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  466.862043]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  466.862068]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.862104]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.898171] iwlwifi 0000:05:00.0: Q 25 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  466.934021] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  466.934027] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  466.934302]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  466.934328]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.934364]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.970325] iwlwifi 0000:05:00.0: Q 26 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  467.006227] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  467.006233] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  467.006506]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  467.006532]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  467.006568]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  467.042575] iwlwifi 0000:05:00.0: Q 27 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  467.078407] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  467.078413] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  467.078688]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  467.078714]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  467.078750]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  467.114663] iwlwifi 0000:05:00.0: Q 28 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  467.150523] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  467.150529] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  467.150809]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  467.150835]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  467.150871]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  467.186834] iwlwifi 0000:05:00.0: Q 29 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  467.222691] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  467.222696] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  467.222970]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  467.222996]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  467.223032]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  467.259024] iwlwifi 0000:05:00.0: Q 30 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  470.049014] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  470.049125] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
[  470.067221] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  470.067299] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
[  476.050187] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  476.050291] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
[  476.068381] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  476.068467] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
[  482.048861] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  482.048983] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
[  482.066871] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  482.066950] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
[  488.051070] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  488.051200] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
[  488.069179] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  488.069237] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
[  494.045452] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  494.045567] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
[  494.065124] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  494.065204] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
[  500.047854] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  500.047989] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
[  500.066118] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  500.066189] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5

```

---

### Post by chili555 on 2016-10-09
Much better.> Works for an undetermined amount of time before failing. Is this still the case? What are the clues in the log after it fails?```
dmesg | grep -e iwl -e wlo1
```

---

### Post by ross-spencer on 2016-10-09
Oh yep, sorry, i edited the above, but here's the response now, it failed as i was fixing the original: 
 
```

[   14.296800] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-7265D-19.ucode failed with error -2
[   14.299746] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-7265D-18.ucode failed with error -2
[   14.751689] iwlwifi 0000:05:00.0: loaded firmware version 17.352738.0 op_mode iwlmvm
[   15.448032] iwlwifi 0000:05:00.0: Detected Intel(R) Dual Band Wireless AC 3165, REV=0x210
[   15.448162] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[   15.448360] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[   15.531126] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   15.553980] iwlwifi 0000:05:00.0 wlo1: renamed from wlan0
[   31.836537] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[   31.836735] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[   31.896669] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[   31.896860] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[  458.048488] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  458.048623] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
[  458.067046] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  458.067122] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
[  464.048913] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  464.049021] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
[  464.067097] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  464.067175] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
[  464.860315] iwlwifi 0000:05:00.0: Queue 2 stuck for 10000 ms.
[  464.860336] iwlwifi 0000:05:00.0: Current SW read_ptr 110 write_ptr 131
[  464.878183] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/pcie/trans.c:1552 iwl_trans_pcie_grab_nic_access+0xfb/0x110 [iwlwifi]()
[  464.878195] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  464.878522]  [<ffffffffc049a13f>] ? iwl_read32+0x1f/0x90 [iwlwifi]
[  464.878550]  [<ffffffffc04a961b>] iwl_trans_pcie_grab_nic_access+0xfb/0x110 [iwlwifi]
[  464.878576]  [<ffffffffc04a740e>] iwl_trans_pcie_read_mem+0x3e/0xc0 [iwlwifi]
[  464.878602]  [<ffffffffc04a33bc>] iwl_pcie_txq_stuck_timer+0xdc/0x390 [iwlwifi]
[  464.878639]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  464.878677]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  464.878979] iwl data: 00000000: c0 8d a7 15 01 00 00 00 00 dd c8 1e 02 88 ff ff  ................
[  464.896921] iwlwifi 0000:05:00.0: FH TRBs(0) = 0x5a5a5a5a
[  464.914796] iwlwifi 0000:05:00.0: FH TRBs(1) = 0x5a5a5a5a
[  464.932747] iwlwifi 0000:05:00.0: FH TRBs(2) = 0x5a5a5a5a
[  464.950675] iwlwifi 0000:05:00.0: FH TRBs(3) = 0x5a5a5a5a
[  464.968584] iwlwifi 0000:05:00.0: FH TRBs(4) = 0x5a5a5a5a
[  464.986482] iwlwifi 0000:05:00.0: FH TRBs(5) = 0x5a5a5a5a
[  465.004397] iwlwifi 0000:05:00.0: FH TRBs(6) = 0x5a5a5a5a
[  465.022328] iwlwifi 0000:05:00.0: FH TRBs(7) = 0x5a5a5a5a
[  465.058177] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  465.058183] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  465.058468]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  465.058494]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.058530]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.094463] iwlwifi 0000:05:00.0: Q 0 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  465.130263] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  465.130269] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  465.130552]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  465.130578]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.130615]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.166576] iwlwifi 0000:05:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  465.202412] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  465.202417] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  465.202693]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  465.202719]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.202755]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.238722] iwlwifi 0000:05:00.0: Q 2 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  465.274563] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  465.274568] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  465.274843]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  465.274868]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.274906]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.310869] iwlwifi 0000:05:00.0: Q 3 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  465.346677] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  465.346683] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  465.346959]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  465.346984]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.347020]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.382947] iwlwifi 0000:05:00.0: Q 4 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  465.418789] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  465.418795] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  465.419075]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  465.419100]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.419136]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.455075] iwlwifi 0000:05:00.0: Q 5 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  465.490885] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  465.490891] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  465.491168]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  465.491195]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.491232]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.527273] iwlwifi 0000:05:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  465.563119] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  465.563124] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  465.563402]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  465.563427]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.563465]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.599390] iwlwifi 0000:05:00.0: Q 7 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  465.635233] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  465.635239] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  465.635516]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  465.635542]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.635579]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.671482] iwlwifi 0000:05:00.0: Q 8 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  465.707330] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  465.707336] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  465.707610]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  465.707636]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.707672]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.743677] iwlwifi 0000:05:00.0: Q 9 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  465.779505] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  465.779511] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  465.779790]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  465.779816]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.779853]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.815791] iwlwifi 0000:05:00.0: Q 10 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  465.851621] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  465.851627] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  465.851908]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  465.851933]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.851970]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.887927] iwlwifi 0000:05:00.0: Q 11 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  465.923771] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  465.923777] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  465.924052]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  465.924078]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.924114]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.960085] iwlwifi 0000:05:00.0: Q 12 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  465.995899] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  465.995905] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  465.996183]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  465.996208]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  465.996244]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.032233] iwlwifi 0000:05:00.0: Q 13 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  466.068071] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  466.068077] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  466.068358]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  466.068385]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.068424]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.104415] iwlwifi 0000:05:00.0: Q 14 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  466.140277] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  466.140283] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  466.140645]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  466.140671]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.140723]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.176671] iwlwifi 0000:05:00.0: Q 15 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  466.212520] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  466.212526] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  466.212805]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  466.212831]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.212867]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.248833] iwlwifi 0000:05:00.0: Q 16 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  466.284656] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  466.284662] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  466.284936]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  466.284962]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.284997]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.320934] iwlwifi 0000:05:00.0: Q 17 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  466.356819] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  466.356825] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  466.357101]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  466.357127]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.357163]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.393126] iwlwifi 0000:05:00.0: Q 18 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  466.428922] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  466.428928] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  466.429200]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  466.429226]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.429261]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.465229] iwlwifi 0000:05:00.0: Q 19 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  466.501025] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  466.501031] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  466.501306]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  466.501332]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.501369]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.537304] iwlwifi 0000:05:00.0: Q 20 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  466.573176] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  466.573182] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  466.573459]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  466.573485]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.573521]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.609517] iwlwifi 0000:05:00.0: Q 21 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  466.645343] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  466.645348] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  466.645618]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  466.645644]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.645681]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.681617] iwlwifi 0000:05:00.0: Q 22 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  466.717430] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  466.717435] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  466.717709]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  466.717734]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.717770]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.753741] iwlwifi 0000:05:00.0: Q 23 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  466.789639] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  466.789645] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  466.789920]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  466.789946]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.789981]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.825921] iwlwifi 0000:05:00.0: Q 24 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  466.861764] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  466.861770] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  466.862043]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  466.862068]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.862104]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.898171] iwlwifi 0000:05:00.0: Q 25 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  466.934021] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  466.934027] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  466.934302]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  466.934328]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.934364]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  466.970325] iwlwifi 0000:05:00.0: Q 26 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  467.006227] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  467.006233] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  467.006506]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  467.006532]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  467.006568]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  467.042575] iwlwifi 0000:05:00.0: Q 27 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  467.078407] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  467.078413] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  467.078688]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  467.078714]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  467.078750]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  467.114663] iwlwifi 0000:05:00.0: Q 28 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  467.150523] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  467.150529] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  467.150809]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  467.150835]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  467.150871]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  467.186834] iwlwifi 0000:05:00.0: Q 29 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  467.222691] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]()
[  467.222696] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  467.222970]  [<ffffffffc04a359d>] iwl_pcie_txq_stuck_timer+0x2bd/0x390 [iwlwifi]
[  467.222996]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  467.223032]  [<ffffffffc04a32e0>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
[  467.259024] iwlwifi 0000:05:00.0: Q 30 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[  470.049014] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  470.049125] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
[  470.067221] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  470.067299] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
[  476.050187] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  476.050291] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
[  476.068381] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  476.068467] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
[  482.048861] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  482.048983] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
[  482.066871] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  482.066950] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
[  488.051070] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  488.051200] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
[  488.069179] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  488.069237] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
[  494.045452] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  494.045567] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
[  494.065124] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  494.065204] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
[  500.047854] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  500.047989] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
[  500.066118] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd
[  500.066189] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5

```

---

### Post by ross-spencer on 2016-10-09
And using your other grep pattern:

```
[   31.836329] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready[   31.911277] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[   33.136201] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[   62.105022] wlo1: authenticate with 00:60:64:8b:02:2e
[   62.108070] wlo1: send auth to 00:60:64:8b:02:2e (try 1/3)
[   62.110187] wlo1: authenticated
[   62.114550] wlo1: associate with 00:60:64:8b:02:2e (try 1/3)
[   62.122922] wlo1: RX AssocResp from 00:60:64:8b:02:2e (capab=0x411 status=0 aid=1)
[   62.123673] wlo1: associated
[   62.123746] IPv6: ADDRCONF(NETDEV_CHANGE): wlo1: link becomes ready
```

---

### Post by chili555 on 2016-10-09
> [  464.860315] iwlwifi 0000:05:00.0: Queue 2 stuck for 10000 ms.
[  464.860336] iwlwifi 0000:05:00.0: Current SW read_ptr 110 write_ptr 131
[  464.878183] WARNING: CPU: 1 PID: 0 at /build/linux-R0TiM8/linux-4.4.0/drivers/net/wireless/iwlwifi/pcie/trans.c:1552 iwl_trans_pcie_grab_nic_access+0xfb/0x110 [iwlwifi]()
[  464.878195] Modules linked in: drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common arc4 videodev media amd_freq_sensitivity iwlmvm kvm_amd kvm btusb btrtl mac80211 irqbypass btbcm btintel bluetooth hp_wmi snd_hda_codec_realtek crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi sparse_keymap snd_hda_intel snd_hda_codec aesni_intel snd_hda_core iwlwifi aes_x86_64 lrw snd_hwdep gf128mul glue_helper ablk_helper cryptd cfg80211 input_leds snd_pcm snd_seq_midi joydev serio_raw snd_seq_midi_event snd_rawmidi k10temp edac_mce_amd edac_core snd_seq i2c_piix4 fam15h_power snd_seq_device snd_timer shpchp snd soundcore wmi hp_wireless
[  464.878522]  [<ffffffffc049a13f>] ? iwl_read32+0x1f/0x90 [iwlwifi]
[  464.878550]  [<ffffffffc04a961b>] iwl_trans_pcie_grab_nic_access+0xfb/0x110 [iwlwifi]
<snip>To use a highly technical term, that's a train wreck!

Let's turn off power management and see if it helps.```
sudo -i
echo "options iwlwifi power_save=0"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Reboot and test.

---

### Post by ross-spencer on 2016-10-10
Thanky you so much for your help on this. 

I followed your instructions and turned off power management, and have been running Wi-Fi for about eight hours now. 

Dmesg looks good:

```
[   14.339491] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-7265D-19.ucode failed with error -2[   14.431322] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-7265D-18.ucode failed with error -2
[   14.561310] iwlwifi 0000:05:00.0: loaded firmware version 17.352738.0 op_mode iwlmvm
[   15.023700] iwlwifi 0000:05:00.0: Detected Intel(R) Dual Band Wireless AC 3165, REV=0x210
[   15.023814] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[   15.024011] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[   15.240408] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   15.341169] iwlwifi 0000:05:00.0 wlo1: renamed from wlan0
[   31.465667] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[   31.465889] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[   31.526015] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[   31.526208] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[  223.438390] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[  223.438616] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[  223.499157] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[  223.499360] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled

```

I can mark this as solved in a day or two.

As I'm still learning is power management a known issue for these cards or does it just prevent the symptoms of something else? 

Either way, looking good so far. Thank you.

---

### Post by chili555 on 2016-10-10
> As I'm still learning is power management a known issue for these cards or does it just prevent the symptoms of something else? 
I think it's actually a problem with Network Manager. I also think it is scheduled to be fixed in an update. In the meantime, the practical user slaps a bandage on the problem and soldiers on.

I myself use an Intel 7260 without any problem at all. It's a mystery.

Your *dmesg* looks awesome.

---

### Post by ross-spencer on 2016-10-13
I don't mind a band-aid, especially if a fix seems to be on the horizon. 

Unfortunately this time it crashed again after a day, is this message useful to help at all?

```
[   18.186543] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-7265D-19.ucode failed with error -2[   18.186887] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-7265D-18.ucode failed with error -2
[   18.494381] iwlwifi 0000:05:00.0: loaded firmware version 17.352738.0 op_mode iwlmvm
[   18.968217] iwlwifi 0000:05:00.0: Detected Intel(R) Dual Band Wireless AC 3165, REV=0x210
[   18.968306] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[   18.968531] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[   19.084667] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   19.452244] iwlwifi 0000:05:00.0 wlo1: renamed from wlan0
[   39.477553] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[   39.477751] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[   39.537593] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[   39.537786] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[13305.442705] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[13305.442902] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[13305.502753] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[13305.502955] iwlwifi 0000:05:00.0: L1 Enabled - LTR Disabled
[15440.927629] iwlwifi 0000:05:00.0: Error sending STATISTICS_CMD: time out after 2000ms.
[15440.927644] iwlwifi 0000:05:00.0: Current CMD queue read_ptr 91 write_ptr 92
[15440.927730] iwlwifi 0000:05:00.0: Start IWL Error Log Dump:
[15440.927738] iwlwifi 0000:05:00.0: Status: 0x00000000, count: -1
[15440.927743] iwlwifi 0000:05:00.0: Loaded firmware version: 17.352738.0
[15440.927750] iwlwifi 0000:05:00.0: 0xFFFFFFFF | ADVANCED_SYSASSERT          
[15440.927756] iwlwifi 0000:05:00.0: 0xFFFFFFFF | uPc
[15440.927762] iwlwifi 0000:05:00.0: 0xFFFFFFFF | branchlink1
[15440.927767] iwlwifi 0000:05:00.0: 0xFFFFFFFF | branchlink2
[15440.927773] iwlwifi 0000:05:00.0: 0xFFFFFFFF | interruptlink1
[15440.927778] iwlwifi 0000:05:00.0: 0xFFFFFFFF | interruptlink2
[15440.927783] iwlwifi 0000:05:00.0: 0xFFFFFFFF | data1
[15440.927788] iwlwifi 0000:05:00.0: 0xFFFFFFFF | data2
[15440.927793] iwlwifi 0000:05:00.0: 0xFFFFFFFF | data3
[15440.927798] iwlwifi 0000:05:00.0: 0xFFFFFFFF | beacon time
[15440.927803] iwlwifi 0000:05:00.0: 0xFFFFFFFF | tsf low
[15440.927807] iwlwifi 0000:05:00.0: 0xFFFFFFFF | tsf hi
[15440.927812] iwlwifi 0000:05:00.0: 0xFFFFFFFF | time gp1
[15440.927817] iwlwifi 0000:05:00.0: 0xFFFFFFFF | time gp2
[15440.927822] iwlwifi 0000:05:00.0: 0xFFFFFFFF | time gp3
[15440.927827] iwlwifi 0000:05:00.0: 0xFFFFFFFF | uCode version major
[15440.927832] iwlwifi 0000:05:00.0: 0xFFFFFFFF | uCode version minor
[15440.927837] iwlwifi 0000:05:00.0: 0xFFFFFFFF | hw version
[15440.927842] iwlwifi 0000:05:00.0: 0xFFFFFFFF | board version
[15440.927847] iwlwifi 0000:05:00.0: 0xFFFFFFFF | hcmd
[15440.927851] iwlwifi 0000:05:00.0: 0xFFFFFFFF | isr0
[15440.927856] iwlwifi 0000:05:00.0: 0xFFFFFFFF | isr1
[15440.927861] iwlwifi 0000:05:00.0: 0xFFFFFFFF | isr2
[15440.927866] iwlwifi 0000:05:00.0: 0xFFFFFFFF | isr3
[15440.927872] iwlwifi 0000:05:00.0: 0xFFFFFFFF | isr4
[15440.927877] iwlwifi 0000:05:00.0: 0xFFFFFFFF | isr_pref
[15440.927882] iwlwifi 0000:05:00.0: 0xFFFFFFFF | wait_event
[15440.927886] iwlwifi 0000:05:00.0: 0xFFFFFFFF | l2p_control
[15440.927891] iwlwifi 0000:05:00.0: 0xFFFFFFFF | l2p_duration
[15440.927896] iwlwifi 0000:05:00.0: 0xFFFFFFFF | l2p_mhvalid
[15440.927901] iwlwifi 0000:05:00.0: 0xFFFFFFFF | l2p_addr_match
[15440.927906] iwlwifi 0000:05:00.0: 0xFFFFFFFF | lmpm_pmg_sel
[15440.927910] iwlwifi 0000:05:00.0: 0xFFFFFFFF | timestamp
[15440.927915] iwlwifi 0000:05:00.0: 0xFFFFFFFF | flow_handler
[15441.012425] iwlwifi 0000:05:00.0: L1 Disabled - LTR Disabled
[15441.012490] iwlwifi 0000:05:00.0: L1 Disabled - LTR Disabled
[15446.011571] iwlwifi 0000:05:00.0: Failed to load firmware chunk!
[15446.011583] iwlwifi 0000:05:00.0: Could not load the [0] uCode section
[15446.011596] iwlwifi 0000:05:00.0: Failed to start INIT ucode: -110
[15446.011601] iwlwifi 0000:05:00.0: Failed to run INIT ucode: -110
[15446.011761] Modules linked in: btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 amd_freq_sensitivity videobuf2_core kvm_amd kvm v4l2_common irqbypass arc4 videodev btusb media iwlmvm crct10dif_pclmul crc32_pclmul btrtl aesni_intel btbcm btintel mac80211 aes_x86_64 bluetooth lrw hp_wmi sparse_keymap gf128mul glue_helper ablk_helper iwlwifi cryptd input_leds joydev cfg80211 serio_raw fam15h_power k10temp edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec edac_core snd_hda_core snd_seq_midi snd_seq_midi_event snd_rawmidi shpchp snd_hwdep snd_pcm
[15446.012227] Modules linked in: btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 amd_freq_sensitivity videobuf2_core kvm_amd kvm v4l2_common irqbypass arc4 videodev btusb media iwlmvm crct10dif_pclmul crc32_pclmul btrtl aesni_intel btbcm btintel mac80211 aes_x86_64 bluetooth lrw hp_wmi sparse_keymap gf128mul glue_helper ablk_helper iwlwifi cryptd input_leds joydev cfg80211 serio_raw fam15h_power k10temp edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec edac_core snd_hda_core snd_seq_midi snd_seq_midi_event snd_rawmidi shpchp snd_hwdep snd_pcm
[15446.012755] Modules linked in: btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 amd_freq_sensitivity videobuf2_core kvm_amd kvm v4l2_common irqbypass arc4 videodev btusb media iwlmvm crct10dif_pclmul crc32_pclmul btrtl aesni_intel btbcm btintel mac80211 aes_x86_64 bluetooth lrw hp_wmi sparse_keymap gf128mul glue_helper ablk_helper iwlwifi cryptd input_leds joydev cfg80211 serio_raw fam15h_power k10temp edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec edac_core snd_hda_core snd_seq_midi snd_seq_midi_event snd_rawmidi shpchp snd_hwdep snd_pcm
[15446.013481] Modules linked in: btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 amd_freq_sensitivity videobuf2_core kvm_amd kvm v4l2_common irqbypass arc4 videodev btusb media iwlmvm crct10dif_pclmul crc32_pclmul btrtl aesni_intel btbcm btintel mac80211 aes_x86_64 bluetooth lrw hp_wmi sparse_keymap gf128mul glue_helper ablk_helper iwlwifi cryptd input_leds joydev cfg80211 serio_raw fam15h_power k10temp edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec edac_core snd_hda_core snd_seq_midi snd_seq_midi_event snd_rawmidi shpchp snd_hwdep snd_pcm
[15446.014183] Modules linked in: btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 amd_freq_sensitivity videobuf2_core kvm_amd kvm v4l2_common irqbypass arc4 videodev btusb media iwlmvm crct10dif_pclmul crc32_pclmul btrtl aesni_intel btbcm btintel mac80211 aes_x86_64 bluetooth lrw hp_wmi sparse_keymap gf128mul glue_helper ablk_helper iwlwifi cryptd input_leds joydev cfg80211 serio_raw fam15h_power k10temp edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec edac_core snd_hda_core snd_seq_midi snd_seq_midi_event snd_rawmidi shpchp snd_hwdep snd_pcm
[15446.014861] Modules linked in: btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 amd_freq_sensitivity videobuf2_core kvm_amd kvm v4l2_common irqbypass arc4 videodev btusb media iwlmvm crct10dif_pclmul crc32_pclmul btrtl aesni_intel btbcm btintel mac80211 aes_x86_64 bluetooth lrw hp_wmi sparse_keymap gf128mul glue_helper ablk_helper iwlwifi cryptd input_leds joydev cfg80211 serio_raw fam15h_power k10temp edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec edac_core snd_hda_core snd_seq_midi snd_seq_midi_event snd_rawmidi shpchp snd_hwdep snd_pcm
[15446.015662] Modules linked in: btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 amd_freq_sensitivity videobuf2_core kvm_amd kvm v4l2_common irqbypass arc4 videodev btusb media iwlmvm crct10dif_pclmul crc32_pclmul btrtl aesni_intel btbcm btintel mac80211 aes_x86_64 bluetooth lrw hp_wmi sparse_keymap gf128mul glue_helper ablk_helper iwlwifi cryptd input_leds joydev cfg80211 serio_raw fam15h_power k10temp edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec edac_core snd_hda_core snd_seq_midi snd_seq_midi_event snd_rawmidi shpchp snd_hwdep snd_pcm
[15446.018737] Modules linked in: btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 amd_freq_sensitivity videobuf2_core kvm_amd kvm v4l2_common irqbypass arc4 videodev btusb media iwlmvm crct10dif_pclmul crc32_pclmul btrtl aesni_intel btbcm btintel mac80211 aes_x86_64 bluetooth lrw hp_wmi sparse_keymap gf128mul glue_helper ablk_helper iwlwifi cryptd input_leds joydev cfg80211 serio_raw fam15h_power k10temp edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec edac_core snd_hda_core snd_seq_midi snd_seq_midi_event snd_rawmidi shpchp snd_hwdep snd_pcm
[15446.019782] Modules linked in: btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 amd_freq_sensitivity videobuf2_core kvm_amd kvm v4l2_common irqbypass arc4 videodev btusb media iwlmvm crct10dif_pclmul crc32_pclmul btrtl aesni_intel btbcm btintel mac80211 aes_x86_64 bluetooth lrw hp_wmi sparse_keymap gf128mul glue_helper ablk_helper iwlwifi cryptd input_leds joydev cfg80211 serio_raw fam15h_power k10temp edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec edac_core snd_hda_core snd_seq_midi snd_seq_midi_event snd_rawmidi shpchp snd_hwdep snd_pcm
[15446.020612] Modules linked in: btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 amd_freq_sensitivity videobuf2_core kvm_amd kvm v4l2_common irqbypass arc4 videodev btusb media iwlmvm crct10dif_pclmul crc32_pclmul btrtl aesni_intel btbcm btintel mac80211 aes_x86_64 bluetooth lrw hp_wmi sparse_keymap gf128mul glue_helper ablk_helper iwlwifi cryptd input_leds joydev cfg80211 serio_raw fam15h_power k10temp edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec edac_core snd_hda_core snd_seq_midi snd_seq_midi_event snd_rawmidi shpchp snd_hwdep snd_pcm
[15446.021375] Modules linked in: btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 amd_freq_sensitivity videobuf2_core kvm_amd kvm v4l2_common irqbypass arc4 videodev btusb media iwlmvm crct10dif_pclmul crc32_pclmul btrtl aesni_intel btbcm btintel mac80211 aes_x86_64 bluetooth lrw hp_wmi sparse_keymap gf128mul glue_helper ablk_helper iwlwifi cryptd input_leds joydev cfg80211 serio_raw fam15h_power k10temp edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec edac_core snd_hda_core snd_seq_midi snd_seq_midi_event snd_rawmidi shpchp snd_hwdep snd_pcm
[15446.022076] Modules linked in: btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 amd_freq_sensitivity videobuf2_core kvm_amd kvm v4l2_common irqbypass arc4 videodev btusb media iwlmvm crct10dif_pclmul crc32_pclmul btrtl aesni_intel btbcm btintel mac80211 aes_x86_64 bluetooth lrw hp_wmi sparse_keymap gf128mul glue_helper ablk_helper iwlwifi cryptd input_leds joydev cfg80211 serio_raw fam15h_power k10temp edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec edac_core snd_hda_core snd_seq_midi snd_seq_midi_event snd_rawmidi shpchp snd_hwdep snd_pcm
[15446.022696] Modules linked in: btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 amd_freq_sensitivity videobuf2_core kvm_amd kvm v4l2_common irqbypass arc4 videodev btusb media iwlmvm crct10dif_pclmul crc32_pclmul btrtl aesni_intel btbcm btintel mac80211 aes_x86_64 bluetooth lrw hp_wmi sparse_keymap gf128mul glue_helper ablk_helper iwlwifi cryptd input_leds joydev cfg80211 serio_raw fam15h_power k10temp edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec edac_core snd_hda_core snd_seq_midi snd_seq_midi_event snd_rawmidi shpchp snd_hwdep snd_pcm
[15446.023391] Modules linked in: btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 amd_freq_sensitivity videobuf2_core kvm_amd kvm v4l2_common irqbypass arc4 videodev btusb media iwlmvm crct10dif_pclmul crc32_pclmul btrtl aesni_intel btbcm btintel mac80211 aes_x86_64 bluetooth lrw hp_wmi sparse_keymap gf128mul glue_helper ablk_helper iwlwifi cryptd input_leds joydev cfg80211 serio_raw fam15h_power k10temp edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec edac_core snd_hda_core snd_seq_midi snd_seq_midi_event snd_rawmidi shpchp snd_hwdep snd_pcm
[15446.024104] Modules linked in: btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 amd_freq_sensitivity videobuf2_core kvm_amd kvm v4l2_common irqbypass arc4 videodev btusb media iwlmvm crct10dif_pclmul crc32_pclmul btrtl aesni_intel btbcm btintel mac80211 aes_x86_64 bluetooth lrw hp_wmi sparse_keymap gf128mul glue_helper ablk_helper iwlwifi cryptd input_leds joydev cfg80211 serio_raw fam15h_power k10temp edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec edac_core snd_hda_core snd_seq_midi snd_seq_midi_event snd_rawmidi shpchp snd_hwdep snd_pcm
[15446.025028] Modules linked in: btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 amd_freq_sensitivity videobuf2_core kvm_amd kvm v4l2_common irqbypass arc4 videodev btusb media iwlmvm crct10dif_pclmul crc32_pclmul btrtl aesni_intel btbcm btintel mac80211 aes_x86_64 bluetooth lrw hp_wmi sparse_keymap gf128mul glue_helper ablk_helper iwlwifi cryptd input_leds joydev cfg80211 serio_raw fam15h_power k10temp edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec edac_core snd_hda_core snd_seq_midi snd_seq_midi_event snd_rawmidi shpchp snd_hwdep snd_pcm
[15446.025968] Modules linked in: btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 amd_freq_sensitivity videobuf2_core kvm_amd kvm v4l2_common irqbypass arc4 videodev btusb media iwlmvm crct10dif_pclmul crc32_pclmul btrtl aesni_intel btbcm btintel mac80211 aes_x86_64 bluetooth lrw hp_wmi sparse_keymap gf128mul glue_helper ablk_helper iwlwifi cryptd input_leds joydev cfg80211 serio_raw fam15h_power k10temp edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec edac_core snd_hda_core snd_seq_midi snd_seq_midi_event snd_rawmidi shpchp snd_hwdep snd_pcm
[15446.026705] Modules linked in: btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 amd_freq_sensitivity videobuf2_core kvm_amd kvm v4l2_common irqbypass arc4 videodev btusb media iwlmvm crct10dif_pclmul crc32_pclmul btrtl aesni_intel btbcm btintel mac80211 aes_x86_64 bluetooth lrw hp_wmi sparse_keymap gf128mul glue_helper ablk_helper iwlwifi cryptd input_leds joydev cfg80211 serio_raw fam15h_power k10temp edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec edac_core snd_hda_core snd_seq_midi snd_seq_midi_event snd_rawmidi shpchp snd_hwdep snd_pcm
[15446.027394] Modules linked in: btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 amd_freq_sensitivity videobuf2_core kvm_amd kvm v4l2_common irqbypass arc4 videodev btusb media iwlmvm crct10dif_pclmul crc32_pclmul btrtl aesni_intel btbcm btintel mac80211 aes_x86_64 bluetooth lrw hp_wmi sparse_keymap gf128mul glue_helper ablk_helper iwlwifi cryptd input_leds joydev cfg80211 serio_raw fam15h_power k10temp edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec edac_core snd_hda_core snd_seq_midi snd_seq_midi_event snd_rawmidi shpchp snd_hwdep snd_pcm
[15446.028126] Modules linked in: btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 amd_freq_sensitivity videobuf2_core kvm_amd kvm v4l2_common irqbypass arc4 videodev btusb media iwlmvm crct10dif_pclmul crc32_pclmul btrtl aesni_intel btbcm btintel mac80211 aes_x86_64 bluetooth lrw hp_wmi sparse_keymap gf128mul glue_helper ablk_helper iwlwifi cryptd input_leds joydev cfg80211 serio_raw fam15h_power k10temp edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec edac_core snd_hda_core snd_seq_midi snd_seq_midi_event snd_rawmidi shpchp snd_hwdep snd_pcm
[15446.028901] Modules linked in: btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 amd_freq_sensitivity videobuf2_core kvm_amd kvm v4l2_common irqbypass arc4 videodev btusb media iwlmvm crct10dif_pclmul crc32_pclmul btrtl aesni_intel btbcm btintel mac80211 aes_x86_64 bluetooth lrw hp_wmi sparse_keymap gf128mul glue_helper ablk_helper iwlwifi cryptd input_leds joydev cfg80211 serio_raw fam15h_power k10temp edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec edac_core snd_hda_core snd_seq_midi snd_seq_midi_event snd_rawmidi shpchp snd_hwdep snd_pcm
[15446.029540] Modules linked in: btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 amd_freq_sensitivity videobuf2_core kvm_amd kvm v4l2_common irqbypass arc4 videodev btusb media iwlmvm crct10dif_pclmul crc32_pclmul btrtl aesni_intel btbcm btintel mac80211 aes_x86_64 bluetooth lrw hp_wmi sparse_keymap gf128mul glue_helper ablk_helper iwlwifi cryptd input_leds joydev cfg80211 serio_raw fam15h_power k10temp edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec edac_core snd_hda_core snd_seq_midi snd_seq_midi_event snd_rawmidi shpchp snd_hwdep snd_pcm
[15446.030270] Modules linked in: btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 amd_freq_sensitivity videobuf2_core kvm_amd kvm v4l2_common irqbypass arc4 videodev btusb media iwlmvm crct10dif_pclmul crc32_pclmul btrtl aesni_intel btbcm btintel mac80211 aes_x86_64 bluetooth lrw hp_wmi sparse_keymap gf128mul glue_helper ablk_helper iwlwifi cryptd input_leds joydev cfg80211 serio_raw fam15h_power k10temp edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec edac_core snd_hda_core snd_seq_midi snd_seq_midi_event snd_rawmidi shpchp snd_hwdep snd_pcm
[15446.031009] Modules linked in: btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 amd_freq_sensitivity videobuf2_core kvm_amd kvm v4l2_common irqbypass arc4 videodev btusb media iwlmvm crct10dif_pclmul crc32_pclmul btrtl aesni_intel btbcm btintel mac80211 aes_x86_64 bluetooth lrw hp_wmi sparse_keymap gf128mul glue_helper ablk_helper iwlwifi cryptd input_leds joydev cfg80211 serio_raw fam15h_power k10temp edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec edac_core snd_hda_core snd_seq_midi snd_seq_midi_event snd_rawmidi shpchp snd_hwdep snd_pcm
[15446.031917] Modules linked in: btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 amd_freq_sensitivity videobuf2_core kvm_amd kvm v4l2_common irqbypass arc4 videodev btusb media iwlmvm crct10dif_pclmul crc32_pclmul btrtl aesni_intel btbcm btintel mac80211 aes_x86_64 bluetooth lrw hp_wmi sparse_keymap gf128mul glue_helper ablk_helper iwlwifi cryptd input_leds joydev cfg80211 serio_raw fam15h_power k10temp edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec edac_core snd_hda_core snd_seq_midi snd_seq_midi_event snd_rawmidi shpchp snd_hwdep snd_pcm
[15446.033010] Modules linked in: btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 amd_freq_sensitivity videobuf2_core kvm_amd kvm v4l2_common irqbypass arc4 videodev btusb media iwlmvm crct10dif_pclmul crc32_pclmul btrtl aesni_intel btbcm btintel mac80211 aes_x86_64 bluetooth lrw hp_wmi sparse_keymap gf128mul glue_helper ablk_helper iwlwifi cryptd input_leds joydev cfg80211 serio_raw fam15h_power k10temp edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec edac_core snd_hda_core snd_seq_midi snd_seq_midi_event snd_rawmidi shpchp snd_hwdep snd_pcm
[15446.033537] Modules linked in: btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c drbg ansi_cprng ctr ccm rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 amd_freq_sensitivity videobuf2_core kvm_amd kvm v4l2_common irqbypass arc4 videodev btusb media iwlmvm crct10dif_pclmul crc32_pclmul btrtl aesni_intel btbcm btintel mac80211 aes_x86_64 bluetooth lrw hp_wmi sparse_keymap gf128mul glue_helper ablk_helper iwlwifi cryptd input_leds joydev cfg80211 serio_raw fam15h_power k10temp edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec edac_core snd_hda_core snd_seq_midi snd_seq_midi_event snd_rawmidi shpchp snd_hwdep snd_pcm
```

---

### Post by ericwoud on 2016-12-22
Here the same problem. Restarting network manager does not work. Nothing seems to work to reset the adapter, except a reboot. See part of dmesg log when the first error comes in:

> 
[ 410.000601] iwlwifi 0000:02:00.0: Queue 16 stuck for 10000 ms.
[  410.000674] iwlwifi 0000:02:00.0: Current SW read_ptr 145 write_ptr 147
[  410.033748] ------------[ cut here ]------------
[  410.033806] WARNING: CPU: 3 PID: 0 at /build/linux-fEAasX/linux-4.9.0/drivers/net/wireless/intel/iwlwifi/pcie/trans.c:1864 iwl_trans_pcie_grab_nic_access+0xeb/0xf0 [iwlwifi]
[  410.033813] Timeout waiting for hardware access (CSR_GP_CNTRL 0xffffffff)


To reset the adapter, so i could use wifi again, wrote the following script:

> #find /sys -name wlan0 -path *devices/pci*
# result: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0
echo -n 1 > /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/remove
echo -n 1 > /sys/devices/pci0000:00/0000:00:1c.1/rescan
service network-manager restart


Use the find command in the first line to find the correct adress in your system. Exclude the part with /net/wlan0

However, after being stuck and applied once, the problem does not reappear until after the next reboot. So as a 'fix' let it start at boottime with systemd:

sudo gedit /etc/systemd/system/startup.service

> [Unit]
Description=Startup Service

[Service]
Type=simple
ExecStart=/bin/su -c "/bin/echo -n 1 > /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/remove ; \
                                                            /bin/echo -n 1 > /sys/devices/pci0000:00/0000:00:1c.1/rescan ; \
                                                            /usr/sbin/service network-manager restart"

[Install]
WantedBy=multi-user.target


And install with:
sudo systemctl preset startup.service

Somehow this fixes the problem of my 3160 intel wireless adapter to hang after 10 minutes use or so... This works on my Lenovo Yoga 300 11-IBY (80M0) with intel 3160 wifi adapter.

---

### Post by DiCon on 2017-01-16
Thank you so much, ericwoud. The same problem was bothering me for a while now on an Intel 7260 card and I just stumbled on your workaround. And indeed, it does not just get the network running again without rebooting, it actually fixes the problem until the next reboot, which strike me as rather odd...

So, for reference, that it seems to be the same problem, here is a typical dmesg excerpt from my system (which is a Dell XPS 12 9q33):
```
[  779.792010] iwlwifi 0000:06:00.0: Queue 16 stuck for 10000 ms.
[  779.792034] iwlwifi 0000:06:00.0: Current SW read_ptr 96 write_ptr 162
[  779.809645] ------------[ cut here ]------------
[  779.809670] WARNING: CPU: 2 PID: 0 at /home/kernel/COD/linux/drivers/net/wireless/intel/iwlwifi/pcie/trans.c:1864 iwl_trans_pcie_grab_nic_access+0xeb/0xf0 [iwlwifi]
[  779.809673] Timeout waiting for hardware access (CSR_GP_CNTRL 0xffffffff)
```

Interestingly, for me the problem seems to be related to the load of a network. At home this bug occurs about once a week, but in my office at the uni it happens randomly about 10 times a day. In an empty lecture hall, while preparing the lecture, it happens about once per hour, but when the lecture hall is filled with 300 students, I can hardly check my mail before the connection drops and I am more or less constantly rebooting to get a connection. (Well, not anymore, thanks to you!)

Did you report this anywhere else or do you have any idea if this is Ubuntu-specifiy or an iwl problem? I would like to submit a bug report and contribute to a "real" solution... So far, I reproduced this bug with Ubuntu 16.10 from a USB stick, my regular 16.10 installation and with 16.10 and the most recent mainline kernel.

---

### Post by chili555 on 2017-01-16
I have two Intel wireless devices, including a 7260 that runs perfectly. I'd like to offer some suggestions.

First, let's disable power saving in Network Manager; from the terminal:```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```Next, be certain that you have the latest firmware:```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.162_all.deb
sudo dpkg -i linux-firmware*.deb
```Reboot.

Next, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

If you are in a situation where changing the router is not feasible, a landlord, university, etc., you may get a connection even with TKIP with a driver parameter:```
sudo -i
echo "options iwlwifi swcrypto=1"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

After making these changes and after a reboot, check the logs again:```
dmesg | grep iwl
```Any more of those ugly stuck queue messages?

---

### Post by DiCon on 2017-01-17
First of all, I have to take back that the script fixes the problem until the next reboot. Seems like I was just lucky, because today, the script allows me to reconnect to the network without rebooting (still better than without), but it will break down again after a while. So maybe it's not the same bug after all...

@chili555:
Thanks for all the suggestions. I already have the latest firmware (iwlwifi-7260-17.ucode, also check that it's used with modinfo iwlwifi) and the correct regulatory domain (de). Also, I experience the problems on different networks with different severity. Not sure about the settings at home, but here at the uni it is a mixed mode (which I cannot change) network using CCMP (also certainly no TKIP at home). So, I just tested the power saving mode, but it did not help...

Also, the Wifi worked great for almost three years before these problems occurred a few months ago - not exactly sure when, but I remember that the problem was fairly new and that I was hoping that it would be resolved when updating to 16.10, which I did on the 5th of November according to my logs. So, maybe I should grab an older Ubuntu version, run it from USB and upgrade until it breaks again...

---

### Post by chili555 on 2017-01-17
>  I already have the latest firmware (iwlwifi-7260-17.ucode, also check that it's used with modinfo iwlwifimodinfo shows the firmware that the driver version will use if available. The only way to verify what is *actually* loaded is:```
dmesg | grep iwl
```My system loads -17:```
[    4.511808] iwlwifi 0000:03:00.0: loaded firmware version [COLOR="#FF0000"]17[/COLOR].352738.0 op_mode iwlmvm

```Incidentally, the driver will sometimes load a newer version than listed in modinfo; for example -18 or -19. Generally, however, experimental not-ready-for-prime-time firmware files are not helpful.

Did you try swcrypto=1?

---

### Post by DiCon on 2017-01-17
I have to admit, that I didn't try it at first as I thought you found it helpful in TKIP networks. Now I tried and still have disconnects... It took a while longer (at least I think so - it was disconnected when I returned to the office after a meeting), but that's probably due to the randomness of the problem.

About the firmware version: It's definitely 17. I tried to downgrade it to 16 since the release of 17 into the Ubuntu repository is close to my estimate of when the trouble started. But my iwlwifi does not accept anything below 17 and also 17 is the most recent available - so I will have to test an older kernel... (Of course I now also double-checked with dmesg and it's identical to your version.)

If I understand it correctly, there will be no new versions after 17 unless there are backports - but since you mention experimental firmware: Is there a source for such firmware that I am not aware of?

---

### Post by chili555 on 2017-01-17
> Is there a source for such firmware that I am not aware of?My resource is here: [https://github.com/OpenELEC/iwlwifi-firmware/tree/master/firmware](https://github.com/OpenELEC/iwlwifi-firmware/tree/master/firmware) As you can see, -17 is the newest they have.> I have to admit, that I didn't try it at first as I thought you found it helpful in TKIP networks. Now I tried and still have disconnects..At this point, I'd try anything.

If you'd rather remove it, simply edit the file and remove the last line that you added above.

---

### Post by ericwoud on 2017-01-21
Then I think we are talking about different bugs. My solution applies to a Lenovo Yoga 300 11-IBY (80M0). I can confirm the solution still works, after a month still no stuck wifi adapter (intel 3160) at all.

---

### Post by rob.johnson on 2018-01-19
I hope I'm not too late, but I'm running into a very similar issue on 16.04.3 with an Intel 8265 card. I too get the 'Warning: CPU' messages when allowing iwlwifi on boot. chili555 responded to my question on AskUbuntu to suggest adding iwlwifi to the modprobe blacklist, and that does indeed let the machine boot up correctly. I notice that with iwlwifi enabled, i have absolutely no network connections once the GUI loads, even the Intel onboard ethernet on my Dell Precision M3520. Attempting to sudo causes the terminal to hang.

So back on topic, with iwlwifi blacklisted at boot, the GUI loads. I've then manually modprobe'd iwlwifi once the machine is fully up and wifi then works properly. At a guess, a dependency isn't being loaded, or is being loaded in the wrong order. Out of paranoia, I then decided to unload the module before putting my laptop into sleep mode to improve my chances of getting it back:

```
root@M3520:~# rmmod iwlwifi
rmmod: ERROR: Module iwlwifi is in use by: iwlmvm
root@M3520:~# rmmod iwlmvm

```

At this point, the terminal hangs again. If I switch to another tab and attempt to sudo, that hangs as well. So based on this, I *think* the culprit may be this iwlmvm module instead. For now, manually loading iwlwifi when I need wireless is a viable workaround. Anyone else found a solution?

---

### Post by chili555 on 2018-01-19
I think the correct method is:```
sudo modprobe -r iwlwifi
```And then it should take out all the dependencies with it.

You might also be certain that the default /etc/modprobe.d/iwlwifi.conf file is in place.```
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

```FYI, the module dependencies are found with modinfo:```
$ modinfo iwlwifi
filename:       /lib/modules/4.13.0-25-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
<snip>
[COLOR="#FF0000"]depends:        cfg80211[/COLOR]
```As well as:```
$ modinfo iwlmvm
filename:       /lib/modules/4.13.0-25-generic/kernel/drivers/net/wireless/intel/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     EBD7611E6805E2BDE8304CC
[COLOR="#FF0000"]depends:        iwlwifi,mac80211,cfg80211[/COLOR]
<snip>
```You can get the module to load even though it's blacklisted after a short wait by adding to /etc/rc.local so that it reads:```
sleep 3
modprobe iwlwifi

exit  0
```You might have to play with the sleep 3 (seconds) a bit. It might need 4 or it might work perfectly well with 2 or 1.

---

### Post by rob.johnson on 2018-01-19
> **chili555 said:**
> I think the correct method is:```
sudo modprobe -r iwlwifi
```And then it should take out all the dependencies with it.

Figures with Linux there's always more than one way to do something...

I just found it quite interesting that trying to remove the iwlmvm module caused the same symptoms as when it loads up normally.

My /etc/modprobe.d/iwlwifi.conf file is present and matches yours, but that does seem like a hacky script to remove the modules.

On the subject of hacky scripts, the idea of adding to rc.local did occur to me, but this is something I'd like to get to the bottom of, try to figure out why it's crashing in the first place. I use my laptop mostly on ethernet anyway so I don't need the wifi loaded all the time.

---

### Post by chili555 on 2018-01-19
The only way to find the problem, as far as I know, is to let it crash, reboot and check the log; /var/log/syslog would be my first suspect.

Which firmware is loading?```
dmesg | grep -i firm
```

---

### Post by rob.johnson on 2018-01-19
```
[12626.928614] iwlwifi 0000:02:00.0: loaded firmware version 31.560484.0 op_mode iwlmvm
```

---

### Post by chili555 on 2018-01-19
Let's see if the firmware is corrupted and if there are some alternatives:```
ls -al /lib/firmware | grep 8265
```My system says:```
-rw-r--r--  1 root root 2389968 Nov  9 14:36 iwlwifi-8265-21.ucode
-rw-r--r--  1 root root 1811984 Nov  9 14:36 iwlwifi-8265-22.ucode
-rw-r--r--  1 root root 2234528 Nov  9 14:36 iwlwifi-8265-27.ucode
-rw-r--r--  1 root root [COLOR="#FF0000"]2307104[/COLOR] Nov 15 16:47 iwlwifi-8265-31.ucode

```We hope your -31 is the exact same size.

We might also try renaming it so it doesn't load and see if -27 is stable.

---

### Post by rob.johnson on 2018-01-22
```
rob.johnson@M3520:~$ ls -l /lib/firmware/*8265*
-rw-r--r-- 1 root        root        2389968 Nov  9 19:36 /lib/firmware/iwlwifi-8265-21.ucode
-rw-r--r-- 1 rob.johnson rob.johnson 1811984 Jan  5  2017 /lib/firmware/iwlwifi-8265-22.ucode
-rw-r--r-- 1 root        root        1811984 Nov  9 19:36 /lib/firmware/iwlwifi-8265-22.ucode.old
-rw-r--r-- 1 root        root        2234528 Nov  9 19:36 /lib/firmware/iwlwifi-8265-27.ucode
-rw-r--r-- 1 root        root        2307104 Nov 15 21:04 /lib/firmware/iwlwifi-8265-31.ucode
rob.johnson@M3520:~$ sha256sum /lib/firmware/iwlwifi-8265-31.ucode 
2f8c0f2b2c42d61b8284a2a3d3b2b5e0a50a1be8c8adb50ae49b80620136dbff  /lib/firmware/iwlwifi-8265-31.ucode
```

The size matches, but the checksum would be more accurate in telling us if it's corrupted. Can you post the sha256sum of your firmware file?

What's kind of annoying is that the 'version' isn't really a version, according to what I've read the number only relates to ABI compatibility. So there can be multiple versions of -31 with different code, but they can all swap in (in theory) without breaking anything because they use the same system calls. So there's a chance that both of us have valid firmware, but different versions and the checksums won't match...

---

### Post by chili555 on 2018-01-22
I get:```
chili@T440p:~$ sha256sum /lib/firmware/iwlwifi-8265-31.ucode 
2f8c0f2b2c42d61b8284a2a3d3b2b5e0a50a1be8c8adb50ae49b80620136dbff  /lib/firmware/iwlwifi-8265-31.ucode

```It appears to be identical.

---

### Post by rob.johnson on 2018-01-22
Right, so, ```
modprobe iwlwifi
``` after the desktop loads is not the miracle cure I thought it was - I just unplugged my laptop, did exactly that and although it connected to the network, I had no access. When I plugged back in, Network-Manager showed No Cable Connected, network settings reused to load and the entire machine quickly locked up. Had to hard reboot. Best part is that I can only see a string of ^@ binary in syslog and kern.log shortly after swapping connections, and immediately before rsyslog reinitialised on reboot.

The plot thickens.

---

### Post by chili555 on 2018-01-22
> **rob.johnson said:**
> Right, so, ```
modprobe iwlwifi
``` after the desktop loads is not the miracle cure I thought it was - I just unplugged my laptop, did exactly that and although it connected to the network, I had no access. When I plugged back in, Network-Manager showed No Cable Connected, network settings reused to load and the entire machine quickly locked up. Had to hard reboot. Best part is that I can only see a string of ^@ binary in syslog and kern.log shortly after swapping connections, and immediately before rsyslog reinitialised on reboot.

The plot thickens.Can you capture the last 100 lines or so leading up to and starting the crash, post it here and give us the link? [http://paste.ubuntu.com](http://paste.ubuntu.com)

When it gets full, /var/log/syslog gets archived as syslog.1 and a new syslog started so you may need to look around a bit.

---

### Post by rob.johnson on 2018-01-25
Right, so I tried a bunch of 4.13 kernels. Anything prior to -26 would not let me boot past the LUKS password screen (couldn't type anything), and if I manually removed the 'quiet splash' instructions from the kernel command line, the kernel wouldn't boot at all - er, huh? 4.13.0-31 seems to be unstable, but 4.13.0-26 is holding steady. Wifi is up and working - I'm typing this on the laptop now, on wifi. On the downside, the bluetooth component of the card seems to be misbehaving - getting lots of USB errors in the logs saying 'kworker blocked for 120 seconds' followed by USB disconnects and reconnects. Now I've found a stable starting point, I can poke around some more.

---

### Post by rob.johnson on 2018-01-26
Nope, 4.13.0-26 wasn't stable after all. It seems to be a cold boot more than anything - after flicking through a few kernels, the wifi card would then come up properly on the last kernel I tried. -31 has not been stable by any means though.

I've given up trying to get the 8265 working on my Precision and have swapped it with a Qualcomm 6174 card out of one of our XPSen, which started working immediately. Ironically, it worked on the first boot in that laptop, on the same -26 kernel. It's possible I had a slightly loose connection to the wifi card all along, and swapping the cards properly reseated both. At least things are stable now!

---

### Post by rob.johnson on 2018-02-21
Well, this is still annoying the heck out of me. The Qualcomm card was generating PCIe bus errors. Combined with the Intel card issues, I began to suspect hardware problems, namely the slot itself being damaged or losing connection due to thermal expansion. I was able to dig through our hardware and found an unused Intel 8260 card - a real eureka moment as the 8260 drivers work with kernel versions 4.2+. However, the problems persisted with the 8260 so I called Dell out to replace the motherboard.

It hasn't helped. I'm still seeing lots and lots of freezing and tasks hanging, now on kernel version 4.13.0-32. It got to the point that I physically removed the wifi card just to get the machine stable.

What I've done is kept the 8260 and dropped my kernel back to 4.4.0-112. I think the drivers are fundamentally broken in the newer kernels. I'll know in a day or two if this works around the problem.

In the meantime, I've got some logs for the hung tasks. They seem to relate to both the blutooth (btusb) and wifi card (rfkill), which is what made me suspect the card itself or the PCIe slot.

> Feb 19 10:06:07 M3520 kernel: [  484.316030] INFO: task kworker/0:2:74 blocked for more than 120 seconds.
Feb 19 10:06:07 M3520 kernel: [  484.316032]       Tainted: P           OE   4.13.0-32-generic #35~16.04.1-Ubuntu
Feb 19 10:06:07 M3520 kernel: [  484.316033] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Feb 19 10:06:07 M3520 kernel: [  484.316034] kworker/0:2     D    0    74      2 0x00000000
Feb 19 10:06:07 M3520 kernel: [  484.316038] Workqueue: usb_hub_wq hub_event
Feb 19 10:06:07 M3520 kernel: [  484.316039] Call Trace:
Feb 19 10:06:07 M3520 kernel: [  484.316043]  __schedule+0x3c2/0x890
Feb 19 10:06:07 M3520 kernel: [  484.316044]  schedule+0x36/0x80
Feb 19 10:06:07 M3520 kernel: [  484.316045]  schedule_timeout+0x1f0/0x360
Feb 19 10:06:07 M3520 kernel: [  484.316047]  ? wake_up_process+0x15/0x20
Feb 19 10:06:07 M3520 kernel: [  484.316048]  ? insert_work+0x6d/0x80
Feb 19 10:06:07 M3520 kernel: [  484.316049]  ? __queue_work+0x149/0x440
Feb 19 10:06:07 M3520 kernel: [  484.316050]  wait_for_completion+0xb4/0x140
Feb 19 10:06:07 M3520 kernel: [  484.316051]  ? wait_for_completion+0xb4/0x140
Feb 19 10:06:07 M3520 kernel: [  484.316052]  ? wake_up_q+0x70/0x70
Feb 19 10:06:07 M3520 kernel: [  484.316053]  __synchronize_srcu.part.14+0x85/0xb0
Feb 19 10:06:07 M3520 kernel: [  484.316055]  ? trace_raw_output_rcu_utilization+0x50/0x50
Feb 19 10:06:07 M3520 kernel: [  484.316056]  synchronize_srcu_expedited+0x27/0x30
Feb 19 10:06:07 M3520 kernel: [  484.316056]  ? synchronize_srcu_expedited+0x27/0x30
Feb 19 10:06:07 M3520 kernel: [  484.316057]  synchronize_srcu+0xbb/0xe0
Feb 19 10:06:07 M3520 kernel: [  484.316059]  debugfs_remove_recursive+0x18d/0x1c0
Feb 19 10:06:07 M3520 kernel: [  484.316068]  hci_unregister_dev+0xfc/0x2c0 [bluetooth]
Feb 19 10:06:07 M3520 kernel: [  484.316070]  btusb_disconnect+0x64/0x130 [btusb]
Feb 19 10:06:07 M3520 kernel: [  484.316072]  usb_unbind_interface+0x72/0x260
Feb 19 10:06:07 M3520 kernel: [  484.316074]  device_release_driver_internal+0x155/0x210
Feb 19 10:06:07 M3520 kernel: [  484.316075]  device_release_driver+0x12/0x20
Feb 19 10:06:07 M3520 kernel: [  484.316076]  bus_remove_device+0xe9/0x160
Feb 19 10:06:07 M3520 kernel: [  484.316077]  device_del+0x1d7/0x310
Feb 19 10:06:07 M3520 kernel: [  484.316077]  ? usb_remove_ep_devs+0x1f/0x30
Feb 19 10:06:07 M3520 kernel: [  484.316079]  usb_disable_device+0x9e/0x270
Feb 19 10:06:07 M3520 kernel: [  484.316080]  usb_disconnect+0x92/0x290
Feb 19 10:06:07 M3520 kernel: [  484.316080]  hub_port_connect+0x80/0x9e0
Feb 19 10:06:07 M3520 kernel: [  484.316081]  hub_event+0x8aa/0xb10
Feb 19 10:06:07 M3520 kernel: [  484.316083]  ? pick_next_task_fair+0x443/0x560
Feb 19 10:06:07 M3520 kernel: [  484.316084]  ? __switch_to+0xb2/0x530
Feb 19 10:06:07 M3520 kernel: [  484.316086]  process_one_work+0x156/0x410
Feb 19 10:06:07 M3520 kernel: [  484.316087]  worker_thread+0x4b/0x460
Feb 19 10:06:07 M3520 kernel: [  484.316088]  kthread+0x109/0x140
Feb 19 10:06:07 M3520 kernel: [  484.316089]  ? process_one_work+0x410/0x410
Feb 19 10:06:07 M3520 kernel: [  484.316090]  ? kthread_create_on_node+0x70/0x70
Feb 19 10:06:07 M3520 kernel: [  484.316091]  ret_from_fork+0x1f/0x30
Feb 19 10:06:07 M3520 kernel: [  484.316115] INFO: task lshw:1598 blocked for more than 120 seconds.
Feb 19 10:06:07 M3520 kernel: [  484.316116]       Tainted: P           OE   4.13.0-32-generic #35~16.04.1-Ubuntu
Feb 19 10:06:07 M3520 kernel: [  484.316117] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Feb 19 10:06:07 M3520 kernel: [  484.316117] lshw            D    0  1598   1569 0x00000000
Feb 19 10:06:07 M3520 kernel: [  484.316119] Call Trace:
Feb 19 10:06:07 M3520 kernel: [  484.316120]  __schedule+0x3c2/0x890
Feb 19 10:06:07 M3520 kernel: [  484.316121]  ? path_openat+0x3cc/0x13e0
Feb 19 10:06:07 M3520 kernel: [  484.316122]  schedule+0x36/0x80
Feb 19 10:06:07 M3520 kernel: [  484.316123]  schedule_preempt_disabled+0xe/0x10
Feb 19 10:06:07 M3520 kernel: [  484.316124]  __mutex_lock.isra.2+0x2ae/0x4e0
Feb 19 10:06:07 M3520 kernel: [  484.316125]  __mutex_lock_slowpath+0x13/0x20
Feb 19 10:06:07 M3520 kernel: [  484.316126]  ? __mutex_lock_slowpath+0x13/0x20
Feb 19 10:06:07 M3520 kernel: [  484.316127]  mutex_lock+0x2f/0x40
Feb 19 10:06:07 M3520 kernel: [  484.316128]  usb_device_read+0xc3/0x150
Feb 19 10:06:07 M3520 kernel: [  484.316129]  full_proxy_read+0x54/0x90
Feb 19 10:06:07 M3520 kernel: [  484.316130]  __vfs_read+0x18/0x40
Feb 19 10:06:07 M3520 kernel: [  484.316131]  vfs_read+0x93/0x130
Feb 19 10:06:07 M3520 kernel: [  484.316132]  SyS_read+0x55/0xc0
Feb 19 10:06:07 M3520 kernel: [  484.316133]  entry_SYSCALL_64_fastpath+0x33/0xa3
Feb 19 10:06:07 M3520 kernel: [  484.316134] RIP: 0033:0x7f23c0cb9260
Feb 19 10:06:07 M3520 kernel: [  484.316135] RSP: 002b:00007ffcc2e12268 EFLAGS: 00000246 ORIG_RAX: 0000000000000000
Feb 19 10:06:07 M3520 kernel: [  484.316136] RAX: ffffffffffffffda RBX: 00000000009d50e0 RCX: 00007f23c0cb9260
Feb 19 10:06:07 M3520 kernel: [  484.316136] RDX: 0000000000001000 RSI: 0000000000b0eca0 RDI: 0000000000000003
Feb 19 10:06:07 M3520 kernel: [  484.316137] RBP: 00007ffcc2e13100 R08: 00007f23c0f86ba8 R09: 0000000000000000
Feb 19 10:06:07 M3520 kernel: [  484.316137] R10: 00007f23c0f86b78 R11: 0000000000000246 R12: 00007ffcc2e12410
Feb 19 10:06:07 M3520 kernel: [  484.316138] R13: 0000000000000000 R14: 0000000000000000 R15: 0000000000000000
Feb 19 10:06:07 M3520 kernel: [  484.316142] INFO: task fusermount:2576 blocked for more than 120 seconds.
Feb 19 10:06:07 M3520 kernel: [  484.316143]       Tainted: P           OE   4.13.0-32-generic #35~16.04.1-Ubuntu
Feb 19 10:06:07 M3520 kernel: [  484.316143] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Feb 19 10:06:07 M3520 kernel: [  484.316144] fusermount      D    0  2576   1705 0x00000000
Feb 19 10:06:07 M3520 kernel: [  484.316145] Call Trace:
Feb 19 10:06:07 M3520 kernel: [  484.316146]  __schedule+0x3c2/0x890
Feb 19 10:06:07 M3520 kernel: [  484.316147]  schedule+0x36/0x80
Feb 19 10:06:07 M3520 kernel: [  484.316148]  schedule_timeout+0x1f0/0x360
Feb 19 10:06:07 M3520 kernel: [  484.316149]  ? ttwu_do_wakeup+0x1e/0x150
Feb 19 10:06:07 M3520 kernel: [  484.316150]  ? ttwu_do_activate+0x7a/0x90
Feb 19 10:06:07 M3520 kernel: [  484.316151]  wait_for_completion+0xb4/0x140
Feb 19 10:06:07 M3520 kernel: [  484.316151]  ? wait_for_completion+0xb4/0x140
Feb 19 10:06:07 M3520 kernel: [  484.316152]  ? wake_up_q+0x70/0x70
Feb 19 10:06:07 M3520 kernel: [  484.316153]  __synchronize_srcu.part.14+0x85/0xb0
Feb 19 10:06:07 M3520 kernel: [  484.316155]  ? trace_raw_output_rcu_utilization+0x50/0x50
Feb 19 10:06:07 M3520 kernel: [  484.316156]  ? ktime_get_mono_fast_ns+0x4b/0xa0
Feb 19 10:06:07 M3520 kernel: [  484.316157]  synchronize_srcu+0xcd/0xe0
Feb 19 10:06:07 M3520 kernel: [  484.316157]  ? synchronize_srcu+0xcd/0xe0
Feb 19 10:06:07 M3520 kernel: [  484.316158]  debugfs_remove+0x72/0xa0
Feb 19 10:06:07 M3520 kernel: [  484.316160]  bdi_unregister+0x18e/0x210
Feb 19 10:06:07 M3520 kernel: [  484.316161]  bdi_put+0x97/0xa0
Feb 19 10:06:07 M3520 kernel: [  484.316162]  generic_shutdown_super+0xef/0x120
Feb 19 10:06:07 M3520 kernel: [  484.316163]  kill_anon_super+0x12/0x20
Feb 19 10:06:07 M3520 kernel: [  484.316164]  fuse_kill_sb_anon+0x47/0x50
Feb 19 10:06:07 M3520 kernel: [  484.316165]  deactivate_locked_super+0x43/0x70
Feb 19 10:06:07 M3520 kernel: [  484.316166]  deactivate_super+0x5a/0x60
Feb 19 10:06:07 M3520 kernel: [  484.316167]  cleanup_mnt+0x3f/0x80
Feb 19 10:06:07 M3520 kernel: [  484.316168]  __cleanup_mnt+0x12/0x20
Feb 19 10:06:07 M3520 kernel: [  484.316169]  task_work_run+0x7e/0xa0
Feb 19 10:06:07 M3520 kernel: [  484.316170]  exit_to_usermode_loop+0xc4/0xd0
Feb 19 10:06:07 M3520 kernel: [  484.316171]  syscall_return_slowpath+0x59/0x60
Feb 19 10:06:07 M3520 kernel: [  484.316173]  entry_SYSCALL_64_fastpath+0xa1/0xa3
Feb 19 10:06:07 M3520 kernel: [  484.316173] RIP: 0033:0x7f36ed053487
Feb 19 10:06:07 M3520 kernel: [  484.316174] RSP: 002b:00007ffdc7a98c88 EFLAGS: 00000206 ORIG_RAX: 00000000000000a6
Feb 19 10:06:07 M3520 kernel: [  484.316174] RAX: 0000000000000000 RBX: 00007f36ed516698 RCX: 00007f36ed053487
Feb 19 10:06:07 M3520 kernel: [  484.316175] RDX: 0000000000000000 RSI: 000000000000000a RDI: 000055c3746527ae
Feb 19 10:06:07 M3520 kernel: [  484.316175] RBP: 0000000000000003 R08: 0000000000000000 R09: 0000000000000001
Feb 19 10:06:07 M3520 kernel: [  484.316176] R10: 0000000000000000 R11: 0000000000000206 R12: 000055c3746527a0
Feb 19 10:06:07 M3520 kernel: [  484.316176] R13: 00000000ffffffff R14: 000055c374650050 R15: 000055c374652a17
Feb 19 10:08:07 M3520 kernel: [  605.148063] INFO: task kworker/0:2:74 blocked for more than 120 seconds.
Feb 19 10:08:07 M3520 kernel: [  605.148066]       Tainted: P           OE   4.13.0-32-generic #35~16.04.1-Ubuntu
Feb 19 10:08:07 M3520 kernel: [  605.148067] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Feb 19 10:08:07 M3520 kernel: [  605.148068] kworker/0:2     D    0    74      2 0x00000000
Feb 19 10:08:07 M3520 kernel: [  605.148072] Workqueue: usb_hub_wq hub_event
Feb 19 10:08:07 M3520 kernel: [  605.148073] Call Trace:
Feb 19 10:08:07 M3520 kernel: [  605.148076]  __schedule+0x3c2/0x890
Feb 19 10:08:07 M3520 kernel: [  605.148077]  schedule+0x36/0x80
Feb 19 10:08:07 M3520 kernel: [  605.148078]  schedule_timeout+0x1f0/0x360
Feb 19 10:08:07 M3520 kernel: [  605.148081]  ? wake_up_process+0x15/0x20
Feb 19 10:08:07 M3520 kernel: [  605.148082]  ? insert_work+0x6d/0x80
Feb 19 10:08:07 M3520 kernel: [  605.148083]  ? __queue_work+0x149/0x440
Feb 19 10:08:07 M3520 kernel: [  605.148084]  wait_for_completion+0xb4/0x140
Feb 19 10:08:07 M3520 kernel: [  605.148085]  ? wait_for_completion+0xb4/0x140
Feb 19 10:08:07 M3520 kernel: [  605.148086]  ? wake_up_q+0x70/0x70
Feb 19 10:08:07 M3520 kernel: [  605.148087]  __synchronize_srcu.part.14+0x85/0xb0
Feb 19 10:08:07 M3520 kernel: [  605.148102]  ? trace_raw_output_rcu_utilization+0x50/0x50
Feb 19 10:08:07 M3520 kernel: [  605.148103]  synchronize_srcu_expedited+0x27/0x30
Feb 19 10:08:07 M3520 kernel: [  605.148104]  ? synchronize_srcu_expedited+0x27/0x30
Feb 19 10:08:07 M3520 kernel: [  605.148104]  synchronize_srcu+0xbb/0xe0
Feb 19 10:08:07 M3520 kernel: [  605.148106]  debugfs_remove_recursive+0x18d/0x1c0
Feb 19 10:08:07 M3520 kernel: [  605.148133]  hci_unregister_dev+0xfc/0x2c0 [bluetooth]
Feb 19 10:08:07 M3520 kernel: [  605.148136]  btusb_disconnect+0x64/0x130 [btusb]
Feb 19 10:08:07 M3520 kernel: [  605.148137]  usb_unbind_interface+0x72/0x260
Feb 19 10:08:07 M3520 kernel: [  605.148139]  device_release_driver_internal+0x155/0x210
Feb 19 10:08:07 M3520 kernel: [  605.148140]  device_release_driver+0x12/0x20
Feb 19 10:08:07 M3520 kernel: [  605.148141]  bus_remove_device+0xe9/0x160
Feb 19 10:08:07 M3520 kernel: [  605.148142]  device_del+0x1d7/0x310
Feb 19 10:08:07 M3520 kernel: [  605.148143]  ? usb_remove_ep_devs+0x1f/0x30
Feb 19 10:08:07 M3520 kernel: [  605.148144]  usb_disable_device+0x9e/0x270
Feb 19 10:08:07 M3520 kernel: [  605.148145]  usb_disconnect+0x92/0x290
Feb 19 10:08:07 M3520 kernel: [  605.148146]  hub_port_connect+0x80/0x9e0
Feb 19 10:08:07 M3520 kernel: [  605.148147]  hub_event+0x8aa/0xb10
Feb 19 10:08:07 M3520 kernel: [  605.148149]  ? pick_next_task_fair+0x443/0x560
Feb 19 10:08:07 M3520 kernel: [  605.148154]  ? __switch_to+0xb2/0x530
Feb 19 10:08:07 M3520 kernel: [  605.148156]  process_one_work+0x156/0x410
Feb 19 10:08:07 M3520 kernel: [  605.148158]  worker_thread+0x4b/0x460
Feb 19 10:08:07 M3520 kernel: [  605.148159]  kthread+0x109/0x140
Feb 19 10:08:07 M3520 kernel: [  605.148172]  ? process_one_work+0x410/0x410
Feb 19 10:08:07 M3520 kernel: [  605.148173]  ? kthread_create_on_node+0x70/0x70
Feb 19 10:08:07 M3520 kernel: [  605.148175]  ret_from_fork+0x1f/0x30
Feb 19 10:08:07 M3520 kernel: [  605.148183] INFO: task kworker/4:3:982 blocked for more than 120 seconds.
Feb 19 10:08:07 M3520 kernel: [  605.148184]       Tainted: P           OE   4.13.0-32-generic #35~16.04.1-Ubuntu
Feb 19 10:08:07 M3520 kernel: [  605.148185] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Feb 19 10:08:07 M3520 kernel: [  605.148187] kworker/4:3     D    0   982      2 0x00000000
Feb 19 10:08:07 M3520 kernel: [  605.148193] Workqueue: events rfkill_any_led_trigger_worker
Feb 19 10:08:07 M3520 kernel: [  605.148193] Call Trace:
Feb 19 10:08:07 M3520 kernel: [  605.148194]  __schedule+0x3c2/0x890
Feb 19 10:08:07 M3520 kernel: [  605.148195]  schedule+0x36/0x80
Feb 19 10:08:07 M3520 kernel: [  605.148196]  schedule_preempt_disabled+0xe/0x10
Feb 19 10:08:07 M3520 kernel: [  605.148197]  __mutex_lock.isra.2+0x2ae/0x4e0
Feb 19 10:08:07 M3520 kernel: [  605.148198]  __mutex_lock_slowpath+0x13/0x20
Feb 19 10:08:07 M3520 kernel: [  605.148199]  ? __mutex_lock_slowpath+0x13/0x20
Feb 19 10:08:07 M3520 kernel: [  605.148200]  mutex_lock+0x2f/0x40
Feb 19 10:08:07 M3520 kernel: [  605.148201]  rfkill_any_led_trigger_worker+0x16/0x80
Feb 19 10:08:07 M3520 kernel: [  605.148202]  process_one_work+0x156/0x410
Feb 19 10:08:07 M3520 kernel: [  605.148203]  worker_thread+0x4b/0x460
Feb 19 10:08:07 M3520 kernel: [  605.148204]  kthread+0x109/0x140
Feb 19 10:08:07 M3520 kernel: [  605.148205]  ? process_one_work+0x410/0x410
Feb 19 10:08:07 M3520 kernel: [  605.148206]  ? kthread_create_on_node+0x70/0x70
Feb 19 10:08:07 M3520 kernel: [  605.148207]  ret_from_fork+0x1f/0x30
Feb 19 10:08:07 M3520 kernel: [  605.148211] INFO: task NetworkManager:1327 blocked for more than 120 seconds.
Feb 19 10:08:07 M3520 kernel: [  605.148212]       Tainted: P           OE   4.13.0-32-generic #35~16.04.1-Ubuntu
Feb 19 10:08:07 M3520 kernel: [  605.148213] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Feb 19 10:08:07 M3520 kernel: [  605.148213] NetworkManager  D    0  1327      1 0x00000000
Feb 19 10:08:07 M3520 kernel: [  605.148214] Call Trace:
Feb 19 10:08:07 M3520 kernel: [  605.148215]  __schedule+0x3c2/0x890
Feb 19 10:08:07 M3520 kernel: [  605.148216]  schedule+0x36/0x80
Feb 19 10:08:07 M3520 kernel: [  605.148217]  schedule_timeout+0x1f0/0x360
Feb 19 10:08:07 M3520 kernel: [  605.148218]  wait_for_completion+0xb4/0x140
Feb 19 10:08:07 M3520 kernel: [  605.148219]  ? wait_for_completion+0xb4/0x140
Feb 19 10:08:07 M3520 kernel: [  605.148220]  ? wake_up_q+0x70/0x70
Feb 19 10:08:07 M3520 kernel: [  605.148221]  __synchronize_srcu.part.14+0x85/0xb0
Feb 19 10:08:07 M3520 kernel: [  605.148222]  ? trace_raw_output_rcu_utilization+0x50/0x50
Feb 19 10:08:07 M3520 kernel: [  605.148223]  synchronize_srcu+0xcd/0xe0
Feb 19 10:08:07 M3520 kernel: [  605.148223]  ? synchronize_srcu+0xcd/0xe0
Feb 19 10:08:07 M3520 kernel: [  605.148224]  debugfs_remove+0x72/0xa0
Feb 19 10:08:07 M3520 kernel: [  605.148230]  iwl_mvm_vif_dbgfs_clean+0x29/0x50 [iwlmvm]
Feb 19 10:08:07 M3520 kernel: [  605.148234]  iwl_mvm_mac_remove_interface+0x5c/0x140 [iwlmvm]
Feb 19 10:08:07 M3520 kernel: [  605.148243]  drv_remove_interface+0x44/0x110 [mac80211]
Feb 19 10:08:07 M3520 kernel: [  605.148252]  ieee80211_do_stop+0x512/0x840 [mac80211]
Feb 19 10:08:07 M3520 kernel: [  605.148259]  ieee80211_sdata_stop+0x1e/0x30 [mac80211]
Feb 19 10:08:07 M3520 kernel: [  605.148267]  ieee80211_stop_p2p_device+0x12/0x20 [mac80211]
Feb 19 10:08:07 M3520 kernel: [  605.148276]  cfg80211_stop_p2p_device+0x6c/0x180 [cfg80211]
Feb 19 10:08:07 M3520 kernel: [  605.148281]  cfg80211_shutdown_all_interfaces+0x96/0xc0 [cfg80211]
Feb 19 10:08:07 M3520 kernel: [  605.148287]  cfg80211_rfkill_set_block+0x26/0x30 [cfg80211]
Feb 19 10:08:07 M3520 kernel: [  605.148288]  rfkill_set_block+0x90/0x160
Feb 19 10:08:07 M3520 kernel: [  605.148289]  rfkill_fop_write+0x117/0x1c0
Feb 19 10:08:07 M3520 kernel: [  605.148290]  __vfs_write+0x18/0x40
Feb 19 10:08:07 M3520 kernel: [  605.148291]  vfs_write+0xb8/0x1b0
Feb 19 10:08:07 M3520 kernel: [  605.148292]  ? do_sys_open+0x1b4/0x280
Feb 19 10:08:07 M3520 kernel: [  605.148293]  SyS_write+0x55/0xc0
Feb 19 10:08:07 M3520 kernel: [  605.148294]  ? SyS_fcntl+0x5d/0xb0
Feb 19 10:08:07 M3520 kernel: [  605.148296]  entry_SYSCALL_64_fastpath+0x33/0xa3
Feb 19 10:08:07 M3520 kernel: [  605.148297] RIP: 0033:0x7f9d87f8f4bd
Feb 19 10:08:07 M3520 kernel: [  605.148297] RSP: 002b:00007ffe191f1fb0 EFLAGS: 00000293 ORIG_RAX: 0000000000000001
Feb 19 10:08:07 M3520 kernel: [  605.148298] RAX: ffffffffffffffda RBX: 0000000000000018 RCX: 00007f9d87f8f4bd
Feb 19 10:08:07 M3520 kernel: [  605.148299] RDX: 0000000000000008 RSI: 00007ffe191f1fc0 RDI: 0000000000000018
Feb 19 10:08:07 M3520 kernel: [  605.148299] RBP: 0000000000000000 R08: 000000000249e5c0 R09: 0000000000000005
Feb 19 10:08:07 M3520 kernel: [  605.148300] R10: 0000000000000050 R11: 0000000000000293 R12: 00007f9d8a11e7b8
Feb 19 10:08:07 M3520 kernel: [  605.148300] R13: 00000000024f31b0 R14: 0000000000000000 R15: 000000000061c578
Feb 19 10:08:07 M3520 kernel: [  605.148305] INFO: task landscape-broke:4175 blocked for more than 120 seconds.
Feb 19 10:08:07 M3520 kernel: [  605.148306]       Tainted: P           OE   4.13.0-32-generic #35~16.04.1-Ubuntu
Feb 19 10:08:07 M3520 kernel: [  605.148307] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Feb 19 10:08:07 M3520 kernel: [  605.148307] landscape-broke D    0  4175   1566 0x00000000
Feb 19 10:08:07 M3520 kernel: [  605.148308] Call Trace:
Feb 19 10:08:07 M3520 kernel: [  605.148310]  __schedule+0x3c2/0x890
Feb 19 10:08:07 M3520 kernel: [  605.148311]  ? __slab_free+0x9e/0x2e0
Feb 19 10:08:07 M3520 kernel: [  605.148312]  schedule+0x36/0x80
Feb 19 10:08:07 M3520 kernel: [  605.148313]  schedule_preempt_disabled+0xe/0x10
Feb 19 10:08:07 M3520 kernel: [  605.148314]  __mutex_lock.isra.2+0x2ae/0x4e0
Feb 19 10:08:07 M3520 kernel: [  605.148315]  __mutex_lock_slowpath+0x13/0x20
Feb 19 10:08:07 M3520 kernel: [  605.148316]  ? __mutex_lock_slowpath+0x13/0x20
Feb 19 10:08:07 M3520 kernel: [  605.148317]  mutex_lock+0x2f/0x40
Feb 19 10:08:07 M3520 kernel: [  605.148318]  rtnetlink_rcv+0x19/0x30
Feb 19 10:08:07 M3520 kernel: [  605.148320]  netlink_unicast+0x18c/0x240
Feb 19 10:08:07 M3520 kernel: [  605.148321]  netlink_sendmsg+0x2dd/0x3c0
Feb 19 10:08:07 M3520 kernel: [  605.148323]  sock_sendmsg+0x38/0x50
Feb 19 10:08:07 M3520 kernel: [  605.148324]  SYSC_sendto+0x101/0x190
Feb 19 10:08:07 M3520 kernel: [  605.148325]  ? SYSC_getsockname+0x89/0xe0
Feb 19 10:08:07 M3520 kernel: [  605.148327]  ? fd_install+0x25/0x30
Feb 19 10:08:07 M3520 kernel: [  605.148327]  ? sock_map_fd+0x44/0x70
Feb 19 10:08:07 M3520 kernel: [  605.148329]  SyS_sendto+0xe/0x10
Feb 19 10:08:07 M3520 kernel: [  605.148330]  entry_SYSCALL_64_fastpath+0x33/0xa3
Feb 19 10:08:07 M3520 kernel: [  605.148330] RIP: 0033:0x7fec02ab4513
Feb 19 10:08:07 M3520 kernel: [  605.148331] RSP: 002b:00007febf3bf3b10 EFLAGS: 00000293 ORIG_RAX: 000000000000002c
Feb 19 10:08:07 M3520 kernel: [  605.148331] RAX: ffffffffffffffda RBX: 00007febf3bf4bd0 RCX: 00007fec02ab4513
Feb 19 10:08:07 M3520 kernel: [  605.148332] RDX: 0000000000000014 RSI: 00007febf3bf4bd0 RDI: 0000000000000010
Feb 19 10:08:07 M3520 kernel: [  605.148332] RBP: 00007febf3bf4c60 R08: 00007febf3bf4bb0 R09: 000000000000000c
Feb 19 10:08:07 M3520 kernel: [  605.148333] R10: 0000000000000000 R11: 0000000000000293 R12: 00007febf3bf4bb0
Feb 19 10:08:07 M3520 kernel: [  605.148333] R13: 000000000000061f R14: 0000000000000010 R15: 0000000000000010
Feb 19 10:08:07 M3520 kernel: [  605.148335] INFO: task lshw:1598 blocked for more than 120 seconds.
Feb 19 10:08:07 M3520 kernel: [  605.148336]       Tainted: P           OE   4.13.0-32-generic #35~16.04.1-Ubuntu
Feb 19 10:08:07 M3520 kernel: [  605.148336] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Feb 19 10:08:07 M3520 kernel: [  605.148337] lshw            D    0  1598   1569 0x00000000
Feb 19 10:08:07 M3520 kernel: [  605.148338] Call Trace:
Feb 19 10:08:07 M3520 kernel: [  605.148339]  __schedule+0x3c2/0x890
Feb 19 10:08:07 M3520 kernel: [  605.148340]  ? path_openat+0x3cc/0x13e0
Feb 19 10:08:07 M3520 kernel: [  605.148341]  schedule+0x36/0x80
Feb 19 10:08:07 M3520 kernel: [  605.148342]  schedule_preempt_disabled+0xe/0x10
Feb 19 10:08:07 M3520 kernel: [  605.148342]  __mutex_lock.isra.2+0x2ae/0x4e0
Feb 19 10:08:07 M3520 kernel: [  605.148344]  __mutex_lock_slowpath+0x13/0x20
Feb 19 10:08:07 M3520 kernel: [  605.148344]  ? __mutex_lock_slowpath+0x13/0x20
Feb 19 10:08:07 M3520 kernel: [  605.148345]  mutex_lock+0x2f/0x40
Feb 19 10:08:07 M3520 kernel: [  605.148346]  usb_device_read+0xc3/0x150
Feb 19 10:08:07 M3520 kernel: [  605.148347]  full_proxy_read+0x54/0x90
Feb 19 10:08:07 M3520 kernel: [  605.148348]  __vfs_read+0x18/0x40
Feb 19 10:08:07 M3520 kernel: [  605.148349]  vfs_read+0x93/0x130
Feb 19 10:08:07 M3520 kernel: [  605.148350]  SyS_read+0x55/0xc0
Feb 19 10:08:07 M3520 kernel: [  605.148351]  entry_SYSCALL_64_fastpath+0x33/0xa3
Feb 19 10:08:07 M3520 kernel: [  605.148351] RIP: 0033:0x7f23c0cb9260
Feb 19 10:08:07 M3520 kernel: [  605.148352] RSP: 002b:00007ffcc2e12268 EFLAGS: 00000246 ORIG_RAX: 0000000000000000
Feb 19 10:08:07 M3520 kernel: [  605.148352] RAX: ffffffffffffffda RBX: 00000000009d50e0 RCX: 00007f23c0cb9260
Feb 19 10:08:07 M3520 kernel: [  605.148353] RDX: 0000000000001000 RSI: 0000000000b0eca0 RDI: 0000000000000003
Feb 19 10:08:07 M3520 kernel: [  605.148353] RBP: 00007ffcc2e13100 R08: 00007f23c0f86ba8 R09: 0000000000000000
Feb 19 10:08:07 M3520 kernel: [  605.148353] R10: 00007f23c0f86b78 R11: 0000000000000246 R12: 00007ffcc2e12410
Feb 19 10:08:07 M3520 kernel: [  605.148354] R13: 0000000000000000 R14: 0000000000000000 R15: 0000000000000000
Feb 19 10:08:07 M3520 kernel: [  605.148359] INFO: task fusermount:2576 blocked for more than 120 seconds.
Feb 19 10:08:07 M3520 kernel: [  605.148360]       Tainted: P           OE   4.13.0-32-generic #35~16.04.1-Ubuntu
Feb 19 10:08:07 M3520 kernel: [  605.148361] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Feb 19 10:08:07 M3520 kernel: [  605.148361] fusermount      D    0  2576   1705 0x00000000
Feb 19 10:08:07 M3520 kernel: [  605.148362] Call Trace:
Feb 19 10:08:07 M3520 kernel: [  605.148363]  __schedule+0x3c2/0x890
Feb 19 10:08:07 M3520 kernel: [  605.148364]  schedule+0x36/0x80
Feb 19 10:08:07 M3520 kernel: [  605.148365]  schedule_timeout+0x1f0/0x360
Feb 19 10:08:07 M3520 kernel: [  605.148366]  ? ttwu_do_wakeup+0x1e/0x150
Feb 19 10:08:07 M3520 kernel: [  605.148367]  ? ttwu_do_activate+0x7a/0x90
Feb 19 10:08:07 M3520 kernel: [  605.148368]  wait_for_completion+0xb4/0x140
Feb 19 10:08:07 M3520 kernel: [  605.148368]  ? wait_for_completion+0xb4/0x140
Feb 19 10:08:07 M3520 kernel: [  605.148369]  ? wake_up_q+0x70/0x70
Feb 19 10:08:07 M3520 kernel: [  605.148370]  __synchronize_srcu.part.14+0x85/0xb0
Feb 19 10:08:07 M3520 kernel: [  605.148372]  ? trace_raw_output_rcu_utilization+0x50/0x50
Feb 19 10:08:07 M3520 kernel: [  605.148373]  ? ktime_get_mono_fast_ns+0x4b/0xa0
Feb 19 10:08:07 M3520 kernel: [  605.148374]  synchronize_srcu+0xcd/0xe0
Feb 19 10:08:07 M3520 kernel: [  605.148375]  ? synchronize_srcu+0xcd/0xe0
Feb 19 10:08:07 M3520 kernel: [  605.148375]  debugfs_remove+0x72/0xa0
Feb 19 10:08:07 M3520 kernel: [  605.148377]  bdi_unregister+0x18e/0x210
Feb 19 10:08:07 M3520 kernel: [  605.148378]  bdi_put+0x97/0xa0
Feb 19 10:08:07 M3520 kernel: [  605.148379]  generic_shutdown_super+0xef/0x120
Feb 19 10:08:07 M3520 kernel: [  605.148380]  kill_anon_super+0x12/0x20
Feb 19 10:08:07 M3520 kernel: [  605.148381]  fuse_kill_sb_anon+0x47/0x50
Feb 19 10:08:07 M3520 kernel: [  605.148382]  deactivate_locked_super+0x43/0x70
Feb 19 10:08:07 M3520 kernel: [  605.148383]  deactivate_super+0x5a/0x60
Feb 19 10:08:07 M3520 kernel: [  605.148384]  cleanup_mnt+0x3f/0x80
Feb 19 10:08:07 M3520 kernel: [  605.148385]  __cleanup_mnt+0x12/0x20
Feb 19 10:08:07 M3520 kernel: [  605.148385]  task_work_run+0x7e/0xa0
Feb 19 10:08:07 M3520 kernel: [  605.148387]  exit_to_usermode_loop+0xc4/0xd0
Feb 19 10:08:07 M3520 kernel: [  605.148388]  syscall_return_slowpath+0x59/0x60
Feb 19 10:08:07 M3520 kernel: [  605.148389]  entry_SYSCALL_64_fastpath+0xa1/0xa3
Feb 19 10:08:07 M3520 kernel: [  605.148389] RIP: 0033:0x7f36ed053487
Feb 19 10:08:07 M3520 kernel: [  605.148390] RSP: 002b:00007ffdc7a98c88 EFLAGS: 00000206 ORIG_RAX: 00000000000000a6
Feb 19 10:08:07 M3520 kernel: [  605.148391] RAX: 0000000000000000 RBX: 00007f36ed516698 RCX: 00007f36ed053487
Feb 19 10:08:07 M3520 kernel: [  605.148391] RDX: 0000000000000000 RSI: 000000000000000a RDI: 000055c3746527ae
Feb 19 10:08:07 M3520 kernel: [  605.148391] RBP: 0000000000000003 R08: 0000000000000000 R09: 0000000000000001
Feb 19 10:08:07 M3520 kernel: [  605.148392] R10: 0000000000000000 R11: 0000000000000206 R12: 000055c3746527a0
Feb 19 10:08:07 M3520 kernel: [  605.148392] R13: 00000000ffffffff R14: 000055c374650050 R15: 000055c374652a17
Feb 19 10:08:07 M3520 kernel: [  605.148414] INFO: task dropbox:3816 blocked for more than 120 seconds.
Feb 19 10:08:07 M3520 kernel: [  605.148415]       Tainted: P           OE   4.13.0-32-generic #35~16.04.1-Ubuntu
Feb 19 10:08:07 M3520 kernel: [  605.148415] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Feb 19 10:08:07 M3520 kernel: [  605.148416] dropbox         D    0  3816      1 0x00000000
Feb 19 10:08:07 M3520 kernel: [  605.148417] Call Trace:
Feb 19 10:08:07 M3520 kernel: [  605.148418]  __schedule+0x3c2/0x890
Feb 19 10:08:07 M3520 kernel: [  605.148418]  schedule+0x36/0x80
Feb 19 10:08:07 M3520 kernel: [  605.148419]  schedule_preempt_disabled+0xe/0x10
Feb 19 10:08:07 M3520 kernel: [  605.148420]  __mutex_lock.isra.2+0x2ae/0x4e0
Feb 19 10:08:07 M3520 kernel: [  605.148421]  __mutex_lock_slowpath+0x13/0x20
Feb 19 10:08:07 M3520 kernel: [  605.148422]  ? __mutex_lock_slowpath+0x13/0x20
Feb 19 10:08:07 M3520 kernel: [  605.148423]  mutex_lock+0x2f/0x40
Feb 19 10:08:07 M3520 kernel: [  605.148424]  rtnetlink_rcv+0x19/0x30
Feb 19 10:08:07 M3520 kernel: [  605.148425]  netlink_unicast+0x18c/0x240
Feb 19 10:08:07 M3520 kernel: [  605.148426]  netlink_sendmsg+0x2dd/0x3c0
Feb 19 10:08:07 M3520 kernel: [  605.148427]  sock_sendmsg+0x38/0x50
Feb 19 10:08:07 M3520 kernel: [  605.148428]  SYSC_sendto+0x101/0x190
Feb 19 10:08:07 M3520 kernel: [  605.148429]  ? SYSC_getsockname+0x89/0xe0
Feb 19 10:08:07 M3520 kernel: [  605.148430]  ? fd_install+0x25/0x30
Feb 19 10:08:07 M3520 kernel: [  605.148431]  ? sock_map_fd+0x44/0x70
Feb 19 10:08:07 M3520 kernel: [  605.148432]  SyS_sendto+0xe/0x10
Feb 19 10:08:07 M3520 kernel: [  605.148433]  entry_SYSCALL_64_fastpath+0x33/0xa3
Feb 19 10:08:07 M3520 kernel: [  605.148434] RIP: 0033:0x7f17205af513
Feb 19 10:08:07 M3520 kernel: [  605.148434] RSP: 002b:00007f15d6ffaaa0 EFLAGS: 00000293 ORIG_RAX: 000000000000002c
Feb 19 10:08:07 M3520 kernel: [  605.148435] RAX: ffffffffffffffda RBX: 00007f15d6ffbc00 RCX: 00007f17205af513
Feb 19 10:08:07 M3520 kernel: [  605.148435] RDX: 0000000000000014 RSI: 00007f15d6ffbb00 RDI: 0000000000000088
Feb 19 10:08:07 M3520 kernel: [  605.148435] RBP: 00007f15d6ffbb70 R08: 00007f15d6ffbae0 R09: 000000000000000c
Feb 19 10:08:07 M3520 kernel: [  605.148436] R10: 0000000000000000 R11: 0000000000000293 R12: 00007f15d6ffbb00
Feb 19 10:08:07 M3520 kernel: [  605.148436] R13: 00007f15d6ffbae0 R14: 00007f15d6ffaab0 R15: 0000000000000000

---

