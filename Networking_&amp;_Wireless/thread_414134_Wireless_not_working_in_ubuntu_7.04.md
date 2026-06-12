---
title: "Wireless not working in ubuntu 7.04"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by thenamestj on 2007-04-19
Well, for me at least.  Funny thing is, it was able to make it work fine in 6.10 without the need for ndiswrapper.  Anyhoo, It will detect all of the wireless networks in range, including my own.  Yet, it gives me an error when I try to connect.  That, or it will "connect" showing my signal strength in the top left corner, but when i go to check to see if it has an IP address, DNS etc...it says "not available".  I'm pissed.

edit: I'm using a Linksys wusb54g ver. 4

---

### Post by Bad_Byte on 2007-04-19
In the same boat here, wusb54g v1. From the looks of it some one broke something in the linux kernel :mad:. Looks like the only solution for now is to downgrade the kernel untill a new driver gets released which looks like could be a loooong time to wait ](*,) .

---

### Post by olskar on 2007-04-19
Is your problem something ike the problem I have described here?

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106157](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106157)

If so you should confirm it.

---

