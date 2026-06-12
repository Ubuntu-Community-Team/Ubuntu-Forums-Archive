---
title: "Display screen doesnt fit monitor size"
date: 2011-08-18
forum: New to Ubuntu
---

### Post by dangerboy77 on 2011-08-18
Well hello all newborn linux/ubuntu users of which im the youngest, the ubilical cord from windows is till there, but barely, about once every two weeks some bad nutrients from mother bill gates is fed up it.  

Ok my Issue:  Geforce4 440 Go 64mb on Kubuntu 11.04 distro (natty narwhal)  display does not fit monitor.Tried all resolutions in gui system display to no avail. downloaded .run driver from nvidia tried to install with x server killed but install fails (i have minimal experience with terminal commands basic cp/mv/mk/ls/cd/)

Please give me the Kubuntu nutrients i need so i can grow into a superbuntu.......

---

### Post by frankbooth on 2011-08-19
[LIST]
[*]What monitor do you have?
[*]Which resolutions are currently available?
[/LIST]

If you're 100% sure your monitor supports another resolution, you can add it manually, read more [here]("https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions").

---

### Post by realzippy on 2011-08-19
If you have problems with that link,post the output from

```
xrandr -q
```

---

### Post by dangerboy77 on 2011-08-19
Thanks to you both: 
Output for xrandr -q

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA-1 disconnected (normal left inverted right x axis y axis)
LVDS-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+   59.9  
   800x600        59.9  
   640x480        59.4  
   720x400        59.6  
   640x400        60.0  
   640x350        59.8  
TV-1 disconnected (normal left inverted right x axis y axis)
TV-2 disconnected (normal left inverted right x axis y axis)
darkfire@darkfire-8060:~$ 


Thanks for the quick replies guys

---

### Post by realzippy on 2011-08-19
Ok,currently you are on 1024x768....which resolution do you want?
If you don't know tell us -as already asked  ;-)  -which monitor model you
run.

---

### Post by dangerboy77 on 2011-08-19
Its alaptop highgrade notino model 8060.  On the back of the laptop scree or monitor it says w6700.  

Just to check were on the same page - full descriptin of the problem is display on the monitor/laptopscreen is that it fits from left to right until  it gets 3/4 of the way /all elements of the  gui desktop are there.  
Resolution I want is just any resolution that will fit the full physiccal screen/imean the one I'm on has always done it on many a larger screen before.   
Hope I'm helping you to help me.  -  if there is a way for me to be more specific about the laptoop screen model, please tell me how

---

### Post by westie457 on 2011-08-19
Hi.
I had a similar problem some time ago with an (already) old LCD screen. The remedy in my case was to adjust the refresh rate. Unfortunately I cannot remember whether it had to go up or down. 

This might work for you.

---

### Post by dangerboy77 on 2011-08-19
Further surfing reveals its really a hi grade notino w6700 not 8060 thou system name in terminal is 8060. As is on a sticker quoting model no 8060 on the back

Its maximum res is aparantly 1280x854

---

### Post by dangerboy77 on 2011-08-19
Hey westie I've trie d soem of that but not all variations of the available refresh rates and resolutions---jess typing on a pad is hard going -excuse spelling but thanks for the suggestion

---

### Post by realzippy on 2011-08-20
So,if it is this laptop:
[http://www.pcpro.co.uk/reviews/laptops/38678/hi-grade-notino-w6700](http://www.pcpro.co.uk/reviews/laptops/38678/hi-grade-notino-w6700)

..is it ?
..then you want 1280 x 854 resolution. !?

---

### Post by dangerboy77 on 2011-08-20
Yes that is the one.
Ok so how to add the  1,024 x 768 res then......as seemingly xrandr doesnt show it as available

---

### Post by realzippy on 2011-08-20
???
you are already on 1024x768...!?

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA-1 disconnected (normal left inverted right x axis y axis)
LVDS-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
[COLOR="Green"]1024x768 60.0*+ 59.9[/COLOR]
800x600 59.9
640x480 59.4
720x400 59.6
640x400 60.0
640x350 59.8

---

### Post by realzippy on 2011-08-20
Ok,guess a typo and you meant
1280 x 854...

So try:

```
xrandr --newmode "1280x854_60.00"   89.25  1280 1352 1480 1680  854 857 867 887 -hsync +vsync
```
```
xrandr --addmode LVDS-1 1280x854_60.00
```
```
xrandr --output LVDS-1 --mode 1280x854_60.00
```

...if it works,you had to made this permanent (edit a file..)

---

### Post by dangerboy77 on 2011-08-20
yes a typo,(damn newbies)
Im working on your suggestions now

---

### Post by dangerboy77 on 2011-08-20
Well that was a real zippy solution --- you have opened my my mind a bit more to the world of xrandr. 

Ok lets make it permanent now that i have a full gui desktop

---

### Post by dangerboy77 on 2011-08-20
im stabbing in the dark and guessing its something to do with xconf

---

### Post by realzippy on 2011-08-20
Btw,
my username means the "real" zippy (the pinhead),not being *real* zippy...
[http://en.wikipedia.org/wiki/Zippy_the_Pinhead](http://en.wikipedia.org/wiki/Zippy_the_Pinhead)

Yeah,make it permanent...I honestly don 't know how to do this in Kubuntu,
the way it is done in gnome does -of course- **not** work.
Since I escaped to Kubuntu 3 days ago,I have no idea (yet).
Will check this out,but now it is soccer time,so this has to wait a few hours.Suggest googling:
xrandr+permanent+KDE 


You could check the monitor settings,maybe now -after you have run the commands- the resolution is available..

---

### Post by dangerboy77 on 2011-08-20
yeah i gathered you would have a more "indepth meaning to your alias"

Welcome to Kubuntu ive been using it for 2 years but been very ignorant about its capabilities.  Ive started studying Python and thanks to you im now able to do it on a fullscreen kubuntu distro.

And yes ive been constantly googling while youve been tutoring me, and trying to make things happen between responses.  
Had several pages open on xrandr permanentcy settings.....enjoy the soccer...(in which country do they call it soccer....certainly not the uk........It must be America...DINGBURG!!!)

---

### Post by realzippy on 2011-08-20
...yeah,Dingburg,Germany.

Found this:
[https://wiki.kubuntu.org/X/Config/Resolution](https://wiki.kubuntu.org/X/Config/Resolution)

So try:

```
kdesudo kate /etc/kde4/kdm/Xsetup
```

and paste the commands there (guess below the existing).
No idea if it works..

---

### Post by dangerboy77 on 2011-08-20
just downloading gedit for the job

---

### Post by dangerboy77 on 2011-08-20
yes i found that page too but still trying to get my head around how to acutually make the change

---

### Post by eltonw on 2011-08-20
> **dangerboy77 said:**
> Further surfing reveals its really a hi grade notino w6700 not 8060 thou system name in terminal is 8060. As is on a sticker quoting model no 8060 on the back

Its maximum res is aparantly 1280x854
As it appears to be a non-standard resolution, you would need to configure your screen resolution 

1) via the command line as root (superuser), using either xorgconfig or xf86config to re-configure the X System (i.e. the system display parameters). 
***or *** 
2) from a console prompt, (as root) manually edit your X11 file:

$ cd /etc/X11
$ gedit xorg.conf

---

### Post by realzippy on 2011-08-20
> **dangerboy77 said:**
> just downloading gedit for the job

why not using kate ?

---

### Post by dangerboy77 on 2011-08-20
Hey Im using it now, ive been using gedit as it seems to have more user friendlyness options for viewing line numbers and window tabs.  I know you can do all this with kate, i just havnt explored kate properly yet.

---

### Post by dangerboy77 on 2011-08-20
Ok realzippy, im in kate and im in Xsetup file ,, Whats next.

Ive looked at all the documentation but im just not at the level where i can fully understand what to write exactly in the file.

---

### Post by edwardpatch1 on 2011-08-20
same is happening here the desktop of ubuntu 10.04 will not  fit with my screeen why

---

### Post by dangerboy77 on 2011-08-20
ELTON, Whats the difference between doing it in xorg.conf and xsetup?

---

### Post by dangerboy77 on 2011-08-20
> **edwardpatch1 said:**
> same is happening here the desktop of ubuntu 10.04 will not  fit with my screeen why
EDWARD have you read through the whole thread

---

### Post by realzippy on 2011-08-20
> **dangerboy77 said:**
> Ok realzippy, im in kate and im in Xsetup file ,, Whats next.

Ive looked at all the documentation but im just not at the level where i can fully understand what to write exactly in the file.

There might be only 1 line:
/sbin/initctl -q emit login-session-start DISPLAY_MANAGER=kdm

Here your 3 xrandr commands:

```
#! /bin/sh
# Xsetup - run as root before the login dialog appears

#xconsole -geometry 480x130-0-0 -notify -verbose -fn fixed -exitOnFail -file /dev/xconsole &

/sbin/initctl -q emit login-session-start DISPLAY_MANAGER=kdm
xrandr --newmode aso............
xrandr --addmode aso............
xrandr  aso.............

```

---

### Post by edwardpatch1 on 2011-08-20
> **dangerboy77 said:**
> EDWARD have you read through the whole thread

yes but none of it helped me my screen is a philips and modle number is 17B2302Q

---

### Post by realzippy on 2011-08-20
> **edwardpatch1 said:**
> yes but none of it helped me my screen is a philips and modle number is 17B2302Q

things get confusing when jumping in with different hardware.
suggest you open a new thread,or edit the values for your monitor.
:(

---

### Post by edwardpatch1 on 2011-08-20
> **realzippy said:**
> things get confusing when jumping in with different hardware.
suggest you open a new thread,or edit the values for your monitor.
:(
i just need to know how to make it fit why do u need the moniter details

---

### Post by dangerboy77 on 2011-08-20
Realzippy, that has worked for me, great thanks you know some code

A question though, do you know how to set it up in the xorg.conf   file? (look at the disadvantages of doing it in Xsetup [https://wiki.kubuntu.org/X/Config/Resolution#Dynamically_setup_with_xrandr](https://wiki.kubuntu.org/X/Config/Resolution#Dynamically_setup_with_xrandr))

---

### Post by realzippy on 2011-08-20
If editing existing script does not work,create a script in your
home and add it to autostart.
```
kate resolution.sh  #or whatever
```
paste in:

```
#!/bin/bash
xrandr --newmode "1280x854_60.00"   89.25  1280 1352 1480 1680  854 857 867 887 -hsync +vsync
xrandr --addmode LVDS-1 1280x854_60.00
xrandr --output LVDS-1 --mode 1280x854_60.00
```
make executable:
```
chmod +x resolution.sh
```

Alt+F2,autostart,Add script.


**Edit.**
This would have worked also. ;-)

---

### Post by realzippy on 2011-08-20
> **dangerboy77 said:**
> 
A question though, do you know how to set it up in the xorg.conf   file? (look at the disadvantages of doing it in Xsetup [https://wiki.kubuntu.org/X/Config/Resolution#Dynamically_setup_with_xrandr](https://wiki.kubuntu.org/X/Config/Resolution#Dynamically_setup_with_xrandr))

Nowadays there is no xorg.conf,you had to create it first.
(Xorg --configure,stop running X before)
Then you had to edit the modeline in the "monitor" section and again
the resolution in a Subsection into the "Screensection"...


...disturbed by screen resizing?

---

### Post by realzippy on 2011-08-20
> **edwardpatch1 said:**
> i just need to know how to make it fit why do u need the moniter details

Not all details,but the resolution you want.
Monitor's native is best.

We also need your 
```
xrandr -q
```
output.Might be possible that your resolution is limited due to other reasons.The *screen maximum* shown by this command is a good hint.also need screen name reported.

---

### Post by dangerboy77 on 2011-08-20
REALZIPPY it has worked, the only thing thats a bit screwy is the login screen, other than that im very happy that i can go study python now. Thanks allot Zippy.

Its pretty amazing that i got this kind of support through joining the forum, which i have visited many times in the past 2 years (hitting and running)  I had this issue with this very laptop a year ago.  I couldnt find the answer after a week of surfing (obviousley not knowing what to surf for) and then changed it back to XP.  If i only decided not to be so closed minded then, i would have had kubuntu on it a year ago.

---

### Post by realzippy on 2011-08-20
The login screen might be alright if xorg.conf was used,so if you want to go on,press alt+ctrl+F1,log in at shell,run
```
sudo service kdm stop
```

```
sudo Xorg -configure
```
then post the created xorg.conf.new  (is in your user's home folder)

---

### Post by dangerboy77 on 2011-08-20
ok will do

---

### Post by dangerboy77 on 2011-08-20
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	Screen      2  "Screen2" RightOf "Screen1"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
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
	Load  "record"
	Load  "dri2"
	Load  "glx"
	Load  "dri"
	Load  "extmod"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor2"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "VideoKey"           	# <i>
        #Option     "WrappedFB"          	# [<bool>]
        #Option     "GLXVBlank"          	# [<bool>]
        #Option     "ZaphodHeads"        	# <str>
	Identifier  "Card0"
	Driver      "nouveau"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# <str>
        #Option     "fbdev"              	# <str>
        #Option     "debug"              	# [<bool>]
	Identifier  "Card1"
	Driver      "fbdev"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "DefaultRefresh"     	# [<bool>]
        #Option     "ModeSetClearScreen" 	# [<bool>]
	Identifier  "Card2"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
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

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
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

Section "Screen"
	Identifier "Screen2"
	Device     "Card2"
	Monitor    "Monitor2"
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

---

### Post by realzippy on 2011-08-20
Why are there 3 monitors aso ?
Anyway,try this edited vanilla version first:
```
gksudo kate /etc/X11/xorg.conf
```
(if file should not be empty for some reason stop here and post content)
paste in:

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver "nouveau"
        BusID "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        Modeline "1280x854_60.00"   89.25  1280 1352 1480 1680  854 857 867 887 -hsync +vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
        Viewport 0 0
        Depth 24
        Modes   "1280x854"
        EndSubSection
EndSection
```

Don't forget to undo changes you have done to /etc/kde4/kdm/Xsetup
Restart X or reboot to test new xorg.conf..

---

### Post by dangerboy77 on 2011-08-20
no idea bout 3 monitor reason, i did all you requested, deleted alterations to Xsetup, Desktop is back to its original problem

---

### Post by dangerboy77 on 2011-08-20
Ps what does "aso" mean

---

### Post by realzippy on 2011-08-20
aso = and so on

---

### Post by realzippy on 2011-08-20
> **dangerboy77 said:**
> no idea bout 3 monitor reason, i did all you requested, deleted alterations to Xsetup, Desktop is back to its original problem

...you mean suggested xorg.conf does not work ?

---

### Post by realzippy on 2011-08-20
if 1rst does not work,try
```

Section "ServerLayout"
Identifier "X.org Configured"
Screen 0 "Screen0" 0 0
InputDevice "Mouse0" "CorePointer"
InputDevice "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
ModulePath "/usr/lib/xorg/modules"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "built-ins"
EndSection

Section "InputDevice"
Identifier "Keyboard0"
Driver "kbd"
EndSection

Section "InputDevice"
Identifier "Mouse0"
Driver "mouse"
Option "Protocol" "auto"
Option "Device" "/dev/input/mice"
Option "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Monitor Vendor"
ModelName "Monitor Model"
Modeline "1280x854_60.00"   89.25  1280 1352 1480 1680  854 857 867 887 -hsync +vsync
EndSection

Section "Device"
Identifier "Card0"
Driver "nouveau"
BusID "PCI:1:0:0"
Option        "ModeDebug"            "True"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Card0"
Monitor "Monitor0"
SubSection "Display"
Viewport 0 0
Depth 24
Modes       "1280x854"
EndSubSection
EndSection
```

if it doesn't work also,post the resulting
/var/log/Xorg.0.log file......

---

### Post by dangerboy77 on 2011-08-20
when opening xconf i also get this:   

Error: "/var/tmp/kdecache-darkfire" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-darkfire" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-darkfire" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-darkfire" is owned by uid 1000 instead of uid 0.
kdeinit4: Shutting down running client.
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
Error: "/tmp/ksocket-darkfire" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-darkfire" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-darkfire" is owned by uid 1000 instead of uid 0.
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-darkfire" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-darkfire" is owned by uid 1000 instead of uid 0.
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory

Incase you thought it worth mentioning

---

### Post by realzippy on 2011-08-20
what is xconf ?
you mean when running

gksudo kate /etc/X11/xorg.conf


Try:
```
kdesudo kate /etc/X11/xorg.conf
```
same errors ?


Edi:
...back tomorrow.pretty late.

---

### Post by dangerboy77 on 2011-08-20
yes sorry i mean, xorg.conf ( i was abreviating it)  ok no worries i will ignore the konsole error out put, but yes so far ive followed to the letter everything youve said exactly.

I followed your last Xorg.conf  file ammendments.  and upon reboot there is just blackness, im typing to you from the live cd.... Its ok though because im making ammendments from the live cd now to get back to working graphics

---

### Post by dangerboy77 on 2011-08-20
No worries im at work all day tomorrow but will have a look in the evening, Ill revert back to the ammendments in file Xsetup for full screen for the mean time .......Thanks again for your time

---

### Post by realzippy on 2011-08-21
> **dangerboy77 said:**
> Its ok though because im making ammendments from the live cd now to get back to working graphics

Press "shift" when booting to get to grub menu.
Boot the 1rst kernel recovery mode offered.
Drop to "root shell" and remove the xorg.conf you have created...

```
sudo rm /etc/X11/xorg.conf
```
```
sudo reboot
```

.......................
Of course you could delete the file also from the liveCD....

The xorg.conf solution doesn't always work,also (googled a little)
the nouveau driver (free nvidia-driver) seems to have problems with modelines.
Using the vesa driver instead might not work also,since your resolution
(widescreen) is no valid VESA mode..(but I don't know exactly).
If you want to test this,replace in "device section"
"nouveau"
with
"vesa"

---

### Post by dangerboy77 on 2011-08-21
print "thanks zippy, i will give this a try at some point"

#the laptop is so old with old ramtype and and ide drives/battery doesnt charge(always plugged in to work)/----- i had to ebay for second hand ram and hdd/Someone was going to throw this away, i saved it from 'code hell' and really its only in pergatory right now.  

print "may have to call on your expertise for that one again"

print "Youre the man...The Ger...Man" *1000

print "

---

