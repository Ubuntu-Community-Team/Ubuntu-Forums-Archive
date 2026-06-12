---
title: "Firefox memory leak?"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by pzs on 2009-05-08
I leave my machine on overnight with Firefox running. This is what the Firefox line looked like in top this morning:

28885 pzs       20   0 2056m 1.4g  24m S    2 18.6 113:28.93 firefox      

That's right, 2GB of virtual memory and 1.4GB resident. I have one tab and window open - the one I'm using to make this post. I know that these readings aren't always reliable, but can this really be right? I also notice that Firefox is pretty sluggish after it's been running for hours like this. It's fine after a restart.

---

### Post by MysticalRiotCandy on 2009-05-08
Sounds like Firefox is trying too hard to cache everything you've looked at, and some things that it thinks you might want to look at later.  I myself just kill the process when it gets that high, but in the preference settings you can probably lower how fast it stagnates into that by changing the cache size and lowering the history size.  Not much other info I can give you, besides that Firefox is basically just a resource hog on every OS.

---

