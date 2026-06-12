---
title: "usb camera detection"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by tompoe on 2010-09-05
I installed the desktop 10.04 iso on my Dell computer.  I have a Sanyo digital camera on usb port.  I need to have an application that can detect my camera and pass the video/photos to my hard drive.  Any recommendations?

---

### Post by sandyd on 2010-09-05
> **tompoe said:**
> I installed the desktop 10.04 iso on my Dell computer.  I have a Sanyo digital camera on usb port.  I need to have an application that can detect my camera and pass the video/photos to my hard drive.  Any recommendations?
f-spot/digicam?
or maybe use a card reader.

what happens when you plug the camera in?

---

### Post by kmsalex on 2010-09-05
If its detected properly as a camera then you should get a little auto  run prompt asking if you want to use f-spot to import them (i personally  like f-spot and use it my self), if you don't get that auto run then it  was either detected as a flash drive, or not at all. 

If its detected as a flash drive then you should see it as a drive on  your desktop, just double click on it and it should open it in Nautilus.  brows threw the folders till you find the one with your pics/videos and  copy them (don't cut you could screw up the file system) and past them  into a folder of your liking.

If its not detected at all its probably the particular model of camera,  post back here with the exact model and we'll see if there's a work  around for your model.

---

### Post by no2498 on 2010-09-06
you may need to turn the cam on an look if you need to click it to connect to the computer

---

### Post by philinux on 2010-09-06
> **tompoe said:**
> I installed the desktop 10.04 iso on my Dell computer.  I have a Sanyo digital camera on usb port.  I need to have an application that can detect my camera and pass the video/photos to my hard drive.  Any recommendations?

Plug the cam in then open a terminal. Apps>Accessories.

```
lsusb
```

Post back the output of the above command.

---

