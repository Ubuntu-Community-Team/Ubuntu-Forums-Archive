---
title: "Global Menu?"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by TriBlox6432 on 2010-07-11
I've added the repository, and it said that it had installed fine, but when I right click on my panel and select 'add to panel' I can't find Global Menu anywhere.  Can someone help please?

---

### Post by ubudog on 2010-07-12
You need to use the "Create Custom Launcher".  In the "Command" section, put the path of the global menu program.  (probably something like /usr/local/bin/globalmenu) If you can't find it, open a terminal and type ```
locate globalmenu
``` and see if it is in the /usr/local/bin directory.  This may work.

---

