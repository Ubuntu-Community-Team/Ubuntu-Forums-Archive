---
title: "IPTables - Returning Packets Lost?"
date: 2008-08-07
forum: Networking &amp; Wireless
---

### Post by erauqssidlroweht on 2008-08-07
I'm a picture person - so let's start with a network diagram:

```

VPNClient01(10.10.10.10)---VPN/PublicLan---(10.10.10.1 Tun0)Firewall(eth0 10.4.4.20)---(10.4.4.1)RemoteGateway01---WWW---Server01

```

I'm running a Firewall/IDS/NAT and VPN terminator. The VPNClient01 needs to encrypt any data destined for Server01. (The VPN Tunnel is the 10.10.10.* network).

OBSERVATION 1) From the CLI on the Firewall I can traceroute all the way to server01.

OBSERVATION 2) From the CLI on VPNClient01 I can traceroute but only receive the first hop of 10.10.10.1.

OBSERVATION 3) TCPDump on eth0 give the following while tracerouting from VPNClient01:

```

#tcpdump -i eth0
14:24:17.557041 IP 10.4.4.52 > SERVER01: ICMP echo request, id 768, seq 57088, length 72
14:24:17.612664 IP SERVER01 > 10.4.4.52: ICMP time exceeded in-transit, length 36

```

OBSERVATION 4) Eth1 - is the network with the PublicLAN & the 'red' network. Eth0 - is the 'green' network and as the RemoteGateway. Tun0 is the VPN tunnel. 'Green' Network successfully passes into the 'red' network when destined for the a PublicLAN IP address (192.168.1.*).


My packets seem to be gets lost - upon return to the Tun0?


```

# iptables -t nat -L
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination
CUSTOMPREROUTING  all  --  anywhere             anywhere
SQUID      all  --  anywhere             anywhere
PORTFW     all  --  anywhere             anywhere

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
CUSTOMPOSTROUTING  all  --  anywhere             anywhere
REDNAT     all  --  anywhere             anywhere
SNAT       all  --  10.10.10.0/24       anywhere            to:10.4.4.50-10.4.4.52

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Chain CUSTOMPOSTROUTING (1 references)
target     prot opt source               destination

Chain CUSTOMPREROUTING (1 references)
target     prot opt source               destination

Chain PORTFW (1 references)
target     prot opt source               destination

Chain REDNAT (1 references)
target     prot opt source               destination
MASQUERADE  all  --  anywhere             anywhere

Chain SQUID (1 references)
target     prot opt source               destination

```

Performing the following didn't seem to change anything:
Code:

```

iptables -t nat -A POSTROUTING --source 10.4.4.0/24 -o tun0 -j SNAT --to 10.10.10.10

```
What can I try?

---

### Post by erauqssidlroweht on 2008-08-07
It seems in my situation RemoteRouter only accepts traffic from a few IP addresses. After change the NAT statement to mimic a computer that was already transmitting on the remote network I could Ping all the way through. *Sighs* I wish they would have told me that to begin with....


iptables -t nat -A POSTROUTING --source 10.10.10.0/24 -o eth0 -j SNAT --to 10.4.4.**52**

---

