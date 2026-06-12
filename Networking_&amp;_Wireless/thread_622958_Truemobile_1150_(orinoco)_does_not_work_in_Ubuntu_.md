---
title: "Truemobile 1150 (orinoco) does not work in Ubuntu Studio"
date: 2007-11-25
forum: Networking &amp; Wireless
---

### Post by mightysween on 2007-11-25
This might seem similar to other threads out there about the Truemobile 1150 not working, but it is a bit different.

I am using a Dell Truemobile 1150 wireless card (orinoco_cs driver), which I have used in various Linux distros since 2003.

My machine is setup with Win XP Pro, Ubuntu 7.10, and Ubuntu Studio on separate partitions.   The wireless card works fine under Win XP and Ubuntu 7.10 "Gutsy"...as well as the many other distros I've used over the years.   Unfortunately, it does not work with Ubuntu Studio...which simply perplexes me.

Studio uses the 2.6.22-14-rt kernel, while Gusty uses the 2.6.22-14-generic.   

My suspicion is that the final version of Studio was compiled using the Gutsy release candidate kernel -- which did not include the orinoco_cs driver.

The orinoco drivers will not "make" in Studio without re-compiling the kernel.  Compiling a different kernel for studio kind of defeats the purpose I want to use it...

So...does anyone know a way to install the orinoco_cs driver into 2.6.22-14-rt?

I will also file a new bug at launchpad since all of the related ones dealt with this problem during the Feisty to Gutsy and not with Studio.

---

### Post by woodslanding on 2007-12-15
I have the same problem, I think!

I'm very new to linux, but the truemobile does not show up in the network hardware list, where my ethernet and modem do.

Do I need to look for another low latency distro?  Any ideas????

---

