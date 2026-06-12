---
title: "GNUstep"
date: 2011-04-13
forum: New to Ubuntu
---

### Post by PZJM on 2011-04-13
Hey folks, could someone please explain what GNUstep is?  All of a sudden I've found this directory in my home directory.  Do I need it?  I don't remember installing it.

Thanks.

---

### Post by rosencrantz on 2011-04-14
[http://en.wikipedia.org/wiki/GNUstep](http://en.wikipedia.org/wiki/GNUstep)
Check for installed gnustep packages with
aptitude search gnustep
If you don't think you need it, simulate uninstalling with apt-get;
sudo apt-get remove --simulate <the whole list of installed gnustep packages> 
and see whether this would uninstall other packages dependent on gnustep.
If not, you can delete folders and uninstall programs at will.

---

### Post by PZJM on 2011-04-15
Thanks for the advice. I'll give it a try.

---

