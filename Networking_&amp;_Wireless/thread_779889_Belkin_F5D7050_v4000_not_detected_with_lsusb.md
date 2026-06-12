---
title: "Belkin F5D7050 v4000 not detected with lsusb"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by Sambo320 on 2008-05-03
This device uses the zd1211rw driver. The device does not even show up with lsusb. The device works with other windows computers. I am running a clean install of ubuntu 8.04. Please help! This has been hell.

---

### Post by thatrandomguy on 2008-05-03
have you tried using these drivers?

[http://rt2x00.serialmonkey.com/](http://rt2x00.serialmonkey.com/)

---

### Post by Paris Heng on 2008-05-03
> **Sambo320 said:**
> This device uses the zd1211rw driver. The device does not even show up with lsusb. The device works with other windows computers. I am running a clean install of ubuntu 8.04. Please help! This has been hell.

Bring up your interface first. ifconfig <interface> up

---

### Post by Sambo320 on 2008-05-04
> **thatrandomguy said:**
> have you tried using these drivers?

[http://rt2x00.serialmonkey.com/](http://rt2x00.serialmonkey.com/)


The rt73 driver is used for versions under 4000. My version 4000 uses the zd1211rw driver.

---

### Post by Martyn12 on 2008-05-04
I had some real problems with this too. The girlfriend uses an Acer Travelmate 2200 with the 1000 version of this card. Like you though, many times (still) it won't be seen by the lsusb and therefore won't work with other modules. 
I eventually got it working by plugging it into one of the other three USB ports available on the Travelmate. Not very scientific (especially as there never seems to be a pattern to which works!) but do eventually get it seen and therefore running. Sometimes it did need a reboot too, just so you are aware. 
As previously mentioned, I am using version 1000 of this card but it now works fine with ndiswrapper and the windows driver. 
Best of luck, 

Martyn.

---

### Post by Sambo320 on 2008-05-04
Even after plugging and replugging to different ports, the device is not recognized...

---

### Post by SeePU on 2008-07-03
I don't know if this will help you but try unplugging any usb devices you may have plugged in while your usb wireless adapter is plugged in.  Reboot and unplug everything from the usb ports except for your wireless adapter.  Does that help? 

As for not reading, it sounds like the native drivers are not getting loaded.  I would google that and search the forums.

---

