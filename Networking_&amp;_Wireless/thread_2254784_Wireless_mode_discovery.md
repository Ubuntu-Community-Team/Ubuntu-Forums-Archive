---
title: "Wireless mode discovery"
date: 2014-11-30
forum: Networking &amp; Wireless
---

### Post by pwabrahams on 2014-11-30
I've been posting lots of questions on this forum, so I'm pleased to have the opportunity to report a discovery.

Here's the problem I was dealing with: I've acquired a TL-WR841N router, though this discovery might apply much more widely.  I was unable to get wireless connections working, although I was in fact able to ping the router at 192.168.0.1 in wireless mode.  I just couldn't contact any other IP addresses, not even on the same network (e.g., 192.168.0.20).  All such IP addresses were accessible via a wired connection from the very same laptop, however.

Since a connection was vislble, I tried editing it.  I noticed that the "mode" was set (by default, presumably) to Infrastructure.  Without really knowing what I was doing, I tried changing it to "Access Point".  And all of a sudden, all my connections worked.  I happen to have an Android phone, and from what I read, the access point mode might be necessary for Android phones.  But this behavior had nothing to do with the phone -- I could have the phone turned off and I still had the same experience.  What's more, it seemed that once I got the connection working in Access Point mode, it then worked in Infrastructure mode also. (Of course, I don't know how long it will continue to work in Infrastructure mode.)

I'm quite curious as to what's going on -- but at this point my problem seems to be solved.  My general (if possibly wrong) conclusion is that if wireless doesn't seem to be working, try changing the Mode to Access Point.

---

