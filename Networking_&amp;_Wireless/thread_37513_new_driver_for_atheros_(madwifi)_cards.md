---
title: "new driver for atheros (madwifi) cards"
date: 2005-05-27
forum: Networking &amp; Wireless
---

### Post by opensensesolutions on 2005-05-27
After seeing several posts about the newer D-Link G520 cards (hardware revision b, etc) and other Atheros (madwifi) based cards not working out of the box with Ubuntu, and having the same problem myself, I came up with a solution:

The newer revision of those cards needs an updated driver which is not in the current ubuntu restricted modules package.  I rebuilt that package and it is available by adding
 deb [http://ubuntupc.com/ubuntu](http://ubuntupc.com/ubuntu) public-sources/
to your /etc/apt/sources.list file and doing an update.
Only the madwifi drivers are changed, the rest of that restricted modules package (nvidia, etc.) remains the same.

Note: the madwifi drivers are experimental, and I have seen kernel freezes  trying to ifdown and ifup the card multiple times with encryption turned on, but they do work well after you get everything set up.

If you'd rather just buy a linux computer with all the the hardware and software preconfigured and working, check out my site at [http://ubuntupc.com/products.html](http://ubuntupc.com/products.html)

---

### Post by jagoode on 2005-05-27
[QUOTE=opensensesolutions]
The newer revision of those cards needs an updated driver which is not in the current ubuntu restricted modules package.  I rebuilt that package and it is available by adding
 deb [http://ubuntupc.com/ubuntu](http://ubuntupc.com/ubuntu) public-sources/
to your /etc/apt/sources.list file and doing an update.
Only the madwifi drivers are changed, the rest of that restricted modules package (nvidia, etc.) remains the same.
[/QUOTE]


Added this line to the end of /etc/apt/sources.list, then did System->Ubuntu Update Manager.

Is there anything else I need to do? I'm still not able to get a net connection.  Bear in mind I'm a newb when you give instructions.  I'm reading everything I can to try to get up to speed on Linux and end dependancy on Windows, but getting my wireless card working is a make or break issue.

---

