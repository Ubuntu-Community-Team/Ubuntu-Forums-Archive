---
title: "network not working with vmware"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by theolster on 2007-03-20
I'm totally new to vmware, but I'd really like to get it working so I can install a zimbra server without having to worry about messing with my existing LAMP install.

But, I can't get the internet to work properly, it doesn't matter if the network is set up using dhcp or static, I still get the same problems...

For example if I try to download a large file I get the following errors:> $ wget [http://kent.dl.sourceforge.net/sourceforge/zimbra/zcs-4.5.3_GA_733.UBUNTU6.tgz](http://kent.dl.sourceforge.net/sourceforge/zimbra/zcs-4.5.3_GA_733.UBUNTU6.tgz)
--23:58:52--  [http://kent.dl.sourceforge.net/sourceforge/zimbra/zcs-4.5.3_GA_733.UBUNTU6.tgz](http://kent.dl.sourceforge.net/sourceforge/zimbra/zcs-4.5.3_GA_733.UBUNTU6.tgz)
           => `zcs-4.5.3_GA_733.UBUNTU6.tgz.1'
Resolving kent.dl.sourceforge.net... 212.219.56.167
Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 216,559,468 (207M) [application/x-tar]

 0% [                                     ] 2,592         --.--K/s             

23:58:52 (304.90 KB/s) - Read error at byte 2592/216559468 (Connection reset by peer). Retrying.

--23:58:53--  [http://kent.dl.sourceforge.net/sourceforge/zimbra/zcs-4.5.3_GA_733.UBUNTU6.tgz](http://kent.dl.sourceforge.net/sourceforge/zimbra/zcs-4.5.3_GA_733.UBUNTU6.tgz)
  (try: 2) => `zcs-4.5.3_GA_733.UBUNTU6.tgz.1'
Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 216,559,468 (207M), 216,556,876 (207M) remaining [application/x-tar]

 0% [                                     ] 5,124         --.--K/s             

23:58:53 (304.63 KB/s) - Read error at byte 5124/216559468 (Connection reset by peer). Retrying.

--23:58:55--  [http://kent.dl.sourceforge.net/sourceforge/zimbra/zcs-4.5.3_GA_733.UBUNTU6.tgz](http://kent.dl.sourceforge.net/sourceforge/zimbra/zcs-4.5.3_GA_733.UBUNTU6.tgz)
  (try: 3) => `zcs-4.5.3_GA_733.UBUNTU6.tgz.1'
Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 216,559,468 (207M), 216,554,344 (207M) remaining [application/x-tar]

 0% [                                     ] 7,656         --.--K/s             

23:58:55 (274.92 KB/s) - Read error at byte 7656/216559468 (Connection reset by peer). Retrying.

--23:58:58--  [http://kent.dl.sourceforge.net/sourceforge/zimbra/zcs-4.5.3_GA_733.UBUNTU6.tgz](http://kent.dl.sourceforge.net/sourceforge/zimbra/zcs-4.5.3_GA_733.UBUNTU6.tgz)
  (try: 4) => `zcs-4.5.3_GA_733.UBUNTU6.tgz.1'
Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 216,559,468 (207M), 216,551,812 (207M) remaining [application/x-tar]

 0% [                                     ] 10,188        --.--K/s             

23:58:58 (384.73 KB/s) - Read error at byte 10188/216559468 (Connection reset by peer). Retrying.
It seems that some data is being transferred, and I can ssh through to the server ok, but other than that :-(

Does anyone have any idea whats going on here?

---

### Post by dmizer on 2007-03-21
what vmware package are you using?  if you're just using vmware player, you'll have a difficult time getting networking to function.  you're best bet is to download and install vmware server (it's now free of charge with registration).  then you can switch between different types of networking connection for optimum server functionality.

if you're using vmware server already, i think you're best bet is to take the issue up with the vmware people.

---

