---
title: "X Composition Manager and AWN dock at auto start"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by bteotarigan on 2009-09-24
I'm installing the Awn Dock and since my computer do not support compiz, i'm installing the alternative X Composition manager instead. I've put both the Awn Dock and the X Composition manager at the start up application programs, but the Awn Dock wouldn't load at the start up. I've tried to run the Awn dock manually after the start up, but it wouldn't work either. The Awn Dock would only load everytime i failed to change the desktop visual effect from none to extra, so i have to do that at every start up. Did i miss something???

---

### Post by Shujah on 2009-09-24
Turn off the alternative composition manager & go to terminal > gconf-editor 

gconf-editor > apps > metacity > general > compositing-manager (check)

---

