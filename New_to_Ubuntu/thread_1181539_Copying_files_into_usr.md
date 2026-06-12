---
title: "Copying files into /usr"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by k_squired on 2009-06-08
I presume I have to use sudo for this, but I'm not sure how -- thanks for any help.  

Also is there a way to merge multiple folders doing this?  ie, take a user folder with subfolders and merge them all

---

### Post by keplerspeed on 2009-06-08
Ok to copy a directory from the home folder to /usr:

```

sudo cp -r directory_name /usr/

```
the -r flag is recurrsive, to copy the files within the folder.

---

### Post by keplerspeed on 2009-06-08
However, to copy a file, it is exactly the same, without the -r:

```

sudo cp file_name.txt /usr/

```

---

### Post by k_squired on 2009-06-08
Uh help me out on this one a little bit I had usr2 in my desktop, which i cd'd to... I ran something like sudo cp -r /usr /usr2 and it just hung indefinitely in my system, if CPU usage is right, even though I thought I closed the terminal.  (either way the terminal hung indefinitly)

Probably a beginner's error, but what could cause that?
cd -r

---

