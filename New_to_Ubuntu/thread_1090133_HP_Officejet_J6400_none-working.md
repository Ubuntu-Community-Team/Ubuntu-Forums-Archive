---
title: "HP Officejet J6400 none-working"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by bellabrokenxx on 2009-03-07
I recently switched from windows to ubuntu
As I do very much enjoy ubuntu 8.04, (hardy heron, i learned the name is), i'm having trouble using my HP Officejet J6400. I can print off it, but the scanner seems to be not wanting to work.  I searched through many websites to find what i need to make it work, but all I found was downloading the hplip. I downloaded it, but I have NO clue how to use it.


is there anyone who can help me?

---

### Post by doctorbighands on 2009-03-07
Can you get XSane to work for you? (Applications > Graphics > XSane)

It's been my experience that instead of pushing the "scan" button on your printer, you have to open XSane and tell it to scan whatever you want for you.

---

### Post by bellabrokenxx on 2009-03-08
sane claims that there is no device, and when i use my "scan to" button, it claims there is no other devices then my friends computer.

---

### Post by kansasnoob on 2009-03-08
Looking here:

[http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html)

I don't specifically see the j6400, but many that start with j64**.

Anyway that's the first place to start.

I have had trouble with the packaged version of HPLIP in both Intrepid and Jaunty, so I've had to go to Synaptic Package Manager and remove hplip, and then download the newest HPLIP and use their Automatic installer:

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

I should also add that to get the HP Device Manager (which will show up in Apps > Accessories) to work I've had to install the following packages:

```
sudo apt-get install libqt4-assistant libqt4-test ttf-dustin python-qt4-common libqt4-xmlpatterns libqt4-help python-qt3 python-qt4 libqt4-webkit python-sip4 libqt4-svg python-reportlab
```

---

### Post by bellabrokenxx on 2009-03-08
I am working on the first step, but when i try to open the synaptic package manager, it comes up with an error.

---

