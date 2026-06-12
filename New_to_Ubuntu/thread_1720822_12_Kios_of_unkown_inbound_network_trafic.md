---
title: "12 Kio/s of unkown inbound network trafic"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by noidem on 2011-04-03
Hi all,

I have a cool Ubuntu 10.10 running smoothly on my good old Medion Laptop.

But I recently noticed in the system monitor a 12 Kio/s inbound unknown network traffic even when the machine is just freshly rebooted and "doing nothing special". No browser, no p2p, no drop box running...

I ran a "top" and saw nothing special.

I installed "iptraf" and ran it as sudo. This didn't help me very much. I couldn't spot the source and destination of this network traffic.

I have another machine, with the same version of Ubuntu 10.10, on the same network, that doesn't have this continuous 12 kio/s inbound traffic.

Is there a tool or command that will help me spot the source or destination of this traffic?

Thanks in advance for your help.

---

### Post by Paqman on 2011-04-03
> **noidem said:**
> 
Is there a tool or command that will help me spot the source or destination of this traffic?


Hmm, not really my area of expertise, but maybe something like Wireshark?

FWIW, even if the machine is supposedly "doing nothing" there are several candidates for quietly using bandwidth (updates, ntp, Ubuntu One, etc)

---

### Post by 5149.5 on 2011-04-03
netstat -antp   ??????????

---

### Post by ~Plue on 2011-04-03
> **noidem said:**
> 
Is there a tool or command that will help me spot the source or destination of this traffic?

install and run etherape as root, then select the network interface

---

