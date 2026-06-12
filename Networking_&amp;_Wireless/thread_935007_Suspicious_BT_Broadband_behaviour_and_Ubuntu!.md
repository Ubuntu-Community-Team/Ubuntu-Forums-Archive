---
title: "Suspicious BT Broadband behaviour and Ubuntu!"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by jesushero on 2008-10-01
I have been using BT's Broadband service (in England) for a while now, and lately I have been experiencing some weird problems. All of a sudden, usually during night-time, there are service outages that last for several hours. However, the suspicious part is that these seem to only be HTTP outages, in that I can't access anything from an http server, but I can still access other network services, such as VPN, SSH, and so on. The even more weird part is that I can VPN to another network and access HTTP services normally, but as soon as I switch back to my own connection, the access is gone. 

Pings work perfectly during this, with normal round-trip times.

I have called BT Customer Service a couple of times and they were trying to blame it on Linux, saying that it is normal for Linux users to experience such problems since it is unsupported!! I have been trying to convince them that since I've been using Linux exclusively in ALL of my computers and they all work fine and HTTP still works within my home network, then it must be something that they are doing!!

There are two ways this can be fixed when it occurs: 

One is to reset the router, which gets a new IP address and then works. 

The other way is to wait for 10 hours and it usually has been restored.

Is anybody else experiencing such problems? Can anyone shed some light as to what might be causing this? 

I believe it's either that the BT HomeHub is causing it, which is not impossible, but I've been using the same HomeHub for more than a year now and this is only happening in the past two months, or it is that BT tries to filter my own Apache Server running on one of my machines! (When the outage occurs, it is impossible to access my home server through HTTP from outside the local network)

I am extremely annoyed that they are trying to blame their own inability to provide a decent service to Linux! I'd really like to find out exactly what this is and rub it in their face! If they are indeed purposely filtering it and there's a way to prove it, I'd consider legal action.

---

### Post by murphykieran on 2008-10-01
I'm on a BT broadband connection in Ireland and I'm having similar problems, but it's not unique to Linux.  There's a Dell Windows XP box here that the internet goes bonkers on at the same time, and the issue first arose when I had XP on this machine here and there were on Linux machines connected to the network. It's also not the router they provided because they provided just a hardwired one that I later replaced with a wireless one to work with a laptop and both had the same problem.

It doesn't go out for hours on end like you described (it has but it's pretty rare), but HTTP does stop working sometimes but HTTPS sites work fine, and other internet apps like BitTorrent downloads work okay. Generally rebooting the router solves the problem.

I phoned them and when they asked me to do something in Windows I explained I had Linux and their tech support claimed that was the problem.  Then when they found out I had replaced the router, they decided that was the problem, even though I explained that the problem first arose with the original router. I gave up arguing with them in the end, they insisted I contacted eircom who own the landline, but they claimed the line was fine and it was my ISPs problem.  I sent off 2 detailed emails to BT Ireland tech support, but they didn't even reply to either of them.

I think it's just a crap broadband service and useless tech support.

---

### Post by Kevbert on 2008-10-01
I used to use BT Broadband when it first came out and suffered similar problems.  You may find that they take local servers, amongst other things, down for maintenance during quiet periods.  I had this problem under Windows XP (before I discovered the wonderful world of linux).
If you have Sky TV, you could try them instead.

---

### Post by jesushero on 2008-10-01
> **murphykieran said:**
> I phoned them and when they asked me to do something in Windows I explained I had Linux and their tech support claimed that was the problem.  Then when they found out I had replaced the router, they decided that was the problem, even though I explained that the problem first arose with the original router. I gave up arguing with them in the end, they insisted I contacted eircom who own the landline, but they claimed the line was fine and it was my ISPs problem.  I sent off 2 detailed emails to BT Ireland tech support, but they didn't even reply to either of them.

I think it's just a crap broadband service and useless tech support.

> **Kevbert said:**
> I used to use BT Broadband when it first came out and suffered similar problems.  You may find that they take local servers, amongst other things, down for maintenance during quiet periods.  I had this problem under Windows XP (before I discovered the wonderful world of linux).
If you have Sky TV, you could try them instead.

Thanks! I was pretty sure that it wouldn't have anything to do with the operating system, but confirmation is always good! The router part is also very useful!

I don't think it has to do with routine maintenance of their systems, since it only affects HTTP and is solved by resetting the router. BT's customer service is worse than unacceptable, I'd advise anyone with other options to stay well clear of BT. 

Was anybody else with such problems running Apache or any kind of HTTP server? I find it quite suspicious that this is the only service that goes down.

---

