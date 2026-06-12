---
title: "mozilla firefox"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by misswham on 2009-04-10
For the past 2 weeks, everytime I try to close firefox, it takes a while and then the screen goes dark and asks me to force quit.  why is this doing this all of a sudden?

---

### Post by kaibob on 2009-04-10
> **misswham said:**
> For the past 2 weeks, everytime I try to close firefox, it takes a while and then the screen goes dark and asks me to force quit.  why is this doing this all of a sudden?

Often that is caused by an extension or plugin. To check this, create a new profile by entering "firefox -ProfileManager" in a terminal window.

---

### Post by computermacgyver on 2009-04-10
I've also gotten this depending on the pages/tabs currently open. If there is a page with an intensive script or flash movie or just a lot of tabs open this can sometimes happen.

You can also use "firefox -safe-mode" to try running without plugins/themes just for one run. If that solves the problem, then look at removing a newly installed plugin, etc.

---

