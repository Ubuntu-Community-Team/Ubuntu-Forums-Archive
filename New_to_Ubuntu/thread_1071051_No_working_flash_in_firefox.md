---
title: "No working flash in firefox"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by timpdx on 2009-02-15
I cannot get flash to install on Firefox. At all. Tried the Adobe Ubuntu installer, 5 times. The .deb installer says I already have Flash and do I want to reinstall. yes. Nothing. I tried installing via the applications menu in Ubuntu. Nothing. Hulu says I don't have flash every time. Youtube won't play videos.

Also tried the gnu flash player, nothing.

and by the way, how on earth do I remove gnash, in case that is causing the problem? Add/Remove says that I have to use Synaptic to get rid of it., but I do a search and there is no gnash listed at all. I do a history and see that I installed gnash, but how on earth do I remove it?

---

### Post by RomeReactor on 2009-02-15
To remove Gnash from the terminal:
```
sudo aptitude purge gnash mozilla-plugin-gnash gnash-common
```
It's probably conflicting with Flash.

Also, enter:
```
about:plugins
```
in Firefox's address bar, and post the entries you get for "Shockwave Flash".

---

### Post by timpdx on 2009-02-15
Yes, gnash was causing the problems.

Synaptic search function does not come up with gnash when I search, but I scrolled waaaaaay down and found the bugger. 

Problem solved. Thx.

---

