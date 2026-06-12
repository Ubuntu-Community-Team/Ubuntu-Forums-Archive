---
title: "Weird Behavior with Bridged network"
date: 2021-06-21
forum: Networking &amp; Wireless
---

### Post by crono1412 on 2021-06-21
I have kinda a long story.  TLDR is that I had a working network bridge to share with vnets from KVM instances, but now it doesn't work in strange ways.

I have an Ubuntu 20.04 (upgraded over the years from much earlier versions) server running file shares, plex, and various other services to my home and wide network. The server uses an ethernet connection directly to the router.  Other devices on the network are working with the internet properly regardless of the issues I'm having on this server.

Originally this was just a file/plex server, but I started playing with KVM, GPU Passthrough, and Home Assistant virtual machines.  The KVM with GPU Passthrough is an experiment to see if I can create a headless steam gaming server (like Stadia). To get the various SteamLink hardware to talk to that VM, I needed to create a network bridge which bridged the physical NIC with the virtual ones. I set this up and it worked great for months, no problems.

```
brctl addbr br0
brctl addif enp12s0 vnet0 vnet1
```

Then updated my /etc/network/interfaces file. The br0 used DHCP

Then last friday I decided I wanted to set up a pihole on this same server.  This required changing things to that I had a static address.  I went and downloaded/installed the pihole script from their website, and got everything set up.  Seemed good until a reboot, then I had no network connectivity.  Changing the br0 to be DHCP again restored function, but obviously wouldn't work for the pihole.  I fought with this for a few days then decided to give up, and I removed the PiHole software from the server using its built in script.

Problem is, throughout my troubleshooting, I've somehow configured it so that whenever the br0 is up, I lose complete connectivity to the internet. After much research, I thought the issue was ip routes. So today I messed around with ip routing (deleted default route which used my physical interface, so the only route to the gateway was through the bridge).  This seemed to fix internet connectivity... but weirdly enough I cannot ping my gateway, and no devices on the local network can see the server.  In spite of this, Plex (which phones home for ease of use outside the local network) works just fine, and I can browse the internet from the server with no problem. Nothing can see the server from the LAN, but the server can talk to WAN through the same gateway, even though it can't ping the gateway.

Another possibly related issue is that even when I completely delete the br0 gateway, like a zombie it will reappear on reboot or restart of networking service.  This is after changing all the VMs to use NAT (which doesn't work for my purposes) instead of br0, and removing it from the interfaces file, and using brctl to delete it.  It somehow keeps coming back.  I think that this must be because some leftover config from pihole must reference it and keeps resurrecting it.  In fact, all these issues might relate back to pihole configs.

Any advice would be appreciated.  I've been pulling my hair out all weekend trying to find a solution.  Since its a network drive primarily, not having access within my home is a big deal. Thanks in advance for any ideas.

EDIT: I thought maybe I had some conflicting network mangers messing with things, so I removed ifupdown and tried to set this up with netplan.  Bridge created with netplan has the exact same behavior.  Here's my netplan yaml

```
network:
  version: 2
  renderer: networkd
  ethernets:
    enp12s0:
      dhcp4: true
      dhcp6: true
  bridges:
    br0:
      interfaces: [enp12s0, vnet0, vnet1]
      parameters:
        stp: true
        forward-delay: 4
      addresses: [ 192.168.1.4/24 ]
  vlans:
    vnet0:
      accept-ra: no
      id: 0
      link: enp12s0
    vnet1:
      accept-ra: no
      id: 1
      link: enp12s0



```

I've tried this config without enp12s0 as a bridge interface (as the example yaml here [https://netplan.io/examples/](https://netplan.io/examples/) for virtio bridge states), but that just results in no network connection for the VMs.

---

### Post by TheFu on 2021-06-21
Less explanation and more config files and commands showing the facts, please.

---

### Post by crono1412 on 2021-06-21
Well, what would you like to see?

---

### Post by crono1412 on 2021-06-21
Here is the current configuration, netplan.

```
master@HomeServer:/etc/netplan$ sudo netplan get all
network:
  bridges:
    br0:
      addresses:
      - 192.168.1.4/24
      dhcp4: false
      gateway4: 192.168.1.1
      interfaces:
      - enp12s0
      nameservers:
        addresses:
        - 192.168.1.1
        - 8.8.8.8
      parameters:
        forward-delay: 4
        stp: true
  ethernets:
    enp12s0:
      dhcp4: false
      dhcp6: false
  renderer: networkd
  version: 2

```

With this configuration, I can access the internet, and the VMs get the IP addresse that it should get (192.168.1.5).  But I cannot ping the gateway (192.168.1.1) from the server, and I cannot ping the server (192.168.1.4) from other devices on the same network. I also cannot ping the VMs from the host (192.168.1.4 to 192.168.1.5).

Here's the ifconfig
```
br0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.4  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::d607:2828:d728:82d1  prefixlen 64  scopeid 0x20<link>
        ether 0e:8a:7f:b5:d9:c9  txqueuelen 1000  (Ethernet)
        RX packets 38143  bytes 9269734 (9.2 MB)
        RX errors 0  dropped 488  overruns 0  frame 0
        TX packets 8111  bytes 1326416 (1.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


enp12s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.4  netmask 255.255.255.0  broadcast 192.168.1.255
        ether 0e:8a:7f:b5:d9:c9  txqueuelen 1000  (Ethernet)
        RX packets 39845  bytes 10076494 (10.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 14534  bytes 1817361 (1.8 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 13062  bytes 1903783 (1.9 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 13062  bytes 1903783 (1.9 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


tun0: flags=4305<UP,POINTOPOINT,RUNNING,NOARP,MULTICAST>  mtu 1500
        inet 10.8.0.1  netmask 255.255.255.255  destination 10.8.0.2
        inet6 fe80::fe5b:e1a6:8022:a25  prefixlen 64  scopeid 0x20<link>
        unspec 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  txqueuelen 100  (UNSPEC)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 183  bytes 21534 (21.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


vnet0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 169.254.165.48  netmask 255.255.0.0  broadcast 169.254.255.255
        inet6 fe80::fc54:ff:fede:61b5  prefixlen 64  scopeid 0x20<link>
        inet6 fe80::f7b0:e9a1:6eb1:6097  prefixlen 64  scopeid 0x20<link>
        ether fe:54:00:de:61:b5  txqueuelen 1000  (Ethernet)
        RX packets 358  bytes 40923 (40.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 9295  bytes 1147353 (1.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

ip route:
```
default via 192.168.1.1 dev br0 proto static 
default via 192.168.1.1 dev enp12s0 src 192.168.1.4 metric 202 
default via 192.168.1.1 dev br0 src 192.168.1.4 metric 203 
10.8.0.0/24 via 10.8.0.2 dev tun0 
10.8.0.2 dev tun0 proto kernel scope link src 10.8.0.1 
169.254.0.0/16 dev vnet0 scope link src 169.254.165.48 metric 209 
192.168.1.0/24 dev enp12s0 proto dhcp scope link src 192.168.1.4 metric 202 
192.168.1.0/24 dev br0 proto dhcp scope link src 192.168.1.4 metric 203
```

I moved my /etc/network/interfaces file to interfaces.old

What else would you like to see?

---

### Post by TheFu on 2021-06-21
The netplan, the routing table, the ip address for the VM host, the ip address for each guest VM ... for starters.

Whenever a VM is involved, the VM host shouldn't use DHCP addresses. It should have a static IP.

I don't see any gateway set or DNS servers.  There are example netplan files in these forums. I posted one in the last week which immediately fixed someone else's problem. Did you see that one?  He was trying to use DHCP too.  Bad idea.

---

### Post by TheFu on 2021-06-21
tun?  Nobody mentioned having a VPN running before.

enp12s0 shouldn't have any IP address assigned.

**route -n** is easier to read.
or use
**ip r | column -t**
to make is readable.

---

### Post by crono1412 on 2021-06-21
```
master@HomeServer:/etc/netplan$ route -nKernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 br0
0.0.0.0         192.168.1.1     0.0.0.0         UG    202    0        0 enp12s0
0.0.0.0         192.168.1.1     0.0.0.0         UG    203    0        0 br0
10.8.0.0        10.8.0.2        255.255.255.0   UG    0      0        0 tun0
10.8.0.2        0.0.0.0         255.255.255.255 UH    0      0        0 tun0
169.254.0.0     0.0.0.0         255.255.0.0     U     209    0        0 vnet0
192.168.1.0     0.0.0.0         255.255.255.0   U     202    0        0 enp12s0
192.168.1.0     0.0.0.0         255.255.255.0   U     203    0        0 br0

```

The tun is ancient and hasn't been used.  I put openVPN on here some months/years ago, and it didn't work out.  Guess I never bothered to remove it. Removed now, no change in behavior.  Here's the new ifconfig.

```

br0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.4  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::d607:2828:d728:82d1  prefixlen 64  scopeid 0x20<link>
        ether 0e:8a:7f:b5:d9:c9  txqueuelen 1000  (Ethernet)
        RX packets 74179  bytes 15878954 (15.8 MB)
        RX errors 0  dropped 1063  overruns 0  frame 0
        TX packets 13991  bytes 2474919 (2.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


enp12s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.4  netmask 255.255.255.0  broadcast 192.168.1.255
        ether 0e:8a:7f:b5:d9:c9  txqueuelen 1000  (Ethernet)
        RX packets 76512  bytes 17284412 (17.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 24827  bytes 3283681 (3.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 20599  bytes 3241216 (3.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 20599  bytes 3241216 (3.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


vnet0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 169.254.165.48  netmask 255.255.0.0  broadcast 169.254.255.255
        inet6 fe80::fc54:ff:fede:61b5  prefixlen 64  scopeid 0x20<link>
        inet6 fe80::f7b0:e9a1:6eb1:6097  prefixlen 64  scopeid 0x20<link>
        ether fe:54:00:de:61:b5  txqueuelen 1000  (Ethernet)
        RX packets 787  bytes 76676 (76.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 34269  bytes 4274544 (4.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

The vnet address in ifconfig doesn't make too much sense to me, as the VM reports its address as 192.168.1.5, and my router also reflects that.  I've found while troubleshooting this issue that ifconfig doesn't always report the whole truth.

How do I prevent enp12s0 from getting an IP address?  Since this is the physical link, doesn't it need an address?

EDIT: found your post you mentioned.  The only material difference between yours and mine is setting dhcp6 to false.  I did that and regenerated/applied the netplan.  No change. For the first 5 seconds or so after changing the config I can reach my routers landing page at 192.168.1.1, but as soon as the bridge takes over it becomes unreachable.  I also disabled network manager because I hear it can cause problems with non-standard network configs.

```

master@HomeServer:/etc/netplan$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.4 icmp_seq=1 Destination Host Unreachable
From 192.168.1.4 icmp_seq=2 Destination Host Unreachable
^C
--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, +2 errors, 100% packet loss, time 2007ms
pipe 2
master@HomeServer:/etc/netplan$ ping www.google.com
PING www.google.com (172.217.164.68) 56(84) bytes of data.
64 bytes from atl26s18-in-f4.1e100.net (172.217.164.68): icmp_seq=1 ttl=57 time=9.01 ms
64 bytes from atl26s18-in-f4.1e100.net (172.217.164.68): icmp_seq=2 ttl=57 time=9.23 ms
64 bytes from atl26s18-in-f4.1e100.net (172.217.164.68): icmp_seq=3 ttl=57 time=9.21 ms
^C
--- www.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 9.010/9.147/9.226/0.097 ms

```

---

### Post by Doug S on 2021-06-21
> **crono1412 said:**
> How do I prevent enp12s0 from getting an IP address?  Since this is the physical link, doesn't it need an address?
Good question. It isn't clear to me why it is getting an IP address. I agree with TheFu, it shouldn't. And, no it doesn't need an address, br0 gets the address.

What do you get for example this:

```
doug@s19:~$ brctl show br0
bridge name     bridge id               STP enabled     interfaces
br0             8000.3c7c3f0d9983       no              enp3s0 
```

---

### Post by crono1412 on 2021-06-21
Here it is.

```
brctl showbridge name    bridge id        STP enabled    interfaces
br0        8000.0e8a7fb5d9c9    yes        enp12s0
                            vnet0
```

---

### Post by TheFu on 2021-06-21
> **crono1412 said:**
>  
EDIT: found your post you mentioned.  The only material difference between yours and mine is setting dhcp6 to false.  I did that and regenerated/applied the netplan.  No change. For the first 5 seconds or so after changing the config I can reach my routers landing page at 192.168.1.1, but as soon as the bridge takes over it becomes unreachable.  I also disabled network manager because I hear it can cause problems with non-standard network configs.

In theory, that is correct, but sometimes order matters.

Humor me.  Put that config in (fixed for your NIC and subnet) and see if it works.
I remember something about the renderer being 2nd as important. Yes, it shouldn't matter, but then there is the real world.

---

### Post by crono1412 on 2021-06-22
I removed

```

      parameters:
        stp: true
        forward-delay: 4

```

as that was the only remaining delta. Here's what I have now.

```

master@HomeServer:/etc/netplan$ cat *
network:
  version: 2
  renderer: networkd
  ethernets:
    enp12s0:
      dhcp4: false
      dhcp6: false
  bridges:
    br0:
      interfaces: [enp12s0]
      dhcp4: false
      dhcp6: false
      addresses: [ 192.168.1.4/24 ]
      gateway4: 192.168.1.1
      nameservers:
        addresses: [ 192.168.1.1 ]
      

```

Generate and apply.  No change.

These problem all started after I installed the PiHole, which I have since removed.  I'm thinking that some network config got left behind that are causing this issue on the bridge.  I ran the install for Pihole for both the br0 and the enp12s0. I tried also creating a br1 from scratch, but it exhibited the same behavior exactly.

I also tried to get rid of the IP address on enp12s0 by doing a dhclient -v -r.  This killed internet connection, even though I have set up static IP over the bridge. I was able to restore it by checking the ip routing tables, and deleting the route from enp12s0.

```

master@HomeServer:/etc/netplan$ sudo dhclient -v
[sudo] password for master: 
Internet Systems Consortium DHCP Client 4.4.1
Copyright 2004-2018 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/


Listening on LPF/vnet0/fe:54:00:de:61:b5
Sending on   LPF/vnet0/fe:54:00:de:61:b5
Listening on LPF/br0/0e:8a:7f:b5:d9:c9
Sending on   LPF/br0/0e:8a:7f:b5:d9:c9
Listening on LPF/enp12s0/0e:8a:7f:b5:d9:c9
Sending on   LPF/enp12s0/0e:8a:7f:b5:d9:c9
Sending on   Socket/fallback
DHCPDISCOVER on vnet0 to 255.255.255.255 port 67 interval 3 (xid=0xcbcec77e)
DHCPDISCOVER on br0 to 255.255.255.255 port 67 interval 3 (xid=0x813c6e28)
DHCPDISCOVER on enp12s0 to 255.255.255.255 port 67 interval 3 (xid=0x65217a43)
DHCPOFFER of 192.168.1.4 from 192.168.1.1
DHCPREQUEST for 192.168.1.4 on br0 to 255.255.255.255 port 67 (xid=0x286e3c81)
DHCPOFFER of 192.168.1.4 from 192.168.1.1
DHCPREQUEST for 192.168.1.4 on enp12s0 to 255.255.255.255 port 67 (xid=0x437a2165)
DHCPACK of 192.168.1.4 from 192.168.1.1 (xid=0x813c6e28)
bound to 192.168.1.4 -- renewal in 41377 seconds.
master@HomeServer:/etc/netplan$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.4 icmp_seq=1 Destination Host Unreachable
^C
--- 192.168.1.1 ping statistics ---
2 packets transmitted, 0 received, +1 errors, 100% packet loss, time 1001ms


master@HomeServer:/etc/netplan$ ping www.google.com
PING www.google.com (216.58.193.164) 56(84) bytes of data.
From 192.168.1.4 icmp_seq=1 Destination Host Unreachable
^C
--- www.google.com ping statistics ---
4 packets transmitted, 0 received, +1 errors, 100% packet loss, time 17896ms


master@HomeServer:/etc/netplan$ ip r
default via 192.168.1.1 dev enp12s0 src 192.168.1.4 metric 202 
default via 192.168.1.1 dev br0 src 192.168.1.4 metric 203 
169.254.0.0/16 dev vnet0 scope link src 169.254.165.48 metric 209 
192.168.1.0/24 dev enp12s0 proto dhcp scope link src 192.168.1.4 metric 202 
192.168.1.0/24 dev br0 proto dhcp scope link src 192.168.1.4 metric 203 
master@HomeServer:/etc/netplan$ sudo ip route delete default via 192.168.1.1 dev enp12s0 src 192.168.1.4 metric 202
master@HomeServer:/etc/netplan$ ip r
default via 192.168.1.1 dev br0 src 192.168.1.4 metric 203 
169.254.0.0/16 dev vnet0 scope link src 169.254.165.48 metric 209 
192.168.1.0/24 dev enp12s0 proto dhcp scope link src 192.168.1.4 metric 202 
192.168.1.0/24 dev br0 proto dhcp scope link src 192.168.1.4 metric 203


```

Still can't ping 192.168.1.1 though.

I wonder if there is a way to wipe all possible net configs and restart from scratch without a full install of the OS.

EDIT2: I tried clearing the arp cache. Didn't help.
```

 master@HomeServer:/etc/netplan$ sudo arp -nAddress                  HWtype  HWaddress           Flags Mask            Iface
192.168.1.48                     (incomplete)                              enp12s0
192.168.1.46             ether   b0:e4:d5:eb:47:00   C                     br0
192.168.1.33                     (incomplete)                              enp12s0
192.168.1.46                     (incomplete)                              enp12s0
192.168.1.1              ether   10:0c:6b:59:93:ba   C                     br0
192.168.1.17                     (incomplete)                              enp12s0
192.168.1.6                      (incomplete)                              enp12s0
192.168.1.7                      (incomplete)                              enp12s0
192.168.1.1                      (incomplete)                              enp12s0
192.168.1.2                      (incomplete)                              enp12s0
192.168.1.3                      (incomplete)                              enp12s0
192.168.1.8                      (incomplete)                              enp12s0

```
10:0c:6b:59:93:ba is the MAC of the gateway. I don't know what the MAC on 192.168.1.46 belongs to.

---

### Post by TheFu on 2021-06-22
I don't think any brctl commands are needed.  Neplan config handles all of that, so probably should delete any bridge created using bridge-utils.  That's just a guess. I know I haven't used brctl in at least 8 yrs to create anything. Only use it to check on bridge config, perhaps once every 3 yrs, if there was an issue.  In the olden days, around 2010, this stuff was all new to me.

The .yaml file looks reasonable. Would be helpful to see the current yaml file, the current **ip a** and the current **ip r|column -t** with each attempted modification. Also not if any generate or apply issues are reported.  Might be useful to use the --debug option on both netplan commands too. Maybe something useful will come out?  Who knows.  If any other files in the netplan directory have yaml extensions, those could conflict. May also want to disable any other network management tools completely - like network-manager or wicd or ifupdown stuff.

Because I don't use netplan on my VM hosts, think I mentioned that previously, there isn't much more I can guess to be helpful. Sorry.

My pihole is connected to my normal bridge, as setup years ago.  But my pihole isn't a VM, it is an LXD container. It just seemed like the way to play with an lxd container.
From inside the pihole, it looks like a normal network:
```
pihole:~$ ip r | column -t
default         via  172.22.22.1  dev    eth0    src    172.22.22.80  metric  206
172.22.22.0/24  dev  eth0         proto  kernel  scope  link          src     172.22.22.80  metric  206

pihole:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
6: eth0@if7: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 00:16:3e:d5:71:a5 brd ff:ff:ff:ff:ff:ff link-netnsid 0
    inet 172.22.22.80/24 brd 172.22.22.255 scope global eth0
       valid_lft forever preferred_lft forever
```
lxd containers are treated more like VMs than containers.
From the VM host, it looks like:
```
$ ip a 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: **enp3s0**: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq master br0 state UP group default qlen 1000
    link/ether 0c:9d:92:87:ce:13 brd ff:ff:ff:ff:ff:ff
3: **br0**: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 0c:9d:92:87:ce:13 brd ff:ff:ff:ff:ff:ff
    inet 172.22.22.6/24 brd 172.22.22.255 scope global **br0**
       valid_lft forever preferred_lft forever

$ ip r| column -t
default           via  172.22.22.1  dev    **br0**     onlink
172.22.22.0/24    dev  **br0**          proto  kernel  scope   link  src  172.22.22.6

And the /etc/resolv.conf on the VM host is:
[CODE]nameserver 172.22.22.80
```
[/CODE]

And the bridges on the VM host:
```
$ brctl show br0
bridge name     bridge id               STP enabled     interfaces
**br0**             8000.0c9d9287ce13       no              **enp3s0**
                                                        vethCDK24M
                                                        vnet0
                                                        vnet1
                                                        vnet2
                                                        vnet3
                                                        vnet48
```
I think that's the entire, working, setup. I could post the interfaces file, but don't think that would be too helpful for a netplan need. 

I do have an older physical system that isn't hosting any VMs right now. Suppose I could install netplan and try some stuff out. I need to think on that a bit, since there are some other NICs used on that system for LAN services that shouldn't be touched during the week. It does need to happen at some point before 2023.

---

### Post by crono1412 on 2021-06-22
Yeah, what's really frustrating to me is that everything *should* be working. We've been through all the different ways to configure a bridge.  This server started as like a 12.04(?) installation and I've upgraded it over the years, so I wasn't even using netplan until I wanted to troubleshoot this issue. I've killed the br0 numerous times, and created br1 using netplan to see if its something weird with br0 specifically was going on, but it seems bridges are busted. 

I also don't understand where all my extra "default" routes are coming from on my iptable. I have 3 of them, and 2 of them are br0 related.
```

master@HomeServer:/etc/netplan$ ip r | column -t
default         via  192.168.1.1  dev    br0      proto  static                                        
default         via  192.168.1.1  dev    enp12s0  src    192.168.1.25    metric  202                   
default         via  192.168.1.1  dev    br0      src    192.168.1.4     metric  203                   
169.254.0.0/16  dev  vnet0        scope  link     src    169.254.165.48  metric  209                   
192.168.1.0/24  dev  enp12s0      proto  dhcp     scope  link            src     192.168.1.25  metric  202
192.168.1.0/24  dev  br0          proto  dhcp     scope  link            src     192.168.1.4   metric  203

```

You have way more networks than I, but no entries in your ip route tables.  I wonder why.  Also something keeps recreating entries in the ip route table for me, because I can delete routs and they come back sometime later.

---

### Post by TheFu on 2021-06-22
I removed many of the IPs and route entries to limit confusion.
When I look at the #13 routing table, I'm concerned there is more than 1 default route.  That's a problem. Also, enp12s0 still has an IP and it shouldn't.  Where is that coming from - the ip for enp12s0?  In the ifupdown world, enp12s0 would be set to manual, not dhcp and not static.  Then it would only be referenced in the br0 stanza.  The netplan yaml file does something similar.  I'd guess that is the issue.

---

### Post by crono1412 on 2021-06-22
The only thing I can think of that is supplying the IP is that I had an address reservation in my router config for that Mac. But it shouldn't be assigning the address without a dhcp request from the computer, right?

---

### Post by TheFu on 2021-06-22
> **crono1412 said:**
> The only thing I can think of that is supplying the IP is that I had an address reservation in my router config for that Mac. But it shouldn't be assigning the address without a dhcp request from the computer, right?

I don't know. Easy to test - change the IP the DHCP server give it.  Reserved IPs should never be in the same range as dynamic addresses or static IPs on a subnet.  I only use dhcp reservation for IoT stuff and those aren't allowed on the same network(s) as computers that matter.
Has network-manager been purged, completely?  That would be my guess.

---

### Post by crono1412 on 2021-06-22
Well, it definitely has something to do with enp12s0 getting an IP. I made changes in the router so that it didn't reserve a number for that interface, and changed the static ip to one outside of the dhcp assignment range on the router, and for a blissful 5 minutes everything worked with the bridge. It worked long enough for me to spin up the VMs to make sure that everybody was talking... and then suddenly everything stopped again. Low and behold enp12s0 was getting an IP address, and as soon as it did it broke everything.

When it gets its address, it gets a default IP route entry, and that breaks the internet.  Deleting the default route through enp12s0 restores internet, but intranet connectivity is still broken. And dispite assigning an IP address locally, and ipconfig showing the address we assigned to the br0, the ip route shows it going through a completely different address.

```

master@HomeServer:/etc/netplan$ ifconfig
br0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        **inet 192.168.1.253**  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::6dcd:70c4:486f:1c36  prefixlen 64  scopeid 0x20<link>
        inet6 fe80::e470:7dff:fef9:bf14  prefixlen 64  scopeid 0x20<link>
        ether e6:70:7d:f9:bf:14  txqueuelen 1000  (Ethernet)
        RX packets 56140  bytes 11778155 (11.7 MB)
        RX errors 0  dropped 369  overruns 0  frame 0
        TX packets 14183  bytes 2205434 (2.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


enp12s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.8  netmask 255.255.255.0  broadcast 192.168.1.255
        ether 0e:8a:7f:b5:d9:c9  txqueuelen 1000  (Ethernet)
        RX packets 113161  bytes 41664788 (41.6 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 53744  bytes 7943783 (7.9 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 23062  bytes 4040562 (4.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 23062  bytes 4040562 (4.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


vnet3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 169.254.165.48  netmask 255.255.0.0  broadcast 169.254.255.255
        inet6 fe80::fc54:ff:fede:61b5  prefixlen 64  scopeid 0x20<link>
        inet6 fe80::f7b0:e9a1:6eb1:6097  prefixlen 64  scopeid 0x20<link>
        ether fe:54:00:de:61:b5  txqueuelen 1000  (Ethernet)
        RX packets 1264  bytes 118183 (118.1 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 33182  bytes 4391374 (4.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```
```

master@HomeServer:/etc/netplan$ ip r | column -t
default         via  192.168.1.1  dev    **br0   src    192.168.1.11**    metric  206                   
169.254.0.0/16  dev  vnet3        scope  link  src    169.254.165.48  metric  208                   
192.168.1.0/24  dev  enp12s0      proto  dhcp  scope  link            src     192.168.1.8   metric  202
192.168.1.0/24  dev  br0          proto  dhcp  scope  link            src     192.168.1.11  metric  206

```


The router has entries for both 192.168.1.8 (enp12s0) and 192.168.1.253 (br0).  192.168.1.11, from the IP route, is one of my nest devices.

Here's my DHCPCD log for one of my resets and retries:
```

Jun 22 15:38:04 HomeServer systemd-networkd[17690]: br0: DHCPv6 lease lost
Jun 22 15:38:04 HomeServer dhcpcd[3794]: br0: pid 1 deleted IP address 192.168.1.11/24
Jun 22 15:38:04 HomeServer dhcpcd[3794]: enp12s0: adding default route via 192.168.1.1
Jun 22 15:38:04 HomeServer dhcpcd[3794]: br0: deleting route to 192.168.1.0/24
Jun 22 15:38:04 HomeServer dhcpcd[3794]: br0: deleting default route via 192.168.1.1
Jun 22 15:38:04 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.2/24
Jun 22 15:38:04 HomeServer dhcpcd[3794]: enp12s0: pid 1 deleted IP address 192.168.1.8/24
Jun 22 15:38:04 HomeServer dhcpcd[3794]: vnet3: adding default route
Jun 22 15:38:04 HomeServer dhcpcd[3794]: enp12s0: deleting route to 192.168.1.0/24
Jun 22 15:38:04 HomeServer dhcpcd[3794]: enp12s0: deleting default route via 192.168.1.1
Jun 22 15:38:04 HomeServer dhcpcd[3794]: enp12s0: probing address 192.168.1.25/24
Jun 22 15:38:04 HomeServer dhcpcd[3794]: br0: hardware address 10:0c:6b:58:c0:2a claims 192.168.1.2
Jun 22 15:38:04 HomeServer dhcpcd[3794]: enp12s0: hardware address b4:2e:99:cd:b1:d6 claims 192.168.1.25
Jun 22 15:38:05 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:05 HomeServer dhcpcd[3794]: enp12s0: soliciting a DHCP lease
Jun 22 15:38:06 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:06 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:06 HomeServer dhcpcd[3794]: enp12s0: offered 192.168.1.8 from 192.168.1.1
Jun 22 15:38:06 HomeServer dhcpcd[3794]: enp12s0: ignoring offer of 192.168.1.8 from 192.168.1.1
Jun 22 15:38:06 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:06 HomeServer dhcpcd[3794]: enp12s0: probing address 192.168.1.8/24
Jun 22 15:38:06 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:07 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:07 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:07 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:08 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:08 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:09 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:09 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:09 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:09 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:09 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:10 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:10 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:10 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:10 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:11 HomeServer dhcpcd[3794]: enp12s0: using static address 192.168.1.8/24
Jun 22 15:38:11 HomeServer dhcpcd[3794]: enp12s0: adding route to 192.168.1.0/24
Jun 22 15:38:11 HomeServer dhcpcd[3794]: enp12s0: adding default route via 192.168.1.1
Jun 22 15:38:11 HomeServer dhcpcd[3794]: vnet3: deleting default route
Jun 22 15:38:12 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:13 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:13 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:13 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:13 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:13 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:14 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:14 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:14 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:15 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:15 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:16 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:16 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:16 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:16 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:16 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:17 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:18 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:18 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:18 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:18 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:19 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:19 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:19 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:19 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:20 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:21 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:21 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:21 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:21 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:21 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:22 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:22 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:22 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:22 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:22 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:23 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:23 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:23 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:23 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:25 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:26 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:26 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:26 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:26 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:27 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:28 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:28 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:28 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:28 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:28 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:29 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:29 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:29 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:30 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:30 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:31 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:31 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:31 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:31 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:31 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:32 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:32 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:32 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:32 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:33 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:34 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:34 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:34 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:34 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:34 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:35 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:35 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:35 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:35 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:36 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:37 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:37 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:37 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:37 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:37 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:38 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:38 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:38 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:38 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:39 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:40 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:40 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:40 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:40 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:40 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:41 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:41 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:41 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:41 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:42 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:43 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:43 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:43 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:43 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:43 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:44 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:45 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:45 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:45 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:45 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:46 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:46 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:46 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:46 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:46 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:48 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:48 HomeServer dhcpcd[3794]: br0: offered 192.168.1.22 from 192.168.1.1
Jun 22 15:38:48 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.22 from 192.168.1.1
Jun 22 15:38:48 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.22/24
Jun 22 15:38:48 HomeServer dhcpcd[3794]: br0: hardware address 00:07:a6:19:b4:6c claims 192.168.1.22
Jun 22 15:38:49 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:49 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:49 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:50 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:50 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:51 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:51 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:51 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:51 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:51 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:52 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:52 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:52 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:52 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:52 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:53 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:53 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:53 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:53 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:54 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:55 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:55 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:55 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:55 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:55 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:56 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:56 HomeServer dhcpcd[3794]: br0: offered 192.168.1.26 from 192.168.1.1
Jun 22 15:38:56 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.26 from 192.168.1.1
Jun 22 15:38:56 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.26/24
Jun 22 15:38:57 HomeServer dhcpcd[3794]: br0: hardware address 54:60:09:f3:2c:ba claims 192.168.1.26
Jun 22 15:38:58 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:38:58 HomeServer dhcpcd[3794]: br0: offered 192.168.1.22 from 192.168.1.1
Jun 22 15:38:58 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.22 from 192.168.1.1
Jun 22 15:38:58 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.22/24
Jun 22 15:38:58 HomeServer dhcpcd[3794]: br0: hardware address 18:b4:30:cc:d9:ea claims 192.168.1.22
Jun 22 15:38:59 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:39:00 HomeServer dhcpcd[3794]: br0: offered 192.168.1.30 from 192.168.1.1
Jun 22 15:39:00 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.30 from 192.168.1.1
Jun 22 15:39:00 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.30/24
Jun 22 15:39:02 HomeServer dhcpcd[3794]: br0: hardware address 30:59:b7:5c:3d:fa claims 192.168.1.30
Jun 22 15:39:03 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:39:03 HomeServer dhcpcd[3794]: br0: offered 192.168.1.30 from 192.168.1.1
Jun 22 15:39:03 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.30 from 192.168.1.1
Jun 22 15:39:03 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.30/24
Jun 22 15:39:05 HomeServer dhcpcd[3794]: br0: hardware address 30:59:b7:5c:3d:fa claims 192.168.1.30
Jun 22 15:39:06 HomeServer dhcpcd[3794]: enp12s0: pid 1 deleted IP address 192.168.1.8/24
Jun 22 15:39:06 HomeServer dhcpcd[3794]: vnet3: adding default route
Jun 22 15:39:06 HomeServer dhcpcd[3794]: enp12s0: deleting route to 192.168.1.0/24
Jun 22 15:39:06 HomeServer dhcpcd[3794]: enp12s0: deleting default route via 192.168.1.1
Jun 22 15:39:06 HomeServer dhcpcd[3794]: enp12s0: probing address 192.168.1.25/24
Jun 22 15:39:06 HomeServer dhcpcd[3794]: enp12s0: hardware address b4:2e:99:cd:b1:d6 claims 192.168.1.25
Jun 22 15:39:06 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:39:06 HomeServer dhcpcd[3794]: br0: offered 192.168.1.30 from 192.168.1.1
Jun 22 15:39:06 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.30 from 192.168.1.1
Jun 22 15:39:06 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.30/24
Jun 22 15:39:07 HomeServer dhcpcd[3794]: enp12s0: soliciting a DHCP lease
Jun 22 15:39:07 HomeServer dhcpcd[3794]: enp12s0: offered 192.168.1.8 from 192.168.1.1
Jun 22 15:39:07 HomeServer dhcpcd[3794]: enp12s0: ignoring offer of 192.168.1.8 from 192.168.1.1
Jun 22 15:39:07 HomeServer dhcpcd[3794]: enp12s0: probing address 192.168.1.8/24
Jun 22 15:39:08 HomeServer dhcpcd[3794]: br0: hardware address 30:59:b7:5c:3d:fa claims 192.168.1.30
Jun 22 15:39:09 HomeServer dhcpcd[3794]: br0: soliciting a DHCP lease
Jun 22 15:39:10 HomeServer dhcpcd[3794]: br0: offered 192.168.1.30 from 192.168.1.1
Jun 22 15:39:10 HomeServer dhcpcd[3794]: br0: ignoring offer of 192.168.1.30 from 192.168.1.1
Jun 22 15:39:10 HomeServer dhcpcd[3794]: message repeated 2 times: [ br0: ignoring offer of 192.168.1.30 from 192.168.1.1]
Jun 22 15:39:10 HomeServer dhcpcd[3794]: br0: probing address 192.168.1.30/24
Jun 22 15:39:12 HomeServer dhcpcd[3794]: enp12s0: using static address 192.168.1.8/24
Jun 22 15:39:12 HomeServer dhcpcd[3794]: enp12s0: adding route to 192.168.1.0/24
Jun 22 15:39:12 HomeServer dhcpcd[3794]: enp12s0: adding default route via 192.168.1.1
Jun 22 15:39:12 HomeServer dhcpcd[3794]: vnet3: deleting default route
Jun 22 15:39:15 HomeServer dhcpcd[3794]: br0: using static address 192.168.1.30/24
Jun 22 15:39:15 HomeServer dhcpcd[3794]: br0: adding route to 192.168.1.0/24
Jun 22 15:39:15 HomeServer dhcpcd[3794]: br0: adding default route via 192.168.1.1
Jun 22 15:39:17 HomeServer dhcpcd[3794]: br0: hardware address 30:59:b7:5c:3d:fa claims 192.168.1.30
Jun 22 15:41:24 HomeServer dhcpcd[3794]: enp12s0: deleted default route via 192.168.1.1

```

The interfaces are actively refusing the IP address offered by the router, and then decide to take it anyway.  Even though we have assigned an IP to the br0, and enp12s0 shouldn't be getting one. I'm going to try and disable dhcpcd and reboot and see if this magically solves our problems or not.

EDIT: It would appear that disabling dhcpcd has solved the problem.  I'm not sure its the right solution, considering that something was calling dhcpcd to get ip addresses, and it is still likely doing so in a futile attempt to thwart me, but for now the problem has been worked around.

Thanks TheFu for your assistance in helping me track down the issue.

---

### Post by TheFu on 2021-06-22
DHCP is evil. Don't use it on servers.

If this were a pure server (no GUI), then you wouldn't have these issues.  On a desktop install, there are all sorts of failures with 20 different systems trying to manage IPs, DNS, mDNS, just a bunch of crap.

All this time, I assumed you'd put the pihole into a VM. Is that not the situation?  pihole is a self-contained solution. I don't think it wants to be installed on a shared system.  I keep dissimilar network services separate and once I setup a network service, then all clients start using it, not their own less-optimal, solution.  If I'm running a DNS server, then none of my systems on the LAN will run a DNS server, caching server or get dns answers from anywhere else.  My WAN router - asks the pihole for DNS answers - so does my LAN router.

Oh and avahi is something that gets in the way almost always when we start running LAN DNS.  I've always disabled avahi (zeroconf) on all my systems, then only re-enabled it on the 1-2 systems where it is actually helpful.

---

### Post by crono1412 on 2021-06-22
Pihole is just another network service. More elegant and skilled people put stuff like that in dockers, but I have no clue how to use docker. In any case, I had removed pihole from this server before starting to troubleshoot this issue (though I may put it back, just so all critical services are handled by the same machine). It's currently on a spare pi4 I'm using for weekly backups.

---

