---
title: "anyone know a dhcp that accepts bad credit???"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by Mgiacchetti on 2008-06-10
im using a wap54g as a client bridge using DD-WRT firmware..  the Gateway is a WRT54g with UPDATED CURRENT linksys firmware.  

I cannot get a dhcp lease from my wrt on my compaq connected to my wap.

it sees the laptops fine, and the comp wired directly to the WRT ok as well, but when my comp tries to lease, its like "nope you have horrible credit."

ive tried everything, including:
updating firmware on linksys (twice)
factory reset on both
power cycle entire network

on my compaq box i cannot get a lease in windows and ubuntu.  in ubuntu its something like 
DHCP REQUEST  5
DHCP REQUEST  7
DHCP REQUEST  14
DHCP REQUEST  9

NO AVAILABLE DHCP RESPONSE ..... sleeping

ok now.  do i have to disable dnsmasq on the client bridge to be able to get a dhcp??  

for now i am forced to use Static ip's which i really dont wanna do.

(sidenote)
i have sun virtualbox installed with a bridge at br0  (that is my actual connection) so anything done to eth0 is useless because bro0 overrides it.

(other information)
it was working correctly, then it stopped.  when i am in coma mode, i cannot ping anything, no 192.168.1.1 or 192.168.1.2, i ifconfig and i get the above...  i get no connection until i set br0 static.  then all is online.

---

### Post by Mgiacchetti on 2008-06-10
friendly little ^bump^

---

### Post by netztier on 2008-06-11
> **Mgiacchetti said:**
> 
ok now.  do i have to disable dnsmasq on the client bridge to be able to get a dhcp??  


To the very best of my knowledge, there is no "bad credit" concept in DHCP. Where'd you get that term from?
If your client doesn't receive any DHCP OFFER messages after it sent out it's DHCP DISCOVER messages, it might just be that these never made it to the DHCP server (typical reason on WLANs: bad encryption setup) - hence it has no cause to send an OFFER message back. 

Oh wait.. your log excerpt said DHCP REQUEST - so the OFFER did come back, actually, but the DHCP REQUEST got lost somewhere.. hmm. 

On the other hand: if you use a "client bridge", it is supposed to be a "bridge". Bridges work at Layer 2 and have no concept of IP addresses (bar having one to serve their Web GUI), they should work on MAC addresses only. Therefore, "dnsmasq" and other upper-layer oriented functionality such as firewalls, network address translation and the likes should be disabled (unless they come in their layer2-oriented flavour and are configured accordingly, but L2-firewalling is a rather advanced thing).

I think that something's mangling the DHCP dialog - try removing anthing on the client bridge that might interfere at the IP or upper layer.

regards

Marc

---

### Post by Mgiacchetti on 2008-06-11
ok that was a **bad** from memory quote of my problem

actual log is as follows:```

Listening on LPF/eth0/my mac address
Sending on   LPF/eth0/my mac address
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by Mgiacchetti on 2008-06-11
> **netztier said:**
> 

Oh wait.. your log excerpt said DHCP REQUEST - so the OFFER did come back, actually, but the DHCP REQUEST got lost somewhere.. hmm. 
see above post

> **netztier said:**
> 
On the other hand: if you use a "client bridge", it is supposed to be a "bridge". Bridges work at Layer 2 and have no concept of IP addresses (bar having one to serve their Web GUI), they should work on MAC addresses only. Therefore, "dnsmasq" and other upper-layer oriented functionality such as firewalls, network address translation and the likes should be disabled (unless they come in their layer2-oriented flavour and are configured accordingly, but L2-firewalling is a rather advanced thing).

however when i first set this system up...  EXACTLY AS IT IS NOW i (my machine) received an ip address from the host router (wrt)..  something happened somewhere along the line that disabled the ability for my box(compaq) to receive an ip through the bridge(wap) from the host router(wrt)

> **netztier said:**
> 
I think that something's mangling the DHCP dialog - try removing anthing on the client bridge that might interfere at the IP or upper layer.


so you mean disable dnsmasq?

yes or no.

---

