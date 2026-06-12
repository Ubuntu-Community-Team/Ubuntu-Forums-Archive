---
title: "Need Help: DWA-552 and Linksys WMP300N - Cant get working properly"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by Carlo1973 on 2008-05-17
Hi there! Have weird issues with Ubuntu 8.04 regarding configuring my wireless network. First off, I've been using ndiswrapper up until now. 

I can get my Linksys WMP300N to connect fine if there is no encryption (no WEP, WPA, or WPA2), but as soon as I enable encrytpion it no longer connects. I have the WPA2 key I use stored on my flash drive and it works in windows but not in Linux.

My Dlink DWA-552 See's the network (granted only in G mode - 52Mbps tops) but never is able to connect - with or without encryption of any sort. 

Help getting this addressed would be great! my home network is setup for WPA2 due to the fact I live in a residential neighbour hood in an appartment where everyone one seem's to have a wireless connection. 


Carlo

---

### Post by SMB6009 on 2008-05-28
I'm having the same problem in Kubuntu 8.04, except I am using the Linksys WMP300N to connect to a Linksys WRT150N router. I can connect to public networks near my house, but I can't connect to my WPA-protected router. I am also using NDISwrapper.

Steve

---

### Post by Carlo1973 on 2008-05-29
Hey Steve - I actually got it working briefly, but it was extremly slow. Then I messed it up by installing something that caused my X-Windows drivers to go wonky to the point where i couldnt reconfigure properly in terminal. Had to reinstall and went back to my orriginal problem. I think I got it working tho by downloading the newer windows xp linksys drivers. But that still doesn't account for the connection to be slow. My system is maybe 20 feet from the router (1 room in between). The connection says it's running at 270MBps to the router, but it feels like its running a lot slower than that (IE: takes about 10 seconds+ before any webpages display and download speeds are not that impressive). When I go to windows on the same system, it works like a charm and connection flips through quite quickly (also indicating that the connection is 270MBps to router). If I don't use encryption, it works fabulously in Linux. 

I have to assume it is an issue in how linux works with WPA or WPA2

Still no response by anyone who knows how to fix this lol Seen guides on here for older cards, with a bunch of hacks. I haven't gotten around to trying them. They suggest not using NDISwrapper. Try doing a search on here and see if you can find the guide. When I get home from work tonight I will try to post the link in this forum

---

### Post by SMB6009 on 2008-05-29
Carlo

I did find this post on how to configure the WMP300N with a WPA- protected network. It didn't work for me, but it might work for you. I am currently testing out Kubuntu with the live CD. Maybe that affects it. Anyway, here is the post I found: [http://ubuntuforums.org/showthread.php?p=3284373]("http://ubuntuforums.org/showthread.php?p=3284373")

Steve

---

