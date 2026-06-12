---
title: "Cannot connect to network in 7.10."
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by Tybee on 2007-10-04
I realize this is still beta, however so close to release in the next couple of weeks I seek answers. Running Gutsy Gibbon 7.10. Computer configuration does not matter. Network is built-in Marvell Yukon Gigabit. Prior Ubuntu versions had absolutely zero issues using my network.

Network configuration is unchanged between then and now. Wired network.

Fresh, totally clean install of Gutsy.

Network configuration shows nothing but 0.0.0.0. It defaults to roaming mode. Changing it to DHCP or otherwise won't work. Disconnecting/reconnecting everything won't work. It detects that the network cable has been unplugged and even goes through the cute little whirl animation when plugged back in, however it refuses to obtain an IP address and will not connect to the local network.

How can I fix this?

---

### Post by noob12 on 2007-10-04
You may want to file a bug on launchpad.

What is the device id of your wired ethernet controller?  (Run **lspci -nnvv** and find out).

What driver has claimed the device? (Run **sudo lshw -C network** and look at the configuration line).

---

