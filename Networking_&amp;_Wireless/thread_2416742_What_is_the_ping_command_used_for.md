---
title: "What is the ping command used for?"
date: 2019-04-14
forum: Networking &amp; Wireless
---

### Post by John_Patrick_Mason on 2019-04-14
I've read tutorials on how to properly use the ping command, but I've yet to find a tutorial that explains how you can use the ping command for troubleshooting problems on your network.

First off, why would you ping a website, say arstechnica.com, to check if a website is down? Why wouldn't you instead just open a browser, type arstechnica.com, and when you find the website is unreachable for some reason, try another website in your browser. If both websites are unreachable, then you can probably infer that you're suffering from some kind of network issue on *your* network. So, what's the point of pinging a website if you can just use a browser?

The second question I have is about pinging your router. What does this tell you?

Lastly, why do people find it useful to ping another host on their network, say a desktop? Why do some people find this useful?

---

### Post by patrick.f on 2019-04-14
It's all about what you want. 
Do you want to know if you can reach a website? Just open it in your browser and you know :)

But what do you do if it goes beyond that and you need/want to know, WHY it's not working?
In this case you need to break your tools as far as you can, and test every single stuff you can for itself.

Ping is running on an ICMP protocol. You Browser will send over TCP protocol (which http is based on)
This are differnt things.
Ping can even fail, while Http do work. (if the server's firewall is denying it)

If you access via an DNS, your browser will do a DNS resolution - which you can't see.
Ping will also do that, but you will see the result of it. (the IP)
A server can response to a ping (which means your network reaches it. Its alive), but the website will not show. (Dead webserver software?)


Ping is mainly a very low level tool to test if you can reach the other network-card, through all the internet.
Hope that helps

---

### Post by 1clue on 2019-04-14
Ping tests to see if a network interface is active and configured. I use it to test the status of various things, mostly to debug network problems.

If I can't reach a web site, I will sometimes ping the site. If the site pings but the web browser doesn't get a page, then that typically means one of these things:
[LIST]
[*]The web server service is deliberately turned off
[*]The web server service is unable to respond. Possible reasons would be that a script is hung (development box or bug) or the system might have trouble (out of memory, disk partition full, etc) but is still sane enough to respond to a ping.
[/LIST]

If the site won't ping AND the web page won't load, then it could be:
[LIST]
[*]Internet outage
[*]Denial of service attack
[*]Power failure on the server
[*]Server system turned off
[/LIST]

There are more possibilities, these are just things that come to mind.

If a system can't seem to make a connection at all (I'm installing a new desktop or server or whatever) then:
[LIST]
[*]If I can ping localhost then my network stack is running.
[*]If I can ping my link local address (192.168.x.y) then that network interface should be configured.
[*]If I can ping my router then my network cable is most likely working.
[*]If I can ping something on the other side of that router then I have a correctly configured netmask and router, and so does your remote box.
[/LIST]

The problem with 'something on the other side of the router' is that often public systems will refuse to answer ICMP packets. So you either need to know a public server that does respond to ping, or you need to find something else to use.

Another thing is that ping prints response times and percentage of dropped packets. If you have a problematic file server you can see if it might be related to the physical network or the "lower functions" of basic networking by using ping. A good connection has quick response which has relatively consistent timing between all but the first packet. The first packet may need to use a DNS lookup to get an IP address from a name.

In short, ping does not depend on some service being active, it only depends on a correctly configured network stack. Systems which block ping are technically operating with a flawed TCP stack, but there are valid reasons to block it.

---

