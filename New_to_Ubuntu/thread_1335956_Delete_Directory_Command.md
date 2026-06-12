---
title: "Delete Directory Command"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by Cooter2543 on 2009-11-24
I have an empty directory that will not delete.

I have tried:

```
$ sudo rmdir /JDownloader_0.8.821
```

When I open the dierctory, or use the ls command, it shows nothing in it. Yet when I try the rmdir command, it tells me:

```
rmdir: failed to remove `/JDownloader_0.8.821': Directory not empty

```

What's going on?

---

### Post by rudy.b on 2009-11-24
There may be hidden files/directories in the directory.  You can check with the 'a' switch on the ls command:

```

$ ls -a /JDownloader_0.8.821

```

---

### Post by Cooter2543 on 2009-11-24
You are right, there is a file named junique. When I try to remove it, I get this:

```
rm: cannot remove `junique': No such file or directory
```

How would I go about getting rid of that pesky file?

---

### Post by HereInOz on 2009-11-24
How about going to the directory above the one you want to remove, and using:

sudo rm -r JDownloader_0.8.821

This will remove all files in the directory, and the directory itself.

---

### Post by Cooter2543 on 2009-11-24
Thanks to you both. It makes me feel all warm and tingly inside to learn how to operate Ubuntu better each day! :D

---

