---
title: "How to delete a route permanently?"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by YesWeCan on 2010-06-06
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.8.0.5        0.0.0.0         255.255.255.255 UH        0 0          0 tun0
10.8.0.1        10.8.0.5        255.255.255.255 UGH       0 0          0 tun0
192.168.1.0     10.8.0.5        255.255.255.0   UG        0 0          0 tun0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0

I added a route to my routing table (3rd row above) and now I would like to delete it. I can delete it using 'sudo route del -net 192.168.1.0 netmask 255.255.255.0 dev tun0' but on reboot it gets reinstated. How do I delete it permanently?
Many thanks.
Brian

---

### Post by YesWeCan on 2010-07-26
My goof. I had a application that added this route at boot time that I forgot about. All fixed.

---

