---
title: "Madwifi 0.9.2 released"
date: 2006-07-27
forum: Networking &amp; Wireless
---

### Post by Eversmann on 2006-07-27
New version, improved network scan, some bugs fixed:

> We've started to address some of the known issues related to scanning, and
some of them have been fixed in this release. Another area that received
some attention is the build system (again).

MadWifi now supports an enhanced iwspy feature which allows to define a
signal strength threshold. When the monitored devices reaches the defined
threshold, the driver rises an iwspy event that then can be handled by
userspace tools.

Last but not least: the sample rate algorithm provides statistics via the
/proc file system. You might know this functionality from madwifi-old
where it has been available for some time - now that's finally available
in the new codebase as well.

all the changes and fixes are listed here: [http://madwifi.org/log/trunk?rev=1694&stop_rev=1654](http://madwifi.org/log/trunk?rev=1694&stop_rev=1654)

More details and links for downloading at [www.madwifi.org](www.madwifi.org)

---

