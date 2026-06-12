---
title: "Short and Bitter - ethtool -K eth0 sg off rx off tx off tso off :("
date: 2007-09-01
forum: Networking &amp; Wireless
---

### Post by emit22 on 2007-09-01
realtek card + Cannot set device tcp segmentation offload settings
Trying to bridge a vmware network from fiesty 7.04 <> red hat
Have the fun issue that seems widespread of zero tcp ability,
minimal pings, and no access to the internet.

Quite sure that the equivalent of this for a realtek card:

ethtool -K ra0 sg off rx off tx off tso off

Will solve the problem,
so hopefully someone can assist.

Thanks a lot.

---

### Post by emit22 on 2007-09-01
Cannot set device rx csum settings: Operation not supported

As well if it is of any help as this is entirely beyond me.  thx again

---

### Post by emit22 on 2007-09-01
Frustrations...
Sorry for the multiple posts, but realtek is garbage or what?

root@ABCBOX:~# ethtool -K ra0 tx off
Cannot set device tx csum settings: Operation not supported
root@ABCBOX:~# ethtool -K ra0 sg off
Cannot set device scatter-gather settings: Operation not supported
root@ABCBOX:~# ethtool -K ra0 tso off
Cannot set device tcp segmentation offload settings: Operation not supported
root@ABCBOX:~# rm ra0?

---

