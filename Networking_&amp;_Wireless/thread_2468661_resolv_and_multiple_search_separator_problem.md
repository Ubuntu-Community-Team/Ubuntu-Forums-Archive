---
title: "resolv and multiple search separator problem"
date: 2021-11-07
forum: Networking &amp; Wireless
---

### Post by godfather007 on 2021-11-07
Hi,

i'm strunggling with receiving multiple search suffixes.
Receiving through DHCP or cloud-init, it does not matter: multiple suffixes end up wrong in resolv.conf

I have multiple ".local" domains which i need to resolve. Unfortunately .local domains are mDNS and will be skipped by DNS @ 127.0.0.53 (multicast DNS on a server?)

Receiving multiple domain searches ends up with "internal.local**044**mgmt.local**044**corp.local"

Setting them manually using:
**sudo resolvectl domains eth0 internal.local mgmt.local corp.local**
makes it work but a _netplan apply_ makes **044 **come back through DHCP or cloud-init.

Any idea which divider character can be used? , ; : <space> ?

---

### Post by The Cog on 2021-11-07
I don't know, but if it's of any help, 044 is the octal for a dollar $ symbol, so I think that's where the 044 is coming from.

---

### Post by TheFu on 2021-11-07
Setup a real DNS. It isn't THAT hard.
Also consider using DHCP reservations for anything important - for non-laptop systems, it is smarter to use static IPs setup on-the-workstations/servers than to use DHCP reservations due to security failures [https://www.anvilsecure.com/blog/dhcp-games-with-smart-router-devices.html](https://www.anvilsecure.com/blog/dhcp-games-with-smart-router-devices.html) in DHCP.

When you do switch to using a local DNS, be certain to disable the caching DNS setup on your systems. Let the LAN DNS do that and reduce the points of failure.
Laptops are harder, if they move around.  I typically only have wifi use DHCP while the wired connection (using a USB3-to-GigE adapter) always uses a static IP.

---

### Post by godfather007 on 2021-11-07
> **TheFu said:**
> Setup a real DNS. It isn't THAT hard.
Also consider using DHCP reservations for anything important - for non-laptop systems, it is smarter to use static IPs setup on-the-workstations/servers than to use DHCP reservations due to security failures [https://www.anvilsecure.com/blog/dhcp-games-with-smart-router-devices.html](https://www.anvilsecure.com/blog/dhcp-games-with-smart-router-devices.html) in DHCP.

When you do switch to using a local DNS, be certain to disable the caching DNS setup on your systems. Let the LAN DNS do that and reduce the points of failure.
Laptops are harder, if they move around.  I typically only have wifi use DHCP while the wired connection (using a USB3-to-GigE adapter) always uses a static IP.


Yeah, i know.. i'm doing that manually now for about 20 years ;) but the world evolves to.... (in my company) .. k8s.


So i'm preparing for a orchestrated kubernetes environment where machines get spun up automatically through proxmox.
Resolv.conf is acting the same when using manual ip settings through Cloud-init.

---

### Post by TheFu on 2021-11-07
Well, use a devops tool (or any script you want) to fix it.  mask any systemd-resolved stuff and purge resolvconf. Delete and replace /etc/resolv.conf to have what you want - pointing at the DNS server.

I'd never trust mDNS.

---

### Post by godfather007 on 2021-11-08
> **TheFu said:**
> Well, use a devops tool (or any script you want) to fix it.  mask any systemd-resolved stuff and purge resolvconf. Delete and replace /etc/resolv.conf to have what you want - pointing at the DNS server.

I'd never trust mDNS.


I guess you're right... this is probably not the place to argue why there's a mDNS implementation on a server.iso ](*,)


Could i also create my own cloud-init image with a suiteable DNS client? One that interprets multiple search suffixes through DHCP (or cloud-init)?
Any advice on this direction?

---

### Post by godfather007 on 2021-11-09
It feels there is a problem with proxmox "use the host-settings" for cloud-init values.
Whenever setting the value "per VM", it works (with manual IP).

---

