---
title: "Screen Resolution still not working"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by bigboy7foru on 2009-09-16
I ran the xrandr command and this was the results:

root@dvvpn:/home/dvvpn# xrandr
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0  


This machine was running on on a much higher resolution before installing Ubuntu.

Any and all help would be appreciated.

Thanks in advance
Aaron

---

### Post by SunnyRabbiera on 2009-09-16
You know ever since Ubuntu lost its decent monitor helper this has been an issue, try openSUSE as it has a great monitor config tool

---

### Post by Ratscallion on 2009-09-16
Try going System -> preferences -> Display, there's a screen res thingy in there... and it's simpler for newer people as it's a GUI.

---

### Post by bigboy7foru on 2009-09-16
There is no display in the preferences
 
im running Ubuntu 8.10
 
whats the program called that I need to download?
 
Thanks for the help guys

---

### Post by Ratscallion on 2009-09-16
Hmm... Try Screen Resolution? There should be something along those lines in the System menus... (that's Administration AND/OR Preferences). I haven't used 8.10 in a while, so I'm not sure here, sorry I can't help more than that!

---

### Post by SunnyRabbiera on 2009-09-16
> **bigboy7foru said:**
> There is no display in the preferences
 
im running Ubuntu 8.10
 
whats the program called that I need to download?
 
Thanks for the help guys

Thats odd, it should be under system > preferences

---

### Post by bigboy7foru on 2009-09-16
its under screen resolution and it only gives 800x600 and 640x480
 
how can I change it? Also it doesnt reconize the monitor at all though?
 
 
> **Ratscallion said:**
> Hmm... Try Screen Resolution? There should be something along those lines in the System menus... (that's Administration AND/OR Preferences). I haven't used 8.10 in a while, so I'm not sure here, sorry I can't help more than that!

---

### Post by HarrisonNapper on 2009-09-16
What kind of monitor do you have? Have you tried searching synaptic for keywords like "monitor" or "display"? There may be some helpful tools there, as well.

---

### Post by rock it on 2009-09-16
Im newbie, but....
I had problems with screen res and It all worked once I had installed my nvidia card driver. Then nvidia x server settings.

dunno if tht will help.

---

### Post by bigboy7foru on 2009-09-16
It's an acer AL2216W
Graphic card is ATI 3D mach64
 
I have searched for the dirvers but i just cannot find them. 
 
 
 
> **HarrisonNapper said:**
> What kind of monitor do you have? Have you tried searching synaptic for keywords like "monitor" or "display"? There may be some helpful tools there, as well.

---

### Post by Ratscallion on 2009-09-16
So you say that the Display settings doesn't help in System -> Preferences? Odd...
I shan't ignore rock it, so try doing what they said.

---

### Post by bigboy7foru on 2009-09-16
Would the nvidia card driver and nvidia x server settings work on an ATI  card??

---

### Post by bigboy7foru on 2009-09-16
so i was able to get something different working but the monitor is posting a message saying input no accepted... im rebooting to see what happens

---

### Post by bigboy7foru on 2009-09-16
well i was able to get it to have a bigger res but when i changed it the monitor  has a screen saver that sayss input is not supported???

---

### Post by SunnyRabbiera on 2009-09-16
> **bigboy7foru said:**
> well i was able to get it to have a bigger res but when i changed it the monitor  has a screen saver that sayss input is not supported???

Hmm, well cant say much here other then maybe another distro lays in your future.

---

### Post by bigboy7foru on 2009-09-16
Well the range i had selected was to large
 
and now im just trying to change it in the xorg.conf file 
 
 
> **SunnyRabbiera said:**
> Hmm, well cant say much here other then maybe another distro lays in your future.

---

### Post by DJonsson2008 on 2009-09-16
A small modification to the xorg.conf did it for me,
I found even just using generic Vesa drivers I 
could get higher resolution and refresh rates. 

As well though its work the price of an Nvidia card
simply for the compatibility it seems, although until
recently my 9000 series seemed to be bleeding edge for
8.04 LTS recent updates have corrected this.

This is discussed more in detail at this link.
[http://ubuntuforums.org/showthread.php?t=1126931&goto=newpost](http://ubuntuforums.org/showthread.php?t=1126931&goto=newpost)

For now this is what I put in my xorg.conf.
for the screen display at 1024x786@76

Section "Monitor"
Identifier "Configured Monitor"
Vendorname "Acer"
Modelname "Acer AL1916W"
Horizsync 30.0-82.0
Vertrefresh 56.0-76.0
EndSection

---

### Post by DJonsson2008 on 2009-09-16
CAVEAT: Make sure via MFG specs or testing on another machine
your monitor can take the parameters you put in xorg.conf.
I've yet to do it myself but it seems somebody could fry
a monitor with the wrong parameters, and sometimes I wonder
if that isn't why do much disclaimer comes with these Linux
graphic drivers and Linux.

---

### Post by bigboy7foru on 2009-09-16
> **DJonsson2008 said:**
> A small modification to the xorg.conf did it for me,
I found even just using generic Vesa drivers I 
could get higher resolution and refresh rates. 
 
As well though its work the price of an Nvidia card
simply for the compatibility it seems, although until
recently my 9000 series seemed to be bleeding edge for
8.04 LTS recent updates have corrected this.
 
This is discussed more in detail at this link.
[http://ubuntuforums.org/showthread.php?t=1126931&goto=newpost](http://ubuntuforums.org/showthread.php?t=1126931&goto=newpost)
 
For now this is what I put in my xorg.conf.
for the screen display at 1024x786@76
 
Section "Monitor"
Identifier "Configured Monitor"
Vendorname "Acer"
Modelname "Acer AL1916W"
Horizsync 30.0-82.0
Vertrefresh 56.0-76.0
EndSection
 
 
 
Do you know the command to edit the xorg.config file??

---

### Post by DJonsson2008 on 2009-09-16
i'm not on a linux box at the moment,
but recall it as

sudo gedit /etc/xll/xorg.conf

or use cd /etc 
cd /x11
and sudo gedit xorg.conf

if my memory serves me well

---

### Post by DJonsson2008 on 2009-09-16
locate xorg.conf 

will tell you where the file is.

then use sudo gedit 

be sure and back up the file you have,
if it is working at all

i believe that something like 

cp xorg.conf xorg_lores.bak would work.

---

### Post by bigboy7foru on 2009-09-17
[http://myy.helia.fi/~karte/acer_al2216w_-_22_inch_monitor_with_linux.html](http://myy.helia.fi/~karte/acer_al2216w_-_22_inch_monitor_with_linux.html)
 
 
fixed it thanks

---

### Post by Ratscallion on 2009-09-17
Now you seem to be done, can you do what the bold bit in my signature says? Thanks :)

---

### Post by bigboy7foru on 2009-09-17
sorry i was trying to figure out how to do it lol thanks :)

---

