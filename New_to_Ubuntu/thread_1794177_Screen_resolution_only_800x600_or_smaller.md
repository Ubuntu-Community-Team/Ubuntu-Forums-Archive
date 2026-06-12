---
title: "Screen resolution only 800x600 or smaller"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by trpted on 2011-06-30
I saw the info at

[http://america.hannsg.net/onweb.jsp?prod_no=333333333:&webno=3333333375](http://america.hannsg.net/onweb.jsp?prod_no=333333333:&webno=3333333375)

that says this monitor/screen Resolution can up to 1280 x 1024 SXGA.

but in System ---> Preferences ---> Display on my ubuntu 10.04 LTS computer I can only go up to 800 x 600.

[http://www.ubuntugeek.com/how-to-change-screen-resolution-in-ubuntu.html](http://www.ubuntugeek.com/how-to-change-screen-resolution-in-ubuntu.html)

Here are some extra details, that you will need to know..

#1 I had another monitor/screen were I had a higher resolution then I have now connected to this computer.

It was a Dell E153FPc that is/was dying..

Note from [http://support.dell.com/support/edocs/monitors/E153fpb/En/specs.htm](http://support.dell.com/support/edocs/monitors/E153fpb/En/specs.htm) the highest that will go is 1024 x 768

#2 Here are the commands, that I ran..

--

*@*-desktop:~$ lspci | grep VGA
00:01.0 VGA compatible controller: Intel Corporation 82810 (CGC) Chipset Graphics Controller (rev 03)
*@*-desktop:~$ sudo lshw -C video
*-display UNCLAIMED
description: VGA compatible controller
product: 82810 (CGC) Chipset Graphics Controller
vendor: Intel Corporation
physical id: 1
bus info: pci@0000:00:01.0
version: 03
width: 32 bits
clock: 66MHz
capabilities: pm vga_controller bus_master cap_list
configuration: latency=0
resources: memory:f8000000-fbffffff(prefetchable) memory:f4000000-f407ffff
*@*-desktop:~$
--

Please help.

Thanks

---

### Post by roololing on 2011-06-30
Quite a few people had this problem. The person on [this forum]("http://ubuntuforums.org/showthread.php?t=1747605&highlight=800+600") seemed to get a solution that worked for them.

---

### Post by wildmanne39 on 2011-06-30
Hi, there are two methods for setting resolution I am going to give you a link for the easiest method most people have a hard time with the second method.
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by trpted on 2011-07-01
> **roololing said:**
> Quite a few people had this problem. The person on [this forum]("http://ubuntuforums.org/showthread.php?t=1747605&highlight=800+600") seemed to get a solution that worked for them.

Ok. 

#1 requested output..

*@*-desktop:~$ xrandr -q
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
*@*-desktop:~$

#2 > **EGamerHDK said:**
> Hit the Super or Windows key and search "Add" and select Additional Drivers. There should be some kind of graphics drivers there hopefully. Select them and activate. Good luck

There are no additional drivers, listed.

#3 The info at [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760) tells me that I can not run **sudo dpkg-reconfigure xserver-xorg**

#4 At [http://ubuntuforums.org/showthread.php?t=690760&page=4](http://ubuntuforums.org/showthread.php?t=690760&page=4)

I told me about xorg.conf located in /etc/X11/ but I can not find that file.

---

### Post by wildmanne39 on 2011-07-01
> **trpted said:**
> Ok. 

#1 requested output..

*@*-desktop:~$ xrandr -q
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
*@*-desktop:~$

#2 

There are no additional drivers, listed.

#3 The info at [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760) tells me that I can not run **sudo dpkg-reconfigure xserver-xorg**

#4 At [http://ubuntuforums.org/showthread.php?t=690760&page=4](http://ubuntuforums.org/showthread.php?t=690760&page=4)

I told me about xorg.conf located in /etc/X11/ but I can not find that file.Hi, open gedit like this
```
gksu gedit
```
then at the top of the window click on open to open a folder, click file system,etc, on the lower right corner of the window click to show all files, then click on X11, then click on xorg.conf.

---

### Post by trpted on 2011-07-02
> **wildmanne39 said:**
> Hi, open gedit like this
```
gksu gedit
```
then at the top of the window click on open to open a folder, click file system,etc, on the lower right corner of the window click to show all files, then click on X11, then click on xorg.conf.

I tried that, (Please see my screen shot) nope.

---

### Post by wildmanne39 on 2011-07-02
> **trpted said:**
> I tried that, (Please see my screen shot) nope.
Hi, That should have worked, I did it on mine when I wrote those instructions to make sure it worked. So you got to the x11 file but the config file did not show up is that right? you can try ctrl+h while you have that file open and see if it unhides the file.

---

### Post by wildmanne39 on 2011-07-02
Hi, please look at my screenshot.

---

### Post by CatKiller on 2011-07-02
gedit is installed and running in that screenshot (Unsaved Document 1). You can't see many windows because the resolution's low...

I don't think xorg.conf is created by default any more. Things get handled automatically. Monitors are able to advertise their capabilities through a method called EDID, which lets resolutions be automatically selected. Some monitors don't bother, and some actively lie. You can tell X what the timings are that your monitor needs for the resolutions that the monitor can handle (the kind of thing that would otherwise be passed through EDID) through xorg.conf.

The fact that the file isn't there by default doesn't mean that you can't use it. If you create it yourself it will still be read. It's a while since I've done this, so I'm a little rusty, but you'll need to create the file and then put in a Monitor Section with the appropriate information, like so

```
Section "Monitor"
        Identifier      "HU171D"
        HorizSync       31-80
        VertRefresh     55-75
EndSection

```(I got those values from the manual that you linked. If that isn't your monitor then those values might damage it.)

It's possible that you'll also need a Screen Section to tell X that you want to use those settings, which might look something like this

```

Section "Screen"
        Identifier      "Single Screen"
        Device          "Default Device"
        Monitor         "HU171D"
EndSection

```

If you need the Screen Section, you might also need a Device Section:

```
Section "Device"
        Identifier      "Default Device"
EndSection

```

---

### Post by wildmanne39 on 2011-07-02
> I don't think xorg.conf is created by default any more. Hi, thanks for that information, I was thinking I might have had to create it myself, but it has been a while and with as many people as I help on here sometimes I can not remember a little detail like that.

---

### Post by JKyleOKC on 2011-07-02
Here's an absolutely minimum version of xorg.conf that you can copy and paste into your favorite editor. Note that it must be owned by root and readable by everyone else (chmod 644 will give you the right permissions).```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```This will use the "vesa" module, which is totally generic and won't support any fancy effects, but will be enough to get you a GUI from which you can work. You may have to add additional lines in the Monitor section to get high resolution, but this should get you started...

---

### Post by CatKiller on 2011-07-03
> **wildmanne39 said:**
> Hi, thanks for that information, I was thinking I might have had to create it myself, but it has been a while and with as many people as I help on here sometimes I can not remember a little detail like that.

Totally. Especially if you upgrade rather than fresh install, you don't necessarily know the state of the default configuration for new users.

---

### Post by trpted on 2011-07-07
I saw the info at [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

This is the output.

> 
*@*-desktop:~$ xrandr
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
*@*-desktop:~$ cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
*@*-desktop:~$ xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
*@*-desktop:~$ xrandr
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
  1024x768_60.00 (0x74)   63.0MHz
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   47.4KHz
        v: height  768 start  771 end  775 total  798           clock   59.4Hz
*@*-desktop:~$ xrandr --addmode VEGA 1024 768
usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --dryrun
  --nograb
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy
      --rotate normal,inverted,left,right
      --left-of <output>
      --right-of <output>
      --above <output>
      --below <output>
      --same-as <output>
      --set <property> <value>
      --scale <x>x<y>
      --transform <a>,<b>,<c>,<d>,<e>,<f>,<g>,<h>,<i>
      --off
      --crtc <crtc>
      --panning <w>x<h>[+<x>+<y>[/<track:w>x<h>+<x>+<y>[/<border:l>/<t>/<r>/<b>]]]
      --gamma <r>:<g>:<b>
      --primary
  --noprimary
  --newmode <name> <clock MHz>
            <hdisp> <hsync-start> <hsync-end> <htotal>
            <vdisp> <vsync-start> <vsync-end> <vtotal>
            [+HSync] [-HSync] [+VSync] [-VSync]
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>
*@*-desktop:~$ xrandr --addmode VEGA 1024x768
xrandr: cannot find output "VEGA"
*@*-desktop:~$ xrandr --addmode vega 1024x768
xrandr: cannot find output "vega"
*@*-desktop:~$ xrandr --addmode vega 1024X768
xrandr: cannot find output "vega"
*@*-desktop:~$ xrandr --addmode vega 1024x768
xrandr: cannot find output "vega"
*@*-desktop:~$ xrandr --addmode 1024x768
usage: xrandr [options]
****
*@*-desktop:~$ xrandr --addmode auto 1024x768
xrandr: cannot find output "auto"
*@*-desktop:~$ xrandr
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
  1024x768_60.00 (0x74)   63.0MHz
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   47.4KHz
        v: height  768 start  771 end  775 total  798           clock   59.4Hz
*@*-desktop:~$ xrandr --addmode --output -- auto 1024x768
usage: xrandr [options]
***
*@*-desktop:~$:~$ xrandr --addmode vesa 1024x768
xrandr: cannot find output "vesa"
*@*-desktop:~$xrandr --addmode VESA 1024x768
xrandr: cannot find output "VESA"
*@*-desktop:~$


#1 Do you have any idea(s), what the heck is going on here?

#2 This screen works correctly under Windows (some people might call it Winblows for some reason)..

#3 Speaking of Windows: Do you recommend that I follow "Obtaining modelines from Windows program PowerStrip" ?

Thanks.

---

### Post by JKyleOKC on 2011-07-07
> **trpted said:**
> #1 Do you have any idea(s), what the heck is going on here?You have to use the predefined port names for those commands; you can't invent your own. The link at 
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) lists a number of them up near the top in the "getting started" section; hopefully one of those will meet your needs.
> **trpted said:**
> #2 This screen works correctly under Windows (some people might call it Winblows for some reason)..Since the video drivers for Linux are totally different, this doesn't mean much other than that your hardware is okay.
> **trpted said:**
> #3 Speaking of Windows: Do you recommend that I follow "Obtaining modelines from Windows program PowerStrip" ?I've never tried it; I found "cvt" to do the job for me. However if it outputs the modeline data in the correct format, it ought to be okay.

Have you tried installing that minimal xorg.conf file I posted a few messages back? If it works at all for you, you can modify its "monitor" section to add the modeline and not bother with "xrandr" at all.

EDIT: Try "xrandr -q" to find out what the port names for your own system are. You'll get a list of resolutions, and near the top of that list will be a line in which the second word is "connected" (there may be several such lines, depending on your driver). The first word of the line is the port name to use with the --addmode command, and it's case-sensitive. Hope this helps!

---

### Post by trpted on 2011-07-07
> **JKyleOKC said:**
> You have to use the predefined port names for those commands; you can't invent your own. The link at 
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) lists a number of them up near the top in the "getting started" section; hopefully one of those will meet your needs.
Since the video drivers for Linux are totally different, this doesn't mean much other than that your hardware is okay.
I've never tried it; I found "cvt" to do the job for me. However if it outputs the modeline data in the correct format, it ought to be okay.

EDIT: Try "xrandr -q" to find out what the port names for your own system are. You'll get a list of resolutions, and near the top of that list will be a line in which the second word is "connected" (there may be several such lines, depending on your driver). The first word of the line is the port name to use with the --addmode command, and it's case-sensitive. Hope this helps!

So this output means...

> 

*@*-desktop:~$ xrandr -q
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
  1024x768_60.00 (0x74)   63.0MHz
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   47.4KHz
        v: height  768 start  771 end  775 total  798           clock   59.4Hz
*@*-desktop:~$ 



Means that I should use

**xrandr --addmode default 1024x768_60.00**

?

Thanks.

[EDIT #1] I tried that command, but this is the same output..

*@*-desktop:~$ xrandr
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   1024x768_60.00   59.4  
*@*-desktop:~$

[EDIT #2]

> 
 
Have you tried installing that minimal xorg.conf file I posted a few messages back? If it works at all for you, you can modify its "monitor" section to add the modeline and not bother with "xrandr" at all.


No, not yet.

Do I have to use

> 
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection


OR do you think I have to use

> 

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"default"
EndSection


?

---

### Post by JKyleOKC on 2011-07-07
Use driver "vesa" in xorg.conf. It's a generic driver that should work with just about any monitor. The "default" name is for a port in your current video driver and may not be the same when you install the xorg.conf.

The new output you get from "xrandr -q" indicates that it now knows about 1024x768 resolution, so you might try the other xrandr commands to set the mode or resolution. I've not done much with xrandr myself, since I tuned my xorg.conf to get the results I need, so I can't give you a definite example, but in general any resolution that you see listed in that output listing should be viable...

Since xrandr and xorg.conf both do essentially the same things, they should not be used at the same time. They're quite likely to battle each other and thus not give you the result one would expect.

---

### Post by wildmanne39 on 2011-07-07
Hi, I tried to use xrandr but it failed I had to use xorg file to fix my problem, but I found a guide on here to use and it was not to hard but it has been awhile so I do not remember exactly how I did it.

---

### Post by trpted on 2011-07-09
After I ran the commands of...

> 
xrandr --newmode "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync

xrandr --addmode default 1024x768_60.00


..I tried to adjust my settings the GUI way, but it did not work.

Here is the error message.

---

### Post by wildmanne39 on 2011-07-09
Hi, I did some researching and found this thread for creating xorg.conf files just in case you do not get it to work with xrandr.
[http://grenage.com/xorg.html](http://grenage.com/xorg.html)

---

