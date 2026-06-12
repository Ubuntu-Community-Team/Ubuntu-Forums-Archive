---
title: "Retrieve forwarded IP in SSH"
date: 2014-04-24
forum: Networking &amp; Wireless
---

### Post by maver1k2 on 2014-04-24
I have a usecase where SSH request go through a load balancer. in order to provide Client IP visibility to servers, the LB does Client IP forwarding. Now is there a way to have the SSHD retrieve the forwarded IP, like something similar to X-Forwarded-for in HTTP ? Thanks.

---

### Post by SeijiSensei on 2014-04-25
It sounds like it's using a form of network address translation so the answer is no.

X-Forwarded-For is an "application-level" protocol.  You'd need to have customized versions of the forwarding software on the load balancer and on the SSH server to add that information.  Plus it would add an enormous amount of overhead because that information would need to be included in every packet. 

That's one of the drawbacks of NAT; the originating IP address is rewritten.  I use application-level TCP proxies for some services, and the IP is overwritten in that case as well.  Any other solution would break routing.  If the traffic originates on 10.10.10.10 and passed out from the load balancer at 192.168.1.100, the recipient machine wouldn't know how to reach 10.10.10.10.  Simply passing reply traffic out the default gateway wouldn't work.  That gateway might not know how to reach 10.10.10.10 either.   So the replies are sent back to 192.168.1.100, which knows to forward them back to 10.10.10.10.

You might be able to create a set of routing rules on the Cisco that would preserve the address, but I can't help with that, I'm afraid.  I haven't thought much about that approach, and I have no experience configuring Cisco equipment.

---

