---
title: "wifi drivers"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by don_diego on 2009-05-28
To install a wifi PCMCIA card I went to its manufacturer's website and downloaded a driver for it. However, when I tried to add it to the Windows Wireless Drivers, the system said "Invalid driver". Since there were other drivers listed on the website (unfortunately no specific info was given as to what they were for) I then downloaded another one which - luckily - turned out to be a Linux tar file.

I did manage to extract the file's contents and now have several files and folders but no idea which one might be the driver. I am going to attach the file (or try to) and am hoping somebody can help me understand how to deal with this.

TIA

---

### Post by don_diego on 2009-05-28
Sorry, I guess my first stab at attaching a file didn't work.

---

### Post by keiser_soze on 2009-05-28
Please send

> lsusb

print out.

---

### Post by don_diego on 2009-05-28
Not sure how usb is relevant but here it is:

l```
utz@ubuntu-laptop:~$ lsusb
Bus 002 Device 003: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/4GB Flash Drive
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04d9:0499 Holtek Semiconductor, Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
lutz@ubuntu-laptop:~$ 
```

---

### Post by mapes12 on 2009-05-28
Here are some links that may be helpful:

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

[http://madwifi.org/](http://madwifi.org/)

[http://ubuntuforums.org/showthread.php?t=794815](http://ubuntuforums.org/showthread.php?t=794815)

[https://help.ubuntu.com/community/Wi...3d3c3468508d45](https://help.ubuntu.com/community/Wi...3d3c3468508d45)

[https://help.ubuntu.com/community/Wi...eShootingGuide](https://help.ubuntu.com/community/Wi...eShootingGuide)

Good luck.

Mark

---

