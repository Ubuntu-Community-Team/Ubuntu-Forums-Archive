---
title: "VM can't ping domain but can ping IP address"
date: 2018-10-14
forum: Networking &amp; Wireless
---

### Post by satimis on 2018-10-14
Hi all,

Host - Ubuntu 16.04
VM - Ubuntu 18.04
VirtualBox

VM can't ping domain but can ping IP address

$ ls -al /etc/resolv.conf ```

lrwxrwxrwx 1 root root 37 Oct 13 13:54 /etc/resolv.conf -> /run/systemd/resolve/stub-resolv.conf

```

$ cat /run/systemd/resolve/stub-resolv.conf ```

# This file is managed by man:systemd-resolved(8). Do not edit.
#
# This is a dynamic resolv.conf file for connecting local clients to the
# internal DNS stub resolver of systemd-resolved. This file lists all
# configured search domains.
#
# Run "systemd-resolve --status" to see details about the uplink DNS servers
# currently in use.
#
# Third party programs must not access this file directly, but only through the
# symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,
# replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.

nameserver 127.0.0.53

```

$ cat /etc/network/interfaces```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
dns-nameservers 218.xxx.xx.xxx 219.xx.xx.xx

# The primary network interface
auto enp0s3
iface enp0s3 inet manual

# add bridge ports
auto br0
iface br0 inet static
        address         192.168.0.89
        network         192.168.0.0
        netmask         255.255.255.0
        broadcast       192.168.0.255
        gateway         192.168.0.1
        bridge_ports    enp0s3
        bridge_fd       9
        bridge_hello    2
        bridge_maxage   12
        bridge_stop     off

```

Several months before I encountered the same problem.  Unfortunately I forgot the solution.

Please help.  Thanks

Regards
satimis

---

### Post by SeijiSensei on 2018-10-14
What do you mean by "ping domain?"  Something like "ping ubuntuforums.org"?  That won't work unless you have a A record for the domain name in the DNS records for that domain like this:

```

@               IN      SOA     example.com.    admin.example.com. (
                                2017011902 ; serial
                                43200      ; refresh (12 hours)
                                3600       ; retry (1 hour)
                                172800     ; expire (2 days)
                                43200      ; minimum (12 hours)
                                )

                IN      A       10.10.10.10

                IN      NS     ns.example.com.
                IN      NS     ns2.example.com

[etc.]

```

---

### Post by satimis on 2018-10-14
> **SeijiSensei said:**
> What do you mean by "ping domain?"  Something like "ping ubuntuforums.org"?  That won't work unless you have a A record for the domain name in the DNS records for that domain like this:

```

@               IN      SOA     example.com.    admin.example.com. (
                                2017011902 ; serial
                                43200      ; refresh (12 hours)
                                3600       ; retry (1 hour)
                                172800     ; expire (2 days)
                                43200      ; minimum (12 hours)
                                )

                IN      A       10.10.10.10

                IN      NS     ns.example.com.
                IN      NS     ns2.example.com

[etc.]

```

On Terminal

$ ping yahoo.com```

ping: yahoo.com: Name or service not known

```

$ ping [www.yahoo.com](www.yahoo.com)```

ping: www.yahoo.com: Name or service not known

```


$ ping 72.30.35.9```

PING 72.30.35.9 (72.30.35.9) 56(84) bytes of data.
64 bytes from 72.30.35.9: icmp_seq=1 ttl=52 time=228 ms
64 bytes from 72.30.35.9: icmp_seq=2 ttl=52 time=228 ms
64 bytes from 72.30.35.9: icmp_seq=3 ttl=52 time=228 ms
64 bytes from 72.30.35.9: icmp_seq=4 ttl=52 time=228 ms
64 bytes from 72.30.35.9: icmp_seq=5 ttl=52 time=228 ms
64 bytes from 72.30.35.9: icmp_seq=6 ttl=52 time=228 ms
.....

```

Neither I can browse Internet on browser.

Regards
satimis

---

### Post by SeijiSensei on 2018-10-14
Sounds like your VMs DNS is broken.  Does it point to the same name servers the VM host uses?  Are you using NAT or bridged networking?  Does it work if you use NAT?

I don't know why you have a bridged adapter in the VM.  I never use bridging for anything other than bridged-mode networking in VB where specifying a bridged adapter is not required.   On my host machine, ifconfig shows the adapter name as "wlxec086b1841a7:"  In the VM with bridging, it appears as "enp0s3".

---

### Post by satimis on 2018-10-14
> **SeijiSensei said:**
> Sounds like your VMs DNS is broken.  Does it point to the same name servers the VM host uses?  Are you using NAT or bridged networking?  Does it work if you use NAT?

I don't know why you have a bridged adapter in the VM.  I never use bridging for anything other than bridged-mode networking in VB where specifying a bridged adapter is not required.
Bridged Adapter.

Same configuration works on Ubuntu 16.04 VMs, newly installed.  I have the problem fixed before.  Old Ubuntu 18.04 VM works without problem except newly installed Ubuntu 18.04 VM

satimis

---

### Post by satimis on 2018-10-16
Hi all,

Problem was solved as follow;

$ cat /etc/network/interfaces```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# The primary network interface
auto enp0s3
iface enp0s3 inet manual

# add bridge ports
auto br0
iface br0 inet static
        address         192.168.0.91
        network         192.168.0.0
        netmask         255.255.255.0
        broadcast       192.168.0.255
        gateway         192.168.0.1
        bridge_ports    enp0s3
        bridge_fd       9
        bridge_hello    2
        bridge_maxage   12
        bridge_stop     off

```

Removed the symlink
$ ls -al /etc/resolv.conf```

-rw-r--r-- 1 root root 68 Oct 15 12:46 /etc/resolv.conf

```

Created a new /etc/resolv.conf and added nameservers on it as follow;
$ cat /etc/resolv.conf```
 
# Generated by NetworkManager
nameserver 218.xxx.xx.xxx
nameserver 219.xxx.xxx.xx

```

Then ran;
$ sudo chattr +i /etc/resolv.conf

$ lsattr /etc/resolv.conf```

----i------------- /etc/resolv.conf

```

Rebooted VM.  On browser I can connect Internet.  /etc/resolv.conf has not been reset on reboot.

But according to my recollection this is NOT the solution used by me previously.
============================================================

All previous installed Ubuntu 18.04 VMs retain;

$ ls -al /etc/resolv.conf```
 
lrwxrwxrwx 1 root root 39 Apr 30 23:26 /etc/resolv.conf -> ../run/systemd/resolve/stub-resolv.conf

```

$ cat /run/systemd/resolve/stub-resolv.conf```
 
# This file is managed by man:systemd-resolved(8). Do not edit.
#
# This is a dynamic resolv.conf file for connecting local clients to the
# internal DNS stub resolver of systemd-resolved. This file lists all
# configured search domains.
#
# Run "systemd-resolve --status" to see details about the uplink DNS servers
# currently in use.
#
# Third party programs must not access this file directly, but only through the
# symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,
# replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.

nameserver 127.0.0.53

```


During testing I found following interesting problem;

Retained symlink```

/etc/resolv.conf -> ../run/systemd/resolve/stub-resolv.conf

```

Changed /etc/network/interfaces as follows;```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
   nameservers:
         addresses: [218.xxx.xx.xxx,219.xxx.xxx.xx]

# The primary network interface
auto enp0s3
iface enp0s3 inet manual

# add bridge ports
auto br0
iface br0 inet static
        address         192.168.0.91
        network         192.168.0.0
        netmask         255.255.255.0
        broadcast       192.168.0.255
        gateway         192.168.0.1
        bridge_ports    enp0s3
        bridge_fd       9
        bridge_hello    2
        bridge_maxage   12
        bridge_stop     off

```

Rebooted PC.

I can connect Internet on browser but the static IP was not "192.168.0.91".

It became "192.168.0.136".  I don't know WHY?


Remark:
======
I encountered some problems on running Ubuntu 18.04 apart from slow booting.

This is a quite fast PC;
CPU - AMD 8-core
RAM - 32G
HD - 2TB SSD (OS and VMs are running on it)
FTTH connection - 1000M up/down

I still retain running Ubuntu 16.04 desktop on my PCs as host

Regards
satimis

---

