---
title: "Setting up network inside VMware with Ubuntu 7.10"
date: 2008-03-06
forum: Networking &amp; Wireless
---

### Post by sNNooPY on 2008-03-06
I need to be able to connect to the internet and to my host computer (e.g. access my partitions from inside ubuntu in vmware).
I run VMware workstation on an IBM T60p laptop, and I connect to different wireless networks during the day.

At home, internet works...as is. that is , inside VMware, network connection is NAT and I haven't touched a thing inside Ubuntu.
however when I connect to some other wireless network (e.g. at college), there's no net connection inside ubuntu. :(

what's the most efficient way to establish:

1. a relabile network connection from within VMware. NAT? bridged? what? what needs to be done inside ubuntu to make things work?
2. the easiest way to access files on my partitions (WinXP machine)

---

### Post by SpaceTeddy on 2008-03-06
> **sNNooPY said:**
> 1. a relabile network connection from within VMware. NAT? bridged? what? what needs to be done inside ubuntu to make things work?

i have vmware server running - i remember that some time back you had to recompile the vmware modules yourself before they acctually worked properly. But my computer has been running so long i don't remeber if i had to do that with gutsy or not (i definetly did that in feisty).
As for the connection, i always use NAT. That hides the virtual machine inside mine, but gives me all the network access i need. Especially if you have to through VPN it is advisable to do this, since othewise you'd need to connect your vm to the VPN aswell
> **sNNooPY said:**
> 
2. the easiest way to access files on my partitions (WinXP machine)
my guest is windows - i gave it a share and created a link to it on my desktop - drag and drop into that folder from there on...

---

### Post by eheck on 2008-03-14
> **SpaceTeddy said:**
> i have vmware server running - i remember that some time back you had to recompile the vmware modules yourself before they acctually worked properly. But my computer has been running so long i don't remeber if i had to do that with gutsy or not (i definetly did that in feisty).
AFAIK if you have do that or not depends on what your vmx configuration says. If there's "virtualDev=vmxnet" in it for example you need the vmxnet module to use the network. This in turn comes with vmware tools but needs to be recompiled to match the kernel.
I always run guest VMs without any "virtualDev" configuration. Then the pcnet32 module is used. Which works for me.

---

