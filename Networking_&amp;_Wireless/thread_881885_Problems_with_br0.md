---
title: "Problems with br0"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by malif on 2008-08-06
I have created a br0 with eth3 and eth4 on a machine. It needs to be a transparent bridge and it is doing so wonderfully... the only problem is for some reason one of my eth's keeps picking up and IP address and that kills the bridge (to some extent, the packets still pass through the bridge just the machine cannot access the internet) sadly enough I think I found the problem to be the dreaded nm-applet trying to fix my "broken" eth3-4. I have also do a little bit of prodding and if I type

sudo ifconfig eth4 down

then the applet will leave me alone (actually it will create a eth3:avai with a 169 IP address but the internet still works great) 

So really what I am asking is where can I add that command to ubuntu startup in such as to run before user login and after the nm-applet has run the first time. 

Yes I know that removing nm-applet would fix it but I can't (not that I don't know how just that a situation prevents it)

---

### Post by SpaceTeddy on 2008-08-07
can you please post the config of you network configuration (preferably the /etc/network/interfaces)

thanks

---

### Post by malif on 2008-08-07
Here it is  

# /etc/network/interfaces file
 #
 # Loopback interface
 auto lo
      iface lo inet loopback
 #
 # Configure the bridge
 auto br0
 iface br0 inet static
      address 10.55.2.150
      netmask 255.255.0.0
      broadcast 10.55.255.255
      gateway 10.55.0.1
    # Ports you want to add to your bridge
    bridge_ports eth3 eth4
    # Time to wait before loading the bridge
    bridge_maxwait 0

---

### Post by SpaceTeddy on 2008-08-07
for network manager to ignore devices and NOT try to automatically obtain an ip, you need to specify them in the interfaces file. Then NM will ignore the. 
Also, when you are working with bridges, the bridges network devices should have NO ip configuration and be in promisc mode. As far as i can see in your config that is not done. 

Try adding these lines to your /etc/network/interfaces

```
auto eth3
iface eth3 inet manual
up ifconfig $IFACE 0.0.0.0 up
up ip link set $IFACE promisc on
down ip link set $IFACE promisc off
down ifconfig $IFACE down 

auto eth4
iface eth4 inet manual
up ifconfig $IFACE 0.0.0.0 up
up ip link set $IFACE promisc on
down ip link set $IFACE promisc off
down ifconfig $IFACE down
```

These lines will make sure that the network interfaces eth3 and eth4 are configured manually, will not be picked up by NM, will not obtain any IP configuration and are in promisc mode.

i think that should do the trick :)

---

### Post by joeyoung25 on 2011-08-16
Is this still the case for Ubuntu 10.04?? I am trying to get 2 nics to bridge so they are redundant. 

Will this work?? I only have 2 wired nics and of course the l0. No wireless.


# Loopback interface
auto lo
iface lo inet loopback
#
# Configure the bridge
auto br0
iface br0 inet static
address 192.168.10.29
netmask 255.255.255.0
broadcast 192.168.10.255
gateway 192.168.10.254
# Ports you want to add to your bridge
bridge_ports eth0 eth1
# Time to wait before loading the bridge
bridge_maxwait 0

auto eth0
iface eth0 inet manual
up ifconfig $IFACE 0.0.0.0 up
up ip link set $IFACE promisc on
down ip link set $IFACE promisc off
down ifconfig $IFACE down 

auto eth1
iface eth1 inet manual
up ifconfig $IFACE 0.0.0.0 up
up ip link set $IFACE promisc on
down ip link set $IFACE promisc off
down ifconfig $IFACE down

---

