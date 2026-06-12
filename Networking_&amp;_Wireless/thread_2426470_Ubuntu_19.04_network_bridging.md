---
title: "Ubuntu 19.04 network bridging"
date: 2019-09-09
forum: Networking &amp; Wireless
---

### Post by michaels24082 on 2019-09-09
Hello all,

I am new to Ubuntu and trying to create a network bridge that will assign multiple IP addresses from my NIC/router to VM's. I have search and found several solutions using both the /etc/network/interfaces file and the /etc/netplan/*** files. These solutions result in creating a new bridged network br0 that is supposed to piggy back on my NIC device named enp6s0. All examples say that enp6s0 is supposed to not grab the IP address and br0 should, however in all cases enp6s0 grabs the ip address. Most of these instructions I have found are for Ubuntu 18.04 and earlier but do not seem to work on 19.04. Can anyone please direct me to the proper instructions for setting up a this type of bridge on 19.04. I know its possible as VMware does it.

Thanks in advance,
Mike

---

### Post by pcfan1234 on 2019-09-10
So you like to have direct access from the VMs to you network?
In Virtualbox you have the option to set the network adapter to bridge mode.
This bridges the virtual NIC with your NIC so you get the IP directly from your router's DHCP.
In the VM you can set up more network adapters if you need more than one.
Is that what you want?

A bridge in Ubuntu is for connecting 2 physical networks (the computer acts like a switch/hub)

---

### Post by michaels24082 on 2019-09-26
I do not want to use virtual box. I am using Qemu/KVM. So the bridging has to come from linux. I have accidentally started another thread with more specific details.

---

