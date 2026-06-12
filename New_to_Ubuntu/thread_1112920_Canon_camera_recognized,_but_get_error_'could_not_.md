---
title: "Canon camera recognized, but get error 'could not claim the USB device'"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by Motorhead Kaze on 2009-04-01
Hi there.
Having some trouble connecting our Canon PC1192 camera through the USB port.

In FSpot, when trying to import photos, I see the camera listed as a "Canon Powershot S3 IS (PTP Mode)" on the import source list. But when I click "import" I get a message that reads:

"Error connecting to camera. Received error 'could not claim the USB device' while connecting to camera"

I have read a few threads on the net related to this message, but the fixes are far more technical than I can understand.But basically, Ubuntu knows the camera is connected and even what kind it is, but I cannot get inside the camera to fetch the photos.

BTW, my Sanyo camera hooks right up to Ubuntu without a hitch. It shows up on the desktop as a 2Gb device, the Canon nada.

Thanks for any help in advance.

---

### Post by franco81 on 2009-04-01
I had problems with fspot and came across gphoto2 and gtkam, I wrote this blog post about it: [http://deadlytechnology.com/linux/save-photos-nikon-ubuntu/](http://deadlytechnology.com/linux/save-photos-nikon-ubuntu/)

I think if you just go to Applications->Add/Remove and search for gtkam to install then after it is installed you should be able to find it in application->graphics and it should be straightforward from there. HTH.

---

### Post by Motorhead Kaze on 2009-04-21
Just when I was ready to fix this...my nephew went back to the States and took his camera with him. Thanks for the help anyway! Learned about some new programs this way.

---

