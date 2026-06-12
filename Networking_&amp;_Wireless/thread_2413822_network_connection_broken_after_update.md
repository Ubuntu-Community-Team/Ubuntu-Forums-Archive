---
title: "network connection broken after update"
date: 2019-03-02
forum: Networking &amp; Wireless
---

### Post by carlmather2001 on 2019-03-02
After update on 1 march my internet access is broken. Network Manager shows connection is working. I can access from my laptop and phone but desktop computer (which was only machine updated) cannot access at all. Have rebooted/restarted at least a dozen times. Swapped cables around. Restarted router 5 times. Nothing changes.
[ATTACH=CONFIG]282663[/ATTACH][ATTACH=CONFIG]282664[/ATTACH]
Top left of screen shows network not connecting - network symbol with question mark - even though network manager shows connected.
Can't access with Firefox, Thunderbird, Terminal, etc.
Don't know how to fix this.

---

### Post by wildmanne39 on 2019-03-02
*Thread moved to **Networking & Wireless a more appropriate sub-forum**.*

Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created and someone will probably be able to help you.

---

### Post by carlmather2001 on 2019-03-02
```
########## wireless info START ##########

Report from: 03 Mar 2019 08:22 NZDT +1300

Booted last: 03 Mar 2019 00:00 NZDT +1300

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.10
Release:    18.10
Codename:    cosmic

##### kernel ############################

Linux 4.18.0-15-generic #16-Ubuntu SMP Thu Feb 7 10:56:39 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, noprompt, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Gigabyte Technology Co., Ltd Onboard Ethernet [1458:e000]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 012: ID 0781:556b SanDisk Corp. 
Bus 003 Device 007: ID 13fd:3940 Initio Corporation 
Bus 003 Device 006: ID 11b0:6348 ATECH FLASH TECHNOLOGY 
Bus 003 Device 004: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 003 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 003 Device 005: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 003 Device 003: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### secure boot #######################

'mokutil' is not installed (package "mokutil").

##### lsmod #############################

snd_soc_rt5640        126976  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          229376  1 snd_soc_rt5640
snd_pcm                98304  7 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_soc_rt5640,snd_soc_core,snd_hda_core,snd_pcm_dmaengine

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
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'eth0' [IF1]> brd <MAC address>
    inet 192.168.1.3/24 brd 192.168.1.255 scope global dynamic noprefixroute eth0
       valid_lft 78923sec preferred_lft 78923sec
    inet6 fd9c:b2b2:986:b00:54d4:30d5:b9bf:a21e/64 scope global temporary dynamic 
       valid_lft 7146sec preferred_lft 3546sec
    inet6 fd9c:b2b2:986:b00:d588:1966:93f1:c051/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 7146sec preferred_lft 3546sec
    inet6 fe80::24a2:c9f7:1fc6:89af/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

default via 192.168.1.1 dev eth0 proto dhcp metric 20100 
169.254.0.0/16 dev eth0 scope link metric 1000 
192.168.1.0/24 dev eth0 proto kernel scope link src 192.168.1.3 metric 100 

##### resolv.conf #######################

[644 root '/etc/resolv.conf']
nameserver 8.8.8.8
nameserver 8.8.4.4

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1037     1  0 06:17 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (Onboard Ethernet)
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'eth0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       7a190f5d-7eb2-39ca-bdee-8bcf44fdfbd5
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.1.3/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.1.1, mt = 20100
IP4.ROUTE[2]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             198.18.0.1
IP4.DNS[2]:                             198.18.0.2
DHCP4.OPTION[1]:                        broadcast_address = 192.168.1.255
DHCP4.OPTION[2]:                        dhcp_lease_time = 86400
DHCP4.OPTION[3]:                        dhcp_message_type = 5
DHCP4.OPTION[4]:                        dhcp_rebinding_time = 75600
DHCP4.OPTION[5]:                        dhcp_renewal_time = 43200
DHCP4.OPTION[6]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[7]:                        domain_name = home
DHCP4.OPTION[8]:                        domain_name_servers = 192.168.1.1 192.168.1.1
DHCP4.OPTION[9]:                        expiry = 1551633443
DHCP4.OPTION[10]:                       ip_address = 192.168.1.3
DHCP4.OPTION[11]:                       network_number = 192.168.1.0
DHCP4.OPTION[12]:                       next_server = 0.0.0.0
DHCP4.OPTION[13]:                       requested_broadcast_address = 1
DHCP4.OPTION[14]:                       requested_domain_name = 1
DHCP4.OPTION[15]:                       requested_domain_name_servers = 1
DHCP4.OPTION[16]:                       requested_domain_search = 1
DHCP4.OPTION[17]:                       requested_host_name = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[20]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_scope = 1
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       requested_static_routes = 1
DHCP4.OPTION[26]:                       requested_subnet_mask = 1
DHCP4.OPTION[27]:                       requested_time_offset = 1
DHCP4.OPTION[28]:                       requested_wpad = 1
DHCP4.OPTION[29]:                       routers = 192.168.1.1
DHCP4.OPTION[30]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         fd9c:b2b2:986:b00:54d4:30d5:b9bf:a21e/64
IP6.ADDRESS[2]:                         fd9c:b2b2:986:b00:d588:1966:93f1:c051/64
IP6.ADDRESS[3]:                         fe80::24a2:c9f7:1fc6:89af/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.ROUTE[2]:                           dst = fd9c:b2b2:986:b00::/64, nh = ::, mt = 100
IP6.ROUTE[3]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.DNS[1]:                             fe80::1
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:11:96:d9:34:8:44:5c:38:6:f2:ee:b7:89:b0:98:1a
DHCP6.OPTION[2]:                        dhcp6_name_servers = fe80::1
DHCP6.OPTION[3]:                        dhcp6_server_id = 0:1:0:1:12:cf:f7:bd:9c:b2:b2:9:86:b
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[6]:                        requested_dhcp6_name_servers = 1
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   7a190f5d-7eb2-39ca-bdee-8bcf44fdfbd5 | Wired connection 1

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
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve

##### NetworkManager profiles ###########

##### Netplan config ####################

##### iw reg get ########################

Region: Pacific/Auckland (based on set time zone)

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

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

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

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

########## wireless info END ############
```

---

### Post by wildmanne39 on 2019-03-02
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by carlmather2001 on 2019-03-02
```

########## wireless info START ##########

Report from: 03 Mar 2019 08:22 NZDT +1300

Booted last: 03 Mar 2019 00:00 NZDT +1300

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.10
Release:    18.10
Codename:    cosmic

##### kernel ############################

Linux 4.18.0-15-generic #16-Ubuntu SMP Thu Feb 7 10:56:39 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, noprompt, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Gigabyte Technology Co., Ltd Onboard Ethernet [1458:e000]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 012: ID 0781:556b SanDisk Corp. 
Bus 003 Device 007: ID 13fd:3940 Initio Corporation 
Bus 003 Device 006: ID 11b0:6348 ATECH FLASH TECHNOLOGY 
Bus 003 Device 004: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 003 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 003 Device 005: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 003 Device 003: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### secure boot #######################

'mokutil' is not installed (package "mokutil").

##### lsmod #############################

snd_soc_rt5640        126976  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          229376  1 snd_soc_rt5640
snd_pcm                98304  7 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_soc_rt5640,snd_soc_core,snd_hda_core,snd_pcm_dmaengine

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
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'eth0' [IF1]> brd <MAC address>
    inet 192.168.1.3/24 brd 192.168.1.255 scope global dynamic noprefixroute eth0
       valid_lft 78923sec preferred_lft 78923sec
    inet6 fd9c:b2b2:986:b00:54d4:30d5:b9bf:a21e/64 scope global temporary dynamic 
       valid_lft 7146sec preferred_lft 3546sec
    inet6 fd9c:b2b2:986:b00:d588:1966:93f1:c051/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 7146sec preferred_lft 3546sec
    inet6 fe80::24a2:c9f7:1fc6:89af/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

default via 192.168.1.1 dev eth0 proto dhcp metric 20100 
169.254.0.0/16 dev eth0 scope link metric 1000 
192.168.1.0/24 dev eth0 proto kernel scope link src 192.168.1.3 metric 100 

##### resolv.conf #######################

[644 root '/etc/resolv.conf']
nameserver 8.8.8.8
nameserver 8.8.4.4

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1037     1  0 06:17 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (Onboard Ethernet)
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'eth0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       7a190f5d-7eb2-39ca-bdee-8bcf44fdfbd5
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.1.3/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.1.1, mt = 20100
IP4.ROUTE[2]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             198.18.0.1
IP4.DNS[2]:                             198.18.0.2
DHCP4.OPTION[1]:                        broadcast_address = 192.168.1.255
DHCP4.OPTION[2]:                        dhcp_lease_time = 86400
DHCP4.OPTION[3]:                        dhcp_message_type = 5
DHCP4.OPTION[4]:                        dhcp_rebinding_time = 75600
DHCP4.OPTION[5]:                        dhcp_renewal_time = 43200
DHCP4.OPTION[6]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[7]:                        domain_name = home
DHCP4.OPTION[8]:                        domain_name_servers = 192.168.1.1 192.168.1.1
DHCP4.OPTION[9]:                        expiry = 1551633443
DHCP4.OPTION[10]:                       ip_address = 192.168.1.3
DHCP4.OPTION[11]:                       network_number = 192.168.1.0
DHCP4.OPTION[12]:                       next_server = 0.0.0.0
DHCP4.OPTION[13]:                       requested_broadcast_address = 1
DHCP4.OPTION[14]:                       requested_domain_name = 1
DHCP4.OPTION[15]:                       requested_domain_name_servers = 1
DHCP4.OPTION[16]:                       requested_domain_search = 1
DHCP4.OPTION[17]:                       requested_host_name = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[20]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_scope = 1
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       requested_static_routes = 1
DHCP4.OPTION[26]:                       requested_subnet_mask = 1
DHCP4.OPTION[27]:                       requested_time_offset = 1
DHCP4.OPTION[28]:                       requested_wpad = 1
DHCP4.OPTION[29]:                       routers = 192.168.1.1
DHCP4.OPTION[30]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         fd9c:b2b2:986:b00:54d4:30d5:b9bf:a21e/64
IP6.ADDRESS[2]:                         fd9c:b2b2:986:b00:d588:1966:93f1:c051/64
IP6.ADDRESS[3]:                         fe80::24a2:c9f7:1fc6:89af/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.ROUTE[2]:                           dst = fd9c:b2b2:986:b00::/64, nh = ::, mt = 100
IP6.ROUTE[3]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.DNS[1]:                             fe80::1
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:11:96:d9:34:8:44:5c:38:6:f2:ee:b7:89:b0:98:1a
DHCP6.OPTION[2]:                        dhcp6_name_servers = fe80::1
DHCP6.OPTION[3]:                        dhcp6_server_id = 0:1:0:1:12:cf:f7:bd:9c:b2:b2:9:86:b
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[6]:                        requested_dhcp6_name_servers = 1
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   7a190f5d-7eb2-39ca-bdee-8bcf44fdfbd5 | Wired connection 1

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
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve

##### NetworkManager profiles ###########

##### Netplan config ####################

##### iw reg get ########################

Region: Pacific/Auckland (based on set time zone)

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

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

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

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

########## wireless info END ############

```

---

### Post by jeremy31 on 2019-03-02
I imagine ```
ping -c3 8.8.8.8
```
works but trying to ping google.com fails
Post URL from terminal for ```
systemd-resolve --status | nc termbin.com 9999
```

---

### Post by carlmather2001 on 2019-03-02
```
   	 	 	 	   knot@working:~$ ping -c3 8.8.8.8
 PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
 64 bytes from 8.8.8.8: icmp_seq=1 ttl=53 time=51.1 ms
 64 bytes from 8.8.8.8: icmp_seq=2 ttl=53 time=50.0 ms
 64 bytes from 8.8.8.8: icmp_seq=3 ttl=53 time=50.7 ms
 
 
 --- 8.8.8.8 ping statistics ---
 3 packets transmitted, 3 received, 0% packet loss, time 4ms
 rtt min/avg/max/mdev = 50.005/50.583/51.080/0.479 ms
 knot@working:~$ systemd-resolve --status | nc termbin.com 9999
 nc: getaddrinfo for host "termbin.com" port 9999: Name or service not known
 knot@working:~$  
```

---

### Post by jeremy31 on 2019-03-02
Try ```
systemd-resolve --status > systemd-resolve.txt
```
Post the contents of systemd-resolve.txt

---

### Post by carlmather2001 on 2019-03-02
```

########## wireless info START ##########

Report from: 03 Mar 2019 08:22 NZDT +1300

Booted last: 03 Mar 2019 00:00 NZDT +1300

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.10
Release:    18.10
Codename:    cosmic

##### kernel ############################

Linux 4.18.0-15-generic #16-Ubuntu SMP Thu Feb 7 10:56:39 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, noprompt, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Gigabyte Technology Co., Ltd Onboard Ethernet [1458:e000]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 012: ID 0781:556b SanDisk Corp. 
Bus 003 Device 007: ID 13fd:3940 Initio Corporation 
Bus 003 Device 006: ID 11b0:6348 ATECH FLASH TECHNOLOGY 
Bus 003 Device 004: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 003 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 003 Device 005: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 003 Device 003: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### secure boot #######################

'mokutil' is not installed (package "mokutil").

##### lsmod #############################

snd_soc_rt5640        126976  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          229376  1 snd_soc_rt5640
snd_pcm                98304  7 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_soc_rt5640,snd_soc_core,snd_hda_core,snd_pcm_dmaengine

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
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'eth0' [IF1]> brd <MAC address>
    inet 192.168.1.3/24 brd 192.168.1.255 scope global dynamic noprefixroute eth0
       valid_lft 78923sec preferred_lft 78923sec
    inet6 fd9c:b2b2:986:b00:54d4:30d5:b9bf:a21e/64 scope global temporary dynamic 
       valid_lft 7146sec preferred_lft 3546sec
    inet6 fd9c:b2b2:986:b00:d588:1966:93f1:c051/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 7146sec preferred_lft 3546sec
    inet6 fe80::24a2:c9f7:1fc6:89af/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

default via 192.168.1.1 dev eth0 proto dhcp metric 20100 
169.254.0.0/16 dev eth0 scope link metric 1000 
192.168.1.0/24 dev eth0 proto kernel scope link src 192.168.1.3 metric 100 

##### resolv.conf #######################

[644 root '/etc/resolv.conf']
nameserver 8.8.8.8
nameserver 8.8.4.4

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1037     1  0 06:17 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (Onboard Ethernet)
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'eth0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       7a190f5d-7eb2-39ca-bdee-8bcf44fdfbd5
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.1.3/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.1.1, mt = 20100
IP4.ROUTE[2]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             198.18.0.1
IP4.DNS[2]:                             198.18.0.2
DHCP4.OPTION[1]:                        broadcast_address = 192.168.1.255
DHCP4.OPTION[2]:                        dhcp_lease_time = 86400
DHCP4.OPTION[3]:                        dhcp_message_type = 5
DHCP4.OPTION[4]:                        dhcp_rebinding_time = 75600
DHCP4.OPTION[5]:                        dhcp_renewal_time = 43200
DHCP4.OPTION[6]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[7]:                        domain_name = home
DHCP4.OPTION[8]:                        domain_name_servers = 192.168.1.1 192.168.1.1
DHCP4.OPTION[9]:                        expiry = 1551633443
DHCP4.OPTION[10]:                       ip_address = 192.168.1.3
DHCP4.OPTION[11]:                       network_number = 192.168.1.0
DHCP4.OPTION[12]:                       next_server = 0.0.0.0
DHCP4.OPTION[13]:                       requested_broadcast_address = 1
DHCP4.OPTION[14]:                       requested_domain_name = 1
DHCP4.OPTION[15]:                       requested_domain_name_servers = 1
DHCP4.OPTION[16]:                       requested_domain_search = 1
DHCP4.OPTION[17]:                       requested_host_name = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[20]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_scope = 1
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       requested_static_routes = 1
DHCP4.OPTION[26]:                       requested_subnet_mask = 1
DHCP4.OPTION[27]:                       requested_time_offset = 1
DHCP4.OPTION[28]:                       requested_wpad = 1
DHCP4.OPTION[29]:                       routers = 192.168.1.1
DHCP4.OPTION[30]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         fd9c:b2b2:986:b00:54d4:30d5:b9bf:a21e/64
IP6.ADDRESS[2]:                         fd9c:b2b2:986:b00:d588:1966:93f1:c051/64
IP6.ADDRESS[3]:                         fe80::24a2:c9f7:1fc6:89af/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.ROUTE[2]:                           dst = fd9c:b2b2:986:b00::/64, nh = ::, mt = 100
IP6.ROUTE[3]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.DNS[1]:                             fe80::1
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:11:96:d9:34:8:44:5c:38:6:f2:ee:b7:89:b0:98:1a
DHCP6.OPTION[2]:                        dhcp6_name_servers = fe80::1
DHCP6.OPTION[3]:                        dhcp6_server_id = 0:1:0:1:12:cf:f7:bd:9c:b2:b2:9:86:b
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[6]:                        requested_dhcp6_name_servers = 1
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   7a190f5d-7eb2-39ca-bdee-8bcf44fdfbd5 | Wired connection 1

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
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve

##### NetworkManager profiles ###########

##### Netplan config ####################

##### iw reg get ########################

Region: Pacific/Auckland (based on set time zone)

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

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

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

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

########## wireless info END ############

```

---

### Post by carlmather2001 on 2019-03-04
reinstalled system. problem solved.

---

