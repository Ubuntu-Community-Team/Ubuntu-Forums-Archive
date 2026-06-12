---
title: "Make my NAT computer do PPTP VPN pass through"
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by zooounds on 2007-03-17
My Ubuntu Edgy computer is a NAT server. How does I make it possible for at least one (but possible many) LAN clients to use a PPTP VPN?

Which kernel modules must I insert? Iptables rules?

Getting panic here ...

Regards
Fredrik

---

### Post by koenn on 2007-03-17
pptp passes through nat transparently, i.e. if you allow everything out, and established in, it should work. If you want it more secure, you can specify ip addresses of servers you want to connect to, and port numbers (look up what ports pptp uses).

---

### Post by zooounds on 2007-03-18
> **koenn said:**
> pptp passes through nat transparently, i.e. if you allow everything out, and established in, it should work. If you want it more secure, you can specify ip addresses of servers you want to connect to, and port numbers (look up what ports pptp uses).

That does not work for me.

The VPN works fine if I'm not behind NAT.

Are you sure there are no kernel modules (conntrack etc) that are needed?

---

### Post by koenn on 2007-03-18
According to the documentation, al you need is to allow traffic _towards_ the vpn you're connecting to (tcp port 1743) + allow the replies ('established') and it will be NATed no problem. 

I checked my NAT box and it does have contrack installed - i probably included it when first installing iptables, so I can't verify if it would work without. I think you only need contrack if your iptables uses 'state' such as 'related'.

---

### Post by zooounds on 2007-03-18
> **koenn said:**
> According to the documentation, al you need is to allow traffic _towards_ the vpn you're connecting to (tcp port 1743) + allow the replies ('established') and it will be NATed no problem. 

I checked my NAT box and it does have contrack installed - i probably included it when first installing iptables, so I can't verify if it would work without. I think you only need contrack if your iptables uses 'state' such as 'related'.

So none of these are needed?

ip_conntrack_pptp
ip_conntrack_proto_gre
ip_nat_pptp
ip_nat_proto_gre

I still can't get it to work :(

---

### Post by koenn on 2007-03-18
I only have these, and a working pptp :
```

stargate:~# lsmod
Module                  Size  Used by    Not tainted
ipt_MASQUERADE          1216   1
ipt_state                608   2
iptable_filter          1728   1
iptable_nat            12628   3  [ip_nat_ftp ip_nat_irc ipt_MASQUERADE ipt_REDIRECT]
ip_conntrack           12652   4  [ip_conntrack_ftp ip_conntrack_irc ip_nat_ftp ip_nat_irc ipt_MASQUERADE ipt_REDIRECT ipt_state iptable_nat]
ip_tables              10432  21  [ipt_LOG ipt_MARK ipt_MASQUERADE  .... 


```

what else can I say ?

---

### Post by zooounds on 2007-03-18
I'm just curious; where comes GRE into the picture?

---

### Post by koenn on 2007-03-18
GRE does the encaptulation of packages that are send after the pptp connection is established. 

> After the PPTP control session has been established, GRE is used to encapsulate the data or payload in a secure manner
this explains it further : [http://support.microsoft.com/kb/241251](http://support.microsoft.com/kb/241251). On the diagram you'll see that the IP header sits on top of the GRE packer. The IP header holds source and destination address, which is changed during the NAT proces. So NAT doesn't affect it - unless you're running multiple pptp sessions. In that case, the NAT may get confused about which package belongs to what session - I think the contrack pptp and contrack gre modules are meant to handle that.

---

### Post by koenn on 2007-03-18
> My Ubuntu Edgy computer is a NAT server. How does I make it possible for at least one (but possible many) LAN clients to use a PPTP VPN?
I understood this correctly that the Ubuntu Edgy computer acts as a router and uses NAT to provide internet access or some other form of connectivity to 1 (or more) hosts (computers) on your LAN - and that these hosts will set up pptp sessions with servers elsewhere *through* the Ubuntu Edgy machine. So they do *not* setup pptp vpn with that ubuntu machine, right ?

---

### Post by zooounds on 2007-03-18
> **koenn said:**
> I understood this correctly that the Ubuntu Edgy computer acts as a router and uses NAT to provide internet access or some other form of connectivity to 1 (or more) hosts (computers) on your LAN - and that these hosts will set up pptp sessions with servers elsewhere *through* the Ubuntu Edgy machine. So they do *not* setup pptp vpn with that ubuntu machine, right ?

Correct.

Actually, the hosts on the "LAN" is virutal machines running on the Edgy computer. But the behave like they are sitting on a LAN.

But what could go wrong then? I have no firewall rules at all. Si there any way to se what happens when the client connects to the VPN?

---

### Post by koenn on 2007-03-18
> **zooounds said:**
> 
Actually, the hosts on the "LAN" is virutal machines running on the Edgy computer. But the behave like they are sitting on a LAN.

Hm ... there may be something else at play here. 
How did you set up networking for the virtual machines ? I mean, you can 'bridge' them so that they use the physical NIC directly, you can have them NATed by VMware (as opposed to NATed via iptables on the host system), ...
What exactly are you trying to do ? How exactly did you do you have this set up ?

> Is there any way to see what happens when the client connects to the VPN?
You can install and run ethereal / Whireshark on one of the virtual machines. It then captures all packets passing through the vm's network adaptor, so you can see all it's connection attempts, and the replies it gets. 
I think that's what I'd do first. 

You can also run ethereal / Whireshark on the physical machine and see if it can read the communucations passing through it. 
Both are worth a shot , especially if you enjoy tinkering with networks or understanding how stuff works.

---

### Post by zooounds on 2007-03-18
I run Virtual Box and it is repsonsible to set up the NAT. The client OS:es get a LAN with DHCP.

How do I check what the "rules" for the NAT set up by VirtualBox are? iptables --list says nothing at all for me.

Briding works fine but requires an additional external IP to be used, and my ISP doesn't always provide me with that.

---

### Post by koenn on 2007-03-18
> Briding works fine but requires an additional external IP to be used, and my ISP doesn't always provide me with that. I see. You're computer is directly connected to the internet so bridging requires additional public addresses. 
I run iptables & NAT on an seperate (old) pc that serves as a router so my main pc and any virtual machines in it can use private (LAN) addresses - with the virtual nics bridged so they *really* act as just any other system on my LAN, and only require NAT for internet access. 
If you happen to have an old PC lying around (mine's a Pentium, 133 Mhz, 64 MB RAM) and stick 2 NICs in it it may well be worth the effort. 

> How do I check what the "rules" for the NAT set up by VirtualBox are? iptables --list says nothing at all for me. VirtualBox doesn't use iptables, i think. It uses some built-in mechanism to load the contents of an ip packet on the virtual machine into an ippacket of the physical machine. This happens in your 'virtualization layer' *between* the guest system en the host OS so neither can see it. You may have access to it through VirtualBox itself though, i don't know, never used it. 

Anyway, From the looks of it, any attempt at pptp from a virtual machine to an outside machine should just be NATed by VirtualBox.

There's an excellent manual for VirtualBox at 
[http://www.virtualbox.org/download/UserManual.pdf](http://www.virtualbox.org/download/UserManual.pdf)
page 34 and following describe networking. Maybe you find something else there that suits your needs. On first sight, "Host Interface Networking" (bridging) may be possible if you can set it up so that the virtual NIC gets a private address, and the host (your ubuntu machine) does routing and NAT for it. Looks feasable, but no guearantees. 

Else, I'd just run ethereal in the virtual machine and see what happens during the pptp negociations, see if anything hints at problems. You can also run ethereal on the host system, see if you can catch the NATed pptp packets and see if they get replies, and whether those replies are returned to the virtual machine that initiated the pptp conversation.

---

### Post by zooounds on 2007-03-18
I see... It seems like it is Virtual Box that only NAT TCP-traffic, not GRE.

I'm trying a diffrent approach now. I'm bridging the internal intercafe (LAN) so that I can connect the virtual machin to this and really be on my LAN.

I hope this works :)

Note: It did so I am happy :)

Here is my /etc/network/interfaces as reference if anyone else have the same problem.

```


# Internet
auto eth0
iface eth0 inet dhcp

# LAN
auto eth1
iface eth1 inet manual

# Virtual interface
auto tap0
iface tap0 inet manual
    tunctl_user YOURUSERNAME

# Static adresses on LAN
auto bridge0
iface bridge0 inet static
    address 192.168.0.1
    netmask 255.255.255.0
    bridge-ports eth1 tap0
    bridge-ageing 7200
    bridge-fd 0

```

---

### Post by koenn on 2007-03-18
> **zooounds said:**
> I see... It seems like it is Virtual Box that only NAT TCP-traffic, not GRE.
Yeah, I read that but it didn't register at first. Virtualbox copies tcp-frames into ip-packets on the host, but GRE is its own protocol, not an application using tcp, so maybe that doesn't get processed.

---

### Post by koenn on 2007-03-18
> Note: It did so I am happy 
Cool. 
Now, does this also allow you to route and NAT traffic from eth1 (and the vritual machines) through eth0 towards the internet and such ?

---

