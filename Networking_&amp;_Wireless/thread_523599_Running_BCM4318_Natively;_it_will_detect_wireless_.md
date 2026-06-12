---
title: "Running BCM4318 Natively; it will detect wireless networks but won't connect."
date: 2007-08-12
forum: Networking &amp; Wireless
---

### Post by fpruter on 2007-08-12
I an running Ubuntu 7.04 with a bcm4318 and I install bcm43xx-fwcutter as well as bcm43xx-firmware and my computer will detect wireless networks; however, if I try to connect to them it fails.  I even tried connecting to an unsecured wireless network.

Any ideas?

---

### Post by bmartin on 2007-08-12
You shouldn't be using the firmware with the BCM4318 chipset. See [this thread]("http://ubuntuforums.org/showthread.php?t=405990") for installation instructions. I'm using that chipset with ndiswrapper right now; I used to use the firmware, but had many problems related to ACPI.

Reply to that thread if you have any problems. There are many more eyes over there; many people actively monitor that thread.

---

### Post by acadiansteph on 2007-08-13
I have this card, you may want to try this. It worked like a charm on mine: [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)  . I used the one which ask to download the file and then sudo ./ndiswrapper_setup. Good luck:)

---

### Post by kevdog on 2007-08-13
If you need help specifically with ndiswrapper setup and installing the latest from source code (something highly recommended), please post back and I can walk you through it!

---

