---
title: "IBM T30 (prism 2.5) orinoco woes"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by StFS on 2007-02-04
I used to have debian set up on my laptop (IBM T30) and then I built my own custom kernel and used the hostap driver (downloaded specifically and built by hand). That worked really well but now I have set up Kubuntu (edgy) and tried to use the hostap driver that is bundled with the official kernel package but that doesn't work at all for some reason. So I followed the advice I found in a thread here ([http://ubuntuforums.org/showthread.php?t=288649](http://ubuntuforums.org/showthread.php?t=288649)) to blacklist the hostap and instead use the orinoco drivers).

The orinoco drivers enable me to use KNetworkManager and it scans properly and configures my wireless network card. However, the connection seems very slow and the signal strength seems very low. I'm getting a lot of messages about the NIC being disconnected and then reconnected. Example:
```

Jan 29 11:05:52 phoebe-stfs kernel: [17179640.264000] eth1: New link status: Connected (0001)
Jan 29 11:06:01 phoebe-stfs kernel: [17179649.120000] eth1: New link status: Disconnected (0002)
Jan 29 11:06:03 phoebe-stfs kernel: [17179651.532000] eth1: New link status: Association Failed (0006)
Jan 29 11:23:52 phoebe-stfs kernel: [17180720.452000] eth1: New link status: Connected (0001)
Jan 29 11:24:02 phoebe-stfs kernel: [17180730.024000] eth1: New link status: Disconnected (0002)
Jan 29 11:24:04 phoebe-stfs kernel: [17180732.376000] eth1: New link status: Association Failed (0006)
Jan 29 11:25:11 phoebe-stfs kernel: [17180799.672000] eth1: New link status: Connected (0001)
Jan 29 11:25:55 phoebe-stfs kernel: [17180842.912000] eth1: New link status: Disconnected (0002)
Jan 29 11:25:56 phoebe-stfs kernel: [17180844.816000] eth1: New link status: Association Failed (0006)

```

This pretty much goes on all the time while I'm connected and it can result in failed downloads etc.

If anyone has any ideas about what could be going on (and/or possible fixes), I'd sure appreciate them.

Thanks, Stefan Freyr.

---

