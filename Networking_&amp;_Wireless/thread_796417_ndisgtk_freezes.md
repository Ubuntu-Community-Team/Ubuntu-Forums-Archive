---
title: "ndisgtk freezes"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by gyzer on 2008-05-16
I was messing around with my wireless settings and messed up my wireless connection. I removed my windows wireless drivers from ndisgtk, but then when I go to set everything back up in ndisgtk the program either freezes right when I start it up, or it freezes and becomes unresponsive when I go to add the .inf file. Is there anything I can do to solve this problem? Is there a way to remove ndisgtk and re-install it?

I have tried just using ndiswrapper in the terminal, and I can get it to install the driver and recognize that the hardware is present, but in my network connection manager it doesn't show that I have a wireless device.

---

### Post by Ayuthia on 2008-05-16
> **gyzer said:**
> I was messing around with my wireless settings and messed up my wireless connection. I removed my windows wireless drivers from ndisgtk, but then when I go to set everything back up in ndisgtk the program either freezes right when I start it up, or it freezes and becomes unresponsive when I go to add the .inf file. Is there anything I can do to solve this problem? Is there a way to remove ndisgtk and re-install it?

I have tried just using ndiswrapper in the terminal, and I can get it to install the driver and recognize that the hardware is present, but in my network connection manager it doesn't show that I have a wireless device.
From the terminal, what does lshw -C network show?  Does it have ndiswrapper as the driver?

---

### Post by gyzer on 2008-05-16
This problem might be bigger then I think. After booting up, after less then 10-20min, things become unresponsive. I go to open the terminal, it acts like its loading and then it disappears. Next I'll go to the shutdown menu, and that does the same and it doesn't open up its window. 

Concerning the wireless issue, lsusb when I first boot up doesn't show my usb wireless network adapter. But strangely its LED is flashing fairly quickly and steadily. If I unplug it and then replug it in it does get detected by lsusb, but even with the windows drivers installed in ndisgtk it still says there is no hardware present.

Is there anyway to fix these problems with some sort of repair program or procedure?

---

### Post by Ayuthia on 2008-05-16
> **gyzer said:**
> This problem might be bigger then I think. After booting up, after less then 10-20min, things become unresponsive. I go to open the terminal, it acts like its loading and then it disappears. Next I'll go to the shutdown menu, and that does the same and it doesn't open up its window. 

Concerning the wireless issue, lsusb when I first boot up doesn't show my usb wireless network adapter. But strangely its LED is flashing fairly quickly and steadily. If I unplug it and then replug it in it does get detected by lsusb, but even with the windows drivers installed in ndisgtk it still says there is no hardware present.

Is there anyway to fix these problems with some sort of repair program or procedure?

Is there still a driver installed for NDISwrapper?  If so, remove it for now.  It sounds like you do not have the right driver.  You might want to blacklist ndiswrapper (in /etc/modprobe.d/blacklist) for now just to see if it is ndiswrapper is causing this.

---

### Post by gyzer on 2008-05-17
The problem is fixed now.

This was a strange one. I've got two of these USB wireless network adapters, they are D-Link DWA-130 802.11N's. One is on my Ubuntu box, the other is on my window's box. So I decided to switch them, to see if the one on my Ubuntu box was bad, and low and behold the one that was on my window's box works perfectly with my Ubuntu box, it was detected just fine at start up, and the "broken" one that originally was on my ubuntu box is now on my windows box working perfectly as well.

I guess the problems I was having with the programs freezing and becoming unresponsive had something to do with the system not detecting, or trying to detect the usb network adapter.

Thank you all for your help and insight.

---

