---
title: "No Wifi Adapter after update to 22.04 LTS yesterday"
date: 2023-08-09
forum: Networking &amp; Wireless
---

### Post by clarosoft on 2023-08-09
After an update yesterday, I have no Wifi adapter at all and no network access to do anything about it. Diagnostics here:

Can anyone help?

```



########## wireless info START ##########


Report from: 09 Aug 2023 10:06 BST +0100


Booted last: 09 Aug 2023 00:00 BST +0100


Script from: 25 Jan 2020 03:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.2 LTS
Release:    22.04
Codename:    jammy


##### kernel ############################


Linux 5.15.0-78-generic #85-Ubuntu SMP Fri Jul 7 15:25:09 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, cgroup_enable=memory, swapaccount=1, quiet, splash, gfxpayload=true


##### desktop ###########################


Ubuntu


##### lspci #############################


00:03.0 Ethernet controller [0200]: Intel Corporation 82540EM Gigabit Ethernet Controller [8086:100e] (rev 02)
    Subsystem: Intel Corporation PRO/1000 MT Desktop Adapter [8086:001e]
    Kernel driver in use: e1000


##### lsusb #############################


Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### secure boot #######################


'mokutil' is not installed (package "mokutil").


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
2: enp0s3: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'enp0s3' [IF1]> brd <MAC address>
3: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether <MAC 'docker0' [IF2]> brd <MAC address>
    inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
       valid_lft forever preferred_lft forever


##### iwconfig ##########################


lo        no wireless extensions.


enp0s3    no wireless extensions.


docker0   no wireless extensions.


##### route #############################


172.17.0.0/16 dev docker0 proto kernel scope link src 172.17.0.1 linkdown 


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '/run/systemd/resolve/resolv.conf']


nameserver 168.63.129.16
search .


##### network managers ##################


Installed:


    NetworkManager


Running:


root         638       1  0 09:55 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         docker0
GENERAL.TYPE:                           bridge
GENERAL.NM-TYPE:                        NMDeviceBridge
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/3
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         bridge
GENERAL.DRIVER-VERSION:                 2.3
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'docker0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               0 (unknown)
GENERAL.IP6-CONNECTIVITY:               0 (unknown)
GENERAL.UDI:                            /sys/devices/virtual/net/docker0
GENERAL.PATH:                           --
GENERAL.IP-IFACE:                       docker0
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     no
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
CAPABILITIES.IS-SOFTWARE:               yes
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               no
INTERFACE-FLAGS.CARRIER:                no
INTERFACE-FLAGS.PROMISC:                no
IP4.ADDRESS[1]:                         172.17.0.1/16
IP4.GATEWAY:                            --
IP4.ROUTE[1]:                           dst = 172.17.0.0/16, nh = 0.0.0.0, mt = 0
IP6.GATEWAY:                            --
BRIDGE.SLAVES:                          --
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --


GENERAL.DEVICE:                         enp0s3
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/2
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82540EM Gigabit Ethernet Controller (PRO/1000 MT Desktop Adapter)
GENERAL.DRIVER:                         e1000
GENERAL.DRIVER-VERSION:                 5.15.0-78-generic
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp0s3' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               0 (unknown)
GENERAL.IP6-CONNECTIVITY:               0 (unknown)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:03.0/net/enp0s3
GENERAL.PATH:                           pci-0000:00:03.0
GENERAL.IP-IFACE:                       enp0s3
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     no
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
INTERFACE-FLAGS.PROMISC:                no
WIRED-PROPERTIES.CARRIER:               off
IP4.GATEWAY:                            --
IP6.GATEWAY:                            --
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager config #############


[[/etc/NetworkManager/conf.d/10-ubuntu-fan.conf]]
[keyfile]
unmanaged-devices+=interface-name:fan-*


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
uri=http://connectivity-check.ubuntu.com./


[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-31-mac-addr-change]
match-device=driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no


##### NetworkManager profiles ###########


##### Netplan config ####################


[/etc/netplan/01-network-manager-all.yaml]
network:
 version: 2
 renderer: networkd
 ethernets:
   enp0s3:
     dhcp4: yes
     dhcp6: yes


##### iw reg get ########################


Region: Europe/London (based on set time zone)


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


enp0s3    no frequency information.


docker0   no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp0s3    Interface doesn't support scanning.


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

---

### Post by clarosoft on 2023-08-09
I should add that I tried booting to the previous kernel version and got the same result: No Wifi Adapter

---

