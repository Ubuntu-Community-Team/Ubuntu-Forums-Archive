---
title: "tftp server problems"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by N1ESE on 2008-05-02
Ubuntu 8.04 Server Edition

I am having problems getting my tftp server to respond to ARP requests from my diskless PXE workstations.  The workstations are able to DHCP their IP addresses from the same server but are unable to then establish a tftp connection to continue booting.. only error message is ARP timeout.  

tftpd-hpa is working as I am able to get and put files from any tftp client on my network.  I have even setup a port forward on my gateway to allow tftp and was able to connect from outside of the network.  

Anyone have any ideas of things to look at here?  Thanks

- JT

---

### Post by N1ESE on 2008-05-02
Resolved, I ham-fisted something in dhcpd.conf :(

---

