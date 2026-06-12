---
title: "libunity4 missing?"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by rkrakora on 2011-05-07
I'm running the latest 11.04 Ubuntu and I'm trying to use the Update Manager.  I can download the updates but get a "missing libunity4" package error when it attempts to install.  Is that something I can recover by using the command line?

Thanks all!

Rich

---

### Post by rkrakora on 2011-05-07
bump.... anybody having this problem?

---

### Post by dFlyer on 2011-05-07
can you run synaptic? if so you might want to try and install it from there. If you use the command line: sudo apt-get -f install will install missing file or lib.

---

### Post by rkrakora on 2011-05-08
dFlyer - Thanks for the reply.  Yes, if I use synaptic, same deal.  It downloads but no install.  So is this the proper command?

sudo apt-get -f install libunity4

---

### Post by dFlyer on 2011-05-08
No just enter:

sudo apt-get -f install

That should fix any missing lib.

---

