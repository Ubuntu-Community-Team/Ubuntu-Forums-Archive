---
title: "Webcam and Gyachi"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2010-02-17
Hy all!

I wonder if you can help me make my on board webcam to work with gyachi. It's working OK with skype and cheese, but when I try to use it with gyachy I get:
```
Gyachi (webcam broadcaster)
Error while capturing initial image
```
This is my lsusb:
```
Bus 002 Device 004: ID 05e1:0501 Syntek Semiconductor Co., Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0b05:1712 ASUSTek Computer, Inc. 
Bus 001 Device 002: ID 046d:c019 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
```
From my searches I understand that my camera is a little older and it's working through v4l (video4linux) and this is not supported by gyachi.
I know I should install a package called flashcam, but I'm stuck:
```
troll@my-precious:~$ cd /home/troll/Desktop/flashcam-1.4.4
troll@my-precious:~/Desktop/flashcam-1.4.4$ make
cc -g -o flashcam flashcam.c
flashcam.c: In function &#8216;send_image&#8217;:
flashcam.c:199: error: &#8216;V4L2_PIX_FMT_SGBRG8&#8217; undeclared (first use in this function)
flashcam.c:199: error: (Each undeclared identifier is reported only once
flashcam.c:199: error: for each function it appears in.)
make: *** [flashcam] Error 1
```
What do I do from here?

---

### Post by Troll_the_Great on 2010-02-18
Bump!

---

### Post by Troll_the_Great on 2010-02-19
Bump!

---

### Post by loell on 2010-02-19
not sure if this solution would even work, but maybe worth a try..

try pre-loading vl41compat

```
 LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so gyachi
```

---

### Post by Troll_the_Great on 2010-02-19
> **loell said:**
> not sure if this solution would even work, but maybe worth a try..

try pre-loading vl41compat

```
 LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so gyachi
```

If I run this command I get:
```
troll@my-precious:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so gyachi
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
```

EDIT: I don't know if this is relevant, but if I start gyachi via command line and then try to start the webcam, in the terminal I get:
```
(gyachi-upload:27737): Gtk-CRITICAL **: gtk_widget_set_size_request: assertion `height >= -1' failed
```

---

### Post by Troll_the_Great on 2010-02-21
Bump!

---

### Post by Troll_the_Great on 2010-02-22
Bump!

---

### Post by d3v1150m471c on 2010-02-22
So does the webcam work now?

---

### Post by Troll_the_Great on 2010-02-22
> **d3v1150m471c said:**
> So does the webcam work now?

I don't understand what you mean... If my webcam was working, would I have still bumping?!
Like I said, my webcam is working with cheese and skype, but I can't get it to work with gyachi.

---

### Post by Troll_the_Great on 2010-02-23
Bump!

---

### Post by loell on 2010-02-23
/me don't have anymore ideas. ;)

---

### Post by no2498 on 2010-02-23
cheese is still breaking things
open a terminal  type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2
click the bottom test button
after it comes on do NOT open cheese
an try the program you would like to see it on
did this help ?

---

### Post by Troll_the_Great on 2010-02-25
If I try this I get the error message:
```
An error occurred at 'ioctl VIDIOCSPICT'
Could not set camera properties
```

---

### Post by no2498 on 2010-02-25
was the error for gstreamer-properties
or the program your trying to use cam in

---

### Post by Troll_the_Great on 2010-02-26
> **no2498 said:**
> was the error for gstreamer-properties
or the program your trying to use cam in

The error was in gyachi.

---

### Post by Troll_the_Great on 2010-02-27
Bump!

---

### Post by Troll_the_Great on 2010-02-28
Bump!

---

### Post by fr3ak.m3 on 2010-03-01
> **Troll_the_Great said:**
> Hy all!
From my searches I understand that my camera is a little older and it's working through v4l (video4linux) and this is not supported by gyachi.


If your webcam is being recognized by skype means that you don't need to load the Video4Linux1 driver.

I hae a v4l1 webcam and it works fine with gyachi and cheese but in case of Skype I had to forcefully load the v4l1 driver.

Mate the problem isn't as you think. Start searching new thingi.....

---

### Post by Troll_the_Great on 2010-03-01
> **fr3ak.m3 said:**
> If your webcam is being recognized by skype means that you don't need to load the Video4Linux1 driver.

I hae a v4l1 webcam and it works fine with gyachi and cheese but in case of Skype I had to forcefully load the v4l1 driver.

Mate the problem isn't as you think. Start searching new thingi.....

So, what is my problem then? Why isn't my camera working with gyachi?

---

### Post by DrMelon on 2010-03-01
Maybe you need to specify a video device? Look at the man pages for Gyachi.

---

### Post by Troll_the_Great on 2010-03-01
> **DrMelon said:**
> Maybe you need to specify a video device? Look at the man pages for Gyachi.

Under gyachi options, the video device is /dev/video0. Should I do something different?

---

### Post by no2498 on 2010-03-02
ok from what i see you need to find the how to make the preload file
every one that uses skype needs it 
or you need to run it every time you would like to use your webcam
look for skype     help

---

### Post by Troll_the_Great on 2010-03-04
> **no2498 said:**
> ok from what i see you need to find the how to make the preload file
every one that uses skype needs it 
or you need to run it every time you would like to use your webcam
look for skype     help

I'm sorry mate, but I don't have any ideea on how to "preload" anything. If someone could help I would be grateful.

---

### Post by spiderbatdad on 2010-03-04
The command was provided by loell earlier in this thread:
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so gyachi
``` Make sure gyachi isnt already running.
and it works fine on my machine. This is gyach-e Improved version 1.2.2

I have seen that error in previous kernels when using the preload command and I'm not sure why...seems like using sudo cured it for a while, but that isn't the problem for you I think...

---

### Post by no2498 on 2010-03-04
there is a make file he needs to make so this will work
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so gyachi

i have seen it
its in 1 of the skype how to dos

---

### Post by Troll_the_Great on 2010-03-05
> **spiderbatdad said:**
> The command was provided by loell earlier in this thread:
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so gyachi
``` Make sure gyachi isnt already running.
and it works fine on my machine. This is gyach-e Improved version 1.2.2

I have seen that error in previous kernels when using the preload command and I'm not sure why...seems like using sudo cured it for a while, but that isn't the problem for you I think...

This command is not working, and I said earlier what error I get when I try to run it. I think I will never manage to have webcam with gyachi... :((

---

### Post by no2498 on 2010-03-05
this will not work lib/libv4l/v4l1compat

we use v4l2 now days
you need a converter v4l2 to v4l1

i have only seen it 1 time
and im at a loss for where sorry

---

### Post by Troll_the_Great on 2010-03-07
> **no2498 said:**
> this will not work lib/libv4l/v4l1compat

we use v4l2 now days
you need a converter v4l2 to v4l1

i have only seen it 1 time
and im at a loss for where sorry

Thanks anyway for your time. Maybe somebody else ca help?

---

### Post by spiderbatdad on 2010-03-07
```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so gyachi
```

---

### Post by Troll_the_Great on 2010-03-07
> **spiderbatdad said:**
> ```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so gyachi
```

Thanks for your time, but when I try to run the code I get:
```
ERROR: ld.so: object '/usr/lib/libv4l/v4l2convert.so' from LD_PRELOAD cannot be preloaded: ignored.
``` :(

---

### Post by Troll_the_Great on 2010-03-09
Bump!

---

### Post by loell on 2010-03-09
I can't believe you haven't given up, heheh.. :D

anyway,  i noticed that you can't preload, if you can't preload, most likely your ubuntu install is already broke, probably reinstall then do the preload?

---

### Post by Troll_the_Great on 2010-03-10
> **loell said:**
> I can't believe you haven't given up, heheh.. :D

anyway,  i noticed that you can't preload, if you can't preload, most likely your ubuntu install is already broke, probably reinstall then do the preload?

I'm very persistent :D
As for reinstalling, I think I will wait for the next LTS to arrive in april, and then reinstall.

---

### Post by Troll_the_Great on 2010-03-11
OK guys, last try. If I don't get an answer now, I will wait till Lynx comes and hopefully solves my problem.

---

### Post by no2498 on 2010-03-11
i give you my best
you need to look for the skype, so
i seen 1 that lets you make a file for the the whole computer
and as i said i only seen it 1 time

---

### Post by no2498 on 2010-03-12
open the cam in aa diff program an set the size smaller
skype if you can and cheese
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so (you can do this for all programs

---

### Post by no2498 on 2010-03-12
do you have the flash player from adobe loaded
and the extras medubuntu's

---

### Post by kracheck on 2010-11-16
I'm using a program called WebcamStudio ([http://www.ws4gl.org/](http://www.ws4gl.org/)) to stream my video to any other video capturing program like aMSN or Adobe Flash webcam embedded in webpages. You could try it with Gyachi. Launch WebcamStudio and see if you can select it as a 'device' in Gyachi. If you can it should stream your video to Gyachi since Gyachi will think of the WebcamStudio program as a webcam, in this case a virtual webcam.

Unfortunately it's a very processor-intensive program so maybe you might try something else first.  I must admit it didn't work for me be but I would have preferred that solution since it's less workload for your computer.  The steps can be found here : 
[http://www.swift-tools.net/Flashcam/](http://www.swift-tools.net/Flashcam/)

---

### Post by no2498 on 2010-11-16
kracheck

look in the cheese help faq's

The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    
5.2.&#8195;I have a Mac with iSight and a ATI graphics card, and the colors are weird.


      This is a problem with the ATI graphics card, though there is a work around.
      Change the video-output to custom and insert the following: "ffmpegcolorspace !
      video/x-raw-yuv,format=(fourcc)YV12 ! ffmpegcolorspace ! xvimagesink".
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and select custom from the drop down menu.

---

### Post by kracheck on 2010-11-17
Hi no2498,

Just to put things in perspective, I'm not a Gyachi user but I have solved quite a lot of my webcam problems, especially those with flash, through the use of WebcamStudio. I suggested this program as a possible (trial and error) solution to the problem presented by the person starting the thread. I added that the use of WebcamStudio is processor incentive.

I thank you for your tip that works for cheese and you are right, maybe this might just work for WebcamStudio too ! I tried your suggestion, fired up gstreamer-properties in Ubuntu 10.04 and under the video tap I changed my plugin for default output from 'Autodetect' to "X Window System (X11/XShm/Xv)'. Unfortunately this didn't affect the intensive use of the processor.

I'm not experiencing any problems with my video card and my video isn't sluggish. The fact that WebcamStudio is processor intensive is a known issue explained by the projectmanager of WebcamStudio here : [http://webcamstudio.3802688.n2.nabble.com/WebcamStudio-is-really-processor-intensive-offload-to-CPU-td3997484.html](http://webcamstudio.3802688.n2.nabble.com/WebcamStudio-is-really-processor-intensive-offload-to-CPU-td3997484.html)

---

