---
title: "Intel WiFi Link 5100 on Ubuntu 12.04 Randomly Starts/Stops Working"
date: 2013-09-15
forum: Networking &amp; Wireless
---

### Post by 1n50mn14c on 2013-09-15
I have a Dell Inspiron laptop that has worked perfectly with Ubuntu 12.04 (and 10.04) for the past few years.  A few days ago, though, my wireless started randomly disconnecting, sometimes only for a few seconds and othertimes for several hours.  I believe the issue is with my wireless adapter for the following reasons:

1) The issue began between software updates
2) Everything works normally with a usb wireless adapter
3) The modem is performing normally with the numerous other devices I have on my network (except my wife's new laptop with Windows 8, but that's another story)

I've used Wireshark to see if the card is working at all and that's where it gets interesting.  In managed mode there is absolutely no data being sent or received when my wifi stops working.  However, I can put the card into monitor mode at anytime and see a lot of traffic.  I'm hoping that my wireless adapter isn't starting to fail, but I suspect that might be the case.  Can anyone help me with some command-line-fu to diagnose and possibly fix the problem?

Thanks!

---

### Post by 1n50mn14c on 2013-09-17
Bump

---

