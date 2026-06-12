---
title: "rmmod ndiswrapper hangs"
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by Tyr_7BE on 2008-01-29
Hey All

Hope someone can provide some insight here, as this is the only remaining issue between me and getting Suspend up and running on my Dell Dimension running Gutsy.

If I drop down to a terminal, and type 'rmmod ndiswrapper' or 'modprobe -r ndiswrapper', the command just hangs.  I've left it for 10 minutes, it's still hung.  If I ctl+c it, and type 'lsmod | grep ndis', I see ndiswrapper is still present.  But wireless no longer functions, and I have to reboot to get it back.

I've removed ndiswrapper from my modules list, so it's not mounted at boot.  At boot, if I immeditely type 'modprobe ndiswrapper' followed by 'modprobe -r ndiswrapper', I get the same behaviour.  So it's something that happens immediately upon modprobing the driver.

I've seen this problem all over the net, but nobody seems to have any answers.  Anyone have any ideas?

Thanks.

Gutsy Gibbon, default kernel.  I installed ndiswrapper myself, and manually blacklisted the open source prism54 wireless drivers that weren't working too well.

---

### Post by Tyr_7BE on 2008-01-29
Nobody?

---

