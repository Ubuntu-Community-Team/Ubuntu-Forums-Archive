---
title: "[SOLVED] Having problems with synaptic/terminal installation.."
date: 2008-12-29
forum: New to Ubuntu
---

### Post by MrJoeyUK on 2008-12-29
Okay so whenever I open synaptic I get the following.. 

```
dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

And I also get the same thing in terminal when I use 'sudo apt-get install xxxx'

What's causing this? And how do I fix it? Thanks for any help you can offer.

Joey.

---

### Post by adult swim on 2008-12-29
you need to run from a terminal
```
sudo dpkg --configure -a

sudo apt-get update
```

this is caused by an update being interrupted and not finishing.

---

