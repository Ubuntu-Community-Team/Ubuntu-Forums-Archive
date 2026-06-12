---
title: "Kismet + WG511T"
date: 2007-12-03
forum: Networking &amp; Wireless
---

### Post by JO68 on 2007-12-03
So, after fighting with kismet for a couple days I found that it will not work with my broadcom chip.  Tonight I purchased a netgear wireless card(WG511T) because from what I read both kismet and airsnort/aircrack should work with it.  I am still getting the same error that I had been getting when I had the broadcom chip enabled

jordan@Jordan-Ubuntu:/usr/local/etc$ sudo kismet
Launching kismet_server: /usr/local/bin/kismet_server
Will drop privs to jordan (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
FATAL: Support for capture source type 'madwifi_ag' was not built.  Check the output from 'configure' for more information about why it might not have been compiled in.
Done.


Of course I was not using the source type madwifi_ag with my broadcom chip but I cannot get the right source type in there for it to get past.  

Thanks for helping ,
- Still a linux newbie -
JO

---

