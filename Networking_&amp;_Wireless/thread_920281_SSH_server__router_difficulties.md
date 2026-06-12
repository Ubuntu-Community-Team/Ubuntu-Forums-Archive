---
title: "SSH server / router difficulties"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by agmk on 2008-09-15
I'm trying to set up an ssh server, and I've narrowed my problem down to my router (or my ISP, but that seems highly unlikely).

On the server,
```
ssh localhost
```
and
```
ssh <localname>
```
work, where <localname> is the dns name internal to my home network.

also, from a remote computer, on the LAN
```
ssh <localname>
```
works.

additionally, using DynDNS i can ping the server, both from itself and from the second computer. however,
```
 ssh <dynDNSname>
```
returns "Connection timed out".

I have enabled port forwarding of port 22, udp and tcp, for my router (a TrendNet TEW432BRP), which had some effect - the error was previously "connection refused," but was ultimately of no avail. I have no firewall running on Ubuntu (Hardy Heron), iptables accepts all.

Is there anything I'm missing here? It seems the problem must be in the router, but I can't figure out how to fix it.

thanks...

---

### Post by nadalizadeh on 2008-09-15
Check your forwarding destination on the router.
for example I've a lan clients on my dlink router
which specify it to 192.168.1.x my local ip that
router see's (the ip of pc on the interface which
is connected to the router)

Also ssh with that ip to your self see if sshd is
listening on that interface too.

get interface information with :
ifconfig
/or/
ip a

---

### Post by agmk on 2008-09-15
The the router is forwarding to the correct local IP, and I can ssh to that IP (or the local DNS name). I took the router out and connected directly, and I can ssh there too.

Additionally, port 22 is open according to [http://www.canyouseeme.org/](http://www.canyouseeme.org/).

---

