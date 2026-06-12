---
title: "Removing/Purging Packages"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by ooobooontooo on 2008-12-12
Hi,

Sometimes, when you download packages, it installs multiple components and things from other packages to make it work, right? However, when I try to remove/purge the original package that I installed these extra components don't necessarily go away, correct? If I don't remember which extra components were installed, is there a way to remove everything (including the extra components) that was installed when I first told installed the package? Thanks in advance.

---

### Post by HereInOz on 2008-12-12
You could open a terminal and type:

sudo aptitude autoclean

This will erase old downloaded packages which are no longer needed.

---

### Post by ooobooontooo on 2008-12-12
Isn't aptitude autoclean used for cleaning the cache of packages, basically the cache that rememebers all the packages that can be downloaded? The man page says that it's for removing packages in the cache that can no longer be downloaded. So, I'm assuing this is for the cache that shows which packages exist for downloads. I'm actually asking about already installed components that came with a package.

---

### Post by mc4man on 2008-12-12
sudo apt-get autoremove

If your running 8.10 then before answering y take a good look at what's being removed.

---

### Post by ooobooontooo on 2008-12-12
Excellent thanks. Will they be coming out with an autopurge capability soon, or is that already implied within autoremove?

---

### Post by mc4man on 2008-12-12
That I don't know (mainly use 8.04

In 8.10 all apt-get build-deps are now marked as automatically installed so they are immediately included in autoremove. I've also seen where some packages that shouldn't be removed are in 8.10, that's why it's good to review the list first.

---

### Post by pyromanic123boom on 2008-12-12
I don't think so. You can only use

sudo apt-get autoremove

To clean out any unnecessary packages. But if you want to clear out dependencies, (purge completely), Synaptic works well. Just click on the box and check "mark for complete removal".

---

### Post by fubbleskag on 2008-12-12
can't you use the --purge switch with autoremove?
```
sudo apt-get --purge autoremove
```

---

