---
title: "Advanced Networking (dual ethernet) HELP!"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by ElJefeRocks on 2008-04-28
I have two ethernet ports in my computer, and I want to use one of them only for bittorrent traffic and the other for all other traffic.  Both will be plugged into the same router.  Will there be any benefit to this?

Currently when bittorent starts, net traffic to the computer slows down a lot (ssh, nfs), and I think it is because of the torrent traffic since the computer is sufficient to the load (Athlonx2@2.6ghz, 2gbram).

The ethernet ports are a marvell and a nvidia.

Thanks!

---

### Post by Swiftfeet8 on 2008-04-28
There wouldn't be any benefit to dedicating one of your ethernet ports to just bittorrent traffic.  What you could do is decrease the amount of traffic that your bittorrent application uses (ie. Azerus, Transmission, etc).  The bottle neck or slowness that you are experiencing when you have a torrent running is because the torrent is probably utilizing a large amount of internet bandwidth that you have.

Not sure on the specifics for each application, but you can adjust the speed up/down for torrents.  Let me know what application you are using and I can try to help ya more.

---

### Post by ElJefeRocks on 2008-04-28
I am using torrentflux-b4rt with the bittornado underbelly.  I have all of my torrents throttled and a QOS that works very well actually.  Internet traffic is not actually slow when the torrents are running, just traffic to the server computer (eg. ssh takes a long time to respond).  There is a music server also hosted off of this computer, so I would like to have some dedicated traffic between the ports, and set up a priority between the two of those even.

---

### Post by Swiftfeet8 on 2008-04-28
Ah, ok.  Hmm, lets see.  You could seperate your server and whatever ethernet port on your computer onto their own network.  Then just pass whatever traffic you want across that mini network.

If you would need your server to be on both networks (and don't have 2 NIC's) you can setup a virtual interface/adapter.  Let me know if you would need help with this, or if this helps you at all.

---

### Post by ElJefeRocks on 2008-04-28
Wouldn't this solution still have all of the traffic pass over that one interface though, and then simply route it in the computer itself?  Or do i understand wrong?

Can't I just tell the bittorrent program to only use a specific ethernet port, and then all traffic coming in would also only be to that port?

---

