---
title: "having problems getting my server on the internet"
date: 2014-06-28
forum: Networking &amp; Wireless
---

### Post by techguy2 on 2014-06-28
[COLOR=#333333][FONT=UbuntuRegular]I have just created a headless Ubuntu server. Typically, I've not had a problem getting the ips to work but I'm not sure what the deal in this case is.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Here is my interfaces file, which the system created when I initially installed Ubuntu:

[/FONT][/COLOR]> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
        address 63.141.224.204
        netmask 255.255.255.248
        network 63.141.224.200
        broadcast 63.141.224.207
        gateway 63.141.224.201
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 8.8.8.8 8.8.4.4
        dns-search asezo.com

[COLOR=#333333][FONT=UbuntuRegular]I can connect to this server from another virtual machine on the network but I cannot connect to it from outside of it. Also, I cannot ping anything such as google.com.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I checked a few things but I'm not great with networks and I'm still learning.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]This is what I have read to look for but I'm not sure what I'm looking for with each of these:
[/FONT][/COLOR]
> Lyon:~$ ping google.com
ping: unknown host google.com


Lyon:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         63.141.224.201  0.0.0.0         UG    0      0        0 eth0
localnet        *               255.255.255.248 U     0      0        0 eth0


Lyon:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:5d:b3:ea:08
          inet addr:63.141.224.204  Bcast:63.141.224.207  Mask:255.255.255.248
          inet6 addr: fe80::215:5dff:feb3:ea08/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1878 errors:0 dropped:0 overruns:0 frame:0
          TX packets:819 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:166226 (166.2 KB)  TX bytes:76161 (76.1 KB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

[COLOR=#333333][FONT=UbuntuRegular]I'm not sure if it matters but I am hosting it on a Windows 2012 R2 HyperV machine. I have installed Ubuntu Server 14.04.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Any help would be greatly appreciated![/FONT][/COLOR]

---

