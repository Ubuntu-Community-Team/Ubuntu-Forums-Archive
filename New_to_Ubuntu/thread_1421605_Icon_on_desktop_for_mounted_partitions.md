---
title: "Icon on desktop for mounted partitions"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by Ozymandias_117 on 2010-03-04
Basically, what I want is for icons to only be displayed on my desktop if it is mounted in /media. Is there any way to do this?

---

### Post by kanikilu on 2010-03-04
Run **gconf-editor** from a terminal (or ALT+F2), browse to:

apps > nautilus > desktop

Check the "volumes_visible" box and close the window.

//edit: ...oops, didn't read your question correctly the first time. I don't think there is a way to specify that *only* volumes in /media show up, but I could be wrong...?

---

### Post by Ozymandias_117 on 2010-03-04
Thanks, I had already found that. Was hoping I could specify only the single folder.

---

### Post by Ozymandias_117 on 2010-03-05
Anyone? I figure there must be a way, since /mnt doesn't show any... Seems like there must be somewhere to configure it.

---

### Post by Ozymandias_117 on 2010-03-11
Bump

Just thought I would see if anyone has any ideas.

---

