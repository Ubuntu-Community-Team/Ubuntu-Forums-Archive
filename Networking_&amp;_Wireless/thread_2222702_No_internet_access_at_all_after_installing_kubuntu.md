---
title: "No internet access at all after installing kubuntu-desktop on normal 14.04"
date: 2014-05-07
forum: Networking &amp; Wireless
---

### Post by Thimoteus on 2014-05-07
Before I installed kubuntu-desktop I decided to make a TimeShift snapshot so I would be able to restore my system in case anything went wrong. Well, something went wrong and restoring the snapshot does not help.

I logged into the kubuntu desktop but it wasn't able to connect to the internet. So I restored the snapshot to before the install, but my internet problem persisted. It won't connect on wireless (but it can see wireless network names) or ethernet.

I also logged into my elementary OS (Luna) dual-boot, and internet access wasn't working there either.

Finally I tried a 14.04 live USB session with the same results.

It always seems to fail on "getting IP configuration".

EDIT: Solved. Turned out a simple router restart was all it took. Router was unable to allocate new IP addresses, so eventually every device on the network would have had the same problem but mine was the unlucky first.

---

