---
title: "What's new about Grub and why in 9.10?"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by carusoswi on 2009-11-26
This is not a complaint, but, because I ran into some problems during an update I came to realize that 9.10 uses a new type of Grub than previous versions.  Can someone explain to me the changes, the advantages, and how I now back up the necessary file in order to restore grub if it becomes corrupted?  I am told that menu.lst is no longer used.

Thanks.

Caruso

---

### Post by jrrader on 2009-11-26
It has a much more advanced method of creating that list you see at startup.  It is generated from scripts that gather information about your drive rather than being a flat file.  There's more - I'm sure someone else will come along to tell you.

---

