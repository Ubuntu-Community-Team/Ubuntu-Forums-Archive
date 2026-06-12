---
title: "No Wi-Fi or Bluetooth after fresh install"
date: 2019-12-22
forum: Networking &amp; Wireless
---

### Post by chrisflanary on 2019-12-22
I just did a fresh install of ubuntu. After installing i no longer had wifi options appearing in settings and the Bluetooth option is still there but says no bt found and to plug in a dongle. Ive tried to figure it out including doing another install and nothing is giving me wifi or Bluetooth. They were both working fine before I did the fresh install. Hopefully somebody can give me some ideas on what to do to fix it. Thank you

---

### Post by praseodym on 2019-12-23
Please run the wireless script from the sticky thread and show the outputs

---

### Post by chrisflanary on 2019-12-23
i put xxx for the last 3 of my ip address tho but heres the output of the script. i hope you or someone can help me figure out the wifi and bluetooth problem. thank you


```
########## wireless info START ##########


Report from: 23 Dec 2019 23:32 EST -0500


Booted last: 23 Dec 2019 00:00 EST -0500


Script from: 22 Oct 2018 03:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 19.10
Release:	19.10
Codename:	eoan


##### kernel ############################


Linux 5.3.0-24-generic #26-Ubuntu SMP Thu Nov 14 01:33:18 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:0123]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### secure boot #######################


SecureBoot disabled


##### lsmod #############################


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
2: enp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp1s0' [IF1]> brd <MAC address>
    inet 10.0.0.225/24 brd 10.0.0.255 scope global dynamic noprefixroute enp1s0
       valid_lft 604149sec preferred_lft 604149sec
    inet6 2601:144:202:9ec0::bb58/128 scope global dynamic noprefixroute 
       valid_lft 604151sec preferred_lft 604151sec
    inet6 2601:144:202:9ec0:f590:d20e:5bec:eabb/64 scope global temporary dynamic 
       valid_lft 293224sec preferred_lft 85266sec
    inet6 2601:144:202:9ec0:5ba2:c4c9:cd4c:2882/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 293224sec preferred_lft 293224sec
    inet6 fe80::f09c:ac06:a825:ab73/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever


##### iwconfig ##########################


enp1s0    no wireless extensions.


lo        no wireless extensions.


##### route #############################


default via 10.0.0.1 dev enp1s0 proto dhcp metric 100 
10.0.0.0/24 dev enp1s0 proto kernel scope link src 10.0.0.xxx metric 100 
169.254.0.0/16 dev enp1s0 scope link metric 1000 


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']


nameserver 127.0.0.53
options edns0
search hsd1.va.comcast.net


##### network managers ##################


Installed:


	NetworkManager


Running:


root       989     1  0 23:22 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 --
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               4 (full)
GENERAL.IP6-CONNECTIVITY:               3 (limited)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:13.0/0000:01:00.0/net/enp1s0
GENERAL.IP-IFACE:                       enp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Home
GENERAL.CON-UUID:                       bdaa552a-056b-3b4f-8aae-387ae1ed6e9e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         10.0.0.xxx/xx
IP4.GATEWAY:                            10.0.0.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 10.0.0.1, mt = 100
IP4.ROUTE[2]:                           dst = 10.0.0.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             75.75.75.75
IP4.DNS[2]:                             75.75.76.76
IP4.DOMAIN[1]:                          hsd1.va.comcast.net
DHCP4.OPTION[1]:                        broadcast_address = 10.0.0.xxx
DHCP4.OPTION[2]:                        dhcp_lease_time = 604800
DHCP4.OPTION[3]:                        dhcp_rebinding_time = 529200
DHCP4.OPTION[4]:                        dhcp_renewal_time = 302400
DHCP4.OPTION[5]:                        dhcp_server_identifier = 10.0.0.1
DHCP4.OPTION[6]:                        domain_name = hsd1.va.comcast.net
DHCP4.OPTION[7]:                        domain_name_servers = 75.75.75.75 75.75.76.76
DHCP4.OPTION[8]:                        expiry = 1577766128
DHCP4.OPTION[9]:                        host_name = ghost-2
DHCP4.OPTION[10]:                       ip_address = 10.0.0.xxx
DHCP4.OPTION[11]:                       requested_broadcast_address = 1
DHCP4.OPTION[12]:                       requested_dhcp_server_identifier = 1
DHCP4.OPTION[13]:                       requested_domain_name = 1
DHCP4.OPTION[14]:                       requested_domain_name_servers = 1
DHCP4.OPTION[15]:                       requested_domain_search = 1
DHCP4.OPTION[16]:                       requested_host_name = 1
DHCP4.OPTION[17]:                       requested_interface_mtu = 1
DHCP4.OPTION[18]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[19]:                       requested_nis_domain = 1
DHCP4.OPTION[20]:                       requested_nis_servers = 1
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[23]:                       requested_root_path = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       requested_static_routes = 1
DHCP4.OPTION[26]:                       requested_subnet_mask = 1
DHCP4.OPTION[27]:                       requested_time_offset = 1
DHCP4.OPTION[28]:                       requested_wpad = 1
DHCP4.OPTION[29]:                       routers = 10.0.0.1
DHCP4.OPTION[30]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         2601:144:202:9ec0::bb58/128
IP6.ADDRESS[2]:                         2601:144:202:9ec0:f590:d20e:5bec:eabb/64
IP6.ADDRESS[3]:                         2601:144:202:9ec0:5ba2:c4c9:cd4c:2882/64
IP6.ADDRESS[4]:                         fe80::f09c:ac06:a825:ab73/64
IP6.GATEWAY:                            fe80::7a23:aeff:fe7b:76b6
IP6.ROUTE[1]:                           dst = 2601:144:202:9ec0::/64, nh = ::, mt = 100
IP6.ROUTE[2]:                           dst = ::/0, nh = fe80::7a23:aeff:fe7b:76b6, mt = 20100
IP6.ROUTE[3]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[4]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.ROUTE[5]:                           dst = 2601:144:202:9ec0::bb58/128, nh = ::, mt = 100
IP6.DNS[1]:                             2001:558:feed::1
IP6.DNS[2]:                             2001:558:feed::2
DHCP6.OPTION[1]:                        dhcp6_name_servers = 2001:558:feed::1 2001:558:feed::2
DHCP6.OPTION[2]:                        ip6_address = 2601:144:202:9ec0::bb58
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/1
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   bdaa552a-056b-3b4f-8aae-387ae1ed6e9e | Home


##### NetworkManager.state ##############


cat: /var/lib/NetworkManager/NetworkManager.state: Permission denied


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
unmanaged-devices=*,except:type:wifi,except:type:gsm,except:type:cdma


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


##### Netplan config ####################


[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager


##### iw reg get ########################


Region: America/New_York (based on set time zone)


global
country 00: DFS-UNSET
	(2402 - 2472 @ 40), (6, 20), (N/A)
	(2457 - 2482 @ 20), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
	(2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 80), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
	(5250 - 5330 @ 80), (6, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
	(5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
	(5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


enp1s0    no frequency information.


lo        no frequency information.


##### iwlist scan #######################


enp1s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


##### module parameters #################


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode


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


##### udev rules ########################


##### dmesg #############################


[    8.070306] r8169 0000:01:00.0 enp1s0: Link is Down
[   11.578123] r8169 0000:01:00.0 enp1s0: Link is Up - 1Gbps/Full - flow control rx/tx
[   11.578143] IPv6: ADDRCONF(NETDEV_CHANGE): enp1s0: link becomes ready
[  111.564064] [UFW BLOCK] IN=enp1s0 OUT= MAC=01:00:5e:00:00:01:78:23:ae:7b:76:b6:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=60808 PROTO=2 
[  111.927351] [UFW BLOCK] IN=enp1s0 OUT= MAC=01:00:5e:00:00:fb:14:91:82:f8:2d:45:08:00 SRC=10.0.0.129 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  174.044098] [UFW BLOCK] IN=enp1s0 OUT= MAC=01:00:5e:00:00:01:78:23:ae:7b:76:b6:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=60809 PROTO=2 
[  174.874244] [UFW BLOCK] IN=enp1s0 OUT= MAC=01:00:5e:00:00:fb:14:91:82:f8:2d:45:08:00 SRC=10.0.0.129 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  236.563987] [UFW BLOCK] IN=enp1s0 OUT= MAC=01:00:5e:00:00:01:78:23:ae:7b:76:b6:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=60810 PROTO=2 
[  237.242261] [UFW BLOCK] IN=enp1s0 OUT= MAC=01:00:5e:00:00:fb:14:91:82:f8:2d:45:08:00 SRC=10.0.0.129 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  262.624295] [UFW BLOCK] IN=enp1s0 OUT= MAC=01:00:5e:00:00:fb:78:23:ae:7b:76:b6:08:00 SRC=10.0.0.1 DST=224.0.0.251 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=7792 PROTO=2 
[  262.631270] [UFW BLOCK] IN=enp1s0 OUT= MAC=01:00:5e:00:00:fb:14:91:82:f8:2d:45:08:00 SRC=10.0.0.129 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  361.565188] [UFW BLOCK] IN=enp1s0 OUT= MAC=01:00:5e:00:00:01:78:23:ae:7b:76:b6:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=60811 PROTO=2 
[  361.698425] [UFW BLOCK] IN=enp1s0 OUT= MAC=01:00:5e:00:00:fb:14:91:82:f8:2d:45:08:00 SRC=10.0.0.129 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  405.062561] [UFW BLOCK] IN=enp1s0 OUT= MAC=<MAC 'enp1s0' [IF1]>:3c:8d:20:04:67:ad:08:00 SRC=10.0.0.161 DST=10.0.0.225 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=58848 DPT=51703 LEN=522 
[  406.084712] [UFW BLOCK] IN=enp1s0 OUT= MAC=<MAC 'enp1s0' [IF1]>:3c:8d:20:04:67:ad:08:00 SRC=10.0.0.161 DST=10.0.0.225 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=37341 DPT=51703 LEN=522 
[  407.108462] [UFW BLOCK] IN=enp1s0 OUT= MAC=<MAC 'enp1s0' [IF1]>:3c:8d:20:04:67:ad:08:00 SRC=10.0.0.161 DST=10.0.0.225 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=33260 DPT=51703 LEN=522 
[  408.132779] [UFW BLOCK] IN=enp1s0 OUT= MAC=<MAC 'enp1s0' [IF1]>:3c:8d:20:04:67:ad:08:00 SRC=10.0.0.161 DST=10.0.0.225 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=37208 DPT=51703 LEN=522 
[  425.354738] [UFW BLOCK] IN=enp1s0 OUT= MAC=01:00:5e:00:00:01:78:23:ae:7b:76:b6:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=60812 PROTO=2 
[  425.976336] [UFW BLOCK] IN=enp1s0 OUT= MAC=01:00:5e:00:00:fb:14:91:82:f8:2d:45:08:00 SRC=10.0.0.129 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  486.565288] [UFW BLOCK] IN=enp1s0 OUT= MAC=01:00:5e:00:00:01:78:23:ae:7b:76:b6:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=60813 PROTO=2 
[  487.128300] [UFW BLOCK] IN=enp1s0 OUT= MAC=01:00:5e:00:00:fb:14:91:82:f8:2d:45:08:00 SRC=10.0.0.129 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  524.872858] [UFW BLOCK] IN=enp1s0 OUT= MAC=<MAC 'enp1s0' [IF1]>:3c:8d:20:04:67:ad:08:00 SRC=10.0.0.161 DST=10.0.0.225 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=36778 DPT=59116 LEN=522 
[  525.794549] [UFW BLOCK] IN=enp1s0 OUT= MAC=<MAC 'enp1s0' [IF1]>:3c:8d:20:04:67:ad:08:00 SRC=10.0.0.161 DST=10.0.0.225 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=38231 DPT=59116 LEN=522 
[  526.818308] [UFW BLOCK] IN=enp1s0 OUT= MAC=<MAC 'enp1s0' [IF1]>:3c:8d:20:04:67:ad:08:00 SRC=10.0.0.161 DST=10.0.0.225 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=59313 DPT=59116 LEN=522 
[  527.842721] [UFW BLOCK] IN=enp1s0 OUT= MAC=<MAC 'enp1s0' [IF1]>:3c:8d:20:04:67:ad:08:00 SRC=10.0.0.161 DST=10.0.0.225 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=32779 DPT=59116 LEN=522 
[  611.566427] [UFW BLOCK] IN=enp1s0 OUT= MAC=01:00:5e:00:00:01:78:23:ae:7b:76:b6:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=60814 PROTO=2 
[  612.122312] [UFW BLOCK] IN=enp1s0 OUT= MAC=01:00:5e:00:00:fb:14:91:82:f8:2d:45:08:00 SRC=10.0.0.129 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  644.787363] [UFW BLOCK] IN=enp1s0 OUT= MAC=<MAC 'enp1s0' [IF1]>:3c:8d:20:04:67:ad:08:00 SRC=10.0.0.161 DST=10.0.0.225 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=43907 DPT=49496 LEN=522 
[  645.812051] [UFW BLOCK] IN=enp1s0 OUT= MAC=<MAC 'enp1s0' [IF1]>:3c:8d:20:04:67:ad:08:00 SRC=10.0.0.161 DST=10.0.0.225 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=43919 DPT=49496 LEN=522 
[  646.835235] [UFW BLOCK] IN=enp1s0 OUT= MAC=<MAC 'enp1s0' [IF1]>:3c:8d:20:04:67:ad:08:00 SRC=10.0.0.161 DST=10.0.0.225 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=46119 DPT=49496 LEN=522 
[  647.858744] [UFW BLOCK] IN=enp1s0 OUT= MAC=<MAC 'enp1s0' [IF1]>:3c:8d:20:04:67:ad:08:00 SRC=10.0.0.161 DST=10.0.0.225 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=36373 DPT=49496 LEN=522 


########## wireless info END ############
```

---

### Post by praseodym on 2019-12-24
First, your firewall blocks anything:

```
sudo apt-get remove --purge ufw gufw
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```
Reboot and show
```

lspci -nnk
```

---

### Post by chrisflanary on 2019-12-24
heres the outcome of lspci -nnk i entered after removing the firewall with the commands you posted and  rebooting. thank you again for your help so far.

lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Host Bridge [8086:5af0] (rev 0b)
	DeviceName: Onboard - Other
	Subsystem: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Host Bridge [8086:7270]
00:00.1 Signal processing controller [1180]: Intel Corporation Device [8086:5a8c] (rev 0b)
	DeviceName: Onboard - Other
	Kernel driver in use: proc_thermal
	Kernel modules: processor_thermal_device
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:5a85] (rev 0b)
	DeviceName: Onboard - Video
	Subsystem: Intel Corporation Device [8086:2212]
	Kernel driver in use: i915
	Kernel modules: i915
00:03.0 Multimedia controller [0480]: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Imaging Unit [8086:5a88] (rev 0b)
	DeviceName: Onboard - Sound
00:0e.0 Audio device [0403]: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Audio Cluster [8086:5a98] (rev 0b)
	DeviceName: Onboard - Sound
	Subsystem: Realtek Semiconductor Co., Ltd. Celeron N3350/Pentium N4200/Atom E3900 Series Audio Cluster [10ec:10fc]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel, snd_soc_skl, sof_pci_dev
00:0f.0 Communication controller [0780]: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Trusted Execution Engine [8086:5a9a] (rev 0b)
	DeviceName: Onboard - Other
	Subsystem: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Trusted Execution Engine [8086:7270]
	Kernel driver in use: mei_me
	Kernel modules: mei_me
00:12.0 SATA controller [0106]: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series SATA AHCI Controller [8086:5ae3] (rev 0b)
	DeviceName: Onboard - SATA
	Subsystem: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series SATA AHCI Controller [8086:7270]
	Kernel driver in use: ahci
	Kernel modules: ahci
00:13.0 PCI bridge [0604]: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series PCI Express Port A #1 [8086:5ad8] (rev fb)
	Kernel driver in use: pcieport
00:14.0 PCI bridge [0604]: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series PCI Express Port B #1 [8086:5ad6] (rev fb)
	Kernel driver in use: pcieport
00:15.0 USB controller [0c03]: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series USB xHCI [8086:5aa8] (rev 0b)
	DeviceName: Onboard - Other
	Subsystem: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series USB xHCI [8086:7270]
	Kernel driver in use: xhci_hcd
00:1c.0 SD Host controller [0805]: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series eMMC Controller [8086:5acc] (rev 0b)
	DeviceName: Onboard - Other
	Subsystem: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series eMMC Controller [8086:7270]
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci_pci
00:1f.0 ISA bridge [0601]: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Low Pin Count Interface [8086:5ae8] (rev 0b)
	DeviceName: Onboard - Other
	Subsystem: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Low Pin Count Interface [8086:7270]
	Kernel driver in use: lpc_ich
	Kernel modules: lpc_ich
00:1f.1 SMBus [0c05]: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series SMBus Controller [8086:5ad4] (rev 0b)
	DeviceName: Onboard - Other
	Subsystem: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series SMBus Controller [8086:7270]
	Kernel driver in use: i801_smbus
	Kernel modules: i2c_i801
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:0123]
	Kernel driver in use: r8169
	Kernel modules: r8169

---

### Post by praseodym on 2019-12-25
I dont see a card. Please run

```
cat /sys/bus/sdio/devices/*
cat /sys/bus/sdio/devices/*/uevent
```

---

### Post by chrisflanary on 2019-12-25
both commands come back as the directory not existing. like i said in the original post, before i did the fresh install, i had wifi and bt working perfectly so i know the build has the capability for them. i didnt do anything except reinstall ubuntu so i dont know what happened to make them not work or not show at all for the option to use them

---

### Post by praseodym on 2019-12-25
Lets check

```
dpkg -l linux-* | grep ii
```

---

### Post by chrisflanary on 2019-12-25
ok here is the outcome of the command:

dpkg -l linux-* | grep ii
ii  linux-base                            4.5ubuntu2           all          Linux image base package
ii  linux-firmware                        1.183.3              all          Firmware for Linux kernel drivers
ii  linux-generic                         5.3.0.24.28          amd64        Complete Generic Linux kernel and headers
ii  linux-headers-5.3.0-24                5.3.0-24.26          all          Header files related to Linux kernel version 5.3.0
ii  linux-headers-5.3.0-24-generic        5.3.0-24.26          amd64        Linux kernel headers for version 5.3.0 on 64 bit x86 SMP
ii  linux-headers-generic                 5.3.0.24.28          amd64        Generic Linux kernel headers
ii  linux-image-5.0.0-37-generic          5.0.0-37.40          amd64        Signed kernel image generic
ii  linux-image-5.3.0-24-generic          5.3.0-24.26          amd64        Signed kernel image generic
ii  linux-image-generic                   5.3.0.24.28          amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                  5.3.0-24.26          amd64        Linux Kernel Headers for development
ii  linux-modules-5.0.0-37-generic        5.0.0-37.40          amd64        Linux kernel extra modules for version 5.0.0 on 64 bit x86 SMP
ii  linux-modules-5.3.0-24-generic        5.3.0-24.26          amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.0.0-37-generic  5.0.0-37.40          amd64        Linux kernel extra modules for version 5.0.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.3.0-24-generic  5.3.0-24.26          amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
ii  linux-signed-generic                  5.3.0.24.28          amd64        Complete Signed Generic Linux kernel and headers (dummy transitional package)
ii  linux-sound-base                      1.0.25+dfsg-0ubuntu5 all          base package for ALSA and OSS sound systems

---

