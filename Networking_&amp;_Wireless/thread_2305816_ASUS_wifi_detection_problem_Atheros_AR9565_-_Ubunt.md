---
title: "ASUS wifi detection problem Atheros AR9565 - Ubuntu 15.10"
date: 2015-12-09
forum: Networking &amp; Wireless
---

### Post by arn02 on 2015-12-09
Hello everybody,

Sorry for my bad English, I'm French...;)

I have a Asus with Windows 10 pre-installed and  wifi card ATHEROS AR9565.
So i deleted windows 10 and install Ubuntu 15.10, everything is ok except the wifi connection: wifi card seems to be detected but i don't see networks.
Since this morning i have tried a lot of solutions (from this forum) but nothing fix it.
So finally i post here my script wireless info if anybody has an idea ?

Thanks you, i'm starting to be crazy !! :-)

```




########## wireless info START ##########


Report from: 09 Dec 2015 18:17 CET +0100


Booted last: 09 Dec 2015 00:00 CET +0100


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily


##### kernel ############################


Linux 4.2.0-19-generic #23-Ubuntu SMP Wed Nov 11 11:39:30 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, noprompt, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169


03:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: AzureWave Device [1a3b:213a]
    Kernel driver in use: ath9k


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 006: ID 13d3:3423 IMC Networks 
Bus 001 Device 003: ID 04f2:b483 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 04b3:3107 IBM Corp. ThinkPad 800dpi Optical Travel Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


ath3k                  20480  0
asus_nb_wmi            24576  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
bluetooth             516096  30 bnep,ath3k,btbcm,btrtl,btusb,rfcomm,btintel
ath9k                  98304  0
ath9k_common           36864  1 ath9k
ath9k_hw              450560  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              643072  1 ath9k
cfg80211              540672  4 ath,ath9k_common,ath9k,mac80211
compat                 16384  4 cfg80211,ath9k_common,ath9k,mac80211
wmi                    20480  1 asus_wmi
video                  36864  2 i915,asus_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF]>  
          inet addr:192.168.0.20  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enp2s0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7182 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6778 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5121443 (5.1 MB)  TX bytes:1036089 (1.0 MB)


wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


enp2s0    no wireless extensions.


lo        no wireless extensions.


wlp3s0    IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp2s0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       627     1  0 17:53 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Connexion filaire 1
GENERAL.CON-UUID:                       23652068-3671-4b8c-8d2f-1beb2c71cd21
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   23652068-3671-4b8c-8d2f-1beb2c71cd21 | Connexion filaire 1
IP4.ADDRESS[1]:                         192.168.0.20/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             89.2.0.1
IP4.DNS[2]:                             89.2.0.2
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_interface_mtu = 1
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_time_offset = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        default_ip_ttl = 64
DHCP4.OPTION[8]:                        time_offset = 0
DHCP4.OPTION[9]:                        expiry = 1449766605
DHCP4.OPTION[10]:                       requested_wpad = 1
DHCP4.OPTION[11]:                       next_server = 192.168.0.1
DHCP4.OPTION[12]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       requested_domain_name = 1
DHCP4.OPTION[16]:                       routers = 192.168.0.1
DHCP4.OPTION[17]:                       ip_address = 192.168.0.20
DHCP4.OPTION[18]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[19]:                       requested_static_routes = 1
DHCP4.OPTION[20]:                       dhcp_lease_time = 86400
DHCP4.OPTION[21]:                       domain_name_servers = 89.2.0.1 89.2.0.2
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_ntp_servers = 1
DHCP4.OPTION[26]:                       requested_domain_name_servers = 1
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       network_number = 192.168.0.0
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::<IP6 'enp2s0' [IF]>/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA9565 / AR9565 Wireless Network Adapter
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.2.0-19-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   1878e266-8bfe-4fc8-b332-0e26cc8b90fd | ArnaudHelene


SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 


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


[[/etc/NetworkManager/system-connections/ArnaudHelene]] (600 root)
[connection] id=ArnaudHelene | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF]> | mac-address-blacklist= | ssid=ArnaudHelene
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Paris (based on set time zone)


country GB: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


enp2s0    no frequency information.


lo        no frequency information.


wlp3s0    13 channels in total; available frequencies :
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


wlp3s0    No scan results


##### module infos ######################


[ath3k]
filename:       /lib/modules/4.2.0-19-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     BC24BEB84AA8FE42E66C237
depends:        bluetooth
intree:         Y
vermagic:       4.2.0-19-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        36:C9:DD:EE:C2:96:8B:FC:DA:67:40:D7:CD:68:4B:F0:4B:70:27:94
sig_hashalgo:   sha512


[ath9k]
filename:       /lib/modules/4.2.0-19-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko
version:        backported from Linux (v4.2.6-0-g1c02865) using backports v4.2.6-1-0-g90118c7
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     675E95FA0F6C91239BA048A
depends:        ath9k_hw,mac80211,ath9k_common,compat,cfg80211,ath
vermagic:       4.2.0-19-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


[ath9k_common]
filename:       /lib/modules/4.2.0-19-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_common.ko
version:        backported from Linux (v4.2.6-0-g1c02865) using backports v4.2.6-1-0-g90118c7
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     A74E731B7BC6CD66D4D716C
depends:        compat,ath9k_hw,cfg80211,ath
vermagic:       4.2.0-19-generic SMP mod_unload modversions 


[ath9k_hw]
filename:       /lib/modules/4.2.0-19-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     C845437C8D63BBFD402A15D
depends:        ath
vermagic:       4.2.0-19-generic SMP mod_unload modversions 


[ath]
filename:       /lib/modules/4.2.0-19-generic/updates/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     728F9FA9D17C407477851D2
depends:        cfg80211
vermagic:       4.2.0-19-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.2.0-19-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (v4.2.6-0-g1c02865) using backports v4.2.6-1-0-g90118c7
srcversion:     0059B10CD5F6F6A14631DC4
depends:        cfg80211,compat
vermagic:       4.2.0-19-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.2.0-19-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (v4.2.6-0-g1c02865) using backports v4.2.6-1-0-g90118c7
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     6BE4ED42578C9DFBE16CE50
depends:        compat
vermagic:       4.2.0-19-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 1
ps_enable: 0


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/ath9k.conf]
options ath9k nohwcrypt=1


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


grep: /etc/udev/rules.d/*net*.rules: No such file or directory


##### dmesg #############################


[    8.944720] ath9k 0000:03:00.0 wlp3s0: renamed from wlan0
[   25.438446] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[   25.452184] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   25.539073] r8169 0000:02:00.0 enp2s0: link down
[   25.539115] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   25.634252] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 20 times)
[  194.929486] r8169 0000:02:00.0 enp2s0: link up
[  194.929493] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready


########## wireless info END ############



```

---

### Post by Hadaka on 2015-12-09
Hi, from a working wired connection please do..
```
sudo apt-get update
sudo apt-get dist-upgrade
```
your wireless report shows:
```
##### network managers ##################
Installed:
    NetworkManager
    Wicd
```
you can have one or the other but not both.

to totally remove networkmanager
```
sudo service network-manager stop
sudo apt-get remove network-manager-gnome network-manager
sudo dpkg --purge network-manager-gnome network-manager

```
to remove wcid
```
sudo apt-get remove wicd wicd-gtk
sudo dpkg --purge wicd wicd-gtk.
```
good luck

---

### Post by arn02 on 2015-12-09
thanks for your response.
i saw the double network managers and i removed wcid but same problem... :o
so i change my wireless report in my first post.

---

### Post by Hadaka on 2015-12-09
Hi,please re run the wireless info script
thanks

---

### Post by arn02 on 2015-12-10
hello,

Thanks Hadaka

Finally i have formated hard disk and installed Ubuntu 14.0.04.3 LTS.
Wifi is OK even if when i'm near the modem, i have a low signal (30-50%) ! Any idea ?

---

### Post by Hadaka on 2015-12-10
Hi, ,since you have loaded a new os, please
run and post the wireless script
thanks

---

### Post by arn02 on 2015-12-10
ok, new wireless script:
signal is low whereas i'm at 1m to modem !

```

########## wireless info START ##########

Report from: 10 Dec 2015 10:23 CET +0100

Booted last: 10 Dec 2015 10:14 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.3 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 3.19.0-39-generic #44~14.04.1-Ubuntu SMP Wed Dec 2 10:00:35 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, noprompt, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
	Kernel driver in use: r8169

03:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
	Subsystem: AzureWave Device [1a3b:213a]
	Kernel driver in use: ath9k

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 005: ID 13d3:3423 IMC Networks 
Bus 001 Device 002: ID 04f2:b483 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

asus_nb_wmi            24576  0 
asus_wmi               24576  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
ath9k                 147456  0 
ath9k_common           32768  1 ath9k
ath9k_hw              458752  2 ath9k_common,ath9k
ath3k                  20480  0 
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              708608  1 ath9k
video                  20480  2 i915_bpo,asus_wmi
cfg80211              524288  4 ath,ath9k_common,ath9k,mac80211
bluetooth             491520  23 bnep,ath3k,btusb,rfcomm
wmi                    20480  1 asus_wmi

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

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.15  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4169 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2793 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4348555 (4.3 MB)  TX bytes:379722 (379.7 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"ArnaudHelene"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: <MAC 'ArnaudHelene' [AC1]>   
          Bit Rate=26 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=36/70  Signal level=-74 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:59   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root       853     1  0 10:14 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [ArnaudHelene] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           26 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *ArnaudHelene:   Infra, <MAC 'ArnaudHelene' [AC1]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 45 WPA2

  IPv4 Settings:
    Address:         192.168.0.15
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             89.2.0.1
    DNS:             89.2.0.2

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

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

[[/etc/NetworkManager/system-connections/ArnaudHelene]] (600 root)
[connection] id=ArnaudHelene | type=802-11-wireless
[802-11-wireless] ssid=ArnaudHelene | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Paris (based on set time zone)

country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

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

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.452 GHz (Channel 9)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'ArnaudHelene' [AC1]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"ArnaudHelene"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000112a36d28
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath9k]
filename:       /lib/modules/3.19.0-39-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     DFC03DD607884E899C8398C
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.19.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:BC:4F:7D:1A:69:D3:75:88:1E:66:DF:A5:32:D0:F6:1E:AC:58:5E
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)

[ath9k_common]
filename:       /lib/modules/3.19.0-39-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     8836292C9539A29CB162A5D
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       3.19.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:BC:4F:7D:1A:69:D3:75:88:1E:66:DF:A5:32:D0:F6:1E:AC:58:5E
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.19.0-39-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     C1A24C37619ED65AB1240B9
depends:        ath
intree:         Y
vermagic:       3.19.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:BC:4F:7D:1A:69:D3:75:88:1E:66:DF:A5:32:D0:F6:1E:AC:58:5E
sig_hashalgo:   sha512

[ath3k]
filename:       /lib/modules/3.19.0-39-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     C77B8A018F5C738ABC4CA47
depends:        bluetooth
intree:         Y
vermagic:       3.19.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:BC:4F:7D:1A:69:D3:75:88:1E:66:DF:A5:32:D0:F6:1E:AC:58:5E
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.19.0-39-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     D89F916A5E804AF040C4D29
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:BC:4F:7D:1A:69:D3:75:88:1E:66:DF:A5:32:D0:F6:1E:AC:58:5E
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.19.0-39-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     47672A7084D52DFBE51E2D2
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:BC:4F:7D:1A:69:D3:75:88:1E:66:DF:A5:32:D0:F6:1E:AC:58:5E
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-39-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:BC:4F:7D:1A:69:D3:75:88:1E:66:DF:A5:32:D0:F6:1E:AC:58:5E
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
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
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

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

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0036 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   22.526018] wlan0: authenticate with <MAC 'ArnaudHelene' [AC1]>
[   22.538483] wlan0: send auth to <MAC 'ArnaudHelene' [AC1]> (try 1/3)
[   22.540425] wlan0: authenticated
[   22.544024] wlan0: associate with <MAC 'ArnaudHelene' [AC1]> (try 1/3)
[   22.547893] wlan0: RX AssocResp from <MAC 'ArnaudHelene' [AC1]> (capab=0x1411 status=0 aid=2)
[   22.548013] wlan0: associated
[   22.548034] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  192.006677] wlan0: deauthenticating from <MAC 'ArnaudHelene' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  192.949675] wlan0: authenticate with <MAC 'ArnaudHelene' [AC1]>
[  192.967890] wlan0: send auth to <MAC 'ArnaudHelene' [AC1]> (try 1/3)
[  192.969850] wlan0: authenticated
[  192.973197] wlan0: associate with <MAC 'ArnaudHelene' [AC1]> (try 1/3)
[  192.977181] wlan0: RX AssocResp from <MAC 'ArnaudHelene' [AC1]> (capab=0x1411 status=0 aid=2)
[  192.977284] wlan0: associated
[  334.720443] wlan0: deauthenticating from <MAC 'ArnaudHelene' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  335.651287] wlan0: authenticate with <MAC 'ArnaudHelene' [AC1]>
[  335.669567] wlan0: send auth to <MAC 'ArnaudHelene' [AC1]> (try 1/3)
[  335.671606] wlan0: authenticated
[  335.674596] wlan0: associate with <MAC 'ArnaudHelene' [AC1]> (try 1/3)
[  335.678543] wlan0: RX AssocResp from <MAC 'ArnaudHelene' [AC1]> (capab=0x1411 status=0 aid=2)
[  335.678651] wlan0: associated
[  335.708675] wlan0: deauthenticating from <MAC 'ArnaudHelene' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  336.562175] wlan0: authenticate with <MAC 'ArnaudHelene' [AC1]>
[  336.580603] wlan0: send auth to <MAC 'ArnaudHelene' [AC1]> (try 1/3)
[  336.585040] wlan0: authenticated
[  336.585872] wlan0: associate with <MAC 'ArnaudHelene' [AC1]> (try 1/3)
[  336.589844] wlan0: RX AssocResp from <MAC 'ArnaudHelene' [AC1]> (capab=0x1411 status=0 aid=2)
[  336.589949] wlan0: associated
[  336.620523] wlan0: deauthenticating from <MAC 'ArnaudHelene' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[  336.629138] wlan0: authenticate with <MAC 'ArnaudHelene' [AC1]>
[  336.641640] wlan0: send auth to <MAC 'ArnaudHelene' [AC1]> (try 1/3)
[  336.643622] wlan0: authenticated
[  336.645840] wlan0: associate with <MAC 'ArnaudHelene' [AC1]> (try 1/3)
[  336.649817] wlan0: RX AssocResp from <MAC 'ArnaudHelene' [AC1]> (capab=0x1411 status=0 aid=2)
[  336.649916] wlan0: associated

########## wireless info END ############

```

---

### Post by Hadaka on 2015-12-10
Hi , please open a terminal then COPY and paste..
```
echo "options ath9k nohwcrypt=1"  | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv asus_wmi
sudo modprobe -rfv ath9k
sudo modprobe ath9k
```
then do..
```
sudo iw reg set FR
sudo sed -i 's/^REG.*=$/&FR/' /etc/default/crda
```
then please access your router configuration in the router
and try channel 1,6 or 11  you are currently on channel 9
also check the antenna connections on your router and if possible
on your wifi card
thanks.

---

### Post by arn02 on 2015-12-11
thanks hadaka but no changement.
and before i have channel 1 and i test channel 9 but nothing.
and i return to channel 1...nothing.

maybe the model of wifi card (AR9565) is not very good ?
or it's an Ubuntu problem ? :confused:

---

### Post by Hadaka on 2015-12-12
Hi, let's try to update the driver, Please open a terminal ctrl/alt/t  then
please COPY and paste 's'il vous plaît copier et coller' one line at a time.

1) Download backports package from here - click SAVE
  [URL="https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.3/backports-4.3-1.tar.gz"]https://www.kernel.org/pub/linux/ker...s-4.3-1.tar.gz
[/URL]
2) Drag and drop from Downloads the  package to your Ubuntu Desktop > Right-click > Extract here.
....Downlods >>> Desktop

3) Open a terminal, COPY and paste 's'il vous plaît copier et coller' one line at a time.

```

sudo apt-get install --reinstall linux-headers-generic build-essential
cd Desktop/backports-4.3-1
make defconfig-ath9k
make
sudo make install
```
4) Reboot to load the new driver
```

sudo modprobe -rf ath9k
sudo modprobe -v ath9k
```
Then do.
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get autoremove
sudo apt-get autoclean
```

---

### Post by arn02 on 2016-01-04
hello,

Thanks hadaka and sorry for the delay, i was in holidays without my computer !

i test your solution but no changement and even a bad changement: my wifi is down. 
Before i could connect nearly to the modem (>1m) but now i couldn't connect to anything (only with cable RJ45).
And when i'm start ubuntu and arrive on the Desktop i've a windows "You have been disconnected to the wifi"

What can i make ? I'm lost...

My new wireless script:

```

########## wireless info START ##########

Report from: 04 Jan 2016 11:24 CET +0100

Booted last: 04 Jan 2016 11:03 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.3 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 3.19.0-42-generic #48~14.04.1-Ubuntu SMP Fri Dec 18 10:24:49 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, noprompt, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
	Kernel driver in use: r8169

03:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
	Subsystem: AzureWave Device [1a3b:213a]
	Kernel driver in use: ath9k

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 005: ID 13d3:3423 IMC Networks 
Bus 001 Device 002: ID 04f2:b483 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

asus_nb_wmi            24576  0 
asus_wmi               24576  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
ath9k                 147456  0 
ath9k_common           32768  1 ath9k
ath9k_hw              458752  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              708608  1 ath9k
ath3k                  20480  0 
bluetooth             491520  23 bnep,ath3k,btusb,rfcomm
cfg80211              524288  4 ath,ath9k_common,ath9k,mac80211
wmi                    20480  1 asus_wmi
video                  20480  2 i915_bpo,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.20  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9396 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8001 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8433089 (8.4 MB)  TX bytes:1010723 (1.0 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root       834     1  0 11:03 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Connexion filaire 1] ------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.20
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             89.2.0.1
    DNS:             89.2.0.2

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

[[/etc/NetworkManager/system-connections/Livebox-6AD0]] (600 root)
[connection] id=Livebox-6AD0 | type=802-11-wireless
[802-11-wireless] ssid=Livebox-6AD0 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=802-11-wireless
[802-11-wireless] ssid=AndroidAP | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ArnaudHelene]] (600 root)
[connection] id=ArnaudHelene | type=802-11-wireless
[802-11-wireless] ssid=ArnaudHelene | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Paris (based on set time zone)

country FR:
	(2402 - 2482 @ 40), (N/A, 20)
	(5170 - 5250 @ 40), (N/A, 20)
	(5250 - 5330 @ 40), (N/A, 20), DFS
	(5490 - 5710 @ 40), (N/A, 27), DFS
	(57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels ###################

eth0      no frequency information.

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

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     No scan results

##### module infos ######################

[ath9k]
filename:       /lib/modules/3.19.0-42-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     41D979FB10C5D31B45EF47A
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.19.0-42-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        75:9B:CD:64:55:A9:DF:AB:A6:11:14:85:D0:4E:DE:D5:3A:B8:31:50
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)

[ath9k_common]
filename:       /lib/modules/3.19.0-42-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     8836292C9539A29CB162A5D
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       3.19.0-42-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        75:9B:CD:64:55:A9:DF:AB:A6:11:14:85:D0:4E:DE:D5:3A:B8:31:50
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.19.0-42-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     C1A24C37619ED65AB1240B9
depends:        ath
intree:         Y
vermagic:       3.19.0-42-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        75:9B:CD:64:55:A9:DF:AB:A6:11:14:85:D0:4E:DE:D5:3A:B8:31:50
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.19.0-42-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     D89F916A5E804AF040C4D29
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-42-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        75:9B:CD:64:55:A9:DF:AB:A6:11:14:85:D0:4E:DE:D5:3A:B8:31:50
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.19.0-42-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     47672A7084D52DFBE51E2D2
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-42-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        75:9B:CD:64:55:A9:DF:AB:A6:11:14:85:D0:4E:DE:D5:3A:B8:31:50
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[ath3k]
filename:       /lib/modules/3.19.0-42-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     C77B8A018F5C738ABC4CA47
depends:        bluetooth
intree:         Y
vermagic:       3.19.0-42-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        75:9B:CD:64:55:A9:DF:AB:A6:11:14:85:D0:4E:DE:D5:3A:B8:31:50
sig_hashalgo:   sha512

[cfg80211]
filename:       /lib/modules/3.19.0-42-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-42-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        75:9B:CD:64:55:A9:DF:AB:A6:11:14:85:D0:4E:DE:D5:3A:B8:31:50
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 1
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
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/ath9k.conf]
options ath9k nohwcrypt=1

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

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0036 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   16.695568] r8169 0000:02:00.0 eth0: link down
[   16.695615] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.709627] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  239.092304] r8169 0000:02:00.0 eth0: link up
[  239.092321] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  264.530841] r8169 0000:02:00.0 eth0: link down (repeated 2 times)
[  312.311972] r8169 0000:02:00.0 eth0: link up

########## wireless info END ############

```

---

### Post by Hadaka on 2016-01-04
Hi please do..
```
sudo modprobe -rf ath9k
sudo modprobe -vv ath9k
```
```
dmesg | grep ath
```
post the results please
thanks.

---

### Post by arn02 on 2016-01-04
ok i test:

(note: when i leave sleeping mode, i have the message "you are now disconnected to wifi conection" , like when i start ubuntu)

```
arnaud@arnaud-portable:~$ dmesg | grep ath[    0.513760] Loaded X.509 cert 'Magrathea: Glacier signing key: 759bcd6455a9dfaba6111485d04eded53ab83150'
[   11.273482] ath: phy0: WB335 1-ANT card detected
[   11.273484] ath: phy0: Set BT/WLAN RX diversity capability
[   11.282250] ath: phy0: Enable LNA combining
[   11.283504] ath: phy0: ASPM enabled: 0x43
[   11.283506] ath: EEPROM regdomain: 0x6a
[   11.283508] ath: EEPROM indicates we should expect a direct regpair map
[   11.283511] ath: Country alpha2 being used: 00
[   11.283512] ath: Regpair used: 0x6a
[   11.879823] usbcore: registered new interface driver ath3k
[ 2093.791184] Modules linked in: rtsx_usb_ms rtsx_usb_sdmmc memstick rtsx_usb bnep rfcomm nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common videodev media asus_nb_wmi asus_wmi sparse_keymap snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic intel_rapl iosf_mbi x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul arc4 aesni_intel ath9k aes_x86_64 ath9k_common lrw gf128mul ath9k_hw glue_helper ablk_helper cryptd ath snd_hda_intel snd_hda_controller mac80211 snd_hda_codec snd_hwdep joydev snd_seq_midi serio_raw snd_seq_midi_event snd_pcm i915_bpo ath3k btusb bluetooth mei_me snd_rawmidi cfg80211 mei lpc_ich intel_ips snd_seq shpchp drm_kms_helper drm processor_thermal_device snd_seq_device snd_timer snd i2c_algo_bit wmi soundcore parport_pc ppdev dw_dmac snd_soc_sst_acpi dw_dmac_core lp parport i2c_designware_platform video int3402_thermal 8250_dw spi_pxa2xx_platform i2c_designware_core int3400_thermal acpi_thermal_rel acpi_pad mac_hid r8169 ahci psmouse libahci mii sdhci_acpi sdhci
[ 2093.791248]  [<ffffffff81074dea>] warn_slowpath_common+0x8a/0xc0
[ 2093.791250]  [<ffffffff81074e66>] warn_slowpath_fmt+0x46/0x50
[10386.359095] ath: phy0: ASPM enabled: 0x43
[10423.605750] ath9k: ath9k: Driver unloaded
[10445.123918] ath: phy0: WB335 1-ANT card detected
[10445.123921] ath: phy0: Set BT/WLAN RX diversity capability
[10445.132699] ath: phy0: Enable LNA combining
[10445.133944] ath: phy0: ASPM enabled: 0x43
[10445.133945] ath: EEPROM regdomain: 0x6a
[10445.133946] ath: EEPROM indicates we should expect a direct regpair map
[10445.133948] ath: Country alpha2 being used: 00
[10445.133948] ath: Regpair used: 0x6a





```

---

### Post by arn02 on 2016-01-04
now i can connect to my wifi router if i'm nearly (1 meter !). Like before.
But i can't move away.
It's crazy !

---

### Post by Hadaka on 2016-01-04
Hi,from a working wired connection please COPY
and paste one line at a time.
```
sudo iw reg set FR
sudo sed -i 's/^REG.*=$/&FR/' /etc/default/crda
```
then do..
```
echo "options ath9k btcoex_enable=1" | sudo tee-a /etc/modprobe.d/ath9k.conf
```
remove the wired connection,boot and test wireless. *Please read Note :
*Note1: If there is no improvement then do..
```
echo "options ath9k bt_ant_diversity=0" | sudo tee /etc/modprobe.d/ath9k.bt_ant.conf
```
*Note2: If still no improvement then do..
```
echo "options ath9k bt_ant_diversity=1" | sudo tee /etc/modprobe.d/ath9k.bt_ant.conf
```
thanks.

---

### Post by arn02 on 2016-01-05
hi hadaka and thanks to take your time :-)
i test your complete solution but nothing...

just one thing, this command tee-a was not found
```
echo "options ath9k btcoex_enable=1" | sudo [COLOR=#ff0000]tee-a[/COLOR] /etc/modprobe.d/ath9k.conf
```

so i make
```
echo "options ath9k btcoex_enable=1" | sudo [COLOR=#ff0000]tee[/COLOR] /etc/modprobe.d/ath9k.conf
```

is it ok ?

which kind of problem is it ?
 i don't understand and i'm disappointed from ubuntu whereas i have never had problem like this... :-p

what do you think about a complete format and reinstall of ubuntu ? which version i can install? 14.04 LTS ?

---

### Post by Hadaka on 2016-01-05
Hi that was a typo on my part,sorry about that.
the -a means to append the file, no -a and a new file is written and any data
that was in the file is over written. So let's rebuild it. Please copy and paste..
```
sudo modprobe -rfv ath9k
#create a new file
echo "options ath9k nohwcrypt=1" | sudo tee  /etc/modprobe.d/ath9k.conf
#append the file
echo "options ath9k btcoex_enable=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -v ath9k
```
thanks.

---

### Post by arn02 on 2016-01-06
I test it but nothing.
I have a signal but very low, i should be near my modem !

What do you think about a complete format + reinstall of Ubuntu ?
i have not other ideas...and you ? :-p

---

