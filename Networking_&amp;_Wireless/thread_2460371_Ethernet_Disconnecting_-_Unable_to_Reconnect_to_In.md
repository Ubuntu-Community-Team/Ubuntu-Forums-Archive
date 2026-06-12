---
title: "Ethernet Disconnecting - Unable to Reconnect to Internet"
date: 2021-04-08
forum: Networking &amp; Wireless
---

### Post by jweese1974 on 2021-04-08
[COLOR=#242729][FONT=Arial]I'm not sure what's going on or what happened; I run a machine headless Ubuntu 20.04.2 LTS, it performed an update sometime overnight and when I logged in it prompted me that it needed a reboot - so I did, however, it didn't appear to come back up.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]After attaching a monitor to it I discovered it was running but the network interface was none functional. Not even appearing actually, like it was just deleted or removed. I'll try to share as much information here - but I'm just not sure what could be wrong and I honestly don't know where else to look.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]After trying everything below, I still have no internet connection - and what's worse, after a reboot the only way to get an IP address on my LAN to allow an SSH is by using:[/FONT][/COLOR]
```
$ sudo ip link set enp3s0 down
$ sudo ip link set enp3s0 up
$ sudo ip addr add 192.168.1.150/24 dev enp3s0

```[COLOR=#242729][FONT=Arial]**$ sudo lshw -class network**[/FONT][/COLOR]
```
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 0c
       serial: 2c:56:dc:97:80:9f
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.8.0-48-generic duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=192.168.1.150 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:18 ioport:e000(size=256) memory:fea00000-fea00fff memory:f0800000-f0803fff

```[COLOR=#242729][FONT=Arial]**$ sudo nano /etc/netplan/netcfg.yaml**[/FONT][/COLOR]
```
network:
  version: 2
  renderer: networkd
  ethernets:
    enp3s0:
      dhcp4: no
      addresses:
        - 192.168.1.150/24
      gateway4: 192.168.1.1
      nameservers:
          addresses: [8.8.8.8, 1.1.1.1]

```[COLOR=#242729][FONT=Arial]After a reboot, the above netplan configuration remains, however, additional spacing is being added to some of the lines - causing it to fail.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]**$ ip a**[/FONT][/COLOR]
```
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 2c:56:dc:97:80:9f brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.150/24 scope global enp3s0
       valid_lft forever preferred_lft forever
    inet6 2001:1970:4a26:8100:2e56:dcff:fe97:809f/64 scope global dynamic mngtmpaddr 
       valid_lft 86140sec preferred_lft 14140sec

```[COLOR=#242729][FONT=Arial]**$ ip route show**[/FONT][/COLOR]
```
default via 192.168.1.1 dev enp3s0 
172.17.0.0/16 dev docker0 proto kernel scope link src 172.17.0.1 linkdown 
172.18.0.0/16 dev br-5c71e5479641 proto kernel scope link src 172.18.0.1 
192.168.1.0/24 dev enp3s0 proto kernel scope link src 192.168.1.150

```[COLOR=#242729][FONT=Arial]*I am only able to get the default via 192.168.1.1 dev enp3s0 portion to appear after running **$ sudo ip route add default via 192.168.1.1***[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]**$ sudo netplan --debug try**[/FONT][/COLOR]
```
DEBUG:enp3s0 not found in {}
DEBUG:Merged config:
network:
  ethernets:
    enp3s0:
      addresses:
      - 192.168.1.150/24
      dhcp4: false
      gateway4: 192.168.1.1
      nameservers:
        addresses:
        - 8.8.8.8
        - 1.1.1.1
  renderer: networkd
  version: 2

DEBUG:New interfaces: set()
** (generate:53716): DEBUG: 22:58:01.445: Processing input file /etc/netplan/netcfg.yaml..
** (generate:53716): DEBUG: 22:58:01.445: starting new processing pass
** (generate:53716): DEBUG: 22:58:01.446: We have some netdefs, pass them through a final round of validation
** (generate:53716): DEBUG: 22:58:01.446: enp3s0: setting default backend to 1
** (generate:53716): DEBUG: 22:58:01.446: Configuration is valid
** (generate:53716): DEBUG: 22:58:01.446: Generating output files..

An error occurred: the configuration could not be generated

Reverting.
DEBUG:netplan generated networkd configuration changed, restarting networkd
DEBUG:enp3s0 not found in {}
DEBUG:Merged config:
network:
  ethernets:
    enp3s0:
      addresses:
      - 192.168.1.150/24
      dhcp4: false
      gateway4: 192.168.1.1
      nameservers:
        addresses:
        - 8.8.8.8
        - 1.1.1.1
  renderer: networkd
  version: 2

DEBUG:no netplan generated NM configuration exists
DEBUG:enp3s0 not found in {}
DEBUG:Merged config:
network:
  ethernets:
    enp3s0:
      addresses:
      - 192.168.1.150/24
      dhcp4: false
      gateway4: 192.168.1.1
      nameservers:
        addresses:
        - 8.8.8.8
        - 1.1.1.1
  renderer: networkd
  version: 2

DEBUG:Link changes: {}
DEBUG:netplan triggering .link rules for lo
DEBUG:netplan triggering .link rules for enp3s0
DEBUG:netplan triggering .link rules for br-5c71e5479641
DEBUG:netplan triggering .link rules for docker0
DEBUG:netplan triggering .link rules for vethf90fcb2
DEBUG:netplan triggering .link rules for veth71540be
DEBUG:netplan triggering .link rules for veth18e90b7
DEBUG:netplan triggering .link rules for vetheb58aaa
DEBUG:netplan triggering .link rules for veth728e8e9
DEBUG:netplan triggering .link rules for veth96def70
DEBUG:netplan triggering .link rules for vetha4b92ad
DEBUG:netplan triggering .link rules for vethd43e21c
DEBUG:netplan triggering .link rules for vethb777853
DEBUG:netplan triggering .link rules for veth2b054d4
DEBUG:netplan triggering .link rules for veth8f6354f
DEBUG:netplan triggering .link rules for vethc69182e
DEBUG:netplan triggering .link rules for veth9e52006
DEBUG:netplan triggering .link rules for veth9b90b02
DEBUG:netplan triggering .link rules for veth3f22dda
DEBUG:netplan triggering .link rules for vethc39e6d3
DEBUG:netplan triggering .link rules for vetha38ae56
DEBUG:netplan triggering .link rules for vethf68a144
DEBUG:enp3s0 not found in {}
DEBUG:Merged config:
network:
  ethernets:
    enp3s0:
      addresses:
      - 192.168.1.150/24
      dhcp4: false
      gateway4: 192.168.1.1
      nameservers:
        addresses:
        - 8.8.8.8
        - 1.1.1.1
  renderer: networkd
  version: 2

```[COLOR=#242729][FONT=Arial]This is about all the information I have. I'm just not sure what went wrong, where, how, when.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Any help is greatly appreciated. Thanks![/FONT][/COLOR]

---

### Post by ActionParsnip on 2021-04-08
If this is a home PC, have you tried rebooting your router?

---

### Post by jweese1974 on 2021-04-08
From Ubuntu StackExchange:

[I][COLOR=#242729][FONT=Arial]Have the same problem, network offline after an update. Ubuntu 20.0x[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Found bug listing online: [https://bugs.launchpad.net/netplan/+bug/1922898](https://bugs.launchpad.net/netplan/+bug/1922898)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Here is how I was able to fix my ubuntu 20.x servers![/FONT][/COLOR]
[/I]
[LIST=1]
[*]*Download latest netplan.io_0.102*
[/LIST]

[LIST]
[*]*$ cd /tmp*
[*]*$ wget [http://security.ubuntu.com/ubuntu/pool/main/n/netplan.io/netplan.io_0.102-0ubuntu1~20.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/n/netplan.io/netplan.io_0.102-0ubuntu1~20.04.1_amd64.deb)*
[/LIST]

[LIST=1]
[*]*as root*
[/LIST]

[LIST]
[*]*$ sudo dpkg -i netplan.io_0.102-0ubuntu1~20.04.1_amd64.deb*
[/LIST]

[LIST=1]
[*]*confirm both netplan and libnetplan are in sync*
[/LIST]

[LIST]
[*]*[FONT=inherit]$ sudo dpkg -l |grep netpl[/FONT]*
[*][I][FONT=inherit]libnetplan0:amd64 0.102-0ubuntu1~20.04.1
amd64 YAML network configuration abstraction runtime library[/FONT]
[FONT=inherit]netplan.io 0.102-0ubuntu1~20.04.1
amd64 YAML network configuration abstraction for various backends[/FONT][/I]
[/LIST]

[LIST=1]
[*]*reboot*
[/LIST]
[FONT=inherit]
This worked perfectly.[/FONT]

---

### Post by markthegoose on 2021-04-09
Saved me a rebuild - thanks for posting

---

