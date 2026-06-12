---
title: "Webcam Not Working In 8.10"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by cfree220 on 2009-01-29
Today I installed Intrepid Ibex on a portable hard drive. After I installed Skype, I discovered that my webcam is not working. I'm guessing this means it's missing some sort of a driver? Can anyone tell me how to get it working again?
Thanks in advance,
Chris
PS The mic isn't working either.

---

### Post by jpoRS on 2009-01-30
The mic not working is unusual.  Unfortunately the webcam isn't.  The most important thing for solving this is finding out what hardware you are working with.  Webcam compatibility is completely unpredictable, check [here]("https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras") to see if yours works.  If it is supported follow the suggestions and you'll be back in business.

As for the mic: try this simple trick.  Double click your volume icon in your menubar, click "Preferences" and enable EVERYTHING.  Go back to the regular volume control window, and see if anything is muted.  Sometimes that is the only problem.

Anyway, Let us know what happens, and for future reference it always pays to give us as much information as possible about your computer, software and hardware.  That way we can give you the best help possible.

Good luck, and welcome to the community,
jim

---

### Post by cfree220 on 2009-01-30
Hi,
I'm not sure exactly which cam it is... I'm prety sure it's creative, but I didn't find anything on their site for it (I should note that it is an integrated webcam). I tried your suggestion on the mic... nothing. I tested it with the sound recording, and it's not registering anything (according to the levels indicator). Also, my speakers are not working.

Update on the last bit, apparently only the first headphone jack is supported. I always thought that was strictly a hardware thing.

---

### Post by Crafty Kisses on 2009-01-30
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2) To test your webcam you can do this:

There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly. If Ekiga doesn't work post the results of the following command: ```
lsusb
```

---

### Post by cfree220 on 2009-01-30
Although, they don't sound nearly as good as when I play from Windows, and they aren't nearly as loud.

---

### Post by cfree220 on 2009-01-30
Output:
```

cfreeman@Umbra:~$ lsusb
Bus 007 Device 002: ID 1058:0702 Western Digital Technologies, Inc. Passport External HDD
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:071d Microsoft Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
cfreeman@Umbra:~$

```

---

### Post by cfree220 on 2009-01-30
Oh, wait. lsusb would be list usb devices, right? The webcam is integrated.

---

### Post by waspbr on 2009-01-30
did you try using the "Multimedia Systems Selector" GUI ?

I don't think it is enabled on the menus by defaults, the quickest way to access it is to  press ALT+F2 and type:
```
gstreamer-properties
```*

as the GUI pops up, go to the video tab. At the default input section play around with the plugin settings,  either v4l or v4l2, press the test button after selecting each of them to see if they really work or not. 

gl


* alternatively you can just right click on the ubuntu applications menu, and select the edit menus option, this is going to bring up a dialogue, scroll down to the end where the preferences entry is, click there, then at the right you should see a bunch of boxes enable one that  says Multimedia Systems Selector, close the dialogue.  Now you should be able to access the Multimedia Systems Selector from you preferences menu.

---

### Post by cfree220 on 2009-01-30
hmmm.... I've gotten the video working, but the audio in configuration is still not working.

---

### Post by novafluxx on 2009-01-30
Ah! Trying that gstreamer-properties showed me that my cam does indeed work! Thank You!

---

