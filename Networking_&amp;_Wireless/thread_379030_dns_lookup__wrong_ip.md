---
title: "dns lookup : wrong ip"
date: 2007-03-08
forum: Networking &amp; Wireless
---

### Post by drfloob on 2007-03-08
using nslookup, host, and dig, I am getting the WRONG IP address for a domain I own.  Let's call this domain 'www.test.com'

The problem is, for WHATEVER reason, all of these dns lookups are reporting the IP as 192.168.1.2 (my internal IP), whereas a dns lookup ANYWHERE else gets the correct IP of my server.  A reverse lookup on my internal IP returns a "not found" error.

```

$ nslookup www.test.com
Server:         66.75.164.90
Address:        66.75.164.90#53

Non-authoritative answer:
Name:   www.test.com
Address: 192.168.1.2
```

I have even tried specifying a specific dns sever, using one of opendns.com's servers, and I get the same result.  This HAS to be something local that I just can't find.

I have searched, and cannot find any reason for this.  I've tried restarting the network using /etc/init.d/networking restart, and I'm not running a local dns server (bind is not installed), so there's no local cache to flush (that I know of).

```

$ cat /etc/hosts
127.0.0.1       localhost
```

```

$ cat /etc/resolv.conf 
search socal.rr.com
nameserver 66.75.164.90
nameserver 66.75.164.89
nameserver 208.67.222.222
```

```

$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

```

$ cat /etc/nsswitch.conf 
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

I cannot figure this out.  Please help.  This is a real bugger.

---

### Post by Floppyjoe on 2007-03-08
If your router is using DNSmasq then your local machines may have an assigned Domain name to the internal IP address and possibly this might cause that problem for you.

---

### Post by Mr. C. on 2007-03-08
Turn off your routers DNS caching feature.

---

### Post by drfloob on 2007-03-08
Wicked odd, guys.  I've got a fry's cheapo-special Airlink AR315W wireless router.  It doesn't have a dns cache or use dnsmasq.  At least, I've never found one anywhere.

Anyhow, I restored the router to factory default and the funky lookup went away.  Simply restarting the router wouldn't do it.

I'd still like to know WHY this worked ... but at least it worked!  Thank you both!

---

### Post by Mr. C. on 2007-03-08
Seems unlikely, but lookups may have been cached in NVRAM.

Hard to know, but glad you're up and going,
MrC

---

