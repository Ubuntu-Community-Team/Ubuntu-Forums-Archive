---
title: "coreavc problem"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by zenpyro on 2011-02-10
HI I'm new to using Ubuntu, and I've recently tried getting CoreAVC to work on here using Mplayer using [http://ubuntuforums.org/showthread.php?t=1034075](http://ubuntuforums.org/showthread.php?t=1034075)
those instructions. But I run into a problem when I get to the second step, patch and build DShowServer. When I put it into Terminal it comes up with this...

~/mplayer-with-coreavc$ wget -qO - "http://pastebin.com/pastebin.php?dl=f7ca459d" | patch -p0
(Stripping trailing CRs from patch.)
patching file loader/dshow/DS_VideoDecoder.c
Hunk #1 FAILED at 97.
1 out of 1 hunk FAILED -- saving rejects to file loader/dshow/DS_VideoDecoder.c.rej
patch unexpectedly ends in middle of line

I don't really know how to proceed. Can someone help me?

---

