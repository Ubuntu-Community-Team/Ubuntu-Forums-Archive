---
title: "Ubuntu Wireless adapter not found"
date: 2020-02-29
forum: Networking &amp; Wireless
---

### Post by khalifa97 on 2020-02-29
As the title says,
this is my wireless-info.txt


```
########## wireless info START ##########


Report from: 01 Mar 2020 04:39 EET +0200


Booted last: 01 Mar 2020 00:00 EET +0200


Script from: 22 Oct 2018 03:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.2 LTS
Release:    18.04
Codename:    bionic


##### kernel ############################


Linux 5.3.0-40-generic #32~18.04.1-Ubuntu SMP Mon Feb 3 14:05:59 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, acpi_osi=!, "acpi_osi=Windows, 2009", vt.handoff=1


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:3899]
    Kernel driver in use: r8169


03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter [10ec:c821]
    Subsystem: Lenovo RTL8821CE 802.11ac PCIe Wireless Network Adapter [17aa:c024]


04:00.0 Non-Volatile memory controller [0108]: Toshiba America Info Systems Device [1179:0113] (rev 01)


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 5986:210e Acer, Inc 
Bus 001 Device 004: ID 0bda:c024 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 06cb:0081 Synaptics, Inc. 
Bus 001 Device 002: ID 0000:3825  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### secure boot #######################


SecureBoot disabled


##### lsmod #############################


intel_wmi_thunderbolt    20480  0
wmi_bmof               16384  0
wmi                    32768  2 intel_wmi_thunderbolt,wmi_bmof


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
2: enp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'enp2s0' [IF1]> brd <MAC address>
3: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether <MAC 'docker0' [IF2]> brd <MAC address>
    inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
       valid_lft forever preferred_lft forever
4: bnep0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 1000
    link/ether <MAC 'bnep0' [IF3]> brd <MAC address>
    inet 192.168.44.223/24 brd 192.168.44.255 scope global dynamic noprefixroute bnep0
       valid_lft 3076sec preferred_lft 3076sec
    inet6 fe80::e3c9:f9f0:d064:87e1/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever


##### iwconfig ##########################


lo        no wireless extensions.


bnep0     no wireless extensions.


enp2s0    no wireless extensions.


docker0   no wireless extensions.


##### route #############################


default via 192.168.44.1 dev bnep0 proto dhcp metric 750 
169.254.0.0/16 dev docker0 scope link metric 1000 linkdown 
172.17.0.0/16 dev docker0 proto kernel scope link src 172.17.0.1 linkdown 
192.168.44.0/24 dev bnep0 proto kernel scope link src 192.168.44.223 metric 750 


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']


nameserver 127.0.0.53
options edns0


##### network managers ##################


Installed:


    NetworkManager


Running:


root      1318     1  0 04:24 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


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
GENERAL.UDI:                            /org/bluez/hci0/dev_D4_11_A3_9B_1A_F4
GENERAL.IP-IFACE:                       bnep0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Galaxy A30 Network
GENERAL.CON-UUID:                       79558b87-6504-4c1b-9aa6-dd5ee67f5a52
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
IP4.ADDRESS[1]:                         192.168.44.223/24
IP4.GATEWAY:                            192.168.44.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.44.1, mt = 750
IP4.ROUTE[2]:                           dst = 192.168.44.0/24, nh = 0.0.0.0, mt = 750
IP4.DNS[1]:                             192.168.44.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.44.1
DHCP4.OPTION[5]:                        ip_address = 192.168.44.223
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.44.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.44.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.44.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1583040618
DHCP4.OPTION[20]:                       host_name = ahmed-Lenovo-ideapad-520-15IKB
DHCP4.OPTION[21]:                       requested_netbios_scope = 1
DHCP4.OPTION[22]:                       requested_wpad = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.44.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       next_server = 192.168.44.1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 3600
IP6.ADDRESS[1]:                         fe80::e3c9:f9f0:d064:87e1/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 750
BLUETOOTH.CAPABILITIES:                 NAP
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{15}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   79558b87-6504-4c1b-9aa6-dd5ee67f5a52 | Galaxy A30 Network


GENERAL.DEVICE:                         docker0
GENERAL.TYPE:                           bridge
GENERAL.NM-TYPE:                        NMDeviceBridge
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         bridge
GENERAL.DRIVER-VERSION:                 2.3
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'docker0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/docker0
GENERAL.IP-IFACE:                       docker0
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     docker0
GENERAL.CON-UUID:                       33d5265a-6de1-4df7-bb4c-64e50e5341f6
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
CAPABILITIES.SRIOV:                     no
IP4.ADDRESS[1]:                         172.17.0.1/16
IP4.GATEWAY:                            --
IP4.ROUTE[1]:                           dst = 172.17.0.0/16, nh = 0.0.0.0, mt = 0
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP6.GATEWAY:                            --
BRIDGE.SLAVES:                          --
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{16}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   33d5265a-6de1-4df7-bb4c-64e50e5341f6 | docker0


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
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.4/0000:02:00.0/net/enp2s0
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


[[/etc/NetworkManager/system-connections/Creativo Space Dokki]] (600 root)
[connection] id=Creativo Space Dokki | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Creativo Space Dokki
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Wireless-Guest]] (600 root)
[connection] id=Wireless-Guest | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Wireless-Guest
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/CMP-(2)]] (600 root)
[connection] id=CMP-(2) | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=CMP-(2)
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Kareem's Awesome World]] (600 root)
[connection] id=Kareem's Awesome World | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Kareem's Awesome World
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Helmy’s iPhone]] (600 root)
[connection] id=Helmy’s iPhone | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=72;101;108;109;121;226;128;153;115;32;105;80;104;111;110;101;
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Vodafone WiFi]] (600 root)
[connection] id=Vodafone WiFi | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Vodafone WiFi
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ARC8]] (600 root)
[connection] id=ARC8 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=ARC8
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/NETGEAR]] (600 root)
[connection] id=NETGEAR | type=wifi | permissions=
[wifi] bssid=<MAC address> | mac-address=<MAC address> | mac-address-blacklist= | ssid=NETGEAR
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/WE_9D5F83]] (600 root)
[connection] id=WE_9D5F83 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=WE_9D5F83
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/te WiFi]] (600 root)
[connection] id=te WiFi | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=te WiFi
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Ahmed]] (600 root)
[connection] id=Ahmed | type=wifi | autoconnect=false | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=ahmed-Lenovo-ideapad-520-15IKB
[ipv4] method=shared
[ipv6] method=shared


[[/etc/NetworkManager/system-connections/laz]] (600 root)
[connection] id=laz | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=laz
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/AndroidAP1AF5]] (600 root)
[connection] id=AndroidAP1AF5 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=AndroidAP1AF5
[ipv4] method=auto
[ipv6] method=auto


##### Netplan config ####################


[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager


##### iw reg get ########################


Region: Africa/Cairo (based on set time zone)


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


lo        no frequency information.


bnep0     no frequency information.


enp2s0    no frequency information.


docker0   no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


bnep0     Interface doesn't support scanning.


enp2s0    Interface doesn't support scanning.


docker0   Interface doesn't support scanning.


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


[/etc/modprobe.d/blacklist-ideapad.conf]
blacklist ideapad_laptop


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


[   11.865642] Bluetooth: hci0: RTL: rtl: examining hci_ver=08 hci_rev=000c lmp_ver=08 lmp_subver=8821
[   11.866634] Bluetooth: hci0: RTL: rtl: loading rtl_bt/rtl8821c_fw.bin
[   12.825301] Bluetooth: hci0: RTL: rtl: loading rtl_bt/rtl8821c_config.bin
[   13.172330] [drm] Finished loading DMC firmware i915/kbl_dmc_ver1_04.bin (v1.4)
[   30.100651] r8169 0000:02:00.0 enp2s0: Link is Down


########## wireless info END ############

```

Thanks in advance

---

### Post by chili555 on 2020-03-01
With a working internet connection, open a terminal and do:

```
sudo apt update
sudo apt install rtl8821ce-dkms

```
Reboot.

---

