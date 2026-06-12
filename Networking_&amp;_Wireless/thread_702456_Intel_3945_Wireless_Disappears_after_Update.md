---
title: "Intel 3945 Wireless Disappears after Update"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by aseneca on 2008-02-20
My system is a compaq v3608tx laptop and I am currently using Ubuntu 7.10.

Today, I processed an update that included a kernel update and a intel-video update.  After which, ubuntu could no longer see my wireless card.  I'm assuming this is a problem with the update so I've attempted to force version and rollback the drivers.

I've check the system information menu options and even tried lspci | grep 3945 to no resolution.  Looking through my error logs when I shutdown my system last I can see that nm_device_802_11_wireless_get_mode() reports that it can no longer find eth1 (my wireless connection)

So hopefully the rollback works if not I'm stuck reinstalling.  And, I hope this helps anyone reading with similar configuration from not installing the latest update until it is fixed!

Best of Luck

AS

---

