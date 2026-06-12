---
title: "Where Does IP's Originiate?"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by crazyjx23 on 2007-06-19
This may seem a little off from what normally is discussed in here, but I was curious about it. Anyway, I'm pretty good with network, I know all the protocols, theories, technologies, etc. There is always one thing that I can never seem to find out though. Where do the IP addresses come from? I know the process of assigning a "block" of IP's, but what I want to know is how do the get those IP's at that organization. Is it like DNS?? Or do they connect to ARIN directly like an ISP?? For instance lets say I want to get a group of IP address for my new hosting company and I don't want to got through an ISP. How would I get those assigned IP address directly from ARIN?? I'm sorry if this is just slightly confusing or out right stupid, but I was just curious. I doubt anyone will reply to this anyway......

---

### Post by crazyjx23 on 2007-06-19
LMAO Excuse my youthful ignorance...."Where Does" should be "Where DO" Oops

---

### Post by Mr. C. on 2007-06-19
You have to be a VERY, VERY big player before you'll get a block of IPs from anyone but your ISP.  They are reserved for the major backbone haulers and ISPs.  This has to do with a) efficiency, and b) there just aren't enough IPv4 addresses to give to anyone but the very largest internet providers.

Early on, IP blocks were given out to large corporations, universities, and other pre-"internet" users.  Companies such as IBM, GE, ATT, etc., had large blocks.  Slowly over time, these are aggregated to make routing easier and faster.

It was originally intended that IP blocks would be fairly geographical - so that router tables were as small possible.  Over time, as this become more complex, routing protocols were created to automate the process.  Still, it is important to keep IP blocks aggregated so that routing tables are minimized.  This is why you find, say, all of the 60.x.x.x/8 block allocated to Asia. On route entry to send it overseas.

Hope this answers your question a bit.
MrC

---

### Post by arvevans on 2007-06-19
[http://en.wikipedia.org/wiki/Internet_Assigned_Numbers_Authority]("http://en.wikipedia.org/wiki/Internet_Assigned_Numbers_Authority")
_._

---

