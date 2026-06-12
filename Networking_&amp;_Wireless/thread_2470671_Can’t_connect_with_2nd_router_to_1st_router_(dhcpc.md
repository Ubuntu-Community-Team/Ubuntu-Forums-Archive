---
title: "Can’t connect with 2nd router to 1st router (dhcpcd) - Need help!"
date: 2022-01-07
forum: Networking &amp; Wireless
---

### Post by han85 on 2022-01-07
Hi guys!

I need help because I am not getting anywhere with my problem.

On my Windows machine I can connect over 2nd router to LAN-port 1 over WAN-port out to
1st router on LAN-port 1.

All is working with that.

**On my Linux machine with Ubuntu I cannot connect over 2nd router to LAN-port 2 over WAN-port out to 1st router on LAN-port 1.**

At my 1st router I can see the 2nd router's wan-ip only. Not the client ip from 2nd router.

"DHCPCD"
**/etc/dhcpcd.conf** (config)

static ip_address=**192.168.178.243**/24 - client ip
static routers=**192.168.178.242** - 2nd router ip gateway
static domain_name_servers=127.0.0.1

at router webpage settings:
WAN-ip 2nd router = **192.168.178.241**
Gateway set to 1st router: **192.168.178.142**

eth0 is connected on my Linux machine:
> ip a
...
[B]inet 192.168.178.243/24 brd 192.168.178.255 scope global noprefixroute eth0
       valid_lft forever preferred_lft forever[/B]

but can't connect to internet.

Or do I need to set the **wan-ip from the 2nd router as gateway on dhcpcd.conf**?

Open ports on 1st or 2nd router?

Maybe someone here knows a lot about networks and can help me.

---

### Post by TheFu on 2022-01-07
If your intention is to have 2 wifi areas on the same subnet, then don't use the WAN port on the "extension router" at all and disable all "routing" stuff like DHCP, DNS, on that "extension device".  Connect one of the LAN ports into a LAN port on the main router that connects to the internet.

When troubleshooting network connections, 
ping the main WAN router by IP address.
ping well-known internet IP addresses - like 1.1.1.1 or 8.8.8.8
If those work, then it is a DNS issue, not a network issue.  Ask for DNS help.

---

### Post by han85 on 2022-01-08
@ TheFu, got it now. WAN-TO-LAN is working now (WAN DNS set to 1.1.1.1) but when I set WAN DNS to machine 2 internal Pi-Hole DNS and Local DNS server also to internal Pi-Hole DNS (machine 2) then name resolution/internet isn't working.

Now I just need to figure out how to use Pi-Hole as a DNS server on machine 2 @ second router.

On my main router Pi-Hole works as a local DNS server without problems.

What irritates me is the WAN DNS on my second router.

No idea until now how to solve this with OpenWRT.

Maybe set WAN DNS to router LAN ip (second router) and under DHCP server (second router) set the internal Pi-Hole ip (from machine 2) as DNS server.

In addition, under Local DNS server section on the second router set the internal Pi-Hole DNS server ip. (from machine 2)

Otherwise I do not know how I can solve the WAN DNS issue.

On my main router I do not use WAN.

Any idea how I can solve this with the WAN DNS?

Regards!

---

### Post by TheFu on 2022-01-08
Seems you've confused yourself.

Set all the DNS on your LAN to point at your pihole.  All of it.  The internal router isn't going to be used as a router. It will act like a bridge. You cannot use the WAN port on the internal router.

Only the PiHole should point to external DNS providers.

Do you want all the systems to be on the same LAN/subnet or not?

Perhaps if we label the devices clearly and use name?

rt1 = WAN router. This connects to the Internet directly.
rt2 = LAN bridge.  It doesn't run any routing or DHCP or DNS at all. It is really just a dumb switch
computerA-Z = computers connected to either rt1 or rt2 via wired ethernet

Get those working first.

rt1 and rt2 are connected using a wired ethernet connection. Both sides of the connection plug into "LAN" ports on both devices.

rt1 runs DHCP, but not DNS services.  In the DHCP settings, the DNS services point to the Pi-Hole IP address.
The Pi-Hole must have a static IP, always. Best to set that up on the device and not depend on DHCP reservations.

Start with that.
Are the statements about rt1 and rt2 all correct?

---

### Post by han85 on 2022-01-09
I have now moved to LAN-to-LAN.

Disabled DHCP on second router. Set second router ip for LAN.

Added main router ip (gateway) in: "**/etc/dhcpcd.conf**" (VM machine)

interface eth0
    static ip_address=**pi.hole-ip-here**/24
    static routers=**main-router-ip-here**
    static domain_name_servers=**127.0.0.1**

Edited resolv.conf:
from:

> search pi.hole
> domain pi.hole
> nameserver 127.0.0.1

to:
> search fritz.box
> domain fritz.box
> nameserver 127.0.0.1


Removed from: "**/etc/dnsmasq.d/01-pihole.conf**" (VM machine)
*rebind-domain-ok=pi.hole*

Rebooted and now it works on my VM machine.

SOLVED! :-)

---

### Post by TheFu on 2022-01-09
You shouldn't need to touch the dhcp.conf file nor the resolv.conf.

There appears to be confusion about what the resolv.conf settings
search and domain mean.

These are related to DNS search and DNS domains.  Most home LANs don't need anything for either settings, since they don't have either.

A personal example which might help you understand those settings clearer.
My DNS domain on the LAN is thefu.lan and my public DNS is  .  The domain just tells the local machine what domain it is part of.

hostname: hadar
domainname: thefu.lan

So the dns search and dns domain settings in the /etc/resolv.conf are
```
search thefu.lan jdpfu.com
```
All that does is tell the nameserver queries to try what ever I type in, say "foo" then try  "foo.thefu.lan" and "foo.jdpfu.com" ==== IN THAT ORDER ==== when looking up IP addresses.
I don't have any domain setting in the resolv.conf because my systems have that set elsewhere, but it isn't important at all.

So, if any of my systems look for "blog" ... the DNS search will search and find     blog.jdpfu.com   which is my personal blog website.

The only setting in /etc/resolv.conf that should point at your pihole is the 
```
nameserver 192.168.x.x
```
And it doesn't even get the hostname. I had to use the static IP address.  The fact that fritz.box resolves is just something that vendor did.  Niether are found from my systems here. 
```
$ ping fritz.box
```
doesn't work.

---

### Post by han85 on 2022-01-10
@ TheFu...

Is it necessary to leave my resolv.conf as it is?

_host:_
search pi.hole
domain pi.hole
nameserver 127.0.0.1

_vm:_
search fritz.box
domain fritz.box
nameserver 127.0.0.1

Can I remove the search and domain option from my resolv.conf without problems and leave "**nameserver 127.0.0.1**" alone?

Domain and search (resolv.conf) are for the public network, right?

---

### Post by TheFu on 2022-01-10
There are multiple different ways that the /etc/resolv.conf file might be managed. I don't know how yours is managed. The systemd-resolved or resolvconf or some other process might be managing it. That means it will be re-written without your knowledge based on some entries made elsewhere - perhaps in a GUI or config file.  You'll have to figure out which is doing that, if any.

There is no need for search or domain entries in the resolv.conf file for 99% of home networks.  They are used for all name resolution - LAN and internet.
>  Can I remove the search and domain option from my resolv.conf without problems and leave "nameserver 127.0.0.1" alone?
Probably fine, but I don't know your network, honestly cannot say if you are in the 1% where it matters or not.  You can always put it back. You do make backups, right?  Just make a copy of the file - if it is a regular file.  I suspect resolv.conf is actually a symbolic link to a file stored elsewhere. Read up and understand what a symlink is BEFORE changing stuff.  There's a wikipedia article about it, which is fine.

---

### Post by han85 on 2022-01-10
@ TheFu,

Disabled Systemd-resolved.

Resolv.conf is used directly.

I will try it without search and domain (resolv.conf).

---

