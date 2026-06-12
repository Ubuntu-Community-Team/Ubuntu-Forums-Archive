---
title: "asus pce-ac68 Ubuntu 18.04 detects no wifi"
date: 2018-06-04
forum: Networking &amp; Wireless
---

### Post by potimedia on 2018-06-04
Hey Guys,
i installed a freshly ubuntu 18.04, so I am quite new to the linux world, and have problems with my wifi card.
wireless-info:
```


########## wireless info START ##########

Report from: 04 Jun 2018 17:32 CEST +0200

Booted last: 04 Jun 2018 00:00 CEST +0200

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 4.15.0-22-generic #24-Ubuntu SMP Wed May 16 12:15:17 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

1e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:8677]
    Kernel driver in use: r8169

22:00.0 Network controller [0280]: Broadcom Limited BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)
    Subsystem: ASUSTeK Computer Inc. BCM4360 802.11ac Wireless Network Adapter [1043:85df]
    Kernel driver in use: wl

##### lsusb #############################

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0a5c:21e8 Broadcom Corp. BCM20702A0 Bluetooth 4.0
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 0451:8142 Texas Instruments, Inc. TUSB8041 4-Port Hub
Bus 001 Device 008: ID 09da:000a A4Tech Co., Ltd. Optical Mouse Opto 510D / OP-620D
Bus 001 Device 007: ID 1038:1600 SteelSeries ApS 
Bus 001 Device 004: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 001 Device 005: ID 0451:8142 Texas Instruments, Inc. TUSB8041 4-Port Hub
Bus 001 Device 003: ID 0451:8142 Texas Instruments, Inc. TUSB8041 4-Port Hub
Bus 001 Device 002: ID 0451:8142 Texas Instruments, Inc. TUSB8041 4-Port Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6447104  0
mac80211              778240  0
cfg80211              622592  2 wl,mac80211
eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
video                  40960  1 asus_wmi
wmi_bmof               16384  0
wmi                    24576  2 asus_wmi,wmi_bmof

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp30s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp30s0' [IF1]> brd <MAC address>
    inet 192.168.178.20/24 brd 192.168.178.255 scope global dynamic noprefixroute enp30s0
       valid_lft 861513sec preferred_lft 861513sec
    inet6 2001:16b8:2693:e300:b1a4:1680:3b57:9b94/64 scope global temporary dynamic 
       valid_lft 7032sec preferred_lft 3432sec
    inet6 2001:16b8:2693:e300:e453:b52c:3051:ca08/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 7032sec preferred_lft 3432sec
    inet6 fe80::91ed:a56f:ee85:563b/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp34s0: <NO-CARRIER,BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state DORMANT group default qlen 1000
    link/ether <MAC 'wlp34s0' [IF2]> brd <MAC address>

##### iwconfig ##########################

lo        no wireless extensions.

enp30s0   no wireless extensions.

wlp34s0   IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

default via 192.168.178.1 dev enp30s0 proto dhcp metric 100 
169.254.0.0/16 dev enp30s0 scope link metric 1000 
192.168.178.0/24 dev enp30s0 proto kernel scope link src 192.168.178.20 metric 100 

##### resolv.conf #######################

nameserver 127.0.0.53
search fritz.box

##### network managers ##################

Installed:

    NetworkManager

Running:

root       981     1  0 16:51 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp30s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp30s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:01.3/0000:03:00.2/0000:1d:00.0/0000:1e:00.0/net/enp30s0
GENERAL.IP-IFACE:                       enp30s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       1baf7adc-0c6b-3fef-8344-f0be37304b92
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.178.20/24
IP4.GATEWAY:                            192.168.178.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.178.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.178.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.178.1
IP4.DOMAIN[1]:                          fritz.box
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.178.1
DHCP4.OPTION[5]:                        ip_address = 192.168.178.20
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.178.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.178.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 756000
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.178.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 432000
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = fritz.box
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1528987879
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.178.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       next_server = 192.168.178.1
DHCP4.OPTION[28]:                       ntp_servers = 192.168.178.1
DHCP4.OPTION[29]:                       dhcp_lease_time = 864000
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
IP6.ADDRESS[1]:                         2001:16b8:2693:e300:b1a4:1680:3b57:9b94/64
IP6.ADDRESS[2]:                         2001:16b8:2693:e300:e453:b52c:3051:ca08/64
IP6.ADDRESS[3]:                         fe80::91ed:a56f:ee85:563b/64
IP6.GATEWAY:                            fe80::eadf:70ff:fe40:7c25
IP6.ROUTE[1]:                           dst = 2001:16b8:2693:e300::/56, nh = fe80::eadf:70ff:fe40:7c25, mt = 100
IP6.ROUTE[2]:                           dst = 2001:16b8:2693:e300::/64, nh = ::, mt = 100
IP6.ROUTE[3]:                           dst = ::/0, nh = fe80::eadf:70ff:fe40:7c25, mt = 100
IP6.ROUTE[4]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[5]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[6]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.DNS[1]:                             fd00::eadf:70ff:fe40:7c25
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = fd00::eadf:70ff:fe40:7c25
DHCP6.OPTION[3]:                        dhcp6_server_id = 0:3:0:1:<MAC address>
DHCP6.OPTION[4]:                        dhcp6_unknown_86 = 20:1:16:b8:26:93:e3:0:ea:df:70:ff:fe:40:7c:25
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[7]:                        dhcp6_client_id = 0:4:35:2:2d:5:8b:5c:de:38:b3:2c:71:8c:30:3f:15:a7
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   1baf7adc-0c6b-3fef-8344-f0be37304b92 | Wired connection 1

GENERAL.DEVICE:                         wlp34s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Limited
GENERAL.PRODUCT:                        BCM4360 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.271 (r587334)
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'wlp34s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:03.1/0000:22:00.0/net/wlp34s0
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
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
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
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   9a58445a-cfb9-4d56-900c-907152d2eed1 | WLAN-Boehm

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 

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

[device]
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/WLAN-Boehm]] (600 root)
[connection] id=WLAN-Boehm | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp34s0' [IF2]> | mac-address-blacklist= | ssid=WLAN-Boehm
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

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

enp30s0   no frequency information.

wlp34s0   32 channels in total; available frequencies :
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
          Channel 32 : 5.16 GHz
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 50 : 5.25 GHz
          Channel 52 : 5.26 GHz
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 58 : 5.29 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 66 : 5.33 GHz

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp30s0   Interface doesn't support scanning.

wlp34s0   No scan results

##### module infos ######################

[wl]
filename:       /lib/modules/4.15.0-22-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     00D38A27B7E3C7B97C238FC
depends:        cfg80211
retpoline:      Y
name:           wl
vermagic:       4.15.0-22-generic SMP mod_unload 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[mac80211]
filename:       /lib/modules/4.15.0-22-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1CEA5CF286EDB289C1D0BF8
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-22-generic SMP mod_unload 
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
filename:       /lib/modules/4.15.0-22-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D5B0789D4C423C81CCFB437
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-22-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
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

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[ 2499.833582] ERROR @wl_notify_scan_status : 
[ 2499.833586] wlp34s0 Scan_results error (-22)

########## wireless info END ############

```
[http://paste.ubuntu.com/p/hYs7nh7Gnn/](http://paste.ubuntu.com/p/hYs7nh7Gnn/)

dmseg says:
```
[ 2499.833582] ERROR @wl_notify_scan_status : 
[ 2499.833586] wlp34s0 Scan_results error (-22)
```

reinstallation of bcmwl-kernel-source didn't solve the problem.

I appreciate your help :)

---

### Post by praseodym on 2018-06-05
Please show
```

dmesg | egrep 'wl|key'
```
SecureBoot is turned off?

---

### Post by potimedia on 2018-06-05
Hey praseodym,
thanks for your reply!
Output:
```

dmesg | egrep 'wl|key'
[    0.802079] Initialise system trusted keyrings
[    0.804759] Asymmetric key parser 'x509' registered
[    0.934988] Loaded X.509 cert 'Build time autogenerated kernel key: 2bae1e8c50dcab357f42f039715f6a76c2f9c3dc'
[    0.939147] Loaded UEFI:MokListRT cert 'Canonical Ltd. Master Certificate Authority: ad91990bc22ab1f517048c23b6655a268e345a63' linked to secondary sys keyring
[    0.942029] Key type big_key registered
[   30.367345] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input5
[   30.510877] PKCS#7 signature not signed with a trusted key
[   30.510885] wl: loading out-of-tree module taints kernel.
[   30.510888] wl: module license 'MIXED/Proprietary' taints kernel.
[   30.512320] wl: module verification failed: signature and/or required key missing - tainting kernel
[   30.514099] wl 0000:22:00.0: enabling device (0000 -> 0002)
[   30.584859] wlan0: Broadcom BCM43a0 802.11 Hybrid Wireless Controller 6.30.223.271 (r587334)
[   30.586076] wl 0000:22:00.0 wlp34s0: renamed from wlan0
[   31.161381] IPv6: ADDRCONF(NETDEV_UP): wlp34s0: link is not ready
[   31.291304] IPv6: ADDRCONF(NETDEV_UP): wlp34s0: link is not ready
[   31.315971] ERROR @wl_notify_scan_status : 
[   31.315975] wlp34s0 Scan_results error (-22)
[   35.055973] ERROR @wl_notify_scan_status : 
[   35.055975] wlp34s0 Scan_results error (-22)
[   58.067968] ERROR @wl_notify_scan_status : 
[   58.067969] wlp34s0 Scan_results error (-22)
[   90.740751] ERROR @wl_notify_scan_status : 
[   90.740753] wlp34s0 Scan_results error (-22)

```
Bios says secure boot is off, but i am not sure about the CRM settings
[ATTACH=CONFIG]279986[/ATTACH][ATTACH=CONFIG]279987[/ATTACH]

---

### Post by potimedia on 2018-06-12
Does anyone have an idea?

---

### Post by Pickel on 2018-08-02
Sometimes there is a physical rfkill switch. Check that it is not disabled.

---

