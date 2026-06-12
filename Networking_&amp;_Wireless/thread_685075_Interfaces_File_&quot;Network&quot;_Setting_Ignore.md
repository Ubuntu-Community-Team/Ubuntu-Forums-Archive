---
title: "Interfaces File &quot;Network&quot; Setting Ignored"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by rdmapes on 2008-02-01
Hello All,
I loaded 6.10 on a server w/ 2 NIC's. I have eth1 pointed back internally and can get to the server without a problem. But, when I try to get out to the world I hit a dead end. I am moving the server function of a FC4 machine that has a single hd to a scsi server.

Here is my eth0 config from the interfaces file.
auto eth0
iface eth0 inet static
        address 10.0.165.21
        network 10.0.0.0
        netmask 255.255.255.0
        broadcast 10.0.0.255
        gateway 10.0.0.1 

When I do netstat here is the reply.
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.0.165.0      0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U         0 0          0 eth1

I would like to get the destination of 10.0.0.0 to appear as I believe this is why I cannot get to the world. It seems that the system is ignoring my network setting in the interfaces file. Any thoughts? The old FC4 machine has the correct destination in the netstat.

FC4 netstat printout.
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
10.0.0.0        0.0.0.0         255.255.0.0     U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth1
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 eth0

Thanks in Advance

---

### Post by rdmapes on 2008-02-01
I found the problem.

auto eth0
iface eth0 inet static
#iptables-restore < /etc/iptables.rules
#post-down iptables-restore < /etc/iptables.rules
        address 10.0.165.21
        network 10.0.0.0
        [COLOR="Red"]netmask 255.255.0.0[/COLOR] Needed a zero in the 3rd set.
        [COLOR="Red"]broadcast 10.0.255.255[/COLOR] Needed 255 in the 3rd set.
        gateway 10.0.0.1 

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.10.0    0.0.0.0         255.255.255.0   U         0 0          0 eth1
10.0.0.0        0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         10.0.0.1        0.0.0.0         UG        0 0          0 eth0

Also, updated /etc/sysctl.conf and wham I am good to go.

Enjoy.

---

