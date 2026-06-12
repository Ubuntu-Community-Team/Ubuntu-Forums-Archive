---
title: "Monitor Problems (AOC spectrum 7 GLrA)"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by jayg25 on 2009-04-18
I bought a lot of 10 machines (Dell Dimension 4100's) and monitors (AOC Sepctrum 7GLrA's)for $100 from an auction and I am trying to set them all up with Ubuntu 8.10 for a local after school program. 

The install of 8.10 goes fine but when I plug in the monitors that came -n the pallet it only allows me to set the resolution to 800*600, if I plug in any other monitor I have and reboot the resolution allows me to go to 1024*768 (which is what I want to set them at). 

The monitors I have are AOC Sepctrum 7GLrA's. What do I need to do to fix this?

---

### Post by freeman2000 on 2009-04-20
[bump]

---

### Post by hesjnet on 2009-04-20
what type of video-card does these machines run?

Type in the terminal:
```
lshw -C video
```

Paste the results.

---

### Post by aeiah on 2009-04-20
this page
[http://ubuntuforums.org/showthread.php?t=983520](http://ubuntuforums.org/showthread.php?t=983520)

is mostly about setting up dual monitor support, but it looks like he/she has a working AOC 7GLRA with all the xorg modelines needed. if you havent messed with xorg.conf before then you should read up on it a bit. i suspect you might find the file is blank when you come to looking at it and copy and pasting everything from the one in the link probably wont work. however, the section here:

```


Section "Monitor"
    Identifier     "Configured Monitor"
    VendorName     "AOC"
    ModelName      "AOC SPECTRUM 7Glr & 7GlrA"
    HorizSync       30.0 - 85.0
    VertRefresh     50.0 - 130.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1400x1050@75" 155.8 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
    ModeLine       "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
EndSection

Section "Monitor"
 #
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Envision AOC A785"
    HorizSync       30.0 - 85.0
    VertRefresh     50.0 - 130.0
    Gamma           1
EndSection

```

should tell X all it needs to know about your monitor. you may very well need other bits of info though of course, because that bit of code says nothing about your graphics card or graphics driver etc

---

### Post by jayg25 on 2009-04-20
> **hesjnet said:**
> what type of video-card does these machines run?

Type in the terminal:
```
lshw -C video
```

Paste the results.
Sorry it took so long I had to work today and wasnt able to get back to the computers.

This is the message I get. 

WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 15
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=1 mingnt=5

---

### Post by jayg25 on 2009-04-20
> **aeiah said:**
> this page
[http://ubuntuforums.org/showthread.php?t=983520](http://ubuntuforums.org/showthread.php?t=983520)

is mostly about setting up dual monitor support, but it looks like he/she has a working AOC 7GLRA with all the xorg modelines needed. if you havent messed with xorg.conf before then you should read up on it a bit. i suspect you might find the file is blank when you come to looking at it and copy and pasting everything from the one in the link probably wont work. however, the section here:

```


Section "Monitor"
    Identifier     "Configured Monitor"
    VendorName     "AOC"
    ModelName      "AOC SPECTRUM 7Glr & 7GlrA"
    HorizSync       30.0 - 85.0
    VertRefresh     50.0 - 130.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1400x1050@75" 155.8 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
    ModeLine       "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
EndSection

Section "Monitor"
 #
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Envision AOC A785"
    HorizSync       30.0 - 85.0
    VertRefresh     50.0 - 130.0
    Gamma           1
EndSection

```

should tell X all it needs to know about your monitor. you may very well need other bits of info though of course, because that bit of code says nothing about your graphics card or graphics driver etc

I tried to edit the x11.conf after reading through a few of the suggestions and no combination would work. I would always end up in a "safe mode" type screen telling me my configuration was corrupt and to reload the default. 

I am going to keep trying to get it to work but feel pretty confidant I dont have a clue what I am doing.

---

### Post by geoff123 on 2009-04-20
From your original setup (800x600). Once logged in can you go into  System > Display and select what you want?

---

### Post by jayg25 on 2009-04-20
> **geoff123 said:**
> From your original setup (800x600). Once logged in can you go into  System > Display and select what you want?

800*600 is the highest resolution that is available.

---

### Post by jayg25 on 2009-04-21
I reloaded one of the machines with fedora and the monitor is able to use 1024*768. I am not really sure what is going on but the x11.conf file in fedora is blank like it is in ubuntu.

Anyone else have any ideas?

---

