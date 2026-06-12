---
title: "Broadcom module  from HP mini does not connect after setup on the another laptop"
date: 2016-03-23
forum: Networking &amp; Wireless
---

### Post by Dzen_Tao on 2016-03-23
[FONT=Arial]Hi all[/FONT][FONT=Arial], 
I have a problem [/FONT][FONT=Arial]with the Wi-[/FONT][FONT=Arial]Fi module [/FONT][FONT=Arial]on my laptop (IRU t1301s). M[/FONT][FONT=Arial]y notebook [/FONT][FONT=Arial]had [/FONT][FONT=Arial]a module [/FONT][FONT=Arial]AR9485 [/FONT][FONT=Arial]Atheros[/FONT][FONT=Arial] ([/FONT][FONT=Arial]AzureWave[/FONT][FONT=Arial]), [/FONT][FONT=Arial]but because [/FONT][FONT=Arial]it had [/FONT][FONT=Arial]a weak signal (connection was unstable)[/FONT][FONT=Arial]I replaced that module to [/FONT][FONT=Arial]Broadcom [/FONT][FONT=Arial]BCM4313[/FONT][FONT=Arial], [/FONT][FONT=Arial]which I took [/FONT][FONT=Arial]from an old HP Mini netbook[/FONT][FONT=Arial]. [/FONT][FONT=Arial]But [/FONT][FONT=Arial]now I can't [/FONT][FONT=Arial]with the module [/FONT][FONT=Arial]BCM4313 [/FONT][FONT=Arial]connect to [/FONT][FONT=Arial]a wi-fi network[/FONT][FONT=Arial]. [/FONT][FONT=Arial]I can see [/FONT][FONT=Arial]all access points [/FONT][FONT=Arial]but when I try [/FONT][FONT=Arial]to connect[/FONT][FONT=Arial], I enter [/FONT][FONT=Arial]password [/FONT][FONT=Arial]and [/FONT][FONT=Arial]nothing happens.

On the ubuntu 14.10, 15.10 I have the same result.

This is a wireless-info.txt:
```
########## wireless info START ##########


Report from: 23 Mar 2016 22:00 YEKT +0500


Booted last: 23 Mar 2016 00:00 YEKT +0500


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily


##### kernel ############################


Linux 4.2.0-35-generic #40-Ubuntu SMP Tue Mar 15 22:15:45 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0123]
    Kernel driver in use: r8169


03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1483]
    Kernel driver in use: bcma-pci-bridge


##### lsusb #############################


Bus 003 Device 003: ID 0e8f:00fb GreenAsia Inc. 
Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 058f:3821 Alcor Micro Corp. 
Bus 001 Device 002: ID 0a5c:21b4 Broadcom Corp. BCM2070 Bluetooth 2.1 + EDR
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no


##### lsmod #############################


brcmsmac              573440  0
cordic                 16384  1 brcmsmac
brcmutil               16384  1 brcmsmac
b43                   417792  0
mac80211              745472  2 b43,brcmsmac
cfg80211              557056  3 b43,brcmsmac,mac80211
ssb                    65536  1 b43
bcma                   53248  3 b43,brcmsmac


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF]>  
          inet addr:192.168.0.137  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enp2s0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42623 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25687 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:62130436 (62.1 MB)  TX bytes:1955381 (1.9 MB)


wlp3s0b1  Link encap:Ethernet  HWaddr <MAC 'wlp3s0b1' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


enp2s0    no wireless extensions.


lo        no wireless extensions.


wlp3s0b1  IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=30 dBm   
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


root       690     1  0 21:49 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
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
GENERAL.CONNECTION:                     &#1055;&#1088;&#1086;&#1074;&#1086;&#1076;&#1085;&#1086;&#1077; &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1077; 1
GENERAL.CON-UUID:                       0383cf51-5181-4eb1-95db-32267a3dcadc
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   0383cf51-5181-4eb1-95db-32267a3dcadc | &#1055;&#1088;&#1086;&#1074;&#1086;&#1076;&#1085;&#1086;&#1077; &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1077; 1
IP4.ADDRESS[1]:                         192.168.0.137/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             217.24.176.230
IP4.DNS[2]:                             217.24.177.2
DHCP4.OPTION[1]:                        requested_ntp_servers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        expiry = 1458924746
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 172800
DHCP4.OPTION[14]:                       routers = 192.168.0.1
DHCP4.OPTION[15]:                       ip_address = 192.168.0.137
DHCP4.OPTION[16]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[17]:                       requested_netbios_scope = 1
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name_servers = 217.24.176.230 217.24.177.2
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_routers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       dhcp_message_type = 5
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::<IP6 'enp2s0' [IF]>/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlp3s0b1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4313 802.11bgn Wireless Network Adapter
GENERAL.DRIVER:                         brcmsmac
GENERAL.DRIVER-VERSION:                 4.2.0-35-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp3s0b1' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/bcma0:1/net/wlp3s0b1
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID        BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
MixXxA-MTC  <MAC 'MixXxA-MTC' [AN1]>  Infra  9     2452 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2  no        


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


[[/etc/NetworkManager/system-connections/459]] (600 root)
[connection] id=459 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0b1' [IF]> | mac-address-blacklist= | ssid=459
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ironhide]] (600 root)
[connection] id=ironhide | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=ironhide
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Asia/Yekaterinburg (based on set time zone)


country US: DFS-FCC
    (2402 - 2472 @ 40), (N/A, 30), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A)
    (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


enp2s0    no frequency information.


lo        no frequency information.


wlp3s0b1  11 channels in total; available frequencies :
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


enp2s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlp3s0b1  No scan results


##### module infos ######################


[brcmsmac]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     4B2FFE4B90A21C08ABE6873
depends:        mac80211,bcma,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        D2:CD:13:F4:5F:A3:B0:12:FC:89:B8:D5:00:F9:1D:CC:A4:D9:E0:A8
sig_hashalgo:   sha512


[brcmutil]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     AE9B4BBC6D82855B9265054
depends:        
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        D2:CD:13:F4:5F:A3:B0:12:FC:89:B8:D5:00:F9:1D:CC:A4:D9:E0:A8
sig_hashalgo:   sha512


[b43]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     EBCFBB62711AEC753D1C919
depends:        ssb,bcma,mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        D2:CD:13:F4:5F:A3:B0:12:FC:89:B8:D5:00:F9:1D:CC:A4:D9:E0:A8
sig_hashalgo:   sha512
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)


[mac80211]
filename:       /lib/modules/4.2.0-35-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1E79C1BE23A29358B904F24
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        D2:CD:13:F4:5F:A3:B0:12:FC:89:B8:D5:00:F9:1D:CC:A4:D9:E0:A8
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.2.0-35-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        D2:CD:13:F4:5F:A3:B0:12:FC:89:B8:D5:00:F9:1D:CC:A4:D9:E0:A8
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[ssb]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     B9B638C64CE9AC05F1A1903
depends:        
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        D2:CD:13:F4:5F:A3:B0:12:FC:89:B8:D5:00:F9:1D:CC:A4:D9:E0:A8
sig_hashalgo:   sha512


[bcma]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     6DF74A7EF5817B6F27A5CB0
depends:        
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        D2:CD:13:F4:5F:A3:B0:12:FC:89:B8:D5:00:F9:1D:CC:A4:D9:E0:A8
sig_hashalgo:   sha512


##### module parameters #################


[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2


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


[   26.816432] IPv6: ADDRCONF(NETDEV_UP): wlp3s0b1: link is not ready
[   27.710351] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   27.710363] brcmsmac bcma0:1: brcms_ops_config: change power-save mode: false (implement)
[   27.710520] IPv6: ADDRCONF(NETDEV_UP): wlp3s0b1: link is not ready
[   27.712582] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   27.974951] r8169 0000:02:00.0 enp2s0: link down (repeated 2 times)
[   27.974991] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   28.035224] IPv6: ADDRCONF(NETDEV_UP): wlp3s0b1: link is not ready
[   29.531658] r8169 0000:02:00.0 enp2s0: link up
[   29.531671] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready
[   90.485104] r8169 0000:02:00.0 enp2s0: link down
[  119.716567] wlp3s0b1: authenticate with <MAC address>
[  119.719456] wlp3s0b1: direct probe to <MAC address> (try 1/3)
[  119.920075] wlp3s0b1: direct probe to <MAC address> (try 2/3)
[  120.124128] wlp3s0b1: direct probe to <MAC address> (try 3/3)
[  120.328277] wlp3s0b1: authentication with <MAC address> timed out
[  128.179960] wlp3s0b1: authenticate with <MAC address>
[  128.181262] wlp3s0b1: direct probe to <MAC address> (try 1/3)
[  128.383638] wlp3s0b1: direct probe to <MAC address> (try 2/3)
[  128.587672] wlp3s0b1: direct probe to <MAC address> (try 3/3)
[  128.791809] wlp3s0b1: authentication with <MAC address> timed out
[  144.069802] IPv6: ADDRCONF(NETDEV_UP): wlp3s0b1: link is not ready
[  200.646485] r8169 0000:02:00.0 enp2s0: link up


########## wireless info END ############

```

Module from HP Mini does not connect after setup it on the another laptop.[/FONT]

---

### Post by Hadaka on 2016-03-23
Hi From a working wired connection please open a terminal...ctrl/alt/t
then Copy and paste one line at a time..
```
sudo iw reg set RU
sudo sed -i 's/^REG.*=$/&RU/' /etc/default/crda
```
then do..
*ignore any error on command  #2, continue and do one line at a time..
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
echo -e 'blacklist b43\nblacklist ssb' | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -v brcmsmac
sudo rfkill unblock all
```
disconnect wired connection,boot and test wireless
thanks.

---

### Post by Dzen_Tao on 2016-03-24
Thanks for reply. I really did all what you recommended but it doesn't helped. I can browse neighbouring Wi-Fi access points, enter the pass-key and that's all. After I press the "connect" button system trying to connect and then stopping.

---

### Post by Hadaka on 2016-03-24
Hi, please run and post the wireless-info again ,
thanks

---

### Post by Dzen_Tao on 2016-03-24
Hi, here is wireless-info.txt:

```
########## wireless info START ##########


Report from: 24 Mar 2016 22:00 YEKT +0500


Booted last: 24 Mar 2016 00:00 YEKT +0500


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 15.10
Release:	15.10
Codename:	wily


##### kernel ############################


Linux 4.2.0-35-generic #40-Ubuntu SMP Tue Mar 15 22:15:45 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu (from ~/.dmrc)


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0123]
	Kernel driver in use: r8169


03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:1483]
	Kernel driver in use: bcma-pci-bridge


##### lsusb #############################


Bus 003 Device 003: ID 0e8f:00fb GreenAsia Inc. 
Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 058f:3821 Alcor Micro Corp. 
Bus 001 Device 002: ID 0a5c:21b4 Broadcom Corp. BCM2070 Bluetooth 2.1 + EDR
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


brcmsmac              573440  0
cordic                 16384  1 brcmsmac
brcmutil               16384  1 brcmsmac
mac80211              745472  1 brcmsmac
cfg80211              557056  2 brcmsmac,mac80211
bcma                   53248  2 brcmsmac


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF]>  
          inet addr:192.168.0.137  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enp2s0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1420 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1670 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:949776 (949.7 KB)  TX bytes:294216 (294.2 KB)


wlp3s0b1  Link encap:Ethernet  HWaddr <MAC 'wlp3s0b1' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


enp2s0    no wireless extensions.


lo        no wireless extensions.


wlp3s0b1  IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
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


root       734     1  0 21:57 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
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
GENERAL.CONNECTION:                     &#1055;&#1088;&#1086;&#1074;&#1086;&#1076;&#1085;&#1086;&#1077; &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1077; 1
GENERAL.CON-UUID:                       650ebbad-1fcb-4599-8363-3885234adf2b
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   650ebbad-1fcb-4599-8363-3885234adf2b | &#1055;&#1088;&#1086;&#1074;&#1086;&#1076;&#1085;&#1086;&#1077; &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1077; 1
IP4.ADDRESS[1]:                         192.168.0.137/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             217.24.176.230
IP4.DNS[2]:                             217.24.177.2
DHCP4.OPTION[1]:                        requested_ntp_servers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        expiry = 1459011475
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 172800
DHCP4.OPTION[14]:                       routers = 192.168.0.1
DHCP4.OPTION[15]:                       ip_address = 192.168.0.137
DHCP4.OPTION[16]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[17]:                       requested_netbios_scope = 1
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name_servers = 217.24.176.230 217.24.177.2
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_routers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       dhcp_message_type = 5
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::<IP6 'enp2s0' [IF]>/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlp3s0b1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4313 802.11bgn Wireless Network Adapter
GENERAL.DRIVER:                         brcmsmac
GENERAL.DRIVER-VERSION:                 4.2.0-35-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp3s0b1' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/bcma0:1/net/wlp3s0b1
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
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   09b09272-54fe-4e17-9661-c2a36d0d4164 | 459


SSID  BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
459   <MAC '459' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        


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


[[/etc/NetworkManager/system-connections/459]] (600 root)
[connection] id=459 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0b1' [IF]> | mac-address-blacklist= | ssid=459
[ipv4] method=auto
[ipv6] method=ignore


##### iw reg get ########################


Region: Asia/Yekaterinburg (based on set time zone)


country RU: DFS-ETSI
	(2402 - 2482 @ 40), (N/A, 20), (N/A)
	(5170 - 5250 @ 80), (N/A, 20), (N/A)
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
	(5650 - 5730 @ 80), (N/A, 30), (0 ms), DFS
	(5735 - 5835 @ 80), (N/A, 30), (N/A)


##### iwlist channels ###################


enp2s0    no frequency information.


lo        no frequency information.


wlp3s0b1  11 channels in total; available frequencies :
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


enp2s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.452 GHz (Channel 9)


wlp3s0b1  Scan completed :
          Cell 01 - Address: <MAC '459' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"459"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000061b70a0180
                    Extra: Last beacon: 396ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'planeta128799' [AC2]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"planeta128799"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001af63f169
                    Extra: Last beacon: 152ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[brcmsmac]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     4B2FFE4B90A21C08ABE6873
depends:        mac80211,bcma,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        D2:CD:13:F4:5F:A3:B0:12:FC:89:B8:D5:00:F9:1D:CC:A4:D9:E0:A8
sig_hashalgo:   sha512


[brcmutil]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     AE9B4BBC6D82855B9265054
depends:        
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        D2:CD:13:F4:5F:A3:B0:12:FC:89:B8:D5:00:F9:1D:CC:A4:D9:E0:A8
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/4.2.0-35-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1E79C1BE23A29358B904F24
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        D2:CD:13:F4:5F:A3:B0:12:FC:89:B8:D5:00:F9:1D:CC:A4:D9:E0:A8
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.2.0-35-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        D2:CD:13:F4:5F:A3:B0:12:FC:89:B8:D5:00:F9:1D:CC:A4:D9:E0:A8
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[bcma]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     6DF74A7EF5817B6F27A5CB0
depends:        
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        D2:CD:13:F4:5F:A3:B0:12:FC:89:B8:D5:00:F9:1D:CC:A4:D9:E0:A8
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
blacklist ssb


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


[   31.010319] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   31.332488] r8169 0000:02:00.0 enp2s0: link down
[   31.332530] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   31.333181] r8169 0000:02:00.0 enp2s0: link down
[   31.335934] IPv6: ADDRCONF(NETDEV_UP): wlp3s0b1: link is not ready
[   31.728991] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   31.729002] brcmsmac bcma0:1: brcms_ops_config: change power-save mode: false (implement)
[   31.729151] IPv6: ADDRCONF(NETDEV_UP): wlp3s0b1: link is not ready (repeated 2 times)
[   33.340248] r8169 0000:02:00.0 enp2s0: link up
[   33.340259] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready


########## wireless info END ############

```

---

### Post by Hadaka on 2016-03-24
Hi, open a terminal and do..
```
sudo ifconfig wlp3s0b1 down
sudo ifconfig wlp3s0b1 up
```
then go into network manager and delete the access point "459" or whatever
your ssid is.
then boot and go back into network manager and configure and add access point "459"
again and configure IPv4 and IPv6 like the attached.
[ATTACH=CONFIG]267966[/ATTACH][ATTACH=CONFIG]267967[/ATTACH]
then go into your router configuration and verify the settings, they should be WPA2 AES CCMP
and verify the password for access point "459"
once the router is correct then boot the computer and test.
thanks.

---

### Post by Dzen_Tao on 2016-03-24
Hi, I tested this and still can't connect to wi-fi. I don't know what the problem, because I remember that when I installed the module in the notebook the connection had established succesfully. But the next day the connection vanished and doesn't back more.

This is /var/log/syslog:
```

Mar 24 23:24:08 andrew NetworkManager[698]: <info>  (wlp3s0b1): Activation: starting connection '459' (253a4311-1ba7-4ea4-91db-caa2da569d1
7)
Mar 24 23:24:08 andrew NetworkManager[698]: <info>  (wlp3s0b1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Mar 24 23:24:08 andrew NetworkManager[698]: <info>  (wlp3s0b1): device state change: prepare -> config (reason 'none') [40 50 0]
Mar 24 23:24:08 andrew NetworkManager[698]: <info>  (wlp3s0b1): Activation: (wifi) access point '459' has security, but secrets are requir
ed.
Mar 24 23:24:08 andrew NetworkManager[698]: <info>  (wlp3s0b1): device state change: config -> need-auth (reason 'none') [50 60 0]
Mar 24 23:24:08 andrew NetworkManager[698]: <info>  (wlp3s0b1): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Mar 24 23:24:08 andrew NetworkManager[698]: <info>  (wlp3s0b1): device state change: prepare -> config (reason 'none') [40 50 0]
Mar 24 23:24:08 andrew NetworkManager[698]: <info>  (wlp3s0b1): Activation: (wifi) connection '459' has security, and secrets exist.  No n
ew secrets needed.
Mar 24 23:24:08 andrew NetworkManager[698]: <info>  Config: added 'ssid' value '459'
Mar 24 23:24:08 andrew NetworkManager[698]: <info>  Config: added 'scan_ssid' value '1'
Mar 24 23:24:08 andrew NetworkManager[698]: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Mar 24 23:24:08 andrew NetworkManager[698]: <info>  Config: added 'psk' value '<omitted>'
Mar 24 23:24:08 andrew NetworkManager[698]: <info>  Config: set interface ap_scan to 1
Mar 24 23:24:08 andrew NetworkManager[698]: <info>  (wlp3s0b1): supplicant interface state: inactive -> scanning
Mar 24 23:24:09 andrew wpa_supplicant[806]: wlp3s0b1: SME: Trying to authenticate with c0:4a:00:85:f0:75 (SSID='459' freq=2437 MHz)
Mar 24 23:24:09 andrew kernel: [ 1257.196982] wlp3s0b1: authenticate with c0:4a:00:85:f0:75
Mar 24 23:24:09 andrew kernel: [ 1257.198484] wlp3s0b1: direct probe to c0:4a:00:85:f0:75 (try 1/3)
Mar 24 23:24:09 andrew NetworkManager[698]: <info>  (wlp3s0b1): supplicant interface state: scanning -> authenticating
Mar 24 23:24:09 andrew kernel: [ 1257.400516] wlp3s0b1: direct probe to c0:4a:00:85:f0:75 (try 2/3)
Mar 24 23:24:09 andrew kernel: [ 1257.604662] wlp3s0b1: direct probe to c0:4a:00:85:f0:75 (try 3/3)
Mar 24 23:24:09 andrew kernel: [ 1257.808736] wlp3s0b1: authentication with c0:4a:00:85:f0:75 timed out
Mar 24 23:24:10 andrew wpa_supplicant[806]: wlp3s0b1: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="459" auth_failures=1 duration=10 reason=CONN_FAILED
Mar 24 23:24:10 andrew NetworkManager[698]: <info>  (wlp3s0b1): supplicant interface state: authenticating -> disconnected
Mar 24 23:24:21 andrew NetworkManager[698]: <info>  (wlp3s0b1): supplicant interface state: disconnected -> scanning
Mar 24 23:24:22 andrew wpa_supplicant[806]: wlp3s0b1: CTRL-EVENT-SSID-REENABLED id=0 ssid="459"
Mar 24 23:24:22 andrew wpa_supplicant[806]: wlp3s0b1: SME: Trying to authenticate with c0:4a:00:85:f0:75 (SSID='459' freq=2437 MHz)
Mar 24 23:24:22 andrew kernel: [ 1269.938205] wlp3s0b1: authenticate with c0:4a:00:85:f0:75
Mar 24 23:24:22 andrew kernel: [ 1269.940045] wlp3s0b1: direct probe to c0:4a:00:85:f0:75 (try 1/3)
Mar 24 23:24:22 andrew NetworkManager[698]: <info>  (wlp3s0b1): supplicant interface state: scanning -> authenticating
Mar 24 23:24:22 andrew kernel: [ 1270.141777] wlp3s0b1: direct probe to c0:4a:00:85:f0:75 (try 2/3)
Mar 24 23:24:22 andrew kernel: [ 1270.345895] wlp3s0b1: direct probe to c0:4a:00:85:f0:75 (try 3/3)
Mar 24 23:24:22 andrew kernel: [ 1270.549995] wlp3s0b1: authentication with c0:4a:00:85:f0:75 timed out
Mar 24 23:24:23 andrew wpa_supplicant[806]: wlp3s0b1: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="459" auth_failures=2 duration=20 reason=CONN_FAILED
Mar 24 23:24:23 andrew NetworkManager[698]: <info>  (wlp3s0b1): supplicant interface state: authenticating -> disconnected
Mar 24 23:24:33 andrew NetworkManager[698]: <warn>  (wlp3s0b1): Activation: (wifi) association took too long, failing activation
Mar 24 23:24:33 andrew NetworkManager[698]: <info>  (wlp3s0b1): device state change: config -> failed (reason 'ssid-not-found') [50 120 53]
Mar 24 23:24:33 andrew NetworkManager[698]: <info>  Connection '459' failed to autoconnect; 2 tries left
Mar 24 23:24:33 andrew NetworkManager[698]: <warn>  (wlp3s0b1): Activation: failed for connection '459'
Mar 24 23:24:33 andrew NetworkManager[698]: <info>  (wlp3s0b1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Mar 24 23:24:34 andrew NetworkManager[698]: <info>  Device 'wlp3s0b1' has no connection; scheduling activate_check in 0 seconds.
Mar 24 23:24:34 andrew NetworkManager[698]: <info>  (wlp3s0b1): supplicant interface state: disconnected -> scanning
Mar 24 23:24:34 andrew wpa_supplicant[806]: wlp3s0b1: Reject scan trigger since one is already pending
Mar 24 23:24:34 andrew kernel: [ 1282.067268] IPv6: ADDRCONF(NETDEV_UP): wlp3s0b1: link is not ready
Mar 24 23:24:34 andrew NetworkManager[698]: <warn>  Could not get scan request result: GDBus.Error:fi.w1.wpa_supplicant1.Interface.ScanError: Scan request rejected
Mar 24 23:24:34 andrew NetworkManager[698]: <info>  (wlp3s0b1): supplicant interface state: scanning -> inactive

```

---

### Post by Hadaka on 2016-03-24
Hi your wifi signal is very low..
```
wlp3s0b1  Scan completed :
          Cell 01 - Address: <MAC '459' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=**[COLOR=#ff0000]47/70[/COLOR]**[COLOR=#ff0000][/COLOR]  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"459"
```
Since you recently installed this card, please verify that you 
have a good antenna wire connection on the wifi card.
then disconnect the ethernet connection and test wireless.
thanks.

---

### Post by Dzen_Tao on 2016-03-24
Sorry, I try to connect at a distance of 20 centimeters and it didn't work.
 
[ATTACH=CONFIG]267972[/ATTACH]

---

### Post by Hadaka on 2016-03-24
Try standing next to the router and do and post..
```
iwlist wlp3s0b1 scan
```
thanks.

---

### Post by Dzen_Tao on 2016-03-25
Hi! I solved the connection problem installing another driver:
```

sudo apt-get install bcmwl-kernel-source

```

Thanks!

---

### Post by Hadaka on 2016-03-25
That is great news ! glad you found a solution.
usually, your card broadcom 4313 with pci-id [14e4:4727]
with your kernel version..Linux 4.2.0-35-generic #40-Ubuntu
uses the native driver brcmsmac per this guide..[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)
but..you got it going on the brcmwl "wl" driver this usually only works if..
Special case #3: Use bcmwl-kernel-source for kernel version less than 3.8;
Just glad to see it working,by whatever method provides the solution. Good job !
thanks.
Please take the time to mark your thread SOLVED by logging in to your thread
first post and click **Thread Tools **then choose Mark this thread **Solved**.
marking solved helps others with a like problem.

---

