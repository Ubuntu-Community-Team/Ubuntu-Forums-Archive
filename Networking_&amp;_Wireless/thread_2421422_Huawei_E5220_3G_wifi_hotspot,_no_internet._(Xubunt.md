---
title: "Huawei E5220 3G wifi hotspot, no internet. (Xubuntu Xenial)"
date: 2019-06-21
forum: Networking &amp; Wireless
---

### Post by jynxd on 2019-06-21
Hello, I'd like help getting my usb device to access the internet. It's wifi hotspot that connects to 3G+ bands on its own, as far as the computer is concerned it's a router. From what I understand it uses the ethernet protocol through USB, on windows it shows up as a LAN connection, right next to the ethernet connection. It works fine on windows and puppy linux, I'm actually using it right now on puppy, where it uses the wwan0 interface, but when I try to add an ethernet connection on Xubuntu, only the ethernet interface appears (which is eth0 on puppy, and is connected to an old router that no longer gets internet, I use it to transfer files to other devices) nothing interface shows up if I try to add it as a 3G dongle, I've tried a bunch of usb-modeswitch commands I've read online but they don't work for me.

This is what I get from lsusb: 
Bus 001 Device 008: ID 12d1:1506 Huawei Technologies Co., Ltd. Modem/Networkcard

I have a feeling I'm not supplying enough information about the device, but I don't know what else to say or how to get that info.

---

### Post by wildmanne39 on 2019-06-21
*Thread moved to **Networking & Wireless a more appropriate sub-forum**.*

Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created and someone will probably be able to help.

---

### Post by jynxd on 2019-06-21
I see I had started this thread on the wron subforum. Sorry about that.

Here's what wireless-info exported:

```

########## wireless info START ##########

Report from: 21 Jun 2019 14:47 -04 -0400

Booted last: 21 Jun 2019 00:00 -04 -0400

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.5 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.15.0-45-generic #48~16.04.1-Ubuntu SMP Tue Jan 29 18:03:48 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 02)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 004: ID 05e3:0717 Genesys Logic, Inc. All-in-1 Card Reader
Bus 001 Device 003: ID 12d1:1506 Huawei Technologies Co., Ltd. Modem/Networkcard
Bus 001 Device 002: ID 0930:6544 Toshiba Corp. TransMemory-Mini / Kingston DataTraveler 2.0 Stick (2GB)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 005 Device 002: ID 045e:0719 Microsoft Corp. Xbox 360 Wireless Adapter
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### secure boot #######################

'mokutil' is not installed (package "mokutil").

##### lsmod #############################

mxm_wmi                16384  1 nouveau
wmi                    24576  2 mxm_wmi,nouveau

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
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether <MAC 'enp3s0' [IF1]> brd <MAC address>
    inet 192.168.1.120/24 brd 192.168.1.255 scope global dynamic enp3s0
       valid_lft 86199sec preferred_lft 86199sec
    inet6 fe80::48c5:dac4:6683:7c8e/64 scope link 
       valid_lft forever preferred_lft forever
3: wwx<IF from MAC [IF2]>: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether <MAC 'wwx<IF from MAC [IF2]>' [IF2]> brd <MAC address>

##### iwconfig ##########################

enp3s0    no wireless extensions.

wwx<IF from MAC [IF2]>  no wireless extensions.

lo        no wireless extensions.

##### route #############################

default via 192.168.1.1 dev enp3s0  proto static  metric 100 
169.254.0.0/16 dev enp3s0  scope link  metric 1000 
192.168.1.0/24 dev enp3s0  proto kernel  scope link  src 192.168.1.120  metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/resolvconf/resolv.conf']
nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1007     1  0 14:44 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (Motherboard)
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       enp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Ethernet connection 1
GENERAL.CON-UUID:                       e5469421-c66e-4fec-9ef9-055ff22f017d
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   e5469421-c66e-4fec-9ef9-055ff22f017d | Ethernet connection 1
IP4.ADDRESS[1]:                         192.168.1.120/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        host_name = alpha-G31M-S2L
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 192.168.1.1
DHCP4.OPTION[11]:                       expiry = 1561229073
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.1.1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.1.120
DHCP4.OPTION[17]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       requested_routers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       dhcp_lease_time = 86400
DHCP4.OPTION[25]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::48c5:dac4:6683:7c8e/64
IP6.GATEWAY:                            

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
plugins=ifupdown,keyfile,ofono
dns=dnsmasq
[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### Netplan config ####################

##### iw reg get ########################

Region: America/Caracas (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 20), (6, 20), (N/A), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (5250 - 5330 @ 80), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp3s0    no frequency information.

wwx<IF from MAC [IF2]>  no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp3s0    Interface doesn't support scanning.

wwx<IF from MAC [IF2]>  Interface doesn't support scanning.

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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   14.782212] huawei_cdc_ncm 1-2:1.0 wwx<IF from MAC [IF2]>: renamed from wwan0
[   25.555043] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   25.600116] r8169 0000:03:00.0 enp3s0: link down (repeated 2 times)
[   25.600173] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   27.267004] r8169 0000:03:00.0 enp3s0: link up
[   27.267016] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready

########## wireless info END ############


```

---

### Post by jynxd on 2019-06-22
I followed what I found online, I stopped the modem manager, disabled it, enabled it again, and then started it again.

After half a minute it properly detected that there was a broadband device, it even showed the signal level and that it was a movistar service, however, when I created a new mobile broadband connection, I got no internet, even when I deleted the ethernet one.

Upon reboot it went back to not even detecting the mobile broadband.

wireless-info now shows this.

```

########## wireless info START ##########

Report from: 22 Jun 2019 08:46 -04 -0400

Booted last: 22 Jun 2019 00:00 -04 -0400

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.5 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.15.0-45-generic #48~16.04.1-Ubuntu SMP Tue Jan 29 18:03:48 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 02)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 004: ID 05e3:0717 Genesys Logic, Inc. All-in-1 Card Reader
Bus 001 Device 010: ID 12d1:1506 Huawei Technologies Co., Ltd. Modem/Networkcard
Bus 001 Device 002: ID 0930:6544 Toshiba Corp. TransMemory-Mini / Kingston DataTraveler 2.0 Stick (2GB)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 005 Device 002: ID 045e:0719 Microsoft Corp. Xbox 360 Wireless Adapter
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### secure boot #######################

'mokutil' is not installed (package "mokutil").

##### lsmod #############################

mxm_wmi                16384  1 nouveau
wmi                    24576  2 mxm_wmi,nouveau

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
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether <MAC 'enp3s0' [IF1]> brd <MAC address>
4: wwx<IF from MAC [IF2]>: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether <MAC 'wwx<IF from MAC [IF2]>' [IF2]> brd <MAC address>

##### iwconfig ##########################

wwx<IF from MAC [IF2]>  no wireless extensions.

lo        no wireless extensions.

enp3s0    no wireless extensions.

##### route #############################

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/resolvconf/resolv.conf']

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1000     1  0 08:25 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (Motherboard)
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         40 (Carrier/link changed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       
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
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false

##### NetworkManager config #############

[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3

[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq
[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### Netplan config ####################

##### iw reg get ########################

Region: America/Caracas (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 20), (6, 20), (N/A), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (5250 - 5330 @ 80), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

wwx<IF from MAC [IF2]>  no frequency information.

lo        no frequency information.

enp3s0    no frequency information.

##### iwlist scan #######################

wwx<IF from MAC [IF2]>  Interface doesn't support scanning.

lo        Interface doesn't support scanning.

enp3s0    Interface doesn't support scanning.

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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[  355.900063] r8169 0000:03:00.0 enp3s0: link down
[  355.900105] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[  357.567315] r8169 0000:03:00.0 enp3s0: link up
[  357.567326] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[  518.267884] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[  518.320075] r8169 0000:03:00.0 enp3s0: link down (repeated 2 times)
[  518.320151] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[  519.958859] r8169 0000:03:00.0 enp3s0: link up
[  519.958870] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[  726.105933] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[  726.152045] r8169 0000:03:00.0 enp3s0: link down (repeated 2 times)
[  726.152087] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[  727.817820] r8169 0000:03:00.0 enp3s0: link up
[  727.817831] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[  947.666076] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[  947.720304] r8169 0000:03:00.0 enp3s0: link down
[  947.720382] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[  947.721046] r8169 0000:03:00.0 enp3s0: link down
[  949.355460] r8169 0000:03:00.0 enp3s0: link up
[  949.355470] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[  996.831886] huawei_cdc_ncm 1-2:1.0 wwx<IF from MAC [IF2]>: unregister 'huawei_cdc_ncm' usb-0000:00:1d.7-2, Huawei CDC NCM device
[ 1011.553871] huawei_cdc_ncm 1-2:1.0 wwx<IF from MAC [IF2]>: renamed from wwan0

########## wireless info END ############
```

I really need to use internet on this OS, I'd greatly appreciate some help.

---

### Post by eby on 2019-10-23
First disable "Enable Mobile Broadband" from NM applet on your task bar.

Then list the modem,

```
~ $ mmcli -L

Found 1 modems:
	/org/freedesktop/ModemManager1/Modem/0 [huawei] E5220

~ $ mmcli --modem 0
```

If the modem is listed under "/Modem/2 [huawei] E5220", then above code would be "mmcli --modem 2" to list the parameters.

look for the output, if you see the following,

```
ports: 'ttyUSB1 (at), wwan0 (net)'
```

Then the following should list modem under wwan0 or corresponding number.

```
~ $ ifconfig -a 
```

```

~ $ sudo dhclient -v wwan0
```

Problem with this method is there is no connection indication.

---

