---
title: "camorama - could not connect to video driver"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by nfbueno on 2008-12-28
I have webcam driver already installed for my laptop's built-in webcam. The dmesg has the following lines

> 
[ 9666.403373] microdia: Microdia USB 2.0 webcam driver loaded
[ 9666.403439] microdia: Microdia USB 2.0 Webcam - 0C45:624F plugged-in.
[ 9666.403447] microdia: Detected SN9C20X Bridge
[ 9666.422223] microdia: Detected OV9650 Sensor
[ 9666.525580] microdia: Microdia USB 2.0 Webcam is now controlling video device/dev/video0
[ 9666.527916] usbcore: registered new interface driver usb_microdia_driver
[ 9666.527936] microdia: v2008.11 : Microdia USB 2.0 Webcam Driver



But when I tested it using camorama, I go the following message
> 
Could not connect to video device (/dev/video0). Please check connection.


Can't figure out the problem. Please help. Thanks.

---

### Post by spiderbatdad on 2008-12-28
camorama might be broken in intrepid...at least with that driver. Have you tried cheese?```
sudo apt-get install cheese
```

---

### Post by nfbueno on 2008-12-28
Thanks for the reply. I tried cheese and it only showed color bands.

---

### Post by spiderbatdad on 2008-12-28
so your laptop came with ubuntu pre-installed, and had the microdia driver?
I got my microdia driver here:[http://groups.google.com/group/microdia](http://groups.google.com/group/microdia)

---

### Post by nfbueno on 2008-12-28
> **spiderbatdad said:**
> so your laptop came with ubuntu pre-installed, and had the microdia driver?
I got my microdia driver here:[http://groups.google.com/group/microdia](http://groups.google.com/group/microdia)

I switched from openSUSE to ubuntu a week ago. My webcam is, from lsusb it says, 
> 
Bus 001 Device 003: ID 0c45:624f Microdia PC Camera (SN9C201)


To install the driver, I followed the guide I found in [http://groups.google.com/group/microdia/web/testing-microdia-driver-draft](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft)

---

### Post by spiderbatdad on 2008-12-28
hmmm. yep thats the same driver I'm using...following the building from source directions. It has been working well for me in all apps I use webcam for...gyachi, skype, cheese.
Sorry I dont know what else too offer.

---

