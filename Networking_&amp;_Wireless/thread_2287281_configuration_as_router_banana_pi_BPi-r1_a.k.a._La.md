---
title: "configuration as router: banana pi BPi-r1 a.k.a. Lamobo r1"
date: 2015-07-18
forum: Networking &amp; Wireless
---

### Post by evildevil1990 on 2015-07-18
Hi all! I like complicated things so I bought this router/switch/nas and I'd like it to act as such.
From the many different easy distributions I could install (arch, openWRT, android, bananian, raspbian, that-firewall-os-I-dont-recall-now) I decided to pick one of the most difficult to configure: Lubuntu.
(mainly because I like debian based distros because of the community/support/package system)
I got working most part of the features but the router/switch part.

I tried this
```

#!/usr/bin/bash
# exit 0
echo "Configuring Network Switch ..."
ifconfig eth0 up
swconfig dev eth0 set reset 1
swconfig dev eth0 set enable_vlan 1
swconfig dev eth0 vlan 101 set ports '3 8t'
swconfig dev eth0 vlan 102 set ports '4 0 1 2 8t'
swconfig dev eth0 set apply 1
#swconfig dev eth0 show 
sleep 1
echo "Network Switch swconfig done"
echo "adding vlans ..."
ip link add link eth0 name ethint type vlan id 102
sleep 1
ip link add link eth0 name ethext type vlan id 101
sleep 1
echo "add vlans done"
echo "Starting dhcpcd on ethext"
dhcpcd -4 ethext
sleep 3
exit 0

```

it has dhcpcd -4 option. I don't have the -4 option but even removing it and let the script finish its job it doesn't work.


I also tried this with no luck
```

#
# Lamobo R1 aka BPi R1 Routerboard
#
# Speaker | LAN1 | LAN2 | LAN3 | LAN4 || LAN5 | HDMI
# SW-Port |  P2  |  P1  |  P0  |  P4  ||  P3  |
# VLAN    |  11  |  12  |  13  |  14  ||ALL(t)|
#
# Switch-Port P8 - ALL(t) boards internal CPU Port
#
#device=`ls /sys/class/net/*/device/stmmac-0* | head -1 | cut -d/ -f5`
device="eth0"
SWMAC="02:19:05:00:c8:41" # different from eth0
ip link set $device up
boot_mesg "Configure vlan-switch on $device ..."
# Reset switch, counter and enable vlan mode
swconfig dev $device set reset 1
swconfig dev $device set reset_mib 1
swconfig dev $device set enable_vlan 1
# configure vlans
swconfig dev $device vlan 11 set ports "2 3t 8t"
swconfig dev $device vlan 12 set ports "1 3t 8t"
swconfig dev $device vlan 13 set ports "0 3t 8t"
swconfig dev $device vlan 14 set ports "4 3t 8t"
# activate new config
swconfig dev $device set apply 1
# create interfaces for the vlan's
modprobe 8021q
vconfig add $device 11
vconfig add $device 12
vconfig add $device 13
vconfig add $device 14
# set local mac addresses.
ip link set dev $device.11 address $SWMAC:11
ip link set dev $device.12 address $SWMAC:12
ip link set dev $device.13 address $SWMAC:13
ip link set dev $device.14 address $SWMAC:14
# need to restart udev...
/etc/init.d/udev stop
/etc/init.d/udev start

```

Both cases link goes down on WAN and I have to disable vlan to get it working again.
cannot ping from client(static ip pc) to router, cannot ping from router to client (don't know client-client but that would be irrelevant)
I also need to get wlan working and a remote web interface (maybe some LAMP admin, I could write a remote LAMP based admin but I don't have time and I have other projects to work on now)

It's a pity... good hardware but lack of support/software/community/too many ditros

Thank you!

---

