---
title: "Can't open document"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by flylehe on 2009-03-10
Hi,
I am trying to create a new document without extention but I meet an error when opening it "can't display location: Couldn't display blah blah(the file)". If I add extension ".txt", then I would be able to open it. This happens on my office computer with CentOS under Genome while I don't have such problem with my Ubuntu on my laptop. How to fix it? Thanks!

---

### Post by Peter09 on 2009-03-10
This is because your system believes that files without an extension are directories... normally (in Ubuntu) if you right click on the icon you get a menu which include the option to 'open with'

---

### Post by flylehe on 2009-03-10
Thanks!
In CentOS Gnome, I also have "open with other applications", but once I give it "'/usr/bin/gedit'" in "open with" diaglog, it would say "Could not add application: Could not add application to the application database".

---

### Post by Peter09 on 2009-03-10
in a terminal type
```
which gedit
```

this should tell you the path to gedit, perhaps you have that wrong?

---

### Post by flylehe on 2009-03-10
bash-3.2$ which gedit
/usr/bin/gedit

Seems what I did is correct. Although I cannot open my document by specifying gedit, I can open it in an already-open gedit. Isn't it strange?

---

### Post by tarps87 on 2009-03-10
Try:
```
nano *pathToFile/fileName*
```

You can also try
```
file *pathToFile/fileName*
```

---

