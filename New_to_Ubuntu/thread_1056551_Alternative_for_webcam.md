---
title: "Alternative for webcam??"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by Doug11 on 2009-01-31
Been trying to get my Logitech Quickcam to work for a few days now and I am having no luck what so ever. I can get ti to work in cheese but thats it. I was wondering if it was possible to run MSN messenger in wine and also install the software for the webcam in wine,,would it then work? I haven't tried it but am just curious.

---

### Post by JohnLM_the_Ghost on 2009-01-31
Sorry in wine it is a no go!
Wine can only use it if it has installed properly in native linux.

---

### Post by Crafty Kisses on 2009-01-31
That's really weird my Logitech Quickcam works perfectly, here try this and see if you don't get your webcam going:

Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2) To test your webcam you can do this: There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly. If Ekiga doesn't work post results of the command:
```
lsusb
```

---

### Post by Doug11 on 2009-01-31
I am not getting the bouncing logo but am not getting the webcam out put either, this is what i get from running lsusb

doug@doug-laptop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 046d:c51b Logitech, Inc. 
Bus 001 Device 003: ID 046d:092c Logitech, Inc. QuickCam Chat
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Crafty Kisses on 2009-01-31
Well it appears that it sees the webcam and the built in mic on the webcam, unless that's a headset.
```
Bus 001 Device 004: ID 046d:c51b Logitech, Inc.
Bus 001 Device 003: ID 046d:092c Logitech, Inc. QuickCam Chat
```

---

### Post by Doug11 on 2009-01-31
> **Codename said:**
> Well it appears that it sees the webcam and the built in mic on the webcam, unless that's a headset.
```
Bus 001 Device 004: ID 046d:c51b Logitech, Inc.
Bus 001 Device 003: ID 046d:092c Logitech, Inc. QuickCam Chat
```

It's actually built in to the Laptop. This is about the last thing I need to make the final switch and get rid of MS so the wife can see her grand-daughter on webcam. It's been driving me nuts trying to figure this out.

---

### Post by Doug11 on 2009-01-31
This is the error Ekiga is throwing out,,

Your driver doesn't seem to support any of the color formats supported by Ekiga.
 Please check your kernel driver documentation in order to determine which Palette is supported.

---

### Post by Crafty Kisses on 2009-01-31
Have you checked the Hardware Drivers option too see if there are any drivers available for that built-in webcam. You can access this option by going to **System->Administration->Hardware Drivers**.

---

### Post by Doug11 on 2009-01-31
> **Codename said:**
> Have you checked the Hardware Drivers option too see if there are any drivers available for that built-in webcam. You can access this option by going to **System->Administration->Hardware Drivers**.

There were only two drivers there. FW-cutter for wireless and the fglx graphics driver.

---

### Post by JohnLM_the_Ghost on 2009-02-01
Hmm... fglrx video driver has some certain issues with v4l interface (needed for webcam)
btw If you get black output only, then ther is a chance driver is present, but not configured correctly.
I also have a Logitech QuickCam, but it is no priority for me...
But I might take a look into it.

---

### Post by Doug11 on 2009-02-01
> **JohnLM_the_Ghost said:**
> Hmm... fglrx video driver has some certain issues with v4l interface (needed for webcam)
btw If you get black output only, then ther is a chance driver is present, but not configured correctly.
I also have a Logitech QuickCam, but it is no priority for me...
But I might take a look into it.
I am just getting a black screen when i go into amsn settings. even tried easycam but just kept getting errors. I had it working way back when feisty first come out and then give up on linux for a while. Now would like to make it primary.

---

### Post by proevofanatik on 2009-08-02
has anyone got quickcam messenger plus working yet? this is what i get when i run lsusb

$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 046d:08f6 Logitech, Inc. Quickcam Messenger Plus
Bus 002 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by ftmichael on 2010-06-08
I'm having the same problem in Lucid - just a black screen in Cheese, no video in Skype.  **lsusb** gives me:

```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:092c Logitech, Inc. QuickCam Chat
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

**luvcview** gives me:

```
luvcview 0.2.6

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
Stream settings:
ERROR: Requested frame format MJPG is not available and no fallback format was found.
 Init v4L2 failed !! exit fatal
```

---

### Post by no2498 on 2010-06-10
in/on 910 and up cheese webcam booth is/should be loaded
look for it in sound & video
try the cam in it first

if it does not come on try this

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

retry the cam in cheese
cheese has a nice help file look in the faq's


hope this helps

---

### Post by Breambutt on 2010-06-10
Try loading the uvcmodule with *sudo modprobe uvcvideo*. If it helps, you can add the line *uvcvideo* to /etc/modules with *sudo gedit /etc/modules* to load it on startup.

With regards to Skype, you might need to fidget something else, i.e. [http://ubuntuforums.org/showpost.php?p=9317367&postcount=4](http://ubuntuforums.org/showpost.php?p=9317367&postcount=4) - Forum search should return a few billion threads about this.

There's something fishy going on with the billions of different QuickCam models in the current kernel.

---

### Post by no2498 on 2010-06-10
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

---

