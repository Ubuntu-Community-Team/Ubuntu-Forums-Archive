---
title: "How do I un-install a program"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by jfloydb on 2009-04-26
I'm about to install avidemux with the terminal using the following code:

```
sudo apt-get install avidemux
```

If I don't like it, how do I un-install it?

Thanks

---

### Post by jbrown96 on 2009-04-26
```
sudo apt-get remove avidemux
```

---

### Post by sgosnell on 2009-04-27
Or if you want to really get rid of it, ```
sudo apt-get purge avidemux
```
That removes the config files in addition to the app. Or you can open Synaptic, find avidemux, click on the square at the left of the name, and select Mark for removal or Mark for complete removal.

---

