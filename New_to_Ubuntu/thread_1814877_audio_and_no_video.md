---
title: "audio and no video"
date: 2011-07-30
forum: New to Ubuntu
---

### Post by jagdefalke on 2011-07-30
OK, so I've got an HP Pavilion a807w, with Ubuntu 10.04.2.    I can play anything on the net like youtube, etc.., but anything on my hard drive.. mpeg, avi, what have you, all I get is sound no matter what player I'm using.     I've got the restricted extras and and such.   

I tried using:  

```
-vo vdpau /path/to/video/file 
```based on a different thread.


and got this:

```
michelle@michelle-desktop:~$ mplayer -vo vdpau /path/to/video/file
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /path/to/video/file.
File not found: '/path/to/video/file'
Failed to open /path/to/video/file.


Exiting... (End of file)
michelle@michelle-desktop:~$ 

```I'm guessing this has something to do with the video driver?
I've been to the HP website and it says they don't have a driver for this computer that will work for linux.   I've gone through the software center and can't find anything else I could be missing.     I'm not too familiar with this computer, I can't imagine that I'd be able to watch youtube if it didn't even have a video card, right?

---

### Post by 3rdalbum on 2011-07-30
Have you tried VLC media player? Also, what is the video codec used in the videos that won't play?

---

### Post by jagdefalke on 2011-07-30
yup.    what exactly do you mean by codec?    ( i should know that.. :p )

---

### Post by el_koraco on 2011-07-30
> **jagdefalke said:**
> michelle@michelle-desktop:~$ mplayer -vo vdpau 

You don't enter pazh/to/video/file, but the actual path and the name of the video. 

So it'd be something like

```
mplayer -vo vdpau ~/Videos/godzilla_smashes_buildings.avi

```

---

### Post by whitethorn on 2011-07-30
Alright first of all, have you read the output? It says it can't find the video file.

> 
Playing /path/to/video/file.
File not found: '/path/to/video/file'
Failed to open /path/to/video/file.


Make sure you give it the right path. What kind of graphics card do you have and what drivers are installed? Please post output of 

```
lspci
```
and 
```
cat /etc/X11/xorg.conf
```

And just for the sake of it, try

```
mplayer -vo xv /path/to/file
```

see if that works.

---

### Post by jagdefalke on 2011-07-30
> **el_koraco said:**
> You don't enter pazh/to/video/file, but the actual path and the name of the video. 

So it'd be something like

```
mplayer -vo vdpau ~/Videos/godzilla_smashes_buildings.avi

```

Ah!  Duh.    Ok, so here's what I got:

```
michelle@michelle-desktop:~$ mplayer -vo vdpau ~/Videos/M2U00027.MPG
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/michelle/Videos/M2U00027.MPG.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  9100.0 kbps (1137.5 kbyte/s)
[vdpau] Could not open dynamic library libvdpau.so.1
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 256.0 kbit/16.67% (ratio: 32000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  43.2 (43.2) of 42.8 (42.8)  0.8% 

Exiting... (End of file)
michelle@michelle-desktop:~$ 
```

It says no video, but there's a screenshot of the video in the icon for the video.   There's a screenshot in all the icons for all the videos, so there's gotta be something there.

---

### Post by jagdefalke on 2011-07-30
> **whitethorn said:**
> 


Make sure you give it the right path. What kind of graphics card do you have and what drivers are installed? Please post output of 

```
lspci
```and 
```
cat /etc/X11/xorg.conf
```And just for the sake of it, try

```
mplayer -vo xv /path/to/file
```see if that works.

```
michelle@michelle-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

```
```

michelle@michelle-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:0a.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
michelle@michelle-desktop:~$ 

```

```
michelle@michelle-desktop:~$ mplayer -vo xv /path/to/file
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /path/to/file.
File not found: '/path/to/file'
Failed to open /path/to/file.


Exiting... (End of file)
```



```
michelle@michelle-desktop:~$ cat /etc/X11/xorg.conf
cat: /etc/X11/xorg.conf: No such file or directory
```

---

### Post by whitethorn on 2011-07-30
Is there a specific reason why you want to use vdpau? As I wrote see if -vo xv will work. To get vdpau to work properly you'll probably need to follow this guide to get mplayer compiled with it [http://ubuntuforums.org/showthread.php?t=1037625](http://ubuntuforums.org/showthread.php?t=1037625)

You could probably also try using totem (is that still the default), what happens when you use the file explorer (nautilus) and double click on your video?

Edit:  Make sure you sure the right path, 

```
mplayer -vo xv ~/Videos/M2U00027.MPG
```

---

### Post by jagdefalke on 2011-07-30
I was searching around other threads earlier trying to find a way to fix it without having to start a new thread and saw vdpau mentioned a couple times so I thought I'd try it.   

tried -vo xv and it flashed a black square for a milisecond and that was it, it didn't even play sound.

```
michelle@michelle-desktop:~$ mplayer -vo xv ~/Videos/M2U00027.MPG
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/michelle/Videos/M2U00027.MPG.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  9100.0 kbps (1137.5 kbyte/s)
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Unsupported PixelFormat -1
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 256.0 kbit/16.67% (ratio: 32000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 854x480 Planar YV12 
A:   0.3 V:   0.0 A-V:  0.229 ct:  0.000   1/  1 ??% ??% ??,?% 0 0 

Exiting... (End of file)
```

ya, my default player is totem.

---

### Post by whitethorn on 2011-07-30
ok,

Does totem work? Could you give the output to

```
xvinfo
```
```
ls /etc/X11/
```
```
sudo lsmod |grep sis
```

After some research looks like you might need to make a /etc/X11/xorg.conf
[http://www.winischhofer.net/linuxsispart1.shtml#22](http://www.winischhofer.net/linuxsispart1.shtml#22)


[http://ubuntuforums.org/showthread.php?t=290663](http://ubuntuforums.org/showthread.php?t=290663) (looks like it has problems with 3d/opengl) it should be possible to get videos working though. 
[https://help.ubuntu.com/community/BinaryDriverHowto/Sis](https://help.ubuntu.com/community/BinaryDriverHowto/Sis)

Here's some xorg.conf I found [http://forum.ubuntuusers.de/topic/sis-661-und-1280-aufloesung/#post-2166234](http://forum.ubuntuusers.de/topic/sis-661-und-1280-aufloesung/#post-2166234)

I'll be out for a while bbl tonight, but maybe someone else can jump in here.

---

### Post by jagdefalke on 2011-07-30
OK, thankyou.   I'll check those out in a little while, I gotta go get some sleep... insomnia sucks... :p

Interesting thing, I copied some of the videos over to the Windows XP partition to try them there and had the opposite problem:  video but no sound!

---

### Post by jagdefalke on 2011-07-30
> **whitethorn said:**
> ok,

Does totem work? Could you give the output to

After some research looks like you might need to make a /etc/X11/xorg.conf
[http://www.winischhofer.net/linuxsispart1.shtml#22](http://www.winischhofer.net/linuxsispart1.shtml#22)


[http://ubuntuforums.org/showthread.php?t=290663](http://ubuntuforums.org/showthread.php?t=290663) (looks like it has problems with 3d/opengl) it should be possible to get videos working though. 
[https://help.ubuntu.com/community/BinaryDriverHowto/Sis](https://help.ubuntu.com/community/BinaryDriverHowto/Sis)

Here's some xorg.conf I found [http://forum.ubuntuusers.de/topic/sis-661-und-1280-aufloesung/#post-2166234](http://forum.ubuntuusers.de/topic/sis-661-und-1280-aufloesung/#post-2166234)

I'll be out for a while bbl tonight, but maybe someone else can jump in here.

```
michelle@michelle-desktop:~$ xvinfo
X-Video Extension version 2.2
screen #0
  Adaptor #0: "SIS 300/315/330 series Video Overlay"
    number of ports: 1
    port base: 62
    operations supported: PutImage 
    supported visuals:
      depth 24, visualID 0x21
    number of attributes: 20
      "XV_COLORKEY" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 66046)
      "XV_BRIGHTNESS" (range -128 to 127)
              client settable attribute
              client gettable attribute (current value is 10)
      "XV_CONTRAST" (range 0 to 7)
              client settable attribute
              client gettable attribute (current value is 2)
      "XV_SATURATION" (range -7 to 7)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_HUE" (range -8 to 7)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_AUTOPAINT_COLORKEY" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
      "XV_SET_DEFAULTS" (range 0 to 0)
              client settable attribute
      "XV_TVXPOSITION" (range -32 to 32)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_TVYPOSITION" (range -32 to 32)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_GAMMA_RED" (range 100 to 10000)
              client settable attribute
              client gettable attribute (current value is 1000)
      "XV_GAMMA_GREEN" (range 100 to 10000)
              client settable attribute
              client gettable attribute (current value is 1000)
      "XV_GAMMA_BLUE" (range 100 to 10000)
              client settable attribute
              client gettable attribute (current value is 1000)
      "XV_DISABLE_GRAPHICS" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_DISABLE_GRAPHICS_LR" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_DISABLE_COLORKEY" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_USE_CHROMAKEY" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_INSIDE_CHROMAKEY" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_CHROMAMIN" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 66046)
      "XV_CHROMAMAX" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 66047)
      "XV_SWITCHCRT" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
    maximum XvImage size: 1920 x 1088
    Number of image formats: 9
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x35315652 (RV15)
        guid: 52563135-0000-0000-0000-000000000000
        bits per pixel: 16
        number of planes: 1
        type: RGB (packed)
        depth: 15
        red, green, blue masks: 0x7c00, 0x3e0, 0x1f
      id: 0x36315652 (RV16)
        guid: 52563136-0000-0000-0000-000000000000
        bits per pixel: 16
        number of planes: 1
        type: RGB (packed)
        depth: 16
        red, green, blue masks: 0xf800, 0x7e0, 0x1f
      id: 0x55595659 (YVYU)
        guid: 59565955-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x3231564e (NV12)
        guid: 4e563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 2
        type: YUV (planar)
      id: 0x3132564e (NV21)
        guid: 4e563231-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 2
        type: YUV (planar)
  Adaptor #1: "SIS 315/330 series Video Blitter"
    number of ports: 16
    port base: 63
    operations supported: PutImage 
    supported visuals:
      depth 24, visualID 0x21
    number of attributes: 1
      "XV_SET_DEFAULTS" (range 0 to 0)
              client settable attribute
    maximum XvImage size: 2046 x 2046
    Number of image formats: 7
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x55595659 (YVYU)
        guid: 59565955-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x3231564e (NV12)
        guid: 4e563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 2
        type: YUV (planar)
      id: 0x3132564e (NV21)
        guid: 4e563231-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 2
        type: YUV (planar)
michelle@michelle-desktop:~$ 

```

```
michelle@michelle-desktop:~$ ls /etc/X11/
app-defaults             fonts    xinit   Xreset.d    Xsession.d
cursors                  rgb.txt  xkb     Xresources  Xsession.options
default-display-manager  X        Xreset  Xsession    Xwrapper.config

```

```
michelle@michelle-desktop:~$ sudo lsmod |grep sis
[sudo] password for michelle: 
sis900                 17048  0 
sata_sis                3332  0 
mii                     4381  1 sis900

```

---

### Post by jagdefalke on 2011-07-30
just in case it helps:

```
michelle@michelle-desktop:~$ lspci -v -s 01:00.0
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
    Subsystem: Hewlett-Packard Company Device 2a06
    Flags: 66MHz, medium devsel, IRQ 12
    BIST result: 00
    Memory at e0000000 (32-bit, prefetchable) [size=128M]
    Memory at ed000000 (32-bit, non-prefetchable) [size=128K]
    I/O ports at 9000 [size=128]
    Capabilities: <access denied>
    Kernel modules: sisfb

```



added:    
I checked on the options you suggested but according to this guy:  
[http://www.winischhofer.net/linuxsispart1.shtml#13](http://www.winischhofer.net/linuxsispart1.shtml#13)
I'm pretty much screwed because of the video card I have.     Is this a card that I can change out for a different one, or is it built in and physically inaccessible?

---

### Post by gordintoronto on 2011-07-30
vdpau is for Nvidia video cards, which you don't have.

Is your computer a laptop or desktop? It's "easy" to change the video card on a desktop computer, for a person who is comfortable working inside the case. However, there are several different physical types of video card, and you must have one of the same type as the existing card, or at least compatible with a slot on your motherboard.

Even with your current video card, you should be able to play a video. Did you install VLC Media Player?

You still don't have the path to your file correct, from what I have seen. Upper and lower case are important in Linux, so Desktop and desktop are completely different locations. Why don't you use the Nautilus file manager to locate the file, right-click on it, and select a player.

---

### Post by jagdefalke on 2011-07-30
> **gordintoronto said:**
> vdpau is for Nvidia video cards, which you don't have.

Is your computer a laptop or desktop? It's "easy" to change the video card on a desktop computer, for a person who is comfortable working inside the case. However, there are several different physical types of video card, and you must have one of the same type as the existing card, or at least compatible with a slot on your motherboard.

Even with your current video card, you should be able to play a video. Did you install VLC Media Player?

You still don't have the path to your file correct, from what I have seen. Upper and lower case are important in Linux, so Desktop and desktop are completely different locations. Why don't you use the Nautilus file manager to locate the file, right-click on it, and select a player.

I didn't start trying anything in kernal until last night, after looking around the forum. Up until then ALL I've been using is Nautilus.  
Yes I have VLC Media Player and have tried it.   As well as Movie Player and even Flash Player.   I've been through all the lists of stuff I can find in the software center looking for things that might help.

---

### Post by whitethorn on 2011-07-31
It should be working with the -vo xv command. Could you try installing smplayer (it's a Gui for mplayer).

```
sudo apt-get update && sudo apt-get install smplayer
```

Then start smplayer, Go to Options -> Preferences -> Video tab (General)

You should a list with a label with Output driver and a list beside it. Try going through the list and see if you can get a video to run with one of the drivers. Do you have any other video files you can try, maybe a .avi?

---

### Post by jagdefalke on 2011-07-31
OK, I installed smplayer, but I can't find the Video Tab that your talking about.   There's no Options to click on, on right click or top of window or anywhere.     I do have one .avi and it does the same thing.   Basically the player only shows black (as if the cap was on the video cam..)  and there's some light scratchy lines that flicker horizontally across the monitor while it's playing.      Like I said, I tried playing the vids on the XP partition and got the opposite problem:  video but no sound.    Very interesting.

---

### Post by jagdefalke on 2011-08-08
bump

---

