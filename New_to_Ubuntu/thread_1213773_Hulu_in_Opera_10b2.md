---
title: "Hulu in Opera 10b2"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by Martin Marshalek on 2009-07-15
I have Jaunty amd64 but I don't think this is a 64bit issue though so I posted here. I manually uninstalled flash and replaced it with the 64 bit beta libflashplayer.so for opera and Firefox. I still use java from the restricted-extras package though, I'm not sure if that's 64bit or not. Anyway, in Opera 10b2 (the qt4 build) with the 64bit flash I fixed my original issue with flash simply not loading on all but one site, hulu. When I load a hulu video the opera window goes black and I have to kill the process. When I run it in the terminal this is the error I get when I open hulu. 
```
opera: X Shared memory extension is not available. ZPixmap not supported
opera: Plug-in 4569 is not responding. It will be closed.
opera: Define environment variable OPERA_KEEP_BLOCKED_PLUGIN to keep blocked plug-ins.
Killed

```

The first line is when I open opera and the last is when I kill it. The middle two come up when I open a hulu video. The weird part is that hulu works fine in Firefox. Any suggestions?

---

### Post by Martin Marshalek on 2009-07-15
Sorry for the bump, but I'm really annoyed by this, and I don't know what other issues this may cause.

---

### Post by Martin Marshalek on 2009-07-15
Well, for anyone having this issue, it has been solved. Turns out that it was the older build that was the issue (I just updated from build 4458 to 4478).

---

