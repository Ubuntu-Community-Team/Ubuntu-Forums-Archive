---
title: "Domains are not being resolved"
date: 2017-03-26
forum: Networking &amp; Wireless
---

### Post by 4thVariety on 2017-03-26
Ubuntu 16.04 Desktop (all updates)
two network cards (both have the error at the same time)
error will go away after init 0 and turning the computer back on.
physical machine

From time to time, the computer will stop resolving domain names. Be it Firefox, or apt-get, no IPs are returned when an address is entered. Ping to the IP still works fine. If I grep to see which DNS is being used, it is the right one (my router). If I use the Ubuntu graphical interface to add 8.8.8.8, nothing changes. At first I wanted to blame one or two websites and their popups, but the error is too inconsistent to blame any specific site.

The one thing that does happens is within the graphical manager for the network interface. Instead of just showing "Cable-Network-Connection 1" and 2, there will be a third and fourth entry with the Ubuntu name of the interfaces, i.e. en3s0 and en5s0. Even deleting all entries and building them from scratch will not fix the error. Deleting everything and adding an init 6 to it will.

I am open to suggestions where to look for the source of this error, or how to manually force a DNS back into the system using the terminal.

---

### Post by alexandari on 2017-03-28
The DNS resolution is located in the file /etc/resolv.conf . There you will find entries like:
```
 nameserver 8.8.8.8 
```
or maybe
```
 nameserver 192.168.1.1 
```

the second one is your router. You can edit that file in order to have resolvability of domain names.

---

### Post by vidtek on 2017-03-28
> **4thVariety said:**
> Ubuntu 16.04 Desktop (all updates)
two network cards (both have the error at the same time)
error will go away after init 0 and turning the computer back on.
physical machine

From time to time, the computer will stop resolving domain names. Be it Firefox, or apt-get, no IPs are returned when an address is entered. Ping to the IP still works fine. If I grep to see which DNS is being used, it is the right one (my router). If I use the Ubuntu graphical interface to add 8.8.8.8, nothing changes. At first I wanted to blame one or two websites and their popups, but the error is too inconsistent to blame any specific site.

The one thing that does happens is within the graphical manager for the network interface. Instead of just showing "Cable-Network-Connection 1" and 2, there will be a third and fourth entry with the Ubuntu name of the interfaces, i.e. en3s0 and en5s0. Even deleting all entries and building them from scratch will not fix the error. Deleting everything and adding an init 6 to it will.

I am open to suggestions where to look for the source of this error, or how to manually force a DNS back into the system using the terminal.

4th- Do the other poster's advice, but are you running any virtual machines? That puts the virtual adaptors into the gui interface.  How many physical adaptors do you have?  Try using a static ip address and set your own dns domains first try your own ISP's dns's then a generral one to see if it makes a difference.
Tony

---

