---
title: "Ubuntu IPv6 Redirect functionality issue"
date: 2013-10-03
forum: Networking &amp; Wireless
---

### Post by hrisikeshsahu on 2013-10-03
Hi All,
I am facing a routing issue for the IPv6 Ready logo Interoperability  1.5 topology. Ubuntu is used as the one of the target router for this interopearbility test.

Please find the attachment of the exact topology map.
 
As per test setup –
Ø  Configured REF-Router2 NOT to transmit  Router Advertisement on Network1. But REF-Router2 is able to transmit Router Advertisement on Network2 with 2001:db8:ffff:3::/64 .
Ø  Configured a static route on TAR-RouterD ( ubuntu) Indicating REF-Router2’s Link local address as the next hop for the Network2 . 
Ø  But Ref-Router Not able to routes between Network1 and Network2.  Due to this ICMPv6 request from TAR-router to the global address of REF-Host2 is not working. There is no reply for this ICMPv6 request. 
Ø  Same when I try to transmit ICMPv6 Echo request from REF-HOST2 to global address of TAR-HOST1( Prefix of TAR-RouterD), no ICMPv6 reply. 
Ø  Within Network1 , nodes are able to communicate. But when I try to communicate Netwrok2 from Network1, it is not working.
 
Could you please suggest tell me if I am missing something to route the traffic on REF-Router ?
 
I suspect , as By default Redirect functionality is disabled in Ubuntu. I enabled in /etc/sysctl.conf  and still there is  no success. 
 
Please help me to find this solution.

---

### Post by hrisikeshsahu on 2013-10-03
Ubuntu is used as IPv6 router and it accepts ICMPv6 reply from the HOST( where HOST selected it is the best hop ). Ubuntu should send a redirect message in the ICMPv6 field.
I enabled /etc/sysctl.conf
> 
[FONT=Ubuntu Mono]net.ipv6.conf.all.accept_redirects = 1
[/FONT][FONT=Ubuntu Mono]net.ipv6.conf.all.send_redirects = 1[/FONT][FONT=Ubuntu Mono]
[/FONT][FONT=Ubuntu Mono]
[/FONT]

But no success
Please help me.

---

