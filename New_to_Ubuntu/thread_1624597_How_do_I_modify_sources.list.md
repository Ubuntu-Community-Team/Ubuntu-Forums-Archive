---
title: "How do I modify sources.list ?"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by ericstrom on 2010-11-17
Running Lucid and having a problem with updates. I think I've traced the problem to the fact that all the entries in sources.list are not showing up in the "Other Software" tab of repositories in Synaptic. It looks like I have some excess entries that should be deleted (at least in sources.list).

I tried to delete what I think are the unwanted entries by opening sources.list using GetEdit. But it looks like that is a read only file. So how do I make changes ?

---

### Post by garvinrick4 on 2010-11-17
Hit Alt and F2 and in box type gksudo nautilus and you will be in root nautilus, so can make changes and save. Or can:
 ```
 gksudo gedit /etc/apt/sources.list 
```
in a terminal will accomplish the same task.

---

