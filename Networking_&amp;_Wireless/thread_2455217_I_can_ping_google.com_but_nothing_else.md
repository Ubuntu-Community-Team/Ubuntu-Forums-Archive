---
title: "I can ping google.com but nothing else?"
date: 2020-12-15
forum: Networking &amp; Wireless
---

### Post by dj5000 on 2020-12-15
Something got messed up with my network setting after I defined a static IP. it took me a while to make it working again but now there some weird symptoms. One of those is that can't resolve dns anymore. I can ping google.com with no problem but pinging microsoft.com, godaddy.com or even 8.8.8.8 gets me ping: connect: Network is unreachable


The machine is an I7, 32Gb ram, running Ubuntu server 20.04, mostly headless. using ssh.


Other devices on my network doesn't have the problem.[INDENT][COLOR=#008000]$ ifconfig[/COLOR][/INDENT]
[INDENT][COLOR=#008000]docker0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500[/COLOR][/INDENT]
[INDENT][COLOR=#008000]        inet 172.17.0.1  netmask 255.255.0.0  broadcast 172.17.255.255[/COLOR][/INDENT]
[INDENT][COLOR=#008000]        ether 02:42:22:f6:ee:c8  txqueuelen 0  (Ethernet)[/COLOR][/INDENT]
[INDENT][COLOR=#008000]        RX packets 0  bytes 0 (0.0 B)[/COLOR][/INDENT]
[INDENT][COLOR=#008000]        RX errors 0  dropped 0  overruns 0  frame 0[/COLOR][/INDENT]
[INDENT][COLOR=#008000]        TX packets 0  bytes 0 (0.0 B)[/COLOR][/INDENT]
[INDENT][COLOR=#008000]        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0[/COLOR][/INDENT]
[INDENT][COLOR=#008000]
[/COLOR][/INDENT]
[INDENT][COLOR=#008000]eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500[/COLOR][/INDENT]
[INDENT][COLOR=#008000]        inet 192.168.1.101  netmask 255.255.255.0  broadcast 192.168.1.255[/COLOR][/INDENT]
[INDENT][COLOR=#008000]        inet6 2a02:14c:805f:ffc5:1ac0:4dff:fe41:3e93  prefixlen 64  scopeid 0x0<global>[/COLOR][/INDENT]
[INDENT][COLOR=#008000]        inet6 fe80::1ac0:4dff:fe41:3e93  prefixlen 64  scopeid 0x20<link>[/COLOR][/INDENT]
[INDENT][COLOR=#008000]        ether 18:c0:4d:41:3e:93  txqueuelen 1000  (Ethernet)[/COLOR][/INDENT]
[INDENT][COLOR=#008000]        RX packets 331527  bytes 83760648 (83.7 MB)[/COLOR][/INDENT]
[INDENT][COLOR=#008000]        RX errors 0  dropped 0  overruns 0  frame 0[/COLOR][/INDENT]
[INDENT][COLOR=#008000]        TX packets 182973  bytes 52213897 (52.2 MB)[/COLOR][/INDENT]
[INDENT][COLOR=#008000]        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0[/COLOR][/INDENT]
[INDENT][COLOR=#008000]        device interrupt 16  memory 0x53200000-53220000[/COLOR][/INDENT]
[INDENT][COLOR=#008000]
[/COLOR][/INDENT]
[INDENT][COLOR=#008000]lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536[/COLOR][/INDENT]
[INDENT][COLOR=#008000]        inet 127.0.0.1  netmask 255.0.0.0[/COLOR][/INDENT]
[INDENT][COLOR=#008000]        inet6 ::1  prefixlen 128  scopeid 0x10<host>[/COLOR][/INDENT]
[INDENT][COLOR=#008000]        loop  txqueuelen 1000  (Local Loopback)[/COLOR][/INDENT]
[INDENT][COLOR=#008000]        RX packets 209338  bytes 12397801 (12.3 MB)[/COLOR][/INDENT]
[INDENT][COLOR=#008000]        RX errors 0  dropped 0  overruns 0  frame 0[/COLOR][/INDENT]
[INDENT][COLOR=#008000]        TX packets 209338  bytes 12397801 (12.3 MB)[/COLOR][/INDENT]
[INDENT][COLOR=#008000]        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0[/COLOR]


[/INDENT]
my /etc/resolv.conf keeps getting cleaned up every reboot to this state:[INDENT][COLOR=#008000]# This file is managed by man:systemd-resolved(8). Do not edit.[/COLOR][/INDENT]
[INDENT][COLOR=#008000]#[/COLOR][/INDENT]
[INDENT][COLOR=#008000]# This is a dynamic resolv.conf file for connecting local clients to the[/COLOR][/INDENT]
[INDENT][COLOR=#008000]# internal DNS stub resolver of systemd-resolved. This file lists all[/COLOR][/INDENT]
[INDENT][COLOR=#008000]# configured search domains.[/COLOR][/INDENT]
[INDENT][COLOR=#008000]#[/COLOR][/INDENT]
[INDENT][COLOR=#008000]# Run "resolvectl status" to see details about the uplink DNS servers[/COLOR][/INDENT]
[INDENT][COLOR=#008000]# currently in use.[/COLOR][/INDENT]
[INDENT][COLOR=#008000]#[/COLOR][/INDENT]
[INDENT][COLOR=#008000]# Third party programs must not access this file directly, but only through the[/COLOR][/INDENT]
[INDENT][COLOR=#008000]# symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,[/COLOR][/INDENT]
[INDENT][COLOR=#008000]# replace this symlink by a static file or a different symlink.[/COLOR][/INDENT]
[INDENT][COLOR=#008000]#[/COLOR][/INDENT]
[INDENT][COLOR=#008000]# See man:systemd-resolved.service(8) for details about the supported modes of[/COLOR][/INDENT]
[INDENT][COLOR=#008000]# operation for /etc/resolv.conf.[/COLOR][/INDENT]
[INDENT][COLOR=#008000]
[/COLOR][/INDENT]
[INDENT][COLOR=#008000]nameserver 127.0.0.53[/COLOR][/INDENT]
[INDENT][COLOR=#008000]options edns0 trust-ad[/COLOR][/INDENT]
[INDENT][COLOR=#008000]$ netstat -r[/COLOR][/INDENT]
[INDENT][COLOR=#008000]Kernel IP routing table[/COLOR][/INDENT]
[INDENT][COLOR=#008000]Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface[/COLOR][/INDENT]
[INDENT][COLOR=#008000]172.17.0.0      0.0.0.0         255.255.0.0     U         0 0          0 docker0[/COLOR][/INDENT]
[INDENT][COLOR=#008000]192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eno1[/COLOR]


[/INDENT]
/etc/netplan/00-installer-config.yaml[INDENT][COLOR=#008000]network:[/COLOR][/INDENT]
[INDENT][COLOR=#008000]  version: 2[/COLOR][/INDENT]
[INDENT][COLOR=#008000]  renderer: networkd[/COLOR][/INDENT]
[INDENT][COLOR=#008000]    ethernets:[/COLOR][/INDENT]
[INDENT][COLOR=#008000]        eno1:[/COLOR][/INDENT]
[INDENT][COLOR=#008000]            addresses: ['192.168.1.101/24'][/COLOR][/INDENT]
[INDENT][COLOR=#008000]            nameservers:[/COLOR][/INDENT]
[INDENT][COLOR=#008000]                addresses: [8.8.8.8, 8.8.4.4, 192.168.1.1, 212.143.0.1, 194.90.0.1, '2a02:148::1', '2a02:149::>
[/COLOR](yaml formatting is correct in source file)


[/INDENT]
Any ideas what went wrong and how to fix it?
Please help...


Btw, pinging IP6 addresses does work!

---

### Post by TheFu on 2020-12-15
> (yaml formatting is correct in source file)
Prove it. What you've posted above has errors besides wrong indentation. Details matter.

Use code-tags in the post above. Just edit the post.   [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code)
All text, commands, and command output should be posted wrapped in 'code tags'.

Please.

I don't use IPv6.
I don't use docker.
I don't use resolvconf or systemd-resolved. If you have a DNS server on your LAN, then you don't want/need these.

Simplify.  I suspect that IPv6 is taking priority.
Try this: 
$ more /etc/netplan/01-static.yaml 
```
network:
  version: 2
  renderer: networkd
  ethernets:
     eno1:
       addresses:
          - 192.168.1.101/24
       dhcp4: false
       dhcp6: false
       gateway4: 192.168.1.1
       nameservers:
         addresses: [ 8.8.8.8,8.8.4.4 ]
```
to get started.
That's the shortest netplan for a static IP that I know works.  Notice the indentation is all spaces (never tabs) and that there aren't any spaces between nameservers.

Sorry, I didn't post this earlier. I was on a different machine with a terrible keyboard.

---

### Post by SeijiSensei on 2020-12-15
```
$ netstat -r
Kernel IP routing table
Destination Gateway Genmask Flags MSS Window irtt Iface
172.17.0.0 0.0.0.0 255.255.0.0 U 0 0 0 docker0
192.168.1.0 0.0.0.0 255.255.255.0 U 0 0 0 eno1

```
You don't have a default route to an upstream router. I'm guessing it's some machine with a 192.168.1.something address.  Let's call it 192.168.1.1. Then you need
```
sudo ip route add default via 192.168.1.1
```
or whatever the correct upstream address may be.

---

### Post by The Cog on 2020-12-15
Without an IPv4 default route, only IPv6 destinations will be reachable. I presume you have working IPv6.
 Try ```
ping google.com
``` and I expect to see successful pings to an IPv6 destination.
Also to be sure, post the output of```
ip -4 route
ip -6 route
```

---

