---
title: "Problem in Opening Synaptic Packet Manager"
date: 2011-09-07
forum: New to Ubuntu
---

### Post by manishlogan on 2011-09-07
Hello folks. I am facing problem in using SPM. Whenever I open it, it gives this error:

E: Unable to parse package file /var/lib/apt/lists/archive.getdeb.net_ubuntu_dists_lucid-getdeb_games_binary-i386_Packages (1)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

When I click on Close button below the error, it closes the SPM. Can someone inform me how to fix it..

---

### Post by snip3r8 on 2011-09-07
Does it give you the same message if you type

```
sudo apt-get update
```

---

