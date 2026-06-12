---
title: "Need help connecting to the internet in a virtual machine using ubuntu 9.04"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by ABagOfFritos on 2009-08-15
I have ubuntu installed on a virtual machine using VMware, I downloaded the free beginners guide but the steps given are not helping me.

I have gone into the Network Connections area and input the information for the network I am currently at, but it will not connect to the internet.

I do not get the little icon in the top right with the 2 computers that it should get though, and am unable to find a "Network Manager."

Ubuntu 9.04, Kernel 2.6.28-11-generic
^^ This is where I am booting from, trying to connect to the internet to download and install updates, as I had problems with an initial update attempt where the machine seemed to freeze mid-update.

I need help connecting this thing to the internet, please help in any way you can.

---

### Post by john stiles on 2009-08-15
I think you will find that most of us are using virtualbox, hence the lack of support coming. 9.04 in fact any OS I have tried in virtualbox links automatically to the net. If no help or solution is forthcoming consider this an end option.

---

### Post by JKyleOKC on 2009-08-15
What virtualization software, and host system, are you running? My experience here with VMWare Server and with Virtualbox indicates that you have to specify the type of network connection when creating the virtual machine, although both allow you to change its configuration afterward. Initially, I had a problem similar to yours, but changing the virtual machine's network configurations to "bridged" took care of everything for me. However I'm running Xubuntu as the host system, and WinXP as the virtual machine, which may be the exact opposite of your configuration...

---

### Post by ABagOfFritos on 2009-08-15
> **JKyleOKC said:**
> What virtualization software, and host system, are you running? My experience here with VMWare Server and with Virtualbox indicates that you have to specify the type of network connection when creating the virtual machine, although both allow you to change its configuration afterward. Initially, I had a problem similar to yours, but changing the virtual machine's network configurations to "bridged" took care of everything for me. However I'm running Xubuntu as the host system, and WinXP as the virtual machine, which may be the exact opposite of your configuration...

Yes, this is the opposite for me, I am using Windows Vista as the host with Ubuntu on the virtual machine.

Currently the VM is set to NAT for the network adapter.  Will bridged work with a wireless connection?
I'll test it out in the meantime.

---

### Post by JKyleOKC on 2009-08-15
> **ABagOfFritos said:**
> Currently the VM is set to NAT for the network adapter.  Will bridged work with a wireless connection?
I'll test it out in the meantime.I don't know, since I've never managed to get my one wireless rig working with Xubuntu (or, for that matter, to get any version of Linux working on that laptop!). I would expect it ro work, however, since it basically just passes all the data through from the VM to the host's drivers. You might have problems getting Ubuntu to connect to the wireless router however...

---

### Post by ABagOfFritos on 2009-08-15
> **JKyleOKC said:**
> I don't know, since I've never managed to get my one wireless rig working with Xubuntu (or, for that matter, to get any version of Linux working on that laptop!). I would expect it ro work, however, since it basically just passes all the data through from the VM to the host's drivers. You might have problems getting Ubuntu to connect to the wireless router however...

I guess I'll try wiring up the laptop when I want to use the VM.

---

