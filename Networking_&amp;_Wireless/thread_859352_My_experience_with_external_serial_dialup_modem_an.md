---
title: "My experience with external serial dialup modem and Ubuntu"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by wpshooter on 2008-07-14
I had seen in various threads on the forums that contended that MOST all external serial port dialup modems would work properly with Ubuntu.  And that they did not require any software drivers because they had their own controller to do the processing and that they were unlike Winmodems in that regard.

I just wanted to report that that was not the experience with the one that I obtained for trying to setup dialup on a Ubuntu machine.

I obtained a Trendnet model TFM-560X and after I hooked it up to the computer, it would dial and connect to the ISP just fine every time.  However, the connection would always be dropped/lost in a matter of a few minutes.  And yes, I had the idle timer in Gnome-ppp set to disable.

Perhaps, this was just an isolated defect in just this particular unit that I purchased.

And to go on with the story, I then borrowed a used internal PCI dialup modem from another machine.  I had a VERY difficult time of finding the Ubuntu drivers for this modem but I did finally find the correct driver.

When I got this internal PCI modem setup and configured it dials up every time and does NOT subsequently lose the connection like the external serial modem did.

Maybe just an isolated occurence but I think I will stick with an internal PCI modem from now on as long as I can find one on which the proper Linux drivers can be found for.

Thanks.

---

### Post by lavinog on 2008-07-14
With many dialup modems there is an AT code you can use to have the modem report why the connection dropped.

Some modems handle line noise better than others.

---

