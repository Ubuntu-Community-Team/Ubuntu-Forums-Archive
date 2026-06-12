---
title: "LTSP + rdesktop blackscreen, no ping between clients"
date: 2015-06-08
forum: Networking &amp; Wireless
---

### Post by teufel2 on 2015-06-08
Hello

My LTSP+DHCP server works fine. Clients boot and login ubuntu desktop.
But I can't get the client to boot into a Windows7 VM using rdesktop.

My configurations & tests:

```
Internet on eth0
DHCP IP: 192.168.5.1 on eth1
NAT correctly configured (/etc/ltsp/nat)
Win7: DHCP enabled (my test vm IP: 192.168.5.21) with internet access
ThinClient: PXE boot Ip: 192.168.5.105
```

lts.conf

```
[mac thin client]
RDP_OPTIONS = "-f -a -16"
RDP_SERVER = 192.168.5.21
SCREEN_02=rdesktop
SCREEN_03=shell
SCREEN_07=ldm
```

ok, boot the thin client and i see ubuntu logon as always.
press ctrl+alt+f2  and only see blackscreen and white cursor
press ctrl+alt+f3  and check:

```
root@ltsp105:/#ifconfig
eth0 Linkencap:Ethernet HWaddr xx:xx:xx:xx:xx:xx
       inet addr:192.168.5.105  Bcast:192.168.5.255  Mask:255.255.255.0
       ...
       ...

root@ltsp105:/#ping 192.168.5.21
PING 192.168.5.21 (192.168.5.21) 56(86) bytes of data
from 192.168.5.105 icmp_seq=1 Destination Host Unreachable
from 192.168.5.105 icmp_seq=1 Destination Host Unreachable
...
...
```


If login in f7 screen y can ping to 192.168.5.21 and connect to rdp in terminal but my ip on session is 192.168.5.1

Why can´t ping from thinclient shell (192.168.5.105) to win7VM (192.168.5.21) if they're in the same range??

---

### Post by dzbaan on 2015-06-09
Hi !

Are you try connect to rdp by terminal, like rdesktop 192.168.5.21?

---

### Post by teufel2 on 2015-06-09
My fault !!  #-o

Had wrong mapped the network card in my Hyper-V. Now all works fine

Sorry.

---

