---
title: "Error when cloning ubuntu9.04"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by ilanafri on 2009-10-27
I'm using ghost 11.0.1 to clone my MS \ Linux O.S.
I just installed my new **Ubuntu 9.04 64bit** (KDE included) and want to clone it in order
to deploy in on differebt machines with similar hardware.
I clone this Linux as a disk and not as partiotions to a server in the network.
 
The outcome ERROR is a message box when trying to clone the O.S : 
Title - **Linux Problem detected (1978 )**
error - **"...the problem was most probably unmounted cleanly. we rcommend to quit gohst and run fsck on this volume..."**
 
Notes:
- Running **fsck** on "live" OS not helping, the error remains after trying again
- Not happend on the same machine with Ubuntu 8.04 (32 &64)
- Same bad results also when cloning a partiton
 
Any iseas?
 
thanks
ilan

---

### Post by Mark Phelps on 2009-10-27
You talking about Ghost the MS Windows product?  Did you by any chance use Ext4 for installing Ubuntu 9.04? Don't use Ghost, so I don't know, but since the most current version is 12 (I believe), I would expect that version 11 is not able to handle Ext4-formatted filesystems properly.

If you're going to clone Linux installs, why not use Linux utilities instead?  They're free -- and they're known to work.

---

### Post by LewRockwell on 2009-10-27
[http://clonezilla.org/](http://clonezilla.org/)

.

---

### Post by mapes12 on 2009-10-27
> **LewRockwell said:**
> [http://clonezilla.org/](http://clonezilla.org/)

.+1 for Clonezilla

---

