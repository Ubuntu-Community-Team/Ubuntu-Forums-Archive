---
title: "Wierd Wireless Annoyance"
date: 2006-09-01
forum: Networking &amp; Wireless
---

### Post by etotehpii on 2006-09-01
I've been running dapper for about a month now and its been working fairly well so far.
I'm running a Linksys WMP54G wireless card connected to an Apple Airport Extreme.  Up until a week ago there hasn't been much of a problem.
Except everytime I boot I have to deactivate and reactivate ra0 in order to connect.
Just recently (as in the past week).  I can no longer just deactivate and reactivate ra0.  If I do this it will just idle and wont connect.  What I have to do now is go into properties.  Switch to Plain(ASC II) then back to Hexademical and retype the password.  After I've done this it will connect just fine.

I have no idea why this works and how I managed to create this annoyance.

Any suggestions?

Thanks

---

### Post by randell6564 on 2006-09-01
> **etotehpii said:**
> I've been running dapper for about a month now and its been working fairly well so far.
I'm running a Linksys WMP54G wireless card connected to an Apple Airport Extreme.  Up until a week ago there hasn't been much of a problem.
Except everytime I boot I have to deactivate and reactivate ra0 in order to connect.
Just recently (as in the past week).  I can no longer just deactivate and reactivate ra0.  If I do this it will just idle and wont connect.  What I have to do now is go into properties.  Switch to Plain(ASC II) then back to Hexademical and retype the password.  After I've done this it will connect just fine.

I have no idea why this works and how I managed to create this annoyance.

Any suggestions?

Thanks

Hi! Not posative, but this sounds like a configuration issue within your routers security page. I'd have a look there and see if anything has changed.

---

### Post by Scunizi on 2006-09-01
After messing with wireless for a little bit I found a referance that Ipv6, which is implemented in Dapper by default, can cause some issues with wireless connections.  It seems fairly painless to deactivate and won't hurt your system to not have it there.  You'll find a referance on how to deactivate it in the Wiki located here...[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4).  I hope that solves your issue!

---

### Post by etotehpii on 2006-09-01
Yeah I think that did it.  All I have to do is deactivate and reactivate ra0 and its working fine so far.  Its too earily to tell but I think things are running a little faster now.

Thanks for your help

---

