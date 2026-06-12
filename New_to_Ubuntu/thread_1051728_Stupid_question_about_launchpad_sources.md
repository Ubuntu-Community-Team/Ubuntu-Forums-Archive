---
title: "Stupid question about launchpad sources"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by jakupl on 2009-01-27
I just did what nobody should do, I added sources to my sources.list without really knowing what they do.
I added the launchpad sources.
```
deb http://ppa.launchpad.net/do-core/ubuntu hardy main
deb-src http://ppa.launchpad.net/do-core/ubuntu hardy main 
```
 When I ran the update manager there were a lot of security updates,
So what do the launchpad sources really contain? Is it buggy?

---

### Post by theozzlives on 2009-01-27
I'm adventurous and keep good backups so I would install them and find out.

---

### Post by kostkon on 2009-01-27
> **jakupl said:**
> I just did what nobody should do, I added sources to my sources.list without really knowing what they do.
I added the launchpad sources.
```
deb http://ppa.launchpad.net/do-core/ubuntu hardy main
deb-src http://ppa.launchpad.net/do-core/ubuntu hardy main 
```
 When I ran the update manager there were a lot of security updates,
So what do the launchpad sources really contain? Is it buggy?
You can see what this PPA offers [here]("https://launchpad.net/~do-core/+archive").

I don't see anything strange on there.

It is just a coincidence that you also got security updates. That happened because after your added the PPA, you did an apt-get update, either manually or automatically (if you added the PPA using the Software Sources utility).

Furthermore, just to know, I don't think thay you can get updates from a PPA labeled as security in the update manager; this only can happen for packages from the "official" repos.

---

