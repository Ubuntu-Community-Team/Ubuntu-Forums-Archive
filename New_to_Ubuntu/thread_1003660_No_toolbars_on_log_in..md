---
title: "No toolbars on log in."
date: 2008-12-06
forum: New to Ubuntu
---

### Post by ant2ne on 2008-12-06
Ok, something is definatly long.  Other than the evolution problem, I've noticed that mys system occasionally run unusually slow.

Now when I log in, I don't get my toolbars on my desktop. So that seems like as good a place as any to start troubleshooting.

I'd much rather get this OS polished back up to par, rather than simply reinstalling as if it were some chump MS OS.

---

### Post by kansasnoob on 2008-12-06
What's up with evolution?

If it's only the panels that need restored this works:

[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

I rather know what's up with evolution first.

---

### Post by ant2ne on 2008-12-06
Alt+F2 does nothing.  I can goto a virtual terminal with Cntl+ALt+F5 and enter in those commands. But it doesn't change anything. 

I think the missing panels is part of a symptom, not the underlying problem. 

Evolution is not loading, I had opened a thread on it. I removed Evolution, and then removed the .evolution directory.

I'm kind of stumped on this. I'm not sure where to start.

---

### Post by kansasnoob on 2008-12-06
I'd try:

```
sudo apt-get install --reinstall ubuntu-desktop
```

followed by:

```
sudo apt-get -f install
```

---

### Post by ant2ne on 2008-12-06
> **kansasnoob said:**
> I'd try:

```
sudo apt-get install --reinstall ubuntu-desktop
```

followed by:

```
sudo apt-get -f install
```That did it, bars are back. I can launch X apps again. How do I find out what happend, so I can keep it from happening again.

I gotta hand it to linux. The window manage wouldnt' boot, but the CLI still did.

---

