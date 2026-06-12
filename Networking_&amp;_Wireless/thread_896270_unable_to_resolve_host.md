---
title: "unable to resolve host"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by iswariak on 2008-08-21
Hi all,

I am trying to configure my network using static ip for ubuntu 8.04. Now I am able to access the internet. But if I use sudo in the terminal, it is showing unable to resolve host.

----------------------
content of /etc/hosts
----------------------

127.0.0.1 localhost localhost.localdomain
x.x.x.x geodev1.localdomain geodev1
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

where x.x.x.x is my ip address.

Please advise.

Thanks

---

### Post by jimv on 2008-08-21
you need a line like:


127.0.1.1 YourComputersName

---

### Post by iswariak on 2008-08-21
Even I tried adding the line 127.0.1.1 with my hostname.

But no positive signs

---

### Post by Iowan on 2008-08-21
It probably won't matter, but try reversing the settings for localhost: 
**127.0.0.1 localhost.localdomain localhost**

---

### Post by jimv on 2008-08-22
Here's mine if it helps:

127.0.0.1 localhost ubuntulaptop
127.0.1.1 ubuntulaptop

---

