---
title: "USB AC 1200 WLAN Driver - No WiFi Adapter Found"
date: 2019-10-25
forum: Networking &amp; Wireless
---

### Post by paddy510 on 2019-10-25
Hey, I've got problems getting my wireless connection to work. 

[https://ubuntuforums.org/showthread.php?t=2394372&p=13776566#post13776566](https://ubuntuforums.org/showthread.php?t=2394372&p=13776566#post13776566)

I've got the adapter from this thread and followed the instructions posted by Chili. I got the same error as Muldengold on page 2.

I tried the instructions of Chili from page 3, but I got this output when trying to use make:

```
make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/5.0.0-32-generic/build M=/home/patrick/rtl8822bu  modules
make[1]: Verzeichnis „/usr/src/linux-headers-5.0.0-32-generic“ wird betreten
  CC [M]  /home/patrick/rtl8822bu/core/rtw_cmd.o
  CC [M]  /home/patrick/rtl8822bu/core/rtw_security.o
  CC [M]  /home/patrick/rtl8822bu/core/rtw_debug.o
  CC [M]  /home/patrick/rtl8822bu/core/rtw_io.o
  CC [M]  /home/patrick/rtl8822bu/core/rtw_ioctl_query.o
  CC [M]  /home/patrick/rtl8822bu/core/rtw_ioctl_set.o
  CC [M]  /home/patrick/rtl8822bu/core/rtw_ieee80211.o
  CC [M]  /home/patrick/rtl8822bu/core/rtw_mlme.o
  CC [M]  /home/patrick/rtl8822bu/core/rtw_mlme_ext.o
  CC [M]  /home/patrick/rtl8822bu/core/rtw_mi.o
  CC [M]  /home/patrick/rtl8822bu/core/rtw_wlan_util.o
  CC [M]  /home/patrick/rtl8822bu/core/rtw_vht.o
  CC [M]  /home/patrick/rtl8822bu/core/rtw_pwrctrl.o
  CC [M]  /home/patrick/rtl8822bu/core/rtw_rf.o
  CC [M]  /home/patrick/rtl8822bu/core/rtw_recv.o
  CC [M]  /home/patrick/rtl8822bu/core/rtw_sta_mgt.o
  CC [M]  /home/patrick/rtl8822bu/core/rtw_ap.o
  CC [M]  /home/patrick/rtl8822bu/core/mesh/rtw_mesh.o
  CC [M]  /home/patrick/rtl8822bu/core/mesh/rtw_mesh_pathtbl.o
  CC [M]  /home/patrick/rtl8822bu/core/mesh/rtw_mesh_hwmp.o
  CC [M]  /home/patrick/rtl8822bu/core/rtw_xmit.o
  CC [M]  /home/patrick/rtl8822bu/core/rtw_p2p.o
  CC [M]  /home/patrick/rtl8822bu/core/rtw_rson.o
  CC [M]  /home/patrick/rtl8822bu/core/rtw_tdls.o
  CC [M]  /home/patrick/rtl8822bu/core/rtw_br_ext.o
  CC [M]  /home/patrick/rtl8822bu/core/rtw_iol.o
  CC [M]  /home/patrick/rtl8822bu/core/rtw_sreset.o
  CC [M]  /home/patrick/rtl8822bu/core/rtw_btcoex_wifionly.o
  CC [M]  /home/patrick/rtl8822bu/core/rtw_btcoex.o
  CC [M]  /home/patrick/rtl8822bu/core/rtw_beamforming.o
  CC [M]  /home/patrick/rtl8822bu/core/rtw_odm.o
  CC [M]  /home/patrick/rtl8822bu/core/rtw_rm.o
  CC [M]  /home/patrick/rtl8822bu/core/rtw_rm_fsm.o
  CC [M]  /home/patrick/rtl8822bu/core/efuse/rtw_efuse.o
  CC [M]  /home/patrick/rtl8822bu/os_dep/osdep_service.o
  CC [M]  /home/patrick/rtl8822bu/os_dep/linux/os_intfs.o
  CC [M]  /home/patrick/rtl8822bu/os_dep/linux/usb_intf.o
  CC [M]  /home/patrick/rtl8822bu/os_dep/linux/usb_ops_linux.o
  CC [M]  /home/patrick/rtl8822bu/os_dep/linux/ioctl_linux.o
  CC [M]  /home/patrick/rtl8822bu/os_dep/linux/xmit_linux.o
  CC [M]  /home/patrick/rtl8822bu/os_dep/linux/mlme_linux.o
  CC [M]  /home/patrick/rtl8822bu/os_dep/linux/recv_linux.o
  CC [M]  /home/patrick/rtl8822bu/os_dep/linux/ioctl_cfg80211.o
  CC [M]  /home/patrick/rtl8822bu/os_dep/linux/rtw_cfgvendor.o
/home/patrick/rtl8822bu/os_dep/linux/rtw_cfgvendor.c:1403:4: error: ‘const struct wiphy_vendor_command’ has no member named ‘policy’
   .policy = VENDOR_CMD_RAW_DATA,
    ^~~~~~
/home/patrick/rtl8822bu/os_dep/linux/rtw_cfgvendor.c:1403:13: error: ‘VENDOR_CMD_RAW_DATA’ undeclared here (not in a function); did you mean ‘VENDOR_CMD_MAX_DATA_LEN’?
   .policy = VENDOR_CMD_RAW_DATA,
             ^~~~~~~~~~~~~~~~~~~
             VENDOR_CMD_MAX_DATA_LEN
/home/patrick/rtl8822bu/os_dep/linux/rtw_cfgvendor.c:1412:4: error: ‘const struct wiphy_vendor_command’ has no member named ‘policy’
   .policy = VENDOR_CMD_RAW_DATA,
    ^~~~~~
/home/patrick/rtl8822bu/os_dep/linux/rtw_cfgvendor.c:1421:4: error: ‘const struct wiphy_vendor_command’ has no member named ‘policy’
   .policy = VENDOR_CMD_RAW_DATA,
    ^~~~~~
/home/patrick/rtl8822bu/os_dep/linux/rtw_cfgvendor.c:1431:4: error: ‘const struct wiphy_vendor_command’ has no member named ‘policy’
   .policy = VENDOR_CMD_RAW_DATA,
    ^~~~~~
/home/patrick/rtl8822bu/os_dep/linux/rtw_cfgvendor.c:1440:4: error: ‘const struct wiphy_vendor_command’ has no member named ‘policy’
   .policy = VENDOR_CMD_RAW_DATA,
    ^~~~~~
scripts/Makefile.build:284: recipe for target '/home/patrick/rtl8822bu/os_dep/linux/rtw_cfgvendor.o' failed
make[2]: *** [/home/patrick/rtl8822bu/os_dep/linux/rtw_cfgvendor.o] Error 1
Makefile:1614: recipe for target '_module_/home/patrick/rtl8822bu' failed
make[1]: *** [_module_/home/patrick/rtl8822bu] Error 2
make[1]: Verzeichnis „/usr/src/linux-headers-5.0.0-32-generic“ wird verlassen
Makefile:2001: recipe for target 'modules' failed
make: *** [modules] Error 2
```


Here is the output of my wireless-info.txt

```

########## wireless info START ##########

Report from: 25 Oct 2019 23:45 CEST +0200

Booted last: 25 Oct 2019 00:00 CEST +0200

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 5.0.0-32-generic #34~18.04.2-Ubuntu SMP Thu Oct 10 10:36:02 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

1f:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: ASRock Incorporation Motherboard (one of many) [1849:8168]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 0bda:b812 Realtek Semiconductor Corp. 
Bus 001 Device 006: ID 062a:4101 Creative Labs Wireless Keyboard/Mouse
Bus 001 Device 005: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### secure boot #######################

SecureBoot disabled
Platform is in Setup Mode

##### lsmod #############################

wmi_bmof               16384  0
wmi                    28672  1 wmi_bmof

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
2: enp31s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp31s0' [IF1]> brd <MAC address>
    inet 192.168.0.73/24 brd 192.168.0.255 scope global dynamic noprefixroute enp31s0
       valid_lft 2460sec preferred_lft 2460sec
    inet6 2a02:908:691:e3e0:80e5:bf95:fe72:4650/64 scope global temporary dynamic 
       valid_lft 592409sec preferred_lft 73711sec
    inet6 2a02:908:691:e3e0:8bbd:bca4:f650:cab9/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 1022998sec preferred_lft 418198sec
    inet6 fe80::79d3:50d6:83e:d73/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

enp31s0   no wireless extensions.

lo        no wireless extensions.

##### route #############################

default via 192.168.0.1 dev enp31s0 proto dhcp metric 100 
192.168.0.0/24 dev enp31s0 proto kernel scope link src 192.168.0.73 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0
search home

##### network managers ##################

Installed:

    NetworkManager

Running:

root       958     1  0 20:18 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp31s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (Motherboard (one of many))
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 --
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp31s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:01.3/0000:03:00.2/0000:1d:01.0/0000:1f:00.0/net/enp31s0
GENERAL.IP-IFACE:                       enp31s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Kabelgebundene Verbindung 1
GENERAL.CON-UUID:                       d46b3b96-03fc-37bd-92e0-af79061ef7f2
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.0.73/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.0.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.0.0/24, nh = 0.0.0.0, mt = 100
IP4.DNS[1]:                             192.168.0.1
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_host_name = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        dhcp_lease_time = 3600
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_time_offset = 1
DHCP4.OPTION[8]:                        host_name = patrick-desktop
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       requested_wpad = 1
DHCP4.OPTION[11]:                       domain_name = home
DHCP4.OPTION[12]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 192.168.0.1
DHCP4.OPTION[16]:                       ip_address = 192.168.0.73
DHCP4.OPTION[17]:                       next_server = 192.168.0.1
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[20]:                       requested_static_routes = 1
DHCP4.OPTION[21]:                       expiry = 1572042366
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       requested_routers = 1
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       dhcp_message_type = 5
DHCP4.OPTION[28]:                       network_number = 192.168.0.0
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[30]:                       default_ip_ttl = 64
IP6.ADDRESS[1]:                         2a02:908:691:e3e0:80e5:bf95:fe72:4650/64
IP6.ADDRESS[2]:                         2a02:908:691:e3e0:8bbd:bca4:f650:cab9/64
IP6.ADDRESS[3]:                         fe80::79d3:50d6:83e:d73/64
IP6.GATEWAY:                            fe80::925c:44ff:feac:7f68
IP6.ROUTE[1]:                           dst = 2a02:908:691:e3e0::/64, nh = fe80::925c:44ff:feac:7f68, mt = 100
IP6.ROUTE[2]:                           dst = ::/0, nh = fe80::925c:44ff:feac:7f68, mt = 100
IP6.ROUTE[3]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[4]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[5]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.ROUTE[6]:                           dst = 2a02:908:691:e3e0::/64, nh = ::, mt = 100
IP6.DNS[1]:                             2a02:908:2:a::1
IP6.DNS[2]:                             2a02:908:2:b::1
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2a02:908:2:a::1 2a02:908:2:b::1
DHCP6.OPTION[3]:                        dhcp6_preference = 0
DHCP6.OPTION[4]:                        dhcp6_server_id = 0:1:3:1:25:3a:64:1a:2a:2:9:8:6:0:0:9:54:bc:1e:a:13:ca:ea:cd
DHCP6.OPTION[5]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[6]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[7]:                        dhcp6_client_id = 0:4:8:c2:e4:37:95:bd:bb:ed:77:93:39:e9:92:65:33:35
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   d46b3b96-03fc-37bd-92e0-af79061ef7f2 | Kabelgebundene Verbindung 1

##### NetworkManager.state ##############

cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory

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
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp31s0   no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp31s0   Interface doesn't support scanning.

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

##### udev rules ########################

##### dmesg #############################

########## wireless info END ############


```


Thank you very much in advance!

---

### Post by paddy510 on 2019-10-26
Just in case anyone is interested: I got help to fix it. This is the new driver and it works: 

[https://github.com/cilynx/rtl88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959](https://github.com/cilynx/rtl88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959)

---

