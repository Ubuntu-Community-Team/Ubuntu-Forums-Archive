---
title: "Gtkpod doesn't find my iPod."
date: 2010-03-04
forum: New to Ubuntu
---

### Post by kramer65 on 2010-03-04
Hello,

I installed gtkpod and attached my ipod to my pc. Although it mounts (I can open it in nautilus) I don't see it in gtkpod.

I read somewhere that I have to set the mountpoint in the preferences, but I can't find where that would be possible..

Can anybody help me out here..?

---

### Post by kouter on 2010-03-04
type of ipod? touch or pre-touch?

---

### Post by kramer65 on 2010-03-04
It's an iPod nano 8GB (so a pre-touch)..

---

### Post by kouter on 2010-03-04
tried searching for some how to's or help on google?
 
[http://www.simplehelp.net/2007/07/07/how-to-use-gtkpod-to-manage-your-ipod-in-ubuntu/](http://www.simplehelp.net/2007/07/07/how-to-use-gtkpod-to-manage-your-ipod-in-ubuntu/)
 
see if that helps

---

### Post by nothingspecial on 2010-03-04
Try this

In gtkpod go Edit > Repository/iPod Options

Choose Add new repository/iPod

```
Repository type - iPod

Repository Name - choose one

iPod mount point - browse to it

iTunes db backup - forget it

Model - browse to it
```

Unmount and remount iPod, right click on ipod (in gtkpod) and choose load ipod.

Sorry if a little vague because I`m not running gtkpod atm.

---

### Post by robine on 2010-03-09
Thanks, nothingspecial! That was perfect info and did the trick. I was having the same issue. Much appreciated! :)

---

