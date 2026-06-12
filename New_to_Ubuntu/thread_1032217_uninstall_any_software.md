---
title: "uninstall any software ??"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by usman idrees on 2009-01-06
I want to uninstall Audio Cd Extractor software. How can I do this graphically?

---

### Post by tarps87 on 2009-01-06
Click on applications -> add/remove
now search using the name of the program, untick the box and click apply

You can also go to synaptic this is in System -> administration -> synaptic package manager (or package manager, I can't remember the exact name)
Now search of the package name click on the green box a select mark for removal or mark for complete removal and then click apply.

This is assuming you are using the gnome desktop (if it is the default Ubuntu install then you will be)

To remove a package in the command line
```

sudo apt-get remove *packageName*

```
or for complete removal
```

sudo apt-get purge *packageName*

```
I know you didn't asked about the command line method but it can't hurt to know :)

---

