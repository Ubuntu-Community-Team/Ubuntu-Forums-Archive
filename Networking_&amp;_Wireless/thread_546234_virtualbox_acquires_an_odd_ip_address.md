---
title: "virtualbox acquires an odd ip address"
date: 2007-09-08
forum: Networking &amp; Wireless
---

### Post by mmoalem on 2007-09-08
hi there all  - not sure what i'm doing wrong... i am running virtualbox on feisty host. i have 2 guest machines one xp and one ubuntu. I am using NAT on both and both connects to the internet without problem. however their ip address is a bit odd... my home network is in the range of 10.0.0.1-20 (set in the ADSL modem router) and my other 2 pcs including the ubuntu host acquire addresses within this range using DHCP. the guest machines however have the address 10.0.2.10 (both get the same)
it seems a bit odd to me as the router is instructed to only accept connections on the set range...
hope i made myself clear...:)
cheers
michel

---

### Post by noob12 on 2007-09-08
These are virtual interfaces in the guest machines.  The addresses are just constructed.  They could basically be anything.  They are usually bridged to one of the real interfaces on your physical host; that address is assigned by DHCP from your router in the specified range.

---

### Post by Jose Catre-Vandis on 2007-09-08
If you are using NAT, VirtualBox provides it's own subnet and dhcp server for this, which is unrelated to your real network. You need to do bridging and create new interfaces, under "Host Interface" in order to join your real network.

If it helps, under NAT, VBox uses the subnet: 10.0.2.0.
The gateway address is: 10.0.2.2
The DNS Server is: 10.0.2.3

You can set a static IP fpr your vm if you wish.

---

### Post by mmoalem on 2007-09-09
thank you both, thats explains alot. now, how do i set static ip to the range of the real netowrk? my main reason is to do port forwarding on my router to the vm so i can run run an http server inside virtualbox keeping the rest of the network out of sight to the outside world
also if i want to run utorrent inside a vm which also need port forwarding on the router
cheers
michel

---

