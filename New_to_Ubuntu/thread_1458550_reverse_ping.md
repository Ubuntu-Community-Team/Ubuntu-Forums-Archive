---
title: "reverse ping"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by B34ST1Y on 2010-04-20
In theory, a NAT device, such as a router allows outgoing traffic with no quarrels (i.e. PC1 sends http GET from [www.google.com](www.google.com) ...goes to router -- to google -- back to router -- back to PC1 with packet flow) ......so it stands to reason that the router inspects the incoming packet from the Internet to see if the packet knows where its supposed to go.


Getting to my point, wouldn't it be possible for someone to craft a packet that already "knows" where to go, and initiates the connection from the WAN? Isn't this terribly insecure? 


Some insight on this matter would be greatly appreciated. >.<

---

### Post by OriginalName on 2010-04-20
[http://en.wikipedia.org/wiki/Network_address_translation](http://en.wikipedia.org/wiki/Network_address_translation)

> As described, the method enables communication through the router only when the conversation originates in the masqueraded network, since this establishes the translation tables. For example, a web browser in the masqueraded network can browse a website outside, but a web browser outside could not browse a web site in the masqueraded network. However, most NAT devices today allow the network administrator to configure translation table entries for permanent use. This feature is often referred to as "static NAT" or [port forwarding]("http://en.wikipedia.org/wiki/Port_forwarding") and allows traffic originating in the 'outside' network to reach designated hosts in the masqueraded network.

---

### Post by Drenriza on 2010-04-20
I cant see how.
 
#1 Nat has 2 ip-addresses. A local one 10.x.x.x or 192.168.x.x and a WAN one. (which can be anything, determined by your ISP)
 
#2 When on the WAN you use ip-addresses to get from point A -> B.
When on your local-network (switches) you use your NIC,s mac-address to get from A -> B
 
So for this to work, a package should know. Your online address, your local address and your mac-address. Also routers can have firewalls enabled, to sort packages out.
Or only packages on specific ports can go through the routers firewall.
 
and so on and on. So i cannot see how it would be possible.
 
Also IF such a package would get into your pc. It needs to get past your anti-virus/anti-mallware programs. And install itself undetected.

---

### Post by undecim on 2010-04-20
When you make a connection through your router to the internet, the router stores information about that connection for as long as the connection remains. If an attacker were to try to send packets around the router like that, they would need information about the connection. In other words, they would need to spy on your connection and get a packet first.

And even then, there's no much that just a few packets getting through can do. Unless you have an attack that exploits the TCP/IP stack of the target computer or are communicating with a rootkit already on the computer, the connection that was already made determines what port it will hit and what application will recieve the data.

If any attacker has the ability to eavesdrop on your connection, I think that a bigger concern would be [http://en.wikipedia.org/wiki/Man-in-the-middle_attack](http://en.wikipedia.org/wiki/Man-in-the-middle_attack)

---

