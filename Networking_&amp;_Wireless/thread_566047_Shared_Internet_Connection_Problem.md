---
title: "Shared Internet Connection Problem"
date: 2007-10-03
forum: Networking &amp; Wireless
---

### Post by JustinMorris on 2007-10-03
I imagine I am overlooking something very simple but here is the relevant information.  eth0 is connected to the internet via a router and eth1 is the connection I wish to share via Ubuntu server.  

I have tried this **[here]("http://www.debuntu.org/iptables-how-to-share-your-internet-connection-p3")**, but that did not work. 

I also tried **[this]("https://help.ubuntu.com/7.04/server/C/ip-masquerading.html")**, but was a bit confused.  Is this what I would enter in my particular case?  If this is what I would enter, it doesn't work:
```
sudo iptables -t nat -A POSTROUTING -s 192.168.1.1/24 -o eth0 -j MASQUERADE
sudo iptables -A FORWARD -s 192.168.1.1/24 -o eth0 -j ACCEPT
sudo iptables -A FORWARD -d 192.168.1.1/24 -m state --state ESTABLISHED,RELATED -i eth0 -j ACCEPT
```

I have also tried **[this]("http://ubuntuforums.org/showpost.php?p=2135536&postcount=2")**, but that did not work.

Here is what is in my /etc/network/interfaces.  I think I may have something setup wrong with eth1?  I am not sure,  since I am rather new at this.
```
# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.4
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

# The secondary network interface
auto eth1
iface eth1 inet static
        address 192.168.1.8
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
```

By "doesn't work" I mean, the machine connected via eth1 cannot connect to the internet, or any local network.

---

### Post by helgman on 2007-10-03
My guess is that you have a problem with eth1 (as you suspected).

**eth0** is connected to network 192.168.1.0/24 so **eth0** can be used as a route to that network.

**eth1** is connected to network 192.168.1.0/24 so **eth1** can be used as a route to that network.

You see a similarity? The server thinks that both networks are connected to the same network, using different IP addresses, sure, but it's still the same network. The netmask is what tells you this. A netmask of 255.255.255.0 tells you that 192.168.1 is the network portion of the IP address and that the last digit (4 and 8 in your case) is the host address (you even have the network statement in you configuration). A netmask of 255.255.0.0 would give you 192.168 as the network address and 1.4 and 1.8 as host address.

There are two ways for you to go here. Either you make smaller subnets (the hard way) or you change the last digit of the network address on one of your interfaces. We won't go into the hard way since that might bring trouble down the line, but here is what you could make your **/etc/network/interfaces** look like:

```
# The primary network interface connected to the Internet
auto eth0
iface eth0 inet static
        address 192.168.1.4
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

# The secondary network interface connected to the LAN
auto eth1
iface eth1 inet static
        address 192.168.10.8
        netmask 255.255.255.0
        network 192.168.10.0
        broadcast 192.168.10.255
```

As you see I have omitted the gateway statement in the configuration of eth1. Since eth0 has the gateway there is no need for it in the configuration of eth1.  (Make sure to reconfigure ALL clients on the LAN so they use the 192.168.**10** network as well.)

Also, I've looked some at your iptables and I'm no expert at iptables but I think you will have to change it some to make it work. I'm doing a project where we are using my laptop as a gateway for a wireless ad hoc network and the only iptables statement I give it is:

```
iptables -t nat -A POSTROUTING -o eth0 -s 0/0 -j MASQUERADE
```

I'm have eth2 connected to the wireless network (via Ethernet cable) and eth0 is connected to the Internet. My source (-s) is 0/0 since there are a lot of subnets on the wireless network. I guess you could set it to 192.168.10.0/24. As for the other two you should maybe change them to:

```
sudo iptables -A FORWARD -s 192.168.10.0/24 -o eth0 -j ACCEPT
sudo iptables -A FORWARD -d 192.168.10.0/24 -m state --state ESTABLISHED,RELATED -i eth0 -j ACCEPT
```

Now the first one takes packages with a source address from the 192.168.10.0 network and sends them out on interface eth0 (this should be done the first statment above (the one doing the masquerading) and the second one says that anything that is heading to the 192.168.10.0 network and is already a part of a conversation should be passed through.

Since you are using NAT, nothing (that is part of a conversation) will be heading for 192.168.10.x since every packaged leaving that network will have it's source address changed by the server so that it looks like it's coming from 192.168.1.4.

Anyway, play around a little with those things an let us know if it works out. Also make sure that ip_forwarding is enabled (see that you get the output 1 from cat /proc/sys/net/ipv4/ip_forword), I've forgotten it once or twice ...

Regards,
Helgman

---

### Post by JustinMorris on 2007-10-03
I got it to work following your instructions, I knew it was the eth1, but I wanted to make sure and I didn't know what to change really.  Thank you helgman.

---

