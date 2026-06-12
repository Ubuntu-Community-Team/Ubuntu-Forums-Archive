---
title: "Noob Trouble Installing Deb Pkg"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by onaridge on 2010-11-14
I am trying to install my first deb pkg, Teamviewer, and I am missing something here. The file is in my downloads folder and I guess I need my hand totally held for this one. Whether I have .deb on the end or not the outcome is the same. The folder is called teamviewer_linux_x64.deb

lori@lori-laptop:~$ sudo dpkg -i teamviewer_linux_x64
dpkg: error processing teamviewer_linux_x64 (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 teamviewer_linux_x64

---

### Post by karthick87 on 2010-11-14
First you should get inside the **Downloads** directory and then install it.
```

cd Downloads
sudo dpkg -i teamviewer_linux_x64.deb
```

---

### Post by Paqman on 2010-11-14
Just double-click on it. It'll open up the package manager and away you go.

---

### Post by onaridge on 2010-11-14
I couldn't change directory, I bet I had downloads instead of Downloads. I am still Windows oriented. I didn't know you could just click on them! Oh well, I got it installed....thank you!

---

### Post by karthick87 on 2010-11-14
Mark this thread as solved then.

---

