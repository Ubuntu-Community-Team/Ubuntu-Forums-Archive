---
title: "How do i make hostname.local into just hostname for resolving local dns"
date: 2020-06-28
forum: Networking &amp; Wireless
---

### Post by evil-goat on 2020-06-28
On some devices sutch as windows, the servers *local* hostname resolves fine, but on other devices, it olny resolves if i do hostname.local. How can i make the hostname resolve without putting .local afterward?

---

### Post by TheFu on 2020-06-28
That is a limitation for the default avahi implementation.
To get it working as you want, run a DNS server and setup a search in the resolv.conf file. This is a non-trivial effort dependent on your skill as a Unix admin.  For 5 machines or less, probably just easier to maintain the /etc/hosts.

Aren't DNS and DHCP servers connected on Windows?  They are not on Unix, so if you intend to have DHCP systems also in DNS, that has to be setup for each system using reservations.  Running a local DNS means that all the caching of DNS Canonical sets up on our systems just gets into the way, so we usually want to disable/remove systemd-resolved and resolvconf subsystems after the DNS is working.  Probably want 2 DNS servers for redundancy.

---

### Post by pcfan1234 on 2020-06-30
> **evil-goat said:**
> On some devices sutch as windows, the servers *local* hostname resolves fine, but on other devices, it olny resolves if i do hostname.local. How can i make the hostname resolve without putting .local afterward?
Problems will occur if you do so, because .local is a top level domain that isn't being resolved by the DNS servers in the internet, so you can use it and use either mDNS (Bonjour/Avahi) or you own DNS server running on your own equipment (e.g. BIND, dnsmasq).
If you only use mycomputer instead of mycomputer.local, you will definitely get problems with browser's URL bar, because they are combined with a search bar and mycomputer will be detected as a search term.
mycomputer.local won't, it will be resolved via your local DNS.

---

### Post by TheFu on 2020-06-30
What pcfan1234 says is true, if you keep using Avahi.  

There is a way to force avahi to use something other than .local. Some people use .lan.  But then every system on the network needs to be reconfigured for that, which may not be possible for non-computer devices which include avahi implementions (also called ZeroConf).

Have you tried adding search "local"?

As a reference, I have public and internal servers.  Here's my settings:
```
$ more /etc/resolv.conf 
nameserver 172.22.22.80
nameserver 172.22.22.81
search jdpfu.foo jdpfu.com
```

So the "local" would be equivalent to "jdpfu.foo".  When I ping other systems, the FQDN for the internal gets looked up and used:
```
$ ping hadar
PING hadar.**jdpfu.foo** (172.22.22.6) 56(84) bytes of data.
64 bytes from hadar (172.22.22.6): icmp_seq=1 ttl=64 time=0.124 ms
64 bytes from hadar (172.22.22.6): icmp_seq=2 ttl=64 time=0.189 ms

```
This is exactly what you want.  I get this by running redundant DNS servers inside a pair of LXD containers, running on different physical machines.  Because I do DHCP reservations for a few portable systems, having the redundant DNS is necessary for those devices to get the correct IPs at boot.  But most of my systems use locally configured, static, IPs, so they aren't dependent on any external network services outside the gateway router.

---

