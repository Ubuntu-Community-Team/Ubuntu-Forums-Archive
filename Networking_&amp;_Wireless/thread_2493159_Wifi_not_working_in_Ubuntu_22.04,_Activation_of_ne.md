---
title: "Wifi not working in Ubuntu 22.04, Activation of network connection failed"
date: 2023-12-06
forum: Networking &amp; Wireless
---

### Post by asimovjr on 2023-12-06
My Ubuntu crashed once, had to force reboot using the power button, since then the wifi is not connecting properly, it works (sometimes when I use the command: sudo systemctl start NetworkManager or restart NetworkManager)

Followed the instruction on [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) and ran wireless-info



Txt file genearted is :


```

########## wireless info START ##########


Report from: 05 Dec 2023 21:48 MST -0700


Booted last: 05 Dec 2023 00:00 MST -0700


Script from: 25 Jan 2020 03:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.3 LTS
Release:	22.04
Codename:	jammy


##### kernel ############################


Linux 6.2.0-37-generic #38~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Thu Nov  2 18:01:13 UTC 2 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


0000:02:00.0 Network controller [0280]: MEDIATEK Corp. MT7921 802.11ax PCI Express Wireless Network Adapter [14c3:7961]
	Subsystem: AzureWave Device [1a3b:4680]
	Kernel driver in use: mt7921e


0000:03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. Device [10ec:8162] (rev 05)
	Subsystem: ASUSTeK Computer Inc. Device [1043:208f]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 322e:202c Sonix Technology Co., Ltd. USB2.0 HD UVC WebCam
Bus 003 Device 016: ID 22d9:276a OPPO Electronics Corp. SM6375-QRD _SN:9B1FE125
Bus 003 Device 004: ID 13d3:3563 IMC Networks Wireless_Device
Bus 003 Device 002: ID 30fa:1540 INSTANT USB GAMING MOUSE 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
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


##### lsmod #############################


mac80211             1617920  3 mt76,mt7921_common,mt76_connac_lib
cfg80211             1241088  4 mt76,mac80211,mt7921_common,mt76_connac_lib
asus_nb_wmi            28672  0
wmi_bmof               16384  0
libarc4                16384  1 mac80211
asus_wmi               73728  2 asus_nb_wmi,mfd_aaeon
ledtrig_audio          16384  2 snd_hda_codec_generic,asus_wmi
sparse_keymap          16384  2 intel_hid,asus_wmi
platform_profile       16384  1 asus_wmi
video                  73728  3 asus_wmi,i915,nvidia_modeset
wmi                    40960  4 video,asus_wmi,wmi_bmof,mfd_aaeon


##### interfaces ########################


##### ifconfig ##########################


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp3s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'enp3s0' [IF1]> brd <MAC address>
3: wlp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether <MAC 'wlp2s0' [IF2]> brd <MAC address>
8: enx<IF from MAC [IF3]>: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 1000
    link/ether <MAC 'enx<IF from MAC [IF3]>' [IF3]> brd <MAC address>
    inet 192.168.84.67/24 brd 192.168.84.255 scope global dynamic noprefixroute enx<IF from MAC [IF3]>
       valid_lft 2173sec preferred_lft 2173sec
    inet6 fe80::421b:6d78:60a1:7dfd/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever


##### iwconfig ##########################


lo        no wireless extensions.


enp3s0    no wireless extensions.


enx<IF from MAC [IF3]>  no wireless extensions.


wlp2s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=3 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


##### route #############################


default via 192.168.84.17 dev enx<IF from MAC [IF3]> proto dhcp metric 100 
169.254.0.0/16 dev enx<IF from MAC [IF3]> scope link metric 1000 
192.168.84.0/24 dev enx<IF from MAC [IF3]> proto kernel scope link src 192.168.84.67 metric 100 


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']


nameserver 127.0.0.53
options edns0 trust-ad
search .


##### network managers ##################


Installed:


	NetworkManager


Running:


root       76844       1  0 21:25 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enx<IF from MAC [IF3]>
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/3
GENERAL.VENDOR:                         OPPO Electronics Corp.
GENERAL.PRODUCT:                        SM6375-QRD _SN:9B1FE125
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 6.2.0-37-generic
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'enx<IF from MAC [IF3]>' [IF3]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               4 (full)
GENERAL.IP6-CONNECTIVITY:               4 (full)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/net/enx<IF from MAC [IF3]>
GENERAL.PATH:                           pci-0000:00:14.0-usb-0:2:1.0
GENERAL.IP-IFACE:                       enx<IF from MAC [IF3]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 5
GENERAL.CON-UUID:                       9fbbb258-da27-3916-a7e5-33e27e9a09d8
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               yes
INTERFACE-FLAGS.CARRIER:                yes
INTERFACE-FLAGS.PROMISC:                no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.84.67/24
IP4.GATEWAY:                            192.168.84.17
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.84.17, mt = 100
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.ROUTE[3]:                           dst = 192.168.84.0/24, nh = 0.0.0.0, mt = 100
IP4.DNS[1]:                             192.168.84.17
DHCP4.OPTION[1]:                        broadcast_address = 192.168.84.255
DHCP4.OPTION[2]:                        dhcp_lease_time = 3599
DHCP4.OPTION[3]:                        dhcp_server_identifier = 192.168.84.17
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.84.17
DHCP4.OPTION[5]:                        expiry = 1701840303
DHCP4.OPTION[6]:                        host_name = harsh-ASUS-TUF-Gaming-F15-FX506HCB-FX506HCB
DHCP4.OPTION[7]:                        ip_address = 192.168.84.67
DHCP4.OPTION[8]:                        next_server = 192.168.84.17
DHCP4.OPTION[9]:                        requested_broadcast_address = 1
DHCP4.OPTION[10]:                       requested_domain_name = 1
DHCP4.OPTION[11]:                       requested_domain_name_servers = 1
DHCP4.OPTION[12]:                       requested_domain_search = 1
DHCP4.OPTION[13]:                       requested_host_name = 1
DHCP4.OPTION[14]:                       requested_interface_mtu = 1
DHCP4.OPTION[15]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[16]:                       requested_nis_domain = 1
DHCP4.OPTION[17]:                       requested_nis_servers = 1
DHCP4.OPTION[18]:                       requested_ntp_servers = 1
DHCP4.OPTION[19]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[20]:                       requested_root_path = 1
DHCP4.OPTION[21]:                       requested_routers = 1
DHCP4.OPTION[22]:                       requested_static_routes = 1
DHCP4.OPTION[23]:                       requested_subnet_mask = 1
DHCP4.OPTION[24]:                       requested_time_offset = 1
DHCP4.OPTION[25]:                       requested_wpad = 1
DHCP4.OPTION[26]:                       routers = 192.168.84.17
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         fe80::421b:6d78:60a1:7dfd/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 1024
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/1
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   9fbbb258-da27-3916-a7e5-33e27e9a09d8 | Wired connection 5


GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/4
GENERAL.VENDOR:                         MEDIATEK Corp.
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         mt7921e
GENERAL.DRIVER-VERSION:                 6.2.0-37-generic
GENERAL.FIRMWARE-VERSION:               ____010000-20220209150915
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          60 (connecting (need authentication))
GENERAL.REASON:                         8 (802.1X supplicant disconnected)
GENERAL.IP4-CONNECTIVITY:               1 (none)
GENERAL.IP6-CONNECTIVITY:               1 (none)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlp2s0
GENERAL.PATH:                           pci-0000:02:00.0
GENERAL.IP-IFACE:                       --
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     SETUP-171A
GENERAL.CON-UUID:                       53b0505c-bb50-4298-aa56-9f91516b9a17
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/6
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               no
INTERFACE-FLAGS.CARRIER:                no
INTERFACE-FLAGS.PROMISC:                no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  no
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
WIFI-PROPERTIES.MESH:                   no
WIFI-PROPERTIES.IBSS-RSN:               no
IP4.GATEWAY:                            --
IP6.GATEWAY:                            --
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/6,/org/freedesktop/NetworkManager/Settings/7
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   53b0505c-bb50-4298-aa56-9f91516b9a17 | SETUP-171A
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   42c1c237-4f4f-4df3-a779-6125ae6ea61e | CoxWiFi


GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/2
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 6.2.0-37-generic
GENERAL.FIRMWARE-VERSION:               rtl8125b-2_0.0.2 07/13/20
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.IP4-CONNECTIVITY:               1 (none)
GENERAL.IP6-CONNECTIVITY:               1 (none)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.0/0000:03:00.0/net/enp3s0
GENERAL.PATH:                           pci-0000:03:00.0
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
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               no
INTERFACE-FLAGS.CARRIER:                no
INTERFACE-FLAGS.PROMISC:                no
WIRED-PROPERTIES.CARRIER:               off
IP4.GATEWAY:                            --
IP6.GATEWAY:                            --
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --


SSID               BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY          ACTIVE  IN-USE 
SETUP-0AFE         <MAC 'SETUP-0AFE' [AN1]>  Infra  1     2412 MHz  260 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2              no             
--                 <MAC '--' [AN2]>  Infra  1     2412 MHz  260 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2              no             
--                 <MAC '--' [AN3]>  Infra  1     2412 MHz  260 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2 802.1X       no             
SETUP-0AFE         <MAC 'SETUP-0AFE' [AN4]>  Infra  44    5220 MHz  540 Mbit/s  99      &#9602;&#9604;&#9606;&#9608;  WPA2              no             
SETUP-1A45         <MAC 'SETUP-1A45' [AN5]>  Infra  6     2437 MHz  130 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  WPA2              no             
--                 <MAC '--' [AN6]>  Infra  44    5220 MHz  540 Mbit/s  80      &#9602;&#9604;&#9606;_  WPA2 802.1X       no             
--                 <MAC '--' [AN38]>  Infra  11    2462 MHz  130 Mbit/s  50      &#9602;&#9604;__  WPA2              no             
--                 <MAC '--' [AN39]>  Infra  11    2462 MHz  130 Mbit/s  50      &#9602;&#9604;__  WPA2              no             
--                 <MAC '--' [AN40]>  Infra  157   5785 MHz  540 Mbit/s  50      &#9602;&#9604;__  WPA1 WPA2 802.1X  no             
--                 <MAC '--' [AN41]>  Infra  157   5785 MHz  540 Mbit/s  49      &#9602;&#9604;__  WPA1 WPA2 802.1X  no             
--                 <MAC '--' [AN42]>  Infra  11    2462 MHz  130 Mbit/s  47      &#9602;&#9604;__  WPA1 WPA2 802.1X  no             
--                 <MAC '--' [AN43]>  Infra  11    2462 MHz  130 Mbit/s  45      &#9602;&#9604;__  WPA2              no             
--                 <MAC '--' [AN44]>  Infra  11    2462 MHz  130 Mbit/s  45      &#9602;&#9604;__  WPA2              no             
SETUP-E91F         <MAC 'SETUP-E91F' [AN45]>  Infra  11    2462 MHz  130 Mbit/s  42      &#9602;&#9604;__  WPA2              no             
Verizon_ZRJ7VS     <MAC 'Verizon_ZRJ7VS' [AN46]>  Infra  6     2437 MHz  260 Mbit/s  40      &#9602;&#9604;__  WPA2              no                
--        
     
--          
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
unmanaged-devices=*,except:type:wifi,except:type:gsm,except:type:cdma


[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-31-mac-addr-change]
match-device=driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/SETUP-171A.nmconnection]] (600 root)
[connection] id=SETUP-171A | type=wifi
[wifi] ssid=SETUP-171A
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/CoxWiFi.nmconnection]] (600 root)
[connection] id=CoxWiFi | type=wifi
[wifi] ssid=CoxWiFi
[ipv4] method=auto
[ipv6] method=auto


##### Netplan config ####################


[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager


##### iw reg get ########################


'iw' is not installed (package "iw").


##### iwlist channels ###################


lo        no frequency information.


enp3s0    no frequency information.


enx<IF from MAC [IF3]>  no frequency information.


wlp2s0    32 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz
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


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp3s0    Interface doesn't support scanning.


wlp2s0    Failed to read scan data : Argument list too long


enx<IF from MAC [IF3]>  Interface doesn't support scanning.


##### module infos ######################


[mac80211]
filename:       /lib/modules/6.2.0-37-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
depends:        cfg80211,libarc4
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       6.2.0-37-generic SMP preempt mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/6.2.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       6.2.0-37-generic SMP preempt mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


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


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[38515.965331] wlp2s0: send auth to <MAC 'SETUP-171A' [AN127]> (try 1/3)
[38515.976506] wlp2s0: authenticated
[38515.979690] wlp2s0: associate with <MAC 'SETUP-171A' [AN127]> (try 1/3)
[38516.005520] wlp2s0: associate with <MAC 'SETUP-171A' [AN127]> (try 2/3)
[38516.012746] wlp2s0: RX AssocResp from <MAC 'SETUP-171A' [AN127]> (capab=0x1411 status=0 aid=2)
[38516.041010] wlp2s0: associated
[38516.102241] wlp2s0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC 'SETUP-171A' [AN127]>
[38516.142242] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[38519.713510] wlp2s0: deauthenticated from <MAC 'SETUP-171A' [AN127]> (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
[38523.674759] wlp2s0: authenticate with <MAC 'SETUP-171A' [AN127]>
[38523.696636] wlp2s0: send auth to <MAC 'SETUP-171A' [AN127]> (try 1/3)
[38523.704188] wlp2s0: send auth to <MAC 'SETUP-171A' [AN127]> (try 2/3)
[38523.708594] wlp2s0: authenticated
[38523.711553] wlp2s0: associate with <MAC 'SETUP-171A' [AN127]> (try 1/3)
[38523.724657] wlp2s0: associate with <MAC 'SETUP-171A' [AN127]> (try 2/3)
[38523.730436] wlp2s0: RX AssocResp from <MAC 'SETUP-171A' [AN127]> (capab=0x1411 status=0 aid=2)
[38523.759036] wlp2s0: associated
[38523.760304] wlp2s0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC 'SETUP-171A' [AN127]>
[38532.108017] wlp2s0: deauthenticated from <MAC 'SETUP-171A' [AN127]> (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[38532.247759] wlp2s0: authenticate with <MAC 'SETUP-171A' [AN127]>
[38532.280363] wlp2s0: send auth to <MAC 'SETUP-171A' [AN127]> (try 1/3)
[38532.287945] wlp2s0: authenticated
[38532.291339] wlp2s0: associate with <MAC 'SETUP-171A' [AN127]> (try 1/3)
[38532.314722] wlp2s0: RX AssocResp from <MAC 'SETUP-171A' [AN127]> (capab=0x1411 status=0 aid=2)
[38532.343241] wlp2s0: associated
[38532.358942] wlp2s0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC 'SETUP-171A' [AN127]>
[38568.899499] wlp2s0: deauthenticating from <MAC 'SETUP-171A' [AN127]> by local choice (Reason: 3=DEAUTH_LEAVING)
[38569.386755] wlp2s0: Connection to AP <MAC address> lost
[38585.808169] wlp2s0: authenticate with <MAC 'SETUP-171A' [AN127]>
[38585.828341] wlp2s0: send auth to <MAC 'SETUP-171A' [AN127]> (try 1/3)
[38585.938411] wlp2s0: send auth to <MAC 'SETUP-171A' [AN127]> (try 2/3)
[38585.966077] wlp2s0: authenticated
[38585.968880] wlp2s0: associate with <MAC 'SETUP-171A' [AN127]> (try 1/3)
[38585.990045] wlp2s0: RX AssocResp from <MAC 'SETUP-171A' [AN127]> (capab=0x1411 status=0 aid=2)
[38586.019647] wlp2s0: associated
[38586.118909] wlp2s0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC 'SETUP-171A' [AN127]>
[39251.310460] wlp2s0: Connection to AP <MAC 'SETUP-171A' [AN127]> lost
[39255.228342] wlp2s0: authenticate with <MAC 'SETUP-171A' [AN127]>
[39255.248373] wlp2s0: send auth to <MAC 'SETUP-171A' [AN127]> (try 1/3)
[39255.254337] wlp2s0: authenticated
[39255.255413] wlp2s0: associate with <MAC 'SETUP-171A' [AN127]> (try 1/3)
[39255.271191] wlp2s0: RX AssocResp from <MAC 'SETUP-171A' [AN127]> (capab=0x1411 status=0 aid=2)
[39255.305997] wlp2s0: associated
[39255.306037] wlp2s0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC 'SETUP-171A' [AN127]>
[39523.497758] wlp2s0: Connection to AP <MAC 'SETUP-171A' [AN127]> lost
[39536.095012] wlp2s0: authenticate with <MAC 'SETUP-171A' [AN127]>
[39536.115206] wlp2s0: send auth to <MAC 'SETUP-171A' [AN127]> (try 1/3)
[39536.123664] wlp2s0: authenticated
[39536.124926] wlp2s0: associate with <MAC 'SETUP-171A' [AN127]> (try 1/3)
[39536.146300] wlp2s0: RX AssocResp from <MAC 'SETUP-171A' [AN127]> (capab=0x1411 status=0 aid=2)
[39536.179889] wlp2s0: associated
[39536.179922] wlp2s0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC 'SETUP-171A' [AN127]>
[39579.186735] wlp2s0: Connection to AP <MAC 'SETUP-171A' [AN127]> lost
[39583.065777] wlp2s0: authenticate with <MAC 'SETUP-171A' [AN127]>
[39583.085883] wlp2s0: send auth to <MAC 'SETUP-171A' [AN127]> (try 1/3)
[39583.093065] wlp2s0: authenticated
[39583.094823] wlp2s0: associate with <MAC 'SETUP-171A' [AN127]> (try 1/3)
[39583.113425] wlp2s0: RX AssocResp from <MAC 'SETUP-171A' [AN127]> (capab=0x1411 status=0 aid=2)
[39583.142677] wlp2s0: associated
[39583.221333] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[39583.248973] wlp2s0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC 'SETUP-171A' [AN127]>
[39851.815198] wlp2s0: deauthenticating from <MAC 'SETUP-171A' [AN127]> by local choice (Reason: 3=DEAUTH_LEAVING)
[39858.372726] wlp2s0: authenticate with <MAC 'SETUP-171A' [AN127]>
[39858.392959] wlp2s0: send auth to <MAC 'SETUP-171A' [AN127]> (try 1/3)
[39858.397583] wlp2s0: authenticated
[39858.399687] wlp2s0: associate with <MAC 'SETUP-171A' [AN127]> (try 1/3)
[39858.415297] wlp2s0: associate with <MAC 'SETUP-171A' [AN127]> (try 2/3)
[39858.420319] wlp2s0: RX AssocResp from <MAC 'SETUP-171A' [AN127]> (capab=0x1411 status=0 aid=2)
[39858.449259] wlp2s0: associated
[39858.510668] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[39858.633003] wlp2s0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC 'SETUP-171A' [AN127]>
[39885.882817] wlp2s0: Connection to AP <MAC 'SETUP-171A' [AN127]> lost
[39889.743763] wlp2s0: authenticate with <MAC 'SETUP-171A' [AN127]>
[39889.767755] wlp2s0: send auth to <MAC 'SETUP-171A' [AN127]> (try 1/3)
[39889.776504] wlp2s0: send auth to <MAC 'SETUP-171A' [AN127]> (try 2/3)
[39889.784187] wlp2s0: send auth to <MAC 'SETUP-171A' [AN127]> (try 3/3)
[39889.792320] wlp2s0: authentication with <MAC 'SETUP-171A' [AN127]> timed out
[39894.078830] wlp2s0: authenticate with <MAC 'SETUP-171A' [AN122]>
[39894.098136] wlp2s0: send auth to <MAC 'SETUP-171A' [AN122]> (try 1/3)
[39894.104379] wlp2s0: authenticated
[39894.106379] wlp2s0: associate with <MAC 'SETUP-171A' [AN122]> (try 1/3)
[39894.118697] wlp2s0: associate with <MAC 'SETUP-171A' [AN122]> (try 2/3)
[39894.128955] wlp2s0: associate with <MAC 'SETUP-171A' [AN122]> (try 3/3)
[39894.130619] wlp2s0: RX AssocResp from <MAC 'SETUP-171A' [AN122]> (capab=0x1431 status=0 aid=2)
[39894.162084] wlp2s0: associated
[39894.182471] wlp2s0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC 'SETUP-171A' [AN122]>
[39898.158395] wlp2s0: deauthenticated from <MAC 'SETUP-171A' [AN122]> (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
[39911.965518] wlp2s0: authenticate with <MAC 'SETUP-171A' [AN127]>
[39911.991123] wlp2s0: send auth to <MAC 'SETUP-171A' [AN127]> (try 1/3)
[39911.995980] wlp2s0: send auth to <MAC 'SETUP-171A' [AN127]> (try 2/3)
[39912.000319] wlp2s0: send auth to <MAC 'SETUP-171A' [AN127]> (try 3/3)
[39912.006874] wlp2s0: authentication with <MAC 'SETUP-171A' [AN127]> timed out
[39925.988498] wlp2s0: authenticate with <MAC 'SETUP-171A' [AN127]>
[39926.008908] wlp2s0: send auth to <MAC 'SETUP-171A' [AN127]> (try 1/3)
[39926.016667] wlp2s0: authenticated
[39926.017209] wlp2s0: associate with <MAC 'SETUP-171A' [AN127]> (try 1/3)
[39926.034031] wlp2s0: RX AssocResp from <MAC 'SETUP-171A' [AN127]> (capab=0x1411 status=0 aid=2)
[39926.067093] wlp2s0: associated
[39926.113390] wlp2s0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC 'SETUP-171A' [AN127]>
[39933.816538] wlp2s0: deauthenticating from <MAC 'SETUP-171A' [AN127]> by local choice (Reason: 3=DEAUTH_LEAVING)


########## wireless info END ############
```

---

### Post by chili555 on 2023-12-06
We notice in your wireless_info that, of the SSIDs listed, the one you are attempting to connect to, SETUP-171A, isn’t even listed. Although some 15 are listed, ordered apparently by signal strength, yours isn’t listed.

In *dmesg* we see lots of:

```
wlp2s0: Connection to AP <MAC address> lost
wlp2s0: authentication with <MAC 'SETUP-171A' [AN127]> timed out
wlp2s0: deauthenticated from <MAC 'SETUP-171A' [AN122]> (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
```

This suggests two things, without knowing more details; either a signal strength issue, i.e., you are trying to connect to an access point that is on the next street, or else, the channel to which you connected suddenly changed because the access point is set to use auto-channel select. I recommend a fixed channel.

Please try again:

```
nmcli device wifi list
```

Try to capture the details of SETUP-171A and post them so we may further troubleshoot.

---

### Post by asimovjr on 2023-12-06
I had intentionally delete that from the text file since the list was so long and all those wifi networks were never used. SETUP - 171A is my personal wifi.
I noticed a trend when I used the commnad "sudo systemctl restart/start NetworkManager" the wifi would start for a minute or so. As if it's being turned off via power management.
I found and did "sudo nano /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf",  changed the setting to 2 from  3 as suggested in this post "https://askubuntu.com/questions/1403773/22-04-wifi-keeps-disconnecting-for-a-few-seconds-frequently"
Rebooted two- three times, wifi was still shaky, started my laptop this morning and now my wifi is stable for now, and the continous error I was getting every 5 mins "network manager activation failed for connection" is gone.

To follow your instructions, I will also add the my current nmcli list

---

### Post by chili555 on 2023-12-06
Your access point has a 2.4 gHz segment, on channel 1 and a 5 gHz segment on channel 44.

Your wireless may be dropping because there are two wireless access points with the same name and password. This is typical when you have a 2.4 gHz segment and a 5 gHz segment of the same router. Your wireless may be roaming, looking for a better connection. If this is the case, I suggest that you rename the access points; something like SETUP-171A2 and SETUP-171A5.

After making these changes, reboot the router.

If renaming is not feasible, then bind Network Manager to the 5 gHz segment like this: [https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)

The MAC address of the 5 gHz segment will be different from the 2.4 gHz segment.

---

### Post by jeremy31 on 2023-12-06
I think part of the problem is that it is reporting a TX power of 3 dBm and that isn't much.  I tried one of these devices in the past and they weren't up to par with my Intel wifi chips, even in Windows the Mediatek was poor.  I patched the source code multiple times and tried to make it work better with whatever kernel I had then, it worked a little better with power management off but I couldn't increase the TX power

---

