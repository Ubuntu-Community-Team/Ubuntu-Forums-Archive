---
title: "Netgear WG111T driver causes ubuntu to crash."
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by Barrucadu on 2007-05-13
I followed [this tutorial](https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111) to get my netgear wg111t dongle installed. I had to download the drivers from the netgear website though because the one linked to by the tutorial didn't detect the dongle.
I installed the drivers, everything working perfectly. Reboot, and it freezes half-way through booting. So I removed the dongle and rebooted again. Started up fine, plugged the dongle in, and ubuntu freezes again.
After experimenting, it is "athfmwdl.inf" that is causing this to happen. Any ideas, or commands I could run?

After checking on another computer, ubuntu does connect to my network, but pinging it results in a timeout.

---

