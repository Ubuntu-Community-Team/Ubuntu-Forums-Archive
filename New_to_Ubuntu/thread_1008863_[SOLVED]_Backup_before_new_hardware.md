---
title: "[SOLVED] Backup before new hardware"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by pteri498 on 2008-12-12
I have a fax modem I want to put into my computer. Last time I did it, it took over my sound card and Ubuntu no longer recognized the on-board sound card in the system. This is especially weird since there is no audio-out on the modem, but that's besides the point.

I'm curious, is there a method out there to back up my hardware configuration in case this happens again? I don't want to have to reinstall ubuntu; it takes days to get it back to normal.

---

### Post by pteri498 on 2008-12-12
*Bump* Any ideas?

---

### Post by nhasian on 2008-12-12
i like to use sbackup (simple backup)

```
sudo apt-get install sbackup
```

then you can configure it to backup whatever part of the filesystem you like

---

