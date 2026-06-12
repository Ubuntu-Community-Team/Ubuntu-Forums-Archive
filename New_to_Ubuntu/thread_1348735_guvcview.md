---
title: "guvcview"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by herbertportillo on 2009-12-07
I have a Microsoft (cue the boos) LifeCam Cinema webcam, and I have Cheese, but it isn't good at recording video. It's super choppy and after about 10 seconds it just stops recording the video, but the audio continues. It just runs out of steam, I guess. Maybe it has something to do with Cheese only being able to record in Ogg Video.

Anyways, I downloaded guvcview, and it records video really smoothly. I like it a lot :) But there's a tiny problem. I can only record one video at a time. If I capture a video and stop, guvcview will save it and it will play perfectly. But if I try to record another video, it won't do it. I have to exit the program, open it again, and then record. Is there a setting I can tweak so that I don't have to close and re-open the program everytime I record a video? Any and all help is appreciated. Thx.

---

### Post by herbertportillo on 2009-12-08
Bump?

---

### Post by oluapSissa on 2009-12-08
Hi,

Can you post the output of "guvcview --verbose" (try the video capture at least 2 or 3 times)

this is the first time I heard of this problem and can't really replicate it on my system.

Also this type of thing should really be reported on the application bug tracker:
[http://developer.berlios.de/bugs/?group_id=8179](http://developer.berlios.de/bugs/?group_id=8179)

Lucky you I happen to notice this thread :D
otherwise it would be difficult to fix whatever problem/bug you stumble upon.

Best regards,
Paulo

---

### Post by oluapSissa on 2009-12-09
Hi,
Please also make sure you have the latest version (curr. 1.2.1) from here:
[http://guvcview.berlios.de](http://guvcview.berlios.de)

the package in universe is very old (1.1.1)

Regards,
Paulo

---

### Post by herbertportillo on 2009-12-11
So I ran guvcview --verbose, and this is what happened the first time. I recorded video for about 5 seconds.

```
herbert@herbert-desktop:~$ guvcview --verbose
guvcview 1.1.1
video_device: /dev/video0
vid_sleep: 0
resolution: 1280 x 720
windowsize: 477 x 699
vert pane: 578
spin behavior: 0
mode: mjpg
fps: 1/30
Display Fps: 0
bpp: 0
hwaccel: 1
grabmethod: 1
avi_format: 0
sound: 1
sound Device: 3
sound samp rate: 0
sound Channels: 0
Sound Block Size: 1 seconds
Sound Format: 80 
Sound bit Rate: 160 Kbps
Pan Step: 2 degrees
Tilt Step: 2 degrees
Video Filter Flags: 0
image inc: 0
profile(default):/home/herbert/default.gpfl
starting portaudio...
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
language catalog=> dir:/usr/share/locale type:UTF-8 lang:en_US.UTF-8 cat:guvcview.mo
mjpg: setting format to 1196444237
video device: /dev/video0 
/dev/video0 - device 1
Init. Microsoft® LifeCam Cinema(TM) (location: usb-0000:00:0b.1-3)
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 1280, height = 720 }
	Time interval between frame: 1/10, 2/15, 
{ discrete: width = 960, height = 544 }
	Time interval between frame: 1/15, 1/10, 2/15, 
{ discrete: width = 800, height = 448 }
	Time interval between frame: 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 640, height = 360 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 424, height = 240 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 800, height = 600 }
	Time interval between frame: 1/15, 1/10, 2/15, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 1280, height = 800 }
	Time interval between frame: 1/10, 
{ pixelformat = 'MJPG', description = 'MJPEG' }
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 1280, height = 720 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 960, height = 544 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 800, height = 448 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 640, height = 360 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 800, height = 600 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 416, height = 240 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
checking format: 1196444237
vid:045e 
pid:075d 
driver:uvcvideo
Controls:
control[0]: 0x980900  Brightness, 30:1:255, default 133
control[1]: 0x980901  Contrast, 0:1:10, default 5
control[2]: 0x980902  Saturation, 0:1:200, default 83
control[3]: 0x98090c  White Balance Temperature, Auto, 0:1:1, default 1
control[4]: 0x980918  Power Line Frequency, 0:1:2, default 2
control[5]: 0x98091a  White Balance Temperature, 2800:1:10000, default 4500
control[6]: 0x98091b  Sharpness, 0:1:50, default 25
control[7]: 0x98091c  Backlight Compensation, 0:1:10, default 0
control[8]: 0x9a0901  Exposure, Auto, 0:1:3, default 1
control[9]: 0x9a0902  Exposure (Absolute), 5:1:20000, default 156
control[10]: 0x9a090a  Focus (absolute), 0:1:40, default 0
control[11]: 0x9a090c  Focus, Auto, 0:1:1, default 0
resolutions of 2º format=11 
frame rates of 2º resolution=5 
Def. Res: 1  numb. fps:5
--------------------------------------- device #0
Name                     = HDA NVidia: STAC92xx Analog (hw:0,0)
Host API                 = ALSA
Max inputs = 2, Max outputs = 8
Def. low input latency   =    0.012
Def. low output latency  =    0.012
Def. high input latency  =    0.046
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #1
Name                     = Microsoft® LifeCam Cinema(TM): USB Audio (hw:1,0)
Host API                 = ALSA
Max inputs = 1, Max outputs = 0
Def. low input latency   =    0.012
Def. low output latency  =   -1.000
Def. high input latency  =    0.046
Def. high output latency =   -1.000
Def. sample rate         = 44100.00
--------------------------------------- device #2
Name                     = front
Host API                 = ALSA
Max inputs = 0, Max outputs = 8
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #3
Name                     = surround40
Host API                 = ALSA
Max inputs = 0, Max outputs = 8
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #4
Name                     = surround41
Host API                 = ALSA
Max inputs = 0, Max outputs = 128
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #5
Name                     = surround50
Host API                 = ALSA
Max inputs = 0, Max outputs = 128
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #6
Name                     = surround51
Host API                 = ALSA
Max inputs = 0, Max outputs = 8
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #7
Name                     = surround71
Host API                 = ALSA
Max inputs = 0, Max outputs = 8
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #8
Name                     = pulse
Host API                 = ALSA
Max inputs = 32, Max outputs = 32
Def. low input latency   =    0.012
Def. low output latency  =    0.012
Def. high input latency  =    0.046
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #9
Name                     = dmix
Host API                 = ALSA
Max inputs = 0, Max outputs = 2
Def. low input latency   =   -1.000
Def. low output latency  =    0.043
Def. high input latency  =   -1.000
Def. high output latency =    0.043
Def. sample rate         = 48000.00
--------------------------------------- device #10
[ Default Input, Default Output ]
Name                     = default
Host API                 = ALSA
Max inputs = 32, Max outputs = 32
Def. low input latency   =    0.012
Def. low output latency  =    0.012
Def. high input latency  =    0.046
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #11
[ Default OSS Input, Default OSS Output ]
Name                     = /dev/dsp
Host API                 = OSS
Max inputs = 16, Max outputs = 16
Def. low input latency   =    0.012
Def. low output latency  =    0.012
Def. high input latency  =    0.046
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #12
Name                     = /dev/dsp1
Host API                 = OSS
Max inputs = 16, Max outputs = 0
Def. low input latency   =    0.012
Def. low output latency  =    0.012
Def. high input latency  =    0.046
Def. high output latency =    0.046
Def. sample rate         = 44100.00
----------------------------------------------
SampleRate:0 Channels:0
Video driver: x11
A window manager is available
Cap Video toggled: 1
shift sound by 1121 ms
shift sound forward by 21924 bytes
Cap Video toggled: 0
stop= 1260556472215816704 start=1260556465120799232 
VIDEO: 209 frames in 7095.000000 ms = 29.457364 fps
writing 18432 bytes of audio data
[B]Stoping audio stream
Closing audio stream...
close avi
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
Shuting Down Thread
waiting for thread to finish
 Could not grab image (select timeout): Resource temporarily unavailable[/B]
Thread terminated...
cleaning Thread allocations: 100%
SDL Quit
write /home/herbert/.guvcviewrc OK
closed v4l2 strutures
free controls
free controls - vidState
cleaned allocations - 100%
Closing portaudio ...OK
Exit: OK

```

I ran it a second time and recorded video again for 5 seconds, and this is what happened.

```
herbert@herbert-desktop:~$ guvcview --verbose
guvcview 1.1.1
video_device: /dev/video0
vid_sleep: 0
resolution: 1280 x 720
windowsize: 477 x 699
vert pane: 578
spin behavior: 0
mode: mjpg
fps: 1/30
Display Fps: 0
bpp: 0
hwaccel: 1
grabmethod: 1
avi_format: 0
sound: 1
sound Device: 3
sound samp rate: 0
sound Channels: 0
Sound Block Size: 1 seconds
Sound Format: 80 
Sound bit Rate: 160 Kbps
Pan Step: 2 degrees
Tilt Step: 2 degrees
Video Filter Flags: 0
image inc: 0
profile(default):/home/herbert/default.gpfl
starting portaudio...
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
language catalog=> dir:/usr/share/locale type:UTF-8 lang:en_US.UTF-8 cat:guvcview.mo
mjpg: setting format to 1196444237
video device: /dev/video0 
/dev/video0 - device 1
Init. Microsoft® LifeCam Cinema(TM) (location: usb-0000:00:0b.1-3)
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 1280, height = 720 }
	Time interval between frame: 1/10, 2/15, 
{ discrete: width = 960, height = 544 }
	Time interval between frame: 1/15, 1/10, 2/15, 
{ discrete: width = 800, height = 448 }
	Time interval between frame: 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 640, height = 360 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 424, height = 240 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 800, height = 600 }
	Time interval between frame: 1/15, 1/10, 2/15, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 1280, height = 800 }
	Time interval between frame: 1/10, 
{ pixelformat = 'MJPG', description = 'MJPEG' }
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 1280, height = 720 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 960, height = 544 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 800, height = 448 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 640, height = 360 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 800, height = 600 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 416, height = 240 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
checking format: 1196444237
vid:045e 
pid:075d 
driver:uvcvideo
Controls:
control[0]: 0x980900  Brightness, 30:1:255, default 133
control[1]: 0x980901  Contrast, 0:1:10, default 5
control[2]: 0x980902  Saturation, 0:1:200, default 83
control[3]: 0x98090c  White Balance Temperature, Auto, 0:1:1, default 1
control[4]: 0x980918  Power Line Frequency, 0:1:2, default 2
control[5]: 0x98091a  White Balance Temperature, 2800:1:10000, default 4500
control[6]: 0x98091b  Sharpness, 0:1:50, default 25
control[7]: 0x98091c  Backlight Compensation, 0:1:10, default 0
control[8]: 0x9a0901  Exposure, Auto, 0:1:3, default 1
control[9]: 0x9a0902  Exposure (Absolute), 5:1:20000, default 156
control[10]: 0x9a090a  Focus (absolute), 0:1:40, default 0
control[11]: 0x9a090c  Focus, Auto, 0:1:1, default 0
resolutions of 2º format=11 
frame rates of 2º resolution=5 
Def. Res: 1  numb. fps:5
--------------------------------------- device #0
Name                     = HDA NVidia: STAC92xx Analog (hw:0,0)
Host API                 = ALSA
Max inputs = 2, Max outputs = 8
Def. low input latency   =    0.012
Def. low output latency  =    0.012
Def. high input latency  =    0.046
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #1
Name                     = Microsoft® LifeCam Cinema(TM): USB Audio (hw:1,0)
Host API                 = ALSA
Max inputs = 1, Max outputs = 0
Def. low input latency   =    0.012
Def. low output latency  =   -1.000
Def. high input latency  =    0.046
Def. high output latency =   -1.000
Def. sample rate         = 44100.00
--------------------------------------- device #2
Name                     = front
Host API                 = ALSA
Max inputs = 0, Max outputs = 8
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #3
Name                     = surround40
Host API                 = ALSA
Max inputs = 0, Max outputs = 8
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #4
Name                     = surround41
Host API                 = ALSA
Max inputs = 0, Max outputs = 128
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #5
Name                     = surround50
Host API                 = ALSA
Max inputs = 0, Max outputs = 128
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #6
Name                     = surround51
Host API                 = ALSA
Max inputs = 0, Max outputs = 8
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #7
Name                     = surround71
Host API                 = ALSA
Max inputs = 0, Max outputs = 8
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #8
Name                     = pulse
Host API                 = ALSA
Max inputs = 32, Max outputs = 32
Def. low input latency   =    0.012
Def. low output latency  =    0.012
Def. high input latency  =    0.046
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #9
Name                     = dmix
Host API                 = ALSA
Max inputs = 0, Max outputs = 2
Def. low input latency   =   -1.000
Def. low output latency  =    0.043
Def. high input latency  =   -1.000
Def. high output latency =    0.043
Def. sample rate         = 48000.00
--------------------------------------- device #10
[ Default Input, Default Output ]
Name                     = default
Host API                 = ALSA
Max inputs = 32, Max outputs = 32
Def. low input latency   =    0.012
Def. low output latency  =    0.012
Def. high input latency  =    0.046
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #11
[ Default OSS Input, Default OSS Output ]
Name                     = /dev/dsp
Host API                 = OSS
Max inputs = 16, Max outputs = 16
Def. low input latency   =    0.012
Def. low output latency  =    0.012
Def. high input latency  =    0.046
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #12
Name                     = /dev/dsp1
Host API                 = OSS
Max inputs = 16, Max outputs = 0
Def. low input latency   =    0.012
Def. low output latency  =    0.012
Def. high input latency  =    0.046
Def. high output latency =    0.046
Def. sample rate         = 44100.00
----------------------------------------------
SampleRate:0 Channels:0
Video driver: x11
A window manager is available
Cap Video toggled: 1
shift sound by 1121 ms
shift sound forward by 21924 bytes
Cap Video toggled: 0
stop= 1260556472215816704 start=1260556465120799232 
VIDEO: 209 frames in 7095.000000 ms = 29.457364 fps
writing 18432 bytes of audio data
[B]Stoping audio stream
Closing audio stream...
close avi
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable[/B]
Shuting Down Thread
waiting for thread to finish
 Could not grab image (select timeout): Resource temporarily unavailable
Thread terminated...
cleaning Thread allocations: 100%
SDL Quit
write /home/herbert/.guvcviewrc OK
closed v4l2 strutures
free controls
free controls - vidState
cleaned allocations - 100%
Closing portaudio ...OK
Exit: OK

```

I made the text bold where I think the problem is happening. My webcam has a blue light on it, and when a program (like Cheese) is using the webcam, the blue light turns on. When I close a program, the light turns off. But when I'm capturing video and I stop, the blue light turns off. But it shouldn't since the program is still running.

---

### Post by herbertportillo on 2009-12-11
I also saw that I had the old version of guvcview so I downloaded the new version (1.2.1) and the same thing happened.

```
herbert@herbert-desktop:~$ guvcview --verbose
guvcview 1.2.1
video_device: /dev/video0
vid_sleep: 0
cap_meth: 1
resolution: 1280 x 720
windowsize: 477 x 699
vert pane: 578
spin behavior: 0
mode: mjpg
fps: 1/30
Display Fps: 0
bpp: 0
hwaccel: 1
avi_format: 0
sound: 1
sound Device: 3
sound samp rate: 0
sound Channels: 0
Sound delay: 0 nanosec
Sound Format: 80 
Sound bit Rate: 160 Kbps
Pan Step: 2 degrees
Tilt Step: 2 degrees
Video Filter Flags: 0
image inc: 0
profile(default):/home/herbert/default.gpfl
starting portaudio...
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
language catalog=> dir:/usr/share/locale type:UTF-8 lang:en_US.UTF-8 cat:guvcview.mo
mjpg: setting format to 1196444237
capture method = 1
video device: /dev/video0 
/dev/video0 - device 1
Init. Microsoft® LifeCam Cinema(TM) (location: usb-0000:00:0b.1-3)
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 1280, height = 720 }
	Time interval between frame: 1/10, 2/15, 
{ discrete: width = 960, height = 544 }
	Time interval between frame: 1/15, 1/10, 2/15, 
{ discrete: width = 800, height = 448 }
	Time interval between frame: 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 640, height = 360 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 424, height = 240 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 800, height = 600 }
	Time interval between frame: 1/15, 1/10, 2/15, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 1280, height = 800 }
	Time interval between frame: 1/10, 
{ pixelformat = 'MJPG', description = 'MJPEG' }
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 1280, height = 720 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 960, height = 544 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 800, height = 448 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 640, height = 360 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 800, height = 600 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 416, height = 240 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 2/15, 
vid:045e 
pid:075d 
driver:uvcvideo
checking format: 1196444237
VIDIOC_G_COMP:: Invalid argument
   compression control not supported
fps is set to 1/30
V4L2_CTRL_FLAG_NEXT_CTRL supported
Controls:
control[0]: 0x980900  Brightness, 30:1:255, default 133
control[1]: 0x980901  Contrast, 0:1:10, default 5
control[2]: 0x980902  Saturation, 0:1:200, default 83
control[3]: 0x98090c  White Balance Temperature, Auto, 0:1:1, default 1
control[4]: 0x980918  Power Line Frequency, 0:1:2, default 2
control[5]: 0x98091a  White Balance Temperature, 2800:1:10000, default 4500
control[6]: 0x98091b  Sharpness, 0:1:50, default 25
control[7]: 0x98091c  Backlight Compensation, 0:1:10, default 0
control[8]: 0x9a0901  Exposure, Auto, 0:1:3, default 1
control[9]: 0x9a0902  Exposure (Absolute), 5:1:20000, default 156
control[10]: 0x9a090a  Focus (absolute), 0:1:40, default 0
control[11]: 0x9a090c  Focus, Auto, 0:1:1, default 0
control[12]: 0x9a090d  Zoom, Absolute, 0:1:10, default 0
resolutions of 2º format=11 
frame rates of 2º resolution=5 
fps is set to 1/30
Def. Res: 1  numb. fps:5
no codec detected for H264
--------------------------------------- device #0
Name                     = HDA NVidia: STAC92xx Analog (hw:0,0)
Host API                 = ALSA
Max inputs = 2, Max outputs = 8
Def. low input latency   =    0.012
Def. low output latency  =    0.012
Def. high input latency  =    0.046
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #1
Name                     = Microsoft® LifeCam Cinema(TM): USB Audio (hw:1,0)
Host API                 = ALSA
Max inputs = 1, Max outputs = 0
Def. low input latency   =    0.012
Def. low output latency  =   -1.000
Def. high input latency  =    0.046
Def. high output latency =   -1.000
Def. sample rate         = 44100.00
--------------------------------------- device #2
Name                     = front
Host API                 = ALSA
Max inputs = 0, Max outputs = 8
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #3
Name                     = surround40
Host API                 = ALSA
Max inputs = 0, Max outputs = 8
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #4
Name                     = surround41
Host API                 = ALSA
Max inputs = 0, Max outputs = 128
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #5
Name                     = surround50
Host API                 = ALSA
Max inputs = 0, Max outputs = 128
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #6
Name                     = surround51
Host API                 = ALSA
Max inputs = 0, Max outputs = 8
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #7
Name                     = surround71
Host API                 = ALSA
Max inputs = 0, Max outputs = 8
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #8
Name                     = pulse
Host API                 = ALSA
Max inputs = 32, Max outputs = 32
Def. low input latency   =    0.012
Def. low output latency  =    0.012
Def. high input latency  =    0.046
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #9
Name                     = dmix
Host API                 = ALSA
Max inputs = 0, Max outputs = 2
Def. low input latency   =   -1.000
Def. low output latency  =    0.043
Def. high input latency  =   -1.000
Def. high output latency =    0.043
Def. sample rate         = 48000.00
--------------------------------------- device #10
[ Default Input, Default Output ]
Name                     = default
Host API                 = ALSA
Max inputs = 32, Max outputs = 32
Def. low input latency   =    0.012
Def. low output latency  =    0.012
Def. high input latency  =    0.046
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #11
[ Default OSS Input, Default OSS Output ]
Name                     = /dev/dsp
Host API                 = OSS
Max inputs = 16, Max outputs = 16
Def. low input latency   =    0.012
Def. low output latency  =    0.012
Def. high input latency  =    0.046
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #12
Name                     = /dev/dsp1
Host API                 = OSS
Max inputs = 16, Max outputs = 0
Def. low input latency   =    0.012
Def. low output latency  =    0.012
Def. high input latency  =    0.046
Def. high output latency =    0.046
Def. sample rate         = 44100.00
----------------------------------------------
SampleRate:0 Channels:0
Video driver: x11
A window manager is available
Cap Video toggled: 1
(/home/herbert) 116695252K bytes free on a total of 147509656K (used: 20 %) treshold=102400K
IO thread started...OK
shift sound by 1087 ms
shift sound forward by 21402 bytes
Cap Video toggled: 0
Shuting Down IO Thread
stop= 1260557518438447000 start=1260557509938447000 
VIDEO: 245 frames in 8500.000000 ms = 28.823529 fps
[B]Stoping audio stream
Closing audio stream...
close avi
IO thread finished...OK
IO Thread finished
enabling controls
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
Shuting Down Thread
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable[/B]
Thread terminated...
cleaning Thread allocations: 100%
SDL Quit
Video Thread finished
write /home/herbert/.guvcviewrc OK
free audio mutex
closed v4l2 strutures
free controls
free controls - vidState
cleaned allocations - 100%
Closing portaudio ...OK
Closing GTK... OK

```

---

### Post by oluapSissa on 2009-12-12
This is really strange and I can't replicate it with any of my cameras.
Could you check the output of dmesg when the camera crashes for any relevant messages.
Do the camera controls also fail (check for error messages with guvcview --verbose) or is just the video stream?
Could you also try the matroska container and check if the samething happens or if it's just with avi.

Best regards,
Paulo

---

### Post by herbertportillo on 2009-12-12
The video controls still work, but the video stream dies.

I tried it with .mkv instead of .avi and it still does the same thing. When I press 'Stop Video' the camera is still alive for a few seconds, but then the stream just dies.

---

### Post by oluapSissa on 2009-12-13
OK, it seems MS cameras have some timing issues :(
[https://lists.berlios.de/pipermail/linux-uvc-devel/2009-December/005404.html](https://lists.berlios.de/pipermail/linux-uvc-devel/2009-December/005404.html)

Can you try the proposed warkaround:
just go in /etc/modprob.d
and create uvcvideo.conf
edit and add:

options uvcvideo nodrop=1 trace=15 quirks=0x102 timeout=3000

save and reload the driver:
# sudo rmmod uvcvideo
# sudo modprobe uvcvideo

if this doesn't work please post the output of dmesg

best regards,
Paulo

---

### Post by oluapSissa on 2009-12-13
You may also want to try restarting the video stream, just change the fps or resolution value on the video tab.

regards,
paulo

---

### Post by herbertportillo on 2009-12-14
Changing the resolution restarts the video stream. I think I'll just do that. Thanks you

---

### Post by cometdog on 2010-07-04
Also have a Microsoft LifeCam Cinema.  Wouldn't record at all in Cheese.  Running Lucid on AMD64.

Same issue here - after stopping recording the video stops showing in guvcview.

Those driver options don't work for me.  Here are the last couple of lines from dmesg:
[287711.824912] usbcore: deregistering interface driver uvcvideo
[287720.127987] uvcvideo: Unknown parameter `timeout'

I'll try the workaround listed.

---

