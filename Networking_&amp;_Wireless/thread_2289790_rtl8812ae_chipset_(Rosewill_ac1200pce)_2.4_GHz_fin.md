---
title: "rtl8812ae chipset (Rosewill ac1200pce): 2.4 GHz fine, 5 GHz times out?"
date: 2015-08-07
forum: Networking &amp; Wireless
---

### Post by Retro_Trinity on 2015-08-07
There seems to be a problem with the rtl8812ae similar to the one in this link:

[http://askubuntu.com/questions/613136/rtl8812ae-cannot-connect-to-5ghz-networks](http://askubuntu.com/questions/613136/rtl8812ae-cannot-connect-to-5ghz-networks)

No command-line confirmation of connection timeouts, but it takes a looooong time for the connection attempt to fail, so it's possible that may be the case.  

802.11n functionality is excellent with this nic. It gives a solid 300 mbps. Ac speeds would be better.  The adapter is good for 650 mbps in Windows 10 when connected in 5 GHz mode, and it is stable and reliable.

This is under Lubuntu 15.04 64-bit.  If you would like any more information, please ask.

---

### Post by Retro_Trinity on 2015-08-07
Nothing? Here's my wireless info:

```

########## wireless info START ##########

Report from: 04 Aug 2015 16:12 EDT -0400

Booted last: 04 Aug 2015 11:36 EDT -0400

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 3.19.0-25-generic #26-Ubuntu SMP Fri Jul 24 21:17:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

Lubuntu

##### lspci #############################

04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8812AE 802.11ac PCIe Wireless Network Adapter [10ec:8812] (rev 01)
    Subsystem: Qualcomm Atheros Device [168c:6108]
    Kernel driver in use: rtl8821ae

##### lsusb #############################

Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8821ae             229376  0 
eeepc_wmi              16384  0 
asus_wmi               24576  1 eeepc_wmi
btcoexist              53248  1 rtl8821ae
sparse_keymap          16384  1 asus_wmi
rtl_pci                28672  1 rtl8821ae
rtlwifi                77824  2 rtl_pci,rtl8821ae
mac80211              724992  3 rtl_pci,rtlwifi,rtl8821ae
cfg80211              540672  2 mac80211,rtlwifi
video                  20480  1 asus_wmi
wmi                    20480  1 asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF]>  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34663 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21559055 (21.5 MB)  TX bytes:7802447 (7.8 MB)

##### iwconfig ##########################

lo        no wireless extensions.

wlan1     IEEE 802.11abgn  ESSID:"ReallySlowRouter"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'ReallySlowRouter' [AC1]>   
          Bit Rate=300 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:31   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    1024   0        0 wlan1
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 wlan1

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       755     1  0 15:36 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlan1
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8812AE 802.11ac PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8821ae
GENERAL.DRIVER-VERSION:                 3.19.0-25-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan1' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:15.3/0000:04:00.0/net/wlan1
GENERAL.IP-IFACE:                       wlan1
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     ReallySlowRouter 1
GENERAL.CON-UUID:                       8902cd12-4dc4-4abb-be89-cdd6fbe84f22
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/8
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     300 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   8902cd12-4dc4-4abb-be89-cdd6fbe84f22 | ReallySlowRouter 1
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
IP4.ADDRESS[1]:                         ip = 10.0.0.2/24, gw = 10.0.0.1
IP4.DNS[1]:                             10.0.0.1
DHCP4.OPTION[1]:                        requested_ntp_servers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_broadcast_address = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_time_offset = 1
DHCP4.OPTION[7]:                        expiry = 1438805368
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       requested_netbios_scope = 1
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       ip_address = 10.0.0.2
DHCP4.OPTION[15]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       routers = 10.0.0.1
DHCP4.OPTION[18]:                       broadcast_address = 10.0.0.255
DHCP4.OPTION[19]:                       domain_name_servers = 10.0.0.1
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_routers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       dhcp_message_type = 5
DHCP4.OPTION[25]:                       requested_host_name = 1
DHCP4.OPTION[26]:                       network_number = 10.0.0.0
DHCP4.OPTION[27]:                       dhcp_server_identifier = 10.0.0.1
IP6.ADDRESS[1]:                         ip = fe80::<IP6 'wlan1' [IF]>/64, gw = ::

SSID              BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
Steelman          <MAC 'Steelman' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  27      &#9602;___  WPA2      no        
ReallySlowRouter  <MAC 'ReallySlowRouter' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  WPA2      yes     * 

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

[[/etc/NetworkManager/system-connections/linksys]] (600 root)
[connection] id=linksys | type=802-11-wireless
[802-11-wireless] ssid=linksys | bssid=<MAC address> | mac-address=00:E0:4C:06:2F:03
[ipv4] method=manual
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ReallySlowRouter]] (600 root)
[connection] id=ReallySlowRouter | type=802-11-wireless
[802-11-wireless] ssid=ReallySlowRouter | mac-address=<MAC address>
[ipv4] method=manual
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ReallySlowRouter-5G]] (600 root)
[connection] id=ReallySlowRouter-5G | type=wifi
[wifi] ssid=ReallySlowRouter-5G | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ReallySlowRouter 1]] (600 root)
[connection] id=ReallySlowRouter 1 | type=wifi
[wifi] ssid=ReallySlowRouter | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20), (N/A)
    (2457 - 2482 @ 40), (3, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (3, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), (N/A), NO-IR
    (5735 - 5835 @ 40), (3, 20), (N/A), NO-IR

##### iwlist channels ###################

lo        no frequency information.

wlan1     24 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.457 GHz (Channel 10)

wlan1     Scan completed :
          Cell 01 - Address: <MAC 'ReallySlowRouter' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"ReallySlowRouter"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000c9b98fa8
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'ZyXEL' [AC2]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"ZyXEL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004b2490a6fb
                    Extra: Last beacon: 4ms ago
          Cell 03 - Address: <MAC 'Steelman' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Steelman"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000078307cd180
                    Extra: Last beacon: 3272ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8821ae]
filename:       /lib/modules/3.19.0-25-generic/kernel/drivers/net/wireless/rtlwifi/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     9200E1F9DEA4D2D3C81C455
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        89:7A:AD:75:7D:0E:4D:72:CD:84:24:0B:25:AC:78:28:85:BF:AE:3F
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
filename:       /lib/modules/3.19.0-25-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     A25DC6D8C53D55DA133BC49
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        89:7A:AD:75:7D:0E:4D:72:CD:84:24:0B:25:AC:78:28:85:BF:AE:3F
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.19.0-25-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     35016235A31CEB1854418E1
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        89:7A:AD:75:7D:0E:4D:72:CD:84:24:0B:25:AC:78:28:85:BF:AE:3F
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.19.0-25-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B23264F074A7D27F8B691A2
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        89:7A:AD:75:7D:0E:4D:72:CD:84:24:0B:25:AC:78:28:85:BF:AE:3F
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-25-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E61EB836E1B33C2A2918485
depends:        
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        89:7A:AD:75:7D:0E:4D:72:CD:84:24:0B:25:AC:78:28:85:BF:AE:3F
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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

sudo ifconfig wlan0 down
sudo iw reg set BO
sudo iwconfig wlan0 txpower 20
sudo iwconfig wlan0 frag 512
sudo iwconfig wlan0 rts 512
sudo iwconfig wlan0 retry short 31
sudo iwconfig wlan0 retry long 31
sudo ifconfig wlan0 up
sudo iwconfig wlan0 rate 36M auto

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (rtl8187)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[  554.124503] wlan1: direct probe to <MAC address> (try 1/3)
[  554.327026] wlan1: direct probe to <MAC address> (try 2/3)
[  554.530922] wlan1: direct probe to <MAC address> (try 3/3)
[  554.734816] wlan1: authentication with <MAC address> timed out
[  564.346306] wlan1: authenticate with <MAC address>
[  564.347176] wlan1: direct probe to <MAC address> (try 1/3)
[  564.549685] wlan1: direct probe to <MAC address> (try 2/3)
[  564.753536] wlan1: direct probe to <MAC address> (try 3/3)
[  564.957476] wlan1: authentication with <MAC address> timed out
[  567.772513] wlan1: authenticate with <MAC 'ReallySlowRouter' [AC1]>
[  567.773439] wlan1: send auth to <MAC 'ReallySlowRouter' [AC1]> (try 1/3)
[  567.775707] wlan1: authenticated
[  567.779962] wlan1: associate with <MAC 'ReallySlowRouter' [AC1]> (try 1/3)
[  567.783700] wlan1: RX AssocResp from <MAC 'ReallySlowRouter' [AC1]> (capab=0x1411 status=0 aid=2)
[  567.786612] wlan1: associated
[  567.799358] wlan1: deauthenticating from <MAC 'ReallySlowRouter' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[  567.801647] wlan1: authenticate with <MAC 'ReallySlowRouter' [AC1]>
[  567.802364] wlan1: send auth to <MAC 'ReallySlowRouter' [AC1]> (try 1/3)
[  567.803930] wlan1: authenticated
[  567.807906] wlan1: associate with <MAC 'ReallySlowRouter' [AC1]> (try 1/3)
[  567.811700] wlan1: RX AssocResp from <MAC 'ReallySlowRouter' [AC1]> (capab=0x1411 status=0 aid=2)
[  567.818649] wlan1: associated
[  674.876781] wlan1: deauthenticating from <MAC 'ReallySlowRouter' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  676.442422] wlan1: authenticate with <MAC address>
[  676.443383] wlan1: direct probe to <MAC address> (try 1/3)
[  676.645812] wlan1: direct probe to <MAC address> (try 2/3)
[  676.849706] wlan1: direct probe to <MAC address> (try 3/3)
[  677.053596] wlan1: authentication with <MAC address> timed out
[  679.365457] wlan1: authenticate with <MAC address>
[  679.366189] wlan1: direct probe to <MAC address> (try 1/3)
[  679.568284] wlan1: direct probe to <MAC address> (try 2/3)
[  679.772178] wlan1: direct probe to <MAC address> (try 3/3)
[  679.976071] wlan1: authentication with <MAC address> timed out
[  682.787131] wlan1: authenticate with <MAC address>
[  682.788000] wlan1: direct probe to <MAC address> (try 1/3)
[  682.990496] wlan1: direct probe to <MAC address> (try 2/3)
[  683.194390] wlan1: direct probe to <MAC address> (try 3/3)
[  683.398281] wlan1: authentication with <MAC address> timed out
[  697.015711] wlan1: authenticate with <MAC address>
[  697.016972] wlan1: direct probe to <MAC address> (try 1/3)
[  697.219064] wlan1: direct probe to <MAC address> (try 2/3)
[  697.422956] wlan1: direct probe to <MAC address> (try 3/3)
[  697.626849] wlan1: authentication with <MAC address> timed out
[  701.689941] wlan1: authenticate with <MAC 'ReallySlowRouter' [AC1]>
[  701.690728] wlan1: send auth to <MAC 'ReallySlowRouter' [AC1]> (try 1/3)
[  701.692355] wlan1: authenticated
[  701.700701] wlan1: associate with <MAC 'ReallySlowRouter' [AC1]> (try 1/3)
[  701.704496] wlan1: RX AssocResp from <MAC 'ReallySlowRouter' [AC1]> (capab=0x1411 status=0 aid=2)
[  701.707355] wlan1: associated
[  701.721307] wlan1: deauthenticating from <MAC 'ReallySlowRouter' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[  701.723439] wlan1: authenticate with <MAC 'ReallySlowRouter' [AC1]>
[  701.724127] wlan1: send auth to <MAC 'ReallySlowRouter' [AC1]> (try 1/3)
[  701.725607] wlan1: authenticated
[  701.728623] wlan1: associate with <MAC 'ReallySlowRouter' [AC1]> (try 1/3)
[  701.732326] wlan1: RX AssocResp from <MAC 'ReallySlowRouter' [AC1]> (capab=0x1411 status=0 aid=2)
[  701.739180] wlan1: associated
[ 1935.357556] wlan1: deauthenticating from <MAC 'ReallySlowRouter' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1949.966098] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1974.294924] wlan1: authenticate with <MAC 'ReallySlowRouter' [AC1]>
[ 1974.295649] wlan1: send auth to <MAC 'ReallySlowRouter' [AC1]> (try 1/3)
[ 1974.297200] wlan1: authenticated
[ 1974.304271] wlan1: associate with <MAC 'ReallySlowRouter' [AC1]> (try 1/3)
[ 1974.309406] wlan1: RX AssocResp from <MAC 'ReallySlowRouter' [AC1]> (capab=0x1411 status=0 aid=2)
[ 1974.310938] wlan1: associated

########## wireless info END ############


```

Note the rc.local contents are a leftover from when the wireless adapter of choice was an 802.11g USB dongle that didn't work well until using those settings.  Lubuntu 15.04 consistently ignored rc.local, forcing the execution of the script by-hand.

---

### Post by Retro_Trinity on 2015-08-11
Uh, should users of this chipset be looking for a proprietary/standalone driver (similar to the one for the rtl8812au)?

---

