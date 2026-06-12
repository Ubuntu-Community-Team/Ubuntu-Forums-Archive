---
title: "Realtek 8852 No WiFi in Ubuntu 20.04"
date: 2021-11-02
forum: Networking &amp; Wireless
---

### Post by radut70 on 2021-11-02
I just installed and updated Ubuntu 20.04 on a ThinkPad computer, but WiFi settings do not show up under settings. (I am currently tethered with an iPhone for internet access)
below is my pastebinit:


########## wireless info START ##########

Report from: 02 Nov 2021 08:58 PDT -0700

Booted last: 02 Nov 2021 00:00 PDT -0700

Script from: 25 Jan 2020 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.3 LTS
Release:    20.04
Codename:    focal

##### kernel ############################

Linux 5.11.0-38-generic #42~20.04.1-Ubuntu SMP Tue Sep 28 20:41:07 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0e)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:5095]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8852]
    Subsystem: Lenovo Device [17aa:4852]

04:00.0 USB controller [0c03]: Renesas Technology Corp. uPD720202 USB 3.0 Host Controller [1912:0015] (rev 02)

##### lsusb #############################

Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 003: ID 0bda:4852 Realtek Semiconductor Corp. Bluetooth Radio
Bus 005 Device 002: ID 27c6:6594 Shenzhen Goodix Technology Co.,Ltd. Goodix USB2.0 MISC
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 17ef:60ab Lenovo ThinkPad Essential Wireless Mouse
Bus 003 Device 002: ID 05ac:12a8 Apple, Inc. iPhone5/5C/5S/6
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 5986:213c Acer, Inc Integrated Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

SecureBoot enabled

##### lsmod #############################

wmi_bmof               16384  0
wmi                    32768  1 wmi_bmof

##### interfaces ########################

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0f0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'enp2s0f0' [IF1]> brd <MAC address>
3: enx<IF from MAC [IF2]>: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enx<IF from MAC [IF2]>' [IF2]> brd <MAC address>
    inet 172.20.10.3/28 brd 172.20.10.15 scope global dynamic noprefixroute enx<IF from MAC [IF2]>
       valid_lft 84862sec preferred_lft 84862sec
    inet6 2607:fb90:3129:493a:b527:21fd:f675:62ea/64 scope global temporary dynamic 
       valid_lft 604129sec preferred_lft 85529sec
    inet6 2607:fb90:3129:493a:82f8:e29d:7534:f423/64 scope global mngtmpaddr noprefixroute 
       valid_lft forever preferred_lft forever
    inet6 fe80::6040:359c:c875:a5be/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

enp2s0f0  no wireless extensions.

enx<IF from MAC [IF2]>  no wireless extensions.

##### route #############################

default via 172.20.10.1 dev enx<IF from MAC [IF2]> proto dhcp metric 100 
169.254.0.0/16 dev enx<IF from MAC [IF2]> scope link metric 1000 
172.20.10.0/28 dev enx<IF from MAC [IF2]> proto kernel scope link src 172.20.10.3 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0 trust-ad

##### network managers ##################

Installed:

    NetworkManager

Running:

root         660       1  0 08:47 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enx<IF from MAC [IF2]>
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/3
GENERAL.VENDOR:                         Apple, Inc.
GENERAL.PRODUCT:                        iPhone5/5C/5S/6
GENERAL.DRIVER:                         ipheth
GENERAL.DRIVER-VERSION:                 5.11.0-38-generic
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enx<IF from MAC [IF2]>' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               4 (full)
GENERAL.IP6-CONNECTIVITY:               4 (full)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:08.1/0000:05:00.3/usb3/3-1/3-1:4.2/net/enx<IF from MAC [IF2]>
GENERAL.IP-IFACE:                       enx<IF from MAC [IF2]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 2
GENERAL.CON-UUID:                       eb9b163f-9422-323c-bb8a-ad467f3410a0
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               yes
INTERFACE-FLAGS.CARRIER:                yes
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         172.20.10.3/28
IP4.GATEWAY:                            172.20.10.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 172.20.10.1, mt = 100
IP4.ROUTE[2]:                           dst = 172.20.10.0/28, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             172.20.10.1
DHCP4.OPTION[1]:                        dhcp_lease_time = 85536
DHCP4.OPTION[2]:                        domain_name_servers = 172.20.10.1
DHCP4.OPTION[3]:                        expiry = 1635953570
DHCP4.OPTION[4]:                        ip_address = 172.20.10.3
DHCP4.OPTION[5]:                        next_server = 172.20.10.1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_domain_name = 1
DHCP4.OPTION[8]:                        requested_domain_name_servers = 1
DHCP4.OPTION[9]:                        requested_domain_search = 1
DHCP4.OPTION[10]:                       requested_host_name = 1
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[13]:                       requested_nis_domain = 1
DHCP4.OPTION[14]:                       requested_nis_servers = 1
DHCP4.OPTION[15]:                       requested_ntp_servers = 1
DHCP4.OPTION[16]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[17]:                       requested_root_path = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       requested_static_routes = 1
DHCP4.OPTION[20]:                       requested_subnet_mask = 1
DHCP4.OPTION[21]:                       requested_time_offset = 1
DHCP4.OPTION[22]:                       requested_wpad = 1
DHCP4.OPTION[23]:                       routers = 172.20.10.1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.240
IP6.ADDRESS[1]:                         2607:fb90:3129:493a:b527:21fd:f675:62ea/64
IP6.ADDRESS[2]:                         2607:fb90:3129:493a:82f8:e29d:7534:f423/64
IP6.ADDRESS[3]:                         fe80::6040:359c:c875:a5be/64
IP6.GATEWAY:                            fe80::1019:7369:e98e:5978
IP6.ROUTE[1]:                           dst = 2607:fb90:3129:493a::/64, nh = ::, mt = 100
IP6.ROUTE[2]:                           dst = ::/0, nh = fe80::1019:7369:e98e:5978, mt = 100
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.DNS[1]:                             fe80::1019:7369:e98e:5978
DHCP6.OPTION[1]:                        dhcp6_name_servers = fe80::1019:7369:e98e:5978
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/2
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   eb9b163f-9422-323c-bb8a-ad467f3410a0 | Wired connection 2

GENERAL.DEVICE:                         enp2s0f0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/2
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 5.11.0-38-generic
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp2s0f0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.IP4-CONNECTIVITY:               1 (none)
GENERAL.IP6-CONNECTIVITY:               1 (none)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.2/0000:02:00.0/net/enp2s0f0
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
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               no
INTERFACE-FLAGS.CARRIER:                no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

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
unmanaged-devices=*,except:type:wifi,except:type:gsm,except:type:cdma

[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com/

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

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

lo        no frequency information.

enp2s0f0  no frequency information.

enx<IF from MAC [IF2]>  no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp2s0f0  Interface doesn't support scanning.

enx<IF from MAC [IF2]>  Interface doesn't support scanning.

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

[    2.279809] [drm] Loading DMUB firmware via PSP: version=0x0101000A
[    2.280340] [drm] Found VCN firmware Version ENC: 1.7 DEC: 4 VEP: 0 Revision: 17
[    3.374674] ipheth 3-1:4.2 enx<IF from MAC [IF2]>: renamed from eth0
[    3.579385] r8169 0000:02:00.0 enp2s0f0: Link is Down
[    5.912170] IPv6: ADDRCONF(NETDEV_CHANGE): enx<IF from MAC [IF2]>: link becomes ready

########## wireless info END ############

---

### Post by chili555 on 2021-11-02
Please see my answer here: [https://askubuntu.com/questions/1352260/wifi-adapter-not-found-realtek-10ec8852-on-ubuntu-21-04](https://askubuntu.com/questions/1352260/wifi-adapter-not-found-realtek-10ec8852-on-ubuntu-21-04)

You have the same device and need the same driver.

---

