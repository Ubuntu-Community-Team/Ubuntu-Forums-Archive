---
title: "Kubuntu Edgy--Can't Connect"
date: 2006-11-10
forum: Networking &amp; Wireless
---

### Post by cartwright on 2006-11-10
Yesterday I was able to connect to the internet (via Firefox).  Today I can't get my Kubuntu Edgy desktop to connect at all--I keep getting "Server not found."  I can't connect with Kopete or anything else.

I'm a bit of a newb to Linux.  I've searched these forums and can't really find anything on point.  Can anyone give me some direction in which to go to resolve this?  Thanks.

---

### Post by PisstMSTRCHIEF on 2006-11-10
What kind of connection are you using? wireless?:-k

---

### Post by happy-and-lost on 2006-11-10
How are you connecting? Wifi or Ethernet?

---

### Post by cartwright on 2006-11-10
Ethernet, sorry.  

I'm on a home network through SBC (2wire).

---

### Post by Iowan on 2006-11-10
Check **ifconfig**.  I have an Edgy box that "neglects" to pick up a DHCP IP (although it's currently working).  If there's no inet address (only an inet6 or ipv6), try **dhclient** (from a terminal).  
If you have static addresses set up... try disabling ipv6.

---

