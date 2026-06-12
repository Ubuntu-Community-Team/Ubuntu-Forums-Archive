---
title: "Breaking Movie into many files"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by perito on 2010-08-19
Following this thread: [http://ubuntuforums.org/showthread.php?t=1556400](http://ubuntuforums.org/showthread.php?t=1556400)

If I have a 6GB Movie (.mp4) and I want to break it into lets say 2GBs files ... what program should I use?

Thanks

---

### Post by Paul820 on 2010-08-19
Should be something on there that will do it: [http://www.videohelp.com/tools/sections/linux-video-tools]("http://www.videohelp.com/tools/sections/linux-video-tools")

Lots of great information on that site.

---

### Post by ron999 on 2010-08-19
> **perito said:**
> ... what program should I use?

Thanks

Use **MP4Box**, part of the package **gpac**.
Look for it in Synaptic.

Then use a command like this:-
```
MP4Box -splits 2048000 movie.mp4
```

(That number 2048000 is only approximately 2GB)

---

