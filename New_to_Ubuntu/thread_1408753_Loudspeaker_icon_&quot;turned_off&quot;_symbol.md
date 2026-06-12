---
title: "Loudspeaker icon &quot;turned off&quot; symbol"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by mynot on 2010-02-16
I've just (re-)installed 8.04. The loudspeaker icon has white bar in a red circle attached to it. It is not muted. What does this mean?
Thanks
Tony

---

### Post by Satoru-san on 2010-02-16
are you able to hear anything through your speakers?

If no, open up a terminal and type this

```
alsamixer
```

when that comes up if either the Master or PCM are at zero that is your problem.

---

