---
title: "iptables.rules for 1 to 1 NAT"
date: 2019-09-27
forum: Networking &amp; Wireless
---

### Post by rsteinmetz70112 on 2019-09-27
I am trying to set up my Ubuntu 16.04 server to act as a router for static IP addresses assigned by my isp -ATT. I had this working for different router but now can't get it to work for a new one whihc has a different interface. Here is what I have so far. I've changed the public IP addresses. I had to add a couple of spaces to avoid getting :P
> 
: PREROUTING ACCEPT [66316:6289839]
:INPUT ACCEPT [33999:3265034]
:OUTPUT ACCEPT [10562:903361]
: POSTROUTING ACCEPT [4:240]
-A PREROUTING -d aa.bb.cc.14/32 -j DNAT --to-destination 192.168.1.1
-A PREROUTING -d aa.bb.cc.9/32 -j DNAT --to-destination 192.168.1.2
-A PREROUTING -d aa.bb.cc.10/32 -j DNAT --to-destination 192.168.1.3
-A PREROUTING -d aa.bb.cc.11/32 -j DNAT --to-destination 192.168.1.28
-A PREROUTING -d aa.bb.cc.12/32 -j DNAT --to-destination 192.168.1.29
-A PREROUTING -d aa.bb.cc.13/32 -j DNAT --to-destination 192.168.1.4
-A POSTROUTING -s 192.168.1.1/32 -j SNAT --to-source aa.bb.cc.14
-A POSTROUTING -s 192.168.1.2/32 -j SNAT --to-source aa.bb.cc.9
-A POSTROUTING -s 192.168.1.3/32 -j SNAT --to-source aa.bb.cc.10
-A POSTROUTING -s 192.168.1.28/32 -j SNAT --to-source aa.bb.cc.11
-A POSTROUTING -s 192.168.1.29/32 -j SNAT --to-source aa.bb.cc.12
-A POSTROUTING -s 192.168.1.4/32 -j SNAT --to-source aa.bb.cc.13

I'm trying to set up an Arris BGW210-700 using the Cascaded Router option however there are a number of problems. I'm hoping someone here can clue me in. I've searched the Internet and not really found an answer. 

The Cascaded router has these settings:

[INDENT]**Cascaded Router**
Cascaded Router Enable - Yes
 
Cascaded Router Address - 192.168.1.1
Network Address  -aa.bb.cc.8
Subnet Mask 	255.255.255.48[/INDENT]

However the Network address which I think should be aa.bb.cc.8 but it will only take an IP Address whihc should work with an subnetmask But when I go to save I get an error message "session refused"
If I try to put subnet address of the router aa.bb.cc.14 I get the same thing.

I'm wondering if the subnet public address should be defined with the /32 which reads like a network address or if there is some way to define the subnet specifically in the iptables.rule file. So far I can't figure it out but iptables always confuses me.

---

### Post by SeijiSensei on 2019-09-28
A /32 is the same as an IP address.  

10.10.10.10/32 is the same as just 10.10.10.10.

---

### Post by The Cog on 2019-09-28
That subnet mask looks wrong to me. 255.255.255.248 perhaps, giving you from .8 to .15 (probably .9-.14 usable)?

---

### Post by SeijiSensei on 2019-09-28
[deleted]

---

### Post by rsteinmetz70112 on 2019-09-30
Yes it is it should be network address could be expressed as aaa.bbb.ccc.8/29
The Broadcast address would be aaa.bbb.ccc.15
The usable address range would be aaa.bbb.ccc.9 - aaa.bbb.ccc.14, although ATT seems to reserve aaa.bbb.ccc.14 for a router leaving only 5 addresses usable.
My problem is how to configure one Ubuntu box to act as a router for those addresses. I had this working with an older ATT Gateway then we "upgraded" and I can't get this to work.

---

### Post by SeijiSensei on 2019-09-30
Just to make sure, you did edit /etc/sysctl.conf and enable net.ipv4.ip_forward=1, right? Ubuntu, like most distros these days, blocks packets from being passed between interfaces by default as a security measure.

---

### Post by rsteinmetz70112 on 2019-09-30
> **SeijiSensei said:**
> Just to make sure, you did edit /etc/sysctl.conf and enable net.ipv4.ip_forward=1, right? Ubuntu, like most distros these days, blocks packets from being passed between interfaces by default as a security measure.

Thanks for the reminder and yes I did. I just went back and checked to be sure, although I'm not really sure it's necessary since all I'm doing is address translation utilizing the same interface .

---

### Post by rsteinmetz70112 on 2019-10-04
OK I'm back on this. checked iptables and got teh following output:
```
# iptables -t nat -L
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination
DNAT       all  --  anywhere             aa.bb.cc.14          to:192.168.1.1
DNAT       all  --  anywhere             aa.bb.cc.9           to:192.168.1.2
DNAT       all  --  anywhere             aa.bb.cc.cc          to:192.168.1.3
DNAT       all  --  anywhere             aa.bb.cc.11          to:192.168.1.28
DNAT       all  --  anywhere             aa.bb.cc.12          to:192.168.1.29

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
SNAT       all  --  hamlet               anywhere             to:aa.bb.cc.14
SNAT       all  --  192.168.1.2          anywhere             to:aa.bb.cc.9
SNAT       all  --  192.168.1.3          anywhere             to:aa.bb.cc.cc
SNAT       all  --  romulus.local        anywhere             to:aa.bb.cc.11
SNAT       all  --  remus.local          anywhere             to:aa.bb.cc.12
MASQUERADE  all  --  anywhere             anywhere
SNAT       all  --  hamlet               anywhere             to:aa.bb.cc.14
SNAT       all  --  hamlet               anywhere             to:aa.bb.cc.14
SNAT       all  --  hamlet               anywhere             to:aa.bb.cc.14
```

I don't see anything obvious but then I'm not sure what I'm doing.

---

### Post by SeijiSensei on 2019-10-04
I don't how one does this with a single interface. Every router I've built has two, typically one that faces the Internet and one that faces the local network.

---

### Post by rsteinmetz70112 on 2019-10-04
Quick Followup - 
```
# iptables -t nat -L
```
Takes almost 3 minutes to complete which seems like a long time to me.

---

### Post by SeijiSensei on 2019-10-04
I bet it's a lot quicker with 
```
sudo iptables -L -t nat -nv
```
The -n switch turns off name resolution.

---

### Post by rsteinmetz70112 on 2019-10-04
> **SeijiSensei said:**
> I don't how one does this with a single interface. Every router I've built has two, typically one that faces the Internet and one that faces the local network.

This machine has only one interface now and it worked like that until we changed out the ATT Gateway. I guess could add another network card to see if that would work. 

You could also add additional Ip addresses to an interface and have 2 ip addresses on one interface.

---

### Post by rsteinmetz70112 on 2019-10-04
> **SeijiSensei said:**
> I bet it's a lot quicker with 
```
sudo iptables -L -t nat -nv
```
The -n switch turns off name resolution.

It's almost instantaneous with the -n switch.
Thanks for the tip.

---

### Post by SeijiSensei on 2019-10-04
> **rsteinmetz70112 said:**
> You could also add additional Ip addresses to an interface and have 2 ip addresses on one interface.
I've had machines with dozens of virtual interfaces like eth0:1, etc., but I've only ever done this when all the addresses are in the same IP subnet. I've never tried aliasing an interface with addresses in multiple subnets. I'd imagine it could cause routing problems, but that's just a guess.

---

### Post by rsteinmetz70112 on 2019-10-05
> **SeijiSensei said:**
> I've had machines with dozens of virtual interfaces like eth0:1, etc., but I've only ever done this when all the addresses are in the same IP subnet. I've never tried aliasing an interface with addresses in multiple subnets. I'd imagine it could cause routing problems, but that's just a guess.

And yet it worked with the same ISP on different hardware until several days ago. I have another site where a different ISPs hardware actually has a 1 to 1 NAT table built in. IN the past using different ISPs the 1 to 1 NAT was built into the router. 

If it worked as it used to the WAN IP routes to a Private IP as an alias for a Public IP Router which the forwards the data to the private IP addresses of the Public IP address and back again. NAT.is not a particularly obscure application of NAT

---

### Post by rsteinmetz70112 on 2019-10-22
OK BAck to this it seems the problem was broken firmware. I updated to a later firmware and it's working, at least to the router machine.
I'm still testing to see if everything works as expected now.

---

