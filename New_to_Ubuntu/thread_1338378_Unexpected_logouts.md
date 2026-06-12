---
title: "Unexpected logouts"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by byline on 2009-11-26
[COLOR=Black]I upgraded to Ubuntu 9.10 last month, and last week, while surfing Facebook apps with Firefox, I was unexpectedly logged out. The last two times, I opened my Terminal window and typed: tail /var/log/messages

The second time, I got this message which coincided with the time of the logout:

[/COLOR]   [COLOR=Black]Nov 17 09:59:55 desktop pulseaudio[2937]: pid.c: Stale PID file, overwriting.
Nov 17 10:00:03 desktop pulseaudio[2937]: ratelimit.c: 1 events suppressed 

This last time, I got a similar message also coinciding with the time of the logout:

[/COLOR]   [COLOR=#ff0000][COLOR=Black]Nov 21 16:07:16 desktop pulseaudio[3648]: pid.c: Stale PID file, overwriting.
Nov 21 16:07:22 desktop pulseaudio[3648]: ratelimit.c: 18 events suppressed

I posted a reply in the General Discussion forum, but in a Kubuntu thread where a user was having a similar problem. So I apologize for repeating myself here, but I think because I was posting to a thread focusing on a different operating system, I wasn't getting the answers I sought.

Thanks for any advice you can offer!

P.S. I'm the computer user, my husband the actual Linux guy and installer; he's not the beginner, I am. However, because he suffers with chronic back pain, long periods of sitting to work on this are not an option for him. So, big pictures, little words, OK? :smile:

(For example, in the other thread, [/COLOR][/COLOR]another poster suggested that I search a directory, **/var/log/gdm**, to see if there were any .log files in it. Perhaps "**:0.log**"? But I'm unsure of how to access that directory.)

---

### Post by byline on 2009-11-29
Nothing?

---

### Post by style23 on 2009-11-29
Same thing happens to me when I try to access certain video links on website. Still looking for some type of solution

---

### Post by boie on 2009-11-29
Not sure how to plug in here...but here's my question/problem: My grandson excised windows xp and installed ubuntu...now I can't remember my password to get the os to come up...how do I reset a username and password from the initial screen which just says 'ubuntu'???

---

### Post by arvevans on 2009-11-29
Boie

Your grandson probably (hopefully) left himself a back-door way to enter the system.  If so, have him log in using his own password and then reset your password to something you can remember.

Arv
_._

---

### Post by byline on 2009-12-01
Interestingly enough, it hasn't happened since I disabled most of my Facebook apps. Not sure if it's just coincidence, or that really had something to do with it.

---

### Post by ukripper on 2009-12-01
if it happens again can you post output of this command:
```
tail -n 100 /var/log/Xorg.0.log
```

---

### Post by byline on 2009-12-01
> **ukripper said:**
> if it happens again can you post output of this command:
```
tail -n 100 /var/log/Xorg.0.log
```
Will do. Thanks!

---

### Post by style23 on 2010-01-01
It happend to me again. Here's my output

(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) intel(0): EDID vendor "SYN", prod id 6
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Printing probed modes for output VGA
(II) intel(0): Modeline "1280x960@60"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x768"x60.2   85.50  1360 1376 1438 1498  768 777 783 948 -hsync +vsync (57.1 kHz)
(II) intel(0): Modeline "1792x1344@60"x60.0  204.80  1792 1920 2120 2448  1344 1345 1348 1394 -hsync +vsync (83.7 kHz)
(II) intel(0): Modeline "1600x1200@65"x65.0  175.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (81.2 kHz)
(II) intel(0): Modeline "1600x1200@60"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) intel(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz)
(II) intel(0): Modeline "1400x1050@75"x75.0  155.85  1400 1496 1648 1896  1050 1051 1054 1096 -hsync +vsync (82.2 kHz)
(II) intel(0): Modeline "1400x1050@60"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
(II) intel(0): Modeline "1280x1024@75"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1280x1024@60"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1280x960@75"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 -hsync +vsync (75.2 kHz)
(II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) intel(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(II) intel(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(II) intel(0): Modeline "1152x864@75"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) intel(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1280x768"x60.1   79.50  1280 1344 1480 1680  768 769 772 788 +hsync -vsync (47.3 kHz)
(II) intel(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) intel(0): Modeline "1024x768@85"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768@75"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768@70"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768@60"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624@75"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600@85"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600@72"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600@75"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600@60"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600@56"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480@85"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480@72"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480@75"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480@60"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): Allocate new frame buffer 1024x768 stride 1024
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x00c00000 (pgoffset 3072)
(II) intel(0): New front buffer at 0xc00000
(II) intel(0): xf86UnbindGARTMemory: unbind key 3

---

### Post by style23 on 2010-02-13
I decided to do a fresh install of 9.10 and still I get unexpected log-outs, is there any suggestions? There has to be a conflict some where because this same computer didn't have this problem in 9.04.

---

### Post by Shpongle on 2010-02-13
whats your graphics card ?, I know 9.10 had some changes in relation to graphics acceleration 9.04 was EXA and 9.10 is by default UXA on the intel cards as far as i know.

what are you running when it happens ? ,

---

### Post by style23 on 2010-02-13
> **DillByrne said:**
> whats your graphics card ?, I know 9.10 had some changes in relation to graphics acceleration 9.04 was EXA and 9.10 is by default UXA on the intel cards as far as i know.

what are you running when it happens ? ,

PCI:*(0:0:2:0) 8086:2562:1462:5778 Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device rev 3, Mem @ 0xe0000000/134217728, 0xee000000/524288

Sometimes i'm running my webbrowser(it doesn't matter which one), just going onto a web page, or if i'm switching my wallpaper it might happen. It's weird I just can't make it happen it happens sporadically.

---

### Post by Shpongle on 2010-02-13
it sounds like a graphics issue anyway as it happens when you change wallpaper aswell, are you running compiz ?

---

### Post by style23 on 2010-02-13
> **DillByrne said:**
> it sounds like a graphics issue anyway as it happens when you change wallpaper aswell, are you running compiz ?

I believe its a graphic issue but I can't even run compiz. Where can we look first to see what might be causing the problem which Log file.

---

### Post by style23 on 2010-02-13
Also, sometimes when I change the screen resolution the mouse will disappear. But I can use the mouse it just the pointer becomes invincible. I tried this computer on another monitor as well and the same results.
I looked in the log file viewer but don't know what to look for?

---

### Post by style23 on 2010-02-14
bump

---

### Post by byline on 2010-02-16
> **ukripper said:**
> if it happens again can you post output of this command:
```
tail -n 100 /var/log/Xorg.0.log
```
OK, just now I was going into another website forum discussion, not Facebook, and it happened again. First time it's happened since November, when I discontinued all my Facebook applications. I typed in the above command, and here's what it says:

                                 ~$ tail -n 100 /var/log/Xorg.0.log 
 (II) NVIDIA(0): Initialized GPU GART. 
 (II) NVIDIA(0): Setting mode "nvidia-auto-select" 
 (II) Loading extension NV-GLX 
 (II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized 
 (==) NVIDIA(0): Disabling shared memory pixmaps 
 (II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture 
 (==) NVIDIA(0): Backing store disabled 
 (==) NVIDIA(0): Silken mouse enabled 
 (II) NVIDIA(0): DPMS enabled 
 (II) Loading extension NV-CONTROL 
 (II) Loading extension XINERAMA 
 (==) RandR enabled 
 (II) Initializing built-in extension Generic Event Extension 
 (II) Initializing built-in extension SHAPE 
 (II) Initializing built-in extension MIT-SHM 
 (II) Initializing built-in extension XInputExtension 
 (II) Initializing built-in extension XTEST 
 (II) Initializing built-in extension BIG-REQUESTS 
 (II) Initializing built-in extension SYNC 
 (II) Initializing built-in extension XKEYBOARD 
 (II) Initializing built-in extension XC-MISC 
 (II) Initializing built-in extension SECURITY 
 (II) Initializing built-in extension XINERAMA 
 (II) Initializing built-in extension XFIXES 
 (II) Initializing built-in extension RENDER 
 (II) Initializing built-in extension RANDR 
 (II) Initializing built-in extension COMPOSITE 
 (II) Initializing built-in extension DAMAGE 
 (II) Initializing extension GLX 
 (II) config/hal: Adding input device Power Button 
 (II) LoadModule: "evdev" 
 (II) Loading /usr/lib/xorg/modules/input//evdev_drv.so 
 (II) Module evdev: vendor="X.Org Foundation" 
     compiled for 1.6.4, module version = 2.2.5 
     Module class: X.Org XInput Driver 
     ABI class: X.Org XInput driver, version 4.0 
 (**) Power Button: always reports core events 
 (**) Power Button: Device: "/dev/input/event1" 
 (II) Power Button: Found keys 
 (II) Power Button: Configuring as keyboard 
 (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD) 
 (**) Option "xkb_rules" "evdev" 
 (**) Option "xkb_model" "pc105" 
 (**) Option "xkb_layout" "us" 
 (II) config/hal: Adding input device AT Translated Set 2 keyboard 
 (**) AT Translated Set 2 keyboard: always reports core events 
 (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4" 
 (II) AT Translated Set 2 keyboard: Found keys 
 (II) AT Translated Set 2 keyboard: Configuring as keyboard 
 (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD) 
 (**) Option "xkb_rules" "evdev" 
 (**) Option "xkb_model" "pc105" 
 (**) Option "xkb_layout" "us" 
 (II) config/hal: Adding input device Power Button 
 (**) Power Button: always reports core events 
 (**) Power Button: Device: "/dev/input/event0" 
 (II) Power Button: Found keys 
 (II) Power Button: Configuring as keyboard 
 (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD) 
 (**) Option "xkb_rules" "evdev" 
 (**) Option "xkb_model" "pc105" 
 (**) Option "xkb_layout" "us" 
 (II) config/hal: Adding input device Sleep Button 
 (**) Sleep Button: always reports core events 
 (**) Sleep Button: Device: "/dev/input/event2" 
 (II) Sleep Button: Found keys 
 (II) Sleep Button: Configuring as keyboard 
 (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD) 
 (**) Option "xkb_rules" "evdev" 
 (**) Option "xkb_model" "pc105" 
 (**) Option "xkb_layout" "us" 
 (II) config/hal: Adding input device Macintosh mouse button emulation 
 (**) Macintosh mouse button emulation: always reports core events 
 (**) Macintosh mouse button emulation: Device: "/dev/input/event3" 
 (II) Macintosh mouse button emulation: Found 3 mouse buttons 
 (II) Macintosh mouse button emulation: Found x and y relative axes 
 (II) Macintosh mouse button emulation: Configuring as mouse 
 (**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5 
 (**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200 
 (II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE) 
 (**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1 
 (**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00 
 (**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms 
 (**) Macintosh mouse button emulation: (accel) set acceleration profile 0 
 (II) Macintosh mouse button emulation: initialized for relative axes. 
 (II) config/hal: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) 
 (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): always reports core events 
 (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Device: "/dev/input/event5" 
 (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found 3 mouse buttons 
 (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found x and y relative axes 
 (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found scroll wheel(s) 
 (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Configuring as mouse 
 (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): YAxisMapping: buttons 4 and 5 
 (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200 
 (II) XINPUT: Adding extended input device "Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)" (type: MOUSE) 
 (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) keeping acceleration scheme 1 
 (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) filter chain progression: 2.00 
 (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) filter stage 0: 20.00 ms 
 (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) set acceleration profile 0 
 (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): initialized for relative axes.

---

### Post by byline on 2010-02-17
Anyone?

---

### Post by byline on 2010-02-18
It happened again last night, fifth time since November. Weird that it had stopped altogether since November, but then suddenly started up again. Every time it's happened, I've been on the Internet. Any clues?

---

### Post by byline on 2010-02-21
OK, now it's just happened a sixth time. This was the first time I wasn't online, but was working on a story. I was in the process of deleting a bulleted section and pasting it elsewhere when zap! I was logged off.

Could a flaky graphics card be the cause?

---

### Post by byline on 2010-02-22
Another thought occurred to me: Sometimes, when I turn on the computer in the morning, the clipboard (Glipper) doesn't load properly. When that happens, it asks if I want to delete it, and I always answer no.

Of course, I'm always using the clipboard for copying and pasting text, links, etc. I can't recall if I was doing that the other times those unexpected logouts occurred, but I definitely *was* doing it last night. I was trying to copy and paste a bulleted section of text. I had just copied it and was getting ready to paste it when the computer went to the log-in screen.

Is it possible that the clipboard is getting too full, and that would cause this to happen? Odd question, I know, but I thought I'd ask.

---

