---
title: "CTS protection enabled/disabled filling log"
date: 2008-03-10
forum: Networking &amp; Wireless
---

### Post by wwalkersd on 2008-03-10
I've found some mentions of the following message, but nothing specific to this issue;  On my system, an eMachines T3114 (AMD Sempron 3100+, MSI board, VIA chipset, on-board VIA graphics, Linksys WMP54G v1 wireless card) running Gutsy, my kern.log (which I was looking at in hopes of diagnosing some suspend/hibernate issues) shows the following messages over and over:

Mar 10 13:28:03 upstairs kernel: [  266.676528] wlan0: CTS protection enabled (BSSID=00:11:24:00:d0:5d)
Mar 10 13:28:06 upstairs kernel: [  269.947789] wlan0: CTS protection disabled (BSSID=00:11:24:00:d0:5d)
Mar 10 13:28:33 upstairs kernel: [  296.526835] wlan0: CTS protection enabled (BSSID=00:11:24:00:d0:5d)
Mar 10 13:28:37 upstairs kernel: [  301.433732] wlan0: CTS protection disabled (BSSID=00:11:24:00:d0:5d)
Mar 10 13:28:54 upstairs kernel: [  317.687854] wlan0: CTS protection enabled (BSSID=00:11:24:00:d0:5d)
Mar 10 13:29:08 upstairs kernel: [  331.795176] wlan0: CTS protection disabled (BSSID=00:11:24:00:d0:5d)

"upstairs" is the host name of my computer.

My wireless LAN connection appears to keep working through all of this, but obviously something's going on that's not right.  What do these messages really mean?  How can I make them stop?  Thanks!

---

### Post by angkor on 2008-05-03
Got the same wireless chipset and the same message filling my log. Anyone know what's going on?

I am using the CVS-snapshot rt61 driver.

---

### Post by nmsmith on 2008-05-04
I have the same message filling kern.log (68 MiB) and also syslog (205 MiB)

Surely these files needn't be so big. Don't they start self-truncating after a while?

---

