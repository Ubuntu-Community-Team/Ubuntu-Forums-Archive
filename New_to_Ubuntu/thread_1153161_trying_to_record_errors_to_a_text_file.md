---
title: "trying to record errors to a text file"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by kaston on 2009-05-08
so i am having some problems with a firefox plugin called zotero.  i have set up the about:config options so that when i open firefox via the command line, it displays all the log into on the terminal but there is too much data to fit in the terminal.  i know it's possible to use the pipe command "|" to pipe this to a file but i'm not sure how.  any help is appreciated.

---

### Post by sisco311 on 2009-05-08
just redirect the output to a file:
```
firefox > firefox.log
```

---

