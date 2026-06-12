---
title: "No internet connection"
date: 2019-07-03
forum: Networking &amp; Wireless
---

### Post by work79 on 2019-07-03
Ok so I have this problem that i have got windows 10 and ubuntu dual boot, but on ubuntu there is no wired internet.I have tried wireless adapter and it works but the ethernet does'nt work.If I look on my pc from back i can see that there is only red light coming from network card.This problem isnt just in Ubuntu but other distros aswell even in live usb mode.DHCP is enabled. So im asking for help if you now what it is or something like that.Thanks for help.

---

### Post by TheFu on 2019-07-03
Install **lshw**.
run
```
sudo lshw -C network
```
post the output using "code tags".  <---- Advanced Editor # button.

Want to see if the OS even recognizes the network card at all first.  If it does, then some troubleshooting steps are needed: 
[https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) has steps.
ping the router by IP
ping a well-known internet IP 8.8.8.8
ping a well-known internet address like google.com
Check that the routes make sense - route -n

---

### Post by wildmanne39 on 2019-07-03
Moved to Networking and Wireless forum.

---

### Post by work79 on 2019-07-03
Ok so without the wireless adapter the lshw  wont show anything, and if i ping the router or anything else, it shows totally different ip and it says host unreachable:

```
root@work79-desktop:/home/work79# ping 8.8.8.8PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
From 169.254.10.84 icmp_seq=1 Destination Host Unreachable
From 169.254.10.84 icmp_seq=2 Destination Host Unreachable
From 169.254.10.84 icmp_seq=3 Destination Host Unreachable



```

```
root@work79-desktop:/home/work79# route -nKernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         0.0.0.0         0.0.0.0         U     1002   0        0 enp0s7
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 enp0s7



```
strange

---

### Post by TheFu on 2019-07-03
if lshw doesn't show the network card, then you'll need to figure out what exact card it is and manually enable/install the drivers for it.

---

### Post by fragglebliss on 2019-07-04
Quite an unusual problem actually, if it is a driver problem related to ethernet. Usually, one will have problems detecting and using wireless adapters. Ethernet is usually the option which is almost always guaranteed to be detected and working by default and without any further interaction (other than setting IP addresses and other specific network settings).

---

### Post by work79 on 2019-07-05
Yeah, I'm really lost now.

---

### Post by TheFu on 2019-07-05
> **work79 said:**
> Yeah, I'm really lost now.

**Get out the manual**. Look up the exact network card/chip and post it here.  If the machine is  so new on the market that linux drivers don't recognize it, you are living on the "bleeding edge" and will either need to code the driver yourself or wait.  Call the vendor and complain about the lack of Linux support.

If the machine model is 6+ months old, then you'll most likely just need to download a driver package, compile and install it.  

But all of that begins with you determining the exact model of network adaptor.  Seriously, look in the manual.

---

### Post by work79 on 2019-07-07
Ok, but where do i find the name of my network card (on windows)?

---

### Post by work79 on 2019-08-15
Fixed it by purchasing new motherboard.

---

