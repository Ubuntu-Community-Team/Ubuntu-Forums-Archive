---
title: "Ports and Azureus"
date: 2005-10-02
forum: Networking &amp; Wireless
---

### Post by WhoKnows on 2005-10-02
I have only on port  (113) open but when i set azureus to use it. Azureus says that thereis an NAT problem. But I don't have any routers or anything with NAT. What should I do , so Azureus would work?

---

### Post by mlomker on 2005-10-02
[QUOTE=WhoKnows]I have only on port  (113) open[/quote]

You mean one port in your software firewall or what?  I find it surprising that you don't have any NAT on your connection...that's unusual these days.

You'll want at least 6 ports in a row open.  Clients will make an initial connection on the first one and then get reattached to the others.

---

### Post by WhoKnows on 2005-10-02
No I mean one port is opened. Others areclosed by ISP. In XP it war enough to download with Bitcomet in full speed. I think I should congigure something, but what so it could work.

---

### Post by mlomker on 2005-10-02
> No I mean one port is opened. 

Why would the ISP be blocking all incoming traffic to your machine other than IDENT (a port that is normally blocked for security reasons)?  That doesn't make any sense.  If they are blocking traffic then there isn't anything that you can do about it from your machine.


Edit: had to look up what 113 was.

---

### Post by WhoKnows on 2005-10-02
Its to "protect me" . When its possible to use bittorrent in windows shouldn't it be possible in Ubuntu?   Translation from my ISP homepage " all incoming TCP connections are blocked axept answering packets towards client." But port 113 is open and Bitcomet uses it perfectly in XP.

---

### Post by mlomker on 2005-10-02
I don't know the answer, then.  There are a lot of bitorrent clients...try rufus or one of the others.

You've used something like [Shields Up]("https://www.grc.com/x/ne.dll?bh0bkyd2") to verify that port is open?

---

