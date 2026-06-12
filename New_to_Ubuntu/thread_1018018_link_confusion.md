---
title: "link confusion"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by ant2ne on 2008-12-21
I thought I had already posted this question. But a search did not reveal anything.

/mnt/net.media/*mediafiles* exists just fine
```

ln -sf ~/Desktop/media /mnt/net.media

```

results in ~/Desktop/media/net.media/*mediafiles*

What I'd like is ~/Desktop/media/*mediafiles*

What am I doing wrong?

---

### Post by ohzopants on 2008-12-22
Try putting a / at the end of /mnt/net.media like this:
```

ln -sf ~/Desktop/media /mnt/net.media/

```

---

