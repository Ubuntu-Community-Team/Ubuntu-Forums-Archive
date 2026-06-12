---
title: "defrag and wubi"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by jfloydb on 2009-05-04
can/will 9.04 go through it's regular defrag and clean-up routines with a wubi install? I have been using jaunty a lot since 4/23 and it hasn't happened yet... Thanks...

---

### Post by bodhi.zazen on 2009-05-04
I am not sure but I do not see any reason it would not.

wubi is installed into a file and windows should treat it as any other file.

---

### Post by jfloydb on 2009-05-10
still hasn't happened... Is there any way that I can initiate the defrag and checkdist routines?.. Or is it even necessary?..

---

### Post by sailthesea on 2009-05-10
Am still with my Wubi install of jaunty 
Hasn't freaked out at all yet  And that was on top of a nofrag of windows Just backup in case!

---

### Post by jfloydb on 2009-05-12
it just happened this boot...

---

### Post by SunnyRabbiera on 2009-05-12
You should not have to defrag Ubuntu, EXT the filesystem oif Ubuntu has a low fragmentation rate.
Even with Wubi, unless you gave Ubuntu NTFS.
Wubi just visualizes Ubuntu, and is not an actual install but it should be unharmed if you defrag windows.

---

### Post by prematurebaby on 2009-05-12
Ummmm...All Unix/Linux systems defrag automatically without notice. I don't think its necessary in wubi.

---

### Post by bodhi.zazen on 2009-05-12
> **SunnyRabbiera said:**
> You should not have to defrag Ubuntu, EXT the filesystem oif Ubuntu has a low fragmentation rate.
Even with Wubi, unless you gave Ubuntu NTFS.
Wubi just visualizes Ubuntu, and is not an actual install but it should be unharmed if you defrag windows.

Just to clarify some common musunderstandings about wubi ....

wubi is an Ubuntu installation and is in fact dual booting and not virtualization.

wubi uses the windows boot loader and thus grub is not installed.

wubi installs into a file within windows and is mounted on a loop mount when ubuntu is booted.

---

### Post by SunnyRabbiera on 2009-05-12
> **bodhi.zazen said:**
> Just to clarify some common musunderstandings about wubi ....

wubi is an Ubuntu installation and is in fact dual booting and not virtualization.

wubi uses the windows boot loader and thus grub is not installed.

wubi installs into a file within windows and is mounted on a loop mount when ubuntu is booted.

Ah, I heard it was like a virtual install.
My mistake

---

### Post by bodhi.zazen on 2009-05-12
> **SunnyRabbiera said:**
> Ah, I heard it was like a virtual install.
My mistake

no problem, as I said, wubi is often misunderstood.

---

