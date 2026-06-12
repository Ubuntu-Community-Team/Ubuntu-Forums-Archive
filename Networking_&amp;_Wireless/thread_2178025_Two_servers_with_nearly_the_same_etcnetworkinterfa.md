---
title: "Two servers with nearly the same /etc/network/interfaces but one doesn't work."
date: 2013-10-01
forum: Networking &amp; Wireless
---

### Post by andrew47 on 2013-10-01
I've been working on this problem for the last five hours non-stop, any help would be greatly appreciated. I have two servers with multiple interfaces and IP addresses configured in the /etc/network/interfaces file. One of the machines works, the other gives the following error.

```
RTNETLINK answers: File exists
Failed to bring up eth1.

```

This is the beginning of the interfaces file for the machine that works. It's too long to post the whole thing but it's just the same thing over and over, going up to 30 interfaces.


```
auto eth0
allow-hotplug eth0
iface eth0 inet static
    address 80.241.XX.XX
    netmask 255.255.255.0
    gateway 80.241.XX.XX
    dns-nameservers 79.143.183.251 79.143.183.252
    dns-search contabo.net


auto eth0:0
allow-hotplug eth0:0
iface eth0:0 inet static
   address 80.241.XX.XX
   netmask 255.255.255.0
   gateway 80.241.XX.XX
   dns-nameservers 79.143.183.251 79.143.183.252
   dns-search contabo.net


auto eth0:1
allow-hotplug eth0:1
iface eth0:1 inet static
        address 80.241.XX.XX
        netmask 255.255.255.0
        gateway 80.241.XX.XX
        dns-nameservers 79.143.183.251 79.143.183.252
        dns-search contabo.net


auto eth0:2
allow-hotplug eth0:2
iface eth0:2 inet static
        address 80.241.XX.XX
        netmask 255.255.255.0
        gateway 80.241.XX.XX
        dns-nameservers 79.143.183.251 79.143.183.252
        dns-search contabo.net


auto eth0:3
allow-hotplug eth0:3
iface eth0:3 inet static
        address 178.238.XX.XX
        netmask 255.255.255.0
        gateway 178.238.XX.XX
        dns-nameservers 79.143.183.251 79.143.183.252
        dns-search contabo.net
```

The interfaces file above works fine, no errors and all the IPs work.

The following interfaces file is part of the one from the machine that does not work and is giving the "file already exists" error. Again, this file is just repeating so I don't think I need to post the whole thing. I have removed the DNS, networking and gateway parameters in effort to make it work but nothing I've done has helped. Before, it looked just like the interfaces file above but with different DNS servers because they are in different countries.

```
auto eth1:25
allow-hotplug eth1:25
iface eth1:25 inet static
        address 205.251.XX.XX
        netmask 255.255.255.224


auto eth1:26
allow-hotplug eth1:26
iface eth1:26 inet static
        address 205.251.XX.XX
        netmask 255.255.255.224


auto eth1:27
allow-hotplug eth1:27
iface eth1:27 inet static
        address 205.251.XX.XX
        netmask 255.255.255.224

auto eth1:28
allow-hotplug eth1:28
iface eth1:28 inet static
        address 205.251.XX.XX
        netmask 255.255.255.224
```

When I run ifconfig, the list includes eth0:0-30 and eth1:0-30 even if I don't configure them.

---

### Post by papibe on 2013-10-01
Hi andrew47.

I believe you have to define the interface before creating aliases. In other words, you should have an eth1 entry before creating eth1 : 0

Just a thought.
Regards.

---

### Post by andrew47 on 2013-10-01
I have defined the eth1 interface, I posted a portion near the end of the file. This is the beginning.

```
auto eth1
allow-hotplug eth1
iface eth1 inet static
        address 74.81.XX.XX
        netmask 255.255.255.248

auto eth1:0
allow-hotplug eth1:0
iface eth1:0 inet static
        address 74.81.XX.XX
        netmask 255.255.255.248

auto eth1:1
allow-hotplug eth1:1
iface eth1:1 inet static
        address 74.81.XX.XX
        netmask 255.255.255.248

auto eth1:2
allow-hotplug eth1:2
iface eth1:2 inet static
        address 74.81.XX.XX
        netmask 255.255.255.248
```

---

### Post by papibe on 2013-10-01
Got it, thanks.

When dealing with networking, the message file exists, usually refer to sockets.

My guess is that some of the aliases are trying to create a new default route that conflicts with the one defined before. According to some basic Debian documentation ([here]("https://wiki.debian.org/NetworkConfiguration#Multiple_IP_addresses_on_One_Interface")), aliases should not have the fields 'gateway' or 'dns-nameservers'.

Nevertheless, if you need different default routes for different aliases, you may need to change the metric of the alias, so that the route can be added as fallback.

Hope it helps.
Regards.

---

### Post by andrew47 on 2013-10-01
Thank you for the response.

My interfaces file does not contain gateway or dns-nameservers. The one that works does, the one that doesn't work doesn't. Weird right?

---

### Post by papibe on 2013-10-01
Interesting.

I think at least eth1 should have one, shouldn't it?

What is the current default route?
```
route -n
```
Regards.

---

### Post by andrew47 on 2013-10-01
```
root@nope:/etc# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         74.81.XX.XX     0.0.0.0         UG    100    0        0 eth1
10.0.0.0        10.16.XX.XX    255.0.0.0       UG    0      0        0 eth1
10.0.0.0        10.16.XX.XX    255.0.0.0       UG    0      0        0 eth0
10.16.XX.XX    0.0.0.0         255.255.255.248 U     0      0        0 eth0
10.16.XX.XX    0.0.0.0         255.255.255.248 U     0      0        0 eth1
74.81.XX.XX     0.0.0.0         255.255.255.248 U     0      0        0 eth1
74.81.XX.XX     0.0.0.0         255.255.255.248 U     0      0        0 eth0
205.251.XX.XX 0.0.0.0         255.255.255.224 U     0      0        0 eth1
205.251.XX.XX 0.0.0.0         255.255.255.224 U     0      0        0 eth0

```

---

### Post by SeijiSensei on 2013-10-01
> ```
74.81.XX.XX     0.0.0.0         255.255.255.248 U     0      0        0 eth1
74.81.XX.XX     0.0.0.0         255.255.255.248 U     0      0        0 eth0

```

Well, that cannot be right.  In fact all the routes are duplicated across the interfaces.  

I'd start small.  Get rid of the virtual interfaces for the moment and just set up eth0 and eth1 and make sure they route correctly.  Then start adding the virtuals.

---

### Post by andrew47 on 2013-10-02
Thanks for the suggestion. I have removed everything but eth1 but the problem remains. This is my entire interfaces file...

```
auto eth1
allow-hotplug eth1
iface eth1 inet static
        address 74.81.XX.XX
        netmask 255.255.255.248
        gateway 74.81.XX.XX
```

Results in the error...

```
RTNETLINK answers: File exists
Failed to bring up eth1.

```

and the result of route -n...

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         74.81.XX.XX     0.0.0.0         UG    0      0        0 eth1
0.0.0.0         74.81.XX.XX     0.0.0.0         UG    100    0        0 eth1
10.0.0.0        10.16.XX.XX    255.0.0.0       UG    0      0        0 eth1
10.0.0.0        10.16.XX.XX    255.0.0.0       UG    0      0        0 eth0
10.16.XX.XX    0.0.0.0         255.255.255.248 U     0      0        0 eth0
10.16.XX.XX    0.0.0.0         255.255.255.248 U     0      0        0 eth1
74.81.XX.XX     0.0.0.0         255.255.255.248 U     0      0        0 eth1
74.81.XX.XX     0.0.0.0         255.255.255.248 U     0      0        0 eth0
205.251.XX.XX 0.0.0.0         255.255.255.224 U     0      0        0 eth1
205.251.XX.XX 0.0.0.0         255.255.255.224 U     0      0        0 eth0

```

Why do those routing entries exist in the table if they do not exist in the interfaces file?

---

### Post by andrew47 on 2013-10-02
I believe I have solved the problem by rebooting the machine. Thank you for your assistance.

---

### Post by Ilya80 on 2013-10-02
Have you restarted networking?  Also can try this to clear routing table:```
ip route flush
```

---

