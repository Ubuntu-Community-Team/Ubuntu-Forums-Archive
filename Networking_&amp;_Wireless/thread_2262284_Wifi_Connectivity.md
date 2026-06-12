---
title: "Wifi Connectivity"
date: 2015-01-24
forum: Networking &amp; Wireless
---

### Post by Bob_Henry on 2015-01-24
I'm using 14.10 on an old Compaq laptop.  The Broadcom 4311 is recognised but will not turn on.  I know it is good because it works with windows.  I installed the drivers along with the ndis wrapper but no go as getting it to turn on.  The on/off button is being ignored completely.

---

### Post by coffeecat on 2015-01-24
Welcome to the forum!

Why are you trying to use ndiswrapper? Were you following an old howto you found on the net somewhere? You shouldn't need ndiswrapper for the Broadcom 4311 card. Have a look at this sticky:

[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

If you have identified your card correctly, all you need do is to install the firmware-b43-installer package using a wired connection to get internet connectivity while you do so. However, the installed ndiswrapper may interfere, so you would need to uninstall it. If you need help with doing that, post back describing how you installed ndiswrapper and someone else will be able to help.

If you are unable to connect your Ubuntu system with a wired internet connection, post back, and someone should be able to help.

---

