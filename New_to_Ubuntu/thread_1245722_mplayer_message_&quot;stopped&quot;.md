---
title: "mplayer message &quot;stopped&quot;"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by CheetahDC on 2009-08-20
Okay...I have no idea what I'm doing wrong, but here's my situation.  I'm using Intrepid Ibex and Firefox 3.0.13.  I'm trying to watch: [http://www.apple.com/trailers/fox/avatar/teaserlarge.html](http://www.apple.com/trailers/fox/avatar/teaserlarge.html)

Wasn't working.  Looked around, saw mplayer recommended.  Removed totem and its various plug-ins.  Installed mplayer and its plugins using sudo apt-get install mozilla-mplayer.  I get a message that says "Stopped" in the little movie window after it looks like it's done loading.

What can I do to get it to work?

I even tried the "Force Version" of an older version of mplayer to get this to work.

---

### Post by andrew.46 on 2009-08-20
Hi CheetahDC,

Don't worry it seems that Apple has changed something and many Linux users have been left out in the cold. Looks like it happened over the last couple of hours...

Andrew

---

### Post by llamabr on 2009-08-20
I used to have similar problems, and then they stopped.

As a work around, if it's downloading, but now playing in firefox, it'll still save the source in your /tmp file, which you can then play with mplayer.

---

### Post by CheetahDC on 2009-08-20
> **llamabr said:**
> I used to have similar problems, and then they stopped.

As a work around, if it's downloading, but now playing in firefox, it'll still save the source in your /tmp file, which you can then play with mplayer.

How do I do that?  Also, I downloaded the file to my desktop using a Firefox plugin called Embedded Objects 1.9.  I hit play.  Nothing seems to be happenining

---

### Post by BigBananaMan on 2009-08-20
> How do I do that? Also, I downloaded the file to my desktop using a Firefox plugin called Embedded Objects 1.9. I hit play. Nothing seems to be happenining  I'll tell you how you could do it though I tested it and it didn't work.  Go to your home directory and hit ctrl+h to view hidden items.  Then look for .mozilla/firefox/kv8gtx5p(number will vary).default/cache and it'll be in there.  The file didn't work for me because it never downloaded and was at 92bytes but since you already downloaded it to your desktop, try running it from terminal to see what specific error you get.
```
totem ~/Desktop/avatar2009aug0820a-tsr_h640w.mov
```  You can also try running it with VLC which I keep as a good fallback.

---

