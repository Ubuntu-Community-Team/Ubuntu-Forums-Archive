---
title: "For what iproute2 exist?"
date: 2023-11-11
forum: Networking &amp; Wireless
---

### Post by georgy-trubetkoy-ru74 on 2023-11-11
Which tool should I use for network settings for Ubu/Deb servers?
In the documentation provided by Canonical said to use exactly and only netplan.
But for what in OS the iproute2 exits by default? Who need to use temporary settings at all?
I guess I know where from all this jokes about no-reboot Linux.
Why in ALL distrs Linux still no ONE universal utility for network settings?
What can you recommend for work with network in Debian-based distrs?

---

### Post by TheFu on 2023-11-13
[https://en.wikipedia.org/wiki/The_Cathedral_and_the_Bazaar](https://en.wikipedia.org/wiki/The_Cathedral_and_the_Bazaar) might help explain why Linux provides multiple choices that seem to do similar things to someone looking in from the outside.

Linux isn't authoritarian. It usually is based on merit, so until a clear "best" is known, we often have 2 to 20 options for any specific need.  What is best for me isn't necessarily best for you.

I use netplan since 20.04.  Prior to that, I used the unsupported ifupdown tools. Many of those older tools weren't actually supported since 2011, so for many years, there weren't any fixes for bug or security problems.  

Don't know where you are seeing iproute2
```
$ iproute2
iproute2: command not found
```
It isn't automatically installed on any of my systems.

As for temporary settings ... those behind the scenes commands are called by the netplan process to make the settings we request. They are also handy if we need to test something, especially on a remote system.  I'll often modify network settings on a remote server that can break my access to that system, so 5 minutes later, I want to put back/undo what I tried before, just in case I make a mistake.  That's just one example.  

VPNs are another example.  When I enable my VPN connection, I need to modify the devices, priorities and routing table so ensure nothing leaks outside the VPN tunnel.  Later, say 3 hrs later, when I shutdown the VPN, those temporary settings need to be cleaning removed in the opposite order they were created.

---

### Post by SeijiSensei on 2023-11-13
iproute2 is the package that contains the /bin/ip command. See "man ip" for details.

For instance
```
$ ip route
default via 192.168.100.1 dev eno1 proto dhcp src 192.168.100.86 metric 100 
192.168.100.0/24 dev eno1 proto kernel scope link src 192.168.100.86 metric 100 

```

My system got its IP address, 192.168.100.86, using DHCP. It broadcasts packets to other hosts on the 192.168.100.0/24 network; it sends all other traffic ("the default route") to my router at 192.168.100.1.

"ip addr" returns information about your system's network interfaces and addresses. Some of us old folks still like to use ifconfig for this task :)

---

### Post by TheFu on 2023-11-13
Ah ... I was missing the connection to **ip** command(s) and the iproute2 package.  There are some things to like about ip and somethings are less good than they were previously.

For example, 
```
route -rn

```vs
```
ip route
```

The first created nice, tabular output. With *ip route*, we can almost get the same table, but not quite:  **ip route | column -t**. OTOH, supported and maintained software always beats unsupported, unmaintained software for me, so there isn't any real competition.

---

