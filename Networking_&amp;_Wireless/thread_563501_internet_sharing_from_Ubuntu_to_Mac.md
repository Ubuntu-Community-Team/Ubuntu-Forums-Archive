---
title: "internet sharing from Ubuntu to Mac"
date: 2007-09-30
forum: Networking &amp; Wireless
---

### Post by wayanwolvie on 2007-09-30
Hi,
I have a Ubuntu 7.04 machine connected to my campus LAN (which where I get the internet connection). Now I have a macbook, and I want it to share the internet connection through my Ubuntu. I've bought a secondary Ethernet adapter, but I don't know how to set it up for internet connection sharing. Can somebody tell me how to do it?

---

### Post by helgman on 2007-10-04
There seems to be quit a few questions about this right now so if this works for you, find someone else with the same problem and direct them here. If not, please let me know so we can fix the problem.

The simplest way I know of doing this is as follows:

*** * * SETTING UP THE "ROUTER" * * ***

We have to Ethernet cards attached to our computer.

**/etc/network/interfaces** might look something like this:
```
auto eth0
iface eth0 inet static
   address 192.168.1.5
   netmask 255.255.255.0
   gateway 192.168.1.1

auto eth1
iface eth1 inet static
   address 192.168.2.1
   netmask 255.255.255.0
```

Please note that you can use dhcp on eth0 but please don't on eth1. To know if forwarding packages from one interface to another is enabled use:
```
cat /proc/sys/net/ipv4/ip_forward
```
If it echos a 0 it's not if it echoes a 1 then it is. To make it temporary forward packages (until next reboot):
```
echo 1 > /proc/sys/net/ipv4/ip_forward
```
This is good for temporary testing and just playing around, but if you are going to power of the machine ... don't forget to turn it on again when you power up (if you want forwarding). To make it permanent you have to edit **/etc/sysctl.conf**.  Open it up and look for THIS line:
```
net.ipv4.ip_forward
```
You might find a line saying *#net.ipv4.conf.default.forwarding=1* but just ignore it. I can't seem to get it to work as per the comment above it. For more information [look here](https://bugs.launchpad.net/ubuntu/+source/procps/+bug/84537).

For now I'm sticking with the code below:
```
net.ipv4.ip_forward = 1
```
If you can't find it in your **sysctl.conf** then just add it, or go for the workaround in the link above (I haven't tried it).

When the editing is done run the following command:
```
sudo sysctl -p /etc/sysctl.conf
```
and now the forwarding should be enabled.

So far so good. What we have done now is enable forwarding in the Ubuntu machine so that it acts like a router, connecting the networks on eth0 and eth1. If eth0 is connected to a "public" network then your private addresses on eth1 (and the computer(s) connected to it) will not be processes as they should when they leave your Ubuntu computer (your Ubuntu computer will have no have this problem). So you need to implement a Network Address Translation (NAT) ([Wikipedia](http://en.wikipedia.org/wiki/Network_Address_Translation)) solution on your eth0.

** * * ENABLE NAT ON THE "ROUTER" * * **

I'm not sure if all the steps below are needed and I know there are other ways to do it - but this is the setup I used the last time I used my laptop as a router (with NAT):
```
modprobe iptables_nat
modprobe ip_conntrack
modprobe ip_conntrack_ftp
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```

Maybe someone can give some feedback on the first three lines, if not then just stick with them for now. The last line tells the computer to use it's own IP address for eth0 when it send packages from eth1 out on that interface (eth0), all packages that come from eth1 (the LAN) will look like they come from the Ubuntu machine. Now the "router" is ready to be used.

** * * Settting up a client on the LAN * * **

There are a few things to think about. If you don't have a DHCP-server on the LAN every computer has to be manually configured. There configuration should look something like this:

IP-address: 192.168.2.x (if you use the setup as above)
Netmask: 255.255.255.0
Gateway: 192.168.2.1
DNS: You have to provide the IP address of at least one DNS server. Try /etc/resolv.conf on the Ubuntu machine and see what DNS server it uses.

You should be set to go!

Regards,
Helgman

---

### Post by helgman on 2007-10-04
If my explanation is unclear I just found [this one](https://help.ubuntu.com/community/InternetConnectionSharing). It differs somewhat from mine but ...

---

### Post by wayanwolvie on 2007-10-06
wow, thanks

---

### Post by mips on 2007-10-06
Firestarter ?

---

