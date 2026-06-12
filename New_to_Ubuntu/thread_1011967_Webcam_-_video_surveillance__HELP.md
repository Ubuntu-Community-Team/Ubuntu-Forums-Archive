---
title: "Webcam - video surveillance / HELP"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by BassKozz on 2008-12-15
I am looking to purchase a webcam that I'd like to setup on my home Ubuntu NAS (on 24/7) so that it will record video when it detects motion, and upload that video to a remote FTP server (in case the person decides to steal my desktop).

So this is a two part question:
[LIST=1]
[*]What's the best webcam to buy for this sort of setup?
- I am not looking for anything fancy, i.e. I don't need pan/tilt/zoom support
- Are there any webcams that come with Ubuntu/Linux drivers, or Software?

If the camera comes with Linux software you can disregard the second question
[*]Is there Linux software available that can do this for me, and if so is there a list of compatible webcams?
[/LIST]
TiA,
-BassKozz

---

### Post by Bunx on 2008-12-15
I've read that Logitech webcams tend to have no problems with Linux. Do some research though. I have a Creative webcam and the generic drivers worked fine for it.

---

### Post by Hospadar on 2008-12-15
This might help:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

I don't know how exactly you'd work the motion sensing.
I'd assume you'd probably be writing a script or program to handle the actual recording and ftp-ing.
I very much doubt there is any linux software already out there to do just what you want to do.

Assuming you have a camera that works, and a motion sensor that you can detect the state of (either independently, or by virtue of the camera being on or off), I don't think it would be all that difficult. (routinely check if the camera is running, if so, record, then send to ftp, or better yet, use ftpfs/sftpfs to mount your remote location so as soon as you start recording data is landing on your remote server.

Which leads me to think that either 
a)
you'd need to find a camera with a motion sensor on it, and be able to detect when the motion sensor detects (if it just turns the camera on and off, that might not be so hard)

b)
you'd need a separate motion detector which you can detect the state of (I.E. motion/no motion) and control your camera accordingly.  Maybe you can find instructions online to build a motion sensor, or you can find a commercial motion sensor for not too much that has some linux support.
Maybe too you could hack a motion sensor light to turn your camera on and off (motion sensor triggered, power goes to solid state switch, turns on usb power).

---

### Post by BassKozz on 2008-12-15
This type of software has existed for WinBlows for years now, I remember having a web cam setup on my XP box a few years back that could do this flawlessly, I am surprised that such a thing doesn't exist for Ubuntu :(

---

### Post by BassKozz on 2008-12-15
Wait, I think I found it: [http://www.zoneminder.com](http://www.zoneminder.com)
:D

---

### Post by sleepingdragon on 2008-12-15
Logitech cameras work great, but you can download *motion* from the repos that streams video from a webcam over to a webpage (it has it's own internal web server). Motion will also fire up other commands when motion is detected (such as sending an e-mail).

---

### Post by BassKozz on 2008-12-15
> **sleepingdragon said:**
> Logitech cameras work great, but you can download *motion* from the repos that streams video from a webcam over to a webpage (it has it's own internal web server). Motion will also fire up other commands when motion is detected (such as sending an e-mail).

Would you happen to know the model number(s) that supports these features?

---

### Post by BDNiner on 2008-12-15
Yes Zoneminder is just of the CCTV options for linux. I would do a google search but at the last company i worked for there were 3 serious linux CCTV alternative that they were researching. One was zoneminder, i don't remember the other 2's names but i do remember that the PC would boot straight into the CCTV interface. so no linux desktop would load. This was great since they where supposed to be dedicated to recording video and sound.

I believe that Zoneminder works with a lot of dedicated capture cards like the ones from Avermedia. but that is only if you are going to go as far as running co-ax for the camera system.

[http://www.zoneminder.com/wiki/index.php/Supported_hardware#USB_Cameras](http://www.zoneminder.com/wiki/index.php/Supported_hardware#USB_Cameras)

This is the list of camera's that zoneminder supports.

---

### Post by BassKozz on 2008-12-15
> **BDNiner said:**
> Yes Zoneminder is just of the CCTV options for linux. I would do a google search but at the last company i worked for there were 3 serious linux CCTV alternative that they were researching. One was zoneminder, i don't remember the other 2's names but i do remember that the PC would boot straight into the CCTV interface. so no linux desktop would load. This was great since they where supposed to be dedicated to recording video and sound.

I believe that Zoneminder works with a lot of dedicated capture cards like the ones from Avermedia. but that is only if you are going to go as far as running co-ax for the camera system.

Yeah, after further review, this is a little bit more in-depth than I need...
I am only going to have 1 USB webcam connected, so I think I am looking for a simpler solution such as the one sleepingdragon mentioned...

---

### Post by sleepingdragon on 2008-12-15
You can find a list of compatible webcams [here]("http://ubuntuhcl.org/browse/search+webcams?category=33"). So long as the webcam works correctly, then *motion* will be able to use it for motion detection. *motion* uses anything that can run on the v4l (video 4 linux) drivers, which means that motion is independent of whatever webcam you buy and you can use the full features of *motion*. [Here is a list of motion's features]("http://www.lavrsen.dk/twiki/bin/view/Motion/MotionFeatureList")

---

### Post by BDNiner on 2008-12-15
yeah i guess it is kinda overkill for a single camera setup. Just be carefull, recording video can be pretty taxing on a video since it is encoding on the fly. Make sure to stop recording when you are sitting infront of the computer!

---

### Post by sleepingdragon on 2008-12-15
> **BDNiner said:**
> yeah i guess it is kinda overkill for a single camera setup. Just be carefull, recording video can be pretty taxing on a video since it is encoding on the fly. Make sure to stop recording when you are sitting infront of the computer!

*motion* is has a very small footprint when is comes to CPU demand. my 2.4 Celeron didn't see it go above 1% usage.

---

### Post by BDNiner on 2008-12-15
Really, wasn't the hard disk access slower since it is always trying to write data?

---

### Post by sleepingdragon on 2008-12-15
well, it can depend on the webcam resolution, and the fact that you're not trying to encode full 24-bit colour, it can make a considerable difference to CPU use. If you stick to the usual 320x240 resolution with 16-bit colour, you can get away with a slower CPU. You can also drop the framerate (there's no need for 25fps!), and the video bitrate can also be dropped due to the smaller resolution. Drive usage was hardly noticeable...

---

### Post by BDNiner on 2008-12-16
Yeah there is never a need for framerates that high. The DVR systems that i have worked with would divide 60fps between 8-12 cameras. But they were dedicate machines. I will hook up an old webcam and give motion a try. It seems like a good program for this situation.

---

### Post by Mattie03 on 2009-02-04
Video Surveillance Equipment should by now be common knowledge that the camera is primarily a tool of social control.
____________________________________
The used of [outdoor security system]("http://www.video-surveillance-guide.com/wireless-outdoor-surveillance-systems.htm").

---

### Post by dustigroove on 2009-11-17
> **Mattie03 said:**
> Video Surveillance Equipment should by now be common knowledge that the camera is primarily a tool of social control.

Your point?

---

### Post by ukripper on 2009-11-17
motion should be enough for your needs. [http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome](http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome)

Zoneminder will be full-fledged CCTV solution and is overkill in your situation.

---

