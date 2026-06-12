---
title: "Very green user"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by scott dillon on 2009-11-23
Hi All,

I have installed  ubuntu successfully (partitioned my PC from Windows) and now trying hard to find a driver for my Belkin 802.11g 54mbps F5AD83D usb wireless adapter. 

I was hoping that a driver would be easily downloaded and then installed. 

Would someone be able to spell out the very very basic steps to install the driver?

and still have the possibilty of using the windows side of things.

Best regards, Scott.

---

### Post by coffeecat on 2009-11-23
I tried googling 'Belkin F5AD83D' to check what chipset it has, but there was only one hit - this thread. :? Have you made a typo? Double-check the model number.

Anyway, Belkin usually use Linux-friendly chipsets, so are you sure that it's not working already? Drivers for many wireless devices are built into the kernel. Have a look for the network manager applet icon on the top panel - towards the right, next to the volume control applet. Click on it. Does it show your wireless network? If so, click on your network name, put in your WEP/WPA passphrase where prompted and you should be OK.

If not, go to Applications > Accessories > Terminal. Make sure the Belkin is plugged in and do the following command, then enter:

```
lsusb
```Post the line (copy and paste) for the Belkin. Hopefully, that will tell us the chipset. If not, the ID number will give us a lead.

---

