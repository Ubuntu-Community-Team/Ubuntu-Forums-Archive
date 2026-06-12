---
title: "Logitech Quickcam Again!"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by av.kumar85 on 2009-05-23
Hi I am a Noob. I am sure this has come up at least a hundred times before... but somehow i seem to lack the intelligence to understand any of the many posts regarding how to install a Logitech quickcam. Fortunately, the one thing i have learned is that its vital to list out what OS, and config I am running on to get a solution or a worthwhile suggestion. Unfortunately I dont know which quickcam i have as i have lost the box.

Logitech Quickcam:
Details on the cable tag:
M/N: V-UAZ27A
P/N: 861208-0000
PID: LZ627BP

Details when i try to run with Camorama:
USB Camera: 046D:08ac

My install:
Ubuntu 9.04 Jaunty Jackalope.
Gnome Desktop
Compiz Fusion

I need a how to on installing this webcam, and running it with Camorama, Skype, Ekiga and some sites which can stream through my camera (like Indyarocks.com).

Please help this dumb N00B.. Pleas Please Please....

---

### Post by labinnsw on 2009-05-23
Used to be, we had to install these but on later versions of Ubuntu, most Logitech Cameras are plug and play. Is there a specific problem you are having or an error that you are encountering?

---

### Post by candtalan on 2009-05-23
to help identify, have you seen:
[http://www.logitech.com/index.cfm/405/&cl=gb,en?prodcrid=405](http://www.logitech.com/index.cfm/405/&cl=gb,en?prodcrid=405)
and
[http://www.quickcamteam.net/devices](http://www.quickcamteam.net/devices)
[see Logitech UVC Device Feature list by feature (Last update: 2009-01-05) ]

I recently helped a friend buy and install a Logitech Quickcam S7500 for an Ubuntu 8.04 system (Toshiba Satellite with usb 1.1)
[http://www.argos.co.uk/webapp/wcs/stores/servlet/Search?storeId=10001&catalogId=1500001501&langId=-1&searchTerms=S7500&Submit=GO+%3E](http://www.argos.co.uk/webapp/wcs/stores/servlet/Search?storeId=10001&catalogId=1500001501&langId=-1&searchTerms=S7500&Submit=GO+%3E)
and I plugged it into the usb socket, ran skype, used the Options menu in skype, video devices, 'Test' and it immediately worked. The webcam insitu microphone also worked fine, but I had to use Options, Audio devices, and choose a usb item, not the default item.

I have not tried any other webcam related application only skype.


HTH

---

### Post by av.kumar85 on 2009-05-23
> **labinnsw said:**
> Used to be, we had to install these but on later versions of Ubuntu, most Logitech Cameras are plug and play. Is there a specific problem you are having or an error that you are encountering?

yeha... min is not functioning like a plug and play :(. In camorama, whenever i try there comes a dialog box saying: "Unable to Capture Image". And when i click ok.. the Camorama session exits. I had some minute luck with Skype's video test when i typed this line in the terminal:
[I]
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype[/I]

But i want to use the webcam not only in skype but in other apps as well... 
and i don't want to be running them from terminal...

any help pls !?:confused::frown: No matter how many times i try its like im heading into a brick wall...](*,)

---

### Post by candtalan on 2009-05-23
> **candtalan said:**
>  [snip]I recently helped a friend buy and install a Logitech Quickcam S7500 for an Ubuntu 8.04 system (Toshiba Satellite with usb 1.1)
[http://www.argos.co.uk/webapp/wcs/stores/servlet/Search?storeId=10001&catalogId=1500001501&langId=-1&searchTerms=S7500&Submit=GO+%3E](http://www.argos.co.uk/webapp/wcs/stores/servlet/Search?storeId=10001&catalogId=1500001501&langId=-1&searchTerms=S7500&Submit=GO+%3E)
and I plugged it into the usb socket, ran skype, used the Options menu in skype, video devices, 'Test' and it immediately worked. The webcam insitu microphone also worked fine, but I had to use Options, Audio devices, and choose a usb item, not the default item.

I have not tried any other webcam related application only skype.
I should perhaps add that the laptop has full multimedia capability installed, including the restricted stuff, with all the gstreamer stuff and dvd and w32codecs and the medibuntu repositories too. The skype I used came from the medibuntu repo. I mention all this because I do not know if some libraries or whatever, may be relevant with webcam use. streaming video?

good luck.

---

### Post by labinnsw on 2009-05-23
[Did you see this thread,]("http://ubuntuforums.org/showthread.php?t=642015") and if you did, what part of it are you having trouble with?

I have not been using Camorama. I am going to install it now to see if there are any issues.

---

### Post by labinnsw on 2009-05-23
It worked immediately. I only had to specify a directory to save the pictures.

---

