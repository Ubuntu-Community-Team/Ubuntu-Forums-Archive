---
title: "network manager gnome won't start (automatically)"
date: 2007-04-15
forum: Networking &amp; Wireless
---

### Post by musickeung on 2007-04-15
I am a newbie in Ubuntu.. I have tried to installed LinuxMCE recently, but during the installation my connection stopped (seemed LinuxMCE modified some of my connection settings) and the installation stops at middle.

After a reboot errors came out... "Failed to initialize HAL" and the network-manager-gnome couldn't start, and connection to internet was not possible. After some googling I was able to overcome by 

Recovering the original interface file, and
"sudo /etc/init.d/dbus start" every time after logging in.

But I couldn't find a better fix of this problem.

Any help as to fix this problem / how to completely remove LinuxMCE would be very appreciated.
Thank you!!

---

