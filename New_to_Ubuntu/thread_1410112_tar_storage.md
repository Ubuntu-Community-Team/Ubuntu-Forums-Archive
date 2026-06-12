---
title: "tar storage??"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by Mike242 on 2010-02-18
is it possible to save installed programs to transfer to the next upgrade

Many thanks for the replies the replies/advice  I also tried apt on cd but it failed to complete its search

the storage location will be helpful

---

### Post by Sir Jasper on 2010-02-18
If you use Update Manager to Upgrade to 9.10 (as opposed to a fresh install) you can elect to retain your existing packages. I would recommend you clone or image 9.04 before doing that; then if, for whatever reason, you want to go back to 9.04 that should be possible.

My regards

---

### Post by mcduck on 2010-02-18
> **Mike242 said:**
> is it possible to save installed programs to transfer to the next upgrade

If you just do the upgrade over the internet (using the update manager, as opposed to making a fresh install of the new release from CD), all your programs will be kept (although the upgrade will of course also upgrade those programs to new versions).

However if you do a fresh install from CD storing the program packages from old relase would be qute pointless, as pretty much every single package would be old version and you'd just end downlaoding the new packages as updates anyway.

(Still, if you need to store packages for programs you have installed, you'll find the .deb packages in /var/cache/apt/archives)

---

### Post by Mike242 on 2010-02-22
Tha

---

