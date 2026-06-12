---
title: "RT3290 Wireless issue in 16.04"
date: 2017-03-16
forum: Networking &amp; Wireless
---

### Post by prajankya on 2017-03-16
I have problems for wireless driver in my HP Envy Touchsmart 15 j001tx

Wireless device is Ralink RT3290

I followed many guides like
[http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working](http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working)
[http://askubuntu.com/questions/760838/how-do-i-get-an-rt3290-wireless-card-to-work](http://askubuntu.com/questions/760838/how-do-i-get-an-rt3290-wireless-card-to-work)
[http://askubuntu.com/questions/763772/problem-with-rt3290-wifi-driver](http://askubuntu.com/questions/763772/problem-with-rt3290-wifi-driver)
[http://askubuntu.com/questions/545238/how-to-install-wifi-driver-ralink-rt3290](http://askubuntu.com/questions/545238/how-to-install-wifi-driver-ralink-rt3290)
[http://askubuntu.com/questions/792209/ralink-rt3290-wifi-card-not-working-on-ubuntu-16-04](http://askubuntu.com/questions/792209/ralink-rt3290-wifi-card-not-working-on-ubuntu-16-04)


I tried to blacklist all the wireless drivers and to enable only one at a time, but with no luck..

This is my Wireless info file :

```



########## wireless info START ##########


Report from: 17 Mar 2017 07:36 IST +0530


Booted last: 17 Mar 2017 00:00 IST +0530


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.8.0-41-generic #44~16.04.1-Ubuntu SMP Fri Mar 3 17:11:16 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


07:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    DeviceName: Ralink RT3290LE 802.11bgn 1x1 Wi-Fi Adapter
    Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]


0f:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    DeviceName: Hanksville Gbe Lan Connection
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:1963]


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 064e:e264 Suyin Corp. 
Bus 002 Device 002: ID 271d:0003  
Bus 002 Device 005: ID 138a:0050 Validity Sensors, Inc. Swipe Fingerprint Sensor
Bus 002 Device 004: ID 0eef:a137 D-WAV Scientific Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


rt2800pci              16384  0
rt2800mmio             20480  1 rt2800pci
rt2800lib              94208  2 rt2800mmio,rt2800pci
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
rt2x00lib              57344  5 rt2800lib,rt2x00pci,rt2800mmio,rt2x00mmio,rt2800pci
mac80211              761856  3 rt2800lib,rt2x00pci,rt2x00lib
eeprom_93cx6           16384  1 rt2800pci
cfg80211              581632  2 rt2x00lib,mac80211
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
rt3290sta            1159168  0
mxm_wmi                16384  1 nouveau
wmi                    16384  3 mxm_wmi,nouveau,hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eno1      Link encap:Ethernet  HWaddr <MAC 'eno1' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


enp0s20u4 Link encap:Ethernet  HWaddr <MAC 'enp0s20u4' [IF2]>  
          inet addr:192.168.42.185  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::169d:d213:b48a:60/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7181 errors:1 dropped:0 overruns:0 frame:1
          TX packets:7013 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5285665 (5.2 MB)  TX bytes:1371108 (1.3 MB)


rename3   Link encap:Ethernet  HWaddr <MAC 'rename3' [IF3]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 


##### iwconfig ##########################


lo        no wireless extensions.


enp0s20u4  no wireless extensions.


eno1      no wireless extensions.


rename3   Ralink STA  
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    100    0        0 enp0s20u4
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp0s20u4
192.168.42.0    0.0.0.0         255.255.255.0   U     100    0        0 enp0s20u4


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root      4055     1  0 07:28 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp0s20u4
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         GIONEE
GENERAL.PRODUCT:                        P4
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'enp0s20u4' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /virtual/device/placeholder/2
GENERAL.IP-IFACE:                       enp0s20u4
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     enp0s20u4
GENERAL.CON-UUID:                       443ac81d-63b2-4f5f-9351-e80768a805f8
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1,2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   29b71367-cffa-3899-9c5b-bcd728754034 | Wired connection 1
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   443ac81d-63b2-4f5f-9351-e80768a805f8 | enp0s20u4
IP4.ADDRESS[1]:                         192.168.42.185/24
IP4.GATEWAY:                            192.168.42.129
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[5]:                        ip_address = 192.168.42.185
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.42.129
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.42.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 37800
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.42.129
DHCP4.OPTION[16]:                       dhcp_renewal_time = 21600
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1489759266
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = prajankya-lappy
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.42.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[28]:                       next_server = 192.168.42.129
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 43200
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
IP6.ADDRESS[1]:                         fe80::169d:d213:b48a:60/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               rtl8168g-2_0.0.1 02/06/13
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.6/0000:0f:00.0/net/eno1
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


[[/etc/NetworkManager/system-connections/Kickass]] (600 root)
[connection] id=Kickass | type=wifi | permissions=user:prajankya:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Kickass
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Asia/Kolkata (based on set time zone)


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


enp0s20u4  no frequency information.


eno1      no frequency information.


rename3   0 channels


##### iwlist scan #######################


rename3   Interface doesn't support scanning : Network is down


lo        Interface doesn't support scanning.


enp0s20u4  Interface doesn't support scanning.


eno1      Interface doesn't support scanning.


##### module infos ######################


[rt2800pci]
filename:       /lib/modules/4.8.0-41-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     4D2CAAE95D28B3DF4F72A52
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       4.8.0-41-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2800mmio]
filename:       /lib/modules/4.8.0-41-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     DBE617B0243C0FEB62786D4
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       4.8.0-41-generic SMP mod_unload modversions 


[rt2800lib]
filename:       /lib/modules/4.8.0-41-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     7092408A4EF1A70FC0C7538
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.8.0-41-generic SMP mod_unload modversions 


[rt2x00pci]
filename:       /lib/modules/4.8.0-41-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     D84965563CC7530CFFD2269
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.8.0-41-generic SMP mod_unload modversions 


[rt2x00mmio]
filename:       /lib/modules/4.8.0-41-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     02CA9DA77FC2C7FCCC58176
depends:        rt2x00lib
intree:         Y
vermagic:       4.8.0-41-generic SMP mod_unload modversions 


[rt2x00lib]
filename:       /lib/modules/4.8.0-41-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     CF930122B7900096FC259FA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.8.0-41-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.8.0-41-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     9AF49B72127065FCF655D6A
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-41-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.8.0-41-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     46F63B461AA5E38D042F531
depends:        
intree:         Y
vermagic:       4.8.0-41-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[rt3290sta]
filename:       /lib/modules/4.8.0-41-generic/kernel/drivers/net/wireless/rt3290sta.ko
version:        2.6.0.0_rev1
srcversion:     96CD86FDB670E3BFC172F9B
depends:        
vermagic:       4.8.0-41-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)


##### module parameters #################


[rt2800pci]
nohwcrypt: N


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


rt3290sta


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
blacklist rt2800pci
blacklist rt2800mmio
blacklist rt2800lib
blacklist 2x00pci
blacklist 2x00mmio
blacklist rt2x00lib


[/etc/modprobe.d/blacklist-ralink.conf]
blacklist rt2800pci
blacklist rt2x00pci  


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


[   31.488269] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   31.755512] r8169 0000:0f:00.0 eno1: link down
[   31.755581] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready (repeated 2 times)


########## wireless info END ############



```

---

### Post by prajankya on 2017-03-16
Previously I had made it working with the driver form [https://github.com/pkeeper/rt3290sta.git](https://github.com/pkeeper/rt3290sta.git), until I connected my mobile in usb tethering mode. After which DNS resolv started giving problems and no wifi networks found. Then after reinstalling that same driver (github/pkeeper/rt3290sta) No wireless interface, nothing in iwconfig.

Just as a note, when I was installing 16.04, I formatted previous 14.04 and not "upgraded". In the installation process, the wifi speed was very slow and after few minutes the wifi stopped working. This lead me to assume that 16.04 doesn't have a proper driver for my device.

---

### Post by wildmanne39 on 2017-03-17
*Thread moved to **Networking & Wireless**.*

---

