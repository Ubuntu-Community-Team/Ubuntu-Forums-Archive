---
title: "Considering moving from Windows Home Server"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by fave on 2010-02-07
Hey there, 

I need some opinions as to whether or not I am thinking straight. 

Currently I am running Windows Home Server on a Supermicro mobo with a Xeon quad core proc and about 9tb of drives. This is all for an HTPC with Sagetv running on top. 

I am happy with sage, well 90% happy and I am going to keep with it. 
WHS 50% happy. It seems clunky, needs constant restarting. I'm not happy with it's mirroring backup option. I want to go to a raid solution. 

What I'm looking for is a lightweight 64 bit OS that can run the following;
SageTV
News group reader
AnyDVD
Raid
backup solution for my other computers on the network.

That's about it. I don't think I'm asking to much. I know little about Linux and ubuntu, other than what I have read which is only a bit. I will keep on reading. 

Anyway I hope this maybe the way to go.

Cheers
T

---

### Post by dolphinaura on 2010-02-07
Theirs only one thing first. 
are you using some form of SiS Ethernet Chipset for the ethernet card?
Some of the other users here who have home server have a SiS Ethernet card on their home server, and it is really hard to get it running on linux.
If you are, I highly advise you to either replace it first. Those cards are very difficult to get running on linux.

Now lets see....
SageTV has a linux version, so we dont need to worry about that.
For a news group reader, this thread has a lot of suggestions:[http://ubuntuforums.org/archive/index.php/t-90896.html](http://ubuntuforums.org/archive/index.php/t-90896.html)
AnyDVD -> [Handbrake]("http://handbrake.fr/downloads.php")
RAID & Backup. I dont know about this, but I use AMANDA. not for newbies.

---

### Post by fave on 2010-02-07
SIS card nope, right now the built in chipset I think is Intel... but I can get another gigabit card if that is an issue.

---

### Post by dolphinaura on 2010-02-07
> **fave said:**
> SIS card nope, right now the built in chipset I think is Intel... but I can get another gigabit card if that is an issue.

Good. Intel cards work Ok.
Its just that if its SiS, your wasting your time.
Ive updated my post above with the stuff you wanted...

---

### Post by pirateghost on 2010-02-07
i tried running WHS for a while.  i hated every bit of it.

My recommendations:
SageTV - i dont know if SageTV would work in ubuntu under wine or if there is a better alternative
Newsgroup reader - are we talking newsgroup downloader? sabnzbd would be ideal for that
AnyDVD - dont know of an alternative, or even if its truly needed
RAID - Linux RAID is awesome
backup solution - backuppc running on the server, deltacopy running on the windows clients

---

### Post by fave on 2010-02-07
Cool !

Anydvd is needed in my situation as I rip my blurays to my server but beyond that am... I'm not sure how to word it but... will it run better, smoother, less of a toll on my htpc server over whs? 

I just want a stable simple platform that will not need restarts to clear memory and generally be a pain in the ***. WHS as an idea is nice but it's really a clunker.

---

### Post by halitech on 2010-02-07
not sure on ripping Blueray but there is info here on playing them with a bluray player

[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

---

### Post by Paqman on 2010-02-07
SageTV has .deb downloads available that should work fine on Ubuntu, although you may want to do a bit of homework there first. You may have to buy another license though, probably best to contact them about that.

There are [Linux alternatives]("http://en.wikipedia.org/wiki/Libdvdcss") to AnyDVD for decrypting DVDs, Bluray could be a problem though.

RAID is no problem, Linux is after all primarily a server OS.

---

### Post by dolphinaura on 2010-02-07
I havent seen anything for linux, and i havent been keeping track since I just watch  blu-rays on my dvd player, However, I have found an app called[ makemkv]("http://www.makemkv.com/"). Although it is for windows, probably it can be run in WINE>

---

