---
title: "Directing specific traffic through multiple NICs"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by jmvbxx on 2007-03-19
I am setting up three Ubuntu machines that will each have 2 NICs and are going to be used as VOIP terminals.

How can I direct VOIP traffic through one NIC and web browsing through the second NIC?

I believe it can be done by changing the settings on the router but I'd like to do it right from the o/s.


Thanks in advance!

---

### Post by spd106 on 2007-03-19
You can probably do this with iptables by forwarding the voip ports to one interface and web requests to another. I haven't seen anything voip specific, but the best source on ip tables I've seen is this site [http://www.tldp.org/HOWTO/Adv-Routing-HOWTO/index.html](http://www.tldp.org/HOWTO/Adv-Routing-HOWTO/index.html)

It should be enough to get you started.

---

### Post by Mr. C. on 2007-03-19
Why would you need iptables to do this?  This is a simple routing question.

Your NICs need to be on different layer 2 networks.   Are you expecting otherwise?

Each network will have an entry in the routing table, so addressing either network is automatic.  One NIC will be used to forward all other traffic through the default route.


MrC

---

### Post by hyper_ch on 2007-07-24
Hi there

I need exactly the same but I still don't know how to do that...

The answer from Mr. C doesn't help me at all :( could you explain this to me?

---

### Post by Mr. C. on 2007-07-24
You'll need to describe your details more specifically than the original poster, and answer the follow-up question I asked.  Can't help without data.

MrC

---

### Post by hyper_ch on 2007-07-25
Well, the situation is the following:

I have access to two networks and I want to route certain programs/applications only through one of those networks.

I have two NICs (eth and wifi). I would like to setup that certain applications (bound to a port or if possibly by the appilcation itself) can only use nic2 and the rest can use nic1.

e.g. I want apache server (special port 81) and mysql only to listen and send traffic through nic2 but all the rest goes through nic1.

---

### Post by Mr. C. on 2007-07-26
Some apps, such as Apache, SSH, and others, can be configured to listen on certain interfaces.   Just configure each as meets meets your needs.  Apache can be configure to listen via the Listen directive in httpd.conf.

Again, there isn't much detail here.  Be more specific for more help.

MrC

---

### Post by netztier on 2007-07-26
> **hyper_ch said:**
> 
I have two NICs (eth and wifi). I would like to setup that certain applications (bound to a port or if possibly by the appilcation itself) can only use nic2 and the rest can use nic1.


Well, before anything else, you need to fix the routing issues you're certainly going to have.

Most probably your box will be DHCP client with both NICs, right? The DHCP servers will assign each an address and subnet mask per NIC - so far so good. But by default, the DHCP client will also obtain two sets of default gateway & DNS Server information. This leads to problems like:

[LIST]
[*] Which default route is going to make it into the routing table as the first one? Traffic leaving your box will always follow that route. 
[*] Which DNS servers are going to be listed as the first in /etc/resolv.conf? 
[*] What if these first-listed servers aren't reachable via the first default route? 
[*] What if after a reboot after a week, the sequence of default routes and DNS servers changes because one DHCP server's reply was delayed?
[/LIST]

Basically, there can only be one default route per routing table that is actively being used - a routing table is a "most specific first" thing. This means that you can have any number of default routes in the table, but only ever the first one is going to be used. Have a look at your routing table with **netstat -nr**.

So if you have a set of "internal" networks (i.e. your company, home-LANs, community LANs), you can add specific static routes for these networks, pointing to an "internal" next hop router. If you have only one internal subnet, you don't need a static route - having a NIC in a subnet always generates a route entry for that network, sometimes called a "directly connected route". Any other network destination address is matched by the (first) default route entry which points to the default gateway, reachable via the other NIC.
In both cases, I suggest you configure the "internal" interface with a static address to avoid DHCP interference.


However, should you want to make use of multiple Internet access lines (each with it's default route) or similar things, special things need to be taken care of:
[LIST]
[*]you need to keep track of the existing "communication essions" 
[*]make sure that one "session" always uses the same NIC to leave your box and expects return traffic on that NIC.
[*]you have to rewrite and reroute packets so the always leave the Box through the correct NIC using the correct t source IP address and are addressed (at Layer 2) for the respective next hop router.
[/LIST]

Things like that should be doable with iptables; rhere's guides around that show how to use multiple Internet accesses simultaneously with iptables - but this is advanced stuff. Be sure to check that Link about Linux Advanced Routing & Traffic Control that was posted in this thread.

It's only *after *you have sorted out the routing issues that you can go ahead and start binding applications or services such as Apache to certain interfaces as Mr.C. suggested.

best regards

Marc

---

### Post by hyper_ch on 2007-07-26
actually

eth connects to my router (and the router to the internet) and has a static IP:
10.0.0.5 / 255.255.255.0 / 10.0.0.1

wifi connects to the university network and has a dynamic ip
192.x.x.x

So they are in different subsets. I want to make some services just available on the university network and not to the whole internet...

---

### Post by netztier on 2007-07-26
> **hyper_ch said:**
> actually

eth connects to my router (and the router to the internet) and has a static IP:
10.0.0.5 / 255.255.255.0 / 10.0.0.1

wifi connects to the university network and has a dynamic ip
192.x.x.x

So they are in different subsets. I want to make some services just available on the university network and not to the whole internet...

ah.. then you have the case that can be solved quite easily: default route towards the Internet router, static routes towards the university router
[LIST]
[*]Configure eth for your local router subnet and make sure that the default route points towards the internet router.

[*]Configure wifi for the university network, and be careful that this configuration does not generate another default route entry. Add some static routes in a way that they point to the next-hop router of your uni's network.
[/LIST]
Remember that network-manager currently has a (IMHO) severe limitation: it allows only for one active interface among the ones it manages. You'll have to cleverly select which interface to configure statically (and therefore unmanaged by NM) and which (if needed) to be managed by network-manager and it's WPA abilites.

best regards

Marc

---

### Post by hyper_ch on 2007-07-27
Ok, I need now information on how to do those static and default routes... I guess I can find that out somehow...

But how do I tell then certain applications only to use one of those? will I setup the static routes with a port? So that all connection from/to a specific port will be routed thourgh the wifi (university/static route) card?

---

### Post by netztier on 2007-07-27
> **hyper_ch said:**
> Ok, I need now information on how to do those static and default routes... I guess I can find that out somehow...

Basically: run a shellscript that adds routes when the interface comes up. In /etc/network/interfaces, you can add a statement for an interface that starts with "up <shellscript>", just like you configure the ip address:

```
iface wifi0 inet static
 address 192.x.x.x 
 netmask 255.x.x.x
 up <shellscript>

```

Nota: **no** gateway statement for the interface towards the university networks! It's the shellscript that is going to set the routes for the university networks! Be sure to read **man route** to learn how to write static routing configuration statements.

> **hyper_ch said:**
> But how do I tell then certain applications only to use one of those? will I setup the static routes with a port? So that all connection from/to a specific port will be routed thourgh the wifi (university/static route) card?

The thing is: your routing table will pick the interface for you. If the destination address of the IP packet your machine is sending out matches the default route, it will be forwarded to the Internet Router through eth. If it matches a static route, it will be forwarded to the next-hop uni-router through wifi.

With such a setup, **Interface and route selection is done implicitely via the destination IP address, not by the application itself.**

Now if you want to limit a server running on your local machine (say.. an Apache or an ftp server), you must configure the application itself to "bind" or "listen" only to (a) certain IP address. So if you "bind" Apache to the wifi interface, it will not answer requests coming in on eth - it won't even open a listener on port 80 on that interface.

If this is relatively simple setup doesn't meet your requirements, you'll have to read deeper into advanced routing.

best regards

Marc

---

### Post by hyper_ch on 2007-07-27
Thx, I'll try that now :)

---

