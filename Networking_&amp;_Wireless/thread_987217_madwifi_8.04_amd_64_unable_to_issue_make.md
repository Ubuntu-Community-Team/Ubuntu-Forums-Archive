---
title: "madwifi 8.04 amd 64 unable to issue make"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by HaroldM on 2008-11-19
I'm having problems installing madwifi.  I've used it before for an AR5418 and had no problems.  However now I'm getting this message trying to perform the "make" command:  "cd: can't cd to /lib/modules/2.6.24.21-rt/build is missing, please set KERNALPATH.  Stop."

Looking in /lib/modules I find that there is no build directory for  2.6.24.21-rt; but, there is a link to /usr/src/linux-headers-2.6.24.21-generic in the 2.6.24.21--generic directory.

I think this is somehow related to an install of 2.6.24.21-rt.

Any help is appreciated.

---

