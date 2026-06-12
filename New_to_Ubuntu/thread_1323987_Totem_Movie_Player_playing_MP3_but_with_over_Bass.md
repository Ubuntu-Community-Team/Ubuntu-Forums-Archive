---
title: "Totem Movie Player playing MP3 but with over Bass"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by Cool G5 on 2009-11-12
I played some MP3 files on Totem player but the output is not great. The bass is over & hence the sound is not clear. Which other player can I use for good sound? Is Totem not good or is my decoder not matching well with Totem Player? Please suggest a player which will use less memory.

---

### Post by 3rdalbum on 2009-11-12
The problem is likely to be that the "PCM" channel of your sound system is set too high.

Open a terminal and run this command:

```
alsamixer
```

With the arrow keys, move over to the PCM channel and turn it down to around 90. Press Escape to exit.

See how that is now.

---

