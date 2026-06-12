---
title: "VMWare 2.0 (Mac OS X): Ubuntu Server - Network is down"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by dodeantn on 2008-10-04
Hi,

I've got a Ubuntu Server running in VMWare on Mac OS X. So far I think I've configured everything right.

I can reach the cloud from withtin the virtual machine; but I can't seem to reach the vm from the host (Mac OS X) -- I tried pinging it: "Network is down".

My Ubuntu Server has (of course) a statically configured network interface:

```

auto eth0
iface eth0 inet static
    address 192.168.54.129
    netmask 255.255.255.0
    gateway 192.168.54.2

```

Thanks for your advice,

Cheers

---

