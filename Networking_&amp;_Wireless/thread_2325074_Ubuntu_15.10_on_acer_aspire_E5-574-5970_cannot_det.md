---
title: "Ubuntu 15.10 on acer aspire E5-574-5970 cannot detect any wireless net work"
date: 2016-05-18
forum: Networking &amp; Wireless
---

### Post by zhpz2011 on 2016-05-18
I recently bought an Acer Aspire E5-574-5970 laptop that was pre-installed with Windows 10. Since everything works well on windows including wireless, I replaced the original hard drive with my own and installed ubuntu 15.10 on it. Everything went fine when I installed Ubuntu with the exception that it did not find any wireless connection during installation. Following installation the laptop boots fine, but it still cannot detect any wireless network while it can when the laptop is running windows 10. So I tried running ubuntu 15.10 LIVE, 16.04 LIVE and 14.04 LIVE, but none of them detected WiFi either. 

Later I tried running the standard network test script from Ubuntu Forums**([COLOR=#000000]https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) Below are the results. [/COLOR]**[COLOR=#000000]I was wondering if there is anyone who can help me solve this issue.[/COLOR]



**[SIZE=3]Here is the result I got[/SIZE]**


```
########## wireless info START ##########


Report from: 17 May 2016 22:04 CST -0600


Booted last: 17 May 2016 00:00 CST -0600


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 15.10
Release:	15.10
Codename:	wily


##### kernel ############################


Linux 4.2.0-16-generic #19-Ubuntu SMP Thu Oct 8 15:35:06 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Xubuntu (from ~/.dmrc)


##### lspci #############################


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: Acer Incorporated [ALI] Device [1025:100c]
	Kernel driver in use: r8169


02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)
	Subsystem: Lite-On Communications Inc Device [11ad:0806]


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 04f2:b526 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 04ca:3015 Lite-On Technology Corp. 
Bus 001 Device 005: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: acer-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


wl                   6365184  0
cfg80211              548864  1 wl
acer_wmi               20480  0
sparse_keymap          16384  1 acer_wmi
wmi                    20480  1 acer_wmi
video                  36864  2 i915,acer_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF]>  
          inet addr:172.16.1.70  Bcast:172.16.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enp1s0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9934 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8541 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8089455 (8.0 MB)  TX bytes:1012833 (1.0 MB)


##### iwconfig ##########################


lo        no wireless extensions.


enp1s0    no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.16.1.254    0.0.0.0         UG    0      0        0 enp1s0
0.0.0.0         172.16.1.254    0.0.0.0         UG    100    0        0 enp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp1s0
172.16.1.0      0.0.0.0         255.255.255.0   U     100    0        0 enp1s0


##### resolv.conf #######################


nameserver 127.0.1.1
search Home


##### network managers ##################


Installed:


	NetworkManager


Running:


root      1480     1  0 21:18 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               rtl8168h-2_0.0.2 02/26/15
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/enp1s0
GENERAL.IP-IFACE:                       enp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       1f049707-4659-4d97-9841-dc209fcdcac9
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   1f049707-4659-4d97-9841-dc209fcdcac9 | Wired connection 1
IP4.ADDRESS[1]:                         172.16.1.70/24
IP4.GATEWAY:                            172.16.1.254
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             172.16.1.254
IP4.DNS[2]:                             142.165.21.5
IP4.DOMAIN[1]:                          Home
DHCP4.OPTION[1]:                        network_number = 172.16.1.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_time_offset = 1
DHCP4.OPTION[8]:                        expiry = 1463629090
DHCP4.OPTION[9]:                        domain_name = Home
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 172.16.1.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 172.16.1.254
DHCP4.OPTION[15]:                       dhcp_lease_time = 86400
DHCP4.OPTION[16]:                       ip_address = 172.16.1.70
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       domain_name_servers = 172.16.1.254 142.165.21.5
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       requested_ntp_servers = 1
DHCP4.OPTION[27]:                       requested_netbios_scope = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 172.16.1.254
IP6.ADDRESS[1]:                         fe80::<IP6 'enp1s0' [IF]>/64
IP6.GATEWAY:                            


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


Region: America/Regina (based on set time zone)


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


enp1s0    no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp1s0    Interface doesn't support scanning.


##### module infos ######################


modinfo: ERROR: Module wl not found.
[wl]


[cfg80211]
filename:       /lib/modules/4.2.0-16-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-16-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        6A:1C:9C:21:F0:4A:B8:6F:D1:D7:CE:D6:CA:11:35:40:FC:8E:35:B6
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


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


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


grep: /etc/udev/rules.d/*net*.rules: No such file or directory


##### dmesg #############################


[    9.191886] wl: module license 'MIXED/Proprietary' taints kernel.
[    9.194248] wl: module verification failed: signature and/or required key missing - tainting kernel
[   22.163692] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[   22.436718] r8169 0000:01:00.0 enp1s0: link down
[   22.436819] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready (repeated 2 times)
[  350.252443] r8169 0000:01:00.0 enp1s0: link down
[  350.252496] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready (repeated 2 times)
[ 1340.144541] r8169 0000:01:00.0 enp1s0: link up
[ 1340.144567] IPv6: ADDRCONF(NETDEV_CHANGE): enp1s0: link becomes ready


########## wireless info END ############
```

---

### Post by wildmanne39 on 2016-05-19
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by wildmanne39 on 2016-05-19
First you have the wrong driver installed. Please do:
```
sudo apt-get purge bcmwl-kernel-source
```
then you need to install the firmware for your driver.
```
sudo apt-get install linux-firmware
```
I personally would install 16.04 first then install the firmware because 16.04 is supported for 5 years and 15.10 will expire in a few months.
Reboot

---

### Post by zhpz2011 on 2016-05-19
Thank you for your suggestions. I will give it a try.

---

### Post by zhpz2011 on 2016-05-20
Thank you again, Wild Man. I followed your suggestion on installing 16.04. The installation worked fine (Although the wireless naturally was not detected). I then executed your suggested command of :

```

sudo apt-get install linux-firmware

```
Unfortunately, this indicated that there was no newer version:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware is already the newest version (1.157).
linux-firmware set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Running the standard ubuntu wireless-info script immediately after yielded the following:

```


########## wireless info START ##########

Report from: 19 May 2016 21:55 CST -0600

Booted last: 19 May 2016 00:00 CST -0600

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu (from ~/.dmrc)

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Acer Incorporated [ALI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1025:100c]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)
    Subsystem: Lite-On Communications Inc Device [11ad:0806]
    Kernel driver in use: ath10k_pci

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 04f2:b526 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 04ca:3015 Lite-On Technology Corp. 
Bus 001 Device 006: ID 13fe:4200 Kingston Technology Company Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath10k_pci             45056  0
ath10k_core           311296  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              737280  1 ath10k_core
acer_wmi               20480  0
cfg80211              565248  3 ath,mac80211,ath10k_core
sparse_keymap          16384  1 acer_wmi
wmi                    20480  1 acer_wmi
video                  40960  2 i915_bpo,acer_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF]>  
          inet addr:172.16.1.70  Bcast:172.16.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ea79:4628:cf64:3b3f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9861 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7285 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11536803 (11.5 MB)  TX bytes:805911 (805.9 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp1s0    no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.16.1.254    0.0.0.0         UG    100    0        0 enp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp1s0
172.16.1.0      0.0.0.0         255.255.255.0   U     100    0        0 enp1s0

##### resolv.conf #######################

nameserver 127.0.1.1
search Home

##### network managers ##################

Installed:

    NetworkManager

Running:

root       725     1  0 21:39 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/enp1s0
GENERAL.IP-IFACE:                       enp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       3b31b530-8268-420f-a218-4aa1a2ad49f2
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/4
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   3b31b530-8268-420f-a218-4aa1a2ad49f2 | Wired connection 1
IP4.ADDRESS[1]:                         172.16.1.70/24
IP4.GATEWAY:                            172.16.1.254
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             172.16.1.254
IP4.DNS[2]:                             142.165.21.5
IP4.DOMAIN[1]:                          Home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1463780899
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 172.16.1.254
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 172.16.1.70
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = Home
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 172.16.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 86400
DHCP4.OPTION[23]:                       domain_name_servers = 172.16.1.254 142.165.21.5
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 172.16.1.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 172.16.1.254
IP6.ADDRESS[1]:                         fe80::ea79:4628:cf64:3b3f/64
IP6.GATEWAY:                            

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

##### iw reg get ########################

Region: America/Regina (based on set time zone)

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

enp1s0    no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp1s0    Interface doesn't support scanning.

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board-2.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
srcversion:     8CBDAC7980FC042032AE6A6
depends:        ath10k_core
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     275C24567932534F3B81E01
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)

[ath]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-21-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     A882F4FE63500846E1C859E
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-21-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     00D8DA6D3B739DDD31FFF50
depends:        
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath10k_pci]
irq_mode: 0
reset_mode: 0

[ath10k_core]
cryptmode: 0
debug_mask: 0
rawmode: N
skip_otp: N
uart_print: N

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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[    8.976920] ath10k_pci 0000:02:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    9.292362] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[    9.292372] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-5.bin failed with error -2
[    9.292374] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-5.bin': -2
[    9.292380] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-4.bin failed with error -2
[    9.292381] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-4.bin': -2
[    9.292385] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-3.bin failed with error -2
[    9.292387] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-3.bin': -2
[    9.292391] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-2.bin failed with error -2
[    9.292392] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-2.bin': -2
[    9.292397] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware.bin failed with error -2
[    9.292398] ath10k_pci 0000:02:00.0: could not fetch firmware (-2)
[    9.292400] ath10k_pci 0000:02:00.0: could not fetch firmware files (-2)
[    9.292401] ath10k_pci 0000:02:00.0: could not probe fw (-2)
[   19.685811] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[   19.745915] r8169 0000:01:00.0 enp1s0: link down
[   19.745996] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[  237.834439] r8169 0000:01:00.0 enp1s0: link up
[  237.834466] IPv6: ADDRCONF(NETDEV_CHANGE): enp1s0: link becomes ready

########## wireless info END ############


```

I'd be grateful for any further suggestions that you can make.  I greatly appreciate your guidance and insights.

---

### Post by jeremy31 on 2016-05-20
Please see chili555's answer from
[http://askubuntu.com/questions/763080/no-wifi-in-qualcom-atheros-ubuntu-16-04-acer-aspire-e-15](http://askubuntu.com/questions/763080/no-wifi-in-qualcom-atheros-ubuntu-16-04-acer-aspire-e-15)
Hopefully the firmware will be part of linux-firmware in Ubuntu soon

---

### Post by zhpz2011 on 2016-05-20
It worked! Thank you so much for your help jermy31, I greatly appreciated it.

---

