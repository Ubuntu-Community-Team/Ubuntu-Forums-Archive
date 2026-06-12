---
title: "can't ping local machines from router"
date: 2005-07-03
forum: Networking &amp; Wireless
---

### Post by jaahze on 2005-07-03
Hi, just installed ubuntu and trying to set it up as a router.  
I have a laptop and xbox connected to my ubuntu machine which connects to lan. 
Everything works fine from the laptop, but I can't ping local machines from the router (ubuntu).  

So, eth2 -> external
eth0 (192.168.0.1) -> laptop (192.168.0.3)
eth1 (192.168.0.4.-> xbox  (192.168.0.2)

Any ideas what might be the problem?

route -n
Destination        Gateway              Genmask           Iface
193.167.201.0   0.0.0.0                 255.255.255.0  eth2
192.168.0.0       0.0.0.0                 255.255.255.0  eth0
192.168.0.0       0.0.0.0                 255.255.255.0  eth1
0.0.0.0               193.167.201.254 0.0.0.0              eth2

---

### Post by gruepig on 2005-07-03
[QUOTE=jaahze]

route -n
Destination        Gateway              Genmask           Iface
193.167.201.0   0.0.0.0                 255.255.255.0  eth2
192.168.0.0       0.0.0.0                 255.255.255.0  eth0
192.168.0.0       0.0.0.0                 255.255.255.0  eth1
0.0.0.0               193.167.201.254 0.0.0.0              eth2

[/QUOTE]

I don't think you can have multiple routes to the same network (192.168.0.0/24) on different interfaces.  (Unless you're doing something substantially more complicated.)  If I'm understanding your aims correctly, you want to have two interfaces on your router, one for 192.168.0.0/24 and one for your default gateway.  Cable the 192.168.0.0/24 interface to a switch/hub which is also connected to your hosts; cable the default gateway interface to your uplink.

---

### Post by jaahze on 2005-07-04
[QUOTE=gruepig]I don't think you can have multiple routes to the same network (192.168.0.0/24) on different interfaces.  (Unless you're doing something substantially more complicated.)  If I'm understanding your aims correctly, you want to have two interfaces on your router, one for 192.168.0.0/24 and one for your default gateway.  Cable the 192.168.0.0/24 interface to a switch/hub which is also connected to your hosts; cable the default gateway interface to your uplink.[/QUOTE]

Ok, I think i got that :) Trying to make this as simple as possible now: 
NET <--> (eth2: external_ip) ubuntu (eth0: 192.168.0.1) <--> laptop (192.168.0.3)

How do I get the ubuntu machine to ping my laptop? Net working just fine from the laptop

routing now set up like this: 
route -n
Destination Gateway Genmask Iface
193.167.201.0 0.0.0.0 255.255.255.0 eth2
192.168.0.0 0.0.0.0 255.255.255.0 eth0
0.0.0.0 193.167.201.254 0.0.0.0 eth2

---

### Post by gruepig on 2005-07-04
A few questions/things to try:

[list=1]
[*]Can you ping any hosts from the ubuntu machine (the ubuntu machine itself, something outside your network)?
[*]Can you ping the ubuntu machine from your laptop (as opposed to the other way around)?
[*]What are you using for the netmask and gateway addresses on the laptop? (Should be 255.255.255.0 and 192.168.0.1.)
[*]Do you have firewall software enabled on your laptop? (If so, temporarily disable it.)
[*]What firewall rules do you have on the ubuntu machine? (Run 'iptables -L'  and post the results; the policies for INPUT and OUTPUT should be accept.)
[/list]

---

### Post by jaahze on 2005-07-04
Ok, some progress. Disabled windows firewall and pinging works both ways now (it has worked before with firewall on, but go figure..) 
I have no idea how the iptables should be set up, I've tried pretty much anything I could find (bad,bad idea..) 

So the (final) problem is this: I had samba running on ubuntu and it worked great (with just two machines, no net). After all this messing around I can't connect to samba shares or ssh to my ubuntu machine ("network error: connection timed out"). 

would appreciate a link to a good howto, or sane configuration for iptables

---

