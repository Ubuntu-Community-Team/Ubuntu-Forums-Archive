---
title: "Webcam Issues"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by vertigopher on 2010-08-15
I recently attached a webcam I have, to see if it would work in ubuntu.  Now, I have two programs for recording from a webcam - wxcam and cheese.

When I start cheese, it does show a picture, but it is very very dark, with thin white lines of static.  When I start wxcam, there is no picture; rather, a solid green picture with occasional static.

Now, reading [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam) , I get the impression that the webcam *will* work, but with some setting and/or driver changes, but I'm not sure where to go from here.

If it helps, I get the following from lsusb:
**Bus 005 Device 003: ID 093a:2460 Pixart Imaging, Inc. Q-TEC WEBCAM 100**
Bus 005 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Any help would be greatly appreciated! :) Thanks!

---

### Post by davidmohammed on 2010-08-15
try the following

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each one

---

### Post by vertigopher on 2010-08-15
Ok.  When I test v4l2, I get the same video output that I'm seeing in cheese - very dark, some thin static.

Testing v4l, I get this message:
*Video for Linux (v4l): Could not get/set settings from/on resource.*

---

### Post by no2498 on 2010-08-15
in wxcam click settings start playing

cheese click edit, preference 

you can change settings in both programs

hope this helps some

---

### Post by davidmohammed on 2010-08-15
try launching wxcam with

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so wxcam

(check first that /usr/lib/libv4l/v4l1compat.so actually exists!)

---

### Post by vertigopher on 2010-08-15
Ok, /usr/lib/libv4l/v4l1compat.so did exist, so I ran that command in terminal. 

This is the kind of output I'm seeing out of wxcam and terminal - the "Not a JPEG file:" messages have been coming steadily out of terminal - they have been repeating with different codes for a few minutes now - I'm not sure if I was supposed to let this run a while or not.

---

### Post by davidmohammed on 2010-08-15
doesnt look good.  What happens if you try the same command but with cheese?

---

### Post by vertigopher on 2010-08-15
Well, none of the continuously repeating "Not a JPEG File:" messages, but the same camera output as I was seeing in cheese before - I can see the picture, but it is very dark, semi-greenish.

---

### Post by vertigopher on 2010-08-15
I do have the driver cd for windows, although I'm not sure if and how that would help here.  I am dual-booting with windows xp, and the webcam works fine there - however, I've been using ubuntu as my primary os, rarely booting into xp (and wouldn't mind keeping it that way! :D)

---

### Post by no2498 on 2010-08-16
in wxcam try the preference try rgb32 set the driver to auto

see if that helps

---

### Post by vertigopher on 2010-08-16
If I set it to auto, I get the following message:
[I]An error has occured during frame capture.
Please check the "frame format" options in the preferences menu.
[/I]
The only frame format settings in wxcam that do **not** give me that message are:
YUV420P - mainly green, lots of static, no picture
YUYV - same as above
RGB24 - solid black screen
MPEG - mostly solid green screen, occasional static

Also, there is a small green led on the webcam.  When either of these 4 modes are on wxcam, the led does light up - which would leads me to believe that hopefully something is going on between computer and camera.

---

### Post by no2498 on 2010-08-17
look in the add/remove program
see if you have gstreamer, good, bad, ugly, and 10  installed

---

### Post by vertigopher on 2010-08-17
Add/Remove Program?  I'm not sure exactly what you mean - Software Center or Synaptic?

And either way, if I search for gstreamer, a lot of options come up (particularly in synaptic).  As far as good, bad, ugly, and 10, I'm not sure what you mean?

---

### Post by earthpigg on 2010-08-17
> **vertigopher said:**
> Add/Remove Program?  I'm not sure exactly what you mean - Software Center or Synaptic?

he means software center. add/remove programs is the software center's grandfather, and used to hang out where software center now hangs out in the 'applications' menu.

anywho, here's what i've had luck with:

-install webcamstudio.
-start it, click around and see if you can get it to detect your webcam.
-leave webcamstudio open.
-other software ought to now be able to recognize & use the webcam.

i know it's wonky, but this has worked for me where all other methods failed for a given webcam. don't ask me how that works, don't ask me why that works, but it has for me.

---

### Post by vertigopher on 2010-08-17
No luck for me, unfortunately.  Webcamstudio lists the device as "CIF Single Chip", and the picture is the same quality that I'm seeing in cheese - very dark, slightly greenish, with thin horizontal lines of white static.  

Leaving that open didn't make any change to the results I got in wxcam or cheese.

---

### Post by earthpigg on 2010-08-18
> **vertigopher said:**
> No luck for me, unfortunately.  Webcamstudio lists the device as "CIF Single Chip", and the picture is the same quality that I'm seeing in cheese - very dark, slightly greenish, with thin horizontal lines of white static.  

got it working in studio? good.

on the top, click controls.

select the 'contrast' effect and click the little right arrow.

click on 'contrast' over on the right.

adjust contrast and brightness.

that ought to take care of it being to dark.

next, add the 'RGB' filter. RGB stands for red, green, and blue. adjust sliders.

please share results.

---

### Post by vertigopher on 2010-08-18
No luck - it just doesn't seem to be outputting something that's close enough for me to fix with contrast/brightness.  Here's about as good as I could get it - I can make out my glasses, and a tv antenna in the background, but that's about it.  Very useful in case I need to give any anonymous, garbled voice tv interviews :D, but not for much else.

---

### Post by earthpigg on 2010-08-18
Oh. Turn off the bright light behind you, and put a lamp on your desk. Seriously.

You look the same as if I took a picture of you standing directly in front of the bright 4 PM sun.

The camera and brightest source of light need to be next to each other, and you not in between them.

---

### Post by vertigopher on 2010-08-19
True enough - that was my mistake for trying it with my window behind me. :D

However, even now, with no sunlight coming through the window - I can see me, but the picture quality is greatly reduced compared to what I should be seeing.  The contrast and brightness settings do help, though.  I'm not sure if it's a fair comparison or not, but when I dual boot into windows xp, it is a much better picture.  

It's much better however - I'm really looking to primarily use my webcam as a sort of document camera.  I'm having the same problem in webcamstudio that I have with cheese, however, in that the frame rate is very low when I hit record... so that doesn't help matters much either. 

Thanks for the help so far! I appreciate it! :D

---

### Post by no2498 on 2010-08-19
try this program wxcam it works better for me
read and install all the page tells you to


[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

it has setting in it also

---

### Post by vertigopher on 2010-08-22
I already have wxcam installed - it won't work for me either.  

I just tested the webcam on skype as well - same output.  Very dark, staticy, green.

I saw something on the ubuntu community webcam page about EasyCam2, but it won't install for me.  The blog it refers to appears to be down.

edit: I feel like I'm getting closer.. I found a few posts from people who had problems with the same kind of webcam I do - [http://ubuntuforums.org/showthread.php?t=75284&highlight=spca5xx](http://ubuntuforums.org/showthread.php?t=75284&highlight=spca5xx) - this post seemed to have helped them, but it was written in 2005 :) I'm not sure if that will still work in 10.04.  

Also, my webcam appears in this list - [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) - but I'm not sure how to install the drivers necessary.

Either that or I'm way off track :) Thanks for any ideas!

---

### Post by vertigopher on 2010-08-22
In all reality, skype would probably be the thing I would like to work the most with this webcam right now.  Not sure if that helps or not.

---

### Post by davidmohammed on 2010-08-22
you could try the [latest 2.6.35 kernel]("https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds") to see if it includes any fixes for your webcam.

If it doesnt work, you could always just remove the kernel [instructions in that link OR install ubuntu-tweak.  Reboot using grub to boot from a lucid kernel (2.6.32) and use ubuntu-tweak to remove the 2.6.35 kernel].

---

### Post by vertigopher on 2010-08-22
Ok, I'm game to give it a shot.  I'm having a problem with the 710k header file at [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35.3-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35.3-maverick/)  - when I open package installer, it gives me a message saying "Error: Dependency is not satisfiable: linux-headers-2.6.35-02063503" and won't let me install it.  The other two packages do not give me that error, but I wanted to make sure that I had to install all three together before moving forward.[URL="http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.35.3-maverick/linux-headers-2.6.35-02063503-generic_2.6.35-02063503.201008211321_i386.deb"]
[/URL]

---

### Post by davidmohammed on 2010-08-22
yes - need to install all three - the error message basically means you need to install the headers deb first before the other two.

---

### Post by vertigopher on 2010-08-22
Ok - new kernel successfully installed, and booted into it from grub.  no change in video, however - same output in cheese and skype.

---

### Post by davidmohammed on 2010-08-22
thats a shame.  Looks like your webcam isnt going to work for you.  Spend a tenner on ebay to get a better linux compatible...!

Dont forget to install ubuntu-tweak to remove the 2.6.35 kernel.

---

### Post by vertigopher on 2010-08-22
Unfortunately, that's the conclusion I was beginning to reach - maybe I should have checked the compatibility list BEFORE buying the camera :p 

Oh well - thanks for the help! :D

---

### Post by zazootheparrot on 2010-08-24
> **davidmohammed said:**
> try the following

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each one

I have a problem with my webcam as well and I have already tired what you've said. 
For the V4L1 it gives the following message: 
Video for Linux (v4l): Device "/dev/video0" does not exist.

and for the V4L2 :
Video for Linux 2 (v4l2): Cannot identify device '/dev/video0'

Could you please tell me what to do next?

Thanks

---

### Post by no2498 on 2010-08-24
[http://www.google.com/search?q=Video+for+Linux+%28v4l%29%3A+Device+%22%2Fdev%2Fvideo0%22+does+not+exist.&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=Video+for+Linux+%28v4l%29%3A+Device+%22%2Fdev%2Fvideo0%22+does+not+exist.&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)


[http://www.google.com/search?q=Video+for+Linux+2+%28v4l2%29%3A+Cannot+identify+device+%27%2Fdev%2Fvideo0%27.&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=Video+for+Linux+2+%28v4l2%29%3A+Cannot+identify+device+%27%2Fdev%2Fvideo0%27.&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by sam-bo on 2010-08-24
My built-in webcam on hp dv9000 is not functional.  The thing is that skype default and only setting is "/dev/video1" which is used by the webcam.  How do I open that port to make way for another webcam?

sam

---

### Post by glococo on 2010-09-02
Same issue,

I have upgraded my kernel from ppa repository with 2.6.35.4 and now stop working.

0ac8:303b Z-Star Microelectronics Corp. ZC0303 Webcam

With 2.6.32.24 it was working flawless.
With 2.6.35.4 not work. Black image.

---

### Post by glococo on 2010-09-02
With GUVCViewer:

Error message on console:
Could not grab image (select timeout): Resource temporarily unavailable
Could not grab image (select timeout): Resource temporarily unavailable
Could not grab image (select timeout): Resource temporarily unavailable
..
..

Kernel bug ?
I tried also with 3 PC, and 2 webcams.

Bump !

---

