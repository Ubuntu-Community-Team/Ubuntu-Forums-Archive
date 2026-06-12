---
title: "Can't get online after building custom kernel"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by Hitchhiker427 on 2007-05-15
Hello, as the title suggests, I recently built my own custom kernel, and for some reason I can no longer get online.  

To give you a bit of history, I was originally running Edgy Eft with a custom-built kernel version 2.6.19.  Everything here worked fine.  I then upgraded to Feisty Fawn.  After a little bit of work I got everything working here as well.  However, I was unable to boot into any of Feisty's pre-compiled kernels for some unknown reason.  I was, however, able to boot into my custom-built 2.6.19 kernel.  I figured that this was now outdated and I should upgrade my kernel.  

I then built kernel version 2.6.21.1.  While building, I imported my config from my previously-built (and fully working) kernel.  I also checked some of the newly added options regarding networking.  After booting into the newly built kernel (and reinstalling my drivers) I discovered that I couldn't get online any more.  I wasn't sure what wrong, so I went and rebuilt the kernel, but this time, I checked some more options regarding networking.  

Unfortunately, I still can't get online.  I don't really know how to debug this or what could be wrong.  I should also note that I can still boot between my old kernel (2.6.19) and my new kernel (2.6.21.1).  My internet connectivity works fine on the old kernel, but won't work on the new kernel.

I know I'm not providing much information, but frankly, I don't know what to include or how.  Any help on this issue would be greatly appreciated.  Thanks in advance.

---

### Post by Hitchhiker427 on 2007-05-16
After playing with this some more, I've discovered that Ubuntu recognizes my network card, and I'm capable of successfully pinging my router.  I was also able to access my router's configuration through Firefox (however, this took very long to load, which is very unusual).  When I try to load pages in my browser it stays on "connecting" for a long time before finally timing out.

This leads me to believe that my kernel compilation has nothing to do with my connectivity issues.  It seems to me that if Ubuntu properly recognizes my hardware and can connect to my router that it has the proper drivers loaded.

So, what could be the problem?  Why does my older kernel connect flawlessly, but the newer one doesn't work at all?  I have two networking devices, my external card and my integrated card.  Ubuntu successfully recognizes both, but fails to connect with either.  I thought that maybe they were conflicting, but disabling the on-board network card via the BIOS did not solve my problem.

Any ideas?  Thanks.

---

