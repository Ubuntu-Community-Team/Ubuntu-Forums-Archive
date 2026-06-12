---
title: "Regarding Shoutcast on XMMS"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by Xalticus on 2009-09-18
I read on this forum that XMMS is a good media player and it can stream audio like ShoutCast, I've attempted the straight forward route one would use on Windows in Winamp where I just copy/paste the link into "play location" and that didn't work, thus now I'm lost.

I installed XMMS via a deb file I got from here:[https://edge.launchpad.net/~mapopa/+archive/ppa/+index?field.name_filter=xmms&field.status_filter=published]("https://edge.launchpad.net/%7Emapopa/+archive/ppa/+index?field.name_filter=xmms&field.status_filter=published") so I'm not sure where it is actually located on my machine. I'm using Ubunto 8.10 Intrepid Ibex.

If you don't care about the details, what I want to know is: [B]How do I play Shoutcast Streaming audio on XMMS?

[/B]I'm relatively new to Linux so please bare with me.

---

### Post by andrew.46 on 2009-09-18
Hi Xalticus,

I am not so sure that XMMS is a good choice for this sort of playback and in fact XMMS has been dropped from almost all major Linux distros as development ceased a while back. I have no experience with Shoutcast but I suspect that vlc might do a better job:

```
sudo apt-get install vlc
```

I have taken the trouble to download a shoutcast stream and played it quite successfully with vlc, I attach a screenshot of vlc in action.

All the best,

Andrew

---

### Post by RedRat on 2009-09-18
Try Amarok 1.4. It reads Shoutcast broadcasts and Cool-Streams also. I have heard some bad things about the latest Amarok 2, so you might want to try the 1.4 version.

---

### Post by koleoptero on 2009-09-18
Also if you prefer XMMS-like (hence Winamp-like) programs, you can install audacious, which I can assure you plays shoutcast streams.

To install it go to the add/remove and search for audacious.

---

