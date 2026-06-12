---
title: "Ubuntu 15.10 rtl8821AE"
date: 2015-10-25
forum: Networking &amp; Wireless
---

### Post by alex462 on 2015-10-25
I've upgraded Ubuntu from 15.04 to 15.10 and kernel changed from 3.19 to 4.2. WIFi card started to work much slower. Boot the old kernel and speed returned to previous levels.

wireless info 3.19
```

########## wireless info START ##########

Report from: 25 Oct 2015 23:23 YEKT +0500

Booted last: 25 Oct 2015 00:00 YEKT +0500

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 3.19.0-31-generic #36-Ubuntu SMP Wed Oct 7 15:04:02 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

sed: can't read /root/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

02:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8171 Gigabit Ethernet [1969:10a1] (rev 10)
    Subsystem: ASRock Incorporation Device [1849:10a1]
    Kernel driver in use: alx

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Kernel driver in use: rtl8821ae

##### lsusb #############################

Bus 004 Device 002: ID 8087:8001 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8009 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0451:8046 Texas Instruments, Inc. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 04d9:1603 Holtek Semiconductor, Inc. Keyboard
Bus 001 Device 005: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 001 Device 003: ID 0ac8:c40a Z-Star Microelectronics Corp. 
Bus 001 Device 007: ID 0bda:0821 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 413c:a503 Dell Computer Corp. 
Bus 001 Device 002: ID 0451:8044 Texas Instruments, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

rtl8821ae             229376  0
snd_soc_rt5640         94208  0
btcoexist              53248  1 rtl8821ae
rtl_pci                28672  1 rtl8821ae
snd_soc_rl6231         16384  1 snd_soc_rt5640
rtlwifi                77824  2 rtl_pci,rtl8821ae
mac80211              724992  3 rtl_pci,rtlwifi,rtl8821ae
snd_soc_core          196608  1 snd_soc_rt5640
snd_pcm               106496  8 snd_soc_rt5640,snd_usb_audio,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
cfg80211              540672  2 mac80211,rtlwifi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2a02:17d0:180:1300:cc14:2c70:dc32:dffe/64 Scope:Global
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          inet6 addr: 2a02:17d0:180:1300:<IP6 'wlan0' [IF]>/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:72940 errors:0 dropped:0 overruns:0 frame:0
          TX packets:341227 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6131050 (6.1 MB)  TX bytes:514443657 (514.4 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Keenetic-2391"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: <MAC 'Keenetic-2391' [AC1]>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:35   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       821     1  0 22:23 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8821AE 802.11ac PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8821ae
GENERAL.DRIVER-VERSION:                 3.19.0-31-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.7/0000:03:00.0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Keenetic-2391
GENERAL.CON-UUID:                       58ac8ed2-3772-4c1f-ad09-030a4e759c91
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   58ac8ed2-3772-4c1f-ad09-030a4e759c91 | Keenetic-2391
IP4.ADDRESS[1]:                         192.168.1.110/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_host_name = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[7]:                        requested_domain_name = 1
DHCP4.OPTION[8]:                        expiry = 1445819034
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.1.1
DHCP4.OPTION[15]:                       dhcp_lease_time = 25200
DHCP4.OPTION[16]:                       ip_address = 192.168.1.110
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[21]:                       requested_netbios_scope = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_routers = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       wpad = a
DHCP4.OPTION[26]:                       requested_ntp_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         2a02:17d0:180:1300:<IP6 'wlan0' [IF]>/64
IP6.ADDRESS[2]:                         2a02:17d0:180:1300:cc14:2c70:dc32:dffe/64
IP6.ADDRESS[3]:                         fe80::<IP6 'wlan0' [IF]>/64
IP6.GATEWAY:                            fe80::ee43:f6ff:feda:94f0

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA8171 Gigabit Ethernet
GENERAL.DRIVER:                         alx
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/eth0
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

SSID                        BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Sky_wi-fi                   <MAC 'Sky_wi-fi' [AN1]>  Infra  9     2452 MHz  54 Mbit/s  77      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
Keenetic-2391               <MAC 'Keenetic-2391' [AC1]>  Infra  4     2427 MHz  54 Mbit/s  72      &#9602;&#9604;&#9606;_  WPA2       yes     * 
WiFi-DOM.ru-5862            <MAC 'WiFi-DOM.ru-5862' [AN3]>  Infra  1     2412 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA1 WPA2  no        
WiFi-DOM.ru-2876            <MAC 'WiFi-DOM.ru-2876' [AN4]>  Infra  1     2412 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
ZyXEL_KEENETIC_GIGA_DA30E8  <MAC 'ZyXEL_KEENETIC_GIGA_DA30E8' [AN5]>  Infra  10    2457 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA2       no        
TP-LINK_E6E57A              <MAC 'TP-LINK_E6E57A' [AC2]>  Infra  6     2437 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA2       no        

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

[[/etc/NetworkManager/system-connections/Keenetic-2391]] (600 root)
[connection] id=Keenetic-2391 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF]> | mac-address-blacklist= | ssid=Keenetic-2391
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: Asia/Yekaterinburg (based on set time zone)

country RU: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5650 - 5730 @ 80), (N/A, 30), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     24 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.427 GHz (Channel 4)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.427 GHz (Channel 4)
      1   APs on   Frequency:2.437 GHz (Channel 6)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Keenetic-2391' [AC1]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"Keenetic-2391"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000412ef84dc
                    Extra: Last beacon: 120ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'TP-LINK_E6E57A' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_E6E57A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000f7771d0f180
                    Extra: Last beacon: 5812ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8821ae]
filename:       /lib/modules/3.19.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     D84AE72B78115D804B29DF2
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.19.0-31-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B4:BA:13:D5:CE:C9:3E:1A:F4:B3:4D:36:DA:1B:D4:FC:FF:A5:44:10
sig_hashalgo:   sha512
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
filename:       /lib/modules/3.19.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     A25DC6D8C53D55DA133BC49
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.19.0-31-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B4:BA:13:D5:CE:C9:3E:1A:F4:B3:4D:36:DA:1B:D4:FC:FF:A5:44:10
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.19.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     35016235A31CEB1854418E1
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-31-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B4:BA:13:D5:CE:C9:3E:1A:F4:B3:4D:36:DA:1B:D4:FC:FF:A5:44:10
sig_hashalgo:   sha512

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

[rtl8821ae]
debug: 0
disable_watchdog: N
fwlps: Y
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

[/etc/modprobe.d/vmware-fuse.conf]
alias char-major-10-229 fuse

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x10a1 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8821 (rtl8821ae)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   28.563945] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   28.839331] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[   28.945987] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.664423] wlan0: authenticate with <MAC 'Keenetic-2391' [AC1]>
[   30.664765] wlan0: send auth to <MAC 'Keenetic-2391' [AC1]> (try 1/3)
[   30.666245] wlan0: authenticated
[   30.669717] wlan0: associate with <MAC 'Keenetic-2391' [AC1]> (try 1/3)
[   30.673303] wlan0: RX AssocResp from <MAC 'Keenetic-2391' [AC1]> (capab=0x411 status=0 aid=1)
[   30.673464] wlan0: associated
[   30.673482] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############


```
wireless info 4.2
```

########## wireless info START ##########

Report from: 25 Oct 2015 23:33 YEKT +0500

Booted last: 25 Oct 2015 00:00 YEKT +0500

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-17-generic #20-Ubuntu SMP Thu Oct 22 16:48:33 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

sed: can't read /root/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

02:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8171 Gigabit Ethernet [1969:10a1] (rev 10)
    Subsystem: ASRock Incorporation Device [1849:10a1]
    Kernel driver in use: alx

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Kernel driver in use: rtl8821ae

##### lsusb #############################

Bus 004 Device 002: ID 8087:8001 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8009 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0451:8046 Texas Instruments, Inc. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 04d9:1603 Holtek Semiconductor, Inc. Keyboard
Bus 001 Device 005: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 001 Device 003: ID 0ac8:c40a Z-Star Microelectronics Corp. 
Bus 001 Device 007: ID 0bda:0821 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 413c:a503 Dell Computer Corp. 
Bus 001 Device 002: ID 0451:8044 Texas Instruments, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

rtl8821ae             225280  0
btcoexist              53248  1 rtl8821ae
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
rtl_pci                28672  1 rtl8821ae
rtlwifi                77824  2 rtl_pci,rtl8821ae
snd_soc_core          196608  1 snd_soc_rt5640
mac80211              733184  3 rtl_pci,rtlwifi,rtl8821ae
cfg80211              548864  2 mac80211,rtlwifi
snd_pcm               102400  8 snd_soc_rt5640,snd_usb_audio,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          inet6 addr: 2a02:17d0:180:1300:<IP6 'wlan0' [IF]>/64 Scope:Global
          inet6 addr: 2a02:17d0:180:1300:d855:ae5b:2786:5bc0/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:769 errors:0 dropped:0 overruns:0 frame:0
          TX packets:760 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:509312 (509.3 KB)  TX bytes:170595 (170.5 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Keenetic-2391"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: <MAC 'Keenetic-2391' [AC1]>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:61   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       839     1  0 23:27 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8821AE 802.11ac PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8821ae
GENERAL.DRIVER-VERSION:                 4.2.0-17-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.7/0000:03:00.0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Keenetic-2391
GENERAL.CON-UUID:                       58ac8ed2-3772-4c1f-ad09-030a4e759c91
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   58ac8ed2-3772-4c1f-ad09-030a4e759c91 | Keenetic-2391
IP4.ADDRESS[1]:                         192.168.1.110/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_host_name = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[7]:                        requested_domain_name = 1
DHCP4.OPTION[8]:                        expiry = 1445822886
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.1.1
DHCP4.OPTION[15]:                       dhcp_lease_time = 25200
DHCP4.OPTION[16]:                       ip_address = 192.168.1.110
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[21]:                       requested_netbios_scope = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_routers = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       wpad = a
DHCP4.OPTION[26]:                       requested_ntp_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         2a02:17d0:180:1300:<IP6 'wlan0' [IF]>/64
IP6.ADDRESS[2]:                         2a02:17d0:180:1300:d855:ae5b:2786:5bc0/64
IP6.ADDRESS[3]:                         fe80::<IP6 'wlan0' [IF]>/64
IP6.GATEWAY:                            fe80::ee43:f6ff:feda:94f0

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA8171 Gigabit Ethernet
GENERAL.DRIVER:                         alx
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/eth0
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

SSID              BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Sky_wi-fi         <MAC 'Sky_wi-fi' [AC3]>  Infra  9     2452 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
WiFi-DOM.ru-2876  <MAC 'WiFi-DOM.ru-2876' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
Keenetic-2391     <MAC 'Keenetic-2391' [AC1]>  Infra  4     2427 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA2       yes     * 

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

[[/etc/NetworkManager/system-connections/Keenetic-2391]] (600 root)
[connection] id=Keenetic-2391 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF]> | mac-address-blacklist= | ssid=Keenetic-2391
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: Asia/Yekaterinburg (based on set time zone)

country RU: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5650 - 5730 @ 80), (N/A, 30), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     29 channels in total; available frequencies :
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
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.427 GHz (Channel 4)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:2.467 GHz (Channel 12)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Keenetic-2391' [AC1]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"Keenetic-2391"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000004364d1584
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'WiFi-DOM.ru-2876' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"WiFi-DOM.ru-2876"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000041ae6a0a17e
                    Extra: Last beacon: 9608ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Sky_wi-fi' [AC3]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"Sky_wi-fi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000531ab92f40
                    Extra: Last beacon: 4ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'dlink' [AC4]>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c0f3ad3cc
                    Extra: Last beacon: 4ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8821ae]
filename:       /lib/modules/4.2.0-17-generic/kernel/drivers/net/wireless/rtlwifi/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     8E244B0EA08706E70EB5229
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       4.2.0-17-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        49:46:9E:A5:7A:E3:46:A8:12:CB:06:97:A5:0D:77:F7:ED:75:7F:F9
sig_hashalgo:   sha512
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
filename:       /lib/modules/4.2.0-17-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8B217E7604F811302F8D171
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.2.0-17-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        49:46:9E:A5:7A:E3:46:A8:12:CB:06:97:A5:0D:77:F7:ED:75:7F:F9
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/4.2.0-17-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     335152C55308EE5515FB05B
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-17-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        49:46:9E:A5:7A:E3:46:A8:12:CB:06:97:A5:0D:77:F7:ED:75:7F:F9
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
sig_key:        49:46:9E:A5:7A:E3:46:A8:12:CB:06:97:A5:0D:77:F7:ED:75:7F:F9
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
sig_key:        49:46:9E:A5:7A:E3:46:A8:12:CB:06:97:A5:0D:77:F7:ED:75:7F:F9
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8821ae]
debug: 0
disable_watchdog: N
fwlps: Y
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

[/etc/modprobe.d/vmware-fuse.conf]
alias char-major-10-229 fuse

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x10a1 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8821 (rtl8821ae)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   12.494585] rtl8821ae 0000:03:00.0: enabling device (0000 -> 0003)
[   12.507627] rtl8821ae: Using firmware rtlwifi/rtl8821aefw.bin
[   12.507630] rtl8821ae: Using firmware rtlwifi/rtl8821aefw_wowlan.bin
[   12.556138] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   12.556279] rtlwifi: rtlwifi: wireless switch is on
[   13.924578] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000a lmp_ver=06 lmp_subver=8821
[   13.924580] Bluetooth: hci0: rtl: loading rtl_bt/rtl8821a_fw.bin
[   26.325794] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   26.552279] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[   26.759576] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.749339] wlan0: authenticate with <MAC 'Keenetic-2391' [AC1]>
[   29.749666] wlan0: send auth to <MAC 'Keenetic-2391' [AC1]> (try 1/3)
[   29.751357] wlan0: authenticated
[   29.755076] wlan0: associate with <MAC 'Keenetic-2391' [AC1]> (try 1/3)
[   29.758799] wlan0: RX AssocResp from <MAC 'Keenetic-2391' [AC1]> (capab=0x411 status=0 aid=1)
[   29.762916] wlan0: associated
[   29.762924] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############


```

---

### Post by Retro_Trinity on 2015-10-27
Have you had any luck diagnosing your problem under kernel 4.2 yet? There is a dearth of information regarding problems related to the rtl8821ae driver.  Others are having similar or worse problems with the same driver.  Maybe if we work together, we can find some kind of a solution? Those of us with the rtl8812ae chipset (uses same driver) saw a complete loss of functionality migrating to 15.10 which is rather upsetting.

---

### Post by johna3 on 2016-02-10
[COLOR=#111111][FONT=Ubuntu]Not sure if this is the same problem I had/have but on 15.10 on my asus laptop, the wifi did not work out of the box. 
 I tried a variety of things. This is what finally "worked" for me: 

[/FONT][/COLOR]
[LIST]
[*][COLOR=#111111][FONT=Ubuntu]created a file /etc/modprobe.d/rtl8821ae.conf - after much trial and error added msi=0 to that file[/FONT][/COLOR]
[/LIST]
[INDENT]$ pwd
/etc/modprobe.d
$ ls rtl8821.conf
rtl8821.conf
$ cat rtl8821.conf
options rtl8821ae  debug=0 disable_watchdog=N fwlps=N swlps=Y swenc=Y ips=N msi=0[/INDENT]

[LIST]
[*]I have not tried all of the other combinations of disable_watchdog/fwlps/swlps/swenc/ips so I don't know if there is a better set of parameters to set
[*]This works ok on 2.4G. It does not work in 5G, the drop-outs are too severe for it to be useful.
[*]on 2.4G, speedtest.net says I'm getting 24Mbs, other laptops and my phone are getting 100+Mbs, so there is still something wrong with the settings... but it's usable at least
[*]the msi=0 was from this site [https://github.com/lwfinger/rtlwifi_new/issues/64](https://github.com/lwfinger/rtlwifi_new/issues/64)
[/LIST]

Update: after a suspend (laptop closed) and a resume, it hung again. I tried shutting down Network and/or Wifi and restarting, that helped but there were still a lot of glitches.
It affected music playback (MP3s "skip"), mouse movement are jerky and laggy.


Update: Clicked on "Pre-released updates (wily proposed)" Software Updater tool.
and then updated to latest packages, latest kernel, latest everything
```

$ uname -a
Linux xxx 4.2.0-29-generic #34-Ubuntu SMP Mon Feb 8 16:57:47 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```

Things got faster.
at least so far, I haven't seen any dropouts for 30 minutes. Usually I was getting one every few minutes.
But only on 2.4Ghz. Tried it on 5Ghz and it just wouldn't connect to my router.

FInal result is that the speed test almost doubled (note it is normally 100+Mb/s on my phone and other laptops)

[[IMG]http://www.speedtest.net/result/5101034386.png[/IMG]]("http://www.speedtest.net/my-result/5101034386")

---

### Post by simonn on 2016-05-27
Late to the party (I came across this trying to find out why my laptop wifi is ~ 20Mb/s on ubuntu vs 40Mb/s under Win10).

See my  post [http://ubuntuforums.org/showthread.php?t=1543006&page=42&p=13493037#post13493037](http://ubuntuforums.org/showthread.php?t=1543006&page=42&p=13493037#post13493037). Sections "802.11AC wireless (rtl8821ae) fails (this has happened every kernel upgrade)" and "Wifi fails after suspend/sleep".

Note, with the latter, I keep meaning to add a sleep 5 before removing the kernel module as the script does not work 100% of the time, you sometimes have to do a sudo rmmod rtl8821ae then sudo modprobe rtl8821ae manually, but I have yet to test it.

```

#!/bin/sh
case "$1" in
  suspend|hibernate)
 	/sbin/rmmod rtl8821ae
  ;;
  resume|thaw)
	sleep 5
	/sbin/rmmod rtl8821ae
	sleep 5 
	/sbin/modprobe rtl8821ae
  ;;
esac

exit 0

```

---

