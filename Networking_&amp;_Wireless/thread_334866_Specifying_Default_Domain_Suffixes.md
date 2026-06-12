---
title: "Specifying Default Domain Suffixes"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by tom purl on 2007-01-09
I just set up a new instance of Xubuntu today, and would like to be able to specify value that's in the "search" line in /etc/resolv.conf.  I can edit it manually, but when I restart networking, that line is erased.  I think it has something to do with DHCP, which I am using.

I tried the following in my /etc/networking/interfaces file, but it doesn't seem to be updating my /etc/resolv.conf file:

```
    
auto eth0
iface eth0 inet dhcp
    dns-search foo.bar.com

```

Does anyone know how I can properly set this up?

Thanks a ton in advance!

Tom Purl

---

### Post by Iowan on 2007-01-10
You may need to edit the **/etc/dhcp3/dhclient.conf** file... There are several items on a **request** line - perhaps one (domain-name or domain-name-servers) is responsible for erasing your data.

---

### Post by tom purl on 2007-01-12
Thanks a ton for the help Iowan!  I'll be sure to try this soon.

---

