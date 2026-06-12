---
title: "How to tell what Guarddog has defined as &quot;local&quot;"
date: 2008-01-22
forum: Networking &amp; Wireless
---

### Post by doug-M on 2008-01-22
I'm trying to use Guarddog as a firewall configuration tool but I'm having trouble connecting to a VPN.

I believe I have set it up correctly but I think guarddog has chosen something else as the "local" network IP address range. I can see the packet get dropped in they syslog /var/log/messages.

Some details:

I'm using a laptop that moves between a few networks.

Network interfaces shown by ifconfig:
eth1 - the local wired network using dhcp
vmnet1 - VMWare server host only network
vmnet8 -  VMWare server NAT network
wlan0 - wireless, currently no IP
wmaster0 - wirless, currently no IP (not sure what this interface is)

I created 2 custom guardog  rules for testing to allow everything 
  All TCP -   TCP 0-65535
  All UDP Bidirectional - UDP 0-65535 bidirectional

I created zones for:
VPN - address of PTPP vpn endpoint
VMWare Host
VMWare NAT
VPN internal network - address range at far end of VPN tunnel

Protocols served from zone "internet"  to clients in zones:
  local - All TCP and All UDP Bidirectional

Protocols served from zone "local" to clients in zones:
  VPN - All TCP and All UDP Bidirectional
  VPN internal network - All TCP and All UDP Bidirectional

Protocols served from zone "VPN"  to clients in zones:
  local - All TCP and All UDP Bidirectional

Protocols served from zone "VPN internal network"  to clients in zones:
  local - All TCP and All UDP Bidirectional

This is pretty permissive so I don't see why it wouldn't work.

When I try to connect I see:
DROPPED IN= OUT=eth1 SRC=[dhcp IP of eth1 interface]  DST=[VPN endpoint IP] LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=24761 DF PROTO=47 

Of course if I disable the firewall it works and ppp0 shows up as an interface.

So I suspect that Guarddog has set local to be some other address range (maybe vmnet1?) but I don't know how to tell what it defines as "local".

Any help appreciated, thanks.

---

### Post by doug-M on 2008-05-27
Bumping this back up to the top since it is still a problem.

I didn't have much luck on the Guarddog mailing list either.
They just suggested rerunning the script after any interface changes.
No mention of what script. I did try applying the rules and disable/enable the firewall but it still doesn't work.

So is Guarddog just not useful for slightly complex firewall situations? I tried Firestarter but it seemed even more simplistic and inflexible.

Anyone have suggestions for alternatives or how to diagnose the problem with Guarddog?

---

### Post by doug-M on 2008-05-29
The best alternative I am seeing so far is Firewall Builder [http://www.fwbuilder.org/](http://www.fwbuilder.org/)

---

