---
title: "Emacs-snapshot-gtk error"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by YankeeFan on 2009-01-01
I'm getting a couple of errors whenever I run new updates on my Ubuntu. I do use emacs and I do not have any problems with it, but I'd like to know how to correct these errors if I can.  If anyone can help me, I'd be very appreciative.   

Following is a display from a terminal window when I do a sudo apt-get on any install:

dpkg: error processing emacs-snapshot (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of emacs-snapshot-gtk:
 emacs-snapshot-gtk depends on emacs-snapshot; however:
  Package emacs-snapshot is not configured yet.
dpkg: error processing emacs-snapshot-gtk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
emacs-snapshot
emacs-snapshot-gtk
E: Sub-process /usr/bin/dpkg returned an error code (1)

I do not know how to do whatever I need to do to correct this.  Help?
Thanks...

---

### Post by xenolalia on 2009-01-02
I do not use emacs personally, but from what you posted, it looks like a reinstall would fix whatever errors you are getting.  Was the installation process interupted the first time?  That would explain the whole "un-configured" thing.  Yeah . . . you might give reinstalling through apt-get or synaptic a shot, but that's about all I can think of right now.

Good luck!
Xenolalia

---

### Post by sav2005 on 2009-01-10
I would try "sudo dpkg-reconfigure emacs-snapshot-gtk" and if that does not work 
do "sudo aptitude remove --purge emacs-snaphot-gtk" and "aptitude install emacs-snaphot-gtk"

Laurie

---

