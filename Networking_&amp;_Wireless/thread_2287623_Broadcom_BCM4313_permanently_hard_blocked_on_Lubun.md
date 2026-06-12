---
title: "Broadcom BCM4313 permanently hard blocked on Lubuntu 15.04"
date: 2015-07-21
forum: Networking &amp; Wireless
---

### Post by zeronineseven on 2015-07-21
Hi!
I've been using Lubuntu 12.04 for over year and recently decided to upgrade to Lubuntu 15.04. I completely reinstalled the system and everything looked fine but then I noticed that wifi is not working. When I installed 12.04 everything worked out of the box but with 15.04 I've already spent 2 days to make it work and still nothing. 

I think that the problem is related to "Hard blocked: yes" of phy0  in rfkill output and "brcmsmac bcma0:1: brcms_ops_start: brcms_up()  returned -132" in dmesg output. Then I thought that it might be real  hardware failure and ran Lubuntu 12.04 live image from usb to verify it  but wifi worked again and rfkill reports no hard lock on phy0 there.

What I've tried with no avail:

[LIST]
[*]Pressing Fn+F2 swithces only "Soft blocked" state in "phy0" and "asus-wlan" (but in Lubuntu 12.04 it **also** swithces "Hard blocked" in "phy0"); 
[*]There is "Enable WLAN" option in BIOS however I've never touched it between installations and it's on. Resetting BIOS to default settings also didnt' help; 
[*]Unloading (via modprobe -r) of all wmi-related modules in different combinations and pressing Fn+F2; 
[*]Swithing to proprietary Broadcom driver (like described here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)) leads to completely the same behaviour (the only difference is that rfkill reports "brcmwl-0" instead of "phy0" for Wireless LAN); 
[*]Some other less promising tricks found here and there. 
[/LIST]


Dumps were generated with script from here: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) (looks like it outputs the most relevant info but let me know if I should provide more).

Dump from currently installed Lubuntu 15.04 (I've manually added "b43" and "wl" to /etc/modprobe.d/blacklist.conf to avoid conflicts with brcmsmac):
```

########## wireless info START ##########

Report from: 21 Jul 2015 06:41 MSK +0300

Booted last: 21 Jul 2015 06:20 MSK +0300

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 3.19.0-22-generic #22-Ubuntu SMP Tue Jun 16 17:15:15 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu (from ~/.dmrc)

##### lspci #############################

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: AzureWave Device [1a3b:2047]
    Kernel driver in use: bcma-pci-bridge

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device [1043:100b]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 003: ID 13d3:5711 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 13d3:3315 IMC Networks Bluetooth module
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: asus-wimax: WiMAX
    Soft blocked: no
    Hard blocked: no
4: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

##### lsmod #############################

brcmsmac              577536  0 
cordic                 16384  1 brcmsmac
brcmutil               16384  1 brcmsmac
mac80211              724992  1 brcmsmac
cfg80211              540672  2 brcmsmac,mac80211
eeepc_wmi              16384  0 
asus_wmi               24576  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
bcma                   57344  2 brcmsmac
wmi                    20480  1 asus_wmi
video                  20480  2 gma500_gfx,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2222 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1501 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:229973 (229.9 KB)  TX bytes:174861 (174.8 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    1024   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search lan

##### network managers ##################

Installed:

    NetworkManager

Running:

root       532     1  0 06:20 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

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
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     &#1055;&#1088;&#1086;&#1074;&#1086;&#1076;&#1085;&#1086;&#1077; &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1077; 1
GENERAL.CON-UUID:                       fd1f9149-196d-442b-833b-59b4340eb741
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   fd1f9149-196d-442b-833b-59b4340eb741 | &#1055;&#1088;&#1086;&#1074;&#1086;&#1076;&#1085;&#1086;&#1077; &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1077; 1
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         ip = 192.168.1.68/24, gw = 192.168.1.1
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          lan
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        server_name = server-l.lan
DHCP4.OPTION[5]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[6]:                        ip_address = 192.168.1.68
DHCP4.OPTION[7]:                        filename = undionly.kpxe
DHCP4.OPTION[8]:                        requested_static_routes = 1
DHCP4.OPTION[9]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[10]:                       requested_time_offset = 1
DHCP4.OPTION[11]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       dhcp_rebinding_time = 37800
DHCP4.OPTION[14]:                       requested_domain_name_servers = 1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       requested_broadcast_address = 1
DHCP4.OPTION[17]:                       routers = 192.168.1.1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 21600
DHCP4.OPTION[19]:                       requested_domain_name = 1
DHCP4.OPTION[20]:                       domain_name = lan
DHCP4.OPTION[21]:                       requested_routers = 1
DHCP4.OPTION[22]:                       expiry = 1437492065
DHCP4.OPTION[23]:                       host_name = tania-llaptop
DHCP4.OPTION[24]:                       requested_netbios_scope = 1
DHCP4.OPTION[25]:                       requested_wpad = 1
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       requested_domain_search = 1
DHCP4.OPTION[30]:                       next_server = 192.168.1.152
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
DHCP4.OPTION[32]:                       dhcp_lease_time = 43200
DHCP4.OPTION[33]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         ip = fe80::<IP6 'eth0' [IF]>/64, gw = ::
IP6.DOMAIN[1]:                          lan

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4313 802.11bgn Wireless Network Adapter
GENERAL.DRIVER:                         brcmsmac
GENERAL.DRIVER-VERSION:                 3.19.0-22-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/bcma0:1/net/wlan0
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
WIFI-PROPERTIES.AP:                     yes
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

Region: Europe/Moscow (based on set time zone)

country US: DFS-FCC
    (2402 - 2472 @ 40), (3, 27), (N/A)
    (5170 - 5250 @ 40), (3, 17), (N/A)
    (5250 - 5330 @ 40), (3, 20), (0 ms), DFS
    (5490 - 5600 @ 40), (3, 20), (0 ms), DFS
    (5650 - 5710 @ 40), (3, 20), (0 ms), DFS
    (5735 - 5835 @ 40), (3, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     11 channels in total; available frequencies :
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

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

##### module infos ######################

[brcmsmac]
filename:       /lib/modules/3.19.0-22-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     5F866C1008CB05E51B96C2E
depends:        bcma,mac80211,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.19.0-22-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C7:D4:40:34:4C:0B:3A:C2:A3:CE:C2:AE:B9:72:2E:CF:6C:AE:73:91
sig_hashalgo:   sha512

[brcmutil]
filename:       /lib/modules/3.19.0-22-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     A2434DDD5B2051715F2E908
depends:        
intree:         Y
vermagic:       3.19.0-22-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C7:D4:40:34:4C:0B:3A:C2:A3:CE:C2:AE:B9:72:2E:CF:6C:AE:73:91
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.19.0-22-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     88CC41451370601B0D885E4
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-22-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C7:D4:40:34:4C:0B:3A:C2:A3:CE:C2:AE:B9:72:2E:CF:6C:AE:73:91
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-22-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E61EB836E1B33C2A2918485
depends:        
intree:         Y
vermagic:       3.19.0-22-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C7:D4:40:34:4C:0B:3A:C2:A3:CE:C2:AE:B9:72:2E:CF:6C:AE:73:91
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[bcma]
filename:       /lib/modules/3.19.0-22-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     F17244FFF75F9BDF92327ED
depends:        
intree:         Y
vermagic:       3.19.0-22-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C7:D4:40:34:4C:0B:3A:C2:A3:CE:C2:AE:B9:72:2E:CF:6C:AE:73:91
sig_hashalgo:   sha512

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
blacklist b43
blacklist wl

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    8.707396] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[    8.707443] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[    8.707479] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[    8.707542] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[    8.729323] bcma: bus0: Bus registered
[   94.082260] brcmsmac bcma0:1: mfg 4bf core 812 rev 24 class 0 irq 17
[   94.110115] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 499
[   94.170148] brcmsmac bcma0:1: brcms_ops_start: brcms_up() returned -132

########## wireless info END ############

```


Dump from live image of Lubuntu 12.04:
```


########## wireless info START ##########

Report from: 21 Jul 2015 05:30 UTC +0000

Booted last: 21 Jul 2015 05:25 UTC +0000

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04 LTS
Release:    12.04
Codename:    precise

##### kernel ############################

Linux 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:41:14 UTC 2012 i686 i686 i386 GNU/Linux

file=/cdrom/preseed/lubuntu.seed, boot=casper, initrd=/casper/initrd.lz, quiet, splash, --, debian-installer/language=ru, keyboard-configuration/layoutcode?=ru

##### desktop ###########################

Lubuntu (from ~/.dmrc)

##### lspci #############################

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: AzureWave Device [1a3b:2047]
    Kernel driver in use: brcmsmac

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device [1043:100b]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 001 Device 004: ID 13d3:5711 IMC Networks 
Bus 003 Device 002: ID 13d3:3315 IMC Networks Bluetooth module

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: asus-wimax: WiMAX
    Soft blocked: no
    Hard blocked: no
4: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

bcma                   25651  0 
brcmsmac              540875  0 
mac80211              436455  1 brcmsmac
eeepc_wmi              12949  0 
asus_wmi               19624  1 eeepc_wmi
sparse_keymap          13658  1 asus_wmi
brcmutil               14675  1 brcmsmac
cfg80211              178679  2 brcmsmac,mac80211
crc8                   12781  1 brcmsmac
cordic                 12487  1 brcmsmac
wmi                    18744  1 asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12762 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6356 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18648498 (18.6 MB)  TX bytes:453175 (453.1 KB)
          Interrupt:45 Base address:0x6000 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.0.1
search lan

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1649     1  0 05:25 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [&#1055;&#1088;&#1086;&#1074;&#1086;&#1076;&#1085;&#1086;&#1077; &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1077; 1] --------------------
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
    Address:         192.168.1.68
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

  IPv6 Settings:
    Address:         fe80::<IP6 'eth0' [IF]>
    Prefix:          64
    Gateway:         ::

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Singularity-2.4GHz: Infra, <MAC 'Singularity-2.4GHz' [AC12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2
    Singularity-2.4GHz: Infra, <MAC 'Singularity-2.4GHz' [AC14]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 80 WPA2
    CONDOR:          Infra, <MAC 'CONDOR' [AC1]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 57 WPA2
    MGTS_GPON_16D2:  Infra, <MAC 'MGTS_GPON_16D2' [AC5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 55 WPA2
    NETGEAR06:       Infra, <MAC 'NETGEAR06' [AC9]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 55 WPA2
    onlime:          Infra, <MAC 'onlime' [AC10]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    Zeliska92:       Infra, <MAC 'Zeliska92' [AC6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA2
    Kassik:          Infra, <MAC 'Kassik' [AC15]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 39 WPA2
    box04:           Infra, <MAC 'box04' [AC3]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    Kassik-Telecom:  Infra, <MAC 'Kassik-Telecom' [AC16]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 37 WPA2
    ip:              Infra, <MAC 'ip' [AC2]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 34 WPA2
    Keenetic-4593:   Infra, <MAC 'Keenetic-4593' [AC18]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 34 WPA2
    ASUS:            Infra, <MAC 'ASUS' [AC4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    USERW7PC_Network:Infra, <MAC 'USERW7PC_Network' [AC13]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 32 WPA2
    BAZA:            Infra, <MAC 'BAZA' [AC17]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 32 WPA2
    MGTS_GPON_2FD5:  Infra, <MAC 'MGTS_GPON_2FD5' [AC11]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA2
    VITALY:          Infra, <MAC 'VITALY' [AC20]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 29 WPA2
    Trojan.KeenValAd:Infra, <MAC 'Trojan.KeenValAd' [AC19]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2
    GlobalHome:      Infra, <MAC 'GlobalHome' [AC8]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 52
    GlobalHome:      Infra, <MAC 'GlobalHome' [AC7]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 27

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

'iw' is not installed (package "iw").

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

wlan0     11 channels in total; available frequencies :
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

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      2   APs on   Frequency:2.432 GHz (Channel 5)
      4   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      3   APs on   Frequency:2.447 GHz (Channel 8)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      5   APs on   Frequency:2.457 GHz (Channel 10)
      4   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'CONDOR' [AC1]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"CONDOR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000005c47aeee6ea
                    Extra: Last beacon: 476ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[bcma]
filename:       /lib/modules/3.2.0-23-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     FEAB8743063E94BFBEB09E2
depends:        
intree:         Y
vermagic:       3.2.0-23-generic SMP mod_unload modversions 686 

[brcmsmac]
filename:       /lib/modules/3.2.0-23-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     2A2103247E0A19DFCF0D78E
depends:        mac80211,brcmutil,cfg80211,cordic,crc8
intree:         Y
vermagic:       3.2.0-23-generic SMP mod_unload modversions 686 

[mac80211]
filename:       /lib/modules/3.2.0-23-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     6D32D386D04C34078417B3A
depends:        cfg80211
intree:         Y
vermagic:       3.2.0-23-generic SMP mod_unload modversions 686 
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)

[brcmutil]
filename:       /lib/modules/3.2.0-23-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     DB27B1DE461446E6FBADCFE
depends:        
intree:         Y
vermagic:       3.2.0-23-generic SMP mod_unload modversions 686 

[cfg80211]
filename:       /lib/modules/3.2.0-23-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     66E299164E0FE2BD7E0CCE8
depends:        
intree:         Y
vermagic:       3.2.0-23-generic SMP mod_unload modversions 686 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[mac80211]
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   35.851642] brcmsmac 0000:02:00.0: bus 2 slot 0 func 0 irq 11
[   35.851677] brcmsmac 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   35.851694] brcmsmac 0000:02:00.0: setting latency timer to 64
[   36.239738] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  367.478903] ieee80211 phy0: brcms_ops_config: change monitor mode: false (implement)
[  367.478913] ieee80211 phy0: brcms_ops_config: change power-save mode: false (implement)
[  367.479543] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  367.480104] ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############

```

I'm very frustrated and any help would be greatly appreciated! Thanks in advance!

---

### Post by Bucky Ball on 2015-07-21
*Thread moved to **Networking and Wireless**.*

15.10 is still in development. Not sure why you installed it, if you did. Is that a typo and you mean 15.04??????

You are aware than 12.04 LTS is a long-term support release, supported until 2017? 14.04 LTS is supported until 2019? I'm wondering if you might be much better off installing a current, stable and long-term support release, 14.04 LTS. 

Good luck whatever you do, but if you do mean you have installed 15.10, I have a feeling that is the wrong path for you unless you are keen to test and report in the Ubuntu development forum (not the main forum areas).

PS: If you are using 15.04, please change the thread title.

---

### Post by zeronineseven on 2015-07-21
Many thanks for response, Bucky Ball! And sorry for topic title confusion.
I didn't know about support plans for 12.04 and 14.04 (Ubuntu is not my day-to-day distro). I tried installing Lubuntu 14.04 and wifi  worked like a charm!
However behaviour of 15.04 is still quite strange and feels like a regression. Maybe I should open a ticket about it on the bugtracker?

---

### Post by Bucky Ball on 2015-07-21
You could look for an open ticket first, but lodging a bug report is doubtfully the way to go for now. Why not install 14.04 LTS? 15.04 dies in January 2016, still a way off I guess. 

If you want to fix wireless in 15.04 you want [this]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A12.04_.28Precise_Pangolin.29"), top of page. See how you go, but what you've done already may confuse the issue.

Take note from that link that "The bcmwl-kernel-source package should automatically blacklist the open source drivers so that the STA driver is the only one in use." In other words, that card needs the STA driver. Follow the instructions on the link and let us know how it goes.

---

