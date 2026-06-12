---
title: "Cheese Video is laggy"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by RichieB07 on 2011-02-05
I have an Acer Aspire 5520 with a built-in webcam, I also have an HP HD3100 webcam I use as well.  Whenever I try to record a video in Cheese, it's very laggy.  The audio is out of sync and the movements are jerky.  When I try it with the HP cam, it freezes Cheese completely.

Is there any way to fix this?  And if not, what could I use instead?


Specs for my computer:
160 GB HDD
3GB DDR2 RAM
NVidia 7100m/610 CPU/GPU chipset

---

### Post by madjr on 2011-02-05
does it lag also on video chat?

---

### Post by stmiller on 2011-02-05
Try wxCam:

[http://sourceforge.net/projects/wxcam/files/wxcam/1.0.7/wxcam_1.0.7_i386.deb/download](http://sourceforge.net/projects/wxcam/files/wxcam/1.0.7/wxcam_1.0.7_i386.deb/download)

?

I've had more success with it than cheese for recording video on my netbook.

---

### Post by rcayea on 2011-02-05
I had the same issue with my Toshiba built-in webcam. It came down to having the correct driver installed and when I did, it was still choppy. I bought a Logitech C210 and installed the correct video capture software and it works like a charm.

---

### Post by RichieB07 on 2011-02-06
> **madjr said:**
> does it lag also on video chat?

No, not with either camera.  It's just with Cheese.

> **stmiller said:**
> Try wxCam:

[http://sourceforge.net/projects/wxcam/files/wxcam/1.0.7/wxcam_1.0.7_i386.deb/download](http://sourceforge.net/projects/wxcam/files/wxcam/1.0.7/wxcam_1.0.7_i386.deb/download)

?

I've had more success with it than cheese for recording video on my netbook.

I saw that before, but I'm still to Ubuntu and not entirely sure how to configure that stuff.  I know you have to download something that automatically configures it for you.

> **rcayea said:**
> I had the same issue with my Toshiba built-in webcam. It came down to having the correct driver installed and when I did, it was still choppy. I bought a Logitech C210 and installed the correct video capture software and it works like a charm.

How'd you find the correct video capture software?

---

### Post by no2498 on 2011-02-06
you can also get wxcam from get deb in a deb/file



[http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/)


i hope its still there

---

### Post by RichieB07 on 2011-02-06
> **no2498 said:**
> you can also get wxcam from get deb in a deb/file



[http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/)


i hope its still there

It's not on there anymore.

---

### Post by no2498 on 2011-02-06
[http://forum.eeeuser.com/viewtopic.php?id=19482](http://forum.eeeuser.com/viewtopic.php?id=19482)


he is saying [http://sourceforge.net/projects/wxcam/](http://sourceforge.net/projects/wxcam/)
has it in a deb file too

---

### Post by madjr on 2011-02-07
you could also try guvcview

[http://www.omgubuntu.co.uk/2011/02/webcam-linux/](http://www.omgubuntu.co.uk/2011/02/webcam-linux/)

---

### Post by sijar on 2011-02-08
I finally got **Guvcview**, a great software for Logitech webcam and it does all the stuff that one wants out of it.
But I'm not satisfy with the video recording,
 **video and audio out of synchronisation also video seems to be in slow motion**. 
Please help so that I can tweak in and get a good video recording with the webcam.
Below is the log of **Guvcview**  
------------------------------------------------------------------------------- 
guvcview 1.4.1 
video_device: /dev/video0 
vid_sleep: 0 
cap_meth: 1 
resolution: 640 x 480 
windowsize: 1024 x 715 
vert pane: 578 
spin behavior: 0 
mode: mjpg 
fps: 1/25 
Display Fps: 0 
bpp: 0 
hwaccel: 1 
avi_format: 4 
sound: 1 
sound Device: 4 
sound samp rate: 0 
sound Channels: 0 
Sound delay: 0 nanosec 
Sound Format: 85  
Pan Step: 2 degrees 
Tilt Step: 2 degrees 
Video Filter Flags: 0 
image inc: 0 
profile(default):/home/sijar/default.gpfl 
starting portaudio... 
bt_audio_service_open: connect() failed: Connection refused (111) 
bt_audio_service_open: connect() failed: Connection refused (111) 
bt_audio_service_open: connect() failed: Connection refused (111) 
bt_audio_service_open: connect() failed: Connection refused (111) 
Cannot connect to server socket err = No such file or directory 
Cannot connect to server socket 
jack server is not running or cannot be started 
language catalog=> dir:/usr/share/locale type:UTF-8 lang:en_US.utf8 cat:guvcview.mo 
mjpg: setting format to 1196444237 
capture method = 1 
video device: /dev/video0  
libv4lconvert: warning more framesizes then I can handle! 
libv4lconvert: warning more framesizes then I can handle! 
/dev/video0 - device 1 
libv4lconvert: warning more framesizes then I can handle! 
libv4lconvert: warning more framesizes then I can handle! 
Init. UVC Camera (046d:0825) (location: usb-0000:00:1d.7-5) 
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' } 
{ discrete: width = 640, height = 480 } Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5,  
{ discrete: width = 160, height = 120 } Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5,  
{ discrete: width = 176, height = 144 } Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5,  
{ discrete: width = 320, height = 176 } Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5,  
{ discrete: width = 320, height = 240 } Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5,  
{ discrete: width = 352, height = 288 } Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5,  
{ discrete: width = 432, height = 240 } Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5,  
{ discrete: width = 544, height = 288 } Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5,  
{ discrete: width = 640, height = 360 } Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
  
... repeats a couple of times ...
  
vid:046d  
pid:0825  
driver:uvcvideo 
Adding control for Pan (relative) 
UVCIOC_CTRL_ADD - Error: Operation not permitted 
checking format: 1196444237 
VIDIOC_G_COMP:: Invalid argument compression control not supported 
 fps is set to 1/25  
drawing controls 
control[0]: 0x980900  Brightness, 0:255:1, default 128 
control[0]: 0x980901  Contrast, 0:255:1, default 32 
control[0]: 0x980902  Saturation, 0:255:1, default 32 
control[0]: 0x98090c  White Balance Temperature, Auto, 0:1:1, default 1 
control[0]: 0x980913  Gain, 0:255:1, default 0 
control[0]: 0x980918  Power Line Frequency, 0:2:1, default 2 
control[0]: 0x98091a  White Balance Temperature, 0:10000:10, default 4000 
control[0]: 0x98091b  Sharpness, 0:255:1, default 24 
control[0]: 0x98091c  Backlight Compensation, 0:1:1, default 1 
control[0]: 0x9a0901  Exposure, Auto, 0:3:1, default 3 
control[0]: 0x9a0902  Exposure (Absolute), 1:10000:1, default 166 
control[0]: 0x9a0903  Exposure, Auto Priority, 0:1:1, default 0 
resolutions of format(2) = 19  
frame rates of 1º resolution=6  
Def. Res: 0  numb. fps:6 
---------------------------------------  
device #0 
Name                        = Intel 82801DB-ICH4: Intel 82801DB-ICH4 (hw:0,0) 
Host API                    = ALSA 
Max inputs = 2, Max outputs = 2 
Def. low input latency   =    0.012 
Def. low output latency  =    0.012 
Def. high input latency  =    0.046 
Def. high output latency =    0.046 
Def. sample rate         = 44100.00 
--------------------------------------- 
device #1 
Name                     = Intel 82801DB-ICH4: Intel 82801DB-ICH4 - MIC ADC (hw:0,1) 
Host API                 = ALSA 
Max inputs = 2, Max outputs = 0 
Def. low input latency   =    0.011 
Def. low output latency  =   -1.000 
Def. high input latency  =    0.043 
Def. high output latency =   -1.000 
Def. sample rate         = 48000.00 
---------------------------------------  
device #2 
Name                     = Intel 82801DB-ICH4: Intel 82801DB-ICH4 - MIC2 ADC (hw:0,2) 
Host API                 = ALSA 
Max inputs = 2, Max outputs = 0 
Def. low input latency   =    0.011 
Def. low output latency  =   -1.000 
Def. high input latency  =    0.043 
 Def. high output latency =   -1.000 
 Def. sample rate         = 48000.00 
--------------------------------------- 
device #3 
Name                     = Intel 82801DB-ICH4: Intel 82801DB-ICH4 - ADC2 (hw:0,3) 
Host API                 = ALSA 
Max inputs = 2, Max outputs = 0 
Def. low input latency   =    0.011 
Def. low output latency  =   -1.000 
Def. high input latency  =    0.043 
Def. high output latency =   -1.000 
Def. sample rate         = 48000.00 
---------------------------------------  
device #4 
Name                     = Intel 82801DB-ICH4: Intel 82801DB-ICH4 - IEC958 (hw:0,4) 
Host API                 = ALSA 
Max inputs = 0, Max outputs = 2 
Def. low input latency   =   -1.000 
Def. low output latency  =    0.011 
Def. high input latency  =   -1.000 
Def. high output latency =    0.043 
Def. sample rate         = 48000.00 
--------------------------------------- 
device #5 
Name                     = USB Device 0x46d:0x825: USB Audio (hw:1,0) 
Host API                 = ALSA 
Max inputs = 1, Max outputs = 0 
Def. low input latency   =    0.011 
Def. low output latency  =   -1.000 
Def. high input latency  =    0.043 
Def. high output latency =   -1.000 
Def. sample rate         = 48000.00 
---------------------------------------  
device #6 
Name                     = front 
Host API                 = ALSA 
Max inputs = 0, Max outputs = 2 
Def. low input latency   =   -1.000 
Def. low output latency  =    0.012 
Def. high input latency  =   -1.000 
Def. high output latency =    0.046 
Def. sample rate         = 44100.00 
--------------------------------------- 
device #7 
Name                     = iec958 
Host API                 = ALSA 
Max inputs = 0, Max outputs = 2 
Def. low input latency   =   -1.000 
Def. low output latency  =    0.011 
Def. high input latency  =   -1.000 
Def. high output latency =    0.043 
Def. sample rate         = 48000.00 
---------------------------------------  
device #8 
Name                     = spdif 
Host API                 = ALSA 
Max inputs = 0, Max outputs = 2 
Def. low input latency   =   -1.000 
Def. low output latency  =    0.011 
Def. high input latency  =   -1.000 
Def. high output latency =    0.043 
Def. sample rate         = 48000.00 
---------------------------------------  
device #9 
Name                     = pulse 
Host API                 = ALSA 
Max inputs = 32, Max outputs = 32 
Def. low input latency   =    0.012 
Def. low output latency  =    0.012 
Def. high input latency  =    0.046 
Def. high output latency =    0.046 
Def. sample rate         = 44100.00 
---------------------------------------  
device #10 
Name                     = dmix 
Host API                 = ALSA 
Max inputs = 0, Max outputs = 2 
Def. low input latency   =   -1.000 
Def. low output latency  =    0.043 
Def. high input latency  =   -1.000 
Def. high output latency =    0.043 
Def. sample rate         = 48000.00 
---------------------------------------  
device #11 
[ Default Input, Default Output ] 
Name                     = default 
Host API                 = ALSA 
Max inputs = 32, Max outputs = 32 
Def. low input latency   =    0.012 
Def. low output latency  =    0.012 
Def. high input latency  =    0.046 
Def. high output latency =    0.046 
Def. sample rate         = 44100.00 
---------------------------------------------- 

SampleRate:0 Channels:0 
Video driver: x11 
A window manager is available 
VIDIOC_S_EXT_CTRLS for multiple controls failed (error -1)   using VIDIOC_S_CTRL for user class controls 
control(0x0098091a) "White Balance Temperature" failed to set (error -1) 
VIDIOC_S_EXT_CTRLS for multiple controls failed (error -1)  using VIDIOC_S_EXT_CTRLS on single controls for class: 0x009a0000 
control(0x009a0902) "Exposure (Absolute)" failed to set (error -1) 
VIDIOC_S_EXT_CTRLS for multiple controls failed (error -1) using VIDIOC_S_CTRL for user class controls 
control(0x0098091a) "White Balance Temperature" failed to set (error -1) 
VIDIOC_S_EXT_CTRLS for multiple controls failed (error -1) using VIDIOC_S_EXT_CTRLS on single controls for class: 0x009a0000 
control(0x009a0902) "Exposure (Absolute)" failed to set (error -1) 
Cap Video toggled: 1 
(/home/sijar/Videos/Webcam) 25371756K bytes free on a total of 39908968K (used: 36 %) treshold=51200K 
using audio codec: 0x0055 
Audio frame size is 1152 samples for selected codec 
IO thread started...OK 
[libx264 @ 0x8cbd8b0]using cpu capabilities: MMX2 SSE2 Cache64 
[libx264 @ 0x8cbd8b0]profile Baseline, level 3.0 
[libx264 @ 0x8cbd8b0]non-strictly-monotonic PTS 
shift sound by -9 ms 
shift sound by -9 ms 
shift sound by -9 ms 
AUDIO: droping audio data 
AUDIO: droping audio data 
AUDIO: droping audio data 
AUDIO: droping audio data 
AUDIO: droping audio data
  
... repeats a couple of times ...
  
AUDIO: droping audio data

(/home/sijar/Videos/Webcam) 25371748K bytes free on a total of 39908968K (used: 36 %) treshold=51200K 
AUDIO: droping audio data

AUDIO: droping audio data

  
... repeats a couple of times ...
  
Cap Video toggled: 0 
Shuting Down IO Thread 
AUDIO: droping audio data

stop= 4426644744000 start=4416533023000  
VIDEO: 146 frames in 10111.000000 ms = 14.439719 fps 
Stoping audio stream 
Closing audio stream... 
close avi 
Last message repeated 145 times 
[libx264 @ 0x8cbd8b0]frame I:2     Avg QP:14.10  size: 24492 
[libx264 @ 0x8cbd8b0]frame P:103   Avg QP:16.06  size: 20715 
[libx264 @ 0x8cbd8b0]mb I  I16..4: 48.4%  0.0% 51.6% 
[libx264 @ 0x8cbd8b0]mb P  I16..4: 57.5%  0.0%  0.0%  P16..4: 40.2%  0.0%  0.0%  0.0%  0.0%    skip: 2.3% 
[libx264 @ 0x8cbd8b0]final ratefactor: 62.05 
[libx264 @ 0x8cbd8b0]coded y,uvDC,uvAC intra: 79.7% 92.2% 68.4% inter: 62.4% 87.5% 48.0% 
[libx264 @ 0x8cbd8b0]i16 v,h,dc,p: 23% 17% 41% 19% 
[libx264 @ 0x8cbd8b0]i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 30% 24% 26%  2%  5%  3%  3%  3%  4% 
[libx264 @ 0x8cbd8b0]i8c dc,h,v,p: 53% 20% 23%  4% 
[libx264 @ 0x8cbd8b0]ref P L0: 63.0% 37.0% 
[libx264 @ 0x8cbd8b0]kb/s:-0.00 
total frames encoded: 0 
total audio frames encoded: 0 
IO thread finished...OK 
IO Thread finished 
enabling controls 
Cap Video toggled: 1 
(/home/sijar/Videos/Webcam) 25379744K bytes free on a total of 39908968K (used: 36 %) treshold=51200K 
using audio codec: 0x0055 
Audio frame size is 1152 samples for selected codec 
IO thread started...OK 
[libx264 @ 0x8cfba20]using cpu capabilities: MMX2 SSE2 Cache64 
[libx264 @ 0x8cfba20]profile Baseline, level 3.0 
[libx264 @ 0x8cfba20]non-strictly-monotonic PTS 
shift sound by -236 ms 
shift sound by -236 ms 
shift sound by -236 ms 
(/home/sijar/Videos/Webcam) 25377044K bytes free on a total of 39908968K (used: 36 %) treshold=51200K 
(/home/sijar/Videos/Webcam) 25373408K bytes free on a total of 39908968K (used: 36 %) treshold=51200K 

AUDIO: droping audio data 
AUDIO: droping audio data 
AUDIO: droping audio data 
AUDIO: droping audio data 
AUDIO: droping audio data 
AUDIO: droping audio data
  
... repeats a couple of times ...
  
(/home/sijar/Videos/Webcam) 25370696K bytes free on a total of 39908968K (used: 36 %) treshold=51200K 
AUDIO: droping audio data

AUDIO: droping audio data

AUDIO: droping audio data

  
... repeats a couple of times ...
  
(/home/sijar/Videos/Webcam) 25367680K bytes free on a total of 39908968K (used: 36 %) treshold=51200K 
(/home/sijar/Videos/Webcam) 25364052K bytes free on a total of 39908968K (used: 36 %) treshold=51200K 
(/home/sijar/Videos/Webcam) 25360312K bytes free on a total of 39908968K (used: 36 %) treshold=51200K 
(/home/sijar/Videos/Webcam) 25356628K bytes free on a total of 39908968K (used: 36 %) treshold=51200K 
(/home/sijar/Videos/Webcam) 25352908K bytes free on a total of 39908968K (used: 36 %) treshold=51200K 
(/home/sijar/Videos/Webcam) 25349316K bytes free on a total of 39908968K (used: 36 %) treshold=51200K 
(/home/sijar/Videos/Webcam) 25345552K bytes free on a total of 39908968K (used: 36 %) treshold=51200K 
(/home/sijar/Videos/Webcam) 25341828K bytes free on a total of 39908968K (used: 36 %) treshold=51200K 
(/home/sijar/Videos/Webcam) 25338092K bytes free on a total of 39908968K (used: 36 %) treshold=51200K 
(/home/sijar/Videos/Webcam) 25334412K bytes free on a total of 39908968K (used: 36 %) treshold=51200K 
Cap Video toggled: 0 
Shuting Down IO Thread 
stop= 4708817235000 start=4578624714000  
VIDEO: 1604 frames in 130192.000000 ms = 12.320265 fps 
Stoping audio stream 
Closing audio stream... 
close avi 
Last message repeated 1603 times 
[libx264 @ 0x8cfba20]frame I:16    Avg QP:14.78  size: 42627 
[libx264 @ 0x8cfba20]frame P:1547  Avg QP:16.44  size: 28599 
[libx264 @ 0x8cfba20]mb I  I16..4: 21.6%  0.0% 78.4% 
[libx264 @ 0x8cfba20]mb P  I16..4: 28.1%  0.0%  0.0%  P16..4: 70.5%  0.0%  0.0%  0.0%  0.0%    skip: 1.4% 
[libx264 @ 0x8cfba20]final ratefactor: 88.17 
[libx264 @ 0x8cfba20]coded y,uvDC,uvAC intra: 74.4% 95.8% 83.2% inter: 75.2% 94.6% 69.2% 
[libx264 @ 0x8cfba20]i16 v,h,dc,p: 27% 17% 40% 16% 
[libx264 @ 0x8cfba20]i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 25% 25% 21%  3%  6%  4%  5%  4%  7% 
[libx264 @ 0x8cfba20]i8c dc,h,v,p: 61% 18% 18%  4% 
[libx264 @ 0x8cfba20]ref P L0: 64.0% 36.0% 
[libx264 @ 0x8cfba20]kb/s:-0.00 
total frames encoded: 0 
total audio frames encoded: 0 
IO thread finished...OK 
IO Thread finished 
enabling controls 
Shuting Down Thread 
Thread terminated... 
cleaning Thread allocations: 100% 
SDL Quit 
Video Thread finished 
write /home/sijar/.guvcviewrc OK 
free audio mutex 
closed v4l2 strutures 
free controls 
free controls - vidState 
cleaned allocations - 100% 
Closing portaudio ...OK 
Closing GTK... OK

---

### Post by mikewhatever on 2011-02-08
In my experience, video capture with cheese was laggy because the default capture resolution was set to 1024x1024. Scaling it down under Edit->Preferences to 800x600 or 640x480 got the lag fixed.

---

### Post by Derspankster on 2013-01-26
> **mikewhatever said:**
> In my experience, video capture with cheese was laggy because the default capture resolution was set to 1024x1024. Scaling it down under Edit->Preferences to 800x600 or 640x480 got the lag fixed.
At least for me, this is not true. Even at 640 X 480 the audio is terribly laggy.

---

### Post by gifford on 2013-01-27
Thanks for the tip about Guvcview, seems like a great app.

---

### Post by wildmanne39 on 2013-01-27
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

