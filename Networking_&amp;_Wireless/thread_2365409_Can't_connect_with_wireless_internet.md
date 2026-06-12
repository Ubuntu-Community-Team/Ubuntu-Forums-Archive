---
title: "Can't connect with wireless internet"
date: 2017-07-06
forum: Networking &amp; Wireless
---

### Post by nikuchakopaliani on 2017-07-06
Hello, my problem is that I can connect to the internet only with wired connection. Here are two screenshots... Wireless connections are visible in system settings module, but only there(not in "active connections", and in fact I can't use them.
[IMG]file:///home/user-12/Pictures/Screenshot_20170706_194940.png[/IMG]
[IMG][IMG]file:///home/user-12/Pictures/Screenshot_20170706_194940.png[/IMG][/IMG]
recently I have a problem with updates and I corrected it with the simple command ([COLOR=#545454][FONT=arial]'[/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**sudo dpkg**[/FONT][/COLOR][COLOR=#545454][FONT=arial] --configure -a' )[/FONT][/COLOR] in terminal... also installed GSshutdown and deleted then because this problem appeared whether reason was GSshutdown... I don't know. 
kubuntu 17.04 user

---

### Post by slickymaster on 2017-07-06
Thread moved to **Networking & Wireless** for a better fit.

Please have a read at [this sticky]("https://ubuntuforums.org/showthread.php?t=370108") and perform accordingly

---

### Post by nikuchakopaliani on 2017-07-06
probably, I have another problem...

---

### Post by nikuchakopaliani on 2017-07-06
I tried but it doesn't work for me.

---

### Post by slickymaster on 2017-07-06
> **nikuchakopaliani said:**
> I tried but it doesn't work for me.

What exactly didn't work?

---

### Post by nikuchakopaliani on 2017-07-06
Nothing changed. I don't know what is the problem of this. Have you seen my screenshots?

Sorry for unknowledge... I'm new in linux.:confused:

I don't want to confuse but I need help.

---

### Post by jeremy31 on 2017-07-06
Do you have a wireless-info.txt file in your home folder?  You can upload your screenshots as attachments in advanced reply

---

### Post by nikuchakopaliani on 2017-07-06
&#1090;&#1093;&#1080;&#1089;

---

### Post by nikuchakopaliani on 2017-07-06
info below

---

### Post by nikuchakopaliani on 2017-07-06
yes, I have... ```
######### wireless info START ##########

Report from: 06 Jul 2017 20:24 +04 +0400


Booted last: 06 Jul 2017 00:00 +04 +0400


Script from: 25 Mar 2017 07:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 17.04
Release:	17.04
Codename:	zesty


##### kernel ############################


Linux 4.10.0-26-generic #30-Ubuntu SMP Tue Jun 27 09:30:12 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


/usr/share/xsessions/plasma


##### lspci #############################


04:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Fujitsu Limited. AR9285 Wireless Network Adapter (PCI-Express) [10cf:1537]
	Kernel driver in use: ath9k


08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Fujitsu Limited. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10cf:15b1]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05c8:030e Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes


##### lsmod #############################


ath9k                 147456  0
ath9k_common           36864  1 ath9k
ath9k_hw              466944  2 ath9k,ath9k_common
ath                    28672  3 ath9k_hw,ath9k,ath9k_common
mac80211              782336  1 ath9k
cfg80211              602112  4 mac80211,ath9k,ath,ath9k_common


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp8s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.2.104  netmask 255.255.255.0  broadcast 192.168.2.255
        inet6 fe80::9763:1c59:1be7:e2e2  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 42921  bytes 54965398 (54.9 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 30188  bytes 3548913 (3.5 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 458  bytes 33496 (33.4 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 458  bytes 33496 (33.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlp4s0: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


lo        no wireless extensions.


enp8s0    no wireless extensions.


wlp4s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 enp8s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp8s0
192.168.2.0     0.0.0.0         255.255.255.0   U     100    0        0 enp8s0


##### resolv.conf #######################


nameserver 127.0.0.53


##### network managers ##################


Installed:


	NetworkManager


Running:


root       891     1  0 19:28 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp8s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:08:00.0/net/enp8s0
GENERAL.IP-IFACE:                       enp8s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       40af2647-a98d-3d0d-9392-451ff50b9d4a
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/9
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{7}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   40af2647-a98d-3d0d-9392-451ff50b9d4a | Wired connection 1
IP4.ADDRESS[1]:                         192.168.2.104/24
IP4.GATEWAY:                            192.168.2.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.2.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1499365419
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 7200
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.2.104
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.2.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.2.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.2.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.2.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.2.1
IP6.ADDRESS[1]:                         fe80::9763:1c59:1be7:e2e2/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlp4s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR9285 Wireless Network Adapter (PCI-Express)
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.10.0-26-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:04:00.0/net/wlp4s0
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
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/TP-LINK_AB4CB6]] (600 root)
[connection] id=TP-LINK_AB4CB6 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=TP-LINK_AB4CB6
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Nik-d436d867-8643-47f9-96ef-fbaa867fd9e1]] (600 root)
[connection] id=Nik | type=wifi | permissions=user:user-12:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Nik
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/TP-LINK_AB4CB6-a5942125-9f15-4da6-96df-a8661519f345]] (600 root)
[connection] id=TP-LINK_AB4CB6 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=TP-LINK_AB4CB6
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Silknet-757561]] (600 root)
[connection] id=Silknet-757561 | type=wifi | permissions=user:user-12:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Silknet-757561
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/TP-LINK_AB4CB6-a1040494-ad56-4423-8c1c-d0350c0b8873]] (600 root)
[connection] id=TP-LINK_AB4CB6 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=TP-LINK_AB4CB6
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Nik]] (600 root)
[connection] id=Nik | type=wifi | permissions=user:kubuntu:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Nik
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Asia/Tbilisi (based on set time zone)


global
country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, NO-IR
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, NO-IR
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, NO-IR
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
	(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


lo        no frequency information.


enp8s0    no frequency information.


wlp4s0    13 channels in total; available frequencies :
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


wlp4s0    Interface doesn't support scanning : Network is down


lo        Interface doesn't support scanning.


enp8s0    Interface doesn't support scanning.


##### module infos ######################


[ath9k]
filename:       /lib/modules/4.10.0-26-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     FE068A212939D362AD12CBA
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       4.10.0-26-generic SMP mod_unload 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           led_active_high:Invert LED polarity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)


[ath9k_common]
filename:       /lib/modules/4.10.0-26-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     AAF3B58F80FF1BAC17759BC
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.10.0-26-generic SMP mod_unload 


[ath9k_hw]
filename:       /lib/modules/4.10.0-26-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     B69AC5BDB1497312F28332E
depends:        ath
intree:         Y
vermagic:       4.10.0-26-generic SMP mod_unload 


[ath]
filename:       /lib/modules/4.10.0-26-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     4B8612B6FF71DD27AE8CE67
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-26-generic SMP mod_unload 


[mac80211]
filename:       /lib/modules/4.10.0-26-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     309C9ACED540FCAA1DE7422
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-26-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.10.0-26-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D77C8F93375950F3BA95B16
depends:        
intree:         Y
vermagic:       4.10.0-26-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
led_active_high: -1
nohwcrypt: 0
ps_enable: 0
use_chanctx: 0


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


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   21.767850] ath: phy0: Enable LNA combining
[   21.770399] ath: phy0: ASPM enabled: 0x42
[   21.770404] ath: EEPROM regdomain: 0x6a
[   21.770405] ath: EEPROM indicates we should expect a direct regpair map
[   21.770407] ath: Country alpha2 being used: 00
[   21.770408] ath: Regpair used: 0x6a
[   21.969276] ath9k 0000:04:00.0 wlp4s0: renamed from wlan0
[   28.097377] IPv6: ADDRCONF(NETDEV_UP): wlp4s0: link is not ready


########## wireless info END ############
```

---

### Post by slickymaster on 2017-07-06
```
##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	[COLOR=#ff0000]Hard blocked: yes
```[/COLOR]
Your wifi is Hard Blocked. Look for a hardware switch in your computer and toggle it

---

### Post by nikuchakopaliani on 2017-07-06
I don't understand... What hardware switch is.

---

### Post by nikuchakopaliani on 2017-07-06
my fujitsu ah530 hasn'tphysical wifi on/off switch on the outside

---

### Post by nikuchakopaliani on 2017-07-06
my fujitsu ah530 hasn'tphysical wifi on/off switch on the outside

---

### Post by nikuchakopaliani on 2017-07-06
What should I do?

---

### Post by nikuchakopaliani on 2017-07-06
What should I do?

---

### Post by QIII on 2017-07-06
Posts from another thread merged here.

---

### Post by jeremy31 on 2017-07-06
Try a BIOS reset as this will sometimes clear a hard block, with some laptops you can shut them down, remove battery and power cord and press the power button for 20 seconds, reconnect battery and power cord and it will clear the hard block

---

### Post by nikuchakopaliani on 2017-07-06
> **jeremy31 said:**
> Try a BIOS reset as this will sometimes clear a hard block, with some laptops you can shut them down, r**emove battery and power cord and press the power button for 20 seconds, reconnect battery and power cord** and it will clear the hard block







 

 I don't know how, but I did what you had said and it's perfect! Thank you very much...
  It's very interesting for me how was it done ...

---

### Post by jeremy31 on 2017-07-06
I am not sure how it works as I am not familiar with BIOS coding, all I know is that it does work for some computers when we can't see anything else wrong

---

