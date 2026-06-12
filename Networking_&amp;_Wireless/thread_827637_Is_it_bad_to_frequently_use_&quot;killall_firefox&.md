---
title: "Is it bad to frequently use &quot;killall firefox&quot;"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by Johnny K on 2008-06-13
Like most users, I frequently encounter the problem of the Adobe Flash plugin freezing up in Firefox. After a certain amount of time, the plugin simply stops working and flash videos do not load. The only way (as far as I know) to resolve this problem is to close Firefox (killall or otherwise) and then restart it.

To make this task a little easier, I wrote a very basic bash script:
```
killall firefox
firefox
```

Whenever Flash stops working, I just execute that script and click "Restore Previous Session" when Firefox starts again. This way, the tabs and form data are not become lost in the process of me exiting and restarting Firefox.

So...could this frequent use of killall bad in any way?

---

