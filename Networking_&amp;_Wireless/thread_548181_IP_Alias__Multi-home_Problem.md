---
title: "IP Alias / Multi-home Problem"
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by hc_andy on 2007-09-11
Hi I've removed one of the ip aliases from /etc/network/interface (eth0:0) and restarted networking services with /etc/init.d/networking restart. 

My problem is that the ip alias for eth0:0 still comes up with I do a ipconfig -a. It is also pinging locally from the machine it's set on which indicates it's still up somehow.

How can I permanently remove the ip alias (eth0:0)  from showing up and being up?

---------------

$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:02:B3:2B:C5:7A
          inet addr:203.x.x.78  Bcast:203.x.x.95  Mask:255.255.255.224
          inet6 addr: fe80::202:b3ff:fe2b:c57a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:285337659 errors:0 dropped:0 overruns:0 frame:0
          TX packets:281786869 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1667707083 (1.5 GiB)  TX bytes:1772057439 (1.6 GiB)

eth0:0    Link encap:Ethernet  HWaddr 00:02:B3:2B:C5:7A
          inet addr:210.x.x.222  Bcast:210.x.x.255  Mask:255.255.255.255
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0:1    Link encap:Ethernet  HWaddr 00:02:B3:2B:C5:7A
          inet addr:210.x.x.224  Bcast:210.x.x.255  Mask:255.255.255.255
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2858913 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2858913 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:363644698 (346.7 MiB)  TX bytes:363644698 (346.7 MiB)

---------------

$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 203.x.x.78
        netmask 255.255.255.224
        network 203.x.x.64
        broadcast 203.x.x.95
        gateway 203.x.x.66
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 210.x.x.240

auto eth0:1
iface eth0:1 inet static
        address  210.x.x.224
        netmask 255.255.255.255

---------------

$ uname -a
Linux radius-1 2.6.20-15-server #2 SMP Sun Apr 15 07:41:34 UTC 2007 i686 GNU/Linux

---------------

Thanks.

---

### Post by noob12 on 2007-09-11
By now you probably rebooted and found it went away.  If you haven't rebooted yet, you can just put it down with **ifconfig eth0:0 down**.

It should go away when you put the interface down but if  you removed it before the networking restart then ifdown didn't find anything in /etc/network/interfaces for that interface and so that didn't put it down.  If you had first done a networking stop,  then removed it, then done a networking start (in that order) I would expect it would have gone away.

---

### Post by hc_andy on 2007-09-11
Hi Noob,

Thanks for your reply.

It's a production server so I can't go rebooting it. I've applied the **ifconfig eth0:0 down** command you mentioned and it worked a treat. Thanks for your help.

Cheers.

Andy

> **noob12 said:**
> By now you probably rebooted and found it went away.  If you haven't rebooted yet, you can just put it down with **ifconfig eth0:0 down**.

It should go away when you put the interface down but if  you removed it before the networking restart then ifdown didn't find anything in /etc/network/interfaces for that interface and so that didn't put it down.  If you had first done a networking stop,  then removed it, then done a networking start (in that order) I would expect it would have gone away.

---

