---
title: "Ubuntu libvirt qemu-kvm Networking"
date: 2019-01-24
forum: Networking &amp; Wireless
---

### Post by qombi on 2019-01-24
Hello, 

I have been browsing the internet and various forums including this one. I think I have an idea on how I can configure my libvirt qemu-kvm host server to allow separation of a guest on a DMZ subnet and a guest inside subnet. I am hoping an expert will confirm I am going down the correct path or point me to a better path to take. My background is in networking but not linux networking. I am familiar with Cisco, with knowledge in 801.1q, VLANs, etc. 
Hardware involved: 

PFSense FW with a router on a stick interface configured with the default gateways for dmz eth1.20 and inside eth1.10 used by libvirt qemu-kvm guest. 

Ubuntu Server w/ Libvirt Qemu-KVM installed 1 physical interface 



To accomplish what I am wanting to do from what I have read:


Create two subinterfaces say physical interface is eth1, so inside vlan 10 eth1.10 and dmz vlan 20 eth1.20
Create two virtual bridges(switches), connect guest DMZ guest virtual interface and inside guest virtual interface to their respective bridges, also add the subinterfaces created previous to their respective bridge. 
Install guest and assign IPs in the respective networks, no IP on subinterfaces created eth1 treated as a trunk port. 

Am I on the right track? Thanks for any guidance you may be able to give to a linux newbie. If you can point me in the right direction I am sure I can research the steps needed to configured. I wish not to start down the incorrect path from the start if there is a more proper way of doing this.

---

### Post by qombi on 2019-01-26
Am I going down the wrong path or the correct one? Should I be thinking of this in a different way? "linux bridge" I assume isn't capable of 802.1q so this is the reason for sub interfaces of the physical interface and multiple linux bridges for isolation. Is this a wrong assumption? Can you have 1 linux bridge that supports 802.1q connected the virtual interfaces of the guest and the 1 physical interface of the host and configure the physical interface as a trunk?

---

