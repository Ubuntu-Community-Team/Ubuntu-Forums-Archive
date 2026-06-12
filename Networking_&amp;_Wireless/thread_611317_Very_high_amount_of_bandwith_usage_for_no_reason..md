---
title: "Very high amount of bandwith usage for no reason."
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by conniver on 2007-11-12
Hi,

I had noticed recently that my box uses very high amount of bandwith, which results in the wireless router knocking me off every now and than. Let me elaborate: I am running Kubuntu, and Gaim, and no other programs I am aware of, aside of essentials that run by default. If I am not at my computer it can eat up (according to vnstat) 100-300 MB of down in an hour. I consume 15-20 Gigs of down bandwidth in a week, when I haven't been doing much aside of occasional video on youtube and apt-get update/update. I have a feeling that I am being flooded for some bizzare reason.

Another thing -- I had similar situation before I used Linux. I had very high bandwith usage back when I used Windows, which makes things even more confusing. 

Does anyone have any idea of why such thing may be happening, or what should I use to investigate what is going on?

wbr,
Conniver

---

### Post by reckless2k2 on 2007-11-12
make sure you are not using bittorrent or limewire or another P2P on your network at all. lock down you router if you have one. cloak or disable your SSID, use encryption, and MAC filter. someone could be on your bandwidth and you not know it.

---

### Post by R00t3rMan on 2007-11-12
Get WireShark and see what the traffic is.  What's the BW of your Internet link?  Consider: 1 Mbit/sec for one hour = 450 MBytes (3600 Mbits).   100-300 MBytes does seem like a bit much for an idle computer.  Maybe you have a really chatty LAN :lolflag:

There IS a reason; it just isn't apparent.  WireShark has the answer.  Tcpdump is pretty good too it you like the cli.

---

