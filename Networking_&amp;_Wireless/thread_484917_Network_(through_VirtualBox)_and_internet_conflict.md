---
title: "Network (through VirtualBox) and internet conflict in Feisty Fawn"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by lhansen on 2007-06-26
Hi,

I am new to Linux and have recently installed Feisty as my primary OS. Once installed, I setup a virtual machine using VirtualBox and installed Windows XP Pro. I read a nifty article on how to publish windows programs from my VM to my linux desktop using 2X applicationserver. In order to do this I need to setup a host controlled network on the VM. In order to get this to work I had to make some changes to... 

etc/network/interfaces

Once I made these changes I was able to run the VM with a host controlled network and publish to Ubuntu no problem, but my internet stopped working. 

Symptoms (wirless or wired ): appears connected (using network manager), DNS appears correct, IP address is established, can't ping my wireless router or any other website, and no internet function at all.

In order to test the problem I commented out (i.e., #) the inserted changes in etc/network/interfaces. After a reboot everything works perfectly. Both wired and wireless operate smooth, and I have full internet capability. Of course, with out those above mentioned changes to etc/network/interfaces I can no longer publish programs from my VM.

So... How do I get the changes to etc/network/interfaces to not affect the operation of my internet?

Any help would be greatly appreciated.



Here is what my interfaces file looks like with the changes included (internet does not work ut publishing does):




# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

# added for host control
auto tap0
iface tap0 inet manual
up ifconfig $IFACE 0.0.0.0 up
down ifconfig $IFACE down
tunctl_user lhansen

auto br0
iface br0 inet dhcp
bridge_ports all tap0



And here is what it looks like with my changes commented out (internet works but host control through VirtualBox does not):



# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

# added for host control
#auto tap0
#iface tap0 inet manual
# up ifconfig $IFACE 0.0.0.0 up
# down ifconfig $IFACE down
# tunctl_user lhansen

#auto br0
#iface br0 inet dhcp
# bridge_ports all tap0

---

### Post by jcrow on 2007-07-10
I have the same problem, but it is intermittent. Can someone help me? I took out the tap0 in the last line and rebooted and I got my internet back, but the VM does not work. 

Thanks

---

