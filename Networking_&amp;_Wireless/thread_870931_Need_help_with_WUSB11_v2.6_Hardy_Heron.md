---
title: "Need help with WUSB11 v2.6 Hardy Heron"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by robertj20112 on 2008-07-26
I'm trying to get my Linksys WUSB11 v2.6 Wireless Adapter to work.  The hardware will detect the available networks when I run iwlist scan, but I cannot get the device recognized in Network Manager or in Network Tools.  Installed windows driver using ndiswrapper according to this link:  [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)  and it showed as installed when I ran the ndiswrapper -l command.  Verified ndiswrapper was installed by checking dmesg, then followed the rest of the steps at the above link through the reboot.  But when I run ifconfig after the reboot, wlan0 still shows, and running lshw -C Network does not show the newly-installed driver at wlan0.  Please help!

P.S.  I should also say that Network Tools will not let me configure either the wlan0 or the wlan0:avahi devices, saying that neither of them exist.

---

### Post by robertj20112 on 2008-07-26
> **robertj20112 said:**
> I'm trying to get my Linksys WUSB11 v2.6 Wireless Adapter to work.  The hardware will detect the available networks when I run iwlist scan, but I cannot get the device recognized in Network Manager or in Network Tools.  Installed windows driver using ndiswrapper according to this link:  [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)  and it showed as installed when I ran the ndiswrapper -l command.  Verified ndiswrapper was installed by checking dmesg, then followed the rest of the steps at the above link through the reboot.  But when I run ifconfig after the reboot, wlan0 still shows, and running lshw -C Network does not show the newly-installed driver at wlan0.  Please help!

P.S.  I should also say that Network Tools will not let me configure either the wlan0 or the wlan0:avahi devices, saying that neither of them exist.

Further results:

I was able to force the wireless device to use the driver installed by ndiswrapper by blacklisting the existing driver "at76_usb".  However, after rebooting, the wireless interface with this driver shows up with a logical name "wlan1" and no wireless networks show up in Wicd Manager (which I installed since the previous post.)  Clearly, I need help -- please!

---

### Post by robertj20112 on 2008-07-27
Stumbled into my own solution.  Reloaded Hardy Heron (3rd install, all as dual-boot with XP) after making sure XP was working with the WUSB11v2.6.  Did NOT install ndiswrapper, did NOT install XP drivers, but used the driver installed by Ubuntu this time.  Was able to ping router but not any internet URL.  Firefox would not find internet URL.  Forced Firefox onto internet using Google IP address, which seemed to open the floodgates.  Now have full internet access.  Hope I never have to do that again!

---

