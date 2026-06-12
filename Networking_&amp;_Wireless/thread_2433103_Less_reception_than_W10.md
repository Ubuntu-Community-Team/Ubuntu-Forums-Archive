---
title: "Less reception than W10"
date: 2019-12-13
forum: Networking &amp; Wireless
---

### Post by pedrito2 on 2019-12-13
HI everyone. I'verecently installed lubuntu dual boot since W10 is too bloated for my laptop (HP 240 G7). I've got the wifi working by following the second method: [https://subinsb.com/intall-realtek-d723-wifi-driver-linux/]("https://subinsb.com/install-realtek-d723-wifi-driver-linux/")
com
The problem is that now I cant use wifi from my room (15 meters away from the router) so I have to stay close the router, otherwise it loses connection. Its also very slow in comparison, speed is 6mbps when using lubuntu, and around 20-30mbps when using W10. How can I fix these issues?

The script just in case:[COLOR=#ff0000]** (Script is updated at message #5)**[/COLOR]

```
########## wireless info START ##########

Report from: 13 Dec 2019 20:43 -03 -0300

Booted last: 13 Dec 2019 00:00 -03 -0300

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.6 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.15.0-70-generic #79~16.04.1-Ubuntu SMP Tue Nov 12 14:01:10 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    DeviceName: Hanksville Gbe Lan Connection
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:855e]

05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:d723]
    DeviceName: WLAN
    Subsystem: Hewlett-Packard Company Device [103c:8319]

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:b009 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 13d3:56c9 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

SecureBoot disabled
Platform is in Setup Mode

##### lsmod #############################

rtl8723de              81920  0
btcoexist             344064  1 rtl8723de
phydm_mod             753664  1 rtl8723de
rtl8723_common         24576  1 rtl8723de
rtl_pci                32768  1 rtl8723de
rtlwifi                90112  5 rtl_pci,rtl8723de,btcoexist,phydm_mod,rtl8723_common
r8188eu               417792  0
mac80211              786432  2 rtl_pci,rtlwifi
cfg80211              630784  3 rtlwifi,mac80211,r8188eu
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
wmi_bmof               16384  0
wmi                    24576  2 hp_wmi,wmi_bmof

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether <MAC 'eno1' [IF1]> brd <MAC address>
3: wlo1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether <MAC 'wlo1' [IF2]> brd <MAC address>
    inet 192.168.0.24/24 brd 192.168.0.255 scope global dynamic wlo1
       valid_lft 604428sec preferred_lft 604428sec
    inet6 fe80::cf66:3f66:72b3:6fd/64 scope link 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

eno1      no wireless extensions.

wlo1      IEEE 802.11  ESSID:"FBDFA3"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'FBDFA3' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5979   Missed beacon:0

##### route #############################

default via 192.168.0.1 dev wlo1  proto static  metric 600 
192.168.0.0/24 dev wlo1  proto kernel  scope link  src 192.168.0.24  metric 600 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/resolvconf/resolv.conf']
nameserver 127.0.1.1
search fibertel.com.ar

##### network managers ##################

Installed:

    NetworkManager

Running:

root       673     1  0 19:26 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         rtl8723de
GENERAL.DRIVER-VERSION:                 4.15.0-70-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlo1' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.1/0000:05:00.0/net/wlo1
GENERAL.IP-IFACE:                       wlo1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     FBDFA3
GENERAL.CON-UUID:                       8eaf59d2-0f6e-438a-bafa-4d56b707ac23
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/4
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   8eaf59d2-0f6e-438a-bafa-4d56b707ac23 | FBDFA3
IP4.ADDRESS[1]:                         192.168.0.24/24
IP4.GATEWAY:                            192.168.0.1
IP4.DNS[1]:                             200.42.4.203
IP4.DNS[2]:                             200.49.130.52
IP4.DOMAIN[1]:                          fibertel.com.ar
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 200.42.4.203 200.49.130.52 200.49.130.52
DHCP4.OPTION[5]:                        ip_address = 192.168.0.24
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.0.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 529200
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.0.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 302400
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = fibertel.com.ar
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1576885034
DHCP4.OPTION[21]:                       host_name = joel-HP-240-G7-Notebook-PC
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 192.168.0.1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 604800
IP6.ADDRESS[1]:                         fe80::cf66:3f66:72b3:6fd/64
IP6.GATEWAY:                            

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
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:13.2/0000:02:00.0/net/eno1
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

SSID                       BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
FBDFA3                     <MAC 'FBDFA3' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     * 
Fibertel Wifi 283 2.4 Ghz  <MAC 'Fibertel Wifi 283 2.4 Ghz' [AN2]>  Infra  6     2437 MHz  54 Mbit/s  15      &#9602;___  WPA2       no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager config #############

[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3

[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq
[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/FBDFA3]] (600 root)
[connection] id=FBDFA3 | type=wifi | permissions=user:joel:;
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=FBDFA3
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

##### iw reg get ########################

Region: America/Argentina/Buenos_Aires (based on set time zone)

country AR: DFS-FCC
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A)
    (5250 - 5330 @ 80), (N/A, 24), (0 ms), DFS
    (5490 - 5730 @ 160), (N/A, 24), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)

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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eno1      Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.437 GHz (Channel 6)

wlo1      Scan completed :
          Cell 01 - Address: <MAC 'FBDFA3' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"FBDFA3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000e5c40a9626
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8723de]
filename:       /lib/modules/4.15.0-70-generic/updates/dkms/rtl8723de.ko
firmware:       rtlwifi/rtl8723defw.bin
description:    Realtek 8723DE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     225860B994CF8C6352A5C7A
depends:        rtlwifi,rtl_pci,btcoexist,rtl8723-common,phydm_mod
retpoline:      Y
name:           rtl8723de
vermagic:       4.15.0-70-generic SMP mod_unload 
parm:           dma64:bool
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
parm:           aspm:Set to 1 to enable ASPM (default 0)
 (int)
parm:           debug_level:Set debug level (0-5) (default 0) (int)
parm:           debug_mask:Set debug mask (default 0) (ullong)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           int_clear:Set to 0 to disable interrupt clear before set (default 0)
 (bool)
parm:           ant_sel:Set to 1 or 2 to force antenna number (default 0)
 (int)

[rtl8723_common]
filename:       /lib/modules/4.15.0-70-generic/updates/dkms/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     5AAF25B4699EF07310A021A
depends:        rtlwifi
retpoline:      Y
name:           rtl8723_common
vermagic:       4.15.0-70-generic SMP mod_unload 

[rtl_pci]
filename:       /lib/modules/4.15.0-70-generic/updates/dkms/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     FD9516C293D8A975DA4864C
depends:        mac80211,rtlwifi
retpoline:      Y
name:           rtl_pci
vermagic:       4.15.0-70-generic SMP mod_unload 

[rtlwifi]
filename:       /lib/modules/4.15.0-70-generic/updates/dkms/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     F01C2B7DCFB4342158662D1
depends:        mac80211,cfg80211
retpoline:      Y
name:           rtlwifi
vermagic:       4.15.0-70-generic SMP mod_unload 

[r8188eu]
filename:       /lib/modules/4.15.0-70-generic/kernel/drivers/staging/rtl8188eu/r8188eu.ko
version:        v4.1.4_6773.20130222
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     276AB2B03BBEA50D4D031FE
depends:        cfg80211
staging:        Y
retpoline:      Y
intree:         Y
name:           r8188eu
vermagic:       4.15.0-70-generic SMP mod_unload 
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_channel:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_ht_enable:int
parm:           rtw_cbw40_enable:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_fw_iol:FW IOL (int)
parm:           rtw_mc2u_disable:int
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
parm:           debug:Set debug level (1-9) (default 1) (int)
parm:           monitor_enable:Enable monitor inferface (default: false) (bool)

[mac80211]
filename:       /lib/modules/4.15.0-70-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     CA60D8FB7E9197741540867
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-70-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.15.0-70-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A545B569ABD42802819105C
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-70-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723de]
ant_sel: 0
aspm: 0
debug_level: 0
debug_mask: 18446744073709551615
disable_watchdog: N
dma64: N
fwlps: N
int_clear: N
ips: Y
msi: Y
swenc: N
swlps: N

[r8188eu]
debug: 1
if2name: wlan%d
ifname: wlan%d
monitor_enable: N
rtw_80211d: 0
rtw_ampdu_amsdu: 0
rtw_ampdu_enable: 1
rtw_antdiv_cfg: 2
rtw_antdiv_type: 0
rtw_cbw40_enable: 3
rtw_channel: 1
rtw_channel_plan: 66
rtw_enusbss: 0
rtw_fw_iol: 1
rtw_ht_enable: 1
rtw_hwpdn_mode: 2
rtw_initmac: (null)
rtw_ips_mode: 1
rtw_max_roaming_times: 2
rtw_mc2u_disable: 0
rtw_notch_filter: 0
rtw_power_mgnt: 1
rtw_rx_stbc: 1
rtw_smart_ps: 2
rtw_vcs_type: 1
rtw_vrtl_carrier_sense: 2
rtw_wifi_spec: 0
rtw_wmm_enable: 1

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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[  490.966951] wlo1: send auth to <MAC 'FBDFA3' [AC1]> (try 2/3)
[  491.070962] wlo1: send auth to <MAC 'FBDFA3' [AC1]> (try 3/3)
[  491.174961] wlo1: authentication with <MAC 'FBDFA3' [AC1]> timed out
[  492.847890] wlo1: authenticate with <MAC 'FBDFA3' [AC1]>
[  492.867268] wlo1: send auth to <MAC 'FBDFA3' [AC1]> (try 1/3)
[  492.970996] wlo1: send auth to <MAC 'FBDFA3' [AC1]> (try 2/3)
[  493.075011] wlo1: send auth to <MAC 'FBDFA3' [AC1]> (try 3/3)
[  493.091790] wlo1: authenticated
[  493.095134] wlo1: associate with <MAC 'FBDFA3' [AC1]> (try 1/3)
[  493.199010] wlo1: associate with <MAC 'FBDFA3' [AC1]> (try 2/3)
[  493.303005] wlo1: associate with <MAC 'FBDFA3' [AC1]> (try 3/3)
[  493.407004] wlo1: association with <MAC 'FBDFA3' [AC1]> timed out
[  505.055489] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[  507.435953] wlo1: authenticate with <MAC 'FBDFA3' [AC1]>
[  507.462198] wlo1: send auth to <MAC 'FBDFA3' [AC1]> (try 1/3)
[  507.563318] wlo1: send auth to <MAC 'FBDFA3' [AC1]> (try 2/3)
[  507.667323] wlo1: send auth to <MAC 'FBDFA3' [AC1]> (try 3/3)
[  507.771328] wlo1: authentication with <MAC 'FBDFA3' [AC1]> timed out
[  520.104868] wlo1: authenticate with <MAC 'FBDFA3' [AC1]>
[  520.123869] wlo1: send auth to <MAC 'FBDFA3' [AC1]> (try 1/3)
[  520.135771] wlo1: authenticated
[  520.139621] wlo1: associate with <MAC 'FBDFA3' [AC1]> (try 1/3)
[  520.171168] wlo1: RX AssocResp from <MAC 'FBDFA3' [AC1]> (capab=0x431 status=0 aid=3)
[  520.447113] wlo1: associated
[  524.191030] wlo1: disassociated from <MAC 'FBDFA3' [AC1]> (Reason: 2=PREV_AUTH_NOT_VALID)
[  644.264945] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 1239.809269] wlo1: authenticate with <MAC 'FBDFA3' [AC1]>
[ 1239.828469] wlo1: send auth to <MAC 'FBDFA3' [AC1]> (try 1/3)
[ 1239.832408] wlo1: authenticated
[ 1239.835779] wlo1: associate with <MAC 'FBDFA3' [AC1]> (try 1/3)
[ 1239.844094] wlo1: RX AssocResp from <MAC 'FBDFA3' [AC1]> (capab=0x431 status=0 aid=3)
[ 1240.121108] wlo1: associated
[ 1240.854780] IPv6: ADDRCONF(NETDEV_CHANGE): wlo1: link becomes ready
[ 4270.517706] wlo1: deauthenticating from <MAC 'FBDFA3' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 4271.764230] wlo1: authenticate with <MAC 'FBDFA3' [AC1]>
[ 4271.776490] wlo1: send auth to <MAC 'FBDFA3' [AC1]> (try 1/3)
[ 4271.792388] wlo1: authenticated
[ 4271.795906] wlo1: associate with <MAC 'FBDFA3' [AC1]> (try 1/3)
[ 4271.805941] wlo1: RX AssocResp from <MAC 'FBDFA3' [AC1]> (capab=0x431 status=0 aid=3)
[ 4272.082522] wlo1: associated

########## wireless info END ############

```

---

### Post by guiverc on 2019-12-13
I note you are using Lubuntu 16.04.6 LTS

Lubuntu 16.04 LTS was released 2016-April (thus 16.04) with **3 years **of supported life. The last iteration (16.04.6) being released early (April) this year ([https://lubuntu.me/xenial-released/](https://lubuntu.me/xenial-released/)) where you'll note it states

[B][I][COLOR=#555555][FONT=Ubuntu]Lubuntu 16.04 LTS will be supported until April 2019, with three years of support.

[/FONT][/COLOR][/I][/B]*[COLOR=#555555][FONT=Ubuntu]FYI: Not all flavors re-spun 16.04.6 ISOs; deciding it wasn't worth the effort with mere weeks remaining in 16.04's life-span[/FONT][/COLOR]*[B][I][COLOR=#555555][FONT=Ubuntu]

[/FONT][/COLOR][/I][/B][COLOR=#555555][FONT=Ubuntu]Yes the Ubuntu 16.04 base  (or with standard Unity 7 desktop, server (no desktop), or Ubuntu Kylin desktop) has 5 years of support, but all flavors only came with 3 years of support.  Thus I'd recommend switching to a a supported release of Ubuntu.

If you want to confirm the actual support status of your system, please use `ubuntu-support-status`, but Lubuntu 16.04 is EOL as it is a flavor[/FONT][/COLOR]

---

### Post by praseodym on 2019-12-14
Unload a wrongly loaded driver

```
sudo modprobe -rfv r8188eu rtl8723de
sudo modprobe -v rtl8723de
```
If you used the "git" method, run

```
sudo cp /usr/src/rtlwifi-new-0.6/firmware/rtlwifi/* /lib/firmware/rtlwifi/ 
```
and reboot

---

### Post by pedrito2 on 2019-12-14
> **guiverc said:**
> I note you are using Lubuntu 16.04.6 LTS

Lubuntu 16.04 LTS was released 2016-April (thus 16.04) with **3 years **of supported life. The last iteration (16.04.6) being released early (April) this year ([https://lubuntu.me/xenial-released/](https://lubuntu.me/xenial-released/)) where you'll note it states

[B][I][COLOR=#555555][FONT=Ubuntu]Lubuntu 16.04 LTS will be supported until April 2019, with three years of support.

[/FONT][/COLOR][/I][/B]*[COLOR=#555555][FONT=Ubuntu]FYI: Not all flavors re-spun 16.04.6 ISOs; deciding it wasn't worth the effort with mere weeks remaining in 16.04's life-span[/FONT][/COLOR]*[B][I][COLOR=#555555][FONT=Ubuntu]

[/FONT][/COLOR][/I][/B][COLOR=#555555][FONT=Ubuntu]Yes the Ubuntu 16.04 base  (or with standard Unity 7 desktop, server (no desktop), or Ubuntu Kylin desktop) has 5 years of support, but all flavors only came with 3 years of support.  Thus I'd recommend switching to a a supported release of Ubuntu.

If you want to confirm the actual support status of your system, please use `ubuntu-support-status`, but Lubuntu 16.04 is EOL as it is a flavor[/FONT][/COLOR]


I didnt know, but just updated to 18.04 LTS

---

### Post by pedrito2 on 2019-12-14
> **praseodym said:**
> Unload a wrongly loaded driver

```
sudo modprobe -rfv r8188eu rtl8723de
sudo modprobe -v rtl8723de
```
If you used the "git" method, run

```
sudo cp /usr/src/rtlwifi-new-0.6/firmware/rtlwifi/* /lib/firmware/rtlwifi/ 
```
and reboot

I believe that the connection when i am closer to the router is faster, but it still loses connection from 15 meters away. Updated script:

```
########## wireless info START ##########

Report from: 14 Dec 2019 16:28 -03 -0300

Booted last: 14 Dec 2019 00:00 -03 -0300

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 5.0.0-37-generic #40~18.04.1-Ubuntu SMP Thu Nov 14 12:06:39 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Lubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:855e]
    Kernel driver in use: r8169

05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:d723]
    Subsystem: Hewlett-Packard Company Device [103c:8319]
    Kernel driver in use: rtl8723de

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:b009 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 13d3:56c9 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

SecureBoot disabled
Platform is in Setup Mode

##### lsmod #############################

rtl8723de              81920  0
btcoexist             335872  1 rtl8723de
phydm_mod             753664  1 rtl8723de
rtl8723_common         24576  1 rtl8723de
rtl_pci                28672  1 rtl8723de
rtlwifi                94208  5 rtl_pci,rtl8723de,btcoexist,phydm_mod,rtl8723_common
mac80211              819200  2 rtl_pci,rtlwifi
cfg80211              679936  2 rtlwifi,mac80211
wmi_bmof               16384  0
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
wmi                    28672  2 hp_wmi,wmi_bmof

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'eno1' [IF1]> brd <MAC address>
3: wlo1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether <MAC 'wlo1' [IF2]> brd <MAC address>
    inet 192.168.0.24/24 brd 192.168.0.255 scope global dynamic noprefixroute wlo1
       valid_lft 604346sec preferred_lft 604346sec
    inet6 fe80::32ff:ce23:ac25:aaae/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

eno1      no wireless extensions.

wlo1      IEEE 802.11  ESSID:"FBDFA3"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'FBDFA3' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3228   Missed beacon:0

##### route #############################

default via 192.168.0.1 dev wlo1 proto dhcp metric 600 
192.168.0.0/24 dev wlo1 proto kernel scope link src 192.168.0.24 metric 600 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0
search fibertel.com.ar

##### network managers ##################

Installed:

    NetworkManager

Running:

root       580     1  0 16:20 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         rtl8723de
GENERAL.DRIVER-VERSION:                 5.0.0-37-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlo1' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.1/0000:05:00.0/net/wlo1
GENERAL.IP-IFACE:                       wlo1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     FBDFA3
GENERAL.CON-UUID:                       b11faf74-988f-4546-a2db-bcafaee228c5
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     72 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
IP4.ADDRESS[1]:                         192.168.0.24/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.0.1, mt = 600
IP4.ROUTE[2]:                           dst = 192.168.0.0/24, nh = 0.0.0.0, mt = 600
IP4.DNS[1]:                             200.42.4.203
IP4.DNS[2]:                             200.49.130.52
IP4.DOMAIN[1]:                          fibertel.com.ar
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 200.42.4.203 200.49.130.52 200.49.130.52
DHCP4.OPTION[5]:                        ip_address = 192.168.0.24
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.0.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 529200
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       dhcp_renewal_time = 302400
DHCP4.OPTION[16]:                       routers = 192.168.0.1
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = fibertel.com.ar
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1576956040
DHCP4.OPTION[21]:                       host_name = joel-HP-240-G7-Notebook-PC
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 192.168.0.1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 604800
DHCP4.OPTION[31]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         fe80::32ff:ce23:ac25:aaae/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 600
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   b11faf74-988f-4546-a2db-bcafaee228c5 | FBDFA3

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 --
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:13.2/0000:02:00.0/net/eno1
GENERAL.IP-IFACE:                       --
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
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

SSID    BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY   ACTIVE  IN-USE 
FBDFA3  <MAC 'FBDFA3' [AC1]>  Infra  6     2437 MHz  195 Mbit/s  69      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     *      

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager config #############

[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3

[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile
[ifupdown]
managed=false
[device]
wifi.scan-rand-mac-address=no

[[/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf]]
[main]
dns=systemd-resolved

[[/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf]]
[keyfile]
unmanaged-devices=*,except:type:wifi,except:type:wwan

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/FBDFA3]] (600 root)
[connection] id=FBDFA3 | type=wifi | permissions=user:joel:;
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=FBDFA3
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: America/Argentina/Buenos_Aires (based on set time zone)

global
country AR: DFS-FCC
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A), AUTO-BW
    (5250 - 5330 @ 80), (N/A, 24), (0 ms), DFS, AUTO-BW
    (5490 - 5730 @ 160), (N/A, 24), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)

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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eno1      Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.437 GHz (Channel 6)

wlo1      Scan completed :
          Cell 01 - Address: <MAC 'FBDFA3' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"FBDFA3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000f63596fdc2
                    Extra: Last beacon: 152ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Fibertel Wifi 283 2.4 Ghz' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"Fibertel Wifi 283 2.4 Ghz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002ec606060f
                    Extra: Last beacon: 224ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8723de]
filename:       /lib/modules/5.0.0-37-generic/updates/dkms/rtl8723de.ko
firmware:       rtlwifi/rtl8723defw.bin
description:    Realtek 8723DE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     99CC08D9D1086FB0E409C67
depends:        rtlwifi,rtl_pci,btcoexist,rtl8723-common,phydm_mod
retpoline:      Y
name:           rtl8723de
vermagic:       5.0.0-37-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           dma64:bool
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
parm:           aspm:Set to 1 to enable ASPM (default 0)
 (int)
parm:           debug_level:Set debug level (0-5) (default 0) (int)
parm:           debug_mask:Set debug mask (default 0) (ullong)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           int_clear:Set to 0 to disable interrupt clear before set (default 0)
 (bool)
parm:           ant_sel:Set to 1 or 2 to force antenna number (default 0)
 (int)

[rtl8723_common]
filename:       /lib/modules/5.0.0-37-generic/updates/dkms/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     79658317D5A6BA261734424
depends:        rtlwifi
retpoline:      Y
name:           rtl8723_common
vermagic:       5.0.0-37-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[rtl_pci]
filename:       /lib/modules/5.0.0-37-generic/updates/dkms/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     FD9516C293D8A975DA4864C
depends:        mac80211,rtlwifi
retpoline:      Y
name:           rtl_pci
vermagic:       5.0.0-37-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[rtlwifi]
filename:       /lib/modules/5.0.0-37-generic/updates/dkms/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     F01C2B7DCFB4342158662D1
depends:        mac80211,cfg80211
retpoline:      Y
name:           rtlwifi
vermagic:       5.0.0-37-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[mac80211]
filename:       /lib/modules/5.0.0-37-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0CDD28A506BDDDE9444E85C
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       5.0.0-37-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/5.0.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     DCECEA5B6FF7EF332DBC1F5
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.0.0-37-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723de]
ant_sel: 0
aspm: 0
debug_level: 0
debug_mask: 18446744073709551615
disable_watchdog: N
dma64: N
fwlps: N
int_clear: N
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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   10.186544] rtlwifi: loading out-of-tree module taints kernel.
[   10.186633] rtlwifi: module verification failed: signature and/or required key missing - tainting kernel
[   10.285230] [drm] Finished loading DMC firmware i915/glk_dmc_ver1_04.bin (v1.4)
[   10.388891] rtl8723de: Using firmware rtlwifi/rtl8723defw.bin
[   10.394779] Bluetooth: hci0: RTL: rtl: examining hci_ver=08 hci_rev=000d lmp_ver=08 lmp_subver=8723
[   10.395665] Bluetooth: hci0: RTL: rtl: loading rtl_bt/rtl8723d_fw.bin
[   10.407190] Bluetooth: hci0: RTL: rtl: loading rtl_bt/rtl8723d_config.bin
[   10.476578] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   10.476880] rtlwifi: rtlwifi: wireless switch is on
[   10.585935] rtl8723de 0000:05:00.0 wlo1: renamed from wlan0
[   18.720051] r8169 0000:02:00.0 eno1: Link is Down
[   26.844804] wlo1: authenticate with <MAC 'FBDFA3' [AC1]>
[   28.152610] wlo1: send auth to <MAC 'FBDFA3' [AC1]> (try 1/3)
[   28.196648] wlo1: authenticated
[   28.200632] wlo1: associate with <MAC 'FBDFA3' [AC1]> (try 1/3)
[   28.206912] wlo1: RX AssocResp from <MAC 'FBDFA3' [AC1]> (capab=0x431 status=0 aid=1)
[   28.536555] wlo1: associated
[   29.308955] IPv6: ADDRCONF(NETDEV_CHANGE): wlo1: link becomes ready

########## wireless info END ############
```

---

### Post by jeremy31 on 2019-12-14
If signal strength improves with ```
sudo modprobe -r rtl8723de && sleep 10 && sudo modprobe rtl8723de ant_sel=2
```
Do
```
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de.conf
```

---

### Post by praseodym on 2019-12-14
Do also change the encryption mode in your router to pure WPA2-AES (CCMP), not mixed mode WPA/WPA2, and change the channel fixed to 1 or 13

---

