---
title: "Need help with DHCP"
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by nicarley on 2007-02-16
I have an Ubuntu 6.10 box that has two network cards.  

eth0 is the network card connected to the cable modem that uses dhcp to get its ip address.

eth1 is connected to a switch, which I want to give out dhcp addresses in the range 192.168.0.1 through 192.168.0.100.  Currently the IP address of this net card is:  192.168.0.254

My DNS settings are 208.67.222.222, and 208.67.220.220

I need help with the config files.  I would like to use my internet connection on eth0 to be shared on eth1.  I have the dhcp server installed, but I am a little confused as to what information needs to go in the config file.  Please help!

---

### Post by koenn on 2007-02-17
this should be fairly straightforward

1- set up dhcp so that computers on (the switch connected to) eth1 get correct netwrok settings.
--> edit /etc/dhcp3/dhcpd.conf

make sure you have the following in there :

```
# dhcp lease time for local network - in seconds
default-lease-time 600000;
max-lease-time 720000;

# network config for local network (lease definition)
subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.1 192.168.0.100;
  option routers 192.168.0.254;
  option domain-name-servers 208.67.222.222 208.67.220.220 ;
}

```

2-
Then, set up the Ubuntu 6.10 box that has two network cards to do routing and NAT, so that it can provide a route to the internet for the pc's attached to eth1.

You can start with the instructions in post #2 of this treath, replaceing ip addresses etc with the ones appropriate to your network
[http://ubuntuforums.org/showthread.php?t=358169](http://ubuntuforums.org/showthread.php?t=358169)

---

