---
title: "create bridge network through gui"
date: 2023-02-20
forum: Networking &amp; Wireless
---

### Post by zorin1 on 2023-02-20
I’m hoping that someone can give me some pointers in setting up a bridge network on Kubuntu 22.10.  My motherboard has two Ethernet adapters.  Realtek is on enp6s0 and the Intel is on enp7s0.  I would like to create a bridge on enp6s0 the Realtek adapter for my VMs.   
 
 
 My problem is that I can’t seem to setup the bridge through the Network GUI interface.  I got this working at one point but now I don’t remember how to do it.  I think it had something to do with setting a clone Mac Address.  But that does not seem to work now.   
 
 
 I thought that maybe I could just create some configuration files but then I could not figure out if I’m using Netplan or NetowrkManager.  It would be helpful if someone could tell which network manager we are using in Kubuntu 22.10.   
 
 
 I would really like the steps on how to setup a bridge with the Network GUI interface.  Do I need to create 2 wired Ethernet connections first and then add the bridge?
 
 
 When I create the bridge connection, so I need to set the “Bridged connections” and should the same name as when I created Wired Ethernet connection?   
 
 
 Any help would be very appreciated.

---

### Post by TheFu on 2023-02-21
You need to use netplan if you want a bridge.  There are examples in the netplan documentation.  Best to completely remove network-manager on a system with a non-trivial network configuration.  netplan.io is the website with the documentation AND examples.

There isn't any GUI that I've ever year about.

---

