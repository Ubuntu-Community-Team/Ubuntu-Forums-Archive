---
title: "Problem with ubuntu special  effects"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by itsvan on 2008-12-27
Hi my ubuntu isnt lettimg me use any speciall effects such as,,3d Cube or anythign of that sort,,,if i minimize a page i cant get it back,,and all kinds of weird stuff is happening,,,i think it might somethign to do with my drivers or something,,waht can i do???

---

### Post by macintosh on 2008-12-27
> **itsvan said:**
> Hi my Ubuntu isn't letting me use any special effects such as,,3d Cube or anything of that sort if I minimize a page i cant get it back,,and all kinds of weird stuff is happening,,,i think it might something to do with my drivers or something, what can i do???

Right go to synaptic and reinstall ubuntu-desktop go to System Administration then Synaptic Package Manager then click edit and search. Then click on ubuntu-desktop then click on Package then click Mark for Installation then click Edit and Apply!

---

### Post by Elfy on 2008-12-27
What graphics card do you have and have you installed the driver for it - System Admin >Hardware Drivers

What version of ubuntu are you using?

---

### Post by itsvan on 2008-12-28
im running Ubuntu hardy heron...and i have a NVIDIA GEFORCE 7 series,,,,and it was running fine everything was set up perfectly,,but then i turned it on,,and it was all messed up,,,the resolution was all low,and the effects are not goign through

---

### Post by itsvan on 2008-12-28
and i really have no idea how to isntall the drivers or what not,,,so any help is appreciated

---

### Post by itsvan on 2008-12-28
WARNING: you should run this program as super-user.

  *-display UNCLAIMED     

       description: VGA compatible controller

       product: G70 [GeForce 7800 GT]

       vendor: nVidia Corporation

       physical id: 0

       bus info: pci@0000:01:00.0

       version: a1

       width: 64 bits

       clock: 33MHz

       capabilities: vga_controller bus_master cap_list

       configuration: latency=0

---

### Post by Elfy on 2008-12-28
Reinstall the driver with Hardware Drivers in the Sys Admin menu.

If it appears to be installed can you run this and post it here - make sure to put
[noparse]```
[/noparse] at the beginning of the pasted part of the post and [noparse]
```[/noparse] at the end.

```
cat /var/log/Xorg.0.log
```

---

### Post by itsvan on 2008-12-31
(II) NV(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 94.5 MHz   Image Size:  355 x 265 mm
(II) NV(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) NV(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) NV(0): Serial No: 5C53918FG00B
(II) NV(0): Monitor name: DELL  M991
(II) NV(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 96 kHz, PixClock max 210 MHz
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff0010ac017042303047
(II) NV(0): 	210b010208241bbaea5e88a353469824
(II) NV(0): 	11484ca443006159819945593159a94f
(II) NV(0): 	010101010101ea240060410028303060
(II) NV(0): 	1300630911000018000000ff00354335
(II) NV(0): 	3339313846473030420a000000fc0044
(II) NV(0): 	454c4c20204d3939310a2020000000fd
(II) NV(0): 	0032a01e6015000a20202020202000b6
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(II) NV(0): Unable to detect which CRTCNumber...
(==) NV(0): ...Defaulting to CRTCNumber 0
(II) NV(0): Using CRT on CRTC 0
(II) NV(0): EDID vendor "DEL", prod id 28673
(II) NV(0): Using EDID range info for horizontal sync
(II) NV(0): Using EDID range info for vertical refresh
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 -hsync -vsync (68.7 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "1024x768"x84.9   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync (68.7 kHz)
(II) NV(0): Modeline "1280x1024"x84.8  159.50  1280 1376 1512 1744  1024 1027 1034 1078 -hsync +vsync (91.5 kHz)
(II) NV(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) NV(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) NV(0): Modeline "1600x1200"x75.0  204.75  1600 1720 1888 2176  1200 1203 1207 1255 -hsync +vsync (94.1 kHz)
(--) NV(0): VideoRAM: 262144 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): Configured Monitor: Using hsync range of 30.00-96.00 kHz
(II) NV(0): Configured Monitor: Using vrefresh range of 50.00-160.00 Hz
(II) NV(0): Configured Monitor: Using maximum pixel clock of 210.00 MHz
(II) NV(0): Estimated virtual size for aspect ratio 1.3333 is 1600x1200
(II) NV(0): Clock range:  12.00 to 400.00 MHz
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NV(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NV(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(--) NV(0): Virtual size is 1600x1200 (pitch 1600)
(**) NV(0): *Driver mode "1600x1200": 204.8 MHz, 94.1 kHz, 75.0 Hz
(II) NV(0): Modeline "1600x1200"x75.0  204.75  1600 1720 1888 2176  1200 1203 1207 1255 -hsync +vsync (94.1 kHz)
(**) NV(0): *Default mode "1600x1200": 202.5 MHz, 93.8 kHz, 75.0 Hz
(II) NV(0): Modeline "1600x1200"x75.0  202.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (93.8 kHz)
(**) NV(0): *Default mode "1600x1200": 189.0 MHz, 87.5 kHz, 70.0 Hz
(II) NV(0): Modeline "1600x1200"x70.0  189.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (87.5 kHz)
(**) NV(0): *Default mode "1600x1200": 175.5 MHz, 81.2 kHz, 65.0 Hz
(II) NV(0): Modeline "1600x1200"x65.0  175.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (81.2 kHz)
(**) NV(0): *Default mode "1600x1200": 162.0 MHz, 75.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(**) NV(0): *Default mode "1400x1050": 184.0 MHz, 93.9 kHz, 85.3 Hz
(II) NV(0): Modeline "1400x1050"x85.3  184.00  1400 1464 1656 1960  1050 1051 1054 1100 +hsync +vsync (93.9 kHz)
(**) NV(0): *Default mode "1400x1050": 155.8 MHz, 81.5 kHz, 74.8 Hz
(II) NV(0): Modeline "1400x1050"x74.8  155.80  1400 1464 1784 1912  1050 1052 1064 1090 +hsync +vsync (81.5 kHz)
(**) NV(0): *Default mode "1400x1050": 151.0 MHz, 77.0 kHz, 70.0 Hz
(II) NV(0): Modeline "1400x1050"x70.0  151.00  1400 1464 1656 1960  1050 1051 1054 1100 +hsync +vsync (77.0 kHz)
(**) NV(0): *Default mode "1400x1050": 122.0 MHz, 64.9 kHz, 60.0 Hz
(II) NV(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
(**) NV(0): *Driver mode "1280x1024": 159.5 MHz, 91.5 kHz, 84.8 Hz
(II) NV(0): Modeline "1280x1024"x84.8  159.50  1280 1376 1512 1744  1024 1027 1034 1078 -hsync +vsync (91.5 kHz)
(**) NV(0): *Driver mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(**) NV(0): *Default mode "1280x1024": 157.5 MHz, 91.1 kHz, 85.0 Hz
(II) NV(0): Modeline "1280x1024"x85.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(**) NV(0): *Default mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(**) NV(0): *Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) NV(0): *Default mode "1440x900": 108.8 MHz, 56.9 kHz, 60.2 Hz
(II) NV(0): Modeline "1440x900"x60.2  108.84  1440 1472 1880 1912  900 918 927 946 +hsync +vsync (56.9 kHz)
(**) NV(0): *Default mode "1280x960": 148.5 MHz, 85.9 kHz, 85.0 Hz
(II) NV(0): Modeline "1280x960"x85.0  148.50  1280 1344 1504 1728  960 961 964 1011 +hsync +vsync (85.9 kHz)
(**) NV(0): *Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(**) NV(0): *Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 (49.7 kHz)
(**) NV(0): *Default mode "1152x864": 121.5 MHz, 77.5 kHz, 85.1 Hz
(II) NV(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(**) NV(0): *Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) NV(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) NV(0): *Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x768"x60.0   80.14  1280 1344 1480 1680  768 769 772 795 (47.7 kHz)
(**) NV(0): *Default mode "1152x768": 65.0 MHz, 44.2 kHz, 54.8 Hz
(II) NV(0): Modeline "1152x768"x54.8   65.00  1152 1178 1314 1472  768 771 777 806 +hsync +vsync (44.2 kHz)
(**) NV(0): *Driver mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) NV(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 -hsync -vsync (68.7 kHz)
(**) NV(0): *Driver mode "1024x768": 94.5 MHz, 68.7 kHz, 84.9 Hz
(II) NV(0): Modeline "1024x768"x84.9   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync (68.7 kHz)
(**) NV(0): *Driver mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) NV(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(**) NV(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) NV(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(**) NV(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) NV(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) NV(0): *Default mode "1024x768": 133.5 MHz, 95.3 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "1024x768"x60.0  133.47  1024 1100 1212 1400  768 768 770 794 doublescan -hsync +vsync (95.3 kHz)
(**) NV(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) NV(0): *Default mode "1024x768": 44.9 MHz, 35.5 kHz, 86.9 Hz (I)
(II) NV(0): Modeline "1024x768"x86.9   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(**) NV(0): *Default mode "960x720": 117.0 MHz, 90.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "960x720"x60.0  117.00  960 1024 1128 1300  720 720 722 750 doublescan -hsync +vsync (90.0 kHz)
(**) NV(0): *Default mode "928x696": 109.2 MHz, 86.4 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "928x696"x60.1  109.15  928 976 1088 1264  696 696 698 719 doublescan -hsync +vsync (86.4 kHz)
(**) NV(0): *Default mode "896x672": 102.4 MHz, 83.7 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "896x672"x60.0  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync (83.7 kHz)
(**) NV(0): *Default mode "960x600": 115.0 MHz, 91.0 kHz, 72.8 Hz (D)
(II) NV(0): Modeline "960x600"x72.8  115.00  960 968 1048 1264  600 600 602 625 doublescan -hsync -vsync (91.0 kHz)
(**) NV(0): *Default mode "960x600": 96.6 MHz, 74.5 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "960x600"x60.0   96.58  960 1024 1128 1296  600 600 602 621 doublescan (74.5 kHz)
(**) NV(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) NV(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) NV(0): *Driver mode "800x600": 56.8 MHz, 53.7 kHz, 84.9 Hz
(II) NV(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(**) NV(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) NV(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) NV(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) NV(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) NV(0): *Default mode "800x600": 101.2 MHz, 93.8 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "800x600"x75.0  101.25  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (93.8 kHz)
(**) NV(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) NV(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) NV(0): *Default mode "800x600": 94.5 MHz, 87.5 kHz, 70.0 Hz (D)
(II) NV(0): Modeline "800x600"x70.0   94.50  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (87.5 kHz)
(**) NV(0): *Default mode "800x600": 87.8 MHz, 81.2 kHz, 65.0 Hz (D)
(II) NV(0): Modeline "800x600"x65.0   87.75  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (81.2 kHz)
(**) NV(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "800x600": 81.0 MHz, 75.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "800x600"x60.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz)
(**) NV(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NV(0): *Default mode "840x525": 73.6 MHz, 65.2 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "840x525"x60.1   73.57  840 892 984 1128  525 525 527 543 doublescan (65.2 kHz)
(**) NV(0): *Default mode "700x525": 92.0 MHz, 93.9 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "700x525"x85.3   92.00  700 732 828 980  525 525 527 550 doublescan +hsync +vsync (93.9 kHz)
(**) NV(0): *Default mode "700x525": 77.9 MHz, 81.5 kHz, 74.8 Hz (D)
(II) NV(0): Modeline "700x525"x74.8   77.90  700 732 892 956  525 526 532 545 doublescan +hsync +vsync (81.5 kHz)
(**) NV(0): *Default mode "700x525": 75.5 MHz, 77.0 kHz, 70.0 Hz (D)
(II) NV(0): Modeline "700x525"x70.0   75.50  700 732 828 980  525 525 527 550 doublescan +hsync +vsync (77.0 kHz)
(**) NV(0): *Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "700x525"x60.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz)
(**) NV(0): *Default mode "640x512": 78.8 MHz, 91.1 kHz, 85.0 Hz (D)
(II) NV(0): Modeline "640x512"x85.0   78.75  640 672 752 864  512 512 514 536 doublescan +hsync +vsync (91.1 kHz)
(**) NV(0): *Default mode "640x512": 67.5 MHz, 80.0 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "640x512"x75.0   67.50  640 648 720 844  512 512 514 533 doublescan +hsync +vsync (80.0 kHz)
(**) NV(0): *Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x512"x60.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz)
(**) NV(0): *Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(II) NV(0): Modeline "720x450"x60.2   54.42  720 736 940 956  450 459 463 473 doublescan +hsync +vsync (56.9 kHz)
(**) NV(0): *Driver mode "640x480": 35.0 MHz, 42.9 kHz, 84.6 Hz
(II) NV(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(**) NV(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) NV(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0): *Default mode "640x480": 74.2 MHz, 85.9 kHz, 85.1 Hz (D)
(II) NV(0): Modeline "640x480"x85.1   74.25  640 672 752 864  480 480 482 505 doublescan +hsync +vsync (85.9 kHz)
(**) NV(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) NV(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(**) NV(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) NV(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) NV(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) NV(0): *Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x480"x60.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz)
(**) NV(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) NV(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) NV(0): *Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) NV(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) NV(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x400"x60.0   41.73  640 672 740 840  400 400 402 414 doublescan (49.7 kHz)
(**) NV(0): *Default mode "576x432": 60.8 MHz, 77.5 kHz, 85.2 Hz (D)
(II) NV(0): Modeline "576x432"x85.2   60.75  576 608 672 784  432 432 434 455 doublescan +hsync -vsync (77.5 kHz)
(**) NV(0): *Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "576x432"x75.0   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync (67.5 kHz)
(**) NV(0): *Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "640x384"x60.1   40.07  640 672 740 840  384 384 386 397 doublescan (47.7 kHz)
(**) NV(0): *Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) NV(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(**) NV(0): *Default mode "576x384": 32.5 MHz, 44.2 kHz, 54.8 Hz (D)
(II) NV(0): Modeline "576x384"x54.8   32.50  576 589 657 736  384 385 388 403 doublescan +hsync +vsync (44.2 kHz)
(**) NV(0): *Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(II) NV(0): Modeline "512x384"x85.0   47.25  512 536 584 688  384 384 386 404 doublescan +hsync +vsync (68.7 kHz)
(**) NV(0): *Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "512x384"x75.0   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync (60.0 kHz)
(**) NV(0): *Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) NV(0): Modeline "512x384"x70.1   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync (56.5 kHz)
(**) NV(0): *Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
(**) NV(0): *Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.6 Hz (D)
(II) NV(0): Modeline "512x384"x86.6   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync (35.5 kHz)
(**) NV(0): *Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) NV(0): Modeline "416x312"x74.7   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync (49.7 kHz)
(**) NV(0): *Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "400x300"x85.3   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync (53.7 kHz)
(**) NV(0): *Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) NV(0): Modeline "400x300"x75.1   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync (46.9 kHz)
(**) NV(0): *Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) NV(0): Modeline "400x300"x72.2   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync (48.1 kHz)
(**) NV(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) NV(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) NV(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) NV(0): *Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(II) NV(0): Modeline "320x240"x85.2   18.00  320 348 376 416  240 240 242 254 doublescan -hsync -vsync (43.3 kHz)
(**) NV(0): *Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "320x240"x75.0   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync (37.5 kHz)
(**) NV(0): *Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) NV(0): Modeline "320x240"x72.8   15.75  320 332 352 416  240 244 246 260 doublescan -hsync -vsync (37.9 kHz)
(**) NV(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(**) NV(0): *Default mode "360x200": 17.8 MHz, 37.9 kHz, 85.0 Hz (D)
(II) NV(0): Modeline "360x200"x85.0   17.75  360 378 414 468  200 200 202 223 doublescan -hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "320x200"x85.3   15.75  320 336 368 416  200 200 202 222 doublescan -hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "320x175"x85.3   15.75  320 336 368 416  175 191 192 222 doublescan +hsync -vsync (37.9 kHz)
(**) NV(0): Display dimensions: (360, 270) mm
(**) NV(0): DPI set to (112, 112)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] 0	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xd3000000 - 0xd3000fff (0x1000) MX[B]
	[8] -1	0	0xd3001000 - 0xd3001fff (0x1000) MX[B]
	[9] -1	0	0xd3002000 - 0xd3002fff (0x1000) MX[B]
	[10] -1	0	0xd3003000 - 0xd3003fff (0x1000) MX[B]
	[11] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[12] -1	0	0xd3004000 - 0xd3004fff (0x1000) MX[B]
	[13] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[19] 0	0	0x0000a000 - 0x0000a07f (0x80) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[23] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[24] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[25] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[26] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[27] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[28] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[29] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[30] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[31] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[32] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[33] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[34] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[35] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[36] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[37] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[38] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[39] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
	[40] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[41] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) NV(0): Write-combining range (0xc0000000,0x10000000)
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(II) NV(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"

---

