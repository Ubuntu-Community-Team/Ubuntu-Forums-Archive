---
title: "Format Attached Drive"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by not_yet on 2009-02-28
Hi,

How would i format (wipe clean) a one terrabyte drive attached via firewire cable?

thanks

---

### Post by MarblePanther on 2009-02-28
Install gparted with
```
 sudo apt-get install gparted
```

and go into system,administration, partition editor

make sure your drive is plugged in, but unmount it

then format away!

---

### Post by mkvnmtr on 2009-02-28
Format and wipe are not the same thing. If you only wish to format the advise given above is right on. If you wish to wipe you might try the program wipe. It is of course in the repositories.

---

