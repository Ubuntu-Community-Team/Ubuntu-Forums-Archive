---
title: "&#304;ptables + Squid Transparent Proxy problem"
date: 2013-12-16
forum: Networking &amp; Wireless
---

### Post by secoonder on 2013-12-16
Hello

&#305; am using Squid + &#304;ptables for my Firewall.I am confused about two problems.

1) We can think that squid is Layer 7 Firewall (support HTTP,FTP ...).. &#304;PTABLES is Layer 3-4-5-6-7 firewall(support ip,tcp,udp,http....)
In my own network;
 **i am using HTTP(Layer 7) at _Squid_ and i am using ip(Layer3),tcp/udp(layer4 ),http(layer 7) at_ iptables.._**
My question is ; When the packet comes to firewall , Who program(squid or iptables) will look primarily to the packet?
&#304; think answer is iptables.Because the packet goes from layer 1 to layer 7.What are your opinions ??
in shortly,a packet come to firewall,Who will look primarily it ?

2) i am writing one rule at iptables.&#305; want to deny from my network to 'one reel ip(for ex: 1.2.3.4)'...
if i am writing only ' iptables -A **INPUT** -d 1.2.3.4 -j DROP',       my  network users can not access 1.2.3.4.i understand this situation.
The packet pass the internet,but returning packet  cant passfrom internet to my network because of INPUT chain.it is true.
i am deleting above rule.And then, &#305; am writing bottom rule.

if i am writing only  'iptables -A** FORWARD** -d 1.2.3.4 -j DROP' , my network users can access 1.2.3.4 ?????... i think that  they can not access it. ???
Destination ip is 1.2.3.4. The ip is blocked.But they can access ? i dont understand.i think the packet should not pass at internet.???

Thank you.

---

### Post by SeijiSensei on 2013-12-16
You left out some important context here.  I'm going to assume every port 80 request goes through Squid either because you are using "transparent" proxying via an iptables rule, or all the clients' browsers are configured to use the proxy.  Also I'm assuming when you talk about "accessing" a remote site, you're talking about web browsing and not, say, making an SSH or IMAP connection to a remote host.

1)  Yes, iptables examines every packet before it is passed on to any application-level program like Squid.

2)  Your understanding of what happens when you block a remote site with an INPUT rule is incorrect, however.  With the simple rule "iptables -A INPUT -d 1.2.3.4 -j DROP" any packet arriving on any interface with that destination address is ignored.  The packet isn't being ignored on its return; it never reaches Squid in the first place much less generates a request to the remote site at 1.2.3.4.

3)  The reason why INPUT and FORWARD work differently in this case is because web traffic is not being forwarded through the gateway.  Web requests are sent to Squid which itself sends a separate request to the remote site for the content and passes it back to the browser.  No packets are "forwarded" across interfaces in this case, as Squid is working as a "proxy."  You send it requests, and it handles those requests on your behalf.  With the forwarding rule in place, your users should not be able to access any other service on 1.2.3.4 except web browsing on port 80.  If you have the forwarding rule in place, can the clients connect to an HTTPS site on 1.2.3.4?  I suspect the answer is no.

---

### Post by secoonder on 2013-12-16
SeijiSensei thank you for your answer
i forgot to write.My rules included "iptables -t  nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-ports 3128"
According to the above rule ; Every port 80 request go to SQU&#304;D,is it true ? . &#304;n this case , Should we say " if we use squid+iptables,we cant block port 80 request **on iptables**" ???
For Example ,i request at remote site..dest ip : 1.2.3.4 dest port :80..Squid is taking a packet. &#304;s the packet table dest ip: 1.2.3.4 dest port :80 ?? &#304;s Squid-proxy pass iptables ? Or, does squid change dest ip and dest port ?

you said that " can the clients connect to an HTTPS site on 1.2.3.4?  I suspect the answer is no"" .it is exactly true.i tried access [https://1.2.3.4](https://1.2.3.4) and i can not access.

INPUT means ; my firewall lan ip : 192.168.1.1 my firewall wan ip : 5.6.7.8..
Now , i tried this situation.
i am writing""iptables -A **INPUT** -p tcp --dport 22 1.2.3.4 -j DROP""" ..  But i can access 1.2.3.4...
However ; i removed above rule.and then i add rule:
                 iptables -A **FORWARD **p tcp --dport 22 1.2.3.4 -j DROP".. And i can not acces 1.2.3.4
According to this situation; INPUT is only study destination ip : 192.168.1.1 or 5.6.7.8 ??
May i question to you . 
which commands  to route between 5.6.7.8 and 192.168.1.1?  i make echo 1 >/proc/init/net/ipv4/ipv4_forward 1.does it need ? 
Thank You again.

---

