---
title: "Internet on Xubuntu."
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by ThomasWii on 2008-02-18
Hi, my mum and dads computer has xubuntu on it and its Internet is not working, it was working fine on the live CD, i use a ethernet cable that connects to the router, all help is much is appreciated :)

Thomas

---

### Post by Rogers on 2008-02-18
Interesting.  Can you please type sudo ifconfig -a and paste the output here?

---

### Post by ThomasWii on 2008-02-18
Thanks for your reply, the out put of the "sudo ifconfig -a" is ```
owner@owner-desktop:~$ sudo ifconfig -a
[sudo] password for owner:
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

owner@owner-desktop:~$ 

```

---

### Post by mnemosyne on 2008-02-18
Can you post the output of this command?
```
cat /etc/network/interfaces
```
It seems that the eth0 interface is not configured.

---

### Post by ThomasWii on 2008-02-18
Thanks for your reply, the out put is ```
owner@owner-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

owner@owner-desktop:~$ 

```

---

### Post by mnemosyne on 2008-02-18
Okay, so the ethernet interface isn't configured. Try "sudo mousepad /etc/network/interfaces" (without quotes) and add:
```

auto eth0
iface eth0 inet dhcp
```
Save it then try "sudo /etc/init.d/networking restart" (without quotes) and see if that works.

---

### Post by ThomasWii on 2008-02-18
thanks for reply, the out put was ```
owner@owner-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          eth0: ERROR while getting interface flags: No such device
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
                                                                         [ OK ]
owner@owner-desktop:~$ 

```

---

### Post by sisco311 on 2008-02-18
edit your resolv.conf file:

```
sudo mousepad /etc/resolv.conf
```

> nameserver **your routers ip address here**

restart your network:

```
sudo /etc/init.d/networking restart
```

---

### Post by ThomasWii on 2008-02-18
thanks for your reply, the ip was set to 192.168.0.1 which is the router one

---

