---
title: "Replacing dhcp3-client with dhcpcd (or any other dhcp client that works)"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by zooounds on 2007-04-21
Hi!

Is it possible to replace the dhcp3-client that ships with Feisty with any other dhcp client (like dhcpcd)?

How do I do this?

---

### Post by RandomJoe on 2007-04-21
dhcpcd is listed in Synaptic, so you can easily install it.  I don't know what (if anything) has to be done to use it in place of dhclient.

What problems are you having with dhclient?  It is working fine for me, and even sends the hostname by default now - I used to have to edit the config file to get that to happen...

---

### Post by zooounds on 2007-04-22
This is the issue:

[https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/33968](https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/33968)

---

