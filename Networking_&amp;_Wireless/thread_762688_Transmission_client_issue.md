---
title: "Transmission client issue"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by fxguenea on 2008-04-22
Hi there.. I've recently had some issues with the download rate... Last night it was like ~210 KBseg and now it dropped to ~25 KBseg. I've been trying with Firestarter and router's forwarding, etc, since yesterday, but decided to let it work on its own.. (Transmission 1.11 has a router forwarding option for the desired port and I also keep the port open from de iptables [with a method adquired by forum search])...

The thing is: is that download rates may differ from time to time due to the seeders "generocity"?? or i did something wrong that made download rates fall down?

Oh, I also noticed that after I leaved the torrent running (at ~210 KBseg lastnight) and woke up this morning and saw it working at ~25 KBseg a message  like this was on the torrent info :"Tracker not responding... Retrying" or something like that. It tried to fix it up by some forum look out, but It didn't turn out as I wanted. Finally, just installed a newer version of Transmission to see how it worked... pretty much ~35 KBseg..

Anyone ?

Thanks a lot!

---

### Post by Kebabman on 2008-04-22
This could be due to a number of reasons.

Your ISP may well rate limit you at peak times, such as during the day, but not at night time. My ISP does this and it is written into their Fair Usage Policy that this will be done.

If the tracker is not responding, this might stop you from connecting to new peers, which will likely slow your downloads. This is most likely due to a tracker being down, try to find more trackers.

It could also just be the nature of downloading from a torrent. If you are connected to few seeds and lots of peers then the download is likely to be slower. This is just the nature of the BitTorrent protocol unfortunately.

---

