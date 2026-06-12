---
title: "[Help] wacom driver on HP tm2"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by sam-tm2 on 2010-05-17
hello, i'm new of the world of ubuntu.

i have an HP tm2, its a tablet pc

i want to get my wacom drivers working, and on this forum there is a discussion about it but i cant understand what i have to do exacly step by step and i cant post in the discussion (maybe because i'm new???)

here is the link
[http://ubuntuforums.org/showthread.php?t=1410752](http://ubuntuforums.org/showthread.php?t=1410752)

please help me to find out how to post in that discussion or how to fix my problem.

i need to get:

rotation working
wacom pen fuctions (draw, erase etc)
finger touch working


thanks to all

---

### Post by Favux on 2010-05-17
Hi sam-tm2,

Welcome to Ubuntu forums!

Let's get the digitizer working first.  Check in Synaptic Package Mangaer that xserver-xorg-input-wacom is installed, and if not install it then reboot.  That's the X driver component of the Wacom drivers.

Let's also check if the usb kernel driver wacom.ko is auto-loading.  In a terminal enter:
```
lsmod | grep [Ww]acom
```

---

### Post by sam-tm2 on 2010-05-18
> **Favux said:**
> Hi sam-tm2,

Welcome to Ubuntu forums!

Let's get the digitizer working first.  Check in Synaptic Package Mangaer that xserver-xorg-input-wacom is installed, and if not install it then reboot.  That's the X driver component of the Wacom drivers.

Let's also check if the usb kernel driver wacom.ko is auto-loading.  In a terminal enter:
```
lsmod | grep [Ww]acom
```

hello! thanks for answer.

the X driver component is correctly installed.

after i got the string you gave me in the terminal this was the output answer:

 wacom                  25044  0 

next step? ;)

cheers

---

### Post by Favux on 2010-05-18
Hi sam-tm2,

Alright it sounds like the TM2 is too new for the default wacom.ko (0.8.4-4?) in Lucid to work.  So that means you need to compile linuxwacom 0.8.6-2 for the wacom.ko.  Remember you're not trying to get the Xdriver, it won't work and besides you already have one.  So just the wacom.ko.  Read Lucid (near the top) of the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") and then read through Section 1 a couple of times.  Once you've got it straight then compile the wacom.ko.  It's not as complicated as it looks.  It just has a lot of explanations.

Edit:  And 0.8.6-2 is suppose to have been fixed so you can compile the wacom.ko on Xserver 1.7.  So you shouldn't have to do the extra directory change in the brackets.

---

### Post by sjones411 on 2010-05-18
The Wacom driver didn't work by default for you?  My pen and touch work by default on my TM2.  Strange...

---

### Post by sam-tm2 on 2010-05-18
> **sjones411 said:**
> The Wacom driver didn't work by default for you?  My pen and touch work by default on my TM2.  Strange...

it works just like the mouse... i mean there is no function about eraser or pen writing, and the finger is read not different from it.

what i want to is the possibility to use finger to scroll windows, and use pen propperly! 

now i'll try to read well and compile my wacom.ko!

i'll give news, thanks

---

### Post by Favux on 2010-05-18
> My pen and touch work by default on my TM2.
And that was in Lucid?  OK, that concerns me.  It could mean something else is going on.  We'd need to look at Xorg.0.log in /var/log/ to see what's going on.

---

### Post by jygf on 2010-06-05
Mouse, pen, eraser, touchpad, all works fine on MP TM2 under Ubuntu Lucid Lynx x86_64. 
I just slightly modified the auto_rotate.sh script provided by waka324 in [http://ubuntuforums.org/showthread.php?t=1447925&highlight=tm2](http://ubuntuforums.org/showthread.php?t=1447925&highlight=tm2) , so that when the screen hides keyboard, the screen auto-rotates according to the position you give it, using the accelerometer. 

This script works only if we added hp-wmi in /etc/modules (as described by waka324). I do not know if reboot is required or not after that.

The script is the following:
[FONT=Courier New][COLOR=DarkSlateBlue]#!/bin/bash


ERASER=$(xinput --list | grep 'Wacom ISDv4 E3 eraser' | grep -o [0-9][0-9])
STYLUS=$(($ERASER+1))
TOUCH=$(xinput --list | grep 'Wacom' | grep -o [0-9][0-9] | grep -v $ERASER | grep -v $STYLUS)

#xsetwacom set $STYLUS TopX -100 
#xsetwacom set $STYLUS TopY 12 
#xsetwacom set $STYLUS BottomX 26170 
#xsetwacom set $STYLUS BottomY 16475

xsetwacom set $STYLUS TPCButton 0
xsetwacom set $STYLUS Button2 3
xsetwacom set $STYLUS Button3 4

old="0-normal"

while true; do
    if [ -e /sys/devices/platform/hp-wmi/tablet ];    then
        new=`cat /sys/devices/platform/hp-wmi/tablet`
        if [[ $new == "0" ]]; then
            rotation="NONE"
            xrot="normal"
        else
            POS=`cat /sys/devices/platform/lis3lv02d/position | awk -F "(" '{print$2}'`
            X=`echo  "$POS" | awk -F "," '{print$1}'`
            Y=`echo  "$POS" | awk -F "," '{print$2}'`
            Z=`echo  "$POS" | awk -F "," '{print$3}'  | awk -F ")" '{print$1}'`
            echo "<"$X,$Y,$Z">"

            if [ $X -lt -25 ]; then
                rotation="NONE"
                xrot="normal"
            elif [ $X -gt 25 ]
            then
                rotation="HALF"
                xrot="inverted"
            elif [ $Y -lt -25 ]
            then
                rotation="CCW"
                xrot="left"
            elif [ $Y -gt 25 ]
            then
                rotation="CW"
                xrot="right"
            fi
        fi

        echo $rotation, $xrot

        new=$new"-"$xrot

        if [[ $new != $old ]]; then

            xrandr -o $xrot
            sleep 1s
            xsetwacom set $STYLUS rotate $rotation 
            xsetwacom set $ERASER rotate $rotation
            xsetwacom set $TOUCH rotate $rotation

            old=$new
        fi
    fi
    sleep 0.5s
done
[/COLOR][/FONT]

---

### Post by Favux on 2010-06-05
Hi jygf,

Welcome to Ubuntu forums!

Nice script.  Say would you do me a favor and determine if the Magick Rotation applet works for the TM2?  It's on the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1"), linked in Method 4.

Thank you in advance.

---

### Post by catarano on 2010-08-22
If I rotate my monitor the pen and the pointer are offset

I tried waka324 startup scripts but the problem still remains

If I try a rotation script that I found on another thread on the tm2

I always get the following error

```
warning: output LVDS1 not found; ignoring
property Evdev Axis Inversion doesn't exist, you need to specify its type and format
property Evdev Axis Calibration doesn't exist, you need to specify its type and format
property Evdev Axes Swap doesn't exist, you need to specify its type and format
property Wacom Rotation doesn't exist, you need to specify its type and format
property Wacom Tablet Area doesn't exist, you need to specify its type and format
```

Can anybody help me with fixing input and rotation?

---

### Post by Favux on 2010-08-22
Hi catarano,

Are you in Lucid?  Rotation scripts are at the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").  You should have the linuxwacom drivers controlling the stylus and touch.  I don't know why the evdev driver would enter into it.  Unless it's not set up correctly for the linuxwacom driver, which has gestures for touch.

---

### Post by catarano on 2010-08-22
> **Favux said:**
> Hi catarano,

Are you in Lucid?  Rotation scripts are at the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").  You should have the linuxwacom drivers controlling the stylus and touch.  I don't know why the evdev driver would enter into it.  Unless it's not set up correctly for the linuxwacom driver, which has gestures for touch.

Yes, I am on lucid.
Just to make one thing clear.

Upstream of everything

Should I uninstall the wacom driver that comes with lucid and install everything from the linuxwacom source

or

should I leave the wacom driver that comes with xorg on lucid plus add the wacom.ko from the linuxwacom sources ?

---

### Post by Favux on 2010-08-22
The problem with uninstalling xserver-xorg-input-wacom is it uninstalls xserver-xorg-input-all and vice versa so leave it in place.  A new "dependency" since Karmic which complicates things.

Updating the wacom.ko from the Lucid default 0.8.4-4 might help.

You might be best off updating the wacom.ko and xf86-input wacom.  See I. and II. in the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1") or Sections 1 & 2 at the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  The updated xf86-input-wacom would get you the new two finger gesture support.  We could also develop a .xsetwacom.sh script for the TM2.

---

### Post by catarano on 2010-08-22
> **Favux said:**
> The problem with uninstalling xserver-xorg-input-wacom is it uninstalls xserver-xorg-input-all and vice versa so leave it in place.  A new "dependency" since Karmic which complicates things.

Updating the wacom.ko from the Lucid default 0.8.4-4 might help.

You might be best off updating the wacom.ko and xf86-input wacom.  See I. and II. in the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1") or Sections 1 & 2 at the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  The updated xf86-input-wacom would get you the new two finger gesture support.  We could also develop a .xsetwacom.sh script for the TM2.

Ok

So I installed the wakom.ko and the Xorg driver following the linuxwacom HOWTO

then I also copied the content of 50-wacom-conf into 10-wacom-conf located in /usr/lib/X11/xorg.conf.d

then I looked at the rotation howto and opted for method #4 and thus I installed the Magick rotate applet.

Now automatic rotation is triggered upon locking the monitor in tablet mode, but then I always have the direction of my pen movement inverted.

The same problem arises if I rotate the monitor using the gnome-control panel.

It is really the last thing that I need to fix, since now even multitouch works....

---

### Post by Favux on 2010-08-22
Hi catarano,

Wow, nice work!

Glad to hear gestures work for the TM2.  Very glad to hear Magick works for the TM2.  I wasn't sure it's swivel hinge sent a signal to wmi.  So that's cool, I can add the TM2 to the list of supported tablets.

What's probably going on is you didn't add the "Device names" (without the quotes) corresponding to stylus, eraser, and touch from:
```
xinput --list
```
to the boxes in Advanced Setup.  Right click on the rotating green arrow icon in the upper left of the top panel and chose Setup.

---

### Post by catarano on 2010-08-24
> **Favux said:**
> Hi catarano,

Wow, nice work!

Glad to hear gestures work for the TM2.  Very glad to hear Magick works for the TM2.  I wasn't sure it's swivel hinge sent a signal to wmi.  So that's cool, I can add the TM2 to the list of supported tablets.

What's probably going on is you didn't add the "Device names" (without the quotes) corresponding to stylus, eraser, and touch from:
```
xinput --list
```
to the boxes in Advanced Setup.  Right click on the rotating green arrow icon in the upper left of the top panel and chose Setup.

that I did, however maybe i did not explain myself properly, as inverted maybe is not the right term.

What I mean is that if I move the pen orizontally, the cursor moves vertically and vice versa....

---

### Post by Favux on 2010-08-24
Hi catarano,

I understood what you meant.  What you are describing is the stylus not rotating with the screen orientation.

So either the xwacom drivers don't have the stylus and say the evdev driver does (check Xorg.0.log in /var/log) or maybe you're not putting the correct "Device name" in the box in Advanced Setup.

---

### Post by catarano on 2010-08-24
> **Favux said:**
> Hi catarano,

I understood what you meant.  What you are describing is the stylus not rotating with the screen orientation.

So either the xwacom drivers don't have the stylus and say the evdev driver does (check Xorg.0.log in /var/log) or maybe you're not putting the correct "Device name" in the box in Advanced Setup.

Ok

So I give you my output from xinput --list
```
 Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E3 Finger touch             	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E3 Pen eraser               	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E3 Pen stylus               	id=13	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=16	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=18	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=8	[slave  keyboard (3)]
    &#8627; Power Button                            	id=9	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=10	[slave  keyboard (3)]
    &#8627; HP Webcam                               	id=14	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=15	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                
```

What do you think I should write as device names in the advanced setup?
Could it work also with the id numbers?

---

### Post by Favux on 2010-08-24
Sure it'll work with the ID numbers unless you are hotplugging something, in which case the numbers can change.

Your stylus = Wacom ISDv4 E3 Pen stylus

Use the whole thing, without quotes, in advanced setup.  In a xsetwacom command you'd use the quotes around it.

---

### Post by catarano on 2010-08-24
> **Favux said:**
> Sure it'll work with the ID numbers unless you are hotplugging something, in which case the numbers can change.

Your stylus = Wacom ISDv4 E3 Pen stylus

Use the whole thing, without quotes, in advanced setup.  In a xsetwacom command you'd use the quotes around it.

Thanks! 

It works now!

I used the id numbers, so let's say for stilus I wrote

id=13 and so on

But now I lost the multitouch functionality.

Will check on it in the next following days.

---

### Post by rvm1989 on 2010-09-02
> **catarano said:**
> Thanks! 

It works now!

I used the id numbers, so let's say for stilus I wrote

id=13 and so on

But now I lost the multitouch functionality.

Will check on it in the next following days.

OW, i didn't know it had MT support uner linux.. Did anyone try the utouch package, or get it working?

as for the autorote script... I am not a fan of autorotate, so i made a script for each orientation

as for the assignment of he variables TOUCH=.. etc i noticed that these values can differ after each boot, and they can be < 10. So i adjusted it a little as follows..

```
 if xinput --list | grep "Finger" | grep -o [0-9][0-9]; then
  TOUCH=$(xinput --list | grep 'Finger' | grep -o [0-9][0-9])
 else
  TOUCH=$(xinput --list | grep 'Finger' | grep -o id=[0-9] | grep -o [0-9])
 fi
```

you could do the for the STYLUS and ERASER as well...

tldr; if your touch or pen doesn't always rotate, use the above code for assignment

---

### Post by Favux on 2010-09-02
Hi rvm1989,

> OW, i didn't know it had MT support uner linux.
Using one of the recent xf86-input-wacom's, or cloning the git, in Lucid you have 2FG (2 finger) gesture support.
> Did anyone try the utouch package, or get it working?
Ubuntu has called for uTouch stack testing in Maverick Meerkat in the last day or so:  [http://ubuntuforums.org/showpost.php?p=9784665&postcount=1](http://ubuntuforums.org/showpost.php?p=9784665&postcount=1)

---

### Post by catarano on 2010-09-02
> **rvm1989 said:**
> OW, i didn't know it had MT support uner linux.. Did anyone try the utouch package, or get it working?

as for the autorote script... I am not a fan of autorotate, so i made a script for each orientation

as for the assignment of he variables TOUCH=.. etc i noticed that these values can differ after each boot, and they can be < 10. So i adjusted it a little as follows..

```
 if xinput --list | grep "Finger" | grep -o [0-9][0-9]; then
  TOUCH=$(xinput --list | grep 'Finger' | grep -o [0-9][0-9])
 else
  TOUCH=$(xinput --list | grep 'Finger' | grep -o id=[0-9] | grep -o [0-9])
 fi
```

you could do the for the STYLUS and ERASER as well...

tldr; if your touch or pen doesn't always rotate, use the above code for assignment

Indeed. In fact now I use the full text entry from xinput --list, because I noticed as well that the ID numbers change from time to time.

Thanks for the interest in the issue.

---

### Post by catarano on 2010-09-02
> **Favux said:**
> Hi rvm1989,


Using one of the recent xf86-input-wacom's, or cloning the git, in Lucid you have 2FG (2 finger) gesture support.

Ubuntu has called for uTouch stack testing in Maverick Meerkat in the last day or so:  [http://ubuntuforums.org/showpost.php?p=9784665&postcount=1](http://ubuntuforums.org/showpost.php?p=9784665&postcount=1)

Just to update a bit on my progress of full compatibility:

After disabling the radeon card I could delete the "nomodeset" option from the kernel options in grub, this allows me to also have faster 3D performance.

However, I noticed that the laptop used to become extremely warm / hot, especially in the bottom left area.

In order to alleviate the problem, I added the "acpi.power_nocheck=1" as a boot option in grub.

This made the things much much cooler and now it runs only 10° C higher than windows 7 (39 vs 29-30).

I guess somehow the fan is still not running full speed.

Does anybody have any idea on how to achieve that?

In addition I brought the battery life to around 5 hours, by first installing the laptop-mode-tools and made them active, then disabling bluetooth plus blacklisting all of the radeon and ati HD audio codecs.

I also made all of the suggestions made by powertop permanent as suggested by this thread:

[http://ubuntuforums.org/showthread.php?t=618964](http://ubuntuforums.org/showthread.php?t=618964)

Still, I do not know how to implement USB autosuspend, plus, in order to save energy, I would like to switch on and off at will the touch screen for fingers, while keeping active the pen touch.

Still I have the problem with both the touchpad and the screen to enable multitouch.

Also by using the gpointing devices control panel I cannot enable two fingers scrolling.

So in this case I really do not know what to do.

Sometimes the right button becomes non-responsive....

---

### Post by Favux on 2010-09-02
Hi catarano,

Looks like you've accomplished a lot.
> plus, in order to save energy, I would like to switch on and off at will the touch screen for fingers, while keeping active the pen touch.
Use the toggle touch script attached to the bottom of the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").  Instructions are in "V. Touch toggle script with notification".
> Still I have the problem with both the touchpad and the screen to enable multitouch.
Do you know what happened before you lost multitouch/gestures?  For example did you do a kernel or kernel header update?

Let's look at:
```
xinput --list
```
again, followed by:
```
xsetwacom list
```
The stylus still works?  And both touch and the stylus rotate?

---

### Post by catarano on 2010-09-03
> **Favux said:**
> Hi catarano,

Looks like you've accomplished a lot.

Use the toggle touch script attached to the bottom of the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").  Instructions are in "V. Touch toggle script with notification".

Do you know what happened before you lost multitouch/gestures?  For example did you do a kernel or kernel header update?

Let's look at:
```
xinput --list
```
again, followed by:
```
xsetwacom list
```
The stylus still works?  And both touch and the stylus rotate?

Switching off the touchscreen works.

However, in this case the stylus works only with left click functionality.
In fact, I found out that the button on the pen, which has right-click functionality is disabled.

---

### Post by catarano on 2010-09-03
> **catarano said:**
> Switching off the touchscreen works.

However, in this case the stylus works only with left click functionality.
In fact, I found out that the button on the pen, which has right-click functionality is disabled.

Right click came back after reinstalling linuxwacom and the xorg-wacom driver from sources

---

