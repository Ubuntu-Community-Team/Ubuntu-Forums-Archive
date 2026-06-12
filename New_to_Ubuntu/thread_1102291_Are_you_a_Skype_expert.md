---
title: "Are you a Skype expert?"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by lentomies on 2009-03-21
Does anyone know how to get Skype working if the Webcam is producing a stream???

Thanks!

---

### Post by lentomies on 2009-03-21
How come my web came doesn't work?

---

### Post by LowSky on 2009-03-21
How can we help you if we dont know the hardware exactly, saying webcam means nothing, what model is thr camera in question?

---

### Post by khelben1979 on 2009-03-21
```
sudo lsusb
```
will show what camera you have b.t.w.

---

### Post by HermanAB on 2009-03-21
If your webcam s in use by another program then Skype will not be able to run.

Cheers,

Herman

---

### Post by lentomies on 2009-03-21
Hello all,

Many apologies for my vagueness

I recently completed a fresh 8.04 install. Now I would like to install the Logitech QuickCam model 961462-0403 for use with Skype.

I have another PC running 8.04 and it uses the exact same model webcam. When I installed it everything was plug and play and Skype worked perfectly.

However, on this new machine Skype doesn't even show the video. So I'm lost as to what is wrong! I will add that I did add the SABRENT Philips saa7130 TV turner card. This was installed first than I added Skype. Maybe that screwed up some ordering?

Any help to resolve this matter is appreciated. Thank You!

Does this help?

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:08af Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000

---

### Post by khelben1979 on 2009-03-21
By looking [at this page]("http://www.seismo.ethz.ch/linux/webcam.html"), it seems that you need to create a module for that webcam from the Linux kernel.

If you know what the module is named and that it's already installed in your Linux kernel, then you just need to run it:
```
sudo modprobe [module of the webcam]
```
or
```
sudo insmod [module of the webcam]
```

*I suspect that this isn't enough, but it may give you a start in the right direction.*

---

### Post by suomalainen on 2009-03-21
No, this can't be it because last 8.04 everything was plug and play. Why should this webcam be treated any differently now??????

However, on this new machine Skype doesn't even show the video. So I'm lost as to what is wrong! I will add that I did add the SABRENT Philips saa7130 TV turner card. This was installed first. Maybe that screwed up some ordering?

I would like to note that I installed my tv turner first. I have also noticed the following:

When I open "tv time" I can see the different tv channels. THEN when I open Skype, KEEPING TV TIME OPEN TOOO, and go to Options>Video Devices>Test THEN I can see my video in SKYPE. 

Now what do you think?

---

### Post by lisati on 2009-03-21
> **lentomies said:**
> Hello all,

Many apologies for my vagueness

I recently completed a fresh 8.04 install. Now I would like to install the Logitech QuickCam model 961462-0403 for use with Skype.

I have another PC running 8.04 and it uses the exact same model webcam. When I installed it everything was plug and play and Skype worked perfectly.

However, on this new machine Skype doesn't even show the video. So I'm lost as to what is wrong! I will add that I did add the SABRENT Philips saa7130 TV turner card. This was installed first than I added Skype. Maybe that screwed up some ordering?

Any help to resolve this matter is appreciated. Thank You!

Does this help?

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:08af Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000
I'd be surprised if having more than one video capture device would make a difference. I don't currently have skype installed on the copy of Ubuntu I'm currently running (making it harder to double check) but I seem to recall an option somewhere for selecting video source - I'm pretty sure that the Windows version of Skype I've used on this machine has one.

---

### Post by suomalainen on 2009-03-21
Your correct lisati!

When in Skype I can go to:

Options>Video Devices>

AND here I can choose between my webcam or the tv turner. I'm smart enough to know to choose webcam i.e. Logitech QuickCam Cool (/dev/video1)

F.Y.I. my TV Turner is Sabrent SBT-TVFM (saa7130)(/dev/video0)

I hope someone knows whats going on here. I need this solved.....

---

### Post by mac71 on 2009-03-21
Hi, open synaptic and remove skype. Close it and then open a terminal and do:

 ```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update
```

```
sudo apt-get install medibuntu-keyring
```

```
sudo apt-get update
```

```
sudo apt-get install skype
```

That should get it working- it did for me with my logitec quickcam communicate STX.

---

### Post by lentomies on 2009-03-21
Thanks mac71 but this didn't work either.

Somehow I need to get Skype to see this webcam and use it. The strange thing is that if I open tv time then the Skype webcam will work but not before.

I think somewhere along the line there is a conflict of some sort...

---

### Post by lentomies on 2009-03-21
Hello Everyone,

I don't know if the following information means anything but when Skype is in the task bar and I do a right click on it and choose "options"--> "Video Devices" the green light on the webcam comes on. When I click on test the demo screen just stays black. When I close Skype the green light goes out.

If I launch TVTime and then try to see my Skype test video it will work.

But I need Skype working without TVTIME open!

Can someone help me???

Thanks!!!!

---

### Post by lentomies on 2009-03-22
bump

---

### Post by lentomies on 2009-03-22
Ubunteros,

I was under the impression that when I test my webcam under Options-->Video Devices That if my picture/video isn't seen then the person on the other end will not see it either.

However, after a test with second PC it can be determined that a video from the webcam is being transmitted by Skype although the "sender" may not be able to see their own picture/video during a conversation. Regardless, the "Receiver" does see the video!

Obviously, the sender is suppose to see their picture so they know, for example, that the webcam is positioned correctly.

How can I make Skype see the webcam so that a "live" video from this webcam is produced for the sender???

Thank you!!!

Thank you

---

### Post by lentomies on 2009-03-23
Anyone know how to answer my question in post # 15??

Thanks!!!

---

### Post by khelben1979 on 2009-03-23
I don't know how to help you, but I suggest that you register [here]("http://forum.skype.com/index.php?showforum=18") on the Skype forum.

I think that you have a better probability on getting faster and better support on this matter over there.

---

### Post by suomalainen on 2009-03-23
Hej khelben1979,

I'll take your advice and see what happens.? Just have to be careful because the mods get touchy when you post the same question on multiple forums...

---

### Post by khelben1979 on 2009-03-23
> **suomalainen said:**
> Hej khelben1979,

I'll take your advice and see what happens.? Just have to be careful because the mods get touchy when you post the same question on multiple forums...

You also have the possibility to search their archives.

---

### Post by lentomies on 2009-03-23
Ubunteros, below is a revised description of my issue.

Synopsis:

At issue is the Skype Video Screen. Currently it is unable to display live video streams. In two specidic instances, Skype is unable to stream live video feeds via webcam when:

1) In a live call and the "Start My Video" option has been selected
2) Under the "Video Devices" option a live video stream "TEST" cannot be successfully performed.

A work around has been discovered. However, it isn't a pratical method to follow. The Skype program itself should operate and perform flawlessly as intended.

It is hoped that through the epertise and knowledge of those here that the Skype Video Screen can be restored to its proper functionality.


Please consider the following:


Software/Hardware being used:
Linux-Ubuntu 8.04 LTS
Skype version 2.0.0.72
HP AMD model a500n Additional info available at:
[http://h10025.www1.hp.com/ewfrf/wc/product?product=405440&lc=en&cc=us&dlc=en&submit.y=0&submit.x=0&lang=en&cc=us](http://h10025.www1.hp.com/ewfrf/wc/product?product=405440&lc=en&cc=us&dlc=en&submit.y=0&submit.x=0&lang=en&cc=us)


Scenario 1

1. Applications ---> Internet ---> Skype
2. Right click on Skype icon in tool bar and choose: Options ---> Video Devices (See picture# 1)
3. Click on the "TEST" button over the black screen (See picture# 2")

IMPORTANT NOTE # 1:
At this point the "TEST" button disappears and the Skype test video screen remains black with no "live" video feed that can be seen.

IMPORTANT NOTE # 2:
If a Skype contact is online a call can be placed to that contact. However, When "Start My Video" is chosen a live video feed does not appear in the lower left hand corner of the Skype video screen. However, a live Skype video feed is being transmitted "live" from Skype to the Contacts computer although that live video feed isn't being properly displayed. THIS FEATURE NEEDS TO WORK SO THAT THE CALLER CAN POSITION THE WEBCAM CORRECTLY DURING A CALL.

4. Right click on Skype icon in tool bar and choose: Quit


Scenario 2

1. Applications ---> Internet ---> Skype
2. Applications ---> Sound & Video ---> TVtime Television Viewer
3. Set TVtime Television Viewer volume to zero (0).

ABOUT TVtime Television Viewer:
tvtime is a high quality television application for use with video capture cards on Linux systems. tvtime processes the input from a capture card and displays it on a computer monitor or projector. See: [http://tvtime.sourceforge.net/](http://tvtime.sourceforge.net/)

4. Go to Skype
5. Look for an online contact and make a call to that contact
6. Select "Start My Video"
7. A "live" Skype video feed appears on both the Contacts computer and the computer of the person originating the call. 

IMPORTANT NOTE # 3:
Within the Skype video screen appears both the contacts live video feed and the smaller video of the caller in the bottom left hand corner.

8. End the call with the contact
9. Right click on Skype icon in tool bar and choose: Options ---> Video Devices (See picture# 1)
10. Click on the "TEST" button over the black screen (See picture# 2")
11. Live "TEST" video stream appears (See picture# 3)


Scenario 3

1. Applications ---> Accesories ---> Terminal
2. Enter the following: gstreamer-properties
3. Terminal reports the following, see below, as the Multimedia Systems Selector program opens:

desk@desk-desktop:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
desk@desk-desktop:~$

4. Pictures 4 & 5 show the settings of the Multimedia Systems Selector program.


Scenario 4

1. Applications ---> Accesories ---> Terminal
2. Enter the following: lsusb
3. Terminal reports the following:

desk@desk-desktop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:08af Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000
desk@desk-desktop:~$

---

### Post by infamouskiller on 2009-06-14
This thread is amazing I run the Orbit AF and the Sabrant my problem is that SABRANT sucks and I have the same Phillips 7130 chip.

it constantly crashes skype I suggest a  haupergaunt 

I just use it for testing  a small studio but  I am not going with this chip its latency is horrid and picture. Get a  better capture card it will work and don't buy pinnacle products.

If you run manycam or webcammax take over the video feed skype can use it.

manycam is free.

[www.manycam.com](www.manycam.com) 

let the program control your  7130 video/cable feed and you can upload it to your camera feed to skype or stickcam or whatever your flavour is.

hope this helps.

Im a professional video FX artist and broadcaster so I been through all the solutions.

Im making a small Chroma studio on the I7 920 structure and a Cannon XL2.

I have a Q6600 Just doing the Camera Feed & Chroma. Then that pushes to the Control Room I7 machine. For Broadcast and SAT.

if you wanna check it out hit me a  pm.


I'm using the Orbit AF as a starter Camera ultimatly ending in a  XL2 theres just so much I can afford at a time putting together a studio and it being motorized helps my Editor.


The Orbit AF is the best cam on the market and broadcast in 720 which is a stable Format for everything.

---

