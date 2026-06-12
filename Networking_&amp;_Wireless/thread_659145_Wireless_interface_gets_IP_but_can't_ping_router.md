---
title: "Wireless interface gets IP but can't ping router"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by kung fu buntu on 2008-01-05
I configured my router to use WPA2.

When I plug the network dongle it seems to be detected:
> usb 7-2: new high speed USB device using ehci_hcd and address 13
usb 7-2: configuration #1 chosen from 1 choice
usb 7-2: reset high speed USB device using ehci_hcd and address 13
zd1211rw 7-2:1.0: firmware version 4725
zd1211rw 7-2:1.0: zd1211b chip 083a:4505 v4810 high 00-13-f7 AL2230_RF pa0 g--NS
zd1211rw 7-2:1.0: eth4
usbcore: registered new interface driver zd1211rw
ADDRCONF(NETDEV_UP): eth4: link is not ready
ADDRCONF(NETDEV_UP): eth4: link is not ready

Using knetworkmanager (*) I can get an IP sometimes. Output of dmesg:
> SoftMAC: Open Authentication completed with 00:13:f7:74:f6:04
ADDRCONF(NETDEV_CHANGE): eth4: link becomes ready
eth4: no IPv6 routers present(*) Is there a way to do this using the CLI? And I don't mean to configure the services in /etc/ files.

My interfaces gets IP 192.168.2.101 but I can't even ping my router in 192.168.2.1:
[FONT="Courier New"]ping: sendmsg: Operation not permitted[/FONT]

Any ideas?
And no... I don't have any another eth* plugged.

Thanks

---

### Post by HermanAB on 2008-01-05
You need a bunch of parameters for a network connection to work, much more than just an IP address:
IP Address
Subnet mask
Gateway address
DNS address
Hostname
Default route

If any of those is wrong, then some things won't work.

Sooooo, check everything with ifconfig and also check route and /etc/resolv.conf.

Cheers,

Herman

---

### Post by kung fu buntu on 2008-01-05
I assumed that knetworkmanager did all that automatically, since it's a point and click GUI.
It asks me for ESSID, type of encryption used and passphrase. Wouldn't it be reasonable to assume that when it gets the IP (likely by DHCP since that is what I have configured in the router) it also gets every other parameter?
For a non-wireless connection I just have to dhclient eth2 to get everything working.

It seems to be configured correctly: ```
eth4      Link encap:Ethernet  HWaddr 00:13:F7:6E:CC:94
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::213:f7ff:fe6e:cc94/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:3 dropped:0 overruns:0 frame:3
          TX packets:319 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1408 (1.3 KiB)  TX bytes:15263 (14.9 KiB)
```

---

### Post by kung fu buntu on 2008-01-06
anyone?

---

### Post by jeefers on 2008-07-09
make sure that iptables is not running or if you want to remove iptables with 

apt-get remove iptables

---

