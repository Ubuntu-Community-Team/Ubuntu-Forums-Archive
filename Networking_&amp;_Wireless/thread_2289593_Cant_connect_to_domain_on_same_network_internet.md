---
title: "Cant connect to domain on same network internet"
date: 2015-08-05
forum: Networking &amp; Wireless
---

### Post by francoisg on 2015-08-05
Hi

We have a internal ubuntu server with public ip 64.x.x.34 linked with a domain hosted by a third party SP. The domain points to that specific ip of the server that we host internally. 

Our internet router has public ip 64.x.x.31.

When i connect from inside our network to domain [www.domain.com/dir/dir]("http://www.domain.com/dir/dir"), the connection cannot resolve. When i connect from a different internet connection to that same domain, i connect fine and everything works.

I do not have a second nic enabled to point to our internal subnet range. I use the dns server for google 8.8.8.8

network config:
----------------------------------------------------
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 64.x.x.34
        netmask 255.255.255.248
        network 64.x.x.37
        gateway 64.x.x.31
        dns-nameservers 8.8.8.8
----------------------------------------------------



I would greatly appreciate any help on this.

Thank you

---

### Post by TheFu on 2015-08-05
Remove the network line - that is deprecated.

If you know the IP for the remote server and it won't change, just add that to your /etc/hosts.
Or you can use all the DNS tools to troubleshoot the DNS issue - hosts, dig, etc.

Would be helpful to see your routing table - please post it - unmodified.

---

### Post by SeijiSensei on 2015-08-05
Not only is it deprecated, but in this case it is also wrong.

The .248 netmask says your ISP allocated a 8-host subnet, of which the first and last addresses are unusable.  So you could have machines with addresses between 25 and 30, or ones with addresses between 33 and 38.  In those cases the network address would be 64.x.x.24/29 or 64.x.x.32/29.  There is no  eight-host subnet that includes both .31 and .34, and there is no eight-host network whose network address ends in .37.

I'd check with the ISP again about the subnet numbering.

Some ISPs allocate sequential network addresses without paying attention to subnet masks.  It could be that you share a full class-C subnet of 253 hosts with other customers.  In that case you would be using 64.x.x.0/24.

---

