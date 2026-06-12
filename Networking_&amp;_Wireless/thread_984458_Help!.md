---
title: "Help!"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by kikizing3 on 2008-11-16
I am having a problem.
I am running Ubuntu 8.10 off of a 4 GB flash drive, and I am running out of space so I would like to have my firefox downloads folder to be on a network drive. But I can't seem to get it to save in there. I have tried it with DownThemAll and just the normal Firefox preferences window but the network drive doesn't show up in the "Open" window.

Could I mount the network drive in /media?

---

### Post by xen-uno on 2008-11-16
Probably because by default, the network drive (non ext3?) is read only. Do a forum search on mounting NTFS partitions (should be a similar procedure for a network drive), which involves editing fstab (involves changing **ro** to **rw** for the particular drive ... if network drives are handled that way). As for FireFox, you could run FF's profile manager (in windows it's **firefox -p** ... for Linux I'm not sure) then create a new profile on the network drive, then copy your current profile contents over to it.

---

