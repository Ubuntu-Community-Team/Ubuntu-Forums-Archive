---
title: "IPv6 Gateway Not Routing"
date: 2013-12-09
forum: Networking &amp; Wireless
---

### Post by matt.lawrence on 2013-12-09
I've done a ton of research and have come up with nothing that works. 

Ultimately, we have setup a StrongSwan gateway in our network that gives out IPv6 addresses to VPN clients. These clients are able to successfully establish the tunnel and are able to ping the gateway's interfaces via their internal addresses. However, they are unable to ping any ipv6 address of clients within the network. On the gateway itself, I am able to ping the ipv6 interfaces of clients in the network without issue.

With this, we decided to create an isolated test environment to see if we could get the basics working. We followed this [official example ]("http://www.strongswan.org/uml/testresults/ipv6/rw-ip6-in-ip4-ikev2/")network by setting up only "Alice" "Moon" and "Carol" in order to see if we could ping. "Carol" is able to setup the tunnel, however, she cannot ping "Alice". The gateway itself is able to ping both. I've checked through the ip tables and routes as shown in the example and they all appear correct.

Is there something that is missing? My only theory is setting up masquerading, however, since the iptables are setup correclty, I don't see any reason for this to fail.

Thanks in advance.

---

### Post by 7182818 on 2013-12-10
Is IPv6 forwarding enabled on your gateway?

sysctl net.ipv6.conf.all.forwarding

If it is 0, try enabling it with 'sudo sysctl -w net.ipv6.conf.all.forwarding=1'

---

### Post by matt.lawrence on 2013-12-11
We had sysctl net.ipv6.conf.all.forwarding enabled (set to 1). However, it still didn't work.

Ultimately, the solution was to make static routes from the clients that needed to be reached from a VPN client. So for example, our VPN Client would VPN in normally, get a proper IP and would be unable to ping Server1. On Server1 we added a static route that pointed all traffic with a destination to a VPN Client address to go to the StrongSwan private interface.

As I understand it, before we did this, we would try to ping Server1 from the VPN Client and it wouldn't reply because the private interface of the StrongSwan wasn't replying to any NDP requests for the VPN Client IP range. I noticed that in the guide I linked above they setup a static route on their destination PC (for this example: Server1), so I'm thinking that this is normal, however, since StrongSwan 5.1.1 says it can fully route IPv6 this is a bit convoluded since it doesn't reply to any NDP requests for VPN Clients.

I've reached out to the StrongSwan devs for clarification or explanation as to why this is done like this, or if it's some sort of bug.

---

### Post by hamilleton on 2014-08-05
> **matt.lawrence said:**
> 
As I understand it, before we did this, we would try to ping Server1 from the VPN Client and it wouldn't reply because the private interface of the StrongSwan wasn't replying to any NDP requests for the VPN Client IP range. I noticed that in the guide I linked above they setup a static route on their destination PC (for this example: Server1), so I'm thinking that this is normal, however, since StrongSwan 5.1.1 says it can fully route IPv6 this is a bit convoluded since it doesn't reply to any NDP requests for VPN Clients.

I've reached out to the StrongSwan devs for clarification or explanation as to why this is done like this, or if it's some sort of bug.

Hello, and any updates on this? I got stuck in this ping6 stuff and maybe ICMPv6 flow problem as well. Static route do the trick but not suitable in my scenario. So I'm wondering if there are any other possible solutions? Thx a lot

---

### Post by matt.lawrence on 2014-08-05
What is your scenario? And is your problem the same as mine, or a bit different?

---

