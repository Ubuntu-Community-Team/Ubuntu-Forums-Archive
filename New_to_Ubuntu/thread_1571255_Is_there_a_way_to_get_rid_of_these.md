---
title: "Is there a way to get rid of these?"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by BugBuster on 2010-09-09
I want to get rid of these detailed names as this causes the drop-down menu to be very wide.

[IMG]http://img251.imageshack.us/img251/9166/imagesnu.jpg[/IMG]

By the way this is a snapshot from the Network-Manager drop down list in Ubuntu Lucid.

---

### Post by QLee on 2010-09-09
Right click on the Network Manager icon, choose edit connections, change the name of whichever connections you choose to whatever you want them to be.

---

### Post by BugBuster on 2010-09-09
> **QLee said:**
> Right click on the Network Manager icon, choose edit connections, change the name of whichever connections you choose to whatever you want them to be.

Well..it may not be clear in this snapshot..but I have set the names of the networks set as per my liking(the ones that are blanked out)

What I wish to get rid of is the detailed names of the ethernet cards that appear against the interfaces by default.These are the exact same entries that come up when I run,
```
$lspci | grep Ethernet
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
03:02.0 Ethernet controller: D-Link System Inc DGE-530T Gigabit Ethernet Adapter (rev 11) (rev 11)
```

---

