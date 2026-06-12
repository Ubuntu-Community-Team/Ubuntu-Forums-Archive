---
title: "ping as root doesn't work with host name, but with ip"
date: 2016-01-08
forum: Networking &amp; Wireless
---

### Post by yvess on 2016-01-08
Hi

I have a really strange ping problem, after an upgrade from 12.04. to 14.04.
I can't ping with the hostname but with the ip it works. I don't have any other dns problems with other services or programs.
I works as normal user, but not as root.
As root user host and dig can resolve the dnsname to an ip. 
busybox ping also works with the hostname.

I have also another server with almost the same installation were it works. This are both kvm linux hosts.

```

root@myhost:~# ping ubuntu.com
ping: unknown host ubuntu.com


root@myhost:~# host ubuntu.com
ubuntu.com has address 91.189.94.40
ubuntu.com mail is handled by 10 mx.canonical.com.


root@myhost:~# ping 91.189.94.40 -c 1
PING 91.189.94.40 (91.189.94.40) 56(84) bytes of data.
64 bytes from 91.189.94.40: icmp_seq=1 ttl=53 time=16.1 ms


root@myhost:~# busybox ping ubuntu.com -c 1
PING ubuntu.com (91.189.94.40): 56 data bytes
64 bytes from 91.189.94.40: seq=0 ttl=53 time=16.189 ms


user@myhost:~$ ping ubuntu.com -c 1
PING ubuntu.com (91.189.94.40) 56(84) bytes of data.
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=1 ttl=53 time=16.1 ms


root@myhost:~# cat /etc/nsswitch.conf
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.


passwd:         compat
group:          compat
shadow:         compat


hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files


protocols:      db files
services:       db files
ethers:         db files
rpc:            db files


netgroup:       nis

```

I tried to make sure the relevant packages are almost the same on both machines. 
Both run kernel [FONT=courier new]Linux web1 3.13.0-74-generic #118-Ubuntu.[/FONT] All resolv files are the same,
/etc/hosts is the same, /etc/nsswitch.conf is the same. I made a diff of the ping program and they are the same. 

I'm clueless!?
any idea? 

yves

---

