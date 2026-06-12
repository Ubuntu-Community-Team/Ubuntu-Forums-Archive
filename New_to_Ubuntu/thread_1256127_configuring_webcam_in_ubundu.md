---
title: "configuring webcam in ubundu"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by shebin on 2009-09-02
I am trying to migrate from windows to Ubundu 9.04 - the Jaunty Jackalope. I am using HP Pavilion dv6125ea laptop and the OS works great. However, i am not able to access my built in webcam in ubundu. The OS does not detect it. any help??????/

---

### Post by t0p on 2009-09-02
Try **cheese**

```
sudo apt-get install cheese
```

It's not the most full-featured webcam app, but it's pretty good at autodetecting/configuring cams and gives you a quick idea if your cam is compatible.

---

### Post by ayenack on 2009-09-02
Also worth a look.

[B]sudo apt-get install camorama

sudo apt-get install cameramonitor[/B]

---

### Post by KIAaze on 2009-09-02
Unlike Windows, there's no popup message notifying you of an attached webcam (unless I missed it).

Running cheese is indeed a good way to quickly know if it works. or not.

Otherwise, here are some useful tips to get more info on the webcam:
> 1)To find out the device ID of your webcam, typing **lsusb **in a terminal window will list all USB devices on your system. Try to find the relevant line for your webcam. The ID then appears after "ID" on that line, in the form xxxx:xxxx where the 'x's are numbers or letters

2)If your webcam is working on some applications other than Skype 2.0 beta, then it would be useful to know what particular driver your webcam is using. To find out, type **lsmod | grep videodev**. The driver name will appear on the line starting with "videodev". 

cf: [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

---

### Post by shebin on 2009-09-03
:D Thank yo u all for your valuable help. i installed cheese and it worked. i hope to build on with this experiance and hope to take microsoft off my system.

luv,
shebin

---

### Post by The_Blode on 2009-09-04
Installing Cheese was all that was required for me to get my unbranded and cheap usb webcam to function. It's strange, the installation of this device under Ubuntu was so easy compared to the Windows one. Many thanks for this post! :D

---

