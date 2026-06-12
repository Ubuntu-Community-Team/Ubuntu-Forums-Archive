---
title: "Multiple Ubuntu 8.10 installations?"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by dspisak on 2008-12-27
Hello.  I successfully split my XP partition into two partitions and loaded 8.10-amd64 onto the new partition.  There were some adventures getting Flash, Citrix ICA Client, and the printer on the print server running but all is well. :) However, just after POST the GRUB boot-loader appears and gives me these options:

Ubuntu 8.10, kernel 2.6.27-9-generic
Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
Ubuntu 8.10, kernel 2.6.27-7-generic
Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
Ubuntu 8.10, memtest86+
Other operating systems:
Microsoft Windows XP Professional

Please explain why two kernels, -9 and -7, would be listed.  Can I use a GRUB editor to hide the -7 information?  TIA.

Dan

---

### Post by thunk77 on 2008-12-27
After a new kernel is installed, the system keeps the old one(s) as a safety measure. For example if you have some problems with the new kernel (e.g. some hardware suddenly stopped working), you can boot safely in the old one.
However if you want to remove the older kernel you can do so using Synaptic. Just search for the version you want to remove.

---

### Post by dspisak on 2008-12-27
> **thunk77 said:**
> After a new kernel is installed, the system keeps the old one(s) as a safety measure. 

<snip>



Good idea!  Thank you for your reply.

---

### Post by hyper_ch on 2008-12-28
well, in an older release from one kernel to another update my wifi stopped... so it was good the old one was still there :) If you have more than two kernels you could remove older ones if you have no problems :)

---

