---
title: "unable to scan"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by manny43 on 2011-05-01
Hello friends,

Ubuntu 11.04
MFC-440CN

Using "Simple Scan" the following message pops up"Failed to scan.Unable to connect to scanner".Please help.Thanks.
Solved as follow:
Installed XSane Image Scanning program
opened /lib/udev/rules.d/40-libsane.rules
Added the following:
#MFC-440CN
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="01af", ENV{libsane_matched}="yes"

---

### Post by mr_luksom on 2011-05-01
That looks suspiciously like a Brother scanner. Have you installed the brscan/brscan2 drivers from the Brother Website?

All of the files and instructions can be found here:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

See if you can install the drivers, and post back here if you have any trouble.

---

### Post by manny43 on 2011-05-01
Thank you

---

