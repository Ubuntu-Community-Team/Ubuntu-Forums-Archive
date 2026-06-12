---
title: "Is the &quot;network&quot; line needed in /etc/network/interfaces?"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by jeeves on 2008-02-24
*I'm experiencing some problems with the network manage in Hardy Heron Alpha 5, so I am configuring my network settings manually.*

SAMPLE CONFIGURATION:
 iface eth0 inet static
address 192.168.0.42
[COLOR="Red"]network 192.168.0.0[/COLOR]  << what goes here?
 netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.1

In all the sample configurations for the  **/etc/network/interfaces** file there is always a line for *network*. Is this line really needed? And if so, **what is supposed to go there?**

I'm using a dsl connection with a static IP.



The only thing the man page for interfaces says is: " Network address (dotted quad) required for 2.0.x kernels"

---

### Post by RebounD11 on 2008-02-24
That seems just fine to me. The network line refers to your ip-domain. If you apply a logical AND operation between your IP address and your netmask in binary the result would be your network:

for example in your case, given the following:
address 192.168.0.42 --> 11000000.10101000.00000000.00101010
netmask 255.255.255.0 --> 11111111.11111111.11111111.00000000
you can calculate address AND netmask, and you will get this:
==> 11000000.10101000.00000000.00000000 <==> 192.168.0.0 being your network

I don't know if it's absolutely necessary for that line to be there, since it can be calculated, try commenting it out and see if anything is changed; but what you posted here seems fine to me.

Are you connecting through a router?

---

### Post by kevdog on 2008-02-24
You dont need the network line if for home use.

---

