---
title: "iptables traffic rules"
date: 2023-02-27
forum: Networking &amp; Wireless
---

### Post by bepa77 on 2023-02-27
Hi.
  I am trying to get my head around how iptables work. From what I have read online it seems that the default setting for iptables is allow in both directions, instead of the typical allow outgoing deny incoming. Is this true?
  Also I am trying to get my head around incoming traffic if a linux clients firewall is set to allow all incoming. Does that mean that all ports on the client are reachable from the outside, or do you have to have a service or application listening on a specific port on the client for that port (and only that port) to be reachable for others?

---

### Post by TheFu on 2023-02-27
iptables is being replaced by nftables. If you are just starting out and on a 22.04+ system, I'd concentrate on learning nftables instead.  Find online articles and concrete examples.

Firewalls can work at different levels, though source IP is the most common.  It can be target port or it can be sourceIP and target port or source port.  IP can be IPv4 or IPv6. They are completely separate to the firewall, so if you need a rule and your system supports IPv6 (it does unless you go out of your way to prevent it!), then you'll need 2 rules. One for IPv4 and one for IPv6.

Services can listen on a specific interface and port and protocol. Typically, we are concerned with UDP and TCP as the protocols.   /etc/services has a custom list of services to port/protocols for any Unix-like OS. The names or the numbers can be used in most commands.  That file has the defaults, but those are not mandatory.  And service can use any unused port.  If a port is already used, then either a traffic cop has to be the listener and recognize which back-end service should receive the packets or if there isn't a traffic cop, only 1 network service listener is allowed.  An example of a traffic cop would be a tool that allows port 443/tcp to be used for HTTPS, ssh, and VPN connections.  This would be desirable since many company security firewalls would block the normal ports for ssh and VPNs, so re-using 443/tcp would likely bypass that, assuming they don't have deep-packet-inspection hardware to see the specific types of traffic egressing from their network.  Fortune 50 companies and many govts do, but many hotels and mid-sized companies will not.

---

### Post by Doug S on 2023-02-27
> **bepa77 said:**
> Hi.
  I am trying to get my head around how iptables work. From what I have read online it seems that the default setting for iptables is allow in both directions, instead of the typical allow outgoing deny incoming. Is this true?

Yes. The default is no rules at all and a default of ACCEPT for the empty chains. Example:

```
doug@s19:~$ [COLOR="#FF0000"]sudo iptables -xvnL[/COLOR]
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
```

I agree with TheFu about nftables verses iptables, but I have yet to make the transition.

---

