---
title: "update-initramfs killed my networking"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by sojyujai on 2008-08-11
I've been trying to set up a HTPC and while trying to install lirc drivers for my remote control I somehow killed all the networking on the computer.

I previously had installed madwifi to get my dlink dwa-556 wifi card working and switched to the wicd network manager (the default network-manager was removed) - all according to the instructions on [**this thread**]("http://ubuntuforums.org/showthread.php?t=718244").  I had it all working properly after this.

Later I started the installation of lirc by following the how-to on [**this page**]("http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with-lirc.html").  

It was during Step 3 (Prevent usbhid from controlling the iMON) that I ran into trouble.  After I edited /etc/modprobe.d/usbhid, ran update-initramfs -u and rebooted I lost all networking.

I'm not sure exactly what happened but I'm guessing it's because I had previously removed network-manager and replaced it with wicd that networking somehow was removed/damaged during boot-up after I ran update-initramfs.

After ifconfig all I'm seeing now is a lo device when previously I saw an eth0, eth1 and ath0 and lo (I have two ethernet ports and the wifi port on the dwa-556

If anyone has any suggestions how to get my networking back I'd appreciate it!

---

