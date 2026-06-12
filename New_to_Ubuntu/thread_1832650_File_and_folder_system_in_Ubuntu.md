---
title: "File and folder system in Ubuntu"
date: 2011-08-25
forum: New to Ubuntu
---

### Post by zirch on 2011-08-25
How does the file and folder system in Ubuntu work? What are the Window's "Program Files" and "AppData" equivalents in Ubuntu? Where can I find application settings, plugins, and logs in Ubuntu? I'm using Wubi Ubuntu 11.04 by the way.

---

### Post by fdrake on 2011-08-25
> **zirch said:**
> How does the file and folder system in Ubuntu work? What are the Window's "Program Files" and "AppData" equivalents in Ubuntu? Where can I find application settings, plugins, and logs in Ubuntu? I'm using Wubi Ubuntu 11.04 by the way.

I think it will take at least a book to answer to your questions.
My suggestion? A Practical Guide to Ubuntu Linux. Sobel
[http://www.sobell.com/UB3/index.html](http://www.sobell.com/UB3/index.html)

---

### Post by zirch on 2011-08-25
> **fdrake said:**
> I think it will take at least a book to answer to your questions.


Oh. Okay...
What about where I can find the bookmark file of Firefox? In Windows, I can find it in the Mozilla folder in AppData. It's either a .html or .json file, I suppose.

---

### Post by SoFl W on 2011-08-25
Both windows and Linux are similar, inside your home folder is everything about your stuff.  Many things are hidden, meaning it has a period in front of the name.  Press ctrl-h to see hidden files from your file viewer.

Firefox----
/home/zirch/.mozilla/firefox/SOME-LETTERS.default/

by default your should be in the /home/zirch/ directory.  That is your "home" directory.

/home/USERNAME/

---

### Post by zirch on 2011-08-25
> **SoFl W said:**
> Both windows and Linux are similar, inside your home folder is everything about your stuff.  Many things are hidden, meaning it has a period in front of the name.  Press ctrl-h to see hidden files from your file viewer.

Firefox----
/home/zirch/.mozilla/firefox/SOME-LETTERS.default/

by default your should be in the /home/zirch/ directory.  That is your "home" directory.

/home/USERNAME/

I see. Thanks!

---

### Post by oldos2er on 2011-08-25
> **zirch said:**
> How does the file and folder system in Ubuntu work? What are the Window's "Program Files" and "AppData" equivalents in Ubuntu? Where can I find application settings, plugins, and logs in Ubuntu? I'm using Wubi Ubuntu 11.04 by the way.

Each user's config data is stored in their home folder as hidden files/folders. System-wide config data is mostly in /etc. Logs are usually in /var/log.

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

