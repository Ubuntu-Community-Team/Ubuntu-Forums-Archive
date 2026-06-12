---
title: "Ugh, wireless..agian."
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by COLiNx86 on 2007-12-06
Ok so I made a thread about my wireless not working and I got some people to attempt to help me but nothing worked:(. the next day I powered on my laptop and bam it worked. well it stopped again. So this morning I was looking around in the files and I found the blacklist file.
this is what it looks like
```

blacklist bcm43xx
blacklist bcm43xx
blacklist bcm43xx
blacklist ndiswrapper
blacklist ndiswrapper
blacklist bcm43xx
blacklist bcm43xx
blacklist bcm43xx

```Is it supposed to say all of those that many times. Oh and also I had to force my computer to turn off earlier and it turned off and then when I turned it back on it went from the normal loading/boot screen where it says ubuntu with the little loading bar. and when it got about one third done it said it needed to check my hdd and it did and was fine but it finished booting in a text screen until it got to the login screen. but while it was at the text screen it said can't load blacklist ndiswrapper or something (went by fast).
I also don't have the wlan0 i have like eth26 or something.

So are all of these normal, anything I should fix? Please help I don't want to re-install..again.
Thanks In advanced.

---

### Post by COLiNx86 on 2007-12-06
I'm sorry for bumping this but seriously can't someone help me?

Also and Update.
I reinstalled Ubuntu but this time I went with the normal version instead of the 64 bit version. So I follow the guide for ndiswrapper, the one I followed before that worked. and well it just didn't work..at all. can someone please help me. cause I refuse to go back to windows but Linux is driving me crazy.

---

### Post by SactoBob on 2007-12-09
You can use ndiswrapper, in which case you need to blacklist the bcm43xx driver.
Or you can use bcm43xx, in which case you have no need for ndiswrapper at all.

You have both blacklisted (one entry will do), so I would recommend you pick one method and research the extensive documentation which both methods have.  You don't want two drivers fighting over the same card.  ON the other hand, you can't blacklist them BOTH or there is no driver available.

---

