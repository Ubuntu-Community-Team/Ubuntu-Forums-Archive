---
title: "Wifi extremely random"
date: 2016-10-14
forum: Networking &amp; Wireless
---

### Post by vs010203 on 2016-10-14
I have a Dell laptop with an extremely frustrating wireless issue. I have been having this issue for quite some time but finally ended up posting here. 

So, I have an extremely unpredictable wireless connection. Sometimes it works well for a few hours and then gets extremely slow suddenly. Pings would have extremely high packet loss. This problem does not occur with other android devices we use, so I don't think router is the problem. 

I upgraded to 16.04 yesterday which seemed to have not done anything. Then i removed and reinstalled the bcmwl-kernel-source package.

But there is absolutely no change in the issue. 



I am posing the output of the script here,

```



########## wireless info START ##########


Report from: 14 Oct 2016 15:16 IST +0530


Booted last: 14 Oct 2016 00:00 IST +0530


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-43-generic #63-Ubuntu SMP Wed Oct 12 13:48:03 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


06:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
	Kernel driver in use: wl


07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Dell RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [1028:0651]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 0a5c:21d7 Broadcom Corp. BCM43142 Bluetooth 4.0
Bus 001 Device 003: ID 0bda:5756 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: dell-rbtn: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
6: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no


##### lsmod #############################


wl                   6365184  0
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          212992  1 snd_soc_rt5640
dell_laptop            20480  0
dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
dcdbas                 16384  1 dell_laptop
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core
cfg80211              565248  1 wl
wmi                    20480  2 dell_led,dell_wmi
video                  40960  3 i915,dell_wmi,dell_laptop


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:192.168.0.17  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:319449 errors:0 dropped:0 overruns:0 frame:84124
          TX packets:212023 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:389151147 (389.1 MB)  TX bytes:26298980 (26.2 MB)
          Interrupt:18 


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


wlan0     IEEE 802.11abg  ESSID:"Tech_D0017775"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'Tech_D0017775' [AC1]>   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root      8030     1  0 15:10 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM43142 802.11b/g/n (Wireless 1704 802.11n + BT 4.0)
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.248 (r487574)
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlan0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:06:00.0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Tech_D0017775
GENERAL.CON-UUID:                       daed44a7-2634-406c-ae00-ce593d52eb86
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     13 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   daed44a7-2634-406c-ae00-ce593d52eb86 | Tech_D0017775
IP4.ADDRESS[1]:                         192.168.0.17/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             202.88.156.6
IP4.DNS[2]:                             202.88.156.8
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 202.88.156.6 202.88.156.8
DHCP4.OPTION[5]:                        ip_address = 192.168.0.17
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[8]:                        default_ip_ttl = 64
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       time_offset = 0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_rebinding_time = 529200
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       requested_broadcast_address = 1
DHCP4.OPTION[17]:                       routers = 192.168.0.1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 302400
DHCP4.OPTION[19]:                       requested_domain_name = 1
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1477042835
DHCP4.OPTION[22]:                       requested_wpad = 1
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 192.168.0.1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 604800
IP6.ADDRESS[1]:                         fe80::<IP6 'wlan0' [IF2]>/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               rtl8106e-1_0.0.1 06/29/12
GENERAL.HWADDR:                         <MAC 'eth0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:07:00.0/net/eth0
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


SSID           BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Tech_D0017775  <MAC 'Tech_D0017775' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  58      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     * 


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


no-auto-default=<MAC 'eth0' [IF1]>,


[ifupdown]
managed=false


##### NetworkManager profiles ###########


Sorry, try again.
Sorry, try again.
[[/etc/NetworkManager/system-connections/Nupur's iPhone]] (600 root)
[connection] id=Nupur's iPhone | type=802-11-wireless
[802-11-wireless] ssid=Nupur's iPhone | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/CLOUDNINE-WIFI]] (600 root)
[connection] id=CLOUDNINE-WIFI | type=802-11-wireless
[802-11-wireless] ssid=CLOUDNINE-WIFI | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Dev-Home]] (600 root)
[connection] id=Dev-Home | type=802-11-wireless
[802-11-wireless] ssid=Dev-Home | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Shifu 1]] (600 root)
[connection] id=Shifu 1 | type=802-11-wireless
[802-11-wireless] ssid=Shifu | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/appus]] (600 root)
[connection] id=appus | type=802-11-wireless
[802-11-wireless] ssid=appus | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ASUS]] (600 root)
[connection] id=ASUS | type=802-11-wireless
[802-11-wireless] ssid=ASUS | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Nupur-708]] (600 root)
[connection] id=Nupur-708 | type=802-11-wireless
[802-11-wireless] ssid=Nupur-708 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Shifu]] (600 root)
[connection] id=Shifu | type=802-11-wireless
[802-11-wireless] ssid=Shifu | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Tech_D0017775]] (600 root)
[connection] id=Tech_D0017775 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=Tech_D0017775
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/maheshmunet]] (600 root)
[connection] id=maheshmunet | type=802-11-wireless
[802-11-wireless] ssid=maheshmunet | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Asia/Kolkata (based on set time zone)


country DE: DFS-ETSI
	(2400 - 2483 @ 40), (N/A, 20), (N/A)
	(5150 - 5250 @ 80), (N/A, 20), (N/A), NO-OUTDOOR
	(5250 - 5350 @ 80), (N/A, 20), (0 ms), NO-OUTDOOR, DFS
	(5470 - 5725 @ 160), (N/A, 26), (0 ms), DFS
	(57000 - 66000 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


lo        no frequency information.


eth0      no frequency information.


wlan0     32 channels in total; available frequencies :
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
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
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
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Tech_D0017775' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"Tech_D0017775"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[wl]
filename:       /lib/modules/4.4.0-43-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     4DDC5FCDB1E30F7DFDCA530
depends:        cfg80211
vermagic:       4.4.0-43-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


[cfg80211]
filename:       /lib/modules/4.4.0-43-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-43-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp
lp


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma


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
blacklist acer
blacklist acer_wmi
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma
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


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:07:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4365 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x14e4:0x4365 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[ 8045.695191] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[ 8045.695194] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[ 8047.344451] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[ 8047.582227] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 8047.755827] r8169 0000:07:00.0 eth0: link down
[ 8047.755892] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[ 9537.366444] r8169 0000:07:00.0 eth0: link down
[ 9537.366501] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 9561.119689] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9561.123892] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 9561.296656] r8169 0000:07:00.0 eth0: link down
[ 9561.296752] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[ 9879.927786] r8169 0000:07:00.0 eth0: link down
[ 9879.927863] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[ 9896.878508] r8169 0000:07:00.0 eth0: link down
[ 9896.878564] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 9902.783266] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9902.787491] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 9902.957993] r8169 0000:07:00.0 eth0: link down
[ 9902.958099] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[10268.418443] ERROR @wl_dev_intvar_get : error (-1)


########## wireless info END ############



```

---

### Post by Hadaka on 2016-10-14
Hi, from a working wired connection open a terminal  ctrl/alt/t then
please copy and paste one line at a time.
```
sudo apt-get remove --purge bcmwl-kernel-source
```
Then..
```
sudo apt-get update
sudo apt-get install linux-headers-$(uname -r) build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-3_all.deb
sudo dpkg -i broadcom-sta-dkms_6.30.223.271-3_all.deb
```

 Power Management: is ON it needs to be OFF

*Please open your editor with this command..
```
sudo gedit /etc/network/if-up.d/off-power-manager
```
THen copy these two lines into the editor.
```
#!/bin/sh
/sbin/iwconfig wlan0 power off
```
Save and close gedit..editor

Set country code.
```
sudo iw reg set IN
sudo sed -i 's/^REG.*=$/&IN/' /etc/default/crda
```

Clean up this confused file. The system builds a new one on first boot.
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```

Then if possible please access your router configuration and change from
WPA2 TKIP  TO WPA2 CCMP    NO TKIP

remove wired connection boot and test wireless
Thanks

---

### Post by vs010203 on 2016-10-15
Hi Hadaka,

Thanks for the reply. 

I did all the steps except the last one since the router is from the cable company and I don't know how to get in.

For now everything is smooth, but the original problem was so random I don't even know how to test it to be sure. I'll just keep on testing. 

Another thing is I looked at this thread

[https://bbs.archlinux.org/viewtopic.php?id=193129&p=2](https://bbs.archlinux.org/viewtopic.php?id=193129&p=2)

Before trying out your changes I tried what was written in the last message.

```
 
ping -s 16000 192.168.1.1

```

That also seemed to make it smoother, but I could not understand why this would make a difference.

---

### Post by Hadaka on 2016-10-15
Hi, yeah a ping attack on the router 192.168.1.1 is not going to be a good fix for the issue.
There were 2 or 3 things from your last wireless report that were likely causing your drops.
Most notably updating the broadcom version. As was stated in post #39 of the link you attached.
"[COLOR=#333333][FONT=sans-serif]After long experience with  6.30.223.271-4 I must say the problem is no longer. "

this is the same version you just installed from my last post, hope it fixes your
problem.

thanks.[/FONT][/COLOR]

---

### Post by vs010203 on 2016-10-17
Based on testing for the last few days, I am marking this as solved. 

Thanks.

---

