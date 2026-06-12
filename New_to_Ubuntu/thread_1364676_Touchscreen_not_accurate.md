---
title: "Touchscreen not accurate"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by ehalls on 2009-12-26
Hi, I have just installed unbuntu 9.10 on my GIGABYTE M912 tablet pc. The touch screen is working, however it is only accurate in the very middle of the screen. As soon as I start to move out a bit it the mouse is slaking after and I cant use the scrollbar or the menu in the top or bottom of the desktop. Does anyone have any clue how to solve the problem?

Best regards Erik

---

### Post by Favux on 2009-12-26
Hi Erik,

Welcome to Ubuntu forums!

A couple questions.  Is it a UMPC touchscreen in your GIGABYTE M912 tablet pc?  If so it may be using the evtouch driver.  Is it?

If so then this might help:  [http://ubuntuforums.org/showthread.php?t=419235](http://ubuntuforums.org/showthread.php?t=419235)

Except in Karmic you would want to modify the evtouch .fdi rather than the xorg.conf.

Hope this helps.

---

### Post by ehalls on 2009-12-27
> **Favux said:**
> Hi Erik,

Welcome to Ubuntu forums!

A couple questions.  Is it a UMPC touchscreen in your GIGABYTE M912 tablet pc?  If so it may be using the evtouch driver.  Is it?

If so then this might help:  [http://ubuntuforums.org/showthread.php?t=419235](http://ubuntuforums.org/showthread.php?t=419235)

Except in Karmic you would want to modify the evtouch .fdi rather than the xorg.conf.

Hope this helps.

Hello, I am not sure what touch screen it is. How do I check that in Unbuntu?

---

### Post by Favux on 2009-12-27
Hi Erik,

> I am not sure what touch screen it is. How do I check that in Unbuntu? 
There are a bunch of ways to check it.  Let's trying entering (copy & paste) in a terminal:
```
grep -i name /proc/bus/input/devices
```
And see what the output is.

---

### Post by ehalls on 2009-12-27
> **Favux said:**
> Hi Erik,


There are a bunch of ways to check it.  Let's trying entering (copy & paste) in a terminal:
```
grep -i name /proc/bus/input/devices
```And see what the output is.

Hi Favux,

This is my output:

erik@erik-laptop:~$ grep -i name /proc/bus/input/devices
N: Name="Power Button"
N: Name="Lid Switch"
N: Name="Power Button"
N: Name="Sleep Button"
N: Name="Macintosh mouse button emulation"
N: Name="AT Translated Set 2 keyboard"
N: Name="Video Bus"
N: Name="USB Optical Mouse"
N: Name="DIALOGUE INC PenMount USB"
N: Name="SynPS/2 Synaptics TouchPad"
N: Name="HDA Digital PCBeep"
erik@erik-laptop:~$

---

### Post by Favux on 2009-12-27
Hi Erik,

OK, it is a "DIALOGUE INC PenMount USB" touchscreen.  If you don't have the driver and penmount .fdi installed another .fdi/driver is probably running it, which is why it isn't working right.  Maybe the Synaptic touchpad driver or evdev.

In Synaptic Package Manager you would look for "xserver-xorg-input-penmount".  Hopefully installing that driver package would also install the appropriate .fdi and things would work on a reboot.  I don't know but it is possible that the driver direct from PenMount would be better.  You might want to check the dates and README's.  See:  [http://www.penmount.com.tw/down_2_1.php](http://www.penmount.com.tw/down_2_1.php)  Look for the  "Ubuntu 9.10 Driver V2.4.4".

Good luck!

---

### Post by ehalls on 2009-12-27
> **Favux said:**
> Hi Erik,

OK, it is a "DIALOGUE INC PenMount USB" touchscreen.  If you don't have the driver and penmount .fdi installed another .fdi/driver is probably running it, which is why it isn't working right.  Maybe the Synaptic touchpad driver or evdev.

In Synaptic Package Manager you would look for "xserver-xorg-input-penmount".  Hopefully installing that driver package would also install the appropriate .fdi and things would work on a reboot.  I don't know but it is possible that the driver direct from PenMount would be better.  You might want to check the dates and README's.  See:  [http://www.penmount.com.tw/down_2_1.php](http://www.penmount.com.tw/down_2_1.php)  Look for the  "Ubuntu 9.10 Driver V2.4.4".

Good luck!


Using the Package Manager didn't work however downloading the driver from the PenMount website included software for calibrating the touch screen. So now it works flawlessly! Thanks Favux!:guitar:

---

### Post by Favux on 2009-12-27
Hi Erik,

That's outstanding!  Nice work.  You are welcome.

---

### Post by Favux on 2009-12-29
Hi Erik,

While looking for something else I stumbled on a bug report about the lack of calibration for PenMount.  It's still open so if you posted on it you would help raise the priority.  Plus it looks like all they need/want is the url to the PenMount driver which you can now give them.

This would be a good thing to do.  Positive Karma so to speak.  :)

The bug report is at:  [https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-input-penmount/+bug/227183](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-input-penmount/+bug/227183)

---

### Post by ehalls on 2009-12-29
> **Favux said:**
> Hi Erik,

While looking for something else I stumbled on a bug report about the lack of calibration for PenMount.  It's still open so if you posted on it you would help raise the priority.  Plus it looks like all they need/want is the url to the PenMount driver which you can now give them.

This would be a good thing to do.  Positive Karma so to speak.  :)

The bug report is at:  [https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-input-penmount/+bug/227183](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-input-penmount/+bug/227183)


Hi Favux,

Ok, so should I register at that forum and say I have fixed the problem by installing the driver you gave me? 

There is one other issue with the touchscreen, when I rotate the screen, which I might want to when converting to the tablet mode because its easier reading on the web that way, the calibration doesn't go with it, so I have to recalibrate. 

And by the way, is there a way to put a shortcut on the panel for rotating the screen so i don't need to go into screen settings all the time?

Best regards

---

### Post by ScottinSoCal on 2009-12-29
> **ehalls said:**
> And by the way, is there a way to put a shortcut on the panel for rotating the screen so i don't need to go into screen settings all the time?

Go into Display Preferences and put a check in "Show displays on panel". You'll get an icon in the panel, near your clock.

---

### Post by Favux on 2009-12-29
Hi Erik,

> Ok, so should I register at that forum and say I have fixed the problem by installing the driver you gave me? 
Right, tell them the story, i.e. the driver in Synaptic didn't allow calibration.   But the new 9.10 deb at PenMount site (give URL) does have calibration and works.
> And by the way, is there a way to put a shortcut on the panel for rotating the screen so i don't need to go into screen settings all the time?
Right click on the Panel and choose 'Add to Panel' and then pick 'Display Geometry Switcher'.
> There is one other issue with the touchscreen, when I rotate the screen, which I might want to when converting to the tablet mode because its easier reading on the web that way, the calibration doesn't go with it, so I have to recalibrate.
Do you mean the cursor doesn't reorient?  Or do you mean the coordinates are then wrong?  Either way post the READ ME or any other related information.  Use Manage Attachments.  If it is too big compress it by right clicking it and telling it to Create Archive.  Maybe instead of 'Display Geometry Switcher' you need a rotation script.  Or something added to the penmount.fdi.  So knowing where that is would also be good.

---

### Post by ehalls on 2009-12-30
> **Favux said:**
> 

Do you mean the cursor doesn't reorient?  Or do you mean the coordinates are then wrong?  Either way post the READ ME or any other related information.  Use Manage Attachments.  If it is too big compress it by right clicking it and telling it to Create Archive.  Maybe instead of 'Display Geometry Switcher' you need a rotation script.  Or something added to the penmount.fdi.  So knowing where that is would also be good.

Hi there,

I'm afraid there is no 'Display Geometry Switcher' on ubuntu netbook remix however, going to Display Preferences and put a check in "Show displays on panel" worked, thanks Scottinsocal.

I went to the site you gave me Favux to report the problem. I just looked at the readme and saw that it doesn't sport screen rotation. Readme is attached but I didn't find penmount.fdi. I have calibrated the touchscreen for the tablet mode since I find no need for using the touchscreen in when I having touchpad, but it would be nice to have them both working. :)

Off topic, is there a way to find your posts and threads on the forum more easily so I don't need to go trough the search engine all the time?

Best regars

---

### Post by Favux on 2009-12-31
Hi Erik,

It looks like it allows rotation.  The README doesn't mention a .fdi so maybe it set up in the xorg.conf.  Let's take a look:
```
gedit /etc/X11/xorg.conf
```

> Off topic, is there a way to find your posts and threads on the forum more easily so I don't need to go trough the search engine all the time?
Well, not really.  You can go to the forum your interested in, or where the post was posted.

---

### Post by ehalls on 2009-12-31
> **Favux said:**
> Hi Erik,

It looks like it allows rotation.  The README doesn't mention a .fdi so maybe it set up in the xorg.conf.  Let's take a look:
```
gedit /etc/X11/xorg.conf
```
Well, not really.  You can go to the forum your interested in, or where the post was posted.

Hi Favux,

The command opens a text file, what should I do in it?

---

### Post by Favux on 2009-12-31
Hi Erik,

Copy it and post it usint the code (#) tags next to the quote tags.

---

### Post by ehalls on 2009-12-31
> **Favux said:**
> Hi Erik,

Copy it and post it usint the code (#) tags next to the quote tags.


```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
  InputDevice  "Penmount" "AlwaysCore"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "dbe"
    Load  "glx"
    Load  "record"
    Load  "dri"
    Load  "extmod"
    Load  "dri2"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "Mobile 945GME Express Integrated Graphics Controller"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


Section "InputDevice"
  Identifier  "Penmount"
  Driver    "penmount"
  Option  "Device"           "/dev/input/event7"
  Option  "Protocol"         "PM6000USB"
  Option  "BaudRate"         "19200"
  Option  "ADBit"            "10"
  Option  "ConfigFile"       "/etc/penmount.dat"
  Option  "RandR"            "0"
  Option  "DebugLevel"       "0"
EndSection


Section "ServerFlags"
  Option  "AutoAddDevices"   "False"
EndSection
```

---

### Post by Favux on 2009-12-31
Hi Erik,

Since the screen is rotating with your Intel video chipset I think we are good.

Change in the PenMount section this line:
```
  Option  "RandR"            "0"
```
to:
```
  Option  "RandR"            "1"
```
and reboot.

Good luck!

---

### Post by ehalls on 2010-01-01
> **Favux said:**
> Hi Erik,

Since the screen is rotating with your Intel video chipset I think we are good.

Change in the PenMount section this line:
```
  Option  "RandR"            "0"
```to:
```
  Option  "RandR"            "1"
```and reboot.

Good luck!

Hi Favux,

That made the touchscreen calibrated in normal mode, but when I rotate the screen and have the computer in tablet mode I have to recalibrate the touchscreen. 

It seem that the touch software doesn't know that I have rotated the screen, if I draw the pen downwards or upwards, the mouse goes left- or rightwards. Maybe there is a possibility to do two calibrations and switch between them when rotating the screen? 

Cheers

---

### Post by Favux on 2010-01-01
Hi Erik,

I'm not clear if adding that did anything for you.  Are you saying touch reoriented before we added that line and you still have the calibration issue you had before?

You'll have to figure out if the calibration program stores a calibrations script somewhere.  If it follows the rules it should be a .config or something in your /home/username directory.  Then you can set up a launcher to run the script.

Check the PenMount site for a FAQ or whatever.  Also see if there's a place to contact them.

By the way nice job on posting on the Launchpad bug report.  :)

And Happy New Year.

---

### Post by ehalls on 2010-01-01
> **Favux said:**
> Hi Erik,

I'm not clear if adding that did anything for you. Are you saying touch reoriented before we added that line and you still have the calibration issue you had before?

You'll have to figure out if the calibration program stores a calibrations script somewhere. If it follows the rules it should be a .config or something in your /home/username directory. Then you can set up a launcher to run the script.

Check the PenMount site for a FAQ or whatever.  Also see if there's a place to contact them.

By the way nice job on posting on the Launchpad bug report.  :)

And Happy New Year.

Hi Favux, Happy New Year, wish you all the best for 2010 :)

So let me explain this in detail;
Before installing any drivers the touch screen worked as long as I was not moving towards the edges of the screen. If I touch on the very edge of the screen, the pointer will be 30 pixels inwards towards the middle. That makes it impossible to scroll or close a maximized window. 

After installing the driver you gave me the touch screen worked very well in the edges. However, if I rotated the screen the coordinates got inverted. Example, if I point at the lower-left corner, the pointer will appear in the upper-left corner. To use the touch screen when the display was rotated I had to recalibrate.

Is most important to use the touch screen in rotated mode (tablet mode). I want to rotate the screen because it's much easier to read web pages that way. I calibrated PenMount when in rotated screen, thus making the touch screen coordinates inverted in laptop mode.

After making the change in the text file you told me, by exchanging 0 for 1, the touch screen got calibrated in laptop mode, but inverted in tablet mode.

Lately I have been experimenting with different Ubuntus, like Xbuntu and UNR. After a while I decided to use Ubuntu, so I installed Ubuntu with the format whole disk option and updated it. When I tried to install PenMount driver once again, the whole system crashed, and I was thrown into the prompt, the same you get to by pressing Ctrl-Alt-F1. When pressing Ctrl-Alt-F7 I just see a blinking marker. I could just press Ctrl-Alt-Del to restart. I have tried install it for 3 times now, but the system always crashes.

Inverted: 
Think a coordinate system on the display with the origin in the middle then the xDisplay=-xPoint
yDisplay=-yPoint


Do you understand what I mean with tablet mode and why I want to rotate the screen when in tablet mode? Please tell me if anything is unclear :) I hope it was not to troublesome for you to read through this long explanation. But the biggest problem now is that the system crashes when trying to install the driver :confused:

I am happy to do the Launchpad report :)

Thanks for all your help!

Erik

---

### Post by Favux on 2010-01-01
Hi Erik,

OK, that's what I needed to know.  I was hoping you were telling me that with the "RandR" line and calibration you were seeing touch rotating in sync with the screen.  In that case there must be something like an xsetwacom rotate command somewhere we could use.  To see what I mean see the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").

> After installing the driver you gave me the touch screen worked very well in the edges. However, if I rotated the screen the coordinates got inverted. Example, if I point at the lower-left corner, the pointer will appear in the upper-left corner. To use the touch screen when the display was rotated I had to recalibrate.
That's what happens if you have no way to rotate the device (touch) along with the screen.

> After making the change in the text file you told me, by exchanging 0 for 1, the touch screen got calibrated in laptop mode, but inverted in tablet mode.
Are you saying it was calibrated in tablet mode and inverted in laptop mode when it was 0?  That was/is the question I am asking you.

---

### Post by ehalls on 2010-01-01
> **Favux said:**
> Hi Erik,

OK, that's what I needed to know.  I was hoping you were telling me that with the "RandR" line and calibration you were seeing touch rotating in sync with the screen.  In that case there must be something like an xsetwacom rotate command somewhere we could use.  To see what I mean see the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").


That's what happens if you have no way to rotate the device (touch) along with the screen.


Are you saying it was calibrated in tablet mode and inverted in laptop mode when it was 0?  That was/is the question I am asking you.

Yes. Because I originally calibrated the screen in tablet mode.

---

### Post by Favux on 2010-01-01
Hi Erik,

Well then try changing:
```
Option  "RandR"            "0"
```
from 0 to 1 and see if that flips touch orientation relative to the screen in laptop mode.  Presumably it will do the opposite in portrait (tablet) mode.

In other words does 0 indicate correct orientation of touch in laptop and 1 correct orientation in tablet?

If so then there must be the equivalent of the xsetwacom command infrastructure somewhere for your touch and the question becomes can we turn
```
Option  "RandR"            "0"
```
into it's command line equivalent and use it in a rotation script?

---

### Post by ehalls on 2010-01-01
I managed to install the driver again, I ran ./install.hs from the ctr-alt-f1 screen. Then the crashed ubuntu started up again, I could login and install the driver :) Really scary, especially for a beginner like me when everything gets black when you are installing a driver :S

---

### Post by Favux on 2010-01-01
Hi Erik,

Ouch.

That's probably the xorg.conf being generated.  In Karmic with Intel video you might not even have an xorg.conf with a default install.  Did you look at the xorg.conf or make a backup copy before you installed PenMount?  But it's suppose to be the 9.10 version so I'm guessing something gets mis-configured with the Intel video.

---

### Post by ehalls on 2010-01-01
> **Favux said:**
> Hi Erik,

Well then try changing:
```
Option  "RandR"            "0"
```from 0 to 1 and see if that flips touch orientation relative to the screen in laptop mode.  Presumably it will do the opposite in portrait (tablet) mode.

In other words does 0 indicate correct orientation of touch in laptop and 1 correct orientation in tablet?

If so then there must be the equivalent of the xsetwacom command infrastructure somewhere for your touch and the question becomes can we turn
```
Option  "RandR"            "0"
```into it's command line equivalent and use it in a rotation script?

This is very strange, now changing the 0 to 1 doesn't do anything. Besides after I login I have to enter the password again because "/usr/sbin/gPen" wants to do changes to my system... I restart the computer everytime, is it enough to log in and log out?

---

### Post by ehalls on 2010-01-01
> **Favux said:**
> Hi Erik,

Ouch.

That's probably the xorg.conf being generated.  In Karmic with Intel video you might not even have an xorg.conf with a default install.  Did you look at the xorg.conf or make a backup copy before you installed PenMount?  But it's suppose to be the 9.10 version so I'm guessing something gets mis-configured with the Intel video.
 
I'm not sure I understand, what is xorg.conf?

---

### Post by ehalls on 2010-01-01
> **ehalls said:**
> I'm not sure I understand, what is xorg.conf?

edit

ahh that's the file we are editing in, no I didn't do a backup.

---

### Post by Favux on 2010-01-01
To make a backup use the copy command:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
To restore the backup from the command line just reverse it:
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

---

### Post by ehalls on 2010-01-02
> **Favux said:**
> To make a backup use the copy command:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```To restore the backup from the command line just reverse it:
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

Hi Favux,
Ok, but is there really a need to backup when we just are changing a number? It's not hard to change back... 

If you understand math, the correct way to describe the disorientation of the touch screen is:

Xdisplay, Ydisplay: where the mouse ends up
Xpoint, Ypoint: where on the screen we actually are pointing

Xpixel=768
Ypixel=1280

origin is in the center of the screen,

Xdisplay =Xpixel*(Ypoint/Ypixel)
Ydisplay =Ypixel*(Xpoint/Xpixel)


I have tried several times now, but changing 0 to 1 doesn't do anything on my current ubuntu install... is there any hope?

By the way, I am in Taiwan right now, so do you know if there is any chinese inc to text recognition in cellwriter?

---

### Post by Favux on 2010-01-02
Hi Erik,

What we were trying to find out was if changing 0 to 1 in:
```
Option  "RandR"            "0"
```
did more than enable the touch to rotate.  From what you're saying it's not clear to me this option does anything.  Apparently you can calibrate touch in whatever orientation you're in, with or without the line, or whether it is 0 or 1.

So in the calibration code you have it must be doing the transform you describe.  With Wacom you can go through the xsetwacom utilities.  That gives you a command line command you can use in a script.  Apparently the PenMount doesn't offer anything like that.  Except, again apparently, in the calibration program's code.  That's what I was suggesting you contact PenMount about.  Some tablets have a feature where a switch in the swivel hinge or a button on the tablet can trigger automatic rotation which may also include any devices like stylus and touch.  Maybe there's a program/code that enables that functionality in your tablet?

Sorry, I haven't seen anything specific about Chinese with CellWriter.  You might want to contact the dev., he seems reponsive.
[http://risujin.org/cellwriter/](http://risujin.org/cellwriter/)
[http://code.google.com/p/cellwriter/](http://code.google.com/p/cellwriter/)

---

### Post by ehalls on 2010-01-02
Hi Favux

> **Favux said:**
> Hi Erik,
What we were trying to find out was if changing 0 to 1 in:
```
Option  "RandR"            "0"
```did more than enable the touch to rotate.  From what you're saying it's not clear to me this option does anything.  Apparently you can calibrate touch in whatever orientation you're in, with or without the line, or whether it is 0 or 1.

No, changing this option does nothing. 


Sorry, I don't really understand the rest you wrote, but there is no button on the computer that rotates the screen. I have contacted penmount but since is says in the readme: "3.Touch Not support screen rotation " I am not very hopeful... I will try to look around and see if I find something. Thanks for the help :) Or do you have any more suggestions?

Best regards

---

### Post by luksa on 2010-01-11
Hi,

I have exactely the same problem on my m912 with Ubuntu 9.10. I think it is a bug in the new Penmount driver. What I found out so far: 

[LIST]
[*] The "RandR" option is definitely what we want - the driver should autodetect rotation when "RandR" = 1
[*]Penmount says here ([http://www.penmount.com/mail/2009/PMY09008_en.htm](http://www.penmount.com/mail/2009/PMY09008_en.htm)) that rotation detection is possible...
[*] I previously had Ubuntu 9.04 installed on my m912 - there the Penmount driver worked fine with the "RandR" option.
[/LIST]
 
Unfortunatly a bug-report mail to Penmount is still unanswered - maybe if more people write directly to Penmount they will correct this issue....

Best Regards
luksa

---

### Post by Favux on 2010-01-11
Hi luksa,

Welcome to Ubuntu forums!

That's what I thought changing the boolean from 0 to 1 (off to on) would do!  I think the fpit driver uses the same option for rotation auto-detection.

So it's a bug.  Thanks for clearing that up.

Good luck with PenMount!  You might also want to post on the launchpad bug to try and get the (fixed) driver in the repository.

---

### Post by ehalls on 2010-01-17
> **luksa said:**
> Hi,

I have exactely the same problem on my m912 with Ubuntu 9.10. I think it is a bug in the new Penmount driver. What I found out so far: 

[LIST]
[*] The "RandR" option is definitely what we want - the driver should autodetect rotation when "RandR" = 1
[*]Penmount says here ([http://www.penmount.com/mail/2009/PMY09008_en.htm](http://www.penmount.com/mail/2009/PMY09008_en.htm)) that rotation detection is possible...
[*] I previously had Ubuntu 9.04 installed on my m912 - there the Penmount driver worked fine with the "RandR" option.
[/LIST]
 
Unfortunatly a bug-report mail to Penmount is still unanswered - maybe if more people write directly to Penmount they will correct this issue....

Best Regards
luksa

Hi Luksa, I will try to install ubuntu 9.04 to try the screen rotation, I'll tell you how it goes. What is your impression of m912? I think it's very slow on ubuntu.. and the web browser sometimes locks and doesn't respond for 5 sec... There is no thread about the computer, maybe I should start one? :)

Best Regards

Erik

---

### Post by luksa on 2010-01-18
Hi Erik,

be careful with 9.04 on the m912, there are ather things that won't work out of the box:

- the support for the Intel graphic chipset is bad (actually the reason why I updated to 9.10)
- the WLAN module requires the madWifi drivers which make problems with the standby mode (manual driver restart after waking up from standby is required).
- the Penmount driver interferes with the touchpad and keyboard - after installing the Penmount driver on 9.04 I had to edit the xorg.conf to get the touchpad and keyboard working properly again...

Now to the m912 in general: My m912x is quite OK with Ubuntu - even better than WinXP, especially the boot time!
I have no problems with Firefox 3.5.

And there is more free software for the touchscreen e.g.: xournal or cellwriter - features that are only available in the tabletPC edition of WinXP....

Best Regards
luksa

---

### Post by luksa on 2010-03-03
Hi,

Today I tried again a mail to penmount - maybe they will answer this time...;)

> 
Dear Sirs,

I seems the RandR option in xorg.conf does not work properly any more with the Ubuntu 9.10 Driver 2.4.4 (Penmount6000 USB)

The RandR option worked fine with Ubuntu 9.04 and the 2.4.1 Driver....

However with Ubuntu 9.10 and the 2.4.4 Driver display rotation with XRandR is only recognized after a new Callibration with gCal.
 
Will there be a fix for this?
In case of a reply, I will post it here....

Best Regards
luksa

---

### Post by luksa on 2010-03-08
Hi,

Got a reply from penmount - and they sent me a new driver which recognizes the screen rotation automatically....:D:D:D

The driver on their website is "PenMount V2.4.4 Driver 20091022"I am now using the "Test Driver 20091228", which work perfectly well on my M912X...

Just write them an email - either they will send the driver to you, or - better - might update the driver available for download on their website....

Best Regards
luksa[FONT=Arial]  
[/FONT]

---

### Post by void_false on 2010-04-30
Hey guys. Maybe it's only me, but after installing the penmount driver i have no scroll on touchpad.

---

### Post by luksa on 2010-05-08
hi,

try adding the following to your xorg.conf:

> Section "InputDevice"
	Identifier 	"Synaptics Touchpad"
	Driver 		"synaptics"
	Option 		"SendCoreEvents" "true"
	Option 		"Device" "/dev/psaux"
	Option 		"Protocol" "auto-dev"
	Option 		"HorizEdgeScroll" "5"
	Option		"SHMConfig" "true"
EndSection

and 
> InputDevice  "Synaptics Touchpad"
in the ServerLayout section of the xorg.conf...

I had to add this to my ubuntu 9.10 xorg.conf...

luksa

---

### Post by luksa on 2010-05-08
Hello,

And a new Penmount Problem::mad:

I just upgraded to 10.04 - I had to remove the old penmount driver before updateing, otherwise the keyboard won't work after the upgrade....fortunately I made a clonezilla backup before...:p

Then I installed the new Penmount driver from their homepage and there are two problems:
1) the calibration only works partially - the crosshair for calibrating is always in the upper left corner, and doesn't move. Fortunately I already know the positions from previous versions, so I could do a rough calibration...;)
2) more serious: The Rotation -Basically the screen rotation is recognized by the driver, but the width and height values are obviously not swapped. That means in portrait mode, the mouse pointer only moves to y=768 instead of 1280...

Has anyone made the same experiences with 10.04 on the m912x ? 

regards
luksa

---

### Post by luksa on 2010-05-12
Hi,

News from Penmount on the rotation issue:

xrandr 1.3 is NOT supported...:mad:
ubuntu 9.10 and 10.04 report v1.3 (xrandr -v), so thats the reason why the official penmount drivers don't work with screen rotation on 9.10 and 10.04...
Anyway, the inoffical testing driver I got from Penmount in an email works on 9.10, but they have no (inoffical) driver for 10.04 right now.

I'll stay with 9.10 for now....:(

regards
luksa

---

### Post by dpsci on 2010-05-15
I'm having this same problem.  If anyone has a workaround I'd love to hear it, otherwise I guess I'll just move back to 9.xx

---

### Post by void_false on 2010-05-15
PenMount has open specs. I dont understand why it doesnt go straight to the kernel. Or at least to repositories.

---

### Post by JaseP on 2010-06-16
Download Penmount's Lucid 10.04 driver, install, then when calibrating make sure to do a 4 point standard calibration, touching the 4 corners from top left in a clockwise pattern.

The main bug is that the touch target doesn't move...

---

### Post by Tiefenrausch on 2010-07-16
WOW hes right ! THX matey :D

---

### Post by luksa on 2010-10-11
hi,

the penmount 3.0.2 driver fixes the calibration and rotation issues!
[http://www.penmount.com/Download/Driver/PenMount/PenMount%20Ubuntu%2010.04%20Driver%20V3.0.2.tar.bz2](http://www.penmount.com/Download/Driver/PenMount/PenMount%20Ubuntu%2010.04%20Driver%20V3.0.2.tar.bz2)

regards, luksa

---

### Post by JaseP on 2011-04-25
Yep, the newest driver fixes the rotation and calibration issues in 10.04... Glad I checked back here. ... More responsive too!!!

---

