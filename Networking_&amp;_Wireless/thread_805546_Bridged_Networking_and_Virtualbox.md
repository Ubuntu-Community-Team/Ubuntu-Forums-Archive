---
title: "Bridged Networking and Virtualbox"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by gmclachl on 2008-05-24
Hi there,
 I have been trying to set up bridged network (wireless) for virtualbox following this guide.

[https://help.ubuntu.com/community/VirtualBox#head-af51dcc9d72523d76717d072610694dbb2dbe2e0](https://help.ubuntu.com/community/VirtualBox#head-af51dcc9d72523d76717d072610694dbb2dbe2e0)

However I can't get it fully working. I can ping the os within the virtual machine from the  host and my router says that the  vm machine is connected to the network, but I can't ping anything from the vm itself. I keep getting a "Network Unreachable" error. 

Thanks
George

---

### Post by bluefrog on 2008-05-24
follow virtualbox help and it will work (click help in virtualbox window and look for host network. Changing group owner of /dev/net/tun is stupid. just add your user to uml-net group as suggested by virtualbox help.
as for wifi host networking, the way described there is dodgy.

another thing I noticed which is funny in the howto you mention, sudo gpasswd -a `whoami` vboxusers is going to add root to the vboxusers, you don't want/need to run virtualbox as root.

---

### Post by gmclachl on 2008-05-26
I managed to get it working, I had made a mistake with the IP addresses I had assigned the same IP to my virtual card and the one in the VM.

George

---

