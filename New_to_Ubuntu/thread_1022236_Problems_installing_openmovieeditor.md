---
title: "Problems installing openmovieeditor"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by Vagabond_Cookie on 2008-12-26
I'm pretty new to linux, and I've been trying to install this program.
Unfortunately its a tar.gz.

I tar'd it, and ls/directoried it, and I was './configure'ing it when it stopped because "C++ compiler cannot create executables"

Help?

---

### Post by Toshibawarrior on 2008-12-26
> **Vagabond_Cookie said:**
> I'm pretty new to linux, and I've been trying to install this program.
Unfortunately its a tar.gz.

I tar'd it, and ls/directoried it, and I was './configure'ing it when it stopped because "C++ compiler cannot create executables"

Help?

Go to a terminal and type:

```
sudo apt-get install build-essential
```

Looks like you don't have the necessary packages to build applications/programs...Also make sure you're using the correct directories...

Or better yet, go to Synaptic Package Manager (System>Administration>Synaptic Package Manager) and search for:

openmovieeditor

the version might be outdated but it's almost certain to work with almost no problems.


Let me know how it goes.

---

