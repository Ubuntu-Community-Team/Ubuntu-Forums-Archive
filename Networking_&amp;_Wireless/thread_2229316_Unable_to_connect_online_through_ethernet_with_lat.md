---
title: "Unable to connect online through ethernet with latest version Ubuntu Server"
date: 2014-06-12
forum: Networking &amp; Wireless
---

### Post by matt_c2 on 2014-06-12
Hello everyone, 

I am a complete beginner to linux, however I decided to use my old unused acer aspire Revo 1600 nettop to start learning. I downloaded the 64bit off of [http://www.ubuntu.com/download/server](http://www.ubuntu.com/download/server) just  a few days ago.  Full info about the machine here [http://www.cnet.com/products/acer-aspire-revo-ar1600-u910h/](http://www.cnet.com/products/acer-aspire-revo-ar1600-u910h/)

It has a gigabit ethernet and I see lights flashing when I connected it to my switch so I think it can connect. I used the ping command below and this is my result. 

ping [www.google.com](www.google.com)
ping: Unknown host [www.google.com](www.google.com) 

when I use ifconfig  

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2480 (2.4 KB)  TX bytes:2480 (2.4KB)


Do you guys mind helping me with this? I really don't know what's going on. 

Thank you.

---

### Post by Bashing-om on 2014-06-12
matt_c2; Hello ,

Sure, I will start this ball rolling. let's look at the basics and go from there:
network card detected ?
```

sudo lshw -C network
lspci | grep Ethernet

```

We know from the output of 'ifconfig' that there is no IP address assigned, so: let's check the interface config file:
```

cat /etc/network/interfaces

```
And what can you "ping" ?
```

ping -c3 127.0.0.1 ##checks to make sure the hardware works##
ping -c3 192.168.0.1  ## the IP of the router/switch - replace with the correct IP for your switch##
ping -c3 8.8.8.8 ## are you getting out-of-house ??##

```

And what is assigned for nameservers ?
```

cat /etc/resolv.conf

```

We are looking at several things, perhaps these outputs will indicate where the fault lies.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

