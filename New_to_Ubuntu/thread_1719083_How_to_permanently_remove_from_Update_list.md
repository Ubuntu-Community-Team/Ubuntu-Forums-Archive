---
title: "How to permanently remove from Update list?"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by resander on 2011-04-01
The update installation does not work for an external repository. The update stops with various error messages. There is another repository that I can use instead, but how do I remove the repository that is not working from the Update list. I can untick the components of the faulty update and they will not be included when I click 'Install now' button, but the ticks are back again when I invoke the Update Manager.

How can I permanently remove unwanted components from the Update list of the Update Manager?

---

### Post by Enigmapond on 2011-04-01
```
 gksudo gedit /etc/apt/sources.list
```

be careful and just remove the 1 or 2 lines that pertain, save and close.

---

### Post by resander on 2011-04-01
Many thanks Enigmapond,

That worked fine.

---

### Post by Enigmapond on 2011-04-01
My Pleasure! Glad to help.. :D

---

