---
title: "Can't update!! help!!"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by rkakkar on 2009-10-12
My proxy settings are not working in the command line. As a result of which I can't do apt-get update.

I'm currently using Kubuntu Karmic and KPackage Kit is broken!! So basically I can't update and neither can I install any new software. When Karmic releases, how can I update my system from its current Beta state to the final one?

---

### Post by mgranet on 2009-10-12
KPackageKit is known broken (mentioned in the beta release notes), and will be fixed by release time. In the mean time there are plenty of alternatives, such as Synaptic.

If your proxy settings are not allowing apt-get to update, then it's unlikely that ANY package manager will be able to do anything, as they are really just front-ends for apt-get.

---

