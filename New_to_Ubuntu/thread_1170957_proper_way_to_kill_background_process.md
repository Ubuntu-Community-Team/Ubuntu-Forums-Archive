---
title: "proper way to kill background process?"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by helstreak on 2009-05-26
I started something running in the background with &.  I killed the process with:

kill bg [1]

Is that the proper way to do it?  And how do you switch to a background process?

Thank you for your help :)

---

### Post by mkvnmtr on 2009-05-26
I don't know about the proper way but I normally use htop to kill things. Makes it easy and I don't have to know the correct name to do the deed.

---

### Post by x33a on 2009-05-26
if it's a commandline process, then you can use
```
fg
``` to bring it to foreground.

if it's a gui app, then just switch to the window.

and there is no harm in killing the process with kill command.

but if the process has another way of shutting down, then first bring it to foreground and then quit it through the proper way.

---

