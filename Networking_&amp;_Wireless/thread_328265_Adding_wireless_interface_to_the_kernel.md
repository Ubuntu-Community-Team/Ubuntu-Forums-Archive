---
title: "Adding wireless interface to the kernel?"
date: 2006-12-30
forum: Networking &amp; Wireless
---

### Post by lenticular on 2006-12-30
In pursuing a fix to a problem several months ago, I followed instructions to recompile a new kernel.  At the end of the instructions was a note like "oh yes, this does not include wireless."   That will teach me to read all the way to the end before doing the cut-n-paste thing.

Right now, my kernel is 2.6.17, and it sees no wireless interface:

$ ifconfig eth1
eth1: error fetching interface information: Device not found

When I really do need wireless, I boot to an older kernel.

Can anyone point me to howto that will help me recompile and add wireless, please?

Thanks,
  John

---

