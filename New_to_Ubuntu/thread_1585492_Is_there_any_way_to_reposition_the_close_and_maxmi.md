---
title: "Is there any way to reposition the close and max/min buttons to the right side of the"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by venom104 on 2010-09-30
Is there any way to reposition the close and max/min buttons to the right side of the screen? I'm currently using ubuntu 10.04 and I HATE having to crawl up to the left side of the screen to close a window.

---

### Post by lswartz on 2010-09-30
You sure can. Try [here]("http://www.ubuntumini.com/2010/04/move-window-buttons-to-right.html") for instructions.

---

### Post by limestone on 2010-09-30
In terminal do:
```

gconftool-2 -t str --set /apps/metacity/general/button_layout ":minimize,maximize,close"
```

---

