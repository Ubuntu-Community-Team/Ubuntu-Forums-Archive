---
title: "Confusion about WAN connection"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by Peque on 2007-10-09
Hey there. 

I'm a little confused here about what to do to get this working. 
My Firewall is a Soekris Net48010+1601 with Iptables on it. 
My company have just give me an internet connection ( a buisnessline ) at home. 
And I got this letter with this information: 
Ip-address 83.95.44.14
Gateway: 83.95.44.13
Netmask: 255.255.255.252

And got this Extra IPadresses like this 
87.50.193.216/30 netmask 255.255.255.252   Addresses available 87.50.193.217-83.50.193.218

How do I set this one up - for the networkinterface? 
As it look now:
```

# WAN Interface
auto eth0
iface eth0 inet static
        address 83.95.44.14
        netmask 255.255.255.252
        gateway 83.95.44.13

# Extra IP nummer 1
auto eth0:0
iface eth0:0 inet static
        address 87.50.193.217
        netmask 255.255.255.252

``` 
My IPtables script is by the time pretty komplex :-) but goes a little like this in the big view: 
eth0 = WAN 
eth1 = LAN 
eth2 = DMZ
eth3 = plutozone

I have access from LAN to plutozone, where I want my secundary public IP to go to - but no access from the outside - and that seems a little strange to me - so I would like to know if there is something special to define the settings for such an options in /etc/network/interface. 
Do I have done it correctly so that at this time its my IPTABLES script or is it the settings for the network? 

Greetings 
Per Jørgensen

I can ping etc from all interfaces - but the funny part is:

---

