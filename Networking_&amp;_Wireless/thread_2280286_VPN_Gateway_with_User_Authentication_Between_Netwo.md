---
title: "VPN Gateway with User Authentication Between Networks"
date: 2015-05-29
forum: Networking &amp; Wireless
---

### Post by TimothyGreer on 2015-05-29
Hi All,

Ok, So we have a Cisco ASA 5500 that we currently use to separate two portions of our network with a VPN tunnel, but its old hardware and has only 100 Mbs ethernet connections.  The networks it connects are in the same building, so I want to try and cut out this bottleneck for when development copies huge files.

Setting up VPN is something I've done before, just not in a Linux system, so some of my terminology might be wrong here.

We use VMware vSphere, so I intend to just setup an Ubuntu VM and give it NICs on the VLANs for the networks I want to connect.

I'm wondering if there is a way to use OpenVPN or some other software to connect the two networks, but only when someone has logged in and only for the machine they loged in from. I think I'm supposed to use Bridged VPN mode, but not sure if that right or how to make it not be 'always on'

IE John Doe connects from his Windows machine and then that machine has VPN access to the network on the other side of the Ubuntu VM.

I'm fine if I have to create some sort of user access list on the Ubuntu VM, but a way to use an Active Directory Group for control is a plus, rest f the environment is Windows based.

Also I'm looking into separating out some of the machines on the destination network into seperate VLANs for further security between the VMs, so being able to log in once and get to multiple target VLANs is a plus.  All the VLANs have separate sub nets.

Any help or advice is greatly appreciated, even if its a not possible or just the name of some software packages to check out.

I'll try to elaborate on any part that needs further clarification.

---

