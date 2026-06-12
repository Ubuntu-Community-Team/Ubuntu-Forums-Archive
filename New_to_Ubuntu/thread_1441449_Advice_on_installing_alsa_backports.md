---
title: "Advice on installing alsa backports"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by johnfrith on 2010-03-28
I'd like to install the alsa backports, in case it helps with a sound problem I'm having. Synaptic shows various backports with also in their name, eg:
linux-backports-modules-alsa-2.6.31-XX-generic-pae

Half don't have the pae at the end.

My kernel is 2.6.31-20-generic-pae, so do I install all of them, or just the one with the number that matches the kernal? 

Do I install the pae version only?

Also the notes for all say

"You likely do not want to install this package directly. Instead, install the linux-backports-modules-alsa-generic-pae meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed."

but even linux-backports-modules-alsa-2.6.31-20-generic-pae says this. Isn't it referring to itself?

Advice appreciated. Just don't want to do something wrong in case it messes everything up. A little knowledge is a dangerous thing!

---

### Post by sandyd on 2010-03-28
> **johnfrith said:**
> I'd like to install the alsa backports, in case it helps with a sound problem I'm having. Synaptic shows various backports with also in their name, eg:
linux-backports-modules-alsa-2.6.31-XX-generic-pae

Half don't have the pae at the end.

My kernel is 2.6.31-20-generic-pae, so do I install all of them, or just the one with the number that matches the kernal? 

Do I install the pae version only?

Also the notes for all say

"You likely do not want to install this package directly. Instead, install the linux-backports-modules-alsa-generic-pae meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed."

but even linux-backports-modules-alsa-2.6.31-20-generic-pae says this. Isn't it referring to itself?

Advice appreciated. Just don't want to do something wrong in case it messes everything up. A little knowledge is a dangerous thing!
install
linux-backports-modules-alsa-karmic-generic-pae

---

### Post by johnfrith on 2010-03-28
Thanks carlee. Obviously a woman who likes to cut to the chase.

Hope that means the same in LA as it does in the UK!

---

