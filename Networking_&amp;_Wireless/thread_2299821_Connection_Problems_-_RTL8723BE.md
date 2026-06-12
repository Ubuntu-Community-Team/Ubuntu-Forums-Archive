---
title: "Connection Problems - RTL8723BE"
date: 2015-10-21
forum: Networking &amp; Wireless
---

### Post by Pawliko on 2015-10-21
Hello,
I have problem with my wifi connection. Internet is working  for some minutes, then slow down, slow down more more... and finaly it doesn't work. It will work only if i reconect.
I tried many guide, and solutions, but its not working for me.
Currently i don't know what am standing on. I changed many files, added some lines in some files...

Please keep in mind that am new user of linux :P

Please help me solve my problem :P

I add script output.
```


########## wireless info START ##########


Report from: 21 Oct 2015 19:50 CEST +0200


Booted last: 18 Oct 2015 21:14 CEST +0200


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid


##### kernel ############################


Linux 3.19.0-31-generic #36-Ubuntu SMP Wed Oct 7 15:04:02 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


GNOME Classic


##### lspci #############################


08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lenovo Device [17aa:b736]
    Kernel driver in use: rtl8723be


09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:380d]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 004 Device 002: ID 8087:8000 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8008 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 248a:8564  
Bus 001 Device 003: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 5986:055e Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
7: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no


##### lsmod #############################


rtl8723be             143360  0 
btcoexist             188416  1 rtl8723be
rtl_pci                40960  1 rtl8723be
rtlwifi               122880  3 btcoexist,rtl_pci,rtl8723be
mac80211              724992  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              540672  2 mac80211,rtlwifi
ideapad_laptop         20480  0 
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  0 


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


bond0     Link encap:Ethernet  HWaddr <MAC 'bond0' [IF]>  
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.16  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:329823 errors:0 dropped:0 overruns:0 frame:0
          TX packets:229519 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:447478213 (447.4 MB)  TX bytes:25726003 (25.7 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


bond0     no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"ADom"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: <MAC 'ADom' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:7   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    400    0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     400    0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search home


##### network managers ##################


Installed:


    NetworkManager


Running:


root       717     1  0 Oct18 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8723BE PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8723be
GENERAL.DRIVER-VERSION:                 3.19.0-31-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:08:00.0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     ADom
GENERAL.CON-UUID:                       9ea23868-eb65-4a9c-95a1-c7a3f4018b1c
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/7
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     72 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{6}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   9ea23868-eb65-4a9c-95a1-c7a3f4018b1c | ADom
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
IP4.ADDRESS[1]:                         ip = 192.168.1.16/24, gw = 192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.1 192.168.1.1
DHCP4.OPTION[5]:                        ip_address = 192.168.1.16
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.1.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = home
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1445536023
DHCP4.OPTION[21]:                       vendor_unknown_3561 = 4:6:63:38:39:31:46:39:5:f:4e:37:31:34:31:39:36:37:30:30:30:37:38:33:35:6:6:46:75:6e:62:6f:78
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 192.168.1.1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         ip = fe80::<IP6 'wlan0' [IF]>/64, gw = ::


GENERAL.DEVICE:                         bond0
GENERAL.TYPE:                           bond
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         bonding
GENERAL.DRIVER-VERSION:                 3.7.1
GENERAL.FIRMWARE-VERSION:               2
GENERAL.HWADDR:                         <MAC 'bond0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          70 (connecting (getting IP configuration))
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/bond0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     &#321;&#261;czone po&#322;&#261;czenie 1
GENERAL.CON-UUID:                       ba77acd7-6284-478b-95c5-1e72b8ac1372
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
BOND.SLAVES:                            
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{9}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   ba77acd7-6284-478b-95c5-1e72b8ac1372 | &#321;&#261;czone po&#322;&#261;czenie 1


GENERAL.DEVICE:                         <MAC address>
GENERAL.TYPE:                           bt
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         bluez
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /org/bluez/674/hci0/dev_D4_87_D8_88_88_88
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{15}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   1d60c983-880e-4203-91cf-9ad40628c480 | GT-I9100 Network


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
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:09:00.0/net/eth0
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


SSID  BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
ADom  <MAC 'ADom' [AC1]>  Infra  9     2452 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA2      yes     * 


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


sed: -e expression #1, char 287: Invalid preceding regular expression
[[/etc/NetworkManager/system-connections/sasasDom 1]] (600 root)
[connection] id=sasasDom 1 | type=802-11-wireless
[802-11-wireless] ssid=sasasDom | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/**Pasaz Grunwaldzki free WiFi**]] (600 root)


[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=802-11-wireless
[802-11-wireless] ssid=AndroidAP | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ADom]] (600 root)
[connection] id=ADom | type=wifi
[wifi] ssid=ADom | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/PWR-WiFi]] (600 root)
[connection] id=PWR-WiFi | type=wifi
[wifi] ssid=PWR-WiFi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Darmowe_Orange_WiFi]] (600 root)
[connection] id=Darmowe_Orange_WiFi | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=Darmowe_Orange_WiFi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[connection] id=eduroam | type=wifi | permissions=user:piotr:;
[wifi] ssid=eduroam
[ipv4] method=auto
[ipv6] method=auto
[802-1x] ca-cert=/home/piotr/.cat_installer/ca.pem


[[/etc/NetworkManager/system-connections/sasasDom]] (600 root)
[connection] id=sasasDom | type=wifi
[wifi] ssid=sasasDom | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/McD-Hotspot]] (600 root)
[connection] id=McD-Hotspot | type=wifi
[wifi] ssid=McD-Hotspot | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


##### iw reg get ########################


Region: Europe/Warsaw (based on set time zone)


country PL: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


eth0      no frequency information.


bond0     no frequency information.


lo        no frequency information.


wlan0     13 channels in total; available frequencies :
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
          Current Frequency:2.452 GHz (Channel 9)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


bond0     Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.452 GHz (Channel 9)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'ADom' [AC1]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"ADom"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003b7d47bde5
                    Extra: Last beacon: 108ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rtl8723be]
filename:       /lib/modules/3.19.0-31-generic/updates/dkms/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     1A35907BCCEF84FE28F988D
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
vermagic:       3.19.0-31-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)


[rtl_pci]
filename:       /lib/modules/3.19.0-31-generic/updates/dkms/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     50149A68C0A3A531EFD566D
depends:        mac80211,rtlwifi
vermagic:       3.19.0-31-generic SMP mod_unload modversions 


[rtlwifi]
filename:       /lib/modules/3.19.0-31-generic/updates/dkms/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     AA292FEB01DFF0A9680EAA5
depends:        mac80211,cfg80211
vermagic:       3.19.0-31-generic SMP mod_unload modversions 


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


[rtl8723be]
debug: 0
disable_watchdog: N
fwlps: N
ips: N
msi: N
swenc: Y
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
options iwlwifi 11n_disable=0


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1


[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be swenc=1 fwlps=0 ips=0


[/etc/modprobe.d/rtl8723.conf]
options rtl8723be fwlps=N ips=N


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (ath9k_htc)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
KERNEL=="wlan0", RUN+="/sbin/iwconfig wlan0 txpower 15"


##### dmesg #############################


[ 3117.412269] rtlwifi: wireless switch is on
[ 3117.428061] r8169 0000:09:00.0 eth0: link down
[ 3118.166421] btusb: Loaded firmware rtl_bt/rtl8723b_fw.bin
[ 3118.405963] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3118.419199] r8169 0000:09:00.0 eth0: link down
[ 3120.013777] wlan0: authenticate with <MAC 'ADom' [AC1]>
[ 3120.024947] wlan0: send auth to <MAC 'ADom' [AC1]> (try 1/3)
[ 3120.028254] wlan0: authenticated
[ 3120.030980] wlan0: associate with <MAC 'ADom' [AC1]> (try 1/3)
[ 3120.035610] wlan0: RX AssocResp from <MAC 'ADom' [AC1]> (capab=0x411 status=0 aid=5)
[ 3120.037586] wlan0: associated
[ 4688.471496] wlan0: deauthenticating from <MAC 'ADom' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 4693.762653] wlan0: authenticate with <MAC 'ADom' [AC1]>
[ 4693.773667] wlan0: send auth to <MAC 'ADom' [AC1]> (try 1/3)
[ 4693.779073] wlan0: authenticated
[ 4693.781733] wlan0: associate with <MAC 'ADom' [AC1]> (try 1/3)
[ 4693.787488] wlan0: RX AssocResp from <MAC 'ADom' [AC1]> (capab=0x411 status=0 aid=5)
[ 4693.788373] wlan0: associated


########## wireless info END ############



```

---

### Post by praseodym on 2015-10-21
Try these module parameters:

```
echo "options rtl8723be swenc=1 fwlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
Reboot.

---

### Post by Pawliko on 2015-10-22
I tried this:

```

  echo "options rtl8723be fwlps=0" | sudo tee /etc/modprobe.d/rtl8723be.conf

echo "options rtl8723be fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf

 echo "options rtl8723be swenc=1 fwlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
```

It didn't work. Same freezes/slow speed.

---

