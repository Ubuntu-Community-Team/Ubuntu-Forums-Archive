---
title: "Help. Package manager not working"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by Nervouswreck on 2009-07-03
I tried to install wine using the apt-get command. I get the following:
```

$sudo apt-get install wine
**************** #enter password
Reading package lists... Done
Segmentation faulty tree... 0%
$

```
When I tried the GUI synaptic package manager the window opened but did not load the list of packages before it closed.

I was playing around with the panels in gnome before this happened but I don't see why that would make a difference. Earlier, I also tried downloading a different package over a wifi network and lost my signal in the middle, but I have no clue why that would do anything either.

Hope someone can help, thanks.

---

### Post by jmszr on 2009-07-03
Nervouswreck,

There is an off-chance that this might help:```
sudo rm /var/cache/apt/*.bin
```

---

### Post by Nervouswreck on 2009-07-03
It did. I appreciate it. Explanation please?

---

### Post by jmszr on 2009-07-03
Nervouswreck,

Near as I can figure, when your download got cut off it left some debris behind - the code I gave you cleared it out.

---

### Post by Nervouswreck on 2009-07-03
Sorry, I can't expect to bug you for info if I can't even frame my question, can I?

I know the rm command (and obviously sudo if I'm using apt-get). My questions were:
a)what are those 2 .bin files?
b)how do their contents affect how apt-get accesses the repositories?
c)wouldn't any debris from the download be found in the directory the package gets installed to, not the cache?

---

### Post by jmszr on 2009-07-03
Nervouswreck.

Sorry, good questions all, but north of my pay-grade (so to speak). I would be interested in knowing the answers - I have an inkling, but nothing I'd say with the slightest certitude - it would be conjecture at best (and probably wrong).

---

