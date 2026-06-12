---
title: "Offset screen issue"
date: 2011-08-04
forum: New to Ubuntu
---

### Post by Osric1 on 2011-08-04
This is probably a ridiculously easy question but I have genuinely been wresting with it for hours and cannot for the life of me sort it out. After playing a game with a different resolution when I returned to my desktop it did not return to the resolution I normally use. When I adjusted it back to my normal setting I was left with my screen offset. How do I resize my screen to fit the edges of my monitor so I don't have two inches off the edge and a black border on the other side?:(

Many thanks in advance for your assistance

---

### Post by jtarin on 2011-08-04
What version of Ubuntu? Did you try to reboot?

---

### Post by Osric1 on 2011-08-05
Tried rebooting, came back the same, 11.04 version. I seem to remember adjusting the screen to fit the monitor when I installed the previous version of Ubuntu for the first time. The screen is offset on all resolution sizes so it unlikely to be a resolution issue as it is not resolved by altering the resolution. It has rendered the OS next to unusable as the bottom panel is below the screen unless I make it huge in a lower resolution. Effectively the visible screen has moved lower and to the left leaving a black rim around the screen into which the mouse cannot travel. I have also noticed that some programs crash when changing resolution.  I must admit I have had a good deal of trouble with 11.04 and have to have it set up as the older version and regret upgrading as it appears to be more resource hungry and glitchy, I can no longer copy from a web page and paste into a search form for example and have problems with cursor placement with a mouse in search forms.:( I don't know whether it is because my PC is becoming somewhat aged, but 11.04 has provided me with no usueful extra functionality and has gone from a wonderfully hassle free stable platform into one that limps along like a corrupted Windows and has me forever digging around trying to sort things out. 

Thanks for taking the time to reply

---

### Post by realzippy on 2011-08-05
..which game was it ?

---

### Post by Osric1 on 2011-08-05
Wesnoth

---

### Post by realzippy on 2011-08-05
can you post output from 

```
xrandr --verbose
```


Have you tried reinstalling wesnoth,ubuntu-desktop?
```
sudo apt-get install ubuntu-desktop wesnoth --reinstall
```

---

### Post by Osric1 on 2011-08-05
Sorry can't copy and paste into this window, the "paste" option is not available and WAY too long to do by hand - my other very frustrating issue, I am unable to paste into Firefox. Tried attaching a text file but got "invalid file" error, if you can think of another way to get you the information let me know. Wesnoth did not actually crash, it just left the screen offset when I exited. It might also be worth pointing out that I had also installed Vegastrike, and some war game called Stalin or such like the same day, both of which crashed after a short time. The "paste" issue coincided with the installation of 11.04 which as I recall was also problematic. I haven't tried reinstalling Wesnoth as the problem is permanent now and have restarted several times and have not played Wesnoth since the problem arose. The OS is now verging on unusable with its present glitch and playing Wesnoth successfully is the least of my problems. If you think reinstalling Wesnoth is going to fix this issue I'll happily do so. What I'm really after, at least in the first instance, is a way of adjusting the screen to fit the monitor correctly so as to render my PC usable.

Thanks again for your help

---

### Post by realzippy on 2011-08-05
Hold left mouse button for copy,press mousewheel to paste....
for the xrandr command,but you can just run the 2nd command first,since it
reinstalls the desktop and wesnoth.If it helps,we need no xrandr output...

---

### Post by Osric1 on 2011-08-05
Fantastic, well done, got the paste to work.

Tried the reinstall - sorry didn't realise it would reinstall desktop or I would have just done it - no change I'm afraid. Below is the xrandr --verbose readout


Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA-0 connected 1024x768+0+0 (0x5a) normal (normal left inverted right x axis y axis) 698mm x 393mm
    Identifier: 0x51
    Timestamp:  51751
    Subpixel:   no subpixels
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       0
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID:
        00ffffffffffff005262080101010101
        ff130103084627780a9e2fa3554a9a25
        10454aafce0081c08180010101010101
        010101010101662150b051001b304070
        3600ba892100001e0e1f008051001e30
        40803700ba892100001c000000fc0054
        4f53484942412d54560a2020000000fd
        00384c1f410b000a20202020202000d5
    load detection: 1 (0x00000001)    range:  (0,1)
  1360x768 (0x54)   85.5MHz +HSync +VSync +preferred
        h: width  1360 start 1424 end 1536 total 1792 skew    0 clock   47.7KHz
        v: height  768 start  771 end  777 total  795           clock   60.0Hz
  1280x1024 (0x55)  108.0MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock   64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   60.0Hz
  1280x768 (0x56)   79.5MHz -HSync +VSync
        h: width  1280 start 1344 end 1472 total 1664 skew    0 clock   47.8KHz
        v: height  768 start  771 end  778 total  798           clock   59.9Hz
  1280x720 (0x57)   74.4MHz -HSync +VSync
        h: width  1280 start 1336 end 1472 total 1664 skew    0 clock   44.7KHz
        v: height  720 start  721 end  724 total  746           clock   60.0Hz
  1024x768 (0x58)   78.8MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock   60.1KHz
        v: height  768 start  769 end  772 total  800           clock   75.1Hz
  1024x768 (0x59)   75.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1328 skew    0 clock   56.5KHz
        v: height  768 start  771 end  777 total  806           clock   70.1Hz
  1024x768 (0x5a)   65.0MHz -HSync -VSync *current
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x5b)   50.0MHz +HSync +VSync
        h: width   800 start  856 end  976 total 1040 skew    0 clock   48.1KHz
        v: height  600 start  637 end  643 total  666           clock   72.2Hz
  800x600 (0x5c)   49.5MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock   46.9KHz
        v: height  600 start  601 end  604 total  625           clock   75.0Hz
  800x600 (0x5d)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x5e)   36.0MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  640x480 (0x5f)   31.5MHz -HSync -VSync
        h: width   640 start  664 end  704 total  832 skew    0 clock   37.9KHz
        v: height  480 start  489 end  491 total  520           clock   72.8Hz
  640x480 (0x60)   31.5MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock   37.5KHz
        v: height  480 start  481 end  484 total  500           clock   75.0Hz
  640x480 (0x61)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   60.0Hz
  720x400 (0x62)   28.3MHz -HSync +VSync
        h: width   720 start  738 end  846 total  900 skew    0 clock   31.5KHz
        v: height  400 start  412 end  414 total  449           clock   70.1Hz
DVI-0 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x52
    Timestamp:  51751
    Subpixel:   horizontal rgb
    Clones:    
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
S-video disconnected (normal left inverted right x axis y axis)
    Identifier: 0x53
    Timestamp:  51751
    Subpixel:   no subpixels
    Clones:    
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    tv standard:    pal
        supported: ntsc         pal          pal-m        pal-60      
                   ntsc-j       scart-pal    pal-cn       secam       
    load detection: 1 (0x00000001)    range:  (0,1)

---

### Post by realzippy on 2011-08-06
No idea,xrandr is fine.
Start a live CD to see if it works,or if the "error" is "in" the monitor;
can you reset monitor to vanilla ?

---

### Post by Osric1 on 2011-08-06
I have an xbox360 and a TV routed through the same monitor and they are all fine so I doubt it is a monitor issue. It just seems that during a resolution change the display became offset from the monitor.  I have been trying all the other resolutions and have found the 1280x720 (16:9) allows correct. The problem is that when I chose any other resolution it no longer adjusts the borders accordingly resulting in an offset screen. I don't know whether this clarifies things a little or gives a better insight into the underlying issue: for some reason I am unable to properly switch between resolutions.

---

### Post by Osric1 on 2011-08-06
I have an xbox360 and a TV routed through the same monitor and they are all fine so I doubt it is a monitor issue. It just seems that during a resolution change the display became offset from the monitor.  I have been trying all the other resolutions and have found the 1280x720 (16:9) allows correct borders. The problem is that when I chose any other resolution it no longer adjusts the borders accordingly resulting in an offset screen. I don't know whether this clarifies things a little or gives a better insight into the underlying issue: for some reason I am unable to properly switch between resolutions.

---

### Post by Osric1 on 2011-08-06
I have an xbox360 and a TV routed through the same monitor and they are  all fine so I doubt it is a monitor issue. It just seems that during a  resolution change the display became offset from the monitor.  I have  been trying all the other resolutions and have found the 1280x720 (16:9)  allows correct borders. The problem is that when I chose any other  resolution it no longer adjusts the borders accordingly resulting in an  offset screen. I don't know whether this clarifies things a little or  gives a better insight into the underlying issue: for some reason I am  unable to properly switch between resolutions.

---

