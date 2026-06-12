---
title: "I'm so close to getting this wireless card working."
date: 2010-03-11
forum: New to Ubuntu
---

### Post by Everynameistaken on 2010-03-11
[http://ubuntuforums.org/showthread.php?p=8827649](http://ubuntuforums.org/showthread.php?p=8827649)

Okay, I've downloaded this driver and I'm trying to run the terminal operations, but no folder called "hybrid" is created when it's extracted or anything, so I can't change to that directory.

---

### Post by J_Stanton on 2010-03-11
> **Everynameistaken said:**
> [http://ubuntuforums.org/showthread.php?p=8827649](http://ubuntuforums.org/showthread.php?p=8827649)

Okay, I've downloaded this driver and I'm trying to run the terminal operations, but no folder called &quot;hybrid&quot; is created when it's extracted or anything, so I can't change to that directory.

you don't need to have a directory named hybrid. hybrid is the file you downloaded. mv ~/Desktop/hybrid-portsrc-x86_32-v5.60.48.36.tar.gz ~/dev is what you want. for the rest of the steps replace hybrid* with hybrid-portsrc-x86_32-v5.60.48.36.tar.gz

---

### Post by spiderbatdad on 2010-03-11
so you are following carlee's post?
You create a directory called ~/dev and move the tar package into it?
when you untar do ```
tar -xvzf hybrid<use the tab key to autocomplete package names>
```After that command enter command
```
ls
```to list what is in your newly created ~/dev directory. Post the output of your terminal sessions here.

---

