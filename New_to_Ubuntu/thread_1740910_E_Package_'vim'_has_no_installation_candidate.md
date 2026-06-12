---
title: "E: Package 'vim' has no installation candidate"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by mustafa ibrahim on 2011-04-27
help i just installed my ubuntu server now there a starnge thing


root@ubuntu:/home/mustafa-sr1# apt-get install vim
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package vim is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'vim' has no installation candidate
root@ubuntu:/home/mustafa-sr1#

---

### Post by dnairb on 2011-04-27
If you have only just installed Ubuntu, you need to run the following first:

```
sudo apt-get update
```

Then try installing vim again

---

### Post by mustafa ibrahim on 2011-04-27
i solved this problem with


apt-get update



thanks

---

