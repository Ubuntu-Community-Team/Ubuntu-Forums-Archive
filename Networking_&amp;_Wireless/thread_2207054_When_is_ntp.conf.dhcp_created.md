---
title: "When is ntp.conf.dhcp created?"
date: 2014-02-21
forum: Networking &amp; Wireless
---

### Post by raubvogel on 2014-02-21
Stupid question: from what I understood by reading [https://bugs.launchpad.net/ubuntu/+source/ntp/+bug/374896](https://bugs.launchpad.net/ubuntu/+source/ntp/+bug/374896), among other things, if you configure the interface to do dhcp boot and the dhcp server provide ntp info, /etc/dhcp/dhclient.conf causes ntp.conf.dhcp to be created. Is that so? Because I can't find the file.

I did notice if I create (using touch) /etc/ntp.conf.dhcp, I get the expected behaviour (ntp servers are pulled from dhcp)

---

