---
title: "Add and remove programs"
date: 2010-12-25
forum: New to Ubuntu
---

### Post by hunter99507 on 2010-12-25
I was wondering if there was a place to look to see all of your installed programs like the windows "add and remove" I know you can use synaptics but that doesnt really help me becuase it shows everything thats installed. I am trying to see the programs that i have installed.  Anyway to do that?

---

### Post by karthick87 on 2010-12-25
To see all installed programs,

```
sudo dpkg --get-selections
```

---

### Post by tango_ninja on 2010-12-25
If you want more of a streamlined list, showing only application names and not packages, go to Applications > Software Center and select 'Installed Software'

---

### Post by hunter99507 on 2010-12-25
Is their anything simpler?  I must have over 200 items in that list.

---

### Post by hunter99507 on 2010-12-25
The software center is exactly what i am looking for but it doesnt show everything.  For example i installed a bunch of games from the humble bundle (Braid, cortex ect..) and they dont show on that list.  Is their anyway to display that list in the software center?

---

### Post by lisati on 2010-12-25
> **hunter99507 said:**
> Is their anything simpler?  I must have over 200 items in that list.
I don't know. :( The software center is one of my favourite places to look, and for some it's easier than browsing Synaptic Package Manager's list.

---

