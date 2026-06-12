---
title: "Streaming Radio keeps stopping after 8/10 minuets"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by Peterfc on 2010-07-01
After spending a day going through the search for help i have to admit defeat.

I listen to three local radio stations but after between 8/10 minuets the stream stops. In the search someone said top remove Totem and after this still the radio stops. 

I have 10.04 with all updates applied. This has happened before the recent update to Firefox.

I do not know what to list from my machine to help.

Peter

---

### Post by ajgreeny on 2010-07-01
I presume it was **totem-mozilla** that you removed, or did you also get rid of **totem** itself?

I have always removed totem-mozilla and used another media player plugin in its place in my browser.  It used to be **mozilla-mplayer**, but now that has no further development going on, I use **gecko-mediaplayer** instead.  Many users prefer vlc-plugin, but I have never liked that, though I do use vlc for most media uses other than in the browser.

I do not see any obvious reason, however, why any media player plugin should stop after 10 mins, and I suspect it is nothing to do with whatever plugin you use, but perhaps some other setting.  Just out of interest, try using something like gnome-mplayer to play the stream direct, rather than through firefox.  If that plays on after the 10 min time has elapsed, it points to a firefox problem, but I have no idea where to start looking for clues.

---

### Post by tgalati4 on 2010-07-01
Open a terminal and run firefox:

firefox

Then post the output after the stream stops.  I'm guessing it's a flash problem.  Many radio stations use a flash player and it balls up.

---

### Post by ajgreeny on 2010-07-02
Good point tgalati4, I had forgotten about flash streams.

However, I do wish sites would use something better than flash!

---

