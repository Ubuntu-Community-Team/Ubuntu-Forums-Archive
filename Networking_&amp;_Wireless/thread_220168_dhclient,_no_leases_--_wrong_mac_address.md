---
title: "dhclient, no leases -- wrong mac address?"
date: 2006-07-21
forum: Networking &amp; Wireless
---

### Post by jedsen on 2006-07-21
I installed ubuntu for a friend of mine on his old PII 300MHz thinkpad. He has an old Dlink ethernet card for it, as it has no built-in ethernet, and for the life of me I couldn't get it to register with my router. My router is blocking all but a few MAC addresses, but even after entering the MAC address reported by ifconfig into the router (which is also running linux), I couldn't get a lease from the dhcp server. How do I figure out if this is a MAC address reporting issue, or an issue with the ethernet card (which seems to be working just fine)?

Thanks for any leads.

---

### Post by fabiand on 2006-07-21
Hey,

try to install tcpdump or ethereal (via Synaptic).
Afterwards you can run tcpdump while trying to get a lease.
Run tcpdump: sudo tcpdump -v -i eth0

---

### Post by jedsen on 2006-07-21
Thanks for the reply.

But the thing is, I can't download any packages on to it short of burning a CD, as it has no internet connection. It will be a big hassle to figure out what what dependencies I need to put on the CD.

---

