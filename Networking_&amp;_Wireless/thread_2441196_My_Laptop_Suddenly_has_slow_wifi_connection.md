---
title: "My Laptop Suddenly has slow wifi connection"
date: 2020-04-20
forum: Networking &amp; Wireless
---

### Post by borpot on 2020-04-20
Hi, This is my first time posting a thread here please be good to me.

Unfortunately, my Ubuntu OS has a much slower connection compared to my Windows OS with 2.4ghz connection.
I've tried several solutions that I've encountered on the internet, some of them had solved the problem but after rebooting the computer
the problem came back. Below is the wireless information on my laptop, please help, Thanks!

> 

########## wireless info START ##########


Report from: 21 Apr 2020 00:07 PST +0800


Booted last: 21 Apr 2020 00:00 PST +0800


Script from: 22 Oct 2018 03:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.6 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.15.0-96-generic #97~16.04.1-Ubuntu SMP Wed Apr 1 03:03:31 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:388a]
    Kernel driver in use: r8169


03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: Lenovo RTL8821AE 802.11ac PCIe Wireless Network Adapter [17aa:a814]
    Kernel driver in use: rtl8821ae


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:58ea Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0bda:0821 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 06cb:0081 Synaptics, Inc. 
Bus 001 Device 002: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### secure boot #######################


SecureBoot disabled


##### lsmod #############################


rtl8821ae             233472  0
btcoexist             172032  1 rtl8821ae
rtl_pci                32768  1 rtl8821ae
rtlwifi                98304  3 rtl_pci,rtl8821ae,btcoexist
mac80211              786432  3 rtl_pci,rtl8821ae,rtlwifi
intel_wmi_thunderbolt    16384  0
wmi_bmof               16384  0
cfg80211              634880  2 rtlwifi,mac80211
ideapad_laptop         20480  0
sparse_keymap          16384  1 ideapad_laptop
mxm_wmi                16384  1 nouveau
wmi                    24576  5 intel_wmi_thunderbolt,wmi_bmof,ideapad_laptop,mxm_wmi,nouveau
video                  45056  3 ideapad_laptop,i915,nouveau


##### interfaces ########################


[/etc/network/interfaces]
auto lo
iface lo inet loopback


##### ifconfig ##########################


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: enp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether <MAC 'enp2s0' [IF1]> brd <MAC address>
3: wlp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether <MAC 'wlp3s0' [IF2]> brd <MAC address>
    inet 192.168.1.2/24 brd 192.168.1.255 scope global dynamic wlp3s0
       valid_lft 85427sec preferred_lft 85427sec


##### iwconfig ##########################


enp2s0    no wireless extensions.


lo        no wireless extensions.


wlp3s0    IEEE 802.11  ESSID:"BULAYBULAY_2.4G"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: <MAC 'BULAYBULAY_2.4G' [AC1]>   
          Bit Rate=150 Mb/s   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:323   Missed beacon:0


##### route #############################


default via 192.168.1.1 dev wlp3s0  proto static  metric 600 
169.254.0.0/16 dev wlp3s0  scope link  metric 1000 
192.168.1.0/24 dev wlp3s0  proto kernel  scope link  src 192.168.1.2  metric 600 


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '../run/resolvconf/resolv.conf']
nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       963     1  0 Apr20 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8821AE 802.11ac PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8821ae
GENERAL.DRIVER-VERSION:                 4.15.0-96-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       wlp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     BULAYBULAY_2.4G
GENERAL.CON-UUID:                       16b9f819-b1c8-48cb-bf33-79c426d02a2d
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     150 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0,1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   4dce0884-7121-4b2d-b5ba-d636529c0602 | BULAYBULAY_5G
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   16b9f819-b1c8-48cb-bf33-79c426d02a2d | BULAYBULAY_2.4G
IP4.ADDRESS[1]:                         192.168.1.2/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1587484284
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.2
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.1.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.1.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.1.1


GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.4/0000:02:00.0/net/enp2s0
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


SSID             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
BULAYBULAY_2.4G  <MAC 'BULAYBULAY_2.4G' [AC1]>  Infra  4     2427 MHz  54 Mbit/s  72      &#9602;&#9604;&#9606;_  WPA2      yes     * 
BULAYBULAY_5G    <MAC 'BULAYBULAY_5G' [AN2]>  Infra  36    5180 MHz  54 Mbit/s  27      &#9602;___  WPA2      no        


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager config #############


[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 2


[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq
[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/NCoV]] (600 root)
[connection] id=NCoV | type=wifi | permissions=user:moymoy:;
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=NCoV
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/BULAYBULAY_2.4G]] (600 root)
[connection] id=BULAYBULAY_2.4G | type=wifi | permissions=user:moymoy:;
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=BULAYBULAY_2.4G
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/BULAYBULAY_5G]] (600 root)
[connection] id=BULAYBULAY_5G | type=wifi | permissions=user:moymoy:;
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=BULAYBULAY_5G
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/OGIS_MANOK_2.4G]] (600 root)
[connection] id=OGIS_MANOK_2.4G | type=wifi | permissions=user:moymoy:;
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=OGIS_MANOK_2.4G
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HQ]] (600 root)
[connection] id=HQ | type=wifi | permissions=user:moymoy:;
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=HQ
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/CABZaprtWIFI_1]] (600 root)
[connection] id=CABZaprtWIFI_1 | type=wifi | permissions=user:moymoy:;
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=CABZaprtWIFI_1
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/CABZapartmentWIFI]] (600 root)
[connection] id=CABZapartmentWIFI | type=wifi | permissions=user:moymoy:;
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=CABZapartmentWIFI
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/SOUNDWAVE]] (600 root)
[connection] id=SOUNDWAVE | type=wifi | permissions=user:moymoy:;
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=SOUNDWAVE
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/my.IIT]] (600 root)
[connection] id=my.IIT | type=wifi | permissions=user:moymoy:;
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=my.IIT
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/OGIS_MANOK_5G]] (600 root)
[connection] id=OGIS_MANOK_5G | type=wifi | permissions=user:moymoy:;
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=OGIS_MANOK_5G
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Linksys01716]] (600 root)
[connection] id=Linksys01716 | type=wifi | permissions=user:moymoy:;
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=Linksys01716
[ipv4] method=auto
[ipv6] method=auto


##### Netplan config ####################


##### iw reg get ########################


Region: Asia/Manila (based on set time zone)


country PH: DFS-FCC
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A)
    (5250 - 5330 @ 80), (N/A, 24), (0 ms), DFS
    (5490 - 5730 @ 160), (N/A, 24), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)


##### iwlist channels ###################


enp2s0    no frequency information.


lo        no frequency information.


wlp3s0    32 channels in total; available frequencies :
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
          Current Frequency:2.427 GHz (Channel 4)


##### iwlist scan #######################


enp2s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.427 GHz (Channel 4)


wlp3s0    Scan completed :
          Cell 01 - Address: <MAC 'BULAYBULAY_2.4G' [AC1]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"BULAYBULAY_2.4G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001328877544
                    Extra: Last beacon: 136ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rtl8821ae]
filename:       /lib/modules/4.15.0-96-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw_29.bin
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     1F4F5BD5D1F911A750255CF
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
retpoline:      Y
name:           rtl8821ae
vermagic:       4.15.0-96-generic SMP mod_unload 
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
parm:           int_clear:Set to 0 to disable interrupt clear before set (default 1)
 (bool)


[rtl_pci]
filename:       /lib/modules/4.15.0-96-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     901E81899DD2E40E9859DDC
depends:        mac80211,rtlwifi
retpoline:      Y
name:           rtl_pci
vermagic:       4.15.0-96-generic SMP mod_unload 


[rtlwifi]
filename:       /lib/modules/4.15.0-96-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8314A91F15FE35C9525C5B5
depends:        mac80211,cfg80211
retpoline:      Y
name:           rtlwifi
vermagic:       4.15.0-96-generic SMP mod_unload 


[mac80211]
filename:       /lib/modules/4.15.0-96-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     E91E6F217E202F31AADED53
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-96-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.15.0-96-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E59180B39A14C88983A9687
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-96-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8821ae]
debug: 0
disable_watchdog: N
fwlps: Y
int_clear: Y
ips: Y
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
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode


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


[/etc/modprobe.d/libopenni-sensor-pointclouds0.conf]
blacklist gspca_kinect


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[    3.886749] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000a lmp_ver=06 lmp_subver=8821
[    3.886751] Bluetooth: hci0: rtl: loading rtl_bt/rtl8821a_config.bin
[    3.922757] bluetooth hci0: Direct firmware load for rtl_bt/rtl8821a_config.bin failed with error -2
[    3.922782] Bluetooth: hci0: rtl: loading rtl_bt/rtl8821a_fw.bin
[    4.098012] rtlwifi: loading out-of-tree module taints kernel.
[    4.107362] rtlwifi: module verification failed: signature and/or required key missing - tainting kernel
[    4.128901] rtl8821ae: Using firmware rtlwifi/rtl8821aefw_29.bin
[    4.128904] rtl8821ae: Using firmware rtlwifi/rtl8821aefw_wowlan.bin
[    4.141824] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    4.142041] rtlwifi: rtlwifi: wireless switch is on
[    4.167862] rtl8821ae 0000:03:00.0 wlp3s0: renamed from wlan0
[    8.397499] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[    8.689001] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    8.745929] r8169 0000:02:00.0 enp2s0: link down
[    8.745993] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    8.853964] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   71.620039] wlp3s0: authenticate with <MAC 'BULAYBULAY_2.4G' [AC1]>
[   71.620580] wlp3s0: send auth to <MAC 'BULAYBULAY_2.4G' [AC1]> (try 1/3)
[   71.622092] wlp3s0: authenticated
[   71.623645] wlp3s0: associate with <MAC 'BULAYBULAY_2.4G' [AC1]> (try 1/3)
[   71.627284] wlp3s0: RX AssocResp from <MAC 'BULAYBULAY_2.4G' [AC1]> (capab=0x1431 status=0 aid=75)
[   71.627980] wlp3s0: associated
[   71.665138] wlp3s0: Limiting TX power to 16 (16 - 0) dBm as advertised by <MAC 'BULAYBULAY_2.4G' [AC1]>
[   71.665439] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready


########## wireless info END ############




---

