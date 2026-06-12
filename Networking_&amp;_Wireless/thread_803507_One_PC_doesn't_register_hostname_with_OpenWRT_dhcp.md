---
title: "One PC doesn't register hostname with OpenWRT dhcp"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by jeffk on 2008-05-22
I have an OpenWRT WRT54GL serving DHCP with DNS to Ubuntu 8.04 PCs, and one Ubuntu 8.04 server on a static IP.

One of the PCs gets a DHCP lease, but does not send (or the OpenWRT does not read) it's hostname.

AFAICT, this PC is configured identically to the others which work.

```
OpenWRT # cat /tmp/dhcp.leases | head -n 1
1211494537 00:32:BA:28:4b:a1 192.168.10.185 * *
```
```
acme@acme-pc:~$ hostname -f
acme-pc.lan

acme@acme-pc:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       acme-pc.lan     acme-pc
192.168.10.99   server1

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

acme@acme-pc:~$ cat /etc/hostname 
acme-pc

acme@acme-pc:~$ cat /etc/resolv.conf 
search lan
nameserver 192.168.10.1

acme@acme-pc:~$ cat /etc/dhcp3/dhclient
cat: /etc/dhcp3/dhclient: No such file or directory

acme@acme-pc:~$ cat /etc/dhcp3/dhclient.conf
request subnet-mask, broadcast-address, time-offset, routers, domain-name,    domain-name-servers, host-name, ntp-servers;

acme@acme-pc:~$ cat /etc/avahi/avahi-daemon.conf 
# $Id: avahi-daemon.conf 1463 2007-05-08 22:50:58Z lennart $
#
# This file is part of avahi.
# 
# avahi is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as
# published by the Free Software Foundation; either version 2 of the
# License, or (at your option) any later version.
#
# avahi is distributed in the hope that it will be useful, but WITHOUT
# ANY WARRANTY; without even the implied warranty of MERCHANTABILITY
# or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public
# License for more details.
#
# You should have received a copy of the GNU Lesser General Public
# License along with avahi; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

# See avahi-daemon.conf(5) for more information on this configuration
# file!

[server]
#host-name=foo
#domain-name=local
#browse-domains=0pointer.de, zeroconf.org
use-ipv4=yes
use-ipv6=no
#check-response-ttl=no
#use-iff-running=no
#enable-dbus=yes
#disallow-other-stacks=no
#allow-point-to-point=no

[wide-area]
enable-wide-area=yes

[publish]
#disable-publishing=no
#disable-user-service-publishing=no
#add-service-cookie=no
#publish-addresses=yes
#publish-hinfo=yes
#publish-workstation=yes
#publish-domain=yes
#publish-dns-servers=192.168.50.1, 192.168.50.2
#publish-resolv-conf-dns-servers=yes
#publish-aaaa-on-ipv4=yes
#publish-a-on-ipv6=no

[reflector]
#enable-reflector=no
#reflect-ipv=no

[rlimits]
#rlimit-as=
rlimit-core=0
rlimit-data=4194304
rlimit-fsize=0
rlimit-nofile=30
rlimit-stack=4194304
rlimit-nproc=3

acme@acme-pc:~$ cat /etc/avahi/hosts
(all comment lines)
```

---

