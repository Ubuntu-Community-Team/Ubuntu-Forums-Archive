---
title: "pick you os screen seems funny"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by ButchButchButch on 2009-11-23
Hello all.
quick question, my screen where I pick my OS looks like this:

Ubuntu 9.04, Kernal 2.6.28-16
Ubuntu 9.04, Kernal 2.6.28-16 generic (recovery)
Ubuntu 9.04, Kernal 2.6.28-16
Ubuntu 9.04, Kernal 2.6.28-16 Generic (recovery)
Ubuntu 9.04, Kernal 2.6.28-16 
Ubuntu 9.04, Kernal 2.6.28-16 Generic (recovery)
Ubuntu 9.04, MEMTEST 86+
Windows Vista

Should this look this way? (the 3 ubuntu is what im worried about)
Should there be only one ubuntu to choose?

If so how do I fix. Im a complete noob so any feedback would be appriciated.

---

### Post by falconindy on 2009-11-23
I'd wager that you've got -14, -15, and -16 listed, not 3 of the same. This is normal, as new kernel releases are pushed out from the repos and installed. If you want to get rid of them, you can open Synaptic and search for "linux-image". Make sure you only select the -14 and -15 for removal and **nothing else** or your system will not boot. Or, you can just leave them there. It's not hurting anything.

---

