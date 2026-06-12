---
title: "[SOLVED] No network with latest kernel"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by benbelly on 2008-06-07
I've been trying for a few days to get my network working after upgrading to hardy.  Nothing was working for me.  On a whim, I booted into the 2.6.22-14-generic kernel this morning (recovery mode - X freezes in non-recov mode), and the network came up fine.  No problems.  I booted into the recovery console for the latest kernel (2.6.24-17-generic), and networking was still not working.

  So, somewhere between 2.6.22-14 and 2.6.24-17, my network card stopped working.  ethtool reports the forcedeth driver version 0.60 for the older kernel, and version 0.61 for the newer version.  Would it make sense to roll that driver back a version?  Any tips on how to do that?

Thanks,
-Ben

---

### Post by benbelly on 2008-06-07
Bump.  Ok, I've done some poking around.  I figure I HAVE to have the older version of the forcedeth driver somewhere, but I don't know how to force it to be loaded.

Can anyone point me to a how-to or something so I can try to older driver, or  am I going down the wrong path altogether?

-Ben

---

### Post by benbelly on 2008-06-10
Well, this is rather embarrassing. My BIOS was a rev out of date. I thought I had the latest. Turns out that the new version fixed some network stuff. :oops:

So, if any of you have a ASUS P5N32-E SLI, make sure you have the latest BIOS.

---

