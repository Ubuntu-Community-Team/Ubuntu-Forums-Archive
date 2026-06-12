---
title: "RTL8101/2/6E wireless not working"
date: 2018-05-14
forum: Networking &amp; Wireless
---

### Post by juanjo836-arg on 2018-05-14
Hi guys I have a fresh install on a Bangho netbook of xubuntu 16.04 32 bit, (I had first installed 18.04 and downgrade because of wireless not working), the issue persists in 16.04, i have managed to install the official driver from Realtek page, but i can't get it working, i have tried several solutions, but can't make it work. I hope you guys can help me, i am currently connected using a usb wifi TP LINK dongle, works perfectly, wired works also fine, thanks in advance.
```
########## wireless info START ##########

Report from: 14 May 2018 17:42 -03 -0300

Booted last: 14 May 2018 00:00 -03 -0300

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.4 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.13.0-41-generic #46~16.04.1-Ubuntu SMP Thu May 3 10:06:03 UTC 2018 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Device [1991:6030]
    Kernel driver in use: r8101

##### lsusb #############################

Bus 001 Device 003: ID 05e1:0100 Syntek Semiconductor Co., Ltd 802.11g + Bluetooth Wireless Adapter
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 004: ID 0bda:8179 Realtek Semiconductor Corp. RTL8188EUS 802.11n Wireless Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

r8188eu               385024  0
cfg80211              532480  1 r8188eu

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:865 errors:0 dropped:0 overruns:0 frame:0
          TX packets:865 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:71460 (71.4 KB)  TX bytes:71460 (71.4 KB)

wlx<IF from MAC [IF2]> Link encap:Ethernet  HWaddr <MAC 'wlx<IF from MAC [IF2]>' [IF2]>  
          inet addr:192.168.1.14  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::9d65:31d:296c:59b1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3723 errors:0 dropped:57 overruns:0 frame:0
          TX packets:3905 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2580510 (2.5 MB)  TX bytes:589834 (589.8 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp2s0    no wireless extensions.

wlx<IF from MAC [IF2]>  IEEE 802.11bgn  ESSID:"bandera-net"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.422 GHz  Access Point: <MAC 'bandera-net' [AC1]>   
          Bit Rate:72.2 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=99/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlx<IF from MAC [IF2]>
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlx<IF from MAC [IF2]>
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlx<IF from MAC [IF2]>

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       708     1  0 17:33 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlx<IF from MAC [IF2]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        802.11n NIC
GENERAL.DRIVER:                         r8188eu
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF2]>' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/net/wlx<IF from MAC [IF2]>
GENERAL.IP-IFACE:                       wlx<IF from MAC [IF2]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     bandera-net 2
GENERAL.CON-UUID:                       39f1ab38-4dd6-4be1-a309-084a2789b70e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     72 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2,0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   39f1ab38-4dd6-4be1-a309-084a2789b70e | bandera-net 2
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   79760f56-f2d2-4c1f-b521-1f631adceb80 | bandera-net 1
IP4.ADDRESS[1]:                         192.168.1.14/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.WINS[1]:                            192.168.1.1
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        dhcp_message_type = 5
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       expiry = 1526339638
DHCP4.OPTION[15]:                       dhcp_lease_time = 86400
DHCP4.OPTION[16]:                       ip_address = 192.168.1.14
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       vendor_encapsulated_options = 0:8:c0:a8:1:2:c0:a8:1:63
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[22]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[23]:                       routers = 192.168.1.1
DHCP4.OPTION[24]:                       requested_ntp_servers = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       netbios_name_servers = 192.168.1.1
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::9d65:31d:296c:59b1/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8101
GENERAL.DRIVER-VERSION:                 1.032.04-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/enp2s0
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

SSID         BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
bandera-net  <MAC 'bandera-net' [AC1]>  Infra  3     2422 MHz  16 Mbit/s  100     â–‚â–„â–†â–ˆ  WPA2       yes     * 
bandera-net  <MAC 'bandera-net' [AC2]>  Infra  3     2422 MHz  44 Mbit/s  43      â–‚â–„__  WPA2       no        
CHUCHUY      <MAC 'CHUCHUY' [AC3]>  Infra  6     2437 MHz  16 Mbit/s  42      â–‚â–„__  WPA1 WPA2  no        

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

[[/etc/NetworkManager/system-connections/bandera-net 1]] (600 root)
[connection] id=bandera-net 1 | type=wifi | permissions=user:joaquin:;
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=bandera-net
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/bandera-net 2]] (600 root)
[connection] id=bandera-net 2 | type=wifi | permissions=user:joaquin:;
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=bandera-net
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/bandera-net]] (600 root)
[connection] id=bandera-net | type=wifi | permissions=user:xubuntu:;
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=bandera-net
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

##### iw reg get ########################

Region: America/Argentina/La_Rioja (based on set time zone)

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

enp2s0    no frequency information.

wlx<IF from MAC [IF2]>  13 channels in total; available frequencies :
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
          Current Frequency=2.422 GHz (Channel 3)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp2s0    Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.437 GHz (Channel 6)

wlx<IF from MAC [IF2]>  Scan completed :
          Cell 01 - Address: <MAC 'bandera-net' [AC1]>
                    ESSID:"bandera-net"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=100/100  Signal level=99/100  
          Cell 02 - Address: <MAC 'bandera-net' [AC2]>
                    ESSID:"bandera-net"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=42/100  
          Cell 03 - Address: <MAC 'CHUCHUY' [AC3]>
                    ESSID:"CHUCHUY"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=46/100  

##### module infos ######################

[r8188eu]
filename:       /lib/modules/4.13.0-41-generic/kernel/drivers/staging/rtl8188eu/r8188eu.ko
version:        v4.1.4_6773.20130222
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     B51B89DB4ED36B6FD15BBB3
depends:        cfg80211
staging:        Y
intree:         Y
name:           r8188eu
vermagic:       4.13.0-41-generic SMP mod_unload 686 
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

[cfg80211]
filename:       /lib/modules/4.13.0-41-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A5EDD7467E172A70410EBCD
depends:        
intree:         Y
name:           cfg80211
vermagic:       4.13.0-41-generic SMP mod_unload 686 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/r8168-dkms.conf]
alias    pci:v00001186d00004300sv00001186sd00004B10bc*sc*i*    r8168
alias    pci:v000010ECd00008168sv*sd*bc*sc*i*            r8168

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    5.186433] psmouse serio3: elantech: assuming hardware version 1 (with firmware version 0x020006)
[   29.634147] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   29.635442] enp2s0: 0xf80ac000, <MAC 'enp2s0' [IF1]>, IRQ 16
[   29.688747] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   72.378782] r8188eu: module is from the staging directory, the quality is unknown, you have been warned.
[   72.454557] r8188eu 1-2:1.0 wlx<IF from MAC [IF2]>: renamed from wlan0
[   72.601860] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF2]>: link is not ready (repeated 3 times)
[   76.248659] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<IF from MAC [IF2]>: link becomes ready

########## wireless info END ############
```

---

### Post by chili555 on 2018-05-14
Your RTL8101/2/6E device is this:> [COLOR="#FF0000"]Ethernet[/COLOR] controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit [COLOR="#FF0000"]Ethernet [/COLOR]controller [10ec:8136] (rev 02)It is not a wireless device. 

Other than the USB, we see no other wireless device.

---

### Post by juanjo836-arg on 2018-05-14
I'm sorry, what could be the cause, works fine in windows

---

### Post by chili555 on 2018-05-14
What does the Windows Control Panel, or whatever it is (Sorry, I'm not familiar with Windows) say the device is?

What does this tell us?```
lspci -nnk
```

---

### Post by praseodym on 2018-05-15
Bus 001 Device 004: ID 0bda:8179 Realtek Semiconductor Corp. RTL8188EUS 802.11n [COLOR="#FF0000"]Wireless[/COLOR] Network Adapter

Maybe its connected internally by USB?!

---

