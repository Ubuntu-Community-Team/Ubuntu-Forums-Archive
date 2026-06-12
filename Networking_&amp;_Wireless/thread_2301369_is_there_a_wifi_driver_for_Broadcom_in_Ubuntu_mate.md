---
title: "is there a wifi driver for Broadcom in Ubuntu mate"
date: 2015-11-01
forum: Networking &amp; Wireless
---

### Post by dellboy56 on 2015-11-01
Hello guys does anyone know if there is a wifi driver for Broadcom bcm4322 because I might want to try it out on my MacBook but I'm a bit sketchy if no one knows otherwise I wouldn't care because I like mate and I would love to use it on my mac

---

### Post by Bucky Ball on 2015-11-02
*Thread moved to **Networking & Wireless**.*

Yes. PC or Mac, doubt that makes a difference in this instance.

> b43 driver (Open-source)

For Chip ID BCM 4306 (rev 03), 4309, 4311, 4312, 4318, 4322, 4331, 43224 and 43225.

The b43 infrastructure is composed of two parts. The first is the firmware-b43-installer package. This is simply a script to extract and install the b43 driver firmware, maintained by the Ubuntu community. The second is the b43 driver, maintained upstream by the Linux kernel community. Instructions to install the package may be found below. 

... from [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx"). Mate/Ubuntu, same repos. If it doesn't work out of the box it won't be that difficult to get it working. Are you using Ubuntu now and did it work out of the box? Expect similar in Mate. 

Best to search prior to posting. Good luck.

---

### Post by dellboy56 on 2015-11-02
Would you know by any chance how I could obtain the files could I get them from my other laptop and put them on a thumb drive and install?

---

### Post by Hadaka on 2015-11-02
Hi, i gave you instructions how to do this on your other open
thread.
[http://ubuntuforums.org/showthread.php?t=2300751](http://ubuntuforums.org/showthread.php?t=2300751)
please do not post multiple threads for the same problem
thanks.

---

### Post by Bucky Ball on 2015-11-02
*Thread closed.*

Thanks Hadaka. Refer to the thread linked by Hadaka where you are already getting plenty of help. Whatever applies there will apply in Mate.

---

