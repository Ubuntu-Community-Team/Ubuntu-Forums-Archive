---
title: "&quot;Starting NFS Kernel Daemon&quot; hanging for MINUTES"
date: 2007-12-13
forum: Networking &amp; Wireless
---

### Post by 24track on 2007-12-13
I tried to create a bridge between my two network cards (wireless Aironet 340) and an ancient Intel ethernet card following the directions on one of the posts here. 

I didn't succeed in doing that, but I did succeed in making my system hang for about 5 minutes on startup at the following point in the boot:

Starting NFS Kernel Daemon...

There is an error message that flashes after that, but I've not been able to copy it down before it disappears and the system continues on to the boot.

I should mention that before I get any text, I am about 7/8's of the way through the boot up process according to the Ubuntu splash screen status bar.

My question is thus:

How do I reconfigure the offending packages that I've modified (IP tables, network setup, etc...) in a way that will allow me to return the system to it's pre-modified state?

This is a dual boot system (XP though I hardly ever use it) and I am able to create a network bridge there.

Sorry for the somewhat disjointed nature of this post!

Best -
Rich

---

### Post by Alien.col on 2008-03-12
I'm having this same problem, where you able to fix it. I ended up uninstalling nfs-kernel-server and nfs-common. Long boot is gone but now i have no mouse....

use this command to uninstall sudo apt-get remove nfs-kernel-server nfs-common

---

