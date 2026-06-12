---
title: "Need iptables help with NAT to virtual machine"
date: 2014-08-08
forum: Networking &amp; Wireless
---

### Post by egpetrich on 2014-08-08
I have a virtual machine running on a virtual network. I was previously able to forward connections to the virtual machine, but an installed update a few months ago (forgot which update and when, sorry) broke my ability to maintain connections. I'm hoping someone can suggest an improved iptables config.

I add the forwarding rules with this script:

```
# Forward only tcp port 25565
iptables -I FORWARD 3 ! -i virbr0 -o virbr0 -p tcp --dport 25565 -j ACCEPT
iptables -t nat -A PREROUTING ! -i virbr0 -p tcp --dport 25565 -j DNAT --to 192.168.122.2

# Masquerade on packets sent from local network to virtual network.
iptables -t nat -A POSTROUTING -s 192.168.0.0/24 -d 192.168.122.0/24 -j MASQUERADE

# Log and drop invalid packets from the virtual network.
# Accept input packets for established and related connections.
# Derived from "Linux Firewalls" by Michael Rash
iptables -A INPUT -i virbr0 -m state --state INVALID -j LOG --log-prefix "DROP INVALID " --log-ip-options --log-tcp-options
iptables -A INPUT -i virbr0 -m state --state INVALID -j DROP
iptables -A INPUT -i virbr0 -m state --state ESTABLISHED,RELATED -j ACCEPT

# Accept special packets associated with virtual machine VNC connection.
iptables -A INPUT -i virbr0 -p igmp -j ACCEPT

# Log and drop spoofed packets from the virtual network.
iptables -A INPUT -i virbr0 ! -s 192.168.122.0/24 -j LOG --log-prefix "DROP SPOOFED PKT "
iptables -A INPUT -i virbr0 ! -s 192.168.122.0/24 -j DROP
iptables -I INPUT 11 -i virbr0 ! -s 192.168.122.0/24 -j LOG --log-prefix "DROP SPOOFED PKT "
iptables -I INPUT 12 -i virbr0 ! -s 192.168.122.0/24 -j DROP

# Log and drop any other packets from the virtual network.
iptables -A INPUT -i virbr0 -j LOG --log-prefix "DROP UNEXPECTED PKT "
iptables -A INPUT -i virbr0 -j DROP

```

I'm trying to remember why I have two sets of rules to log and drop spoofed packets. Surely I must have had a reason when I wrote this thing in April 2013....

Symptoms are that the initial connection works (I'm running a Minecraft server), but the connection isn't maintained and the client eventually times out. As I said, this used to work just fine.

My "iptables -L" output looks like this:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     udp  --  anywhere             anywhere             udp dpt:domain
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:domain
ACCEPT     udp  --  anywhere             anywhere             udp dpt:bootps
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:bootps
LOG        all  --  anywhere             anywhere             state INVALID LOG level warning tcp-options ip-options prefix "DROP INVALID "
DROP       all  --  anywhere             anywhere             state INVALID
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ACCEPT     igmp --  anywhere             anywhere
LOG        all  -- !192.168.122.0/24     anywhere             LOG level warning prefix "DROP SPOOFED PKT "
DROP       all  -- !192.168.122.0/24     anywhere
LOG        all  -- !192.168.122.0/24     anywhere             LOG level warning prefix "DROP SPOOFED PKT "
DROP       all  -- !192.168.122.0/24     anywhere
LOG        all  --  anywhere             anywhere             LOG level warning prefix "DROP UNEXPECTED PKT "
DROP       all  --  anywhere             anywhere
Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             192.168.122.0/24     state RELATED,ESTABLISHED
ACCEPT     all  --  192.168.122.0/24     anywhere
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:25565
ACCEPT     all  --  anywhere             anywhere
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

And "iptables -t nat -L" looks like this:

```
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination
DNAT       tcp  --  anywhere             anywhere             tcp dpt:25565 to:192.168.122.2

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
MASQUERADE  tcp  --  192.168.122.0/24    !192.168.122.0/24     masq ports: 1024-65535
MASQUERADE  udp  --  192.168.122.0/24    !192.168.122.0/24     masq ports: 1024-65535
MASQUERADE  all  --  192.168.122.0/24    !192.168.122.0/24
MASQUERADE  all  --  192.168.0.0/24       192.168.122.0/24
```

Any suggestions?

---

### Post by egpetrich on 2014-08-18
Looks like the problem has solved itself after I upgraded the virtual machine to 14.04.1 LTS. The host is still on 12.04.5 LTS.

---

### Post by egpetrich on 2014-08-18
Duplicate reply.

---

