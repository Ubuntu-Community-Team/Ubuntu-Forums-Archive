---
title: "Get SAN adapter current traffic speed from /proc"
date: 2015-02-23
forum: Networking &amp; Wireless
---

### Post by peter180 on 2015-02-23
I'm interested is there any similar way like /proc/net file to get SAN adapter current speed? I would like to get current speed values from text file.

---

### Post by tgalati4 on 2015-02-23
What is the model of the SAN?  What is the operating system on it?

There are many open source monitoring tools to gather statistics from a SAN.  Pick one, install it and start monitoring.

Slides and video should be up in a few days from this talk:  [https://www.socallinuxexpo.org/scale/13x/presentations/open-source-monitoring-landscape](https://www.socallinuxexpo.org/scale/13x/presentations/open-source-monitoring-landscape)

Install *icinga2* and point it to your SAN.  [https://www.icinga.org/icinga/icinga-2/](https://www.icinga.org/icinga/icinga-2/)

---

