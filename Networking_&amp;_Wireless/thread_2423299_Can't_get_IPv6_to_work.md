---
title: "Can't get IPv6 to work"
date: 2019-07-20
forum: Networking &amp; Wireless
---

### Post by donsy on 2019-07-20
Version 18.04.2 LTS.
I can't get IPv6 to work. It's configured on my router (Netgear R6120) as connection type DHCP (recommended). Same results with both wireless and Ethernet connection. Below is the output from what I believe to be the pertinent commands (using Ethernet connection). I've already googled this extensively but can't find anything that helps.
```
$ ifconfig
enp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.0.0.3  netmask 255.255.255.0  broadcast 10.0.0.255
        inet6 fe80::a8d6:29a8:f0d7:3047  prefixlen 64  scopeid 0x20<link>
        ether 84:8f:69:af:16:8b  txqueuelen 1000  (Ethernet)
        RX packets 15678  bytes 22836291 (22.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 7308  bytes 620655 (620.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 234  bytes 20854 (20.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 234  bytes 20854 (20.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


$ route -4
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         www.routerlogin 0.0.0.0         UG    100    0        0 enp3s0
10.0.0.0        0.0.0.0         255.255.255.0   U     100    0        0 enp3s0
link-local      0.0.0.0         255.255.0.0     U     1000   0        0 enp3s0


$ route -6
Kernel IPv6 routing table
Destination                    Next Hop                   Flag Met Ref Use If
ip6-localhost/128              [::]                       U    256 1     0 lo
fe80::/64                      [::]                       U    100 6     0 enp3s0
fe80::/64                      [::]                       U    256 1     0 enp3s0
[::]/0                         [::]                       !n   -1  1     0 lo
ip6-localhost/128              [::]                       Un   0   7     0 lo
BSWZ1S1/128                    [::]                       Un   0   4     0 enp3s0
ip6-mcastprefix/8              [::]                       U    256 10     0 enp3s0
[::]/0                         [::]                       !n   -1  1     0 lo


$ cat /proc/net/if_inet6
fe80000000000000a8d629a8f0d73047 02 40 20 80   enp3s0
00000000000000000000000000000001 01 80 10 80       lo


$ lsmod | grep ipv6
nf_reject_ipv6         16384  1 ip6t_REJECT
nf_conntrack_ipv6      20480  5
nf_defrag_ipv6         20480  1 nf_conntrack_ipv6
nf_conntrack          131072  8 xt_conntrack,nf_conntrack_ipv6,nf_conntrack_ipv4,nf_nat,nf_nat_ftp,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_conntrack_ftp



```

---

### Post by The Cog on 2019-07-20
I'm not familiar with how interfaces get given an IPv6 address, but I can see that your interface has not been configured with a routable IPv6 address. The address that it does have (fe80::...) is a "link local" address that can only talk to other addresses on the same cable (like your router, perhaps). You should also see a v6 address with scope "global". you could try with the command ```
sudo dhclient -6 -v
```

---

### Post by donsy on 2019-07-20
Here's the output I get:
```
$ sudo dhclient -6 -v
Internet Systems Consortium DHCP Client 4.3.5
Copyright 2004-2016 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/


RTNETLINK answers: Operation not possible due to RF-kill
no link-local IPv6 address for wlp1s0


If you think you have received this message due to a bug rather
than a configuration issue please read the section on submitting
bugs on either our web page at www.isc.org or in the README file
before submitting a bug.  These pages explain the proper
process and the information we find helpful for debugging..


exiting.



```

---

### Post by The Cog on 2019-07-21
That's odd. According to the ifconfig output above, you don't have an interface wlp1s0, but dhclient is complaining about it. I don't think I would know what to do about that other than try:
```
sudo dhclient -6 -v enp3s0
```

---

### Post by donsy on 2019-07-21
```
$ sudo dhclient -6 -v enp3s0 
Internet Systems Consortium DHCP Client 4.3.5
Copyright 2004-2016 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/


Listening on Socket/enp3s0
Sending on   Socket/enp3s0
Created duid "\000\001\000\001$\307\221k\204\217i\257\026\213".
PRC: Soliciting for leases (INIT).
XMT: Forming Solicit, 0 ms elapsed.
XMT:  X-- IA_NA 69:af:16:8b
XMT:  | X-- Request renew in  +3600
XMT:  | X-- Request rebind in +5400
XMT: Solicit on enp3s0, interval 1090ms.
send_packet6: Operation not permitted
dhc6: send_packet6() sent -1 of 56 bytes
XMT: Forming Solicit, 1090 ms elapsed.
XMT:  X-- IA_NA 69:af:16:8b
XMT:  | X-- Request renew in  +3600
XMT:  | X-- Request rebind in +5400
XMT: Solicit on enp3s0, interval 2190ms.
send_packet6: Operation not permitted
dhc6: send_packet6() sent -1 of 56 bytes
XMT: Forming Solicit, 3280 ms elapsed.
XMT:  X-- IA_NA 69:af:16:8b
XMT:  | X-- Request renew in  +3600
XMT:  | X-- Request rebind in +5400
XMT: Solicit on enp3s0, interval 4500ms.
send_packet6: Operation not permitted
dhc6: send_packet6() sent -1 of 56 bytes
XMT: Forming Solicit, 7780 ms elapsed.
XMT:  X-- IA_NA 69:af:16:8b
XMT:  | X-- Request renew in  +3600
XMT:  | X-- Request rebind in +5400
XMT: Solicit on enp3s0, interval 8830ms.
send_packet6: Operation not permitted
dhc6: send_packet6() sent -1 of 56 bytes
XMT: Forming Solicit, 16620 ms elapsed.
XMT:  X-- IA_NA 69:af:16:8b
XMT:  | X-- Request renew in  +3600
XMT:  | X-- Request rebind in +5400
XMT: Solicit on enp3s0, interval 17620ms.
send_packet6: Operation not permitted
dhc6: send_packet6() sent -1 of 56 bytes
XMT: Forming Solicit, 34260 ms elapsed.
XMT:  X-- IA_NA 69:af:16:8b
XMT:  | X-- Request renew in  +3600
XMT:  | X-- Request rebind in +5400
XMT: Solicit on enp3s0, interval 33970ms.
send_packet6: Operation not permitted
dhc6: send_packet6() sent -1 of 56 bytes
^C



```

---

### Post by The Cog on 2019-07-22
That looks like a firewall is blocking the outgoing request.
Google for "send_packet6: Operation not permitted"

---

### Post by donsy on 2019-07-22
```
$ sudo ufw disable
Firewall stopped and disabled on system startup
$ sudo ufw status
Status: inactive
$ sudo dhclient -6 -v enp3s0
Internet Systems Consortium DHCP Client 4.3.5
Copyright 2004-2016 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/


Listening on Socket/enp3s0
Sending on   Socket/enp3s0
PRC: Soliciting for leases (INIT).
XMT: Forming Solicit, 0 ms elapsed.
XMT:  X-- IA_NA 69:af:16:8b
XMT:  | X-- Request renew in  +3600
XMT:  | X-- Request rebind in +5400
XMT: Solicit on enp3s0, interval 1040ms.
XMT: Forming Solicit, 1040 ms elapsed.
XMT:  X-- IA_NA 69:af:16:8b
XMT:  | X-- Request renew in  +3600
XMT:  | X-- Request rebind in +5400
XMT: Solicit on enp3s0, interval 2180ms.
XMT: Forming Solicit, 3220 ms elapsed.
XMT:  X-- IA_NA 69:af:16:8b
XMT:  | X-- Request renew in  +3600
XMT:  | X-- Request rebind in +5400
XMT: Solicit on enp3s0, interval 4520ms.
XMT: Forming Solicit, 7740 ms elapsed.
XMT:  X-- IA_NA 69:af:16:8b
XMT:  | X-- Request renew in  +3600
XMT:  | X-- Request rebind in +5400
XMT: Solicit on enp3s0, interval 9330ms.
XMT: Forming Solicit, 17080 ms elapsed.
XMT:  X-- IA_NA 69:af:16:8b
XMT:  | X-- Request renew in  +3600
XMT:  | X-- Request rebind in +5400
XMT: Solicit on enp3s0, interval 19220ms.
XMT: Forming Solicit, 36320 ms elapsed.
XMT:  X-- IA_NA 69:af:16:8b
XMT:  | X-- Request renew in  +3600
XMT:  | X-- Request rebind in +5400
XMT: Solicit on enp3s0, interval 39780ms.
XMT: Forming Solicit, 76140 ms elapsed.
XMT:  X-- IA_NA 69:af:16:8b
XMT:  | X-- Request renew in  +3600
XMT:  | X-- Request rebind in +5400
XMT: Solicit on enp3s0, interval 77060ms.
^C



```

---

### Post by donsy on 2019-07-23
I'm marking this thread as solved even though it won't be until I change routers. It seems like Netgear routers have a problem with IPv6 implementation.

---

### Post by chili555 on 2019-07-23
> **donsy said:**
> I'm marking this thread as solved even though it won't be until I change routers. It seems like Netgear routers have a problem with IPv6 implementation.
I don't think it's a Netgear-specific issue. 

In order for IPv6 to work properly, your ISP must offer it, your internet device; that is modem, etc., usually provided by your ISP AND your router must all fully support IPv6. There are many routers, not just Netgear, that were designed and built before the introduction of IPv6 that don't and probably even with an official firware update, probably never will support IPv6. Some can support IPv6 with unofficial, third-party firmware.

I know, I have a stack of them on my shelf!

---

### Post by #&amp;thj^% on 2019-07-23
> **chili555 said:**
> I don't think it's a Netgear-specific issue. 

In order for IPv6 to work properly, your ISP must offer it, your internet device; that is modem, etc., usually provided by your ISP AND your router must all fully support IPv6. There are many routers, not just Netgear, that were designed and built before the introduction of IPv6 that don't and probably even with an official firware update, probably never will support IPv6. Some can support IPv6 with unofficial, third-party firmware.

I know, I have a stack of them on my shelf!

+1 NetGear R6350 dose.
For the OP I just saw this thread, and you can check with:
[B]Note:Router's IPv6 Address on LAN
Not available[/B]
```
test -f /proc/net/if_inet6 && echo "IPv6 supported" || echo "IPv6 not supported"
IPv6 supported

```
Hope this helps.
I keep mine disabled:
```
sysctl -a | grep disable_ipv6
sysctl: permission denied on key 'fs.protected_fifos'
sysctl: permission denied on key 'fs.protected_hardlinks'
sysctl: permission denied on key 'fs.protected_regular'
sysctl: permission denied on key 'fs.protected_symlinks'
sysctl: permission denied on key 'kernel.cad_pid'
sysctl: permission denied on key 'kernel.unprivileged_userns_apparmor_policy'
sysctl: permission denied on key 'kernel.usermodehelper.bset'
sysctl: permission denied on key 'kernel.usermodehelper.inheritable'
sysctl: permission denied on key 'net.core.bpf_jit_harden'
sysctl: permission denied on key 'net.core.bpf_jit_kallsyms'
sysctl: permission denied on key 'net.core.bpf_jit_limit'
sysctl: permission denied on key 'net.ipv4.tcp_fastopen_key'
sysctl: permission denied on key 'net.ipv6.conf.all.stable_secret'
net.ipv6.conf.all.disable_ipv6 = 0
sysctl: permission denied on key 'net.ipv6.conf.default.stable_secret'
net.ipv6.conf.default.disable_ipv6 = 0
sysctl: permission denied on key 'net.ipv6.conf.enp0s25.stable_secret'
net.ipv6.conf.enp0s25.disable_ipv6 = 0
sysctl: permission denied on key 'net.ipv6.conf.lo.stable_secret'
net.ipv6.conf.lo.disable_ipv6 = 0
sysctl: permission denied on key 'net.ipv6.conf.tun0.stable_secret'
net.ipv6.conf.tun0.disable_ipv6 = 0
sysctl: permission denied on key 'net.ipv6.conf.wlp3s0.stable_secret'
net.ipv6.conf.wlp3s0.disable_ipv6 = 0
sysctl: permission denied on key 'vm.mmap_rnd_bits'
sysctl: permission denied on key 'vm.mmap_rnd_compat_bits'
sysctl: permission denied on key 'vm.stat_refresh'

```

---

### Post by donsy on 2019-07-23
> **chili555 said:**
> I don't think it's a Netgear-specific issue. 

In order for IPv6 to work properly, your ISP must offer it, your internet device; that is modem, etc., usually provided by your ISP AND your router must all fully support IPv6. There are many routers, not just Netgear, that were designed and built before the introduction of IPv6 that don't and probably even with an official firware update, probably never will support IPv6. Some can support IPv6 with unofficial, third-party firmware.

I know, I have a stack of them on my shelf!
My ISP, Cox Communications, fully supports IPv6 dual-stack, DHCP. My Motorola Docsis 3.0 modem fully supports IPv6. My old router, a Linksys E900, FULLY SUPPORTED IPv6 -- never had an issue. The only reason I changed was my old router was 802.11n and I wanted to try 802.11ac. After much searching and tweaking the settings, including talking to Netgear support while it was still under warranty, I find the problem to be with the Netgear router itself. And if you browse the internet you'll find that I'm not the only one.

---

