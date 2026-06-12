---
title: "Error in network definition: unknown key 'virtual-ethernets'"
date: 2024-03-12
forum: Networking &amp; Wireless
---

### Post by olutayo on 2024-03-12
I got error of "unknown key" when I used "virtual-ethernets' interface type:

* My laptop is on Ubuntu 22.04

virtual-ethernets:
   veth-starlink0:
      peer: veth-starlink1
   veth-starlink1:
      peer: veth-starlink0
   veth-mtn0:
      peer: veth-mtn1
   veth-mtn1:
      peer: veth-mtn0

What I am missing?

---

