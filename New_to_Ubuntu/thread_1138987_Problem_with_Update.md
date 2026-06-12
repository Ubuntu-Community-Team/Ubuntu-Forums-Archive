---
title: "Problem with Update"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by TAllen013 on 2009-04-26
I'm having trouble updating "linux image 2.6.27-7-generic", it fails everytime.

It says:
"
E: /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb: unable to make backup link of `./boot/vmlinuz-2.6.27-7-generic' before installing new version
"

Does anyone know how to resolve this?

---

### Post by spiderbatdad on 2009-04-26
The only thing i find relating to this is an unresolved bug report regarding a wubi installation. Is this a wubi install? Not sure what to suggest.

---

### Post by TAllen013 on 2009-04-26
Yeah, it is a Wubi install.

Do you happen to know the purpose of this update?  Is this something that is very important?

---

### Post by spiderbatdad on 2009-04-26
These kind of kernel updates generally include minor bug fixes. If you did some searching, I'm sure you could find the differences...which is like saying errr, sorry I don't know specifically. You are surely fine where you are. I don't know anything about wubi really. Does it have a synaptic package manager? If yes, you can probably lock the current version of the package, if you want to get rid of the update notification for that package.

---

