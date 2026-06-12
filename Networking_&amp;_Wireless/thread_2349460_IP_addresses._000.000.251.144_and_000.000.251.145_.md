---
title: "IP addresses. 000.000.251.144 and 000.000.251.145 - is there a connection?"
date: 2017-01-15
forum: Networking &amp; Wireless
---

### Post by rob-rushworth on 2017-01-15
Afternoon all.   I have a question regarding logged IP addresses of visitors to a blog.   As in the title, one is (redacted) 000.000.251.144 and the other one is 000.000.251.145  Are these addresses related?   As a partial Luddite but being semi-aware of technology, I realise that IP addresses are not like addresses in the physical world in that consecutive address numbers means that the houses are neighbours, but does anyone know if there's a possibility of one visitor being the other visitor too?  Thanks

---

### Post by TheFu on 2017-01-15
IPs are provided in blocks. Sometimes those blocks are related and sometimes not, look at the netmask for the network to see.  Cannot tell without the full, correct IP who has what.
Use whois and something like: [http://www.subnet-calculator.com/](http://www.subnet-calculator.com/) to determine what you can.

---

### Post by igdfpm on 2017-01-15
You have kind of redacted the important path and left the trivial ;) A very simplified answer...

IP addresses are assigned in "blocks" per provider. These may then be assigned to customers geographically, by which services the purchase, or by random, geographically across the planet etc etc

If the 1st 2 octets (000.000) are also the same you could say that the 2 addresses are from the same origin (provider) network. More than that is a judgement call - if the OS, device and browser are the same for both IP then you may be inclined to lump them together as one user (that user being assigned a different IP by their provider on 2 separate visits) but caution is advised as there are gonna be quite of your unique visitors running Windows 10 + Chrome...

---

### Post by rob-rushworth on 2017-01-15
Thanks for the replies.  
> You have kind of redacted the important path and left the trivial A very simplified answer...
  Ahh, sorry.  Yes, the first two octets are exactly the same.  For example:  abc.def.251.144 and abc.def.251.145  Then these are distinctly different addresses. That they may or may not be issued to two different people is the issue, correct?  If they were issued to the same person, then that person couldn't have both addresses at the same time, and there would be a change somewhere 'up or down the line ' in srecorded visits, meaning they wouldn't both recur repeatedly over time?  I have recorded visits from both IPs that continue for the same time period of days for both. The chances of  the same IP address being randomly issued to several people within the city and them all having the same interest in my blog seems slight. Likewise, the chances of one interested person being re-assigned the same IP addresses over and again, day in, day out, also seems slight, no?  No idea about things like browser, OS, or other details.  Given those details, is it fair to tip the decision towards there being two different visitors?

---

### Post by TheFu on 2017-01-15
Could be 2 roommates.

Or it could be 1 guy with a home server and multiple IPs who likes to run Wallabug (read-it-later clone).

I have a small public subnet and used different of those IPs for different purposes.  My usable range starts at x.x.x.145/29, so 144 is taken by the gateway.  But just because my subnet is a /29, that doesn't mean THIS specific subnet is also a /29.

What difference does it make?  Either they are being abusive or they aren't.  That's how I look at it.  IPs that used more bandwidth than google does get banned. IPs clearly attacking get banned - like anyone trying to access *php on my site are banned.  I don't run php on the interent due to the difficulty in securing it, at least for me.  For stuff that uses PHP, I require a tunnel/vpn to get internal access.

---

### Post by rob-rushworth on 2017-01-15
I have a recorded IP from an anonymous troll and one from someone known. Do I cut off the known dude due to the 'IP match' ?  100% he's a Luddite with no home server, public subnet, or any more knowledge of PHP than I have, which is zero.

---

### Post by TheFu on 2017-01-15
> **rob-rushworth said:**
> I have a recorded IP from an anonymous troll and one from someone known. Do I cut off the known dude due to the 'IP match' ?  100% he's a Luddite with no home server, public subnet, or any more knowledge of PHP than I have, which is zero.

Moderate the posts.

---

### Post by efflandt on 2017-01-15
Use **whois** command in a terminal window to see who owns the IP range.

---

