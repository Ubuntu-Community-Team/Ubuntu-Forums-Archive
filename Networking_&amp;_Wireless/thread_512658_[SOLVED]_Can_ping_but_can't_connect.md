---
title: "[SOLVED] Can ping but can't connect"
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by Runiko on 2007-07-29
I am using a wired broadband connection to the internet using my ASUS motherboard's built-in SiS NIC. When I first installed Ubuntu 7.04 (dual-boot with windows), I could download all the updates and software I desired. 

One day later, I boot it to Ubuntu and I can only access one out of ten web sites I try to visit and can't wget anything. Half of the sites I can't get to I can ping, and the other half I can't. When I traceroute a ping to an inaccessible site (like ubuntuforums.org) the connection goes out to the sea backbone and just stops dead.

The weird thing is that I can access "nearby" and "universal" sites, like my local college mail (I'm not accessing from on campus; I have my own broadband by CableOne) and Google.

I tried booting the Ubuntu Live install CD, but I couldn't browse with it either, which is bizarre since I did while it was installing the first time.

What on earth is going on??? Help!

---

### Post by bbzbryce on 2007-07-29
> **Runiko said:**
> What on earth is going on??? Help!

Perhaps the DNS from your ISP is currently messed up. Can you connect to servers fine via their IP addresses?

---

### Post by Runiko on 2007-07-29
Sorry, I forgot to mention three things:

1. Windows can connect fine, just like normal. Other computers using my router (macs) are having zero problems.

2. I tried disabling ipv6, but that made no difference.

3. when I was pinging one site, a ping error came back saying the IP for AT&T had filtered the packet. Maybe that was just a glitch, or... ???

---

### Post by Runiko on 2007-07-29
I HAVE FOUND THE SOLUTION!!!

Someone needs to put this in a FAQ somewhere easier to find:

Simply reduce the MTU of your eth0 (or whatever) connection, like this:

typing
```
ifconfig eth0
```

showed several lines of text, one of which said:

```
 UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
```

The problem was that an MTU of 1500 tended to be just big enough to split and get dropped. so simply type:

```
sudo ifconfig eth0 tmu 1492
```

exactly one byte less that this maximum. Everything is happy now! Get everyone with this problem to try this!

---

