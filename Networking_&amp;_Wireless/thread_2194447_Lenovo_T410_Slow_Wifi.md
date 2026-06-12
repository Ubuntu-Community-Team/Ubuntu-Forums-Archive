---
title: "Lenovo T410: Slow Wifi"
date: 2013-12-18
forum: Networking &amp; Wireless
---

### Post by jolindbe on 2013-12-18
Hi!

I have the following problem on my Lenovo T410 with Ubuntu 12.04: On a certain Wifi, my connection is horribly slow (download speeds of a few kB/s despite the connection being 100/100). For other users of this network, the connection speed is fast. If I boot up my computer in Windows (dual-boot), the connection is fast. My computer with Ubuntu using other Wifi networks: fast.

After searching around here a bit, I found the tip to set modprobe -v rt2800pci nohwcrypt=1, but this did not help. Any other suggestions? Please let me know which logs or outputs you would need.

Best regards,
jolindbe

---

### Post by varunendra on 2013-12-20
While being connected to this 'slow' wifi, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by jolindbe on 2013-12-21
Solved with the instructions in this post: [http://ubuntuforums.org/showthread.php?t=1984675&p=12413762#post12413762](http://ubuntuforums.org/showthread.php?t=1984675&p=12413762#post12413762)

---

