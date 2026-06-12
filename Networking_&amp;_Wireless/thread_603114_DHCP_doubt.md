---
title: "DHCP doubt"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by LMSSML on 2007-11-04
Hi there

I made simple configuration for dhcp server butwhen I do 

default-lease-time 86400;
max-lease-time 60800;

and when I do 

/etc/init.d/dhcp3-server restart

it says that I have line 5 that correspond to default-lease-time with an error.

Could anyone help.

---

### Post by SpiritIsReality on 2007-11-04
howdy
I don't know much about dhcp, but could you try setting the default-lease-time to a value less than the max-lease-time?
for example, in the file, /etc/dhcp3/dhcp.conf
default-lease-time 600;
max-lease-time 7200;

trails

---

### Post by LMSSML on 2007-11-05
Hi htere,

Thanks for the fast awnser

But if I want a more long  lease time  it couldn't be done.

Could it be possible that it's incorrect the command default-lease-time

Thanks

---

### Post by SpiritIsReality on 2007-11-05
> **LMSSML said:**
> Hi htere,
Thanks for the fast awnser
But if I want a more long  lease time  it couldn't be done.
Could it be possible that it's incorrect the command default-lease-time
Thanks
howdy
I found this, it has the default and max times set equal in the example.
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch08_:_Configuring_the_DHCP_Server](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch08_:_Configuring_the_DHCP_Server)

[http://www.google.ca/search?hl=en&q=linux+networking&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=linux+networking&btnG=Google+Search&meta=)
[http://www.linuxhomenetworking.com/](http://www.linuxhomenetworking.com/)
trails

---

