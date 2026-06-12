---
title: "problems with ipw3945 and ieee80211"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by av3nger on 2007-06-26
couple of days ago i've configured a new kernel (2.6.21.5) on my notebook (asus f3jr). and my wireless adapter dissapeared. so after a quick search i've found out that i had to install ipw3945 drivers from [http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)
i've followed all the instructions, installed ieee80211 substem. but when i try to install ipw3945 i get an error:
```
ERROR: A compatible subsystem was not found in the following path[s]:

        /lib/modules/2.6.17-11-generic      /lib/modules/2.6.17-11-generic/build

You need to install the ieee80211 subsystem from http://ieee80211.sf.net
and point this build to the location where you installed those sources, eg.:

        % make IEEE80211_INC=/usr/src/ieee80211/

or use the 'make patch_kernel' within the ieee80211 subsystem to patch your
kernel sources.
```

how can i fix this?

---

