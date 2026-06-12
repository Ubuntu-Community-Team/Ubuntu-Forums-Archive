---
title: "Deluge latest release"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by Rician on 2010-09-10
How do i get the latest Deluge version from Deluge team? the ubuntu repository dosent have the latest release. Please help me to get it.

The latest release from Deluge is 1.3.0. rc2 

ubuntu repository only have 1.2.3.

Thanks

---

### Post by beew on 2010-09-10
Download from the Deluge website (their PPA doesn't have the latest)

EDIT: Or get it from Maverick's repository. ;)

---

### Post by Rician on 2010-09-10
Why dosent deluge have the latest in their PPA?

Whats the name of Maverick's repository?

---

### Post by ~Aquatic on 2010-09-10
Go to Software Sources and add this to "Other Software"

```
**ppa:deluge-team/ppa**
```

Currently Hardy, Intrepid, Jaunty, Karmic and Lucid are supported.

More info here: [https://launchpad.net/~deluge-team/+archive/ppa]("https://launchpad.net/%7Edeluge-team/+archive/ppa")

---

### Post by Rician on 2010-09-10
i dont want 1.2.3.. i want latest :)
what about maverick repository? name?
 if the only way to get the latest release is by compiling it myself. How do i compile it?

---

### Post by beew on 2010-09-10
It doesn't have the latest in the PPA (~Aquatic's link) because they are behind in uploading the latest package. Last I checked was a few days ago but Deluge has been prompting me to upgrade to 1.3 for at least a month, maybe they have updated it since.

So just download from their website if you must have Deluge1.3 (which is probably not necessary).

You can enable the Maverick repo in Lucid if you are careful about what you do but mixing repositories is  not recommended. :)

**Edited:**

OK, in their website it is either the ppa or source. So there is no .deb. 

But you can get the latest from a different PPA.

[http://www.techdrivein.com/2010/06/install-latest-deluge-130-rc1-in-ubuntu.html](http://www.techdrivein.com/2010/06/install-latest-deluge-130-rc1-in-ubuntu.html)

---

### Post by ~Aquatic on 2010-09-10
If you want the latest version. Here's a tutorial on how to install Deluge from source.

[http://dev.deluge-torrent.org/wiki/Installing/Source](http://dev.deluge-torrent.org/wiki/Installing/Source)

EDIT: I think 1.2.3 is the latest stable version. 1.3.0 is just a release candidate, right?

---

### Post by Rician on 2010-09-10
Ok i will try to compile it by myself... its a bit to advanced for my brain,lol.

---

### Post by VastOne on 2010-09-10
> **Rician said:**
> why is it not recommended?

Different kernels, different dependencies, different applications.

As was stated, you can do it but it is risky and opens many opportunities for other problems.

---

### Post by ivanovnegro on 2010-09-10
> **Rician said:**
> why is it not recommended?

Because when you mix the repositories you could go with problems while upgrading to Maverick once it becomes stable, dependencie problems and so on.
You can find information about this in the Ubuntu wiki.

---

### Post by beew on 2010-09-10
Don't need to compile from source.
[http://www.techdrivein.com/2010/06/i...in-ubuntu.html](http://www.techdrivein.com/2010/06/i...in-ubuntu.html)

Enable Ferromosca Roberto's ppa as instructed.

---

### Post by Rician on 2010-09-10
Thanks Beew, and everyone else. i now have deluge 1.3.0 rc installed :D

---

### Post by ~Aquatic on 2010-09-11
> **Rician said:**
> Thanks Beew, and everyone else. i now have deluge 1.3.0 rc installed :D
Don't forget to mark the thread as solved.
[I]
Thread Tools > Mark this thread as solved[/I]

---

