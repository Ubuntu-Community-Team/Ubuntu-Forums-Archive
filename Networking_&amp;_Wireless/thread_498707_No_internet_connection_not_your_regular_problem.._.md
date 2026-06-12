---
title: "No internet connection? not your regular problem.. :("
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by smileypaul on 2007-07-11
I've installed Feisty , but am having problems with the internet.

I've tried 3 different NIC's now, all have loaded the drivers properly.

It says "You are now connected to the internet" when i plug the cable in, but no ip address is assigned.

Ive done the usual ifdown eth0, ifup eth1, and....no dhcp offers received. 

Figured id try a static address, then /etc/init.d/networking restart  .. again, nothing.

Can't ping the router (gateway) ..

Im stumped???

Any ideas?

Current Card is a Dlink DFE-530TX  in an IBM Netvista..

if it helps, ive had it working before on a previous install, but i remember having issues (different card)..

Thanks in advance,

Paul

---

### Post by kevdog on 2007-07-11
So you are having problems with your wired connections???

FIrst determine the interface names (eth0,eth1,etc), of the card you want to use.  Probably the best way to do this is:
lshw -C network

Under each card, there will be logical name where it lists the interface name, such as:
       logical name: wlan0

Next lets just try to configure the interface manually (we can automate the process once everything is working)


Try the following assuming eth0 is you interface name:

```

sudo ifconfig eth0 down
sudo ifconfig eth0 192.168.1.100 netmask 255.255.255.0 up
sudo route add default gw 192.168.1.1

```

Check with  
ifconfig

Again substitute numbers that are appropriate for you

---

