---
title: "wired static local ip address"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by jgrabarc on 2008-11-12
I've googled this and come up with a lot of results but most of those were just for an internet static ip address (not just local) or for a previous version of ubuntu, I'm running 8.10(desktop) and a complete newb as in first time i installed it ever.

i have a linksys router and i am trying to set up a static local ip address for a wired computer connection.  

there are also 2 wireless laptops(windows) on the network who have dynamic ip address's this is because the laptops are used on multiple networks and it is a pain to reset the network settings every time you leave the network.

I had this all set up in windows but decided to switch my wired connection to Linux and use LAMP instead of WAMP

so basically I'm trying to get my wired desktop connection to always be 192.168.1.125 so when i do port forwarding in my router it always goes to that computer in ubuntu 8.10

Any help would be greatly appreciated,
John

p.s. this installation of ubuntu is the one right off of there site(default settings) nothing fancy since I'm attempting to learn it right know i am sticking to the absolute basic except it is the 64bit version

---

### Post by gps57 on 2008-11-20
I am trying to do the exact same thing except I am running ubuntu 8.04 desktop.  I just started searching for some information on how to do it.  If I figure it out, I'll post what I did here.

I'll also be watching here for solution.  Good luck.

-gps

---

### Post by handydan918 on 2008-11-20
Most routers allow you to assign a "reserved" ip address to a host based on the MAC address of the NIC in the host. While this is techically different from a true "static" ip, it serves the purpose. The machine in question always has the same ip...

Check thru your router interface and see if you find such an option.

---

### Post by cariboo on 2008-11-20
You can set you static ip address in /etc/network/interfaces. I have done the same on my server, but I had disable the dhcp client, as it still set a dynamic ip address. to set a static ip address, at the prompt type:

```
sudo nano /etc/network/intrefaces
```

You should edit the file to look something like this:

```
cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.1.200
    netmask 255.255.255.0
    broadcast 192.168.1.255
    gateway	192.168.1.1
```

Substitute your preffered ip addres and gateway, press Ctrl-o to save and Ctrl-x to exit.

I just uninstalled dhcp3-client to stop dhcp, restart the network and you're done:

```
sudo /etc/init.d/networking restart
```

Jim

---

