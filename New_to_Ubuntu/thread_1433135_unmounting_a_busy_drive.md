---
title: "unmounting a busy drive"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by linux_noob0 on 2010-03-18
Hey there!
I'd like to unmount my cd/dvd drive cause it's noisy, and i don't know what's causing it to make these weird sounds :)
When i try to unmount it, it tells me the device is busy... any way to fix this?
( i can't eject it even using the eject button... )

thanks!

---

### Post by spiderbatdad on 2010-03-18
```
man umount
```
Will explain the options available. -f is used to force the unmounting.

---

### Post by linux_noob0 on 2010-03-18
didn't work, still said it's busy...
but, it suggested something cool: it sad use lsof to see who's using it...
it appears evince was open with a pdf on another desktop XD
thanks.. solved now :)

---

