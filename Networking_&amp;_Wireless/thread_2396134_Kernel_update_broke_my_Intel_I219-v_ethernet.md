---
title: "Kernel update broke my Intel I219-v ethernet"
date: 2018-07-12
forum: Networking &amp; Wireless
---

### Post by Keith_Helms on 2018-07-12
My ethernet stopped working as soon as I rebooted after installing the latest updates.  I'm running Xubuntu 16.04 and went from kernel 4.4.0-127 to 4.4.0-130.  When I boot the older kernel version, it starts working again.

Here's my syslog from the working 4.4.0-127 kernel:

```
Jul 11 22:30:31 linux-corei7 NetworkManager[982]: <info>  [1531369831.7167] policy: auto-activating connection 'Wired connection 1'
Jul 11 22:30:31 linux-corei7 NetworkManager[982]: <info>  [1531369831.7173] device (enp0s31f6): Activation: starting connection 'Wired connection 1' (b180f5fe-5176-3d00-93f2-4ff51a560d00)
Jul 11 22:30:31 linux-corei7 NetworkManager[982]: <info>  [1531369831.7174] device (enp0s31f6): state change: disconnected -> prepare (reason 'none') [30 40 0]
Jul 11 22:30:31 linux-corei7 NetworkManager[982]: <info>  [1531369831.7175] manager: NetworkManager state is now CONNECTING
Jul 11 22:30:31 linux-corei7 kernel: [    5.860187] e1000e: enp0s31f6 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
Jul 11 22:30:31 linux-corei7 kernel: [    5.860237] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s31f6: link becomes ready
Jul 11 22:30:31 linux-corei7 NetworkManager[982]: <info>  [1531369831.7177] device (enp0s31f6): state change: prepare -> config (reason 'none') [40 50 0]
Jul 11 22:30:31 linux-corei7 NetworkManager[982]: <info>  [1531369831.7180] device (enp0s31f6): state change: config -> ip-config (reason 'none') [50 70 0]
Jul 11 22:30:31 linux-corei7 NetworkManager[982]: <info>  [1531369831.7199] dhcp4 (enp0s31f6): activation: beginning transaction (timeout in 45 seconds)
Jul 11 22:30:31 linux-corei7 NetworkManager[982]: <info>  [1531369831.7208] dhcp4 (enp0s31f6): dhclient started with pid 1345
Jul 11 22:30:31 linux-corei7 dhclient[1345]: DHCPREQUEST of 192.168.1.104 on enp0s31f6 to 255.255.255.255 port 67 (xid=0x2ebfdf88)
Jul 11 22:30:31 linux-corei7 dhclient[1345]: DHCPACK of 192.168.1.104 from 192.168.1.1
Jul 11 22:30:31 linux-corei7 NetworkManager[982]: <info>  [1531369831.7741]   address 192.168.1.104
Jul 11 22:30:31 linux-corei7 NetworkManager[982]: <info>  [1531369831.7741]   plen 24 (255.255.255.0)
Jul 11 22:30:31 linux-corei7 NetworkManager[982]: <info>  [1531369831.7741]   gateway 192.168.1.1
Jul 11 22:30:31 linux-corei7 NetworkManager[982]: <info>  [1531369831.7741]   server identifier 192.168.1.1
Jul 11 22:30:31 linux-corei7 NetworkManager[982]: <info>  [1531369831.7741]   lease time 86400
Jul 11 22:30:31 linux-corei7 NetworkManager[982]: <info>  [1531369831.7742]   nameserver '192.168.0.1'
Jul 11 22:30:31 linux-corei7 avahi-daemon[985]: Joining mDNS multicast group on interface enp0s31f6.IPv4 with address 192.168.1.104.
Jul 11 22:30:31 linux-corei7 NetworkManager[982]: <info>  [1531369831.7742]   nameserver '205.171.3.25'
Jul 11 22:30:31 linux-corei7 avahi-daemon[985]: New relevant interface enp0s31f6.IPv4 for mDNS.
Jul 11 22:30:31 linux-corei7 NetworkManager[982]: <info>  [1531369831.7742]   nameserver '192.168.1.1'
Jul 11 22:30:31 linux-corei7 avahi-daemon[985]: Registering new address record for 192.168.1.104 on enp0s31f6.IPv4.
Jul 11 22:30:31 linux-corei7 NetworkManager[982]: <info>  [1531369831.7742]   domain name 'Home'
Jul 11 22:30:31 linux-corei7 NetworkManager[982]: <info>  [1531369831.7742] dhcp4 (enp0s31f6): state changed unknown -> bound
Jul 11 22:30:31 linux-corei7 NetworkManager[982]: <info>  [1531369831.7748] device (enp0s31f6): state change: ip-config -> ip-check (reason 'none') [70 80 0]
Jul 11 22:30:31 linux-corei7 NetworkManager[982]: <info>  [1531369831.7752] device (enp0s31f6): state change: ip-check -> secondaries (reason 'none') [80 90 0]
Jul 11 22:30:31 linux-corei7 NetworkManager[982]: <info>  [1531369831.7754] device (enp0s31f6): state change: secondaries -> activated (reason 'none') [90 100 0]
Jul 11 22:30:31 linux-corei7 NetworkManager[982]: <info>  [1531369831.7755] manager: NetworkManager state is now CONNECTED_LOCAL
Jul 11 22:30:31 linux-corei7 dhclient[1345]: bound to 192.168.1.104 -- renewal in 37043 seconds.
Jul 11 22:30:31 linux-corei7 NetworkManager[982]: <info>  [1531369831.7787] manager: NetworkManager state is now CONNECTED_GLOBAL
Jul 11 22:30:31 linux-corei7 NetworkManager[982]: <info>  [1531369831.7788] policy: set 'Wired connection 1' (enp0s31f6) as default for IPv4 routing and DNS
Jul 11 22:30:31 linux-corei7 NetworkManager[982]: <info>  [1531369831.7793] dns-plugin[0x20e6d00]: starting dnsmasq...
Jul 11 22:30:31 linux-corei7 NetworkManager[982]: <info>  [1531369831.7804] dns-mgr: Writing DNS information to /sbin/resolvconf
```

Here's the syslog from the failing 4.4.0-130 kernel:

```
Jul 11 22:12:41 linux-corei7 NetworkManager[994]: <info>  [1531368761.8836] policy: auto-activating connection 'Wired connection 1'
Jul 11 22:12:41 linux-corei7 NetworkManager[994]: <info>  [1531368761.8841] device (enp0s31f6): Activation: starting connection 'Wired connection 1' (b180f5fe-5176-3d00-93f2-4ff51a560d00)
Jul 11 22:12:41 linux-corei7 NetworkManager[994]: <info>  [1531368761.8842] device (enp0s31f6): state change: disconnected -> prepare (reason 'none') [30 40 0]
Jul 11 22:12:41 linux-corei7 NetworkManager[994]: <info>  [1531368761.8843] manager: NetworkManager state is now CONNECTING
Jul 11 22:12:41 linux-corei7 NetworkManager[994]: <info>  [1531368761.8845] device (enp0s31f6): state change: prepare -> config (reason 'none') [40 50 0]
Jul 11 22:12:41 linux-corei7 NetworkManager[994]: <info>  [1531368761.8847] device (enp0s31f6): state change: config -> ip-config (reason 'none') [50 70 0]
Jul 11 22:12:41 linux-corei7 NetworkManager[994]: <info>  [1531368761.8849] dhcp4 (enp0s31f6): activation: beginning transaction (timeout in 45 seconds)
Jul 11 22:12:41 linux-corei7 NetworkManager[994]: <info>  [1531368761.8857] dhcp4 (enp0s31f6): dhclient started with pid 2016
Jul 11 22:12:41 linux-corei7 dhclient[2016]: DHCPREQUEST of 192.168.1.104 on enp0s31f6 to 255.255.255.255 port 67 (xid=0x6f9c36ac)
Jul 11 22:12:43 linux-corei7 avahi-daemon[906]: Joining mDNS multicast group on interface enp0s31f6.IPv6 with address fe80::5582:f552:35d2:89e5.
Jul 11 22:12:43 linux-corei7 avahi-daemon[906]: New relevant interface enp0s31f6.IPv6 for mDNS.
Jul 11 22:12:43 linux-corei7 avahi-daemon[906]: Registering new address record for fe80::5582:f552:35d2:89e5 on enp0s31f6.*.
Jul 11 22:12:44 linux-corei7 dhclient[2016]: DHCPREQUEST of 192.168.1.104 on enp0s31f6 to 255.255.255.255 port 67 (xid=0x6f9c36ac)
Jul 11 22:12:48 linux-corei7 dhclient[2016]: DHCPREQUEST of 192.168.1.104 on enp0s31f6 to 255.255.255.255 port 67 (xid=0x6f9c36ac)
Jul 11 22:12:56 linux-corei7 dhclient[2016]: DHCPDISCOVER on enp0s31f6 to 255.255.255.255 port 67 interval 3 (xid=0xf5d1f40d)
Jul 11 22:12:59 linux-corei7 dhclient[2016]: DHCPDISCOVER on enp0s31f6 to 255.255.255.255 port 67 interval 5 (xid=0xf5d1f40d)
Jul 11 22:13:04 linux-corei7 dhclient[2016]: DHCPDISCOVER on enp0s31f6 to 255.255.255.255 port 67 interval 9 (xid=0xf5d1f40d)
Jul 11 22:13:13 linux-corei7 dhclient[2016]: DHCPDISCOVER on enp0s31f6 to 255.255.255.255 port 67 interval 15 (xid=0xf5d1f40d)
Jul 11 22:13:26 linux-corei7 NetworkManager[994]: <warn>  [1531368806.8616] dhcp4 (enp0s31f6): request timed out
Jul 11 22:13:26 linux-corei7 NetworkManager[994]: <info>  [1531368806.8617] dhcp4 (enp0s31f6): state changed unknown -> timeout
Jul 11 22:13:26 linux-corei7 NetworkManager[994]: <info>  [1531368806.8784] dhcp4 (enp0s31f6): canceled DHCP transaction, DHCP client pid 2016
Jul 11 22:13:26 linux-corei7 NetworkManager[994]: <info>  [1531368806.8785] dhcp4 (enp0s31f6): state changed timeout -> done
Jul 11 22:13:26 linux-corei7 NetworkManager[994]: <info>  [1531368806.8792] device (enp0s31f6): state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Jul 11 22:13:26 linux-corei7 NetworkManager[994]: <info>  [1531368806.8798] manager: NetworkManager state is now DISCONNECTED
Jul 11 22:13:26 linux-corei7 NetworkManager[994]: <info>  [1531368806.8801] policy: disabling autoconnect for connection 'Wired connection 1'.
Jul 11 22:13:26 linux-corei7 NetworkManager[994]: <warn>  [1531368806.8806] device (enp0s31f6): Activation: failed for connection 'Wired connection 1'
Jul 11 22:13:26 linux-corei7 NetworkManager[994]: <info>  [1531368806.8821] device (enp0s31f6): state change: failed -> disconnected (reason 'none') [120 30 0]
Jul 11 22:13:26 linux-corei7 avahi-daemon[906]: Withdrawing address record for fe80::5582:f552:35d2:89e5 on enp0s31f6.
Jul 11 22:13:26 linux-corei7 avahi-daemon[906]: Leaving mDNS multicast group on interface enp0s31f6.IPv6 with address fe80::5582:f552:35d2:89e5.
Jul 11 22:13:26 linux-corei7 avahi-daemon[906]: Interface enp0s31f6.IPv6 no longer relevant for mDNS.
```

There is an error message about "ip-config-unavailable", but a search on that doesn't reveal any obvious solution.

Any ideas of what I can do to diagnose or fix this?

---

