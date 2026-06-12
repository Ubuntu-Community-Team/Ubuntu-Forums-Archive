---
title: "TUF FX505DV AMD Ryzen 7"
date: 2020-04-12
forum: Networking &amp; Wireless
---

### Post by dhiaul98 on 2020-04-12
My laptop using dual boot, windows and ubuntu 18.04. In Windows OS, this WiFi worked, but not in ubuntu 18.04


########## wireless info START ##########


```
Report from: 12 Apr 2020 23:58 WIB +0700


Booted last: 12 Apr 2020 00:00 WIB +0700


Script from: 22 Oct 2018 03:34 UTC +0000

```

##### release ###########################


```
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.4 LTS
Release:    18.04
Codename:    bionic


```
##### kernel ############################


```
Linux 5.3.0-46-generic #38~18.04.1-Ubuntu SMP Tue Mar 31 04:17:56 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=1

```

##### desktop ###########################


```
Ubuntu
```


##### lspci #############################

```

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:208f]
    Kernel driver in use: r8169


04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:c822]
    Subsystem: AzureWave Device [1a3b:3750]
    Kernel modules: rtwpci, wl

```

##### lsusb #############################


```
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 002: ID 13d3:56a2 IMC Networks 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 13d3:3548 IMC Networks 
Bus 003 Device 005: ID 0fce:81e7 Sony Ericsson Mobile Communications AB 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```
##### PCMCIA card info ##################


##### rfkill ############################

```

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


```
##### secure boot #######################


```
SecureBoot disabled

```

##### lsmod #############################


```
wl                   6451200  0
asus_nb_wmi            28672  0
asus_wmi               32768  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
mac80211              847872  2 rtwpci,rtw88
wmi_bmof               16384  0
cfg80211              704512  3 wl,mac80211,rtw88
libarc4                16384  1 mac80211
wmi                    32768  2 asus_wmi,wmi_bmof
video                  49152  1 asus_wmi

```

##### interfaces ########################


```
[/etc/network/interfaces]
auto lo
iface lo inet loopback

```

##### ifconfig ##########################


```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'enp2s0' [IF1]> brd <MAC address>
3: enp5s0f3u3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 1000
    link/ether <MAC 'enp5s0f3u3' [IF2]> brd <MAC address>
    inet 192.168.42.81/24 brd 192.168.42.255 scope global dynamic noprefixroute enp5s0f3u3
       valid_lft 7149sec preferred_lft 7149sec
    inet6 fe80::8cb2:549d:4a5b:9d0b/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever


```
##### iwconfig ##########################


```
lo        no wireless extensions.


enp5s0f3u3  no wireless extensions.


enp2s0    no wireless extensions.


```
##### route #############################


```
default via 192.168.42.129 dev enp5s0f3u3 proto dhcp metric 100 
169.254.0.0/16 dev enp5s0f3u3 scope link metric 1000 
192.168.42.0/24 dev enp5s0f3u3 proto kernel scope link src 192.168.42.81 metric 100 


```
##### resolv.conf #######################


```
[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']


nameserver 127.0.0.53
options edns0

```

##### network managers ##################


```
Installed:


    NetworkManager


Running:


root       863     1  0 23:57 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon 
```


##### NetworkManager info ###############


```
GENERAL.DEVICE:                         enp5s0f3u3
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Sony
GENERAL.PRODUCT:                        SO-01J
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'enp5s0f3u3' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:08.1/0000:05:00.3/usb3/3-3/3-3:1.0/net/enp5s0f3u3
GENERAL.IP-IFACE:                       enp5s0f3u3
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       a9a899f5-0935-32d2-bb1c-b927cea7af1e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.42.81/24
IP4.GATEWAY:                            192.168.42.129
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.42.129, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.42.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[5]:                        ip_address = 192.168.42.81
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.42.129
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.42.255
DHCP4.OPTION[10]:                       dhcp_rebinding_time = 6300
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.42.129
DHCP4.OPTION[16]:                       dhcp_renewal_time = 3600
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1586717853
DHCP4.OPTION[20]:                       host_name = anu
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.42.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       next_server = 192.168.42.129
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[30]:                       dhcp_lease_time = 7200
DHCP4.OPTION[31]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         fe80::8cb2:549d:4a5b:9d0b/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{12}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   a9a899f5-0935-32d2-bb1c-b927cea7af1e | Wired connection 1


GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 --
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/net/enp2s0
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
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --
```


##### NetworkManager.state ##############


```
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


```
##### NetworkManager config #############


```
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
unmanaged-devices=*,except:type:wifi,except:type:wwan


[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com/


[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=AndroidAP
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Network]] (600 root)
[connection] id=Network | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Network
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/JTE-WIFI]] (600 root)
[connection] id=JTE-WIFI | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=JTE-WIFI
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/dhiaul]] (600 root)
[connection] id=dhiaul | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=dhiaul
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ROBOTAN 5G]] (600 root)
[connection] id=ROBOTAN 5G | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=ROBOTAN 5G
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Network 1]] (600 root)
[connection] id=Network 1 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Network
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/MADE]] (600 root)
[connection] id=MADE | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=MADE
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/B201AP]] (600 root)
[connection] id=B201AP | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=B201AP
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Burgerking@wifi.id]] (600 root)
[connection] id=Burgerking@wifi.id | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Burgerking@wifi.id
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Kost Ucu]] (600 root)
[connection] id=Kost Ucu | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Kost Ucu
[ipv4] method=auto
[ipv6] method=auto

```

##### Netplan config ####################


```
[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager


```
##### iw reg get ########################


```
Region: Asia/Jakarta (based on set time zone)


global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

```

##### iwlist channels ###################


```
lo        no frequency information.


enp5s0f3u3  no frequency information.


enp2s0    no frequency information.

```

##### iwlist scan #######################


```
lo        Interface doesn't support scanning.


enp5s0f3u3  Interface doesn't support scanning.


enp2s0    Interface doesn't support scanning.


```
##### module infos ######################


```
[wl]
filename:       /lib/modules/5.3.0-46-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     00D38A27B7E3C7B97C238FC
depends:        cfg80211
retpoline:      Y
name:           wl
vermagic:       5.3.0-46-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


[mac80211]
filename:       /lib/modules/5.3.0-46-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     FF7B32E98E39253BED62468
depends:        cfg80211,libarc4
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       5.3.0-46-generic SMP mod_unload 
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
filename:       /lib/modules/5.3.0-46-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     8F07355AEBF42CFCE5139A3
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.3.0-46-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

```

##### module parameters #################


```
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


```
##### /etc/modules ######################


##### modprobe options ##################


```
[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode


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


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/libopenni-sensor-pointclouds0.conf]
blacklist gspca_kinect
```


##### rc.local ##########################


```
grep: /etc/rc.local: No such file or directory
```

##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


```
[    4.107785] r8169 0000:02:00.0 enp2s0: Link is Down
[    7.257962] rndis_host 3-3:1.0 enp5s0f3u3: renamed from usb0
```


########## wireless info END ############

---

### Post by CelticWarrior on 2020-04-12
Your hardware is newer than the Ubuntu release you installed. Try 20.04 instead.

---

