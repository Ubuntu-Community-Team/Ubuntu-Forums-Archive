---
title: "Can't resolve DNS records when assigning static IP"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by spintel on 2008-11-20
When I let network manager use DHCP to get an address from the domain controller, i can access any DNS record with no problem ex. if i ping staff-evs i get a response.

If i assign a static address I cannot hit any DNS records.  if i ping staff-evs it returns unreachable host.  I have my IP, gateway, subnet and dns all defined.

Has this happened with anyone else?

---

### Post by Iowan on 2008-11-20
I haven't personally had it happen, but I've seen other threads mention that as a drawback to a static address on a DHCP network.

---

### Post by superprash2003 on 2008-11-21
after you have configured static ip, post output of cat /etc/resolv.conf

---

### Post by mang_ucup on 2009-02-05
I have the same problem in here. I installed ubuntu in virtual box and create bridge network. When set fix ip to my ubuntu i couldn't resolve the domain name but i can ping to outside ip.

My Bridge ip: 10.0.8.2/24
My Ubuntu ip: 10.0.8.3/24
Gateway 10.0.8.1

My resolv.conf : 10.0.0.1

What i did wrong?

---

