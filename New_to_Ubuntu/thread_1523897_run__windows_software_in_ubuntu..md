---
title: "run  windows software in ubuntu."
date: 2010-07-04
forum: New to Ubuntu
---

### Post by the juman on 2010-07-04
hhhelo there fellaas..

hmm.i  installed ubuntu 10.04 into my computer.you know you have to download plugins to play mp3.
So i have a (they call it a 3g plus mobile broadband modem. You know like a usb pen drive).in its cover it is written that it supports mac and windows..
So is there a way to get a net connection with it.i meen even though it doesent support linux.


any who helps is thanked bye me
----juman----

---

### Post by migs73 on 2010-07-04
Unfortunately you will probably have to download the drivers for you 3G modem as well.(if it is supported). You will need to find yourself somewhere to plug in a LAN cable and get internet access.

---

### Post by bodhi.zazen on 2010-07-04
See if this thread helps with your 3g

[http://ubuntuforums.org/showthread.php?t=999015](http://ubuntuforums.org/showthread.php?t=999015)

For mp3 files , install the LInux software.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

In general windows software does not run on Linux.

---

### Post by migs73 on 2010-07-04
Bodhi

I think the OP's problem is he wants to play mp3's but needs acces to the internet to download the codecs etc. Problem is his internet connection is via the 3G modem, for which he needs to download drivers ( I am assuming it has already been tried without drivers).
Hence my advice to find a LAN connection somewhere.

---

### Post by bodhi.zazen on 2010-07-04
> **migs73 said:**
> Bodhi

I think the OP's problem is he wants to play mp3's but needs acces to the internet to download the codecs etc. Problem is his internet connection is via the 3G modem, for which he needs to download drivers ( I am assuming it has already been tried without drivers).
Hence my advice to find a LAN connection somewhere.

indeed, I hope my first link gets the 3g up , but the OP will likely need to resort to a wired connection as a first step.

---

### Post by bumanie on 2010-07-04
Do you know which 3g modem you have? > lsusb in terminal will list the device. Once the device is known, more help can be given. Many 3g modems do work well in linux - in fact I am using one to write this reply. You can post the output here if you need help finding the device.

---

### Post by spiky001 on 2010-07-04
It might be basicaly not set up in network manager make sure that is done,
+1 To Bumanie  i,m using 3g modem as well set up straight away

---

### Post by the juman on 2010-07-05
> **bumanie said:**
> Do you know which 3g modem you have?  in terminal will list the device. Once the device is known, more help can be given. Many 3g modems do work well in linux - in fact I am using one to write this reply. You can post the output here if you need help finding the device.
does that mean i can get a connection with ubuntu. I told u beforeit says that it doesn't support LINUX

---

### Post by the juman on 2010-07-05
any wayythanks guys it helped a lot

---

### Post by Zintha on 2010-07-05
I have a 3g dongle I used for windows.

Plug-and-play for 10.04 and 9.10 so far, long as I knew some of the setup for it which a quick google will give you what you need.

Works 10x better than in windows too, don't need the crappy windows software for it.

---

### Post by Lucifer The Dark on 2010-07-05
I wouldn't worry too much about your manuals stating only Windows or Mac support, none of my pc components mention Linux support anywhere but they work just as well or in some cases better in Linux than Windows.

---

### Post by mike555 on 2010-07-05
When I used a 3g modem I had to install gnome-ppp to get it working ....... you might need to also.

---

### Post by 3rdalbum on 2010-07-05
1. You wouldn't be able to use a Windows program or a Windows driver on Ubuntu to run your 3G modem.

2. Go to the Network Manager applet on the top panel, right-click it and choose Edit Connections. Click the Mobile Broadband tab and click the Add button, and follow the prompts. If Linux has a driver for this modem, then it will work. Don't worry if the modem's packaging says that it works on "Windows and Mac"; Linux supports a lot of hardware without the manufacturer even knowing.

3. Don't bother trying to run any of the modem's software, just use Network Manager and see if it works.

---

### Post by the juman on 2010-07-05
> **3rdalbum said:**
> 1. You wouldn't be able to use a Windows program or a Windows driver on Ubuntu to run your 3G modem.

2. Go to the Network Manager applet on the top panel, right-click it and choose Edit Connections. Click the Mobile Broadband tab and click the Add button, and follow the prompts. If Linux has a driver for this modem, then it will work. Don't worry if the modem's packaging says that it works on "Windows and Mac"; Linux supports a lot of hardware without the manufacturer even knowing.

3. Don't bother trying to run any of the modem's software, just use Network Manager and see if it works.

i tried it and it has the driver i am checking if it was ..
i am in a hurry

---

