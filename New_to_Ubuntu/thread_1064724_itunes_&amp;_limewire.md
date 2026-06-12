---
title: "itunes &amp; limewire?"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by Yed Ied on 2009-02-09
Trying to download itunes, and it isn't working like it did with the PC or MAC.  Will it work on UBUNTU 8.10?

---

### Post by tegnoto89 on 2009-02-09
Not without Wine.  Windows executable files (.exe) that windows uses to install programs won't work on linux.  You need to download Wine and open the .exe files with Wine, or get ubuntu-compatible alternatives.  For itunes, you can use Rhythmbox, which ubuntu comes with, or Songbird, which looks and feels more like itunes.


Actually, I feel like there are linux-compatible versions of limewire out there; maybe I'm wrong?

---

### Post by howefield on 2009-02-09
I don't believe itunes will work in Ubuntu, but maybe someone can correct me.

There is a limewire equivalent for linux called Frostwire which isn't in the repository, but a .deb can be downloaded from the frostwire site. If it is torrents you are after, Ubuntu comes preloaded with Transmission which will handle them, or at least it does in 8.10, not sure about earlier versions.

---

### Post by nothingspecial on 2009-02-09
For iTunes look at :-
                     Rhythmbox
                     Banshee
                     Songbird
                     Exaile
                     Amarok
                     Gtkpod

For limewire look at:-
                      Transmission
                      Deluge
                      rTorrent

There are plenty of others out there. Welcome to the world of choice.\\:D/

---

### Post by abn91c on 2009-02-09
Fo Limewire for linux go here [http://www.limewire.com/download/version.php](http://www.limewire.com/download/version.php)

---

### Post by SunnyRabbiera on 2009-02-09
Yeh when downloading an app like itunes and it offers you a mac or windows version its really a moot point as this is linux.
Not like itunes works with wine anyhow, recent versions have caused nothing but grief on wine.
But we have plenty of itunes alternatives, but if you are using itunes for your ipod well its probably not going to work.
More recent ipods have a lot of nonsense in them that makes them not work with linux, the4 only way to resolve this is to either jailbreak the ipod or get another MP3 player or use windows in virtualbox.

For you limewire question, there is a linux version of limewire but I like others would recommend frostwire...
its basically the same app but I find frostwire better due to it not needing "premium" access to use features such as higher download rates.

---

### Post by clive littlewood on 2009-02-09
Hi

Just a note of caution, all the apps mentioned for ipod will not work with ipod touch or iphone.     :(

IMHO Frostwire is much better on my box than Limewire.

Clive

---

### Post by overlord.gaurav on 2009-02-09
> **howefield said:**
> I don't believe itunes will work in Ubuntu, but maybe someone can correct me.


I have got iTunes 8.0.2 working under Wine on my PC with a bit of tweaking.
It plays music, library works. What doesn't work is: Genius Playlist, iPod detection. App Store works, but you can't login.
I've heard people have got their iPods detected on iTunes though. And not just iPod...some have even got the iPhone detected.

Having said that, using Banshee for syncing iPod is a better option. [iPod touch and iPhone will not work though]

---

### Post by howefield on 2009-02-09
> **overlord.gaurav said:**
> I have got iTunes 8.0.2 working under Wine on my PC with a bit of tweaking. It plays music, library works. What doesn't work is: Genius Playlist, iPod detection. App Store works, but you can't login.

Sounds fantastic, lol. :rolleyes:

But don't tell me, share your "tweaks" with the original poster.

---

### Post by overlord.gaurav on 2009-02-09
I just followed the steps on the WineHQ page.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14793](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14793)

It was simple to get iTunes started.

Oh, and for iPhone/iPod detection, refer to [this page.]("http://www.huanix.com/sync-in-linux/index.php/ITunes_8_through_modified_Wine") Although, I wasn't successful in doing that. Maybe 'cause am running on 64-bit.

---

