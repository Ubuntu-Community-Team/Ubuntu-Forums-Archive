---
title: "Update queries"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by thadacto on 2009-02-20
I've just updated my hardy 8.04 via the update manager which informed me:
> Failed to fetch [http://ar.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-amd64/Packages.gz](http://ar.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://ar.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-amd64/Packages.gz](http://ar.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://ar.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-amd64/Packages.gz](http://ar.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://ar.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-amd64/Packages.gz](http://ar.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://ar.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/source/Sources.gz](http://ar.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://ar.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/source/Sources.gz](http://ar.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://ar.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/source/Sources.gz](http://ar.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://ar.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/source/Sources.gz](http://ar.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Some index files failed to download, they have been ignored, or old ones used instead.
The first line of quote should continue:
.... /dists/feisty-backports/main/binary-amd64/Packages.gz[/url]  404 Not Found [IP: 91.189.88.46 80]
Only Feisty I can find on the machine are:
feisty-gdm-themes
feisty-session-splashes
feisty-wallpapers
As I am running Hardy, why is it trying to update an much older system?
I don't think I have deleted any repositories. 
What are the "backports" it's trying to update?
Many thanks in advance

---

### Post by taurus on 2009-02-20
You need to have a look at your /etc/apt/sources.list.  If you are running hardy, then you should not have any repos for feisty in there at all.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by thadacto on 2009-02-20
Thanks taurus, I'll give that a try.
How come you're always there to help me? You seem to be my saviour when I have problems!!

Yep, that seems to have got rid of those "Failed to fetch" - to be on the safe side, I just ## those entries.
Many thanks

---

### Post by taurus on 2009-02-20
I am not really here; it's my evil twin!  :evil:

---

### Post by thadacto on 2009-02-20
With me, it's either me or my shadow!!!

---

