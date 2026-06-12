---
title: "Fresh 15.04 install on Toshiba Satellite L455.  Unable to enable wireless"
date: 2015-05-30
forum: Networking &amp; Wireless
---

### Post by zach34 on 2015-05-30
This is a fresh install of Ubuntu 15.04... Not an upgrade.  I cannot enable wireless.  I open Settings->Network, click wireless, click the toggle to turn on and it reverts to off and will not turn on.  I thought maybe I did something wrong on the install, so I re-installed Ubuntu with the same result.

I've reset bios/system settings as suggested by other older threads and it did not fix the problem.  I ran the updates as suggested by the sticky thread and I've ran the info script.  I am still unable to enable my wireless.  It is hard blocked... Not soft blocked.  Shift+F8 does nothing.

Here are the results of the info script:
```


########## wireless info START ##########

Report from: 30 May 2015 17:55 MDT -0600

Booted last: 30 May 2015 17:52 MDT -0600

Script from: 21 May 2015 09:10 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 3.19.0-18-generic #18-Ubuntu SMP Tue May 19 18:30:59 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Toshiba America Info Systems Device [1179:ff00]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:8198 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

##### lsmod #############################

rtl8187                57344  0 
mac80211              626688  1 rtl8187
cfg80211              462848  2 mac80211,rtl8187
eeprom_93cx6           16384  1 rtl8187
wmi                    20480  1 toshiba_acpi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.120  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fd55:77c4:983d:0:725a:b6ff:fe89:1ac0/64 Scope:Global
          inet6 addr: 2601:282:c101:4491:cd2b:fbc0:8fef:79c6/64 Scope:Global
          inet6 addr: fe80::725a:b6ff:fe89:1ac0/64 Scope:Link
          inet6 addr: 2601:282:c101:4491:725a:b6ff:fe89:1ac0/64 Scope:Global
          inet6 addr: fd55:77c4:983d:0:cd2b:fbc0:8fef:79c6/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3347 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2320 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3463560 (3.4 MB)  TX bytes:322364 (322.3 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    1024   0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search hsd1.co.comcast.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root       593     1  0 17:53 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:0e:00.0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       587b045c-2983-49c9-85ca-b23dd619562b
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   587b045c-2983-49c9-85ca-b23dd619562b | Wired connection 1
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         ip = 192.168.1.120/24, gw = 192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             75.75.76.76
IP4.DNS[2]:                             75.75.75.75
IP4.DNS[3]:                             192.168.1.1
IP4.DOMAIN[1]:                          hsd1.co.comcast.net.
DHCP4.OPTION[1]:                        network_number = 192.168.1.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_time_offset = 1
DHCP4.OPTION[8]:                        expiry = 1433116388
DHCP4.OPTION[9]:                        domain_name = hsd1.co.comcast.net.
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.1.1
DHCP4.OPTION[15]:                       dhcp_lease_time = 86400
DHCP4.OPTION[16]:                       ip_address = 192.168.1.120
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       domain_name_servers = 75.75.76.76 75.75.75.75 192.168.1.1
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       requested_ntp_servers = 1
DHCP4.OPTION[27]:                       requested_netbios_scope = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         ip = 2601:282:c101:4491:cd2b:fbc0:8fef:79c6/64, gw = fe80::b675:eff:fec4:4df8
IP6.ADDRESS[2]:                         ip = fd55:77c4:983d:0:cd2b:fbc0:8fef:79c6/64, gw = fe80::b675:eff:fec4:4df8
IP6.ADDRESS[3]:                         ip = 2601:282:c101:4491:725a:b6ff:fe89:1ac0/64, gw = fe80::b675:eff:fec4:4df8
IP6.ADDRESS[4]:                         ip = fd55:77c4:983d:0:725a:b6ff:fe89:1ac0/64, gw = fe80::b675:eff:fec4:4df8
IP6.ADDRESS[5]:                         ip = fe80::725a:b6ff:fe89:1ac0/64, gw = fe80::b675:eff:fec4:4df8
IP6.ROUTE[1]:                           dst = 2601:282:c101:4491::/64, nh = ::, mt = 1
IP6.ROUTE[2]:                           dst = fd55:77c4:983d::/64, nh = ::, mt = 1
IP6.DNS[1]:                             2001:558:feed::2
IP6.DNS[2]:                             2001:558:feed::1
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:73:c1:7c:42:68:8:a4:60:e1:1:<MAC address>
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2001:558:feed::2 2001:558:feed::1
DHCP6.OPTION[3]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[4]:                        requested_dhcp6_server_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[6]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[7]:                        dhcp6_preference = 255
DHCP6.OPTION[8]:                        dhcp6_server_id = 0:3:0:1:b4:75:e:c4:4d:f8

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Manufacturer_Realtek
GENERAL.PRODUCT:                        8198
GENERAL.DRIVER:                         rtl8187
GENERAL.DRIVER-VERSION:                 3.19.0-18-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/net/wlan0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes

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

##### iw reg get ########################

Region: America/Denver (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20), (N/A)
    (2457 - 2482 @ 40), (3, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (3, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), (N/A), NO-IR
    (5735 - 5835 @ 40), (3, 20), (N/A), NO-IR

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

wlan0     14 channels in total; available frequencies :
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

##### iwlist scan #######################

wlan0     Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[rtl8187]
filename:       /lib/modules/3.19.0-18-generic/kernel/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko
license:        GPL
description:    RTL8187/RTL8187B USB wireless driver
author:         Larry Finger <Larry.Finger@lwfinger.net>
author:         Hin-Tak Leung <htl10@users.sourceforge.net>
author:         Herton Ronaldo Krzesinski <herton@mandriva.com.br>
author:         Andrea Merello <andrea.merello@gmail.com>
author:         Michael Wu <flamingice@sourmilk.net>
srcversion:     DE5DF1BDA1FE2F1BDE67103
depends:        mac80211,eeprom_93cx6,cfg80211
intree:         Y
vermagic:       3.19.0-18-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A7:FB:1A:1A:38:6C:62:CC:9C:EE:94:C2:38:B0:77:04:2A:AB:58:BE
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.19.0-18-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     45659D6D4B015B51A3FF148
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-18-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A7:FB:1A:1A:38:6C:62:CC:9C:EE:94:C2:38:B0:77:04:2A:AB:58:BE
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-18-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E61EB836E1B33C2A2918485
depends:        
intree:         Y
vermagic:       3.19.0-18-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A7:FB:1A:1A:38:6C:62:CC:9C:EE:94:C2:38:B0:77:04:2A:AB:58:BE
sig_hashalgo:   sha512
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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (rtl8187)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   12.247285] ieee80211 phy0: hwaddr <MAC 'wlan0' [IF]>, RTL8187BvE V0 + rtl8225z2, rfkill mask 4
[   12.268834] rtl8187: Customer ID is 0x04
[   12.271064] rtl8187: wireless switch is off

########## wireless info END ############



```

---

### Post by zach34 on 2015-06-05
Anything?

---

### Post by hamlet32 on 2015-06-06
try my reply to a similar problem here

[http://ubuntuforums.org/showthread.php?t=2277116]("http://ubuntuforums.org/showthread.php?t=2277116")

---

