---
title: "Problems with Ktorrent"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by psam3 on 2009-11-22
I'm having connection problems with Ktorrent on Ubuntu 9.04 and hoping to see if anyone can point me in the right direction. You can rest assured I used the search function to see about opening ports, but everything seems to be about routers. When starting a torrent, I get the stalled message so I figured I needed to open ports. The thing is though I'm not using a router, I go straight to my Comcast cable modem. Do I still need to open ports or is there something in Ktorrent I just need to adjust? I would appreciate any help, Thanks.

---

### Post by sandyd on 2009-11-22
> **psam3 said:**
> I'm having connection problems with Ktorrent on Ubuntu 9.04 and hoping to see if anyone can point me in the right direction. You can rest assured I used the search function to see about opening ports, but everything seems to be about routers. When starting a torrent, I get the stalled message so I figured I needed to open ports. The thing is though I'm not using a router, I go straight to my Comcast cable modem. Do I still need to open ports or is there something in Ktorrent I just need to adjust? I would appreciate any help, Thanks.
probably your a victim of [http://torrentfreak.com/comcast-lied-to-fcc-blocks-bittorrent-traffic-247-080515/](http://torrentfreak.com/comcast-lied-to-fcc-blocks-bittorrent-traffic-247-080515/)

you dont need to open ports. this is because ubuntu automatically opens ports as needed. (unless you were fiddling around with the firewal config)

---

### Post by psam3 on 2009-11-22
> **carlee said:**
> probably your a victim of [http://torrentfreak.com/comcast-lied-to-fcc-blocks-bittorrent-traffic-247-080515/](http://torrentfreak.com/comcast-lied-to-fcc-blocks-bittorrent-traffic-247-080515/)

you dont need to open ports. this is because ubuntu automatically opens ports as needed. (unless you were fiddling around with the firewal config)

So Comcast is still throttling traffic? I thought they stopped after the big uproar with that

---

### Post by JoJerome on 2010-01-10
Reviving this thread as it sounds like we're having the same problem.

Just installed Karmic on a Compaq laptop. My friend was using the same wireless network for torrent downloads under Vista, so we know it's not a router or ISP issue.

Under KTorrent, it simply says "Stalled" as the status on any new torrents. Any known issues? Workarounds?

It's been a while since I used KTorrent but I remember loving it. Once upon a time in Hardy, on a different machine.

---

### Post by Eisenwinter on 2010-01-11
Have you checked the trackers?

Go to the trackers tab in Ktorrent, and see if the trackers are active.

Sometimes the trackers aren't active, or you don't have any active seeds at the moment, so the download is stalled.

---

### Post by JoJerome on 2010-01-18
I think I figured it out. I think. But if anyone wants to correct (or approve) my homework here, I'd be happy for the help!

1) The day I posted, the network connection was awfully slow. I've noticed no matter the OS, no matter the BitTorrent program I'm using, if the connection gets too sluggish the torrents seem to get tired and give up (for lack of a better analogy).

2) My friend had like two dozen torrents going at once. I also find the more torrents going the more it gets sluggish and the more of them seem to get tired and give up.

This Karmic install is a Windows replacement for a friend who knows very little about computers. I gave him the 10 minute lesson on torrents; what they are, how they're working, why it's a good idea to only download/upload a few at a time.

It also seems to me that having too many torrents going at once might be an alarm to those who would prosecute for downloading/uploading? I have no idea how they actually check, but I would think that a sudden, major suck in bandwidth during certain times of day, from one certain IP address, would be a red flag.

I so far only know one person who's been warned by studios via her ISP (Comcast). Twice. Not sure how she got on their radar, but from what I'm hearing, Comcast has more of a reputation for cracking down on torrents?

---

