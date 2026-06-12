---
title: "Where do I put shared files?"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by Listerofsmeg01 on 2009-11-09
Hi all,

I am setting up some game emulators. Currently I have all my games sat in my home folder, but I want to move them to some shared area so that anyone can use them.

I am not familiar enough with the Linux filesystem to know where to put them. Should they go in /usr/share or somewhere else?

Cheers,
Lister

---

### Post by synicalx on 2009-11-09
> **Listerofsmeg01 said:**
> Hi all,

I am setting up some game emulators. Currently I have all my games sat in my home folder, but I want to move them to some shared area so that anyone can use them.

I am not familiar enough with the Linux filesystem to know where to put them. Should they go in /usr/share or somewhere else?

Cheers,
Lister

You should be able to put them into whatever file you want (*should*) and then right click on it and hit "Sharing options", check "Share this" and select apply.

---

### Post by Listerofsmeg01 on 2009-11-09
Many thanks, but I think you're misunderstanding my question slightly. I don't have a problem as such, I was just wondering the "correct" place to put them in the filesystem (as opposed to just sticking a folding off root for example).

ETA: And by "share" I just mean other users on the same PC can use them. Not sharing over the network or anything.

---

### Post by enyoj on 2009-11-09
There's no folder to put shared files in by convention. You can create a folder anywhere you want - probably somewhere in your home folder - and then give that folder the correct file/folder permissions.

You should add the users to the same group and then make the folder accessible by the users of that group.

---

### Post by kdavies on 2009-11-09
we tried creating a user called shared
everything we want shared is then in /home/shared
and altered the permissions accordingly

---

