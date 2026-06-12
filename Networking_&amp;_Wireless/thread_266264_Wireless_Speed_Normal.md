---
title: "Wireless Speed Normal?"
date: 2006-09-27
forum: Networking &amp; Wireless
---

### Post by eldy on 2006-09-27
I have a Linksys WRT54G router connected 100 Mbit ethernet port to a desktop machine, one Kubuntu 6.06.1 connected wirelessly at 54 Mbit and another Ubuntu 6.06.1 laptop connected wirelessly at 10 Mbit.

When I transfer files with the desktop machine, the 10 Mbit link only does 360 KB/s maximum and the 54 Mbit only does 2048 KB/s maximum. This is with a good connection to the access point--the laptops are five feet from the access point.

Even with a 30% TCP/IP overhead shouldn't I be enjoying 896 KB/s on the 10 Mbit link and 4838 KB/s on the 54 Mbit link?

Which command outputs should I post for someone to be able to determine if my settings are properly tweaked?

---

### Post by wieman01 on 2006-09-27
You could do the following... Check that your router enables both 11 & 54 MBit transfer rate. Apparently there is a problem in Linux whenever the bit-rates don't match. Results in serious performance issues. Seen it a couple of times.

---

