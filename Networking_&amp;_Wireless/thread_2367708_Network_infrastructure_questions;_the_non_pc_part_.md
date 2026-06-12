---
title: "Network infrastructure questions; the non pc part of it"
date: 2017-08-02
forum: Networking &amp; Wireless
---

### Post by cheese66 on 2017-08-02
I have been reading an article about routers some days ago.
They were mentioning something about how to make devices on a LAN safer by modifying the ip-address used by the second router.
(i.e. first router inside ip 192.168.1.1 and then second router inside ip to 192.168.2.1)

My question is, is this true for a LAN to WAN configuration of two routers? Does it really make it safer for(not) reaching devices on a LAN from the internet?

Also, I would like to verify whether a DMZ configuration between two routers makes a LAN safer too. I believe that some say this is, while my mind says this is only the case when there are services pulled by other devices from servers between the routers.

Last two.
Does NAT make traffic safer? It does check whether packages are asked for, right? Or is this only the case when there are also firewalls active in a NAT-device?

Some on reputational places say that a two routers setup should *not* be chosen. They are really against this. Is this because there is double NAT configuration then?
Why does my read article where I started this topic with does not mention this?

Thank you.

---

### Post by TheFu on 2017-08-02
Everyone has different levels of knowledge and skill.  NAT helps low-skilled people, but it doesn't replace a good firewall.

Article writers aren't any different. They are full of opinions.

Network security should always be layered. There should always be AT LEAST 2 levels of protection for everything you care about.
There are 50,000 ways to solve any issue.  Only you can judge what is enough for your needs, your skill, your knowledge.  Overly complex solutions that you don't fully understand are just as bad as simple solutions that don't meet all the needs.

I have never used a DMZ config - if you mean a checkbox in a home router config.  I use multiple subnets to segment different types of equipment from each other and have firewalls that only allow selected ports/protocols between those specific subnets.  For example, my guest wifi subnet cannot access the server or secured desktop subnets except through the WAN ports.  I want the WAN router to provide some protection - it already blocks about 7K internet subnets from around the world which have caused problems/attacked previously.

2 bad firewalls (like any consumer device that doesn't have monthly updates) isn't always better security.  Firewalls seem like easy thing, but they aren't.  There is a vast difference between what can be done in router-based firewall and a firewall running on the client machine.  You need both if you don't force all clients to use a proxy server for all non-LAN data connections.  If your router/firewall doesn't provide updates at least monthly, then you need a better solution.

Or I could be completely wrong.

---

### Post by johndough2 on 2017-08-03
Hi

They were mentioning something about how to make devices on a LAN safer by modifying the ip-address used by the second router.
(i.e. first router inside ip 192.168.1.1 and then second router inside ip to 192.168.2.1)

TRUE.

But it really has very litttle to no actual security level, and for domestic usage behind a firewall it's adequate.

So as TheFu states the better the firewall, the better the security.

---

### Post by nariub on 2017-08-03
yeah NAT in itself hides you from some port scans because it overloads the ports on the single public IP. If a scan comes into a port that is not active or mapped statically (some people do this..), if the port is not active in a NAT session the packet is dropped.

Layer a firewall in the middle of that and you got a bit better security.

Put in an active IPS/IDS and it gets better
Put in anomaly detection a little better.

But the double NAT of two routers .. not really unless you are like me and travel hotels alot.. I light up my own router and SSID within my room to protect me from the hotel folks on the hotel's private subnet.   and gives me more devices i can hang off the single hotel connection.   Double NAT really doesnt hurt that much either.

---

