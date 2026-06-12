---
title: "VMWare's VMNet + no connection on host"
date: 2006-09-15
forum: Networking &amp; Wireless
---

### Post by Sphere87 on 2006-09-15
Hello,

I have the following problem:

I am running Ubuntu 6.06 and installed VMWare Server to run Windows XP Professional as virual machine.

Now i have set the following settings with the vmware-config.pl:

eth0 -> vmnet0 (bridged?)
eth1 -> vmnet1 (bridged?)

It now works fine on the guest OS but on the base OS (my ubuntu) i can't get a connection. I'm using both wireless and wired, and i've read about some problems with wireless but it does also not work for wired. in kwifimanager i see that i am connected to the network though but i can't ping to the router.

i'm using eth0 and eth1 in my network config.

---

### Post by tagra123 on 2006-09-16
Using firestarter (or by editing iptables):

Make sure these ports are open on the ubuntu machine:

443
445
137-139

Also I believe I had to disable ICMP filtering in the firewall.

---

### Post by Sphere87 on 2006-09-16
As a wonder it works today.
I think it needed a reboot :)
(Or at least the service had to be restarted).

---

