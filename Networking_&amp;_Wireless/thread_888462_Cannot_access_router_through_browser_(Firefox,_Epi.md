---
title: "Cannot access router through browser (Firefox, Epiphany, Opera, etc) in Ubuntu"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by vkingpele on 2008-08-13
My computer is running the latest Ubuntu distro, but I cannot access my router through any of the browsers. Any suggestions? It is a wired connection. Using a windows laptop I can access the router wired and wirelessly through its IP address 192.168.1.1, but cannot reach it when trying to connect through ubuntu on a wired connection. What's up with that? Any help is greatly appreciated. Thanks.

UPDATE - First step: attempt a router reset. All good now.

---

### Post by caljohnsmith on 2008-08-13
In Ubuntu, can you access the internet and websites OK, but just not your router? What is the error you get when you go to [http://192.168.1.1](http://192.168.1.1) in Firefox in Ubuntu? Also, try pinging it:
```
ping -c3 192.168.1.1
```
Does that return a response? And what is the output of:
```
route -n
```

---

### Post by vkingpele on 2008-08-13
I am actually not hooked up to the internet on my desktop. It's just plugged into the router to allow me to send files across the network. File transfers work fine so the router is doing its job (Routing). 

Ping -c3 192.168.1.1 returns 
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

From 169.254.5.32 icmp_seq=1 Destination Host Unreachable

From 169.254.5.32 icmp_seq=2 Destination Host Unreachable

From 169.254.5.32 icmp_seq=3 Destination Host Unreachable



--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2010ms
, pipe 3

Route -n returns
IP routing table  

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0

0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0

---

### Post by jimv on 2008-08-13
Wow, nothing should be working on that machine as far as networking goes.  A 169 address is a self-assigned address that basically means no address was assigned to that adapter via DHCP or manually.

What's in /etc/network/interfaces

---

### Post by caljohnsmith on 2008-08-13
I agree with Jimv, I'm having a hard time believing your networking is really working. How about also posting:
```
ifconfig
iwconfig
```

---

### Post by vkingpele on 2008-08-16
Hmmmm seems it was not a Ubuntu problem after all. I recently installed DD-WRT firmware on my router and was trying to set it up to connect to a wireless router in the neighborhood. I must have monkeyed with the wrong settings. Solution - Reset the router. Now it works. Thanks for the help though. I'll add the routing keywords to my lists of useful commands.

---

