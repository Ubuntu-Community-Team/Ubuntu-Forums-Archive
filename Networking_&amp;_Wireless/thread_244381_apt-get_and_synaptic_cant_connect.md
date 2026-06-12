---
title: "apt-get and synaptic cant connect"
date: 2006-08-26
forum: Networking &amp; Wireless
---

### Post by War_Pig on 2006-08-26
Well installed Ubuntu yesterday, nothing could connect to the internet (could ping router though, so I disabled IPv6 in firefox and system wide (checked may times) now firefox works perfectly but apt-get and synaptic cant connect.

I have a Netgear DG632 router with latest firmware all set up correct
Onboard ethernet, detected ok 

Network settings seem ok, ip assigned via dhcp

I really have no ideas :(

Any help is much appreciated

---

### Post by War_Pig on 2006-08-26
got it sorted, had to enter the isp's dns and it resets it after every reboot..but I can live with that :)

---

### Post by bayvista on 2006-11-14
To fix this problem, edit /etc/dhcp3/dhclient.conf. See article by handy on DNS.

---

