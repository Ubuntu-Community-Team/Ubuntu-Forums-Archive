---
title: "dvd error message"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by dimothy10 on 2009-05-11
I am getting the following error message from vlc when trying to play DVDs.  I have followed the docs to get the CSS libraries and the restricted extras package but still no luck.  Would really appreciate some guidance lol

thanks in advance 

tim

```
 libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed
[00000408] dvdnav demux error: cannot set title (can't decrypt DVD?)
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Invalid title IFO (VTS_01_0.IFO).
[00000408] dvdread demux error: fatal error in vts ifo
[00000408] dvdread demux error: DvdReadSetArea(0,0,1) failed (can't decrypt DVD?)
[00000411] main access error: no access module matched "dvd"
[00000407] main input error: open of `dvd:///dev/sr0' failed: could not create access: no access module matched "dvd"

```

---

### Post by ashmew2 on 2009-05-11
What version are you using ? 

Have you tried mplayer ? 
```

sudo apt-get install mplayer
```

I personally dont like the vlc which came bundled with 9.04 :(

---

