---
title: "External media desktop icons not appearing on Desktop"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by isee on 2009-11-26
Hello!

I have the Ubuntu Studio version of Jaunty on my desktop computer.

A few months ago the drive icons stopped appearing on my desktop when I insert a USB or DVD, although they show up in my Places menu.  I can't remember the circumstances as it was a while ago.  This is bothersome in that I cannot right-click to play a movie or Unmount a volume, I have to open a File Browser to do so.

As well, the File Browser does not open automatically when a USB or DVD is inserted.  I have to do so after-the-fact through my Places menu.

I'd really like to regain this functionality.

Thanks for your time!:)

---

### Post by ukripper on 2009-11-26
in terminal type this command:
```
gconf-editor
```

Browse to apps-->Nautilus-->desktop and make sure **Volumes_visible** is ticked

---

### Post by isee on 2009-11-26
Thanks very much ukripper!  That did it :P.

---

### Post by ukripper on 2009-11-26
Great ! you can mark this thread as solved from thread tools.

---

