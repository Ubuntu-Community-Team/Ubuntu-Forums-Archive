---
title: "Applications with no network"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by cuzz on 2008-11-07
Upgraded to 8.10 from 7.10 on a T61, everything is great and love all the new stuff that works, but I'm having issues with internet access. There a couple of apps that I maintain outside of the of the package manager firefox 32, and eclipse. Both of these have lost the ability to connect to the internet. Firefox 32 is no biggey since I only had that installed because the older 64 bit version didn't support flash, but eclipse I need running. Before you recommend I use the installer for eclipse, that is not an option, power user I need total control.

I'm sure that it is some security issue like appamor or the like. Any ideas what could be denying these apps access to the network?

Thanks,
-Chris.

---

### Post by cuzz on 2008-12-13
This turned out to be an issues with the default installed JVMs. Updated $PATH in .profile to find /user/local/java-'version'/bin before Ubuntu's

---

