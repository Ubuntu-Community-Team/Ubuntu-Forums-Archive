---
title: "WAG511 Stopped Working."
date: 2007-08-09
forum: Networking &amp; Wireless
---

### Post by tuaris on 2007-08-09
I just ran an update and it asked me to reboot.  After that, my Netgear WAG511 stopped working.

---

### Post by moore.bryan on 2007-08-10
*was it a kernel update and did you compile your own drivers for the wag?  if so, you'll need to recompile the drivers...*

---

### Post by tuaris on 2007-08-10
I think it was a Kernel update.  I never compiled my own drivers, I just used what ever came with 7.04.

---

### Post by moore.bryan on 2007-08-11
*what kernel are you now running?  do me a favor and try using one of the other kernels in your grub menu; post if the problem persists... that'll tell us if it's a kernel-related issue.*

---

### Post by tuaris on 2007-08-11
It worked fine when I booted with the 2.6.20-15 kernel.  It didn't work when I booted with 2.6.20-16.  Both options had "Generic" next to them.

---

### Post by moore.bryan on 2007-08-11
*well, that tells us the new kernel has some networking option either disabled or set to manual.  i'm not too sure what fix(es) there are/will be...  i'd have a look around the net and forums to see if there are any discussions of your issue specific to the 2.6.20-16-generic kernel.*

---

### Post by tuaris on 2007-08-13
This is strange, a day later I boot back into the new kernel and the WAG511 is working again.  Something must have gotten reset when I booted the old kernel. 

I rebooted about 3 times when I couldn't get the wireless to work in the new kernel.  Any idea what may cause this?

---

### Post by moore.bryan on 2007-08-13
[I]not a clue... the ubuntu gods must favor your success.
;-)[/I]

---

