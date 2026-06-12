---
title: "powerbook g4, issues loading and with diplay?"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by captpicard12 on 2009-08-25
Hi, I actually got ubuntu a few months ago, but a couple weeks after i installed it I lost the charging cord to my powerbook g4 :-(.  I just got a new one today, and i turned it on, and put in Linux video=ofonly command just like I used to.  However, it took about 5 minutes to load.  I had thought that the command didn't work and had almost given up, when it finally came on.  And after I logged in, about 10 error messages showed up asking if I wanted to delete various things that wouldn't load, and nothing on the bottom toolbar or top right corner loaded, they're both completely empty right now.  I'm still not sure what does and doesn't work, I'm at least glad that it could connect to the internet without  the wifi stuff in the top-right corner... anybody know what could've gone wrong since the last time I turned it on?

---

### Post by tgalati4 on 2009-08-25
Old notebook drives get sticky when they haven't been used in a while.

Examine the files in /var/log for errors.

dmesg | more (spacebar to move forward, q to quit)

Examine for current errors.

---

