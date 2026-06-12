---
title: "How To Ubuntuzilla + VP8 + WebM = Html5"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by fremantle on 2010-07-01
hope i can explain this properly.

I am using ubuntuzilla on my karmic. the firefox version is 3.6.6. Flash does not work well in my machine so i wanted to enable html5 on YouTube, but it shows html5 as unsupported on my browser. I know i need to have a webm enabled build of firefox to do that, so it means i have to install a nightly build of firefox and remove ubuntuzilla. as i do not wish to uninstall ubuntuzilla and install a nightly build all over again, i need some answers to these questions >

1. is there a way to upgrade to a nightly build of firefox form ubuntuzilla without any reinstalling? like a terminal command or something else
2. can i manually enable webm, vp8 and make my ubuntuzilla html5 compatible?

thanks in advance
:popcorn:

---

### Post by Kimm on 2010-07-01
I'd say you should stay away from nightly builds, unless you are just trying them out. You would do better to use a different browser that supports VP8 (I suggest Google Chrome, or Chromium with ffmpeg codecs, if you want something completely open source) until a stable release of Firefox supports it.

[http://www.google.com/chrome/](http://www.google.com/chrome/)

---

### Post by nanotube on 2010-07-02
the mozilla builds of firefox do not include the h264 codec that is used by youtube due to patent issues, so... that's a no-go.

---

### Post by fremantle on 2010-07-02
> **nanotube said:**
> the mozilla builds of firefox do not include the h264 codec that is used by youtube due to patent issues, so... that's a no-go.
but the testube page of html5 says that nightly builds have the features to play html5..it will be included in firefox 4

---

### Post by ddecator on 2010-07-03
I'm not as familiar with Ubuntuzilla, but I use the Ubuntu Mozilla Team's daily PPA and the latest versions of Firefox 3.7 (will be bumped up to 4.0 very soon in the PPA) has WebM support (I use it on YouTube with great success). You can try updating your system which will make sure you have the latest version of Firefox from Ubuntuzilla, which may have WebM support (depending on how up-to-date it is), otherwise you can remove that PPA and add the Ubuntu Mozilla Team's. The choice is up to you though, and the daily PPA currently upgrades numerous Mozilla packages (unless you configure your system to only pull the necessary ones from the PPA).

---

### Post by renkinjutsu on 2010-07-03
There are more H264 videos than there are WebM videos. And there are *waaaaaaaay* more flash videos than html5 videos, because youtube ads don't work with the html5 videos.

If you're lucky, the videos you wanna watch are in html5

---

### Post by nanotube on 2010-07-03
> **fremantle said:**
> but the testube page of html5 says that nightly builds have the features to play html5..it will be included in firefox 4

yes, nightly builds of firefox4.
latest mozilla release of firefox is 3.6.6, which is what is available from ubuntuzilla.

if you want nightlies, try the mozilla-daily repo as ddecator suggests. (probably best to uninstall the ubuntuzilla package first, if you go that route).

you can also try the chromium daily ppa - that youtube page says chromium nightlies also include webm.

---

