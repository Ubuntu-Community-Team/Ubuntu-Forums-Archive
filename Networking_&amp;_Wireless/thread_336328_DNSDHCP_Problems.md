---
title: "DNS/DHCP Problems"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by danharper on 2007-01-11
Just set up ubuntu server on a test machine, so far I have configured the network card for dhcp, sorted the package repositories and installed ssh.

I can ping locally and externaly using hostnames on my ubuntu box, but I can't ping the ubuntu box from another client using it's host name.

When I looked on my windows dhcp server the registered IP address has no name against it, how can I make the name appear.

Any help would be appreciated.

Dan

---

### Post by Iowan on 2007-01-12
You probably need to edit /etc/dhcp3/dhclient.conf

```
sudo gedit /etc/dhcp3/dhclient.conf
```
uncomment the line 

```
#send host-name "andare.fugue.com";
```
and insert your hostname.

---

