---
title: "Iptables Goes to Sleep"
date: 2018-11-06
forum: Networking &amp; Wireless
---

### Post by mcduffiejohn on 2018-11-06
I've looked everywhere for a solution. It's out there, but I can't find it. 
I have a VM setup with two network cards. This VM is a gateway for a network of other VMs. The problem is the port forwarding I set up using iptables works fine but only if I keep it alive. If I stop doing anything for a few minutes, I can no longer see any of the VMs behind the gateway VM from outside the network. For instance, I have one VM setup with a honeypot listening on port 22. I forwarded port 22 from my gateway VM to the VM that hosts the honeypot. I tested it using canyouseeme and it saw my service on port 22. If I do nothing for a few minutes and test it again, it cannot see my service on port 22. However, if I log into the VM that hosts the honeypot and ping the gateway, the port forwarding goes back to working immediately. It's like the port forward I set up in the gateway goes to sleep and doesn't wake up when traffic is sent to it. This has cost me a half a day already and it's very annoying. I need to know how to keep my iptables config awake so it's always forwarding and listening. Like I said, it all works fine as configured unless you walk away from it.

Here is the basic info:
All VMs are Ubuntu Server 16.04 and all are fresh, updated yesterday installs with nothing going on except the iptables in the gateway and a single honeypot in another vm at this time.
The network is basically setup like this: ISP router -----> Gateway VM ---->All other VMs


My iptables config is setup in rc.local to start at boot and all VMs are setup with static IPs and their info is correct. That much I am sure of and it works anyway, unless you walk away from it.

My network cards are enp0s3 which faces the internet and enp0s8 which my other VMs use as their gateway.

10.0.0.175 is the ip of enp0s3 which gets all the internet traffic from my ISP's router.
10.0.1.1 is the ip of enp0s8 which acts as a gateway for the other VMs
10.0.1.128 is the honeypot VM which can ping websites like Google and curl them as well
The ISP router forwards port 22 traffic to 10.0.0.175 which forwards it via iptables through 10.0.1.1 to 10.0.1.128:22

This is a test environment at the moment but I will build the same setup in a production environment once it is working correctly.

My rc.local file looks like this (this is the entire file):

```
# /etc/rc.local


# Default policy to drop all incoming packets
# iptables -P INPUT DROP
# iptables -P FORWARD DROP


# Accept incoming packets from localhost and the LAN interface
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -i enp0s8 -j ACCEPT


# Accept incoming packets from the WAN if the router initiated
# the connection
iptables -A INPUT -i enp0s3 -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT


# Forward LAN packets to the WAN
iptables -A FORWARD -i enp0s8 -o enp0s3 -j ACCEPT


# Forward WAN packets to the LAN if the LAN initiated the
# connection
iptables -A FORWARD -i enp0s3 -o enp0s8 -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -t nat -A  PREROUTING -p tcp -d  10.0.0.175 --dport 22 -j DNAT --to 10.0.1.128:22


# NAT traffic going out the WAN interface
iptables -t nat -A POSTROUTING -o enp0s3 -j MASQUERADE
iptables -t nat -A POSTROUTING -j MASQUERADE
iptables -L -t nat


# rc.local needs to exit with 0
exit 0

```

Any help or links would be greatly appreciated. I've beaten my head against this long enough.

---

