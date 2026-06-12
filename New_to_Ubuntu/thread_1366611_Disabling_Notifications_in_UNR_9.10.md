---
title: "Disabling Notifications in UNR 9.10?"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by mr-woof on 2009-12-28
My EEE netbook has UNR 9.10 on it at the moment, the notifications that come up all the time ie your battery is low, you are connected to this network etc etc are doing my nut in!

It keeps telling me the battery is broken etc, can I disable them in anyway? I've had a look about and can't seem to find anything.

Anyone got any ideas?

---

### Post by yeats on 2009-12-28
idea:  poke around in gconf-editor to see if the notifications are set there somewhere...

I've not used it before, but it seems like a likely candidate for where that setting lives.

---

### Post by mr-woof on 2009-12-28
Hmm never heard of that before, is this it?

[http://en.wikipedia.org/wiki/Gconf-editor](http://en.wikipedia.org/wiki/Gconf-editor)

---

### Post by yeats on 2010-01-04
Yep - that's right.  You can invoke it by doing Alt-F2 and typing

```
gconf-editor
```

I would be careful changing anything I didn't know about.  Google is your friend!

---

### Post by warfacegod on 2010-01-04
Remove the Notification Area from your panel. It'll be the one with the battery icon on it.

---

