---
title: "Multiple Natting Gateway Help"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by brownjl on 2008-08-10
Hello,

I am not a newbie to ubuntu but very far from an expert :)

I am hoping to set up a Gateway for a set of private subnets which I want to nat on to a set of public ip on one one public interface.

Public Interface -

Eth0:- IP 192.168.0.2 - 192.168.0.6

Private Subnets - 

Eth1:- IP 192.168.100.1
Eth2:- IP 192.168.101.1
Eth3:- IP 192.168.102.1
Eth4:- IP 192.168.103.1
Eth5:- IP 192.168.104.1

Is it possible to create an IP Tables Nat Gateway which will Nat each of my Private Subnets on to a seperate external IP address on the one public interface? I was thinking of IP Aliasas on Eth0 but I heard they are not supported by iptables.....

Any Help would be appriciated!

Cheers,

James

---

### Post by SpaceTeddy on 2008-08-11
how can 192.168.0.2-6 be a "public" interface ? that is definetly not an internet ip :)

anyway - yes, this is possible. And not that hard to follow either. Here is what i think you should do to accomplish this:

1.) get the virtual interfaces working
In order to utilize your external IP's, your gateway must first own them. This is easiest done via virtual interfaces. So, in your /etc/network/interfaces, add the 192.168.0.2 as your primary up, and then add the virtual interfaces for 192.168.0.3-6 to attach to eth0.
An example would be:
> iface eth0:0 inet static
	address 192.168.0.3
	netmask 255.255.255.0


then bring the interfaces with:
```
sudo ifup eth0:0
```
and so on.
ifconfig should now show you all real and virtual interfaces. 

lastly, check if your server replies to the virtual ip the same as it replies to the real network devices.

2.) Get the SNAT right. 
Now, since your server has the IP's, all you need is some SNAT (**S**ource **N**etwork **A**ddress **T**ranslation) that tells it when to send what from which ip.

the rule looks like this:
```
sudo iptables -A POSTROUTING --table nat -i eth1 --to-source 192.168.0.2
```
this would rewrite all pakets what come in on eth1 (so from the 192.168.100.0/24 network) to be send on to the internet via the 192.168.0.2 address - change the ip and interfaces you see fit. 

That should be all - i think :)

**NOTE**: it's been a very long time since i have done this myself - but my rules here seem to work the same way.
**NOTE**: this can also be accomplished by transparent proxies... i think.

Hope it helps :)

---

