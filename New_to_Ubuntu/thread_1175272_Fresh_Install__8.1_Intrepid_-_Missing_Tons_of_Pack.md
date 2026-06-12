---
title: "Fresh Install  8.1 Intrepid - Missing Tons of Packages?"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by mistypotato on 2009-05-31
Hi,

I reinstalled ubuntu 8.1 today and found lots of missing (seemingly unavailable packages)

For example, there are no apache packages available and Firestarter was not available (in synaptic).

All repositories are checked so Im stumped on this one.

Suggestions?

thx

---

### Post by geekygirl on 2009-06-01
Hopefully I am not stating the obvious but did you ```
sudo apt-get update 
``` after checking all the repo's off in synaptic (or reload that is in the GUI)?
 
You could also double check your sources.list file and see whats going on:
 
```
 
gksudo gedit /etc/apt/sources.list

```
and make sure all the repo's are uncommented (remove the #'s) and you can always try removing the locality part of the repo address as well for me the local repo's have an au. in the address, if I have issues downloading from them I remove the au. part in the address and have had great sucess (usually helpful if the local repo's are playing up lol)

---

