---
title: "[Solved] No Wi-fi adapter found"
date: 2019-04-03
forum: Networking &amp; Wireless
---

### Post by dxc536 on 2019-04-03
I have somehow removed my ability to use wifi on ubuntu and I can't tell you what I did. I've been to multiple forums looking for a fix and a common error that pops up when I type: 
lspci -vnn | grep Network
is 


libkmod: ERROR ../libkmod/libkmod-config.c:656 kmod_config_parse: /etc/modprobe.d/iwlwifi.conf line 8: ignoring bad line starting with '“options'


Anyone have any suggestions?

---

### Post by jeremy31 on 2019-04-03
See the wireless script in my signature and post results as there might be more issues than what is on line 8 of /etc/modprobe.d/iwlwifi.conf

---

### Post by dxc536 on 2019-04-03
[h=1]Ubuntu Pastebin[/h][h=1]Paste from cunningham at Wed, 3 Apr 2019 21:27:27 +0000[/h][Download as text]("http://paste.ubuntu.com/p/v7nTvBDP4Y/plain/")```
########## wireless info START ##########

Report from: 03 Apr 2019 17:27 EDT -0400

Booted last: 03 Apr 2019 00:00 EDT -0400

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.2 LTS
Release:	18.04
Codename:	bionic

##### kernel ############################

Linux 4.15.0-47-generic #50-Ubuntu SMP Wed Mar 13 10:44:52 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

libkmod: ERROR ../libkmod/libkmod-config.c:656 kmod_config_parse: /etc/modprobe.d/iwlwifi.conf line 8: ignoring bad line starting with '&#8220;options'

00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (5) I219-LM [8086:15e3] (rev 31)
	Subsystem: Dell Ethernet Connection (5) I219-LM [1028:07a9]
	Kernel driver in use: e1000e

02:00.0 Network controller [0280]: Intel Corporation Wireless 8265 / 8275 [8086:24fd] (rev 78)
	Subsystem: Intel Corporation Wireless 8265 / 8275 [8086:0050]
	Kernel modules: iwlwifi

##### lsusb #############################

Bus 002 Device 002: ID 125f:312b A-DATA Technology Co., Ltd. Superior S102 Pro
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:568c Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no

##### secure boot #######################

SecureBoot enabled

##### lsmod #############################

wmi_bmof               16384  0
dell_wmi               16384  0
intel_wmi_thunderbolt    16384  0
mxm_wmi                16384  0
dell_laptop            20480  1
dell_smbios            24576  2 dell_wmi,dell_laptop
dell_wmi_descriptor    16384  2 dell_wmi,dell_smbios
sparse_keymap          16384  2 intel_hid,dell_wmi
video                  45056  3 dell_wmi,dell_laptop,i915
wmi                    24576  6 intel_wmi_thunderbolt,dell_wmi,wmi_bmof,dell_smbios,dell_wmi_descriptor,mxm_wmi

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
2: enp0s31f6: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp0s31f6' [IF1]> brd <MAC address>
    inet 192.168.1.128/24 brd 192.168.1.255 scope global dynamic noprefixroute enp0s31f6
       valid_lft 86257sec preferred_lft 86257sec
    inet6 2605:a000:1231:586:1915:96c4:d66d:10c/64 scope global temporary dynamic 
       valid_lft 541522sec preferred_lft 85891sec
    inet6 2605:a000:1231:586:d462:8dda:f89a:88b7/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 541522sec preferred_lft 541522sec
    inet6 fe80::611:e818:c90d:2c35/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

enp0s31f6  no wireless extensions.

##### route #############################

default via 192.168.1.1 dev enp0s31f6 proto dhcp metric 100 
169.254.0.0/16 dev enp0s31f6 scope link metric 1000 
192.168.1.0/24 dev enp0s31f6 proto kernel scope link src 192.168.1.128 metric 100 

##### resolv.conf #######################

[644 root '/etc/resolv.conf']
search neo.rr.com
nameserver 127.0.0.53

##### network managers ##################

Installed:

	NetworkManager

Running:

root      1011     1  0 17:24 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s31f6
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (5) I219-LM
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.1-4
GENERAL.HWADDR:                         <MAC 'enp0s31f6' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1f.6/net/enp0s31f6
GENERAL.IP-IFACE:                       enp0s31f6
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       25f50a6b-7a8f-3e3c-85fc-58ffdb607c35
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.1.128/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.1.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          neo.rr.com
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        server_name = ecosystem.home.cisco.com
DHCP4.OPTION[5]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[6]:                        ip_address = 192.168.1.128
DHCP4.OPTION[7]:                        requested_static_routes = 1
DHCP4.OPTION[8]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[16]:                       routers = 192.168.1.1
DHCP4.OPTION[17]:                       requested_broadcast_address = 1
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       domain_name = neo.rr.com
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1554413092
DHCP4.OPTION[22]:                       host_name = cunningham-Precision-3520
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_wpad = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       requested_domain_search = 1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       next_server = 192.168.1.1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
DHCP4.OPTION[32]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         2605:a000:1231:586:1915:96c4:d66d:10c/64
IP6.ADDRESS[2]:                         2605:a000:1231:586:d462:8dda:f89a:88b7/64
IP6.ADDRESS[3]:                         fe80::611:e818:c90d:2c35/64
IP6.GATEWAY:                            fe80::5aef:68ff:feff:a9a0
IP6.ROUTE[1]:                           dst = 2605:a000:1231:586::/64, nh = fe80::5aef:68ff:feff:a9a0, mt = 100
IP6.ROUTE[2]:                           dst = ::/0, nh = fe80::5aef:68ff:feff:a9a0, mt = 100
IP6.ROUTE[3]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[4]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[5]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.ROUTE[6]:                           dst = 2605:a000:1231:586::/64, nh = ::, mt = 100
IP6.DNS[1]:                             2605:a000:1231:586:5aef:68ff:feff:a9a0
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2605:a000:1231:586:5aef:68ff:feff:a9a0
DHCP6.OPTION[3]:                        dhcp6_domain_search = neo.rr.com.
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        dhcp6_server_id = 0:2:3:9:5:5:<MAC address>
DHCP6.OPTION[7]:                        dhcp6_client_id = 0:4:f7:d4:bf:c6:f:47:8a:13:db:31:14:a7:e5:e4:8:19
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{9}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   25f50a6b-7a8f-3e3c-85fc-58ffdb607c35 | Wired connection 1

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

[[/etc/NetworkManager/system-connections/belkin.b0c]] (600 root)
[connection] id=belkin.b0c | type=wifi | permissions=user:cunningham:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=belkin.b0c
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Dial-up]] (600 root)
[connection] id=Dial-up | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Dial-up
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Dial-up Delux]] (600 root)
[connection] id=Dial-up Delux | type=wifi | permissions=user:cunningham:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Dial-up Delux
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/MHGUEST]] (600 root)
[connection] id=MHGUEST | type=wifi | permissions=user:ubuntu:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=MHGUEST
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CC-Public]] (600 root)
[connection] id=CC-Public | type=wifi | permissions=user:cunningham:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=CC-Public
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/vaptwins]] (600 root)
[connection] id=vaptwins | type=wifi | permissions=user:cunningham:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=vaptwins
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/MHGUEST 1]] (600 root)
[connection] id=MHGUEST 1 | type=wifi | permissions=user:cunningham:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=MHGUEST
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Dial-up Delux-guest]] (600 root)
[connection] id=Dial-up Delux-guest | type=wifi | permissions=user:cunningham:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Dial-up Delux-guest
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

##### iw reg get ########################

nl80211 not found.

##### iwlist channels ###################

lo        no frequency information.

enp0s31f6  no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp0s31f6  Interface doesn't support scanning.

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
&#8220;options iwlwifi disable_msix=1&#8221;

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

########## wireless info END ############

```

---

### Post by jeremy31 on 2019-04-03
In terminal do ```
gedit admin:///etc/modprobe.d/iwlwifi.conf
```
Delete the last line ```
&#8220;options iwlwifi disable_msix=1&#8221;
```

Reboot and if it doesn't work do ```
./wireless-info && cat wireless-info.txt | nc termbin.com 9999
```
Post URL

---

### Post by dxc536 on 2019-04-03
[http://paste.ubuntu.com/p/88qdc84NsM/](http://paste.ubuntu.com/p/88qdc84NsM/)


[https://termbin.com/jof4](https://termbin.com/jof4)

---

### Post by jeremy31 on 2019-04-03
What result fro ```
dkms status; modinfo iwlwifi
```

---

### Post by dxc536 on 2019-04-03
[https://paste.ubuntu.com/p/DpYkDy9wcw/](https://paste.ubuntu.com/p/DpYkDy9wcw/)

---

### Post by jeremy31 on 2019-04-03
Try disabling Secure Boot in BIOS or uninstall iwlwifi backports

---

### Post by dxc536 on 2019-04-03
Uninstalling the backports worked! Thank you so much for your time!

---

