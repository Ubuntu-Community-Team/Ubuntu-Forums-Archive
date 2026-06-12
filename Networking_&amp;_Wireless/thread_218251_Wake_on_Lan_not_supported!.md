---
title: "Wake on Lan not supported!?"
date: 2006-07-18
forum: Networking &amp; Wireless
---

### Post by ml1710 on 2006-07-18
Hi!
Recently I've been trying to move from Debian Stable (with kernel 2.4) to Ubuntu server.  I have a 3com 905b onboard network adaptor (Dell Gx1 computer), which was able to wake on lan by adding "options 3c59x enable_wol=1" to a /etc/modutils/ file.

So far I've tried everything to get it to work with Ubuntu (which is a great distribution). I've added the same options to a /etc/modprobe.d file, enabled acpi, tried modprobe, ethtool, etc, but it still doesn't work.  Also something to note is that when I upgraded my Debian kernel from 2.4 to 2.6 it didn't work either.  Maybe it isn't passing the module options along.

Does anyone have any ideas?  I have been looking for information for two weeks, and any information would be appreciated!

Thanks!

---

