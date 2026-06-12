---
title: "Load Balancing"
date: 2008-04-05
forum: Networking &amp; Wireless
---

### Post by swordphsh on 2008-04-05
My college limits internet connection speeds for the dorms to about 160 KB/s down and somewhere around 20 KB/s up. Each ip leased on the network gets these speeds, for example I could be downloading at 160 KB/s on my pc and also in a virtual machine on my pc (using a bridged connection).

I am wondering if there is any way to set up load balancing between two ethernet adaptors so that i could download up to 320 KB/s from just one computer. I tried setting up an ubuntu server virtual machine with two ethernet adaptors, but I cannot figure out how to get it to route traffic through both of them.

Any help is appreciated,
Thanks.


--Justin

---

### Post by tamoneya on 2008-04-05
I have a similar situation.  While I dont have the same bandwidth limiting I do have two NICs on my motherboard and would like to try and take advantage of that.  What I have noticed is that only one of them gets assigned an IP address through DHCP.  And when I use static only one of them will get a load on it(watching in gkrellm).

---

