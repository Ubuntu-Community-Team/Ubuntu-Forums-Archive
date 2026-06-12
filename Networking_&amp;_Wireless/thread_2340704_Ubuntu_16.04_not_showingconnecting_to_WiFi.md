---
title: "Ubuntu 16.04 not showing/connecting to WiFi"
date: 2016-10-21
forum: Networking &amp; Wireless
---

### Post by carlo8 on 2016-10-21
Hi everybody, I just installed Ubuntu 16.04 on my laptop, and the Wi-Fi is not working.

Specifically, the WiFi signal seems to be weak, since in Settings->Network all the Wi-Fi networks are indicated as "out of range" (my version is actually in italian, so I'm translating....) , but I have a dual boot and in Windows10 everything works perfectly.
I looked on the forum, and I saw that some people with my network adapter (RTL8723BE PCIe Wireless Network Adapter) had the same problem and were suggested to update the drivers...however, I thought it might be better to run the Wi-Fi-info script, and ask for your sugestion before doing anything 

```



########## wireless info START ##########


Report from: 21 Oct 2016 11:14 CEST +0200


Booted last: 21 Oct 2016 00:00 CEST +0200


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-45-generic #66-Ubuntu SMP Wed Oct 19 14:12:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:81ef]
	Kernel driver in use: r8169


03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	DeviceName: Sanji2 
	Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:81c1]


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b56c Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0bda:b008 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


rtl8723be              90112  0
btcoexist              53248  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
rtl_pci                28672  1 rtl8723be
rtlwifi                77824  2 rtl_pci,rtl8723be
mac80211              737280  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              565248  2 mac80211,rtlwifi
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
wmi                    20480  1 hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF1]>  
          inet addr:140.105.75.238  Bcast:140.105.75.255  Mask:255.255.252.0
          inet6 addr: fe80::cf30:e92b:6b70:11fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15427 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3932 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6556343 (6.5 MB)  TX bytes:572866 (572.8 KB)


wlo1      Link encap:Ethernet  HWaddr <MAC 'wlo1' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:38 (38.0 B)


##### iwconfig ##########################


enp2s0    no wireless extensions.


lo        no wireless extensions.


wlo1      IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         140.105.72.1    0.0.0.0         UG    100    0        0 enp2s0
140.105.72.0    0.0.0.0         255.255.252.0   U     100    0        0 enp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0


##### resolv.conf #######################


nameserver 127.0.1.1
search oats.inaf.it


##### network managers ##################


Installed:


	NetworkManager


Running:


root       786     1  0 10:47 ?        00:00:03 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.4/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Connessione via cavo 1
GENERAL.CON-UUID:                       5d8a1e93-771d-33c2-85f7-ff49b1612931
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{7}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   5d8a1e93-771d-33c2-85f7-ff49b1612931 | Connessione via cavo 1
IP4.ADDRESS[1]:                         140.105.75.238/22
IP4.GATEWAY:                            140.105.72.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             140.105.72.4
IP4.DNS[2]:                             140.105.72.174
IP4.DOMAIN[1]:                          oats.inaf.it
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        time_offset = -10800
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       expiry = 1477068994
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 140.105.72.1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 140.105.75.238
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       domain_name = oats.inaf.it
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       broadcast_address = 140.105.75.255
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       dhcp_lease_time = 21600
DHCP4.OPTION[24]:                       domain_name_servers = 140.105.72.4 140.105.72.174
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.252.0
DHCP4.OPTION[27]:                       network_number = 140.105.72.0
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 140.105.75.1
IP6.ADDRESS[1]:                         fe80::cf30:e92b:6b70:11fc/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8723BE PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8723be
GENERAL.DRIVER-VERSION:                 4.4.0-45-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlo1' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/net/wlo1
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    no
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
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Osservatorio]] (600 root)
[connection] id=Osservatorio | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=Osservatorio
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/NOKIA Lumia 625_6986 1]] (600 root)
[connection] id=NOKIA Lumia 625_6986 1 | type=wifi | permissions=user:carlo:;
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=NOKIA Lumia 625_6986
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/units]] (600 root)
[connection] id=units | type=wifi | permissions=user:carlo:;
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=units
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/NOKIA Lumia 625_6986]] (600 root)
[connection] id=NOKIA Lumia 625_6986 | type=wifi | permissions=user:ubuntu:;
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=NOKIA Lumia 625_6986
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/rtmcopisteria]] (600 root)
[connection] id=rtmcopisteria | type=wifi | permissions=user:carlo:;
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=rtmcopisteria
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[connection] id=eduroam | type=wifi | permissions=user:ubuntu:;
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=eduroam
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/eduroam-e29db71a-4471-4079-8dee-5d6bfc1811fa]] (600 root)
[connection] id=eduroam | type=wifi | permissions=user:carlo:;
[wifi] mac-address-blacklist= | ssid=eduroam
[802-1x] ca-cert=/home/carlo/.cat_installer/ca.pem
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Rome (based on set time zone)


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


enp2s0    no frequency information.


lo        no frequency information.


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


enp2s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlo1      No scan results


##### module infos ######################


[rtl8723be]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         PageHe	<page_he@realsil.com.cn>
srcversion:     3B2ECD9306CE299232BAE5D
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           ant_sel:Set to 1 or 2 to force antenna number (default 0)
 (int)


[rtl8723_common]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
srcversion:     AC6426E73F4CB059EE7332C
depends:        
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 


[rtl_pci]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     A96EBF28EBD4603749D5EC3
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 


[rtlwifi]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     632F2E9C01BF2AC04D0F40A
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.4.0-45-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F1176862D12ECD05A1066CF
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-45-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8723be]
ant_sel: 0
debug: 0
disable_watchdog: N
fwlps: Y
ips: Y
msi: N
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


[   10.777561] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[   10.812164] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   10.812325] rtlwifi: rtlwifi: wireless switch is on
[   10.840605] rtl8723be 0000:03:00.0 wlo1: renamed from wlan0
[   24.532871] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready (repeated 2 times)
[   25.120156] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   25.378578] r8169 0000:02:00.0 enp2s0: link down
[   25.378636] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   26.049086] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[  523.876937] wlo1: authenticate with <MAC address>
[  523.898190] wlo1: send auth to <MAC address> (try 1/3)
[  523.902173] wlo1: authenticated
[  523.906239] wlo1: associate with <MAC address> (try 1/3)
[  523.919179] wlo1: RX AssocResp from <MAC address> (capab=0xc31 status=0 aid=8)
[  523.919676] wlo1: associated
[  523.919684] IPv6: ADDRCONF(NETDEV_CHANGE): wlo1: link becomes ready
[  533.599313] wlo1: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)
[  546.353535] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready (repeated 2 times)
[  564.446527] r8169 0000:02:00.0 enp2s0: link up
[  564.446555] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready
[  874.283137] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready (repeated 2 times)


########## wireless info END ############



```

Thanks in advance!

---

### Post by jeremy31 on 2016-10-21
There is a chance that the HP has only one antenna and there is a module parameter that allows us to chose the antenna
```
sudo modprobe -r rtl8723be
```
```
sudo modprobe rtl8723be ant_sel=1
```

Now to see if there are any changes```
iwlist scan | egrep -i 'ssid|quality'
```

Then we can test the other option
```
sudo modprobe -r rtl8723be
```
```
sudo modprobe rtl8723be ant_sel=2
```

Now to see if there are any changes```
iwlist scan | egrep -i 'ssid|quality'
```

One setting or the other should make a difference, if ant_sel=1 worked better do
```
echo "options rtl8723be ant_sel=1" | sudo tee /etc/modprobe.d/rtlantsel.conf
```

If ant_sel=2 was better
```
echo "options rtl8723be ant_sel=2" | sudo tee /etc/modprobe.d/rtlantsel.conf
```

Then things should be automatic after a reboot

---

### Post by carlo8 on 2016-10-21
> **jeremy31 said:**
> There is a chance that the HP has only one antenna and there is a module parameter that allows us to chose the antenna
```
sudo modprobe -r rtl8723be
```
```
sudo modprobe rtl8723be ant_sel=1
```

[...]

One setting or the other should make a difference, if ant_sel=1 worked better do
```
echo "options rtl8723be ant_sel=1" | sudo tee /etc/modprobe.d/rtlantsel.conf
```

Then things should be automatic after a reboot

Thanks, it works perfectly now!!! ;)

---

