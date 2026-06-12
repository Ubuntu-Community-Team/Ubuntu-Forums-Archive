---
title: "Feisty wirelss connects but no internet"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by lhansen on 2007-06-25
Hi All, 

I just switched over to Feist, my first time in Linux, and I am having some wireless issues. At first my wireless worked well following a tutorial in the ubuntu forums. Since then I have set up a VM running Windows XP wtih VirtualBox that has a host network so I can publish windows programs to Feisty. Since then my internet has ceased to function.

Problem: 

Everything suggests I am connected to my wireless router. I have an appropriate IP address, the DNS appears in order, and I have disabled ipv6. After all of this firefox won't load anything and neither will synaptec. I appear connected, but I don't get anything if I ping the route.

Possible causes:

I am running the WiFi radar software, not sure if this has much influence.
I did add several lines of code to my interfaces file in order to get the host network on the VM running.
These are:

auto tap0
iface tap0 inet manual
up ifconfig $IFACE 0.0.0.0 up
down ifconfig $IFACE down
tunctl_user vboxuser

auto br0
iface br0 inet dhcp
bridge_ports all tap0

I'm not sure if these could have caused the problem. Any thoughts out there?

---

### Post by acadiansteph on 2007-06-25
In Edgy you needed wifi-radar. But with Feisty the Network Manager takes cares of the wireless. You should remove wifi-radar because there is a conflict with both programs. After this reboot your laptop and the network manager should identify you wifi networks. If it does; choose your network connnect to it and then it will ask for a password to connect and so on... The network manager icon should be located at the top right corner next to the shut down icon. If you are able to connect  wirelessly, you should see blue bars (showing wireless quality) and a green bar should your connection properties. Hope this helps!!!

---

### Post by lhansen on 2007-06-25
Hmm... that didn't seem to work. I tried both Network Manager and WiFi Radar by themselves with the same result. Solid connection but no internet data transfer.

I did go back into my 'interfaces' file and comment out the amendments I made in order to setup a host network on with my Windows VM. The result... perfectly functioning internet, both wireless and wired.

So, how do I get my amendments to not affect my internet connection?



Here is what my interfaces file looks like with the amendments (internet does not work):




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



And here is what it looks like with my amendments commented (internet works):



# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

# added for host control
#auto tap0
#iface tap0 inet manual
 #   up ifconfig $IFACE 0.0.0.0 up
  #  down ifconfig $IFACE down
   # tunctl_user lhansen

#auto br0
#iface br0 inet dhcp
 #   bridge_ports all tap0

---

### Post by acadiansteph on 2007-06-25
I wish I could help you more, but I am not familiar with changing comments in the interface file. I truly hope you get wireless...Take care, Steph

---

### Post by dominicedmonds on 2007-11-07
You might find this useful: [http://ubuntuforums.org/showthread.php?t=543356](http://ubuntuforums.org/showthread.php?t=543356). ALthough I don't know about radar and such.

---

