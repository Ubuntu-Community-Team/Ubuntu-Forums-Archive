---
title: "Routing problem Ubuntu 12.04"
date: 2013-12-21
forum: Networking &amp; Wireless
---

### Post by jandedecker on 2013-12-21
Hi all,

I have the following configuration:

Hercules machine:

eth0    inet addr:10.0.1.1  Bcast:10.0.1.255  Mask:255.255.255.0
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
tun0    inet addr:10.0.172.1  P-t-P:10.0.172.8  Mask:255.255.255.255
          UP POINTOPOINT RUNNING  MTU:1500  Metric:1

Client machine:

eth1  inet addr: 10.0.1.101 Bcast 10.0.1.255 Mask 255.255.255.0
        UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

Hercules client:

IP address 10.0.172.8


I do not manage to add a route from the client machine to the Hercules
client machine. I scanned the forums and found nothing that works.
The Hercules machine has no problems with the Hercules client, the client
machine has no problems with the Hercules machine.

Can somebody help?

Many thanks,

---

### Post by ian-weisser on 2013-12-22
> **jandedecker said:**
> 
I do not manage to add a route from the client machine to the Hercules
client machine. I scanned the forums and found nothing that works.
The Hercules machine has no problems with the Hercules client, the client
machine has no problems with the Hercules machine.


I do not understand the problem.
If the machines are on the same subnet, and can communicate successfully, then they discovered a route. You don't need to manually specify a route.

---

### Post by jandedecker on 2013-12-23
Hi

The 'Hercules machine' has 2 adapters, eth0 10.0.1.1 & tun/tap 10.0.172.1 for the Hercules guest operating system 10.0.172.8 No problem between 10.0.1.1 & 10.0.172.8

The 'Hercules client machine has 1 adapter eth1 10.0.1.2. The subnet mask is 255.0.0.0 for all machines. 10.0.1.2 & 10.0.1.1 can communicate but I would like to have access to the Hercules guest operating system from the Hercules client machine.

I tried everything I could find on the WWW but could not define a route from 10.0.1.2 to 10.0.172.8 or even 10.0.172.1

Any help would be greatly appreciated.

---

