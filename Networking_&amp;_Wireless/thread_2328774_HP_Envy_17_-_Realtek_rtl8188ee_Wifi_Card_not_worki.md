---
title: "HP Envy 17 - Realtek rtl8188ee Wifi Card not working"
date: 2016-06-24
forum: Networking &amp; Wireless
---

### Post by levi10 on 2016-06-24
Dear all,

I was running Windows 10 as my main OS with a VM using Ubuntu 14.04. Some weeks ago I decided to give Ubuntu 16.04 a try and completely wipe out my Windows 10 partition. The installation went fast but I realized that first of all somehow Ubuntu was feeling slower than Windows 10 and what is more important, my Wifi was not working! 

It did detect Wifis around the area but could not connect to one. I checked this thread: [http://ubuntuforums.org/showthread.php?t=2196520](http://ubuntuforums.org/showthread.php?t=2196520) and tried following the steps. 

Once I tried doing what post #10 said, I got an error:

[ATTACH=CONFIG]269756[/ATTACH]

Could you please help me? 

P.S: And the weird thing is that I still feel Windows 10 was running faster... (I have an SSD where I put my OS). Maybe I have not installed proper drivers.

---

### Post by jeremy31 on 2016-06-24
Please see the wireless script link in my signature and post results.  The errors you had were likely because that backports package is pretty old

Welcome to the forums

---

### Post by levi10 on 2016-06-24
Thank you for your reply and warm welcome.

This is the full .txt file that you asked for:


```


########## wireless info START ##########


Report from: 25 Jun 2016 00:23 CEST +0200


Booted last: 25 Jun 2016 00:00 CEST +0200


Script from: 26 May 2016 21:56 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:27:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
	DeviceName: Realtek RTL8188EE 802.11bgn Wi-Fi Adapter
	Subsystem: Hewlett-Packard Company RTL8188EE Wireless Network Adapter [103c:197d]


0f:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	DeviceName: Hanksville Gbe Lan Connection
	Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:1966]


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 064e:9301 Suyin Corp. 
Bus 002 Device 003: ID 138a:0050 Validity Sensors, Inc. Swipe Fingerprint Sensor
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no


##### lsmod #############################


hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
rtl8188ee              86016  0
rtl_pci                28672  1 rtl8188ee
rtlwifi                77824  2 rtl_pci,rtl8188ee
mac80211              737280  3 rtl_pci,rtlwifi,rtl8188ee
cfg80211              565248  2 mac80211,rtlwifi
mxm_wmi                16384  1 nouveau
wmi                    20480  3 hp_wmi,mxm_wmi,nouveau


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eno1      Link encap:Ethernet  HWaddr <MAC 'eno1' [IF1]>  
          inet addr:192.168.0.34  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2a02:8109:8080:12a2:b58f:93b1:ef24:6df9/64 Scope:Global
          inet6 addr: fe80::d90:59b7:d23a:5417/64 Scope:Link
          inet6 addr: 2a02:8109:8080:12a2:a6dc:4b06:644f:1216/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:62051 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24217 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:84615658 (84.6 MB)  TX bytes:3059416 (3.0 MB)


wlo1      Link encap:Ethernet  HWaddr <MAC 'wlo1' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


lo        no wireless extensions.


eno1      no wireless extensions.


wlo1      IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eno1
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 eno1


##### resolv.conf #######################


nameserver 127.0.1.1
search home


##### network managers ##################


Installed:


	NetworkManager


Running:


root       968     1  0 00:15 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.6/0000:0f:00.0/net/eno1
GENERAL.IP-IFACE:                       eno1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       2bf05f48-10c8-4767-808d-b1802ba05a69
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   2bf05f48-10c8-4767-808d-b1802ba05a69 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.34/24
IP4.GATEWAY:                            192.168.0.1
IP4.DNS[1]:                             192.168.0.1
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        default_ip_ttl = 64
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        host_name = mjeshtri
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       requested_netbios_scope = 1
DHCP4.OPTION[11]:                       next_server = 192.168.0.1
DHCP4.OPTION[12]:                       expiry = 1466810141
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 192.168.0.1
DHCP4.OPTION[16]:                       dhcp_message_type = 5
DHCP4.OPTION[17]:                       ip_address = 192.168.0.34
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name = home
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       dhcp_lease_time = 3600
DHCP4.OPTION[25]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[28]:                       network_number = 192.168.0.0
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         2a02:8109:8080:12a2:b58f:93b1:ef24:6df9/64
IP6.ADDRESS[2]:                         2a02:8109:8080:12a2:a6dc:4b06:644f:1216/64
IP6.ADDRESS[3]:                         fe80::d90:59b7:d23a:5417/64
IP6.GATEWAY:                            fe80::5667:51ff:fe3e:581a
IP6.ROUTE[1]:                           dst = 2a02:8109:8080:12a2::/64, nh = fe80::5667:51ff:fe3e:581a, mt = 100
IP6.DNS[1]:                             2a02:8109:8080:12a2:5667:51ff:fe3e:581a
IP6.DOMAIN[1]:                          home
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:35:6e:0:5e:f0:7a:84:e4:fa:e2:b7:90:a1:d4:a6:2f
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2a02:8109:8080:12a2:5667:51ff:fe3e:581a
DHCP6.OPTION[3]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[4]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[5]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[6]:                        dhcp6_domain_search = home.
DHCP6.OPTION[7]:                        dhcp6_preference = 0
DHCP6.OPTION[8]:                        dhcp6_server_id = 0:1:3:1:1e:ed:b4:c1:2a:2:81:9:80:0:0:1:d5:6a:96:3b:1f:b9:87:27


GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8188EE Wireless Network Adapter
GENERAL.DRIVER:                         rtl8188ee
GENERAL.DRIVER-VERSION:                 4.4.0-24-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlo1' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.0/net/wlo1
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


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/KabelBox-1A98]] (600 root)
[connection] id=KabelBox-1A98 | type=wifi | permissions=user:aulon:;
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=KabelBox-1A98
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Berlin (based on set time zone)


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


eno1      no frequency information.


wlo1      13 channels in total; available frequencies :
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


##### iwlist scan #######################


lo        Interface doesn't support scanning.


wlo1      Interface doesn't support scanning : Network is down


eno1      Interface doesn't support scanning.


##### module infos ######################


[rtl8188ee]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8188ee/rtl8188ee.ko
firmware:       rtlwifi/rtl8188efw.bin
description:    Realtek 8188E 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         zhiyuan_yang	<zhiyuan_yang@realsil.com.cn>
srcversion:     F3DA2CAE75202990553C79D
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)


[rtl_pci]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     CCAF123FC0D21AE93AD5A6F
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 


[rtlwifi]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     251B17ACC83990EE9A63C56
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.4.0-24-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-24-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8188ee]
debug: 0
disable_watchdog: N
fwlps: N
ips: N
msi: Y
swenc: N
swlps: N


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


##### dmesg #############################


[   13.688215] rtl8188ee: rtl8188ee: Power Save off (module option)
[   13.688217] rtl8188ee: rtl8188ee: FW Power Save off (module option)
[   13.688257] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[   13.694389] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   13.694632] rtlwifi: rtlwifi: wireless switch is on
[   13.735008] rtl8188ee 0000:07:00.0 wlo1: renamed from wlan0
[   14.402517] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[   14.405143] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   14.448822] r8169 0000:0f:00.0 eno1: link down (repeated 2 times)
[   14.448890] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   17.129653] r8169 0000:0f:00.0 eno1: link up
[   17.129662] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready


########## wireless info END ############



```

---

### Post by jeremy31 on 2016-06-25
Your wifi is soft blocked so try your FN keyboard combo and see if it enables, otherwise use ```
rfkill unblock wifi
```

---

### Post by levi10 on 2016-06-25
Oh yes. My mistake, sorry. 

I want to point out that I do and can connect to the Wifi. It is just that even though I am connected, there is no internet connection.

This is the output with the wifi enabled:

```


########## wireless info START ##########


Report from: 25 Jun 2016 19:43 CEST +0200


Booted last: 25 Jun 2016 00:00 CEST +0200


Script from: 26 May 2016 21:56 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:27:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
	DeviceName: Realtek RTL8188EE 802.11bgn Wi-Fi Adapter
	Subsystem: Hewlett-Packard Company RTL8188EE Wireless Network Adapter [103c:197d]


0f:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	DeviceName: Hanksville Gbe Lan Connection
	Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:1966]


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 064e:9301 Suyin Corp. 
Bus 002 Device 003: ID 138a:0050 Validity Sensors, Inc. Swipe Fingerprint Sensor
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
rtl8188ee              86016  0
rtl_pci                28672  1 rtl8188ee
rtlwifi                77824  2 rtl_pci,rtl8188ee
mac80211              737280  3 rtl_pci,rtlwifi,rtl8188ee
cfg80211              565248  2 mac80211,rtlwifi
mxm_wmi                16384  1 nouveau
wmi                    20480  3 hp_wmi,mxm_wmi,nouveau


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eno1      Link encap:Ethernet  HWaddr <MAC 'eno1' [IF1]>  
          inet addr:192.168.0.34  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ec18:d2c2:c3eb:bd4b/64 Scope:Link
          inet6 addr: 2a02:8109:8080:12a2:91ec:466c:219b:bd14/64 Scope:Global
          inet6 addr: 2a02:8109:8080:12a2:784a:8d9e:ec34:cd1d/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:528026 errors:0 dropped:0 overruns:0 frame:0
          TX packets:319636 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:691871287 (691.8 MB)  TX bytes:52642073 (52.6 MB)


wlo1      Link encap:Ethernet  HWaddr <MAC 'wlo1' [IF2]>  
          inet6 addr: fe80::32c4:aad7:306d:279/64 Scope:Link
          inet6 addr: 2a02:8109:8080:12a2:14b9:4adb:c350:9f3b/64 Scope:Global
          inet6 addr: 2a02:8109:8080:12a2:570:d7b2:ccba:f55d/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:88 errors:0 dropped:1 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16703 (16.7 KB)  TX bytes:11528 (11.5 KB)


##### iwconfig ##########################


lo        no wireless extensions.


eno1      no wireless extensions.


wlo1      IEEE 802.11bgn  ESSID:"KabelBox-1A98"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'KabelBox-1A98' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eno1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eno1
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 eno1


##### resolv.conf #######################


nameserver 127.0.1.1
search home


##### network managers ##################


Installed:


	NetworkManager


Running:


root       985     1  0 11:02 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.6/0000:0f:00.0/net/eno1
GENERAL.IP-IFACE:                       eno1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       fa80845f-9515-4aed-99ed-b10b858aacc8
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   fa80845f-9515-4aed-99ed-b10b858aacc8 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.34/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        default_ip_ttl = 64
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        host_name = mjeshtri
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       requested_netbios_scope = 1
DHCP4.OPTION[11]:                       next_server = 192.168.0.1
DHCP4.OPTION[12]:                       expiry = 1466879574
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 192.168.0.1
DHCP4.OPTION[16]:                       dhcp_message_type = 5
DHCP4.OPTION[17]:                       ip_address = 192.168.0.34
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name = home
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       dhcp_lease_time = 3600
DHCP4.OPTION[25]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[28]:                       network_number = 192.168.0.0
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         2a02:8109:8080:12a2:91ec:466c:219b:bd14/64
IP6.ADDRESS[2]:                         2a02:8109:8080:12a2:784a:8d9e:ec34:cd1d/64
IP6.ADDRESS[3]:                         fe80::ec18:d2c2:c3eb:bd4b/64
IP6.GATEWAY:                            fe80::5667:51ff:fe3e:581a
IP6.ROUTE[1]:                           dst = 2a02:8109:8080:12a2::/64, nh = fe80::5667:51ff:fe3e:581a, mt = 100
IP6.DNS[1]:                             2a02:8109:8080:12a2:5667:51ff:fe3e:581a
IP6.DOMAIN[1]:                          home
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:35:6e:0:5e:f0:7a:84:e4:fa:e2:b7:90:a1:d4:a6:2f
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2a02:8109:8080:12a2:5667:51ff:fe3e:581a
DHCP6.OPTION[3]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[4]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[5]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[6]:                        dhcp6_domain_search = home.
DHCP6.OPTION[7]:                        dhcp6_preference = 0
DHCP6.OPTION[8]:                        dhcp6_server_id = 0:1:3:1:1e:ed:b4:c1:2a:2:81:9:80:0:0:1:d5:6a:96:3b:1f:b9:87:27


GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8188EE Wireless Network Adapter
GENERAL.DRIVER:                         rtl8188ee
GENERAL.DRIVER-VERSION:                 4.4.0-24-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlo1' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.0/net/wlo1
GENERAL.IP-IFACE:                       wlo1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     KabelBox-1A98
GENERAL.CON-UUID:                       d64648e2-49e1-47b7-81de-9f5a4794d0f9
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/3
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     72 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   d64648e2-49e1-47b7-81de-9f5a4794d0f9 | KabelBox-1A98
IP6.ADDRESS[1]:                         2a02:8109:8080:12a2:570:d7b2:ccba:f55d/64
IP6.ADDRESS[2]:                         2a02:8109:8080:12a2:14b9:4adb:c350:9f3b/64
IP6.ADDRESS[3]:                         fe80::32c4:aad7:306d:279/64
IP6.GATEWAY:                            fe80::5667:51ff:fe3e:581a
IP6.DNS[1]:                             2a02:8109:8080:12a2:5667:51ff:fe3e:581a
IP6.DOMAIN[1]:                          home


SSID                  BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
KabelBox-1A98         <MAC 'KabelBox-1A98' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  78      &#9602;&#9604;&#9606;_  WPA2       yes     * 
Yoursweethome         <MAC 'Yoursweethome' [AC11]>  Infra  11    2462 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA2       no        
Telekom_FON           <MAC 'Telekom_FON' [AC10]>  Infra  11    2462 MHz  54 Mbit/s  47      &#9602;&#9604;__  --         no        
yoursweethome3        <MAC 'yoursweethome3' [AC7]>  Infra  4     2427 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA1 WPA2  no        
Quentin Design        <MAC 'Quentin Design' [AC14]>  Infra  6     2437 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA1 WPA2  no        
HITRON-D080           <MAC 'HITRON-D080' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA1 WPA2  no        
Quentin Design        <MAC 'Quentin Design' [AC6]>  Infra  1     2412 MHz  54 Mbit/s  27      &#9602;___  WPA1 WPA2  no        
Gay Hostel 2.4        <MAC 'Gay Hostel 2.4' [AN8]>  Infra  1     2412 MHz  54 Mbit/s  27      &#9602;___  WPA1 WPA2  no        
ngcz                  <MAC 'ngcz' [AC8]>  Infra  1     2412 MHz  54 Mbit/s  27      &#9602;___  WPA2       no        
Quentin Design        <MAC 'Quentin Design' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  27      &#9602;___  WPA1 WPA2  no        
jpc3                  <MAC 'jpc3' [AC5]>  Infra  1     2412 MHz  54 Mbit/s  27      &#9602;___  WPA1 WPA2  no        
homeNet               <MAC 'homeNet' [AN12]>  Infra  1     2412 MHz  54 Mbit/s  27      &#9602;___  WPA1 WPA2  no        
Vodafone Hotspot      <MAC 'Vodafone Hotspot' [AC4]>  Infra  1     2412 MHz  54 Mbit/s  27      &#9602;___  --         no        
Gay Hostel Guest 2.4  <MAC 'Gay Hostel Guest 2.4' [AC9]>  Infra  1     2412 MHz  54 Mbit/s  27      &#9602;___  WPA1 WPA2  no        
KabelBox-8440         <MAC 'KabelBox-8440' [AN15]>  Infra  11    2462 MHz  54 Mbit/s  27      &#9602;___  WPA2       no        


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


[[/etc/NetworkManager/system-connections/KabelBox-1A98]] (600 root)
[connection] id=KabelBox-1A98 | type=wifi | permissions=user:aulon:;
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=KabelBox-1A98
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Berlin (based on set time zone)


country DE: DFS-ETSI
	(2400 - 2483 @ 40), (N/A, 20), (N/A)
	(5150 - 5250 @ 80), (N/A, 20), (N/A), NO-OUTDOOR
	(5250 - 5350 @ 80), (N/A, 20), (0 ms), NO-OUTDOOR, DFS
	(5470 - 5725 @ 160), (N/A, 26), (0 ms), DFS
	(57000 - 66000 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


lo        no frequency information.


eno1      no frequency information.


wlo1      13 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


eno1      Interface doesn't support scanning.


Channel occupancy:


      9   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      3   APs on   Frequency:2.462 GHz (Channel 11)


wlo1      Scan completed :
          Cell 01 - Address: <MAC 'KabelBox-1A98' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"KabelBox-1A98"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000012dfe310d76
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Quentin Design' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Quentin Design"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000006885181d621
                    Extra: Last beacon: 128ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'HITRON-D080' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"HITRON-D080"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004fe63c47156
                    Extra: Last beacon: 192ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Vodafone Hotspot' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"Vodafone Hotspot"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004fe63c60bba
                    Extra: Last beacon: 84ms ago
          Cell 05 - Address: <MAC 'jpc3' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"jpc3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000061cc9f0180
                    Extra: Last beacon: 1184ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Quentin Design' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Quentin Design"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000e8e73a95180
                    Extra: Last beacon: 624ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'yoursweethome3' [AC7]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"yoursweethome3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000cf9c89186
                    Extra: Last beacon: 2464ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'ngcz' [AC8]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"ngcz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000040af6232
                    Extra: Last beacon: 3364ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'Gay Hostel Guest 2.4' [AC9]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Gay Hostel Guest 2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000481c14c3180
                    Extra: Last beacon: 23360ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'Telekom_FON' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:off
                    ESSID:"Telekom_FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003c20f9acb0
                    Extra: Last beacon: 720ms ago
          Cell 11 - Address: <MAC 'Yoursweethome' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Yoursweethome"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003c20f999de
                    Extra: Last beacon: 724ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'Quentin Design' [AC12]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Quentin Design"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000018ecbd88180
                    Extra: Last beacon: 2784ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'Quentin Design' [AC13]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Quentin Design"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000d94212c2180
                    Extra: Last beacon: 2340ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'Quentin Design' [AC14]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Quentin Design"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000e8e70f39180
                    Extra: Last beacon: 2100ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'Quentin Design' [AC15]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Quentin Design"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000009b6a47b2180
                    Extra: Last beacon: 748ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rtl8188ee]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8188ee/rtl8188ee.ko
firmware:       rtlwifi/rtl8188efw.bin
description:    Realtek 8188E 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         zhiyuan_yang	<zhiyuan_yang@realsil.com.cn>
srcversion:     F3DA2CAE75202990553C79D
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)


[rtl_pci]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     CCAF123FC0D21AE93AD5A6F
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 


[rtlwifi]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     251B17ACC83990EE9A63C56
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.4.0-24-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-24-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8188ee]
debug: 0
disable_watchdog: N
fwlps: N
ips: N
msi: Y
swenc: N
swlps: N


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


##### dmesg #############################


[ 8015.085374] rtlwifi: rtlwifi: wireless switch is on
[ 8015.149215] r8169 0000:0f:00.0 eno1: link down
[ 8016.419544] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 8016.419934] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[ 8016.465640] r8169 0000:0f:00.0 eno1: link down
[ 8016.465722] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[ 8019.413022] r8169 0000:0f:00.0 eno1: link up
[ 8019.413031] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready
[ 8021.400386] r8169 0000:0f:00.0 eno1: link down
[ 8024.399213] r8169 0000:0f:00.0 eno1: link up
[ 8025.007662] r8169 0000:0f:00.0 eno1: link down
[ 8039.237465] r8169 0000:0f:00.0 eno1: link up
[ 9894.397748] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready (repeated 2 times)
[ 9895.287012] wlo1: authenticate with <MAC 'KabelBox-1A98' [AC1]>
[ 9895.297073] wlo1: send auth to <MAC 'KabelBox-1A98' [AC1]> (try 1/3)
[ 9895.298527] wlo1: authenticated
[ 9895.298639] wlo1: associating with AP with corrupt probe response
[ 9895.299543] wlo1: associate with <MAC 'KabelBox-1A98' [AC1]> (try 1/3)
[ 9895.316054] wlo1: RX AssocResp from <MAC 'KabelBox-1A98' [AC1]> (capab=0x431 status=0 aid=5)
[ 9895.316363] wlo1: associated
[ 9895.316372] IPv6: ADDRCONF(NETDEV_CHANGE): wlo1: link becomes ready


########## wireless info END ############



```

---

### Post by jeremy31 on 2016-06-25
I would change the wifi router to channel 9 as it is on a crowded channel 1 now and reboot the router.  Change Network Manager settings for the wireless connection to IPv6 to ignore and reboot computer with ethernet unplugged.

Another issue is that your wifi isn't getting an IPv4 IP address and I am not sure why

---

### Post by levi10 on 2016-06-25
I am not the only one in the household using the router. And the others work fine with the Wifi. 

I installed Network Manager but when I run 'sudo start network-manager' it gives me: "start: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused"

I'm sorry I did not quite understand what was the second step. Should I ignore IPv4 or IPv6? And how do I do that

---

### Post by jeremy31 on 2016-06-25
See the pictures attached to Hadaka's post [http://ubuntuforums.org/showthread.php?t=2328415&p=13507622#post13507622](http://ubuntuforums.org/showthread.php?t=2328415&p=13507622#post13507622) to set IPv6 setting

It doesn't surprise me that other devices have no issues with your current settings.  They have to work in any type of conditions or they wouldn't sell many

It puzzles me that you had to install Network Manager as it should have been part of the download unless you have a server without GUI

---

### Post by levi10 on 2016-06-25
I did what the pics showed and rebooted. 

Still I am connected to the Wifi but no internet access

---

### Post by jeremy31 on 2016-06-25
I would download a new ISO and reinstall Ubuntu as something must have gotten corrupted, especially if you had to install network manager

---

### Post by levi10 on 2016-06-25
It was my mistake - I installed openvpn as part of network manager. So network manager should have been there. And I did reinstall ubuntu 3 times so far...

I had ubuntu dual boot with windows. I don't know what went wrong. I also installed ubuntu 14.04 at one point and still the wifi was not working.

---

### Post by jeremy31 on 2016-06-25
Does wifi work during a Try Ubuntu boot from an ISO?  It might be an issue with the router as your script results showed
```
wlo1: associating with AP with corrupt probe response
```

Is there a limit on how many devices that the router will connect to?

---

### Post by levi10 on 2016-06-25
I tried that a week ago. Did not work. I tried it now with a fresh usb and a freshly downloaded ubuntu from my friend's laptop, still not working. The Wifi connects but no internet access. This is 16.04 but a week ago even when I tried 14.04 i had the same issue. What should I do?

---

### Post by jeremy31 on 2016-06-25
Have you checked the router manufacturers website for firmware updates?  Something isn't quite right with it

---

### Post by levi10 on 2016-06-25
I asked my friend to open his mobile hotspot so I could connect my laptop. And it worked! It turns out it is the router's problem. 

But what do I do now? Two other people are using the same router without having such a problem. 

Thank you so much for your time and expertise!!

---

### Post by jeremy31 on 2016-06-25
> **levi10 said:**
> I asked my friend to open his mobile hotspot so I could connect my laptop. And it worked! It turns out it is the router's problem. 

But what do I do now? Two other people are using the same router without having such a problem. 

Thank you so much for your time and expertise!!

The people not having issues are likely not using Linux based OS and may have fixes for this router issue.  Most manufacturers only care if their routers work properly with windows- last time I checked that was 90+ % of computer users

---

