---
title: "NOVATEL Wireless Modem setup"
date: 2013-10-20
forum: Networking &amp; Wireless
---

### Post by aromo2 on 2013-10-20
Hi,

Just wanted to share how I configured the Novatel Wireless 3G modem in Lubuntu (mine is connected through Bell).

1. Download usb-modeswitch-2.0.1 and usb-modeswitch-data from here: [http://www.draisberghof.de/usb_modeswitch/#download](http://www.draisberghof.de/usb_modeswitch/#download)

2. In Synaptic, remove libusb-devel (if installed) and install libusb-1.0-0, libusb-1.0-0-devel and pkg-config

3. uncompress and untar the files downloaded in step 1

4. cd usb-modeswitch-2.0.1/ and edit usb_modeswitch.h:
    replace the line
       #include<libusb.h>
    with
       #include </usr/include/libusb-1.0/libusb.h>

5. For each directory (usb-modeswitch-2.0.1 and usb-modeswitch-data), do:
    cd <directory>
    make clean
    make remove
    make
    make install

6. At this point you should be able to plug in the Novatel Wireless modem and configure it using the Network Manager applet.

Enjoy.

---

