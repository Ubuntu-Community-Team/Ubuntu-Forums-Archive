---
title: "Madwifi-ng: Please enable wireless extensions"
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by spd106 on 2006-07-25
I'm trying to compile the the madwifi-ng module, but all i seem to get is this error during make asking to enable wireless extensions. This is surprising since I am using wireless right now.

Following the wiki guides and the howto posts (which are based on breezy) I've made the -werror change in the Makefile.inc and changed the target gcc to gcc-3.4. I've been trying the latest stable release 0.9.1 and I've also tried the latest unstable from svn.

Why do I seem to be the only one with this problem?

---

### Post by tturrisi on 2006-07-25
why not just use the mad-wifi drivers that are in the linux-restricted-modules package?

---

### Post by spd106 on 2006-07-25
> why not just use the mad-wifi drivers that are in the linux-restricted-modules package?

I just wanted to see if it was any better.

I found the problem was that had the linux-headers-2.6.15-26 package, but not the linux-headers-2.6.15-26-386 package. Also, I needed to use the included gcc-4, rather than gcc-3.4 instead.

---

