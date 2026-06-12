---
title: "I would like to get rid of KDE (no offense intended)"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by eddski on 2009-12-30
I would like to remove KDE if that is possible. I have been using Gnome and it suits me fine. However I get updates for KDE and as far as I know I don't use it. I don't plan on using it and like the saying "if it aint broke, don't fix it". I tried KDE w/Fedora and didn't really like it. I would just like to remove if that's possible.

---

### Post by x33a on 2009-12-30
how did you install kde in the first place. 

if it was a metapackage, then try 
```
sudo apt-get remove <pkg>
```

pkg = kde metapackage.

if it was many different packages, then you'll have to remove them individually, i am afraid.

---

### Post by avacado on 2009-12-30
I use K9copy and Ksirk and other packages written for kde, seem to integrate fine with gnome and I am sure they update.

---

### Post by anewguy on 2009-12-30
You can also just go to synaptic package manager (system/administration/synaptic package manager), put KDE in the search, then "uncheck" the kde desktop package and click "apply".

Dave :)

---

### Post by brommage on 2010-01-02
Try the commands listed here:  [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by Wiebelhaus on 2010-01-02
Sounds like your using something written for KDE , Like Amarok?

---

