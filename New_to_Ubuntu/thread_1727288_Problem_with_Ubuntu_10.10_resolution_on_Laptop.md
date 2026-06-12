---
title: "Problem with Ubuntu 10.10 resolution on Laptop"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by sg3360 on 2011-04-12
Hey there. I have a problem with Ubuntu 10.10... My resolution is stuck at 800x600 and can't go any higher. It can only go down to 640x480. It says Unknown Monitor too. I have no idea how to fix this so any help would be much appreciated. Thanks. :)

Oh by the way this is on an ESystem Laptop

---

### Post by sanguinoso on 2011-04-12
What video card and drivers are you using?

---

### Post by sg3360 on 2011-04-12
Ehm, I'm not sure, how do I check?

---

### Post by sanguinoso on 2011-04-12
Post the output of ```
lspci | grep VGA
```

---

### Post by sg3360 on 2011-04-12
```
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

```

---

### Post by leviathan8 on 2011-04-12
Please post the output of your *xrandr*.

---

### Post by sanguinoso on 2011-04-12
Can you now post the output of this command ? ```
cat /etc/X11/xorg.conf
```

---

### Post by sg3360 on 2011-04-12
the xrandr command is this :
```
 xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0  
```

And the other is this :
```
cat: /etc/X11/xorg.conf: No such file or directory

```

---

### Post by realzippy on 2011-04-12
Try to install Antonio's SIS driver:

[http://ajoliveira.com/ajoliveira/uk/software/xorg.php](http://ajoliveira.com/ajoliveira/uk/software/xorg.php)

---

### Post by sg3360 on 2011-04-12
```
sudo mousepad /etc/X11/xorg.conf
```
When i put that in, and even if i change it to gedit, it doesnt work, its just blank in gedit

---

### Post by sanguinoso on 2011-04-12
Try ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
And then rebooting the machine.

All this command does is reconfigure your xserver. As it seems something has gone wrong as your xorg.conf is missing.

---

### Post by realzippy on 2011-04-12
> **sanguinoso said:**
> Try ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
And then rebooting the machine.

All this command does is reconfigure your xserver. As it seems something has gone wrong as your xorg.conf is missing.

Doubt this works.
.... it will create a xorg.conf without
a "driver" in the device section.Useless.
Btw,nothing went wrong because of the "missing" xorg.conf...
since OP runs the VESA graphics driver,there is no xorg.conf by default.

---

### Post by sg3360 on 2011-04-12
ah damn, I tried to follow some tutorial, and now neither the mousepad, the wireless, or the keyboard works now D:
im sucha complete noob at linux
I clicked ctrl + alt + f1 and in there i click ctrl alt delete

---

### Post by sanguinoso on 2011-04-12
> **realzippy said:**
> Doubt this works.
.... it will create a xorg.conf without
a "driver" in the device section.Useless.
Btw,nothing went wrong because of the "missing" xorg.conf...
since OP runs the VESA graphics driver,there is no xorg.conf by default.

Ah, I didn't know there was none by default. Its not useless if it creates an xorg.conf because then he can follow the guide to install the sis drivers.

---

### Post by realzippy on 2011-04-12
...they ship a custom xorg.conf with the SIS driver in that link.

We need to know which resolution *sg3360* wants,maybe it could be done also with the VESA driver,but VESA is limited to 1280x1024...

---

### Post by sg3360 on 2011-04-12
actually that's about the resolution I want

---

### Post by realzippy on 2011-04-12
Which resolution do you want to set ?

*ah damn, I tried to follow some tutorial,.. *
Did you solve this issue?System back to vanilla?

Have you checked given [link]("http://ajoliveira.com/ajoliveira/uk/software/xorg.php"),downloaded SIS driver aso?

---

### Post by sg3360 on 2011-04-12
1280x800

And yeah I manged to fix that, reinstalled Ubuntu and it was grand. So what code should I run?

---

### Post by sg3360 on 2011-04-12
Also, I downloaded that SIS_Driver thing, just trying to figure out where to put it

---

### Post by realzippy on 2011-04-13
..in the german ubuntu forum there is a small howto:

1.Assume you downloaded the package to  your *~/Downloads/* directory
open terminal,paste in:

go to Downloads
```
cd ~/Downloads/
```
unpacking
```
tar -xzvf sis_driver_*-bit_10.*.tar.gz
```

when running 32 bit Ubuntu:
```
cd 32-bit/
```
when running 64 bit Ubuntu:
```
cd 64-bit/
```

moving driver files to destination 
```
sudo mv sis671_drv.* /usr/lib/xorg/modules/drivers
```

backup eventually existing xorg.conf
```
cd /etc/X11/ && sudo mv xorg.conf xorg.conf_old
```

creating new xorg.conf
```
gksudo gedit /etc/X11/xorg.conf
```

paste into empty file:

```
# sis671/771 
# native resolution 1280x800, 24 bit, 60 Hz

Section "Device"
	Identifier	"sis"
	Driver		"sis671"
	Screen		0
EndSection

Section "Monitor"
	Identifier	"wxga"
	DisplaySize	1280	800
	Gamma		1
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"sis"
	Monitor		"wxga"
	DefaultDepth	24
	SubSection	"Display"
		Virtual 1280	800
		Depth	24
		Modes	"1280x800@60"	"1024x768@60"	"800x600@60"
	EndSubSection
EndSection
```

close file saving changes.
delete eventually existing old monitors.xml file:
```
rm ~/.gnome2/monitors.xml 

```

Reboot
```
sudo reboot now
```

pray.

If problems rebooting,boot in recovery mode (press shift during bootup),drop to shell,log in as your user,type:
```
sudo rm /etc/X11/xorg.conf
```
```
sudo reboot now
```

---

### Post by sg3360 on 2011-04-13
I've done all that but the only xorg.conf file saved in the /etc/x11/ folder is the xorg.conf_old and I can't rename it or anything cos it says i dont have the permissions necessary even though im running on administrator?

---

### Post by matt-fender on 2011-04-13
E-system? i had to fix the screen res on one of those a few weeks ago.. hmmm. when you open monitors in the system menu and choose a resolution higher than 800x600 does it glitch out?

which E-system? i wrote a xorg.conf for an E-system 3088 and it worked perfectly. It may take me a couple of hours to find it however.

---

### Post by sg3360 on 2011-04-13
ESystem Sorrento 1

And there isnt a resolution higher than 800x600 available, it only shows 800x600 and 640x480

---

### Post by matt-fender on 2011-04-13
Should have that xorg.conf very soon, instructing my friend how to grab the code for us ;)

---

### Post by sg3360 on 2011-04-13
Thanks man :)

---

### Post by matt-fender on 2011-04-13
I've just noticed this xorg.conf is for a different chipset, I've used the openchrome driver for the E-system 3088. However I will post it here incase someone can edit it for your SiS

---

### Post by sg3360 on 2011-04-13
Ah right ok, thanks for that though :)

---

### Post by realzippy on 2011-04-13
> **sg3360 said:**
> I've done all that but the only xorg.conf file saved in the /etc/x11/ folder is the xorg.conf_old and I can't rename it or anything cos it says i dont have the permissions necessary even though im running on administrator?

which command *exactly* makes problems?

---

### Post by sg3360 on 2011-04-13
well when i saw that there was only an xorg.conf_old file there i opened it with gedit through the folder and tried to save it as xorg.conf but it didn't work

---

### Post by realzippy on 2011-04-13
when running
```
gksudo gedit /etc/X11/xorg.conf
```
an empty xorg.conf should open,where you had to paste in the content I told you....?

---

### Post by sg3360 on 2011-04-13
I'm rebooting it now after pasting the content in there and saving again, so I'll let you know

---

### Post by sg3360 on 2011-04-13
I booted it again and it put me in a command text thing straight away, so I followed your other instructions and ran ```
 sudo rm /etc/X11/xorg.conf 
```

---

### Post by realzippy on 2011-04-13
did you use the xorg.conf content from post #20
or the file from post #26 ?

Do you run 32 or 64 bit ?

---

### Post by sg3360 on 2011-04-13
from post #20 and 32 bit

---

### Post by sg3360 on 2011-04-13
Also, i just redid it there, and the xorg.conf file seems to be in the right place and i've rebooted but i still dont get the option to change my resolution

---

### Post by realzippy on 2011-04-13
So now you can boot with that xorg.conf but resolution still limited?
To prove this,show output from

```
cat /etc/X11/xorg.conf
```

and then output from

```
xrandr
```

---

### Post by sg3360 on 2011-04-13
> **realzippy said:**
> So now you can boot with that xorg.conf but resolution still limited?
To prove this,show output from

```
cat /etc/X11/xorg.conf
```

and then output from

```
xrandr
```

It says ```
 cat: /etc/X11/xorg.conf : No such file or directory 
```

---

### Post by realzippy on 2011-04-13
means the file is not in the right place...

*Also, i just redid it there, and the xorg.conf file seems to be in the right place *

?

---

### Post by sg3360 on 2011-04-13
Well I go to computer, then File System,etc,x11 and xorg.conf is there

---

### Post by matt-fender on 2011-04-13
> **sg3360 said:**
> Well I go to computer, then File System,etc,x11 and xorg.conf is there


capital X

X11

;)

---

### Post by sg3360 on 2011-04-13
well i did it again and triple checking that i had the capital X in and when i rebooted i ran into the command line again, so i removed it and rebooted again

---

### Post by realzippy on 2011-04-13
ok,understand (now)   ;-)
Well,something not seems to work.Please check if you have:
sis671_drv.so
and
sis671_drv.la 
in
/usr/lib/xorg/modules/drivers

If so,I have no idea (in the moment)..about the SIS driver....besides trying to add a new 1280x800
mode with xrandr using the VESA driver (which probably won't work,but we can test if you have that patience)

---

### Post by realzippy on 2011-04-13
Can you test the vanilla xorg.conf  (as last shot for the SIS driver) ?

```
gksudo gedit /etc/X11/xorg.conf
```

paste in:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"sis671"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth 	24
EndSection
```

reboot..?

---

### Post by sg3360 on 2011-04-13
yeah both of those are there :(

---

### Post by realzippy on 2011-04-13
try post #43

---

### Post by sg3360 on 2011-04-13
yeah i did that and it boots me into the command and login screen

---

### Post by realzippy on 2011-04-13
just found this here on the forum:
[http://ubuntuforums.org/showpost.php?p=9920147&postcount=568](http://ubuntuforums.org/showpost.php?p=9920147&postcount=568)

The difference is the driver file:
sis671_drv.so
replace existing with the version from the link and recreate the xorg.conf
so you should test this before giving up with SIS and go on with VESA.
Since it is pretty late in europe meanwhile,I am out till tomorrow.

---

### Post by sg3360 on 2011-04-13
I got that far, but do you know how i can extract a file compressed with 7zip? I've no idea how to do it on this, and what I looked up doesn't seem to work

---

### Post by sg3360 on 2011-04-13
never mind, figured it out! just gonna try and put it in the folder now

Annndd I don't know how to get it there properly :(
I'll be on tomorrow if someone can help my nooby self D:

---

### Post by realzippy on 2011-04-14
```
gksudo nautilus
``` 

..opens the file manager with admin privileges.
Then you can drag & drop 
*sis671_drv.so* 
to 
*/usr/lib/xorg/modules/drivers*
replacing existing one.
Then again create xorg.conf

```
gksudo gedit /etc/X11/xorg.conf
```

paste in

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"sis671"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth 	24
EndSection
```

Reboot.
If it works (hopefully),we edit monitor section with H/Vsync values
to give you a wider range of resolution.

---

### Post by sg3360 on 2011-04-14
it boots me into the command screen again, so i logged in and ran ```
 startx 
```

which gave me the following result :
```
(EE) SIS(0): **************************************
(EE) SIS(0):        ERROR:
(EE) SIS(0):No valid modes found - check VertRefresh/HorizSync
(EE) SIS(0):     END OF MESSAGE
(EE) SIS(0): **************************************
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found 
```

It also says i can check the log file at "/var/log/Xorg.0.log" for addition information... should I do that?

---

### Post by realzippy on 2011-04-14
Ah!
Thats a good sign;as I wrote in post #50,we might have to add hsync/vrefresh
values to xorg.conf.

Again delete the existing xorg.conf
```
sudo rm /etc/X11/xorg.conf
```
reboot  (or startx should work also)

run
```
gksudo gedit /etc/X11/xorg.conf
```
(guess you know the commands already?Should I keep repeating them?)
and try this version:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"sis671"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
        HorizSync       28.0 - 83.0
        VertRefresh     56.0 - 75.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth 	24
EndSection
```

---

### Post by sg3360 on 2011-04-14
haha yeah im starting to get the hang of them
I still get the same error with that one

---

### Post by realzippy on 2011-04-14
Ok,try this one:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"sis671"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
        HorizSync       28.0 - 85.0
        VertRefresh     56.0 - 75.0
        Modeline  "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth 	24
        SubSection "Display"
        Depth           24
        Modes   "1280x800" "1024x768" "640x480"
EndSubSection
EndSection
```

But admit I doubt that this will work.

Btw,with cursor up/down you can browse through already given commands at the terminal/shell....

**EDIT:**
If no luck,then this one:
(the one from the link)

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"sis671"
	Screen		0
EndSection

Section "Module"
	Load	"v4l"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"evdev"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"dri"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
	Load	"synaptics"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync 20-107
	VertRefresh 50-185
#	HorizSync 28-72
#	VertRefresh 43-60
EndSection

Section "Screen"
	Identifier	"Screen0"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Depth	24
		Modes	"1280x800" "1280x768" "1024x768" "800x600"
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by sg3360 on 2011-04-15
nope neither of them work :(

---

### Post by realzippy on 2011-04-15
Ok,let's try to build your own xorg.conf:
Delete the non-working xorg.conf,reboot.
When desktop running


Press alt+ctrl+F1
log in with username/password
type (write this down,you won't be able to paste)

```
sudo service gdm stop
```

```
sudo Xorg -configure
```

```
sudo service gdm start
```

```
startx
```

Go to your home folder,post the content of the file
xorg.conf.new
that you have just created.

---

### Post by sg3360 on 2011-04-15
```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
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
    Load  "glx"
    Load  "dri2"
    Load  "extmod"
    Load  "dri"
    Load  "record"
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
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # <str>
        #Option     "fbdev"                  # <str>
        #Option     "debug"                  # [<bool>]
    Identifier  "Card0"
    Driver      "fbdev"
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

```

---

### Post by realzippy on 2011-04-15
Reduced and modified (monitor section):

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Module"
    Load  "dbe"
    Load  "glx"
    Load  "dri2"
    Load  "extmod"
    Load  "dri"
    Load  "record"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    HorizSync       28.0 - 95.0
    VertRefresh     56.0 - 75.0
    Modeline  "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
EndSection

Section "Device"
    Identifier  "Card0"
    Driver      "fbdev"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth 	24
        SubSection "Display"
        Depth           24
        Modes   "1280x800" "1024x768" "640x480"
        EndSubSection
EndSection

```

This should at least boot to desktop.We use the basic "fbdev" driver
(See section "device",driver).Check if you get 1280x800 with this driver, do not know.

---

### Post by sg3360 on 2011-04-15
do i put that in /etc/X11/xorg.conf or in the one in my home folder?

---

### Post by realzippy on 2011-04-15
it has to become xorg.conf
in
/etc/X11

only in this location the kernel/xserver will find it.
So again

```
gksudo gedit /etc/X11/xorg.conf
```

and paste stuff in,close,save,reboot.

---

### Post by realzippy on 2011-04-16
General note.

..meanwhile you may ask yourself if I know what I suggest you to do or why it is just not working out of the box,since this thread has become pretty long.
Well,the problem is your graphics card:
Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
which is not supported by the Linux/Ubuntu kernel (anymore;older Ubuntu versions might work);any ATI/Intel/Nvidia graphics chip would have worked.
SIS hardware is well known to make trouble,not only in the Linux-world.
Thankfully there are guys like [Antonio]("http://ajoliveira.com/ajoliveira/uk/software/xorg.php") who spend lots of there time still hacking drivers for hardware like yours;unfortunately for some reason this driver (there seems to be 3 different around,2 of them we have tested) does
not work on your system.
If you had a look at the [SIS thread]("http://ubuntuforums.org/showpost.php?p=10621990&postcount=702") here on the forum
you see that we did exactly what normally should work.
So we need some more shots in the dark and you have to be patient.
Since your machine refuses to boot/startx with common xorg.conf versions,current
attempt is a xorg.conf you created on your machine with the basic "fbdev"
driver.If this boots,we will change it to "VESA" to see if it still boots,
hopefully in 1280x800.If this fails,we can try a [3rd SIS driver]("http://db.tt/vH7GMYP").
If this also fails,we can modify kernel boot options...
What I want to say:
It might stay a little frustrating..

---

### Post by sg3360 on 2011-04-16
Oh yeah I'd heard about the driver causing problems. And don't worry, I'm not getting impatient or anything, I just haven't been able to get access to my laptop in a while :P I really, really appreciate the help you're giving me, and it is giving me a little bit of better knowledge on how the OS works. :)

And, that last thing you posted didn't work, it still puts me in the command line :( The code it gives it :
```
(EE) Problem parsing the config file
(EE) Error partsing the config file 
```

---

### Post by realzippy on 2011-04-17
?
parsing error usually means a typo in the config file (xorg.conf),but I
cannot find one...?Have you forgotten a letter/line when pasting?
So try the file you have created,without any changes:

```
gksudo gedit /etc/X11/xorg.conf
```

paste in:
```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
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
    Load  "glx"
    Load  "dri2"
    Load  "extmod"
    Load  "dri"
    Load  "record"
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
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # <str>
        #Option     "fbdev"                  # <str>
        #Option     "debug"                  # [<bool>]
    Identifier  "Card0"
    Driver      "fbdev"
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
```

Reboot.This *has* to boot to desktop  ;-)

---

### Post by sg3360 on 2011-04-17
It didn't work :(

```
{EE} open /dev/fb0: no such file or directory
(EE) Screen(s) found, but none have a usable configuration. 
```

---

### Post by realzippy on 2011-04-17
last shot:


```
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
    Load  "dri2"
    Load  "extmod"
    Load  "dri"
    Load  "record"
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
    HorizSync       28.0 - 105.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # <str>
        #Option     "fbdev"                  # <str>
        #Option     "debug"                  # [<bool>]
    Identifier  "Card0"
    Driver      "fbdev"
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
```

---

### Post by realzippy on 2011-04-17
I am at a loss.
Normally the xorg.conf you have created on your machine -with the
frame buffer driver (fbedev)- simply *had* to work.
For fun I copied it to my machine,and it works,the same file,not modified.
If the last version I gave you also does not work -very likely-
you could try the [3rd version of the SIS driver]("http://www.vivaolinux.com.br/dica/Sis671-771-no-Ubuntu-10.10/").
You only have to download it and run a script,it creates the xorg.conf itself.Feel free to ask if questions regarding to the link...

---

### Post by sg3360 on 2011-04-17
Hmm that didn't work either and I can't figure out how to work the 3rd Driver... :(

---

### Post by realzippy on 2011-04-17
> **sg3360 said:**
> Hmm that didn't work either and I can't figure out how to work the 3rd Driver... :(

1. klick that [link]("http://www.4shared.com/file/T5o1ORl0/Sis_671_771tar.html"),save file to /Downloads:

2. Open terminal,navigate to your Downloads folder,type:

```
cd ~/Downloads
```

3.Unpack the file:

```
tar -zxvf Sis.\ 671_771.tar.gz
```

4.Navigate to unpacked file:

```
cd Sis.\ 671_771/
```

5.Make file (script) executable:

```
chmod +x sisimedia.sh 
```

6.Run script:

```
sudo sh sisimedia.sh 
```

7.Reboot

---

### Post by sg3360 on 2011-04-22
So that didn't work... it booted to the command console again so I ran ```
 sudo rm /etc/X11/xorg.conf
```

And now I have a really really off coloured display... Sorry I haven't replied in almost a week, my internets been on and off... How do I uninstall ubuntu on this? Cos sadly, it isn't gonna work on this laptop with the sis driver :( might put it on my pc or on the laptop I get when this one breaks

---

### Post by Pazit on 2011-04-22
> **sg3360 said:**
> So that didn't work... it booted to the command console again so I ran ```
 sudo rm /etc/X11/xorg.conf
```And now I have a really really off coloured display... Sorry I haven't replied in almost a week, my internets been on and off... How do I uninstall ubuntu on this? Cos sadly, it isn't gonna work on this laptop with the sis driver :( might put it on my pc or on the laptop I get when this one breaks
Just try this before you give up :

```
sudo dpkg-reconfigure xserver-xorg

```enter your password when asked and then reboot.

Good Luck;)

---

### Post by realzippy on 2011-04-23
..can you explain:

*really really off coloured display*  ?

Do you mean,during boot you have kinda garbled,mostly pink lightshow?
If so,this might be a good sign...

---

### Post by sg3360 on 2011-04-23
Do I just run that, without any xorg.conf file at all? Cos I did and there doesn't seem to be a difference.

And well, it was kinda like the contrast was really wrong... I can't really explain it but it isn't on now oddly enough.. So it must've just went when i rebooted

---

### Post by Pazit on 2011-04-24
> **sg3360 said:**
> Do I just run that, without any xorg.conf file at all? Cos I did and there doesn't seem to be a difference.

And well, it was kinda like the contrast was really wrong... I can't really explain it but it isn't on now oddly enough.. So it must've just went when i rebooted

yes, just run it and reboot.

now try to enter to : system > preferences > monitors 

and there you should see a list of options to chose from. if you see the resolution that you need  chose it and make default.

---

### Post by sg3360 on 2011-04-26
yeah i ran that and the resolution selection is no different :(

---

### Post by realzippy on 2011-04-26
Hi!
Just spent a few minutes (again ;-) ) with your issue,
Have 2 last ideas,but first I need to know which kernel version you are running...type:

```
uname -r
```

and post the output.


edit:
give me also output from:

```
locate sisimedia_drv.so
```

---

### Post by Pazit on 2011-04-26
> **sg3360 said:**
> yeah i ran that and the resolution selection is no different :(

sorry :(  it worked for me with "sis" problem.

for me it did the magic .

don't give up! you will find the solution.

---

### Post by elvis37 on 2011-04-28
I have sis 671/771 on a Fujitsu Siemens Esprimo Mobile V5535 and I had the same problem with resolution ! Thank GOD that this problem has dissapeared with update to Ubuntu 11.04 . press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '11.04' is available. Click Upgrade and follow the on-screen instructions. Now, after update I have a beautiful 1024x768 resolution ! ;)

---

### Post by sg3360 on 2011-04-28
@realzippy
You have no idea how grateful I am for all the assistance :P Here's the first one :
```
 2.6.35-22-generic

```
and the second :
Well... I put it in and nothing popped up, just the text before where you write a command again.

@Pazit
Ah it's ok, thanks for trying to help me :)

@elvis37
I saw that... I think I'll try it and get back and tell ye if it worked or not :)

---

### Post by sg3360 on 2011-04-28
It worked! I'm now running on 11.04 with the proper resolution :) Thanks for all the help guys

---

