---
title: "dhcp3-server fails to start"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by releep on 2007-06-05
Whenever  I try to start the dhcp server I get a error message 

dhcpd self-test failed. Please fix the config file.
The error was: 

This is my config file

default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.1;

subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.100 192.168.1.120;
} 

any ideas would be helpful.

Ive tried several other config setting to no advail

---

### Post by Wicca on 2007-06-07
Hi,

I'm not sure if this is the reason, but it doensn't look 'neat'. The option stuff is all part of the subnet and should  be placed there. Also, the subnet-mask is mentioned twice (as option subnet-mask 255.255.255.0 and netmask 255.255.255.0).

I should write it this way:

```

default-lease-time 600;
max-lease-time 7200;

subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.100 192.168.1.120;
  option broadcast-address 192.168.1.255;
  option routers 192.168.1.1;
} 

```
I'm not sure how fault tolerant this stuff is, so again: I'm not sure if this does make any difference, but at least you can try.

---

