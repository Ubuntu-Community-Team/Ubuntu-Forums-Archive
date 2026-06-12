---
title: "turning compiz off and on with a keyboard shortcut"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by Falc7 on 2009-05-11
Compiz fusion tends to interfere when i play games with wine. But it can be annoying turning the compiz fusion off through the 'appearance' menu everytime, can i set up a keyboard shortcut to turn compiz from none to 'custom'? I looked under keyboard shortcuts, but didn't see anything about this.

---

### Post by MrWES on 2009-05-11
> **Falc7 said:**
> Compiz fusion tends to interfere when i play games with wine. But it can be annoying turning the compiz fusion off through the 'appearance' menu everytime, can i set up a keyboard shortcut to turn compiz from none to 'custom'? I looked under keyboard shortcuts, but didn't see anything about this.

You can install fusion-icon; which will sit in your notification area. Makes turning compiz on and off a breeze.

```
sudo apt-get install fusion-icon
```
from a terminal.

Bill

---

### Post by Falc7 on 2009-05-11
thanks for your quick reply, i've installed that. How do i use it to turn off compiz? right clicking dosen't seem to bring up any options about that.

---

### Post by stoogiebuncho on 2009-05-11
> **Falc7 said:**
> thanks for your quick reply, i've installed that. How do i use it to turn off compiz? right clicking dosen't seem to bring up any options about that.

Look under "Window Managers" (or something like that).  You'll want to change it to Metacity.

You can also do this from the command line if you want to.

Turn off Compiz:
```
metacity --replace
```

Turn it back on:
```
compiz --replace
```

You can set up launchers to do this for you if you wish.

---

### Post by qjmoss on 2009-05-11
Compiz did effect gaming for me too.

What I do is right click on my desktop and turn off desktop effects..

---

