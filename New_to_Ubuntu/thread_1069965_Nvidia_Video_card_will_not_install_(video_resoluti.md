---
title: "Nvidia Video card will not install (video resolution issue)"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by David_Distracto on 2009-02-14
I am a complete newb with the Linux and the Ubuntu.  I just installed it this afternoon.  I know a little about computers, but more often than not, I know just enough to get myself into trouble.

Ok here is the problem.  I installed the Ubuntu, and when it loaded up the screen was in 640x400 resolution.  This, of course, is difficult to deal with, so I went to change it.  Only one other resolution was offered in the drop down menu, and that was even smaller.  I noticed a flashing note at the top of the screen that said something about a proprietary driver needing to be installed.  I clicked on it, and it said something about Nvidia Accelerated Graphics Driver (version 173) was proprietary but needed to be installed to get the graphics card to work.   So I downloaded and installed it.  I rebooted, and the resolution was still screwed up.  I went back to the hardware drivers, and there was another option now for the driver Nvidia Accelerated Graphics Driver (version 96).  I tried downloading and installing that, and then rebooting with no success.  I tried searching the forums, but I am having some significant difficulty surfing the web or doing anything in this ridiculously giant resolution.

---

### Post by hyperyoda on 2009-02-14
> **David_Distracto said:**
> I am a complete newb with the Linux and the Ubuntu.  I just installed it this afternoon.  I know a little about computers, but more often than not, I know just enough to get myself into trouble.

Ok here is the problem.  I installed the Ubuntu, and when it loaded up the screen was in 640x400 resolution.  This, of course, is difficult to deal with, so I went to change it.  Only one other resolution was offered in the drop down menu, and that was even smaller.  I noticed a flashing note at the top of the screen that said something about a proprietary driver needing to be installed.  I clicked on it, and it said something about Nvidia Accelerated Graphics Driver (version 173) was proprietary but needed to be installed to get the graphics card to work.   So I downloaded and installed it.  I rebooted, and the resolution was still screwed up.  I went back to the hardware drivers, and there was another option now for the driver Nvidia Accelerated Graphics Driver (version 96).  I tried downloading and installing that, and then rebooting with no success.  I tried searching the forums, but I am having some significant difficulty surfing the web or doing anything in this ridiculously giant resolution.

In the newer versions of Ubuntu support for some older graphics card drivers were dropped. Try burning an Ubuntu 6.06 (Dapper Drake) Live CD and try that. It should be able to do 800x600 and 1024x768 resolutions.

Zach

---

### Post by 2hot6ft2 on 2009-02-14
After installing the drivers go back to
System>Administration>Hardware Drivers
and make sure it's set to Active, if it's not activate it and reboot.
If it is active go to
System>Preferences>Screen Resolution
and set it.

If that doesn't work post the graphics card make and model which can usually be found by running
```
lspci
```
in a terminal
Applications>Accessories>Terminal
and post the results.

---

### Post by David_Distracto on 2009-02-14
I am running a GEForce 5500 with 256 mb that i bought a year or so ago.  It not really that old.  I saw in another thread something about beta drivers.

[http://ubuntuforums.org/showthread.php?t=1068400&highlight=nvidia&page=3](http://ubuntuforums.org/showthread.php?t=1068400&highlight=nvidia&page=3)

I am going to attempt to install these drivers and see what happens.

---

### Post by 4Orbs on 2009-02-14
You gotta find the right driver for your specific card. This is [a helpful place.]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14")

---

