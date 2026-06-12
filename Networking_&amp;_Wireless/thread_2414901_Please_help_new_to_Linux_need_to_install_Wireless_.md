---
title: "Please help new to Linux need to install Wireless usb adapter DWA-182 version c"
date: 2019-03-16
forum: Networking &amp; Wireless
---

### Post by adamromeo on 2019-03-16
Hello, pardon me but I recently installed Ubuntu 18.4 LTS on my Laptop Asus Vivobook Model X540BA-RB94  which I just found out it doesn't have an Ethernet controller.    Now I was able to get a wireless USB stick.  D-LINK DWA-182 Version C I couldn't find drivers for the onboard wireless so I got wireless stick. . I downloaded the driver from the site for linux for D-LINK DWA-182 version C

My question is how do I install the driver ? It's on a USB stick. 

The name of file as a Zip   DWA-182_REVC_DRIVER+_4.3.2_LINUX.ZIP

Extracted File Name:   RTL9912AU_linux_v4.3.2_11100.20140411

When I access the extracted file and go to the driver     I have   rtl8812AU_linux_v4.3.2_11100.20140411.tar.gz

Kindly guide me on how to install this  ?  

I have my terminal open

---

### Post by wildmanne39 on 2019-03-16
*Thread moved to **Networking & Wireless a more appropriate sub-forum**.*

---

### Post by adamromeo on 2019-03-16
Alright, so I have renamed the file to rtl8812.tar.gz

---

### Post by adamromeo on 2019-03-16
I typed **tar** zxvf rtl8812.**tar**.gz.

I get a long-list of of everything in that file archive..

---

### Post by kc1di on 2019-03-17
You said you could not get an ethernet connection?

please go to a terminal and type this command and post the output here:
```
lshw -C network
``` Post the output here.  Do this both with usb wireless unattached and attached.

---

### Post by praseodym on 2019-03-17
Try this DEB file

[http://de.archive.ubuntu.com/ubuntu/pool/universe/r/rtl8812au/rtl8812au-dkms_4.3.8.12175.20140902+dfsg-0ubuntu8_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/r/rtl8812au/rtl8812au-dkms_4.3.8.12175.20140902+dfsg-0ubuntu8_all.deb)

---

### Post by jeremy31 on 2019-03-17
> **praseodym said:**
> Try this DEB file

[http://de.archive.ubuntu.com/ubuntu/pool/universe/r/rtl8812au/rtl8812au-dkms_4.3.8.12175.20140902+dfsg-0ubuntu8_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/r/rtl8812au/rtl8812au-dkms_4.3.8.12175.20140902+dfsg-0ubuntu8_all.deb)

Does that have the dkms fix?  I know the rtl8812au-dkms in the repos is still broken

---

