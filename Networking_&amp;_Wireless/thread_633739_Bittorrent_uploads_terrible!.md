---
title: "Bittorrent uploads terrible!"
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by JDHarms on 2007-12-06
I reinstalled Ubuntu three days ago after taking a two year break from it.  Hardware support is much better, and I'm pleased enough to finally stick with it!  Only one thing is holding me back from a full-time switch though:  My bittorrent.

I used uTorrent on XP, and loved it to death.  After much searching, I found Deluge, which I like as well.  The only problem is, the upload is terrible!

I'm a member of a very private tracker, and I like to upload as much as I possibly can.  On Windows, I could load up my torrents and upload a steady stream at 80Kbps for days and days straight.  With Ubuntu, I load up a very popular torrent, with lots of leechers, and next to nothing happens.  I'll announce to the tracker, it'll do one of two things:  Find lots of leechers, then drop them one by one, or find 3-4 leechers and keep dropping/reconnecting with them.

The max upload rate I've seen so far is 3Kbps.  This is very frustrating.  I've put this computer on my router's DMZ, and that still didn't fix it.  I tried running uTorrent through wine, I tried running upwards of 10 seeds at once, I tried only seeding one very leeched torrent.  I've even tried Azureus (Gag)

Nothing doing.  I picked up Linux again to get back into programming after a long hiatus, and thought I'd learn a few new languages, too.  If I can't get this replaced, I'll probably have to reinstall Windows and just find free IDE's for my programming ):

I really hope someone can help.

Notes:

I have no firewall installed currently.  Well, I do, but I disabled it until I can get this working.

Virtual machines are not an option, I find they just slow things down.  If I can't find every app I need to live on the OS, it's not ready for me to switch.

I have a decent working Linux knowledge, I'm not afraid of opening up a terminal.

I'm using the ports in Deluge/Azureus/whatever suggested by my tracker.  They're in the 40000-55000 range.  I've tried points all throughout that range.

Any help is indeed appreciated,

Daniel

---

### Post by mouseboyx on 2007-12-06
Did you forward the ports 40000-55000 on your router config? That is the only thing i know of that could be holding you back.  How do you share without getting caught I would like to do the same?

---

### Post by kelbizzle on 2007-12-06
Nowhere throughout your post did I see that you have successfully completed a port test. Have you?

---

### Post by JDHarms on 2007-12-07
I was under the impression that Ubuntu shipped with open ports.

My torrent clients tell me the ports are open, if that qualifies as a port test.

---

### Post by kelbizzle on 2007-12-07
[http://www.deluge-torrent.org/test-port.php?port=32459](http://www.deluge-torrent.org/test-port.php?port=32459)     <-Change the port to look like yours.

---

### Post by JDHarms on 2007-12-08
My port is indeed open.

---

### Post by kajillin on 2007-12-09
> **mouseboyx said:**
>  How do you share without getting caught I would like to do the same?. 

MoBlock - [http://moblock.berlios.de/](http://moblock.berlios.de/)

---

### Post by Quiane on 2007-12-24
this seems to be getting more and more common in the past few days..i'm in exactly the same boat (so much so that it seems that i'm spamming here!).  Ports forwarded...i'm just wondering if this could be a bug in a gutsy update, or something to do with the system...?

---

