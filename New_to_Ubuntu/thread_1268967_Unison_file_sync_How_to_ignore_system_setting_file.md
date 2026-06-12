---
title: "Unison file sync How to ignore system setting files using graphical interphase?"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by donniezazen on 2009-09-17
Hi,

As the heading says I am using Unison to sync my Ubuntu Laptop and Ubuntu netbook but when using graphical interface Unison is scanning and copying all files including hidden system files & logs How can i stop if from scanning and copying the system files and hidden files?

[http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-manual.html#ignore](http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-manual.html#ignore)

This tutorial expalins how to ignore system files for terminal and i couldnot find instructions for graphical interface.

Please help.
SK

---

### Post by darthmob on 2009-12-22
It's unlikely you are still looking for a solution but your link helped me.

You can find your unison profiles (profilename.prf) in the *~/.unison/* directory. You can edit them with any text editor and adjust the rules just like it's described in the manual.

For example to ignore hidden files / folders (typically starting with a dot on unix filesystems) you can use:
```

ignore = Name .*

```

Depending on how the system files look like you have to add more rules to ignore complete directories or paths.

---

