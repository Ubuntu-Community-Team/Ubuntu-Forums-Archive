---
title: "linux-restricted-modules-ARCH download?"
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2006-12-17
linux-restricted-modules-ARCH???
[https://help.ubuntu.com/community/DialupModemHowto/Lucent](https://help.ubuntu.com/community/DialupModemHowto/Lucent)
(To check that the necessary package is installed, use your package manager, e.g. Synaptic or Adept. You need to look for a package, which is called linux-restricted-modules-ARCH, where ARCH is the last part of the $ uname -r output, i.e. your kernel flavor. If it is not installed yet, install it there.)

I dont seem to have this package. where do you get it?

---

### Post by sdowney717 on 2006-12-18
The difference I have discovered between windows XP and linux is windows works right out of the box for almost everything. where as linux you have to be a geeky compiler computer nerd or know someone who is.
Documentation is meaningless if not fully explained and cross referenced.
There should not be 'Oh, if this is not installed even though should have been by default, simply install it.' With of course no link or explanation of how to do it or where to get it. In fact I bet many of you dont even know either.

---

### Post by spd106 on 2006-12-18
Yes this should have been installed by default. 

You will find it in System -> Admin ->  Synaptic Package Manager. Do a search for linux-restricted-modules, there will be two packages to install, plus two other dependencies. These are the linux-restricted-modules-common and linux-restricted-modules-2.6.17-10-generic if you are using the generic kernel, plus the module-init-tools and nvidia-kernel-common. If you have 386 or k7 etc then there will be a separate package instead of the -generic one. 

If you can't find them in synaptic, or only have access through windows, then try downloading them directly from [here]("http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/").

---

### Post by sdowney717 on 2006-12-20
Thanks very much!
I had tried google but this did not show up.

---

