---
title: "connect in vpn but not working"
date: 2015-11-11
forum: Networking &amp; Wireless
---

### Post by cicciocappuccio on 2015-11-11
Hi to all,

I must configure a vBox ubuntu that must use a vpn cisco.

I have installed ubuntu and vpnc package.

 I have created the conf file of my vpn

```

IKE Authmode psk
Xauth username ciccio.cappuccio@smandrappona.com
Xauth password <my password not crypt>
IPSec ID qwerty
IPSec secret <group password not crypt>

IPSec gateway vpn.smandrappona.it

NAT Traversal Mode cisco-udp
```

when I try to connect the system response whit this message:
```

VPNC started in background (pid: 5913)...
```

if I exec the command  'ip link show'
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default     link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
    link/ether 08:14:2c:fa:3f:40 brd ff:ff:ff:ff:ff:ff
11: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1412 qdisc pfifo_fast state UNKNOWN mode DEFAULT group default qlen 500
    link/none
```
from this result I understand that the vpn is up

now the problem:
1 - I can't resolve the machine in the vpn
2 - the vpn go down after 2'

I don't know if it can help you to understand: I have exec the command ' route -n' and the result for **tun0** is 0.0.0.0 for Destination, Gateway and Genmask.

the last 10 line of log file /var/log/syslog are:
```
Nov 11 16:15:58 VmVodUbLTS NetworkManager[1072]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tun0, iface: tun0): no ifupdown configuration found.Nov 11 16:15:58 VmVodUbLTS NetworkManager[1072]: <warn> /sys/devices/virtual/net/tun0: couldn't determine device driver; ignoring...
Nov 11 16:17:01 VmVodUbLTS CRON[6117]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 11 16:21:57 VmVodUbLTS vpnc[6111]: connection terminated by dead peer detection
Nov 11 16:21:57 VmVodUbLTS NetworkManager[1072]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/tun0, iface: tun0)
Nov 11 16:26:38 VmVodUbLTS NetworkManager[1072]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tun0, iface: tun0)
Nov 11 16:26:38 VmVodUbLTS NetworkManager[1072]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tun0, iface: tun0): no ifupdown configuration found.
Nov 11 16:26:38 VmVodUbLTS NetworkManager[1072]: <warn> /sys/devices/virtual/net/tun0: couldn't determine device driver; ignoring...
Nov 11 16:32:48 VmVodUbLTS vpnc[6310]: connection terminated by dead peer detection
Nov 11 16:32:48 VmVodUbLTS NetworkManager[1072]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/tun0, iface: tun0)
```

where am I wrong?

---

### Post by cicciocappuccio on 2015-11-12
- UPDATE -

searching with google I have found this thread:
[http://askubuntu.com/questions/335694/vpnc-has-stopped-working-with-cisco-vpn-gateway-ubuntu-13-04](http://askubuntu.com/questions/335694/vpnc-has-stopped-working-with-cisco-vpn-gateway-ubuntu-13-04)

the solution that was suggested is: roolback the lib libgcrypt11 to an old version.

I have searched this lib but I don't have it. I have a newer version of it (1.5.3-2ubuntu4.2).

---

### Post by howefield on 2015-11-12
Bear in mind that thread is over 2 years old.

Various versions of Ubuntu packages can be download from packages.ubuntu.com, eg [http://packages.ubuntu.com/search?keywords=libgcrypt11](http://packages.ubuntu.com/search?keywords=libgcrypt11)

---

### Post by cicciocappuccio on 2015-11-12
> **howefield said:**
> Bear in mind that thread is over 2 years old.

Various versions of Ubuntu packages can be download from packages.ubuntu.com, eg [http://packages.ubuntu.com/search?keywords=libgcrypt11](http://packages.ubuntu.com/search?keywords=libgcrypt11)

updated the lib (with old version); nothing change.

---

