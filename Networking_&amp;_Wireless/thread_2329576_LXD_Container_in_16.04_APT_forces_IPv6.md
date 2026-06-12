---
title: "LXD Container in 16.04: APT forces IPv6?"
date: 2016-07-03
forum: Networking &amp; Wireless
---

### Post by jarush on 2016-07-03
I installed a new 16.04 server and spun out a couple of 16.04 containers with LXD.  The host server works fine with APT getting IPv4 addresses from DNS.  Both containers are getting back IPv6 addresses.  I've got a bridge set up on the host and set that bridge to be the default bridge for containers, so both containers are getting DHCP from the same source as the host.  No idea what is going on here.

This is what a vanilla container shows:
Err:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease
  Could not connect to fe80::1%eth0:13128 (fe80::1%eth0), connection timed out



I've tried disabling IPv6:
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

But all that does is get me address family not supported errors:
Err:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial Release
  Something wicked happened resolving 'fe80::1%eth0:13128' (-9 - Address family for hostname not supported)

Oddly the container interfaces on the host show as having an ipv6 address and no ipv4:
vethSQ3Y4C Link encap:Ethernet  HWaddr fe:ba:78:7c:e6:a0
          inet6 addr: fe80::fcba:78ff:fe7c:e6a0/64 Scope:Link




Yet lxc list clearly shows it has having an IPv4 address and no IPv6:
 NAME   |  STATE  |         IPV4          | IPV6 |    TYPE    | SNAPSHOTS |
+---------+---------+-----------------------+------+------------+-----------+
| bastion | RUNNING | 10.255.251.167 (eth0) |      | PERSISTENT | 0         |

The interface in the container shows both ipv4 and 6:
eth0      Link encap:Ethernet  HWaddr 00:16:3e:45:bb:d9
          inet addr:10.255.248.86  Bcast:10.255.251.255  Mask:255.255.252.0
          inet6 addr: fe80::216:3eff:fe45:bbd9/64 Scope:Link

---

### Post by 3-joh8-x on 2016-07-05
Yes, this is a killer. I tried using different combinations of bridges (br0, lxdbr0) to no avail. I also tried the changes to gai.conf and various Acquire::ForceIPv4=true combinations.
I even went so far as to remove IPv6 entirely, but that only made things worse. For what it's worth, KVM and VirtualBox guests work fine using the same bridge.
[COLOR=#242729][FONT=Consolas][FONT=arial][/FONT]
[/FONT][/COLOR]

---

### Post by 3-joh8-x on 2016-07-05
I installed Ubuntu 15.10 in a KVM instance running on a Ubuntu 16.04 host just to prove this is a new failure. Apt works fine in that environment. A Ubuntu 16.04 instance on the same machine fails as described above.

---

### Post by 0-don on 2016-07-15
Problem is on the host machine, not the container.

You have to to disable lxdbr0, edit /etc/default/lxd-bridge
Then change the variables to the following:
USE_LXD_BRIDGE="false"
LXD_BRIDGE=""

Make sure you have "parent" set to br0 in the default profile. (lxc profile edit default)

To create br0 (if you haven't already), edit /etc/network/interfaces
Then set something like this:
auto eth0
iface eth0 inet manual


auto br0
iface br0 inet static
  bridge_ports eth0
  bridge_stp off
  bridge_fd 0
  bridge_maxwait 0
  address 192.168.0.10
  gateway 192.168.0.1
  network 192.168.0.0
  netmask 255.255.255.0
  broadcast 192.168.0.255
  dns-nameservers 8.8.8.8
  dns-search lan.yourdomain.com



When everything is set correctly, just reboot and then networking will work properly in the container.

Good luck.

---

### Post by rokclimb15 on 2016-10-20
If you've applied a non-default profile to the containers to facilitate the other bridge interface, this is necessary since the proxy address lives on lxdbr0 which isn't accessible.

My profile is called public-net, which uses br0 instead of lxdbr0

lxc profile set public-net environment.http_proxy
lxc profile set public-net user.network_mode

---

