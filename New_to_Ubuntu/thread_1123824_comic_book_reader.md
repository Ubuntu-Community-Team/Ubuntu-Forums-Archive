---
title: "comic book reader"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by Archie69 on 2009-04-12
So I have a bunch of comics on my computer and am not able to view any of them.  I had to re-install ubuntu 8.04 and when i transfered the comics back over, some still are viewable in 'document reader' or 'comix' but most of them can't be viewed.  The books are all listed as either .cbz or .cbr 

I never had  a problem before but now can't view them.  When the documents open in comix the error is "could not find the unrar executable.  please install it if you wish to open RAR archives."

I'm lost.  any help guys?

---

### Post by ad_267 on 2009-04-12
Try installing the "rar" and "unrar" packages.

---

### Post by Archie69 on 2009-04-12
I don't know how to do that or where I would start.  All I have are the comics, I no longer have the packages they were downloaded from.

---

### Post by llamabr on 2009-04-12
```
brock@hops:~$ apt-cache search unrar
comix - GTK Comic Book Viewer
unp - unpack (almost) everything with one command
unrar-free - Unarchiver for .rar files
unrar - Unarchiver for .rar files (non-free version)
brock@hops:~$ 

```

So just:

```
sudo apt-get install unrar unrar-free
```

---

### Post by ad_267 on 2009-04-12
Go to System - Administration - Synaptic Package Manager. Click on search and search for packages with "rar" in the name. Right click on rar and unrar and select mark for installation then click on Apply.

If you have any problems, go to Settings - Repositories and make sure universe, restricted and multiverse are ticked then click the Reload button.

---

### Post by Archie69 on 2009-04-12
Cool.  Thanks guys.  I went to Add/Remove and typed .rar and installed the compression tool.  Thanks.

---

