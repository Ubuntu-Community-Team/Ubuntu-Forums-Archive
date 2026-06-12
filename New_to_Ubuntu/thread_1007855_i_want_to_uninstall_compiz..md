---
title: "i want to uninstall compiz."
date: 2008-12-10
forum: New to Ubuntu
---

### Post by jsf_pp on 2008-12-10
is there any way to do that?
please tell me just how.

thanks

---

### Post by Hospadar on 2008-12-10
I think if you "sudo apt-get remove compiz" and then "sudo apt-get autoremove" that should do it.
Compiz as a whole has many packages, so you may want to search through synaptic and find the "compiz" and locate all of its dependancies.

But unless you are *really* pressed for disk space (compiz I suspect is well <100Mb) I would just leave it installed, and disable it in System->Preferences->Visual Effects (I believe).

Even with all the 3-d themes turned off, there are some things that still use compiz.  I removed it once and encountered a couple wierd issues, nothing serious though. (you could always re-install it if there are problems).

---

