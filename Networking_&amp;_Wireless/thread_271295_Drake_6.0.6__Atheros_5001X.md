---
title: "Drake 6.0.6 / Atheros 5001X"
date: 2006-10-04
forum: Networking &amp; Wireless
---

### Post by rkitain on 2006-10-04
I've installed Dapper Drake 6.0.6 release.
I have a Toshiba laptop with a built in wireless card - 
Atheros 5001X  (Atheros chip set).
I do have the drivers:
ar5211.sys net 5211.inf

Newbie questions:

1. without doing anything after the install of ubuntu, I do
   (as root):
   lspci
   but I don't see my wireless device listed.
   Should I?
2. Under /lib/modules/2.6.15-23-386/
   I see madwifi/  and madwifi-ng/ directories
   In those directories are *.ko files.
   Does this mean that madwifi is included with Dapper Drake
   release?
   Should I be able to use the existing madwifi to get
   wireless working?

I've tried driverloader without success.  
Should ndiswrapper work?

Can someone point me to some specific instructions for the
card/chip set I have?

Thanks, Roger.

---

