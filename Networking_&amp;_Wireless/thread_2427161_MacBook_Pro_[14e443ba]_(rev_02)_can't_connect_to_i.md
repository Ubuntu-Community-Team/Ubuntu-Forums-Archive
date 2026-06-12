---
title: "MacBook Pro [14e4:43ba] (rev 02) can't connect to internet Ubuntu 18.04"
date: 2019-09-18
forum: Networking &amp; Wireless
---

### Post by ju4nma on 2019-09-18
Hi, I installed the new version of ubuntu (18.04) in an external hard drive and I run it in my macbook pro 2018.
Since the installation I wasn't able to connect to internet (I authenticated myself and it looped, my credentials were okay, but the connection was never established, and also the wifi bars appear to be very weak) and so i've been trying in different forums to fix this, but I've come to a point in which not even the wifi icon appears. 
I didn't had the wl, when I used modprobe it returned FATAL error, but I was able to include it and excecute the modprobe command.
I found a wireless script and I executed it, I'm attaching it hoping someone can help me with this issue. 



########## wireless info START ##########


Report from: 18 Sep 2019 11:56 CDT -0500


Booted last: 18 Sep 2019 00:00 CDT -0500


Script from: 22 Oct 2018 03:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.3 LTS
Release:	18.04
Codename:	bionic


##### kernel ############################


Linux 5.0.0-29-generic #31~18.04.1-Ubuntu SMP Thu Sep 12 18:29:21 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux


\\boot\vmlinuz-5.0.0-29-generic, ro, initrd=boot\initrd.img-5.0.0-29-generic


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43602 802.11ac Wireless LAN SoC [14e4:43ba] (rev 02)
	Subsystem: Apple Inc. BCM43602 802.11ac Wireless LAN SoC [106b:0173]
	Kernel modules: brcmfmac, wl


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 05ac:1460 Apple, Inc. 
Bus 001 Device 005: ID 03f0:110c Hewlett-Packard 
Bus 001 Device 003: ID 05ac:100f Apple, Inc. 
Bus 001 Device 002: ID 05ac:8600 Apple, Inc. 
Bus 001 Device 004: ID 050d:090b Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 05ac:100e Apple, Inc. 
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 050d:090c Belkin Components 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### secure boot #######################


This system doesn't support Secure Boot


##### lsmod #############################


wl                   6447104  0
cfg80211              675840  1 wl


##### interfaces ########################


[/etc/network/interfaces]
auto lo
iface lo inet loopback


##### ifconfig ##########################


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: bnep0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 1000
    link/ether <MAC 'bnep0' [IF1]> brd <MAC address>
    inet 172.20.10.5/28 brd 172.20.10.15 scope global dynamic noprefixroute bnep0
       valid_lft 85301sec preferred_lft 85301sec
    inet6 fe80::e7a6:815e:bf4:48aa/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever


##### iwconfig ##########################


bnep0     no wireless extensions.


lo        no wireless extensions.


##### route #############################


default via 172.20.10.1 dev bnep0 proto dhcp metric 750 
169.254.0.0/16 dev bnep0 scope link metric 1000 
172.20.10.0/28 dev bnep0 proto kernel scope link src 172.20.10.5 metric 750 


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']


nameserver 127.0.0.53
options edns0


##### network managers ##################


Installed:


	NetworkManager


Running:


root       869     1  0 11:51 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         <MAC address>
GENERAL.TYPE:                           bt
GENERAL.NM-TYPE:                        NMDeviceBt
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         bluez
GENERAL.DRIVER-VERSION:                 --
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /org/bluez/hci0/dev_FC_2A_9C_73_A1_97
GENERAL.IP-IFACE:                       bnep0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     iPhone de Juan Ma Network
GENERAL.CON-UUID:                       3de201c8-cb36-49a2-94ef-2944acfcbcd2
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
IP4.ADDRESS[1]:                         172.20.10.5/28
IP4.GATEWAY:                            172.20.10.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 172.20.10.1, mt = 750
IP4.ROUTE[2]:                           dst = 172.20.10.0/28, nh = 0.0.0.0, mt = 750
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             172.20.10.1
DHCP4.OPTION[1]:                        requested_host_name = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        server_name = iPhone-de-Juan-Ma
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        requested_netbios_scope = 1
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       next_server = 172.20.10.1
DHCP4.OPTION[11]:                       broadcast_address = 172.20.10.15
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       routers = 172.20.10.1
DHCP4.OPTION[15]:                       dhcp_lease_time = 85536
DHCP4.OPTION[16]:                       requested_subnet_mask = 1
DHCP4.OPTION[17]:                       subnet_mask = 255.255.255.240
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       expiry = 1568911122
DHCP4.OPTION[21]:                       domain_name_servers = 172.20.10.1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_ntp_servers = 1
DHCP4.OPTION[25]:                       requested_routers = 1
DHCP4.OPTION[26]:                       network_number = 172.20.10.0
DHCP4.OPTION[27]:                       dhcp_server_identifier = 172.20.10.1
DHCP4.OPTION[28]:                       ip_address = 172.20.10.5
IP6.ADDRESS[1]:                         fe80::e7a6:815e:bf4:48aa/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 750
BLUETOOTH.CAPABILITIES:                 NAP
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{4}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   3de201c8-cb36-49a2-94ef-2944acfcbcd2 | iPhone de Juan Ma Network


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


[[/etc/NetworkManager/system-connections/Tec-Visitantes]] (600 root)
[connection] id=Tec-Visitantes | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Tec-Visitantes
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Tec]] (600 root)
[connection] id=Tec | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Tec
[ipv4] method=auto
[ipv6] method=auto


##### Netplan config ####################


[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager


##### iw reg get ########################


Region: America/Mexico_City (based on set time zone)


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


##### iwlist channels ###################


bnep0     no frequency information.


lo        no frequency information.


##### iwlist scan #######################


bnep0     Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[wl]
filename:       /lib/modules/5.0.0-29-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     00D38A27B7E3C7B97C238FC
depends:        cfg80211
retpoline:      Y
name:           wl
vermagic:       5.0.0-29-generic SMP mod_unload 
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


[cfg80211]
filename:       /lib/modules/5.0.0-29-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     8F0CAF5346FF71FCE9CB198
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.0.0-29-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/BCM43602.conf]
options BCM43602 fwlps=N


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


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


[/etc/pm/sleep.d/config] (644 root)
SUSPEND_MODULES="BCM43602"


##### udev rules ########################


##### dmesg #############################


########## wireless info END ############

Thanks

---

