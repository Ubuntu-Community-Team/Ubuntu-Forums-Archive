---
title: "Erase an entire disk"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by Slownis on 2010-04-16
Hi there,

I'm on Ubuntu 9.10 and I have to mail a flaky 640 gig WD Caviar disk drive back to WD for a refund.  The drive still works, its just flaky.  It has about 300 gigs worth of pics and movies that I need to erase for good.  I need something like a file shredder utility that works recursively on the entire disk.  Or would reformatting make the contents of it unreadable?  Please let me know.  I can work my way around the command line if needed.

Thanks!

---

### Post by e4uforums on 2010-04-16
Give this a shot...

[http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)

---

### Post by sandyd on 2010-04-16
one word : dban

---

### Post by ajgreeny on 2010-04-16
How securely do you need to delete the data?  If it must be completely deleted so that it can never ever be recovered, you can use dban (Duke's Boot And Nuke), or you could simply use dd to overwrite the disk with zeros ```
sudo dd if=/dev/zero of=/dev/sdb
```Just make sure you get the **of=/dev/sdb** correct, or you are in big trouble and will have deleted data from the wrong disk.

Formatting does not actually remove the data, it just marks the space available for overwriting, so it can later be recovered if someone really tries, though in your case, if there is no confidential data there, it may be enough.

Personally, I would go the dd route.

---

