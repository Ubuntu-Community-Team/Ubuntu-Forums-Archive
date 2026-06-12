---
title: "Didnt understand IP addressing?"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by 7raTEYdCql on 2008-10-06
I personally didn't understand the concept of IP addressing.
These are the doubts that i have:
1) If a IP address can be resembled by a.b.c.d then and if each a,b,c,d can take approx. 240 values. Does it mean that simultaneuously 240^4 computers can be connected online. Is this correct?

---

### Post by 7raTEYdCql on 2008-10-06
I personally didn't understand the concept of IP addressing.
These are the doubts that i have:
1) If a IP address can be resembled by a.b.c.d then and if each a,b,c,d can take approx. 240 values. Does it mean that simultaneously 240^4 computers can be connected online. Is this correct?
2) Then when i came to the concept of Subnet mask i began to think it this way. The subnet mask is what classifies you under a ISP. Therefore everyone within a IP has the same Network address.
3) Then my friend told me this. A IP address is what is assigned to ISP, and we are given private IP's within the public IP's of the ISP. This is what happens in an organization. When i was told this i got confused. Can someone please give me a cut through definition of how everyone in the world has a different IP address?? Cause that should mean that there are not enogh IP's, but that is not the case.

---

### Post by cariboo on 2008-10-06
Have a look here, this may help you understand ip addresses a little better:

[http://www.networkcomputing.com/netdesign/ip101.html](http://www.networkcomputing.com/netdesign/ip101.html)

Jim

---

### Post by leg on 2008-10-06
Something like that. The four quads of the dotted quad notation (a.b.c.d) is split to represent the network address and the host address. These can take the form of class c <ne.two.rk>.host, class b <net.work>.<ho.st>  and class a <network>.<h.o.st> . 

The number of hosts that can be addressed on a class c network is 254 because only the last quad is used to represent the hosts. Each quad is represented in a byte which has a maximum value of 2^8 (256) which are 0 - 255. you can't use the last address as it is used as the broadcast address and zero can't be used as it is the same as the network address. 

expand this for each class so for a class b address two quads are used for the host. Two quads are represented in two bytes (16 bits) so can represent 2^16 - 2 hosts.

Class c can represent 2^24 - 2

And ipv6 is becoming more popular and I don't have a clue about that yet.

Hope this is both accurate and helpful.

Consequently the earth is, of course, flat.

---

### Post by Iowan on 2008-10-06
Should probably mention [CIDR]("http://compnetworking.about.com/od/workingwithipaddresses/a/cidr_notation.htm"), (cariboo907's link does) which is Classless Inter-Domain Routing.
Might also mention [private IP addresses]("http://compnetworking.about.com/od/workingwithipaddresses/f/privateipaddr.htm") since one of the questions in your [other thread]("http://ubuntuforums.org/showthread.php?t=940007") touched on them.  Might as well throw in a link about [NAT]("http://compnetworking.about.com/cs/tcpipaddressing/g/bldef_nat.htm") since that's the answer to the last question in your other thread.

---

### Post by bapoumba on 2008-10-07
Threads merged.

---

