---
title: "Re-Enable Unity and menubar. Help!"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by fuzzycut on 2011-04-29
Hi there, i am a mostly first time linux user. Last night I installed Natty and it worked fine. I had heard about compiz and saw it was installed, so I installed the settings manager and had a play around. Eventually I unchecked the tickbox for the unity plugin and desktop wall. This froze the desktop completly and I had to reboot. The next time I logged in nothing happened. The wallpaper loaded and I could right click, but that was it, no unity, no top title bar. I can still use classic ubuntu but I would like to sort this out, without having to reinstall. Can anyone tell me how to re-enable the menubar and unity? Any help appreciated.

---

### Post by howefield on 2011-04-29
Try pressing the Ctrl + ALt + F1 keys and login to the tty1, then type

```
unity --reset
```

Press enter and return to the Unity desktop by pressing Ctrl + Alt + F7

---

### Post by fuzzycut on 2011-04-30
fixed it. Thanks!

---

### Post by Jumponskis1 on 2011-09-13
id like to re-open this thread on account of im having the same problem, messed around with compiz cause i used to use it on hardy heron but this fix didnt work for me and i got an error message that states warning no display variable set, setting it to :0 and name error: global name "GError" is not defined

---

### Post by coffeecat on 2011-09-13
@Jumponskis1, I'm closing this thread as you've now started your own here:

[http://ubuntuforums.org/showthread.php?t=1843253](http://ubuntuforums.org/showthread.php?t=1843253)

It's usually best to start your own thread in the first place, and please do not post the same problem in different threads or different parts of the forum as this dilutes community effort, Thanks

---

