---
title: "Can't access wired Internet, but ssh server is working."
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by Zombie13UK on 2008-09-23
Hi there. I'm having a strange problem with my Ubuntu 8.04.1 installation. I'm using an ADSL router (192.168.1.254) which is set to dish out IPs via DHCP. The Ubuntu box (shuttle-z13) is receiving an IP (192.168.1.66), and I can connect to the ssh server on that box via PuTTY with my Vista laptop.

I know it's not a hardware problem, as the Ubuntu box is dual-booted with Windows XP, and I can access the Internet fine when running XP.

Also worth noting is that I can't access my Samba shares on the Ubuntu box, even though they were working fine a few weeks ago, and no Samba configuration files have been altered.

/etc/hosts
```
127.0.0.1       localhost
127.0.1.1       shuttle-z13

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

/etc/network/interfaces
```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth0
```

/etc/resolv.conf
```
search lan
nameserver 192.168.1.254
```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:30:1b:11:3a:00
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:1bff:fe11:3a00/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:572 errors:0 dropped:0 overruns:0 frame:0
          TX packets:519 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:57500 (56.1 KB)  TX bytes:66400 (64.8 KB)
          Interrupt:21 Base address:0xe400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2992 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2992 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:149736 (146.2 KB)  TX bytes:149736 (146.2 KB)
```

Many thanks for any help you can give! :)

---

### Post by Idefix82 on 2008-09-23
Try shutting down the computer, unplugging all the cables, waiting for about 20 seconds and the plugging everything back in and booting Ubuntu. See if the problem persists.
If that solves the problem, then go to XP and enable Wake-On-Lan.

---

### Post by Zombie13UK on 2008-09-23
Thanks for the lightning-quick reply! However, I've done what you suggested, and the problem persists...

```
rich@shuttle-z13:~$ ping www.yahoo.com
ping: unknown host www.yahoo.com
rich@shuttle-z13:~$

```

---

### Post by Idefix82 on 2008-09-23
Can you type in
```
lshw -C network
```
and post the output here?

---

### Post by Zombie13UK on 2008-09-23
Got a message saying I should run that as a super-user, so I did...

```
rich@shuttle-z13:~$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth0
       version: 10
       serial: 00:30:1b:11:3a:00
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.66 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
```

Cheers!

---

### Post by Idefix82 on 2008-09-23
This is strange, it does look like your connection is up and running. I will keep thinking, but I am running out of ideas.

---

### Post by Zombie13UK on 2008-09-23
Just thought I'd add that I've just booted the Ubuntu live CD, and the Internet works perfectly from there. The problem's gotta be with the Ubuntu installed on the hard disk.

---

### Post by bogdan.veringioiu on 2008-09-23
Hi.

Can you post your routing table?

route -n

Thanks

---

### Post by Zombie13UK on 2008-09-23
```
rich@shuttle-z13:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.254   0.0.0.0         UG    100    0        0 eth0
```

Thanks! :)

---

### Post by bogdan.veringioiu on 2008-09-23
Hm.

I don't see anything weird.

Try to check your dsl router logs. See if there are connections attempts from the ubuntu box.

Regards

---

### Post by Zombie13UK on 2008-09-23
Unfortunately the router I've got at the moment is very basic (O2 Wireless Box II). Not even any logs to view!

However, wouldn't the fact that the Internet works fine under Windows XP and the Ubuntu live CD on that box prove that it's not a fault with the router?

Cheers,
Rich.

EDIT: A-ha! Now we're getting somewhere. I've pinged [www.google.co.uk](www.google.co.uk) from my Vista laptop to get the IP address. If I do "ping 66.249.91.104" on the Ubuntu box I get a reply! So this should only be a DNS issue, right? Any ideas?

---

### Post by Idefix82 on 2008-09-23
Have you tried renewing the dhcp lease by typing
```
dhclient
```
in the terminal? Although it's stramge, since you said that you did obtain an IP address. You should have been given a valid DNS at the same time.

---

### Post by Zombie13UK on 2008-09-23
I haven't used the 'dhclient' command before, so I'm not sure if this looks healthy or not...

```
rich@shuttle-z13:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:30:1b:11:3a:00
Sending on   LPF/eth0/00:30:1b:11:3a:00
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.1.66 from 192.168.1.254
DHCPREQUEST of 192.168.1.66 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.66 from 192.168.1.254
bound to 192.168.1.66 -- renewal in 42362 seconds.
rich@shuttle-z13:~$ ping www.google.co.uk
ping: unknown host www.google.co.uk

```

---

### Post by bogdan.veringioiu on 2008-09-23
Yes, you are right, it looks like a name resolving problem.

Did you enable some kind of firewall on ubuntu box?

Can you check the nameserver setting in your vista box?

Regards

---

### Post by Idefix82 on 2008-09-23
The output looks good. Can you see whether you got a DNS address? You can see it in the network manager for example (click on manual configuration and then on the DNS tab).

---

### Post by kpatz on 2008-09-23
What does your /etc/resolv.conf file look like?

---

### Post by Zombie13UK on 2008-09-23
I checked the network manager, and the DNS setting is 192.168.1.254, which is the address of the router. My Vista box also uses the same IP for DNS, and works fine...

Working Vista settings...
```
   Connection-specific DNS Suffix  . : lan
   Description . . . . . . . . . . . : Atheros AR5007 802.11b/g WiFi Adapter
   Physical Address. . . . . . . . . : 00-1F-3A-79-A0-41
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::a9d9:a286:2149:9d26%10(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.1.65(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : 23 September 2008 14:45:49
   Lease Expires . . . . . . . . . . : 24 September 2008 14:45:49
   Default Gateway . . . . . . . . . : 192.168.1.254
   DHCP Server . . . . . . . . . . . : 192.168.1.254
   DNS Servers . . . . . . . . . . . : 192.168.1.254
   NetBIOS over Tcpip. . . . . . . . : Enabled
```

My /etc/resolv.conf file is in my original post. Sorry to seem a bit dumb, but how can I disable the firewall from the command line? I can't see anything under GNOME to do with the firewall.

Cheers!

---

### Post by Zombie13UK on 2008-09-23
OK everyone! It's working, just found how to disable the firewall with "sudo iptables -F", and I can now resolve addresses! Looks like I can now install Firestarter or something to get the firewall configured correctly.

_Many_ thanks for everybody's help!

Cheers,
Rich.

---

