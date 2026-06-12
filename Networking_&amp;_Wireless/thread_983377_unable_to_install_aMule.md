---
title: "unable to install aMule"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by Quaggles on 2008-11-15
Hi,

I've I just formatted my previous installation of ubuntu (7.04) and installed 8.10. I'm used to adding applications from the Add/Remove Software feature I tried to add aMule and I get this error. 


Cannot install 'amule'

This application conflicts with other installed software. To install 'amule' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

I got into synaptic but I'm not sure which package conflicts with it. Any ideas?

---

### Post by cariboo on 2008-11-15
If you go to synaptic and mark amule for inatallation then click apply, a window will pop up and show the conflicting packages.

Jim

---

### Post by Quaggles on 2008-11-16
THanks! That worked for me.

---

### Post by AlexOK on 2008-12-06
Also, you can use the terminal

Applications -> Accesories -> Terminal

And type on it:

```
sudo apt-get install amule
```

When asked for password, use the password you login on the system

That will remove the conflictive package and install amule for you

---

