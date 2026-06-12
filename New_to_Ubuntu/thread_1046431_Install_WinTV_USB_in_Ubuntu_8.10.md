---
title: "Install WinTV USB in Ubuntu 8.10"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by josesmart on 2009-01-21
Hi everybody.
Could anybody help me find and install drivers for an old Hauppauge WinTV USB in Ubuntu 8.10?
Thanks

---

### Post by DezSP on 2009-01-22
Hiya,

A lot of the Hauppage devices tend to be recognised by Ubuntu, even if it doesn't tell you. I suggest downloading the xawtv package from the Ubuntu repos, if your capture device is properly detected then that viewer should find it. :)

---

### Post by bwang on 2009-01-22
What model is it? It may be detected by MythTV:
```
sudo apt-get install mythtv
```

---

### Post by josesmart on 2009-01-24
> **DezSP said:**
> Hiya,

A lot of the Hauppage devices tend to be recognised by Ubuntu, even if it doesn't tell you. I suggest downloading the xawtv package from the Ubuntu repos, if your capture device is properly detected then that viewer should find it. :)

Thanks DezSP.
Have installed xawtv:) but nothing happened after running xawtv.

This device (WinTV USB) is prior to WINTV USB2 and was working perfectly under Win XP.

Any other suggestion?
Thanks for your help.[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

### Post by josesmart on 2009-01-24
> **bwang said:**
> What model is it? It may be detected by MythTV:
```
sudo apt-get install mythtv
```

Thanks BWANG.
Have installed Mythtv but "Watch TV" didn't work.
This device (WinTV USB) is older than WinTV USB2 and was running perfectly under Win XP.
Any other suggestion?
Thanks beforehand.[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

### Post by DezSP on 2009-01-24
Try running ```
lsusb
``` from a terminal and paste the results here.

---

### Post by josesmart on 2009-01-26
> **DezSP said:**
> Try running ```
lsusb
``` from a terminal and paste the results here.

OK DezSP here goes:

smartlar@AZUL:~$ lsusb
Bus 005 Device 010: ID 067b:2517 Prolific Technology, Inc. Flash Disk Mass Storage Device
Bus 005 Device 009: ID 067b:2515 Prolific Technology, Inc. Flash Disk Embedded Hub
Bus 005 Device 008: ID 0ac8:301b Z-Star Microelectronics Corp. ZC0301 WebCam
Bus 005 Device 007: ID 04b4:6830 Cypress Semiconductor Corp. CY7C68300A EZ-USB AT2 USB 2.0 to ATA/ATAPI
Bus 005 Device 006: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 005 Device 005: ID 04f9:0193 Brother Industries, Ltd MFC-215C
Bus 005 Device 004: ID 04a5:9001 Acer Peripherals Inc. (now BenQ Corp.) AWL400 Wireless Adapter
Bus 005 Device 003: ID 050d:0224 Belkin Components F5U224 USB 2.0 4-Port Hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 0573:4d01 Zoran Co. Personal Media Division (Nogatech) Hauppauge WinTV-USB
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05e3:0502 Genesys Logic, Inc. GL620USB GeneLink USB-USB Bridge
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
smartlar@AZUL:~$ 

Can't wait for a miracle.
Thanks
[http://ubuntuforums.org/images/smilies/icon_razz.gif](http://ubuntuforums.org/images/smilies/icon_razz.gif)

---

### Post by bwang on 2009-01-26
This ancient page: [http://www.linuxquestions.org/hcl/showproduct.php?product=1344&cat=464](http://www.linuxquestions.org/hcl/showproduct.php?product=1344&cat=464)
says drivers are available [here]("http://usbvision.sourceforge.net/")

Unfortunately, the drivers are rather old (last updated in 2004), and seem to be very difficult to install.:(

---

