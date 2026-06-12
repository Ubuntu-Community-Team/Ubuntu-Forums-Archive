---
title: "help! 8.10 no display"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by candtalan on 2009-01-08
I have a PC with ubuntu 8.04 installed and dual boot with 8.10 also installed.

I use 8.04 on a daily basis, but use 8.10 occasionally to see what is going on.

I have just tried booting into 8.10 and get no video display! I then tried the earlier two kernels, but this did not help.

I used crtl alt F1 terminal to do  updates just in case that would help
sudo apt-get update
sudo apt-get upgrade
and about half a dozen items came down and installed, but - still no display.
When I installed from live CD I had to use the F4 Safe Graphics choice, but then there was no  problem, and I used it for months also with no problem.

Help please?

---

### Post by melojo on 2009-01-08
Boot into 8.10 recovery and you will have an option called xfix

---

### Post by candtalan on 2009-01-08
Thanks
recovery mode
 xfix
unfortunately still no display.

from terminal and lspci (using ubuntu 8.04 that is) I see that I am using
VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
can I make use of this information somehow?
tia

---

### Post by melojo on 2009-01-08
Thats the same card I have and I don't have any problems.

---

### Post by candtalan on 2009-01-08
> **melojo said:**
> Thats the same card I have and I don't have any problems.

That's useful to know.

I guess that means it is not a lack of a driver.

Although I probably was set up using the nvidia restricted driver to try out the compiz effects.

Is there a way of examinimg or changing the choice about nvidia drivers?
tia

---

### Post by candtalan on 2009-01-08
Knowing from a previous response that video driver is almost certainly available and is probably not the problem, I wondered about the monitor.
The Monitor is a flat screen display, labelled as 
edge10
type J170
model VT17X7X

So I guess that whatever is happening, the configuration is not picking up appropriate information about the monitor - or from the monitor. 

I wonder how does the monitor information get collected??

The monitor information contained in my install of 8.04 - which works fine - seems to be as follows, but none of this is seen in the 8.10 configuration:

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic CRT Display"
	Modelname	"Monitor 1280x1024"
	Horizsync	31.5-81.0
	Vertrefresh	50-75
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection

I have also tried the 8.10 by connecting it up to an old CRT monitor. and it works ok with a screen resolution of
1400x1050 (4:3) 60hz

1) is there something I can do to encourage 8.10 to configure this monitor?
2) is this a bug that I should report?
3) am I going to get useful mileage by simply copy paste from xorg.conf 8.04 to 8.10?? if so, this seems a vote of poor confidence in 8.10 of course?


tia

---

### Post by Tomatz on 2009-01-08
Do this:

```
sudo apt-get install envyng-gtk
```

Then

```
envyng -t
```

Now install your graphics drivers (select 1). Then:

```
sudo shutdown -r now
```


Now hopefully things should be ok ;)

---

### Post by candtalan on 2009-01-08
> **Tomatz said:**
> Do this:
```
sudo apt-get install envyng-gtk
```

Thanks, I did this from within 8.10  Although no display was showing, I could use ctrl alt F1 and get a terminal. I then logged into the terminal with my usual information and used the command line at that stage.

> 
Then
```
envyng -t
```
Now install your graphics drivers (select 1). Then:
```
sudo shutdown -r now
```
Now hopefully things should be ok ;)

iirc the [envyng -t] activity ended with an option to reboot as a recommended finish.

For the record
the existing problem driver was identified as 
177.82-0ubuntu0.1 (shown as option zero 0)
and the 
envyng -t 
activity here caused this to be replaced with option 1 as suggested above it became
173.14.12-1-0ubuntu4

It worked! I am most impressed and very appreciative!
Thanks Tomatz!

Questions:
1) I am not aware of how the 'wrong' driver came to be installed. I have not previously made any driver 'choices' at all. Is this a bug I need to file or can I do something ese to avoid this in future I wonder?
2) How is it that an apparently wrong (or different) video driver can cause such trouble for the flat screen display unit but still work apparently ok with the old CRT display unit?

tia

---

### Post by Tomatz on 2009-01-08
> **candtalan said:**
> Thanks, I did this from within 8.10  Although no display was showing, I could use ctrl alt F1 and get a terminal. I then logged into the terminal with my usual information and used the command line at that stage.



iirc the [envyng -t] activity ended with an option to reboot as a recommended finish.

For the record
the existing problem driver was identified as 
177.82-0ubuntu0.1 (shown as option zero 0)
and the 
envyng -t 
activity here caused this to be replaced with option 1 as suggested above it became
173.14.12-1-0ubuntu4

It worked! I am most impressed and very appreciative!
Thanks Tomatz!

Questions:
1) I am not aware of how the 'wrong' driver came to be installed. I have not previously made any driver 'choices' at all. Is this a bug I need to file or can I do something ese to avoid this in future I wonder?
2) How is it that an apparently wrong (or different) video driver can cause such trouble for the flat screen display unit but still work apparently ok with the old CRT display unit?

tia

Your welcome.

I think when you updated, an updated kernel was installed. This can sometimes break the gpu drivers. Usually reinstalling them wont work so i advised you to install envy which completely uninstalls the old drivers(including config). Then it installs the latest nvidia drivers from another repository.

Simple really ;)

---

