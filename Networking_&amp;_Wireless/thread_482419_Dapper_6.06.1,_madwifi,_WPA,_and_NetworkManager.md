---
title: "Dapper 6.06.1, madwifi, WPA, and NetworkManager"
date: 2007-06-23
forum: Networking &amp; Wireless
---

### Post by mattengland on 2007-06-23
I have a madwifi-based laptop, and because of [this Feisty problem](http://ubuntuforums.org/showthread.php?t=470429), I am restricting my Ubuntu usage to Dapper.

However, Feisty's NetworkManager was a thing of beauty while I was using it.  I want to get it working in Dapper in a similar fashion if I can.  I see various references to this; I'm trying to figure out which ones (just one would be preferred, but I don't know if I'll get that luck) are most appropriate.

Madwifi install: [http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)
WPA support: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)
NetworkManager install: [http://ubuntuforums.org/showthread.php?t=156319](http://ubuntuforums.org/showthread.php?t=156319)

Are these appropriate?  Am I missing anything?  The NetworkManager install seems like an old reference.

Hopefully there aren't any mutually-exclusive procedures in these things.

---

### Post by scrooge_74 on 2007-06-23
network manager works fine for me on Dapper

---

### Post by mattengland on 2007-06-23
I can get NetworkManager to just plain *work* in Dapper, too.  I can not see the very-handy features of the Feisty flavor of the NetworkManager, namely the graphical choices of SSIDs, etc.  (Maybe this is a wifi-radar-specific feature, or something similar?)

And to clarify: by Dapper I mean the fresh, 6.06.1 LTS cdrom download and install with no updates.  By Feisty I mean the cdrom download and install with no updates.

Basically, my wirelress-ethernet user experience with Feisty is far better than Dapper.  I want Dapper's stability (see above why I chose Dapper due to a Feisty problem) with Feisty's wireless-ethernet features.  I don't care how I get there, I'm just looking to find a way.

---

### Post by scrooge_74 on 2007-06-24
I found you can mix wifi-radar with network manager, it seems they can't coexist very well.  With my laptop the only real reason I changed Dapper for Edgy and then Fesity was for the network manager improvement.  Luckly I my Festy install has been working pretty solid, not that many problems to complain about.

---

### Post by mattengland on 2007-06-24
Ok, so I'm not the only one who likes Feisty's wireless-management improvement (thanks for the notes scrooge_74).

I'm still seaking a way to get said user-experience improvement on Dapper.  Thoughts?

---

### Post by scrooge_74 on 2007-06-24
I dont know if there is a backport for it, or maybe trying  to compile it

---

### Post by mattengland on 2007-06-24
> **scrooge_74 said:**
> I dont know if there is a backport for it, or maybe trying  to compile it

The biggest obstacle I face is I don't know what "it" is.  Is it a bona fide package?  Is it wifi-radar?  network-manager?  wpasupplicant?  Something more, less, else?

This seems to be common issue (ie, getting Feisty-like wireless-management in Dapper), I'd like to think work to address/document it may be helpful for many.

---

### Post by mattengland on 2007-07-03
I'm still looking for feedback on this topic.  Thanks for any help.

---

### Post by ugm6hr on 2007-07-03
I am a Feisty user, but if you are after graphical representation of wifi with a system tray icon that displays connection strength etc, have you tried Wicd?  I actually think it is better with atheros / WPA wifi than Network Manager.  Ever so slightly less impressive looking (no drop-down SSID list from system tray icon), but otherwise does the same thing.  I would recommend the testing version (I use 1.2.9, but am planning to try 1.3.0 soon) rather than stable 1.2.7 (which I found a little unstable!).

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by mattengland on 2007-07-03
> **ugm6hr said:**
> [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Excellent reference, thanks for the tip.  wicd looks promising, although I haven't gotten it to work as well as I would like.  the 1.2.9 and 1.3.0 daemons don't stay running on my Dapper/ThinkpadT41 box, but 1.2.7 works to start.  But when foolishing pressing "connect" on an already-connected WPA access point, causes things to go bad.  Further, after connecting to one access point, you can no longer see any others, despite trying pretty hard to do so (minus rebooting).

**Where's the best place to strike up a wicd-support conversation?  The wicd sf.net forums don't look that populated.**

In any case, thanks again for the wicd reference.

**I'm still interested to see if anyone got wifi-radar working on a Dapper system?**

---

### Post by scrooge_74 on 2007-07-03
I manage to get wifi-radar to work on and off on Dapper, it did not work on a system using a broadcom card, but worked pretty well on an IBM T42, but in the long run changed to network-manager, because it gave me more security settings to use

---

### Post by ugm6hr on 2007-07-04
> **mattengland said:**
> Excellent reference, thanks for the tip.  wicd looks promising, although I haven't gotten it to work as well as I would like.  the 1.2.9 and 1.3.0 daemons don't stay running on my Dapper/ThinkpadT41 box, but 1.2.7 works to start.  But when foolishing pressing "connect" on an already-connected WPA access point, causes things to go bad.  Further, after connecting to one access point, you can no longer see any others, despite trying pretty hard to do so (minus rebooting).

**Where's the best place to strike up a wicd-support conversation?  The wicd sf.net forums don't look that populated.**

Shame 1.2.9/1.3.0 don't behave with Dapper - the issue of not seeing other access points when connected has been resolved (well - I don't have that problem with 1.2.9).  As for trying to connect when already connected - yes, this does cause issues.  According to the 1.3,0 changelog, it now has a "disconnect" option, which should resolve this....

Wicd support - there are plenty of users in these forums (I heard of it from here).  Maybe repost with Wicd / Dapper in the title.  I know the Wicd forum is quiet, but it appears to be quite good in one respect; the developer seems to reply to all the threads personally (although I haven't posted there).

Good luck.

---

### Post by imdano on 2007-07-04
He had posted in the sourceforge supplied wicd forums rather than the phpbb forums originally, which only had a couple of threads in it (hence his concerns about them not being populated).  I directed him to the more [commonly used](http://wicd.sourceforge.net/phpbb/) forum.

I'm interested to know what kind of problems you're running into with the daemon in Dapper.  Does it not load at all?  If you run sudo /opt/wicd/daemon.py do you recieve an error message?  Also, a lot of the work Adam and I did on the 1.3.0 tray icon only applied to Edgy.  I'll try to do some work on the Dapper tray as well, but it'll be a challenge without a Dapper box to test it on...

---

