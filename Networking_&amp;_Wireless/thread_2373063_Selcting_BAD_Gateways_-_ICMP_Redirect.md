---
title: "Selcting BAD Gateways - ICMP Redirect"
date: 2017-10-02
forum: Networking &amp; Wireless
---

### Post by mmethw2003 on 2017-10-02
Hi All,
I have a Server with " ***Ubuntu 12.04.5 LTS*** " and it's connected as follows.


Server -----> SWITCH -------> R1
                       |    |------> R2
                       |---------> R3

Switch and Router interfaces are in the same subnet ( 192.168.0.0/24 ). Server Gateway set R1 ( 192.168.0.1 ).

[SIZE=3]**Issue :-**[/SIZE]
* For some destinations it tries to take other gateways ( like R2 & R3 )

[SIZE=3]**Things Done :-**[/SIZE]
* Created a specific route towards the destination. It works for nearly  one hour and normalized back to take other IPs as gateways.
* Restart the NEtwork interface , same as above work for hour or two.

[SIZE=3]**Findings :- **[/SIZE]
By doing few digging I found out that this happened due to " ICMP  Redirect ". So I edited the sysctl file and disabled ICMP redirects.

But Still am getting this issue. Appreciate If some one can guide me regarding this .....

---

### Post by ajgreeny on 2017-10-02
Ubuntu 12.04 is now EOL (End Of Life) so you should upgrade to, or clean install, a fully supported version as using 12.04 you will get no further updates to any packages; this is a huge security risk, particularly for a server.

I recommend that you use 16.04.3 which will be supported until April 2021

---

### Post by slickymaster on 2017-10-02
Thread moved to **Networking & Wireless** for a better fit.

---

### Post by cabsil on 2017-10-04
ICMP redirects are generated when the router thinks that your traffic is being inefficiently generated. 

There are several rules governing the use of ICMP redirects and their acceptance into a host&#8217;s routing table.  Before an ICMP redirect is generated, the following restrictions are typically adhered to on most of today&#8217;s routers:
 
1.      The outgoing and incoming interface of the packet must be the same.
2.      The IP source address in the packet is on the same logical IP network as the next-hop IP address.
3.      The route used for the outgoing packet must not be an ICMP redirect or a default route.
4.      The packet does not contain an IP source route option.
5.      The gateway must be configured to send redirects.

A few questions:
1.  All of the routers are in the 192.168.0.0/24 subnet?
2.  What is an example of a destination that does has this behavior? 
3.  What do the outside interfaces of the routers look like?  If all the internal ips are in the 192.168.0.0/24 subnet.  What are the external IPs? Public IPs? 
4. Is there a reason why you need the traffic to go through R1 instead of R2 even if R2 is the smarter path? 



Ultimately, I'm thinking that R1 thinks that the path to the destination is through R2 or R3. It knows that the server can get directly to R2 or R3, so it tells the server to just go there instead.

---

