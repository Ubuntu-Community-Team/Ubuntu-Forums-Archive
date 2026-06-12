---
title: "Transmission and Ubuntu"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by squishy121888 on 2009-08-05
Hello. Currently my girlfriend and I [on the same network] are both running Linux distros. Hers is Mint, and mine is Ubuntu 9.04. Both of us seem to have greatly varying speeds on our copies of Transmission. For example, one file took me about 7 hours and took her about 30 minutes. 

When I look at her's, she has a very small number of peers which she is downloading from [Likw 10 out of 12], and I have maybe 10 peers I am downloading from [But around 120 connected peers].

How do I remedy this? My PC has a faster write speed, so if anything I would assume that I should be getting a better speed. Is it the client t's self? I set both of ours up, so I don't see how that would be. Is it that she is using a different distro? Any help would be appreciated/

[Note, my share ration is about 1.93, as by the time I've downloaded anything I've managed to give about twice it's file size]

---

### Post by starcraft.man on 2009-08-05
Torrents depend on many factors. Since you set both up and are using transmission identically on both, I'll run down list of things to check. FYI, share ratio irrelevant except to picky private trackers. On public trackers it's just up to concious.
[LIST]
[*]Forward one different ports to each machine (i.e. one gets 74432 and another 24992) for DHT.
[*]Ensure ports go through security like router.
[*]Ensure configuration identical on both, and configured properly.
[*]Get same torrent file with tracker.
[/LIST]
Now if your still going slow, I'm gonna assume your splitting the connection and her machine just happens to be hogging it. You can't saturate your HDDs ability to write from a torrent in my experience, especially not on most DSL connections. If your not both downloading at the same time, then I assume it's just random luck on getting the right peers at the right time. Some people have larger upload (like fibre users). If she continues to be lucky, I'd let her download and share files to your machine via samba.

---

