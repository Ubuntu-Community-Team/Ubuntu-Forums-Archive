---
title: "Linksys WUSB54Gv4 rt2500usb wireless problem when restarting..."
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by dmg412 on 2007-09-25
I have bought and installed a Linksys WUSB54Gv4 using ndiswrapper and it seems to work fine in fiesty.  The problem is that every time I restart, i have to unplug the adapter and then uninstall the ndiswrapper driver using "sudo ndiswrapper -r rt2500usb".  I then have to turn the computer off, then re plug-in the adapter and re-install the drivers using "sudo ndiswrapper -i rt2500usb" and the wireless device starts working and the network works fine.

I also have a problem switching from one wireless network to a different one.  If I try to switch to a different wireless network, I cannot connect to the new one or the previous one I was connected to and I am forced to restart and re-install the drivers.  This gets annoying after a while.  Does anyone know how to fix this issue or is anyone having the same issue on 7.04...?

---

### Post by uputer on 2007-09-26
Hi, I was reading all posts regarding that Linksys, if it's the adapter, that is.  

I can only use what is intuition when looking at a problem like that.  I could be wrong but it sounds like the wireless connection is being turned off when you restart.  In the wireless configuration, there might be a section in which you can click in some GUI, 'start automatically on startup' or something to that effect.

The other thing to try when it's not working is the commands that turn on the network.   Ifconfig wlan0 down if config wlan0 up and so on.   I'm not up to speed with a lot of the commands but have used the ones for wired i.e. eth0 etc.   I probably explained this incorrectly so search the forums or ask someone who might know (for e.g, someone with a lot of posts regarding networking and wireless).   A script might be useful, too, that turns on the wireless at startup if setting the option of automatically starting at bootup doesn't work.   Having to reinstall at every bootup or restart sounds annoying and should, in theory, be unnecessary.  

Good luck.

---

