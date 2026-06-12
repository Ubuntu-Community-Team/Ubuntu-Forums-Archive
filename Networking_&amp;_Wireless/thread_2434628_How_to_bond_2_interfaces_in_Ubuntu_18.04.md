---
title: "How to bond 2 interfaces in Ubuntu 18.04"
date: 2020-01-08
forum: Networking &amp; Wireless
---

### Post by goudeuk on 2020-01-08
Hello

I'm new to Ubuntu but not Linux. I am struggling to understand how to do NIC bonding on a server mainly because I've never done it before, not even in other Linux systems. The version I am using is **18.04.3. **and (please correct me if I am wrong) the way I have understood NIC bonding is that once the bonding configuration is applied the system creates a virtual interface with a virtual MAC address. Many guides online describe which file to edit which also confused me because the filenames differ however one common instruction is that the config file it needs to be inside */etc/netplan* and end with **.yaml**

I have two interfaces **eno1** and **enp13s0. **At the moment **eno1** is live and pinging, **enp13s0 **is not patched. My question is which IP address should I use in the bonding config file? Should I use the one assigned to **eno1** ? For example this link here is probably what I need: [https://askubuntu.com/questions/1033531/how-can-i-create-a-bond-interface-in-ubuntu-18-04](https://askubuntu.com/questions/1033531/how-can-i-create-a-bond-interface-in-ubuntu-18-04) 

In his answer he provides the bonding config file created by Ubuntu during installation. then he updates his thread saying that if you want the bonding config to survive reboot then you need to create a new file and add these lines to it:

> network:
   bonds:
       bond0:
           addresses: [192.168.0.8/24]
           gateway4: 192.168.0.1
           nameservers:
              addresses: [8.8.8.8,8.8.4.4]
           interfaces:
           - enp5s4
           - enp5s9
           - enp64s0

When I go and edit my ***.yaml** file, which IP should I use? 

Thank you

---

### Post by nick-kostov on 2020-06-03
[COLOR=#000000]Check my [/COLOR][https://ubuntuforums.org/showthread....hlight=bonding]("https://ubuntuforums.org/showthread.php?t=2444718&highlight=bonding")[COLOR=#000000] .  
First check [/COLOR][https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

---

