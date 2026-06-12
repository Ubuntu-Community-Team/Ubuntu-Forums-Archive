---
title: "Blank screen while playing movies"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by htzzz on 2009-06-24
I got blank screen and system down while I try to play any avi files(using mplayer)...
I'm running 8.04 on lenovo R400, ATI 3400 graphics
 
Thank u for ur help!

---

### Post by pedro_orange on 2009-06-24
Do you have all the necessary codecs installed?

When I do a fresh install I like to run:

```
sudo apt-get install ubuntu-restricted-extras
```

This installs all codecs and flash etc. All in one swift command.

---

### Post by htzzz on 2009-06-24
Thank you pedro.
However, it doesnt solve my problem.
The same problem occurs when i run hardware testing in the video session, is it something wrong with my graphics? i m running on lenovo thinkpad r400, ati 3400

---

### Post by htzzz on 2009-06-24
is it a problem of my graphic driver? how can i reconfigure it?

---

### Post by carml on 2009-06-24
What kind of video driver are you using? The proprietary ones or the ones you find under Add/Remove->System Tools?

---

### Post by htzzz on 2009-06-24
I did not install any drivers, since the widescreen is working, i guess i m using the default one coming with the cd...how can i check?

---

### Post by carml on 2009-06-24
The idea I have at the moment is System->Administration->Hardware Driver if you see "In use" near to Ati Accelerated Graphic Driver,you're using the proprietary ones. :)

---

### Post by LubindaMaim on 2009-06-24
Press 'Alt+F2'and run 'gstreamer-properties'. 
In the Window that pops up select the Video tab. Under Default Output in the 'Plugins:' part select 'X Window System (X11/XShm/Xv)' then under 'Device:', Look for 'Radeon Textured Video' select it, then try playing a video.
Hope this works, my ati card's different but its worth a shot.

---

### Post by htzzz on 2009-06-24
OK, before I install anything, I open hardware drivers and see 'ATI accelerated graphics driver' inside, it was disabled by default. If I enable it, after reboot, the grahical interface cannot be loaded.

Then I reboot and enter the recovery mode, chose repair package and let it run...

This time I was able to load graphical interface and I installed ATI driver from this site:
[http://www.techspot.com/drivers/driver/file/download/11436/](http://www.techspot.com/drivers/driver/file/download/11436/)
After that, I reboot. the video is working now, but the driver seems not... I was prompted saying the system is running in low graphics. the resolution is ok, but the color is quite unnatural.

I am getting quite confused here, did I install any driver, is it working or not?

btw, I tried gstreamer-properties, there's nothing in the device menu...

---

