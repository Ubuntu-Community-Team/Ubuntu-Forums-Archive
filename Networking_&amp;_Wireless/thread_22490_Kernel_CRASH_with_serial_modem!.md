---
title: "Kernel CRASH with serial modem!"
date: 2005-03-28
forum: Networking &amp; Wireless
---

### Post by smarttaz on 2005-03-28
Ubuntu 4.10:
 
With my external serial "very hardware" modem [http://www.trendnet.com/en/products/TFM-560X.htm]("http://www.trendnet.com/en/products/TFM-560X.htm") (which works 101% under Slackware, Mepis, WinXP), the facts are:
 
1. If I boot the laptop with the modem "ON" and connected on RS-232, during the boot process, the kernel crashes with the following... uh... "black screen of death" (see the attached pic).
 
This does NOT happen with the LIVE CD!
 
2. More than that, the issue is that, as I don't boot with it up and running, I have to make a 'sudo ln -s /dev/ttyS0 /dev/modem' every time I boot, because the symlink is deleted! A solution to avoid this is to add to the file /etc/udev/udev.rules/ a line:
# UDEV rule for external serial modem
KERNEL="ttyS[0-3]", NAME="%k", MODE="0660", GROUP="dialout", SYMLINK="modem" 
 
However, if I boot with the modem ON and connected to the serial port, the kernel still crashes! (see [modem-crash.jpg]("http://ubuntuforums.org/attachment.php?attachmentid=&stc=1"))
 
Any hint?

---

