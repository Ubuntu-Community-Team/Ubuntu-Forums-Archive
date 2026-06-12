---
title: "Transmission vs. utorrent"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by wirate on 2009-08-24
I ran a torrent with Transmission and it gave me nothing more than 40 KiB/sec download speed. Then I put the same torrent in utorrent and got 140 KiB/sec and thats the maximum I can have with my internet connection. Some problem with Transmission?

---

### Post by j7%&lt;RmUg on 2009-08-24
Not likely, it might just have sped up in the time it took you to swap from transmission to utorrent. I use transmission and i get maxed out speed most of the time (165 KiB/sec). You might have a low peer limit in transmission, if so just adjust the preferences.

---

### Post by credobyte on 2009-08-24
Plenty of possible reasons .. Ignore unencrypted peers, peer limit by itself, etc. - open Preferences and try changing "suspicious" values to something "better".

---

### Post by nikhilbhardwaj on 2009-08-24
since i have a slow connection(256 kb/s}
i limit my upload speed to 10Kb/s for each torrent this way 
i get a better speed while downloading

---

### Post by Codix121 on 2009-08-24
I also found utorrent to be much better than transmission. I get my full bandwidth on utrrent, up to 170, I even tried the same torrent once on utorrent and transmission, I only got up to 80-100kb/s. I don't know why but utorrent rocks! lol.

---

### Post by nhasian on 2009-08-24
i think you can run utorrent with wine, but I've never needed to.  I've tried Deluge, Transmission, and Vuze, and they all work great if you configure your router properly to forward the port.  If you havent been doing that perhaps utorrent is automatically forwarding the ports with uPNP with your router.  that may explain it.

---

### Post by Codix121 on 2009-08-24
Yeah utorrent does automatically forward your ports, I think it's why most people select it. They think it's "faster" when really it's just doing all the work for you :P! It's great for the lazy people like me! :lolflag:

---

### Post by wirate on 2009-08-24
then how do we do that in Transmission. I dont know what forwarding ports means at all :)

---

### Post by hyperdude111 on 2009-08-24
Try deluge, the UI is almost identical to utorrent.

---

### Post by andrew.46 on 2009-08-24
Hi waqar,

> **waqar said:**
> then how do we do that in Transmission. I dont know what forwarding ports means at all :)

I use a newer version of Transmission and this has an option in Preferences for uPNP, I add a screenshot that shows the details.

Andrew

---

### Post by pedro3005 on 2009-08-24
+1 for Deluge. I use it and get max speed all the time.

---

### Post by MrWES on 2009-08-24
> **andrew.46 said:**
> Hi waqar,



I use a newer version of Transmission and this has an option in Preferences for uPNP, I add a screenshot that shows the details.

Andrew

The default version from the repositories also has that option.

I use the svn version of rtorrent -- command line, but extremely light weight and fast.

Bill

---

### Post by andrew.46 on 2009-08-24
Hi MrWES,

> **MrWES said:**
> I use the svn version of rtorrent -- command line, but extremely light weight and fast.

I have rTorrent 0.8.0 which does not appear to support uPNP, has this been added in the svn?

Andrew

---

### Post by wirate on 2009-08-24
> **andrew.46 said:**
> Hi waqar,
I use a newer version of Transmission and this has an option in Preferences for uPNP, I add a screenshot that shows the details.  Better speed now. thnx

---

### Post by wirate on 2009-08-24
^^
Better speeds now. Thnx

---

### Post by powel212 on 2009-08-24
+1 Deluge

and Ktorrents is also a favorite. Much faster and more configurable than the others.

Transmission bites on my mac too. ditch it.

Powel

---

### Post by fela on 2009-08-24
I think the speed problems are more because utorrent is set up better by default for most people's configs, I think you should be able to get good speeds out of both. I do prefer utorrent though because of all its features. On linux I like to use deluge, which is similar to utorrent.

---

### Post by abhilash82 on 2009-08-24
I have used uTorrent through Wine and also Deluge. I did not have any problems in getting the maximum download speed. I get around 220kbps most of the time.

Check if the port you have configured in your torrent application is open for access and the firewall is configured for the same.

---

### Post by Charles Kerr on 2009-08-24
> **waqar said:**
> I ran a torrent with Transmission and it gave me nothing more than 40 KiB/sec download speed. Then I put the same torrent in utorrent and got 140 KiB/sec and thats the maximum I can have with my internet connection. Some problem with Transmission?
There are several possible reasons.  If there are a lot of peers in the swarm, the most common reason is that one client was just "dealt a better hand" from the tracker and that things will even out after Transmission finds better peers and discards the less-helpful ones.

The Transmission wiki page has a checklist of the common reasons for bad speeds at [http://trac.transmissionbt.com/wiki/SlowSpeeds](http://trac.transmissionbt.com/wiki/SlowSpeeds) .  If you go through the entire list and the problem persists, then it *may* be a Transmission bug and should contact its developers.

---

### Post by MrWES on 2009-08-24
> **andrew.46 said:**
> Hi MrWES,



I have rTorrent 0.8.0 which does not appear to support uPNP, has this been added in the svn?

Andrew

Nah, still no luck. Lots of talk about it, but still no developments -- surely would make life a lot easier with uPnP support in rtorrent. I forward my port from the router, but just enabling uPnP support is much easier. 

Bill

---

### Post by tuxxy on 2009-08-24
I hate Transmission too, not even any encryption :confused:

utorrent > Deluge > Transmission

---

### Post by benmoran on 2009-08-24
> **tuxxy said:**
> I hate Transmission too, not even any encryption :confused:


Transmission certainly does have encryption! 

I've used utorrent on windows since version 1. I forced myself to use transmission after switching to Ubuntu, and now I like it more than utorrent. The UI is just so much more intuitive.

---

