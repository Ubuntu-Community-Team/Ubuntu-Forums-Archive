---
title: "Problems setting up dnsmasq DHCP/DNS"
date: 2016-11-14
forum: Networking &amp; Wireless
---

### Post by toothandnail on 2016-11-14
I'm trying to migrate from an old Slackware-based server (provides storage plus DHCP/DNS for my local network) to the latest 16.04 Ubuntu server. Most things have been easy enough to set up, but I'm having lots of problems getting dnsmasq to work the way I need.

This is the dnsmasq.conf I've been using under Slackware:

```
domain-needed
bogus-priv
resolv-file=/etc/nameserver.list
local=/ibmpeers.net/
domain=ibmpeers.net
expand-hosts
dhcp-host=50:f5:da:d4:a8:ef,Firestick,192.168.1.95
dhcp-host=00:23:24:30:D9:C0,brillbox,192.168.1.12
dhcp-option=option:router,192.168.1.254
dhcp-option=vendor:MSFT,2,1i
dhcp-authoritative
```

/etc/namserver.list is a simple list of upstream DNS servers.

This configuration doesn't work under 16.04.1 - DHCP for the local network is fine, but it fails to pick up any of the upstream DNS servers, so nothing, including the server itself, can resolve internet names.

Most of the problem seems to have stemmed from resolvconf. After trying a number of options, I put IGNORE_RESOLVCONF=yes into /etc/default/dnsmasq, and used systemctl disable resolvconf. At that point I was able to put the new test server on a static IP and get external DNS working. Unfortunately, that still leaves me with problems with local DNS resolution (the main reason for using the server for DHCP/DNS services).

I'm wondering if anyone has a working dnsmasq setup to cover what I'm trying to do? Any suggestions for getting things working without having to disable resolvconf would be useful as well.

Paul.

---

