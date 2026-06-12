---
title: "Fresh Ununtu install needs restarting after Cisco switch reloads"
date: 2014-05-15
forum: Networking &amp; Wireless
---

### Post by canzi on 2014-05-15
Hi All
If a Ubuntu server is communicating across a Cisco switch or to a Cisco switch when that switch is rebooted for some reason, that server is then unable to communicate with that vlan until networking service is restarted or in 14.04 the whole server needs restarting,
Suse and Centos do not have this issue,

further info

_Network Layout_
ubuntu -> core -> SE Switch -> SD Switch

_before switch restart_
> root@ubuntu:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.0.0.1        0.0.0.0         UG    0      0        0 eth0
10.0.0.0        *               255.255.255.0   U     0      0        0 eth0

> root@ubuntu:~# tracepath 10.4.168.1
 1?: [LOCALHOST]                                         pmtu 1500
 1:  10.0.0.1                                              0.470ms
 1:  10.0.0.1                                              0.395ms
 2:  10.4.0.78                                             0.668ms
 3:  10.4.176.38                                           0.844ms reached
     Resume: pmtu 1500 hops 3 back 3

_Steps to break_
ping SD Switch 10.4.168.1
reload SE Switch 10.4.76.1

_Broken and can now not ping 10.4.168.1 until service or machine rebooted_
> root@ubuntu:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.0.0.1        0.0.0.0         UG    0      0        0 eth0
10.0.0.0        *               255.255.255.0   U     0      0        0 eth0

> root@ubuntu:~# tracepath 10.4.168.1
 1?: [LOCALHOST]                                         pmtu 1500
 1:  10.0.0.254                                            0.470ms
 1:  10.0.0.254                                            0.488ms
 2:  10.0.0.254                                            0.482ms reached


any help appreciated Steve

---

### Post by TheFu on 2014-05-15
Don't know.  Could this be it? [http://arstechnica.com/tech-policy/2014/05/photos-of-an-nsa-upgrade-factory-show-cisco-router-getting-implant/](http://arstechnica.com/tech-policy/2014/05/photos-of-an-nsa-upgrade-factory-show-cisco-router-getting-implant/)

---

