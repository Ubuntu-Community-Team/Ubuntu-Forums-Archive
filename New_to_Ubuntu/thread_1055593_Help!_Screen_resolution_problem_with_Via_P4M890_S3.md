---
title: "Help! Screen resolution problem with Via P4M890 S3 Unichrome Pro"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by gurogarry on 2009-01-30
Hello. Linux/Ubuntu newbie here. I am running Ubuntu 8.10 with a Via Technologies P4M890 S3 Unichrome Pro (Rev 01) graphics chipset.  When I first installed Ubuntu, it started correctly with 1024x768 screen resolution, with options for higher resolutions. Everything was fine for about a month. 

Then one day while shutting down, the colors of the logo weren't correct. When I rebooted, the computer came up in 800x600 resolution and only give options for 800x600 and 640x480. 

I've tried booting with the LiveCD and a complete reinstall. Both gave the same results. I've spent hours searching through this forum for an answer, and trying out the solutions I sort of understand, but nothing has worked so far. 

Can someone please help me?

Thx,

G.

---

### Post by overdrank on 2009-01-30
HI and have you tried booting into recovery mode and using the xfix option. Recovery mode is usually the second choice from the grub. Then you can choose the xfix option. Then you should be given the choice of booting normally after the configuration of you x is complete.

---

### Post by gurogarry on 2009-01-30
Tried it. No go. Same problem. Any other suggestions?

---

### Post by overdrank on 2009-01-30
> **gurogarry said:**
> Tried it. No go. Same problem. Any other suggestions?

The amount of memory shared with the graphics in bios. If you can adjust this it may help.

---

### Post by gurogarry on 2009-01-31
OK. I increased the shared memory from 64M to 128MB, but still no change. Also, I have a dual boot setup with XP, and the XP works just fine in 1280x768 mode.

---

### Post by gurogarry on 2009-02-22
I'm still not getting anywhere with this and am still stuck in 800x600 resolution. Today I tried following the directions at [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome). 

I got as far as "...change Section "Device" Driver "vesa" to Driver "openchrome".

This is what I got:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

It's not showing any drivers. I also tried running sudo dpkg-reconfigure -phigh xserver-xorg as mentioned, but all I got was:

xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20090222175002

...and was returned to the command prompt. 
   
Can someone please help me?

Thx,

Garry

---

### Post by amylase on 2009-04-14
Hi Gary

I'm using  

> VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)

with exact same problem as you. I went as far as editing the file and like you, I couldn't find Driver "vesa" part.

Did you manage to fix your problem in the end? If so, how did you do it?

Thanks a lot.

---

### Post by MegaJim on 2009-04-14
I've got this chip on my old Laptop.  There seems to be a problem with versions of Ubuntu after 7.10 not properly detecting the resolution of any devices connected to a KM400/P4M800 Unichrome, and 2d acceleration is also causing hard crashes.

The simple solution is to manually specificy the chipset in xorg.conf, disabling acceleration and adding some lines for resolutions.

Here is my xorg.conf from my Acer 1360

```

#/etc/X11/xorg.conf

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"openchrome"
	Option		"XaaNoImageWriteRect"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Modes	"800x600" "1024x768"
	EndSubSection
EndSection

```

---

### Post by Junkieman on 2009-04-14
Hi, I'm not sure this will work, but it's worth a try yeah?


Firstly, backup your files:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Edit xorg.conf, under the "Screen" Section add another entry for your res, for example 1024x768

```
sudo gedit /etc/X11/xorg.conf
```

New lines added are red: 

```
*(snip)...*
Section "Screen"
    Identifier    "Default Screen"
    Device        "Intel Corporation Express Graphics Controller"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Modes        "800x480"
        **[COLOR="Red"]Modes        "1024x768"[/COLOR]**
    EndSubSection
EndSection
*... (snip)*

```

Save the file and restart the X Desktop (CTRL+ALT+BACKSPACE), and check if the res is now available in the Screen Resolution dialog.

---

### Post by Agent.Logic_ on 2009-04-14
Junkieman's solution will fix it 99.99% of the time. I had to tinker with the xorg.conf file myself to fix my display issues. VIA chipsets are gaining a reputation of screwing up displays on systems running linux, and they have very little official support for linux video drivers. Those of us with hardware from this manufacturer are being discriminated against. :(

Should Junkieman's solution not fix it, try downloading the "xserver-xorg-video-openchrome" video driver from Synaptic, and then try editing the xorg.conf file as mentioned in his solution. Do not forget to add the line:
```
Driver "openchrome"
```
under **Section "Device"**. One downside to this driver is that there is little to no support for 3D acceleration, but from experience, I can say that this driver is the most stable and reliable of all drivers for VIA chipsets. Good luck!

---

### Post by stalkingwolf on 2009-04-14
try sudo displayconfig-gtk

---

### Post by MegaJim on 2009-04-14
> **stalkingwolf said:**
> try sudo displayconfig-gtk

that tool was removed

---

### Post by Jakey_TheSnake on 2009-04-14
> **MegaJim said:**
> that tool was removed

Then

```
sudo apt-get install displayconfig-gtk
```

first. It's still in the repositories I believe. It was a useful tool.

edit: no it's not. Why was it removed?

---

### Post by amylase on 2009-04-15
[B][Addendum]
Okay, problem solved. I came back to add this bit. It's quite sad if I told you how I solved the problem, well I didn't solve it but got it to work. I simply googled for "xorg.conf KN400 KM400 ubuntu" and it led me to this champion's thread [http://ubuntuforums.org/showthread.php?t=1046278](http://ubuntuforums.org/showthread.php?t=1046278) which contains his copy of xorg.conf for the same video card. I don't understand what his file says line by line but what the heck, I just used it and now I'm running on 1024x768 resolution. The rectangle still has "Unknown" written on it. To my disappointment even though resolution problem is solved, I am unable to change visual effects to normal or extra and therefore cannot run the cube. Just in case you can't find that dude's copy of xorg.conf, I've duplicated it here.
> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
	Load	"dbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"VIAExt"
	Driver		"openchrome"
	BusID		"PCI:1:0:0"
	Option		"ActiveDevice"	"CRT"
#	Option "LCDDualEdge" "true"
EndSection

Section "Device"
	Identifier	"VIAInt"
	Driver		"openchrome"
	BusID		"PCI:1:0:0"
	Option		"ActiveDevice"	"LCD"
#	Option "LCDDualEdge" "true"
EndSection

Section "Monitor"
	Identifier	"BenQMonitor"
	Option		"DPMS"
	HorizSync	31-81
	VertRefresh	56-76
EndSection

Section "Monitor"
	Identifier	"AveratecLCD"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"FP91G"
	Device		"VIAExt"
	Monitor		"BenQMonitor"
	DefaultDepth	24
	SubSection "Display"
		Viewport	0 0
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"LCD"
	Device		"VIAInt"
	Monitor		"AveratecLCD"
	DefaultDepth	24
	SubSection "Display"
		Viewport	0 0
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"ExternalDisplay"

  Option "Xinerama" "true"
  Screen        "FP91G"
  Screen        "LCD" RightOf "FP91G"

	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "ServerFlags"
	DefaultServerLayout "Road"
EndSection

Section "ServerLayout"
	Identifier	"Road"
	Screen		"LCD"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
[End of Addendum][/B]


This is what lspci says on my system (dual boot Ubuntu 8.04 / Windows XP SP3)

> 00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 46)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
01:00.0 [COLOR="Red"]VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)[/COLOR]


I selected System -> Preferences -> Screen Resolution. It lets me choose either 640x480 or 800x600 and I can see a nice pink rectangle with "unknown" written on its face. 

This is my original /etc/X11/xorg.conf

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

I changed it to this

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
[COLOR="Red"]	SubSection "Display"
        	Modes        "800x600"
	        Modes        "1024x768"
	EndSubSection[/COLOR]
EndSection
```


Now I hit Ctrl+Alt+BKSPC. It logged out and back in. No change. Still in 800x600 resolution. Screen Resolution still only offers 640x480 and 800x600, not 1024 option.

Making sure I haven't set the resolution too high beyond video card's capacity, I booted (GRUB) into windows XP and it runs smoothly on 1024x768 and the information given by XP on the video card is "VIA/S3G KM400/KN400". 

Maybe it's because I didn't say anything about openchrome. Here it is after I added openchrome:

```
Section "Device"
	Identifier	"Configured Video Device"
	[COLOR="Red"]Driver		"openchrome"[/COLOR]
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	[COLOR="Red"]SubSection "Display"
        	Modes        "800x600"
	        Modes        "1024x768"
	EndSubSection[/COLOR]
EndSection
```


Ctrl+Alt+BKSPC again. Still no change. Still in 800x600. Screen resolution still only has 640x480 and 600x800 to choose, no 1024. Maybe I should change the Device under "Screen" also. Here it is

```
Section "Device"
	Identifier	"Configured Video Device"
[COLOR="Red"]	Driver		"openchrome"[/COLOR]
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
[COLOR="Red"]	Driver		"openchrome"[/COLOR]
[COLOR="Red"]	SubSection "Display"
        	Modes        "800x600"
	        Modes        "1024x768"
	EndSubSection[/COLOR]
EndSection
```

Try again. Ctrl+Alt+BKSPC. Didn't like it. The screen turned all black. Cursor flashing on left top corner and not much else happens. I press Ctrl+Alt+F2, did a sudo reboot now. As Ubuntu rebooted, I can see the logo is almost at the bottom of the screen and is somewhat elongated (taller than before), and the system went on to restart. I chose "recovery mode" at GRUB, chose xfix, and logged back in with 800x600.

Just to check I actually have openchrome onboard, I typed this
> dpkg -l |grep openchrome
and this is the result
> ii  xserver-xorg-video-openchrome              1:0.2.903-0ubuntu3                      X.Org X server -- VIA display driver
I take that means openchrome is onboard and my resolution is still not at its best.

What do I do now? Please help. I'm doing this on my girlfriend's computer and if this resolution problem is fixed, I reckon she will be the next convert. Thanks.

---

### Post by Agent.Logic_ on 2009-04-15
Hmm, strange. Try adding the line
```

Virtual      1024 768

```
right after
```

Modes        "1024x768"

```

---

### Post by amylase on 2009-04-15
Hi Agent Logic, thanks for your suggestion. Here is what my xorg.conf looks like now
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"openchrome"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
        	Modes        "800x600"
	        Modes        "1024x768" [COLOR="Red"]Virtual      1024 768[/COLOR]
	EndSubSection
EndSection
```

After I hit Ctrl+Alt+BKSPC, Ubuntu logo became huge, and once I'm in, I could choose between 640x480, 800x600 and 1024x768. The problem is desktop work space extends outside of my monitor's actual view window. I can pan across left, right, up, down which is pretty cool to have a big desk, but it's not quite what I expected. Also, when I tried to switch visual effect to normal or extra, I am told "Desktop effects could not be enabled"... :(

---

### Post by Agent.Logic_ on 2009-04-15
Well, atleast there is some progess lol :P. I'm not sure if the xorg.conf gets touchy about whitespaces and alignment (I'm new to linux myself), but what I meant was putting the **Virtual    1024 768** line right below the **Modes...** line. Also, try removing the Modes "800x600" line. Hopefully it will fix the problem.

This is what my xorg.conf file looks like, I'm also using the shite video adapter made by VIA Technologies:
```

Section "Module"
        Load            "dri"
        Load            "extmod"
        Load            "dbe"
        Load            "glx"
EndSection

Section "DRI"
        Group           0
        Mode            0666
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "openchrome"
        Option          "XaaNoImageWriteRect"
        Option          "SWCursor"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
        SubSection "Display"
                Modes   "1280x800"
                Virtual 1280 800
        EndSubSection
EndSection

```

I've snipped the comments to improve readability here in the thread.

And unfortunately, desktop effects is not supported in the openchrome driver, there is no direct 3D acceleration support :(. VIA's proprietary linux drivers aren't of much help either. They are either buggy, or simply don't work. This is what we get for going for cheap hardware from Taiwan. :(

---

### Post by Agent.Logic_ on 2009-04-15
double post.

---

### Post by Ravernomina on 2009-04-15
Some times unpluging the monitor form the power and the computer then plug the monitor back in the reboot... that did the trick for me :)

---

### Post by anewguy on 2009-04-15
As already mentioned earlier in this thread, the S3 chrome support is weak, but so is the chipset.  If you do get to the resolution you want, keep in mind that the chipset will not support running desktop effects, so things like the cube will be a no-go for you.

In the mean time, I wrote a how-to a few years ago for a laptop that used the S3 chrome.  I am copying in the part that dealt with the video to see if it will be of some use to you:

Video Resolution
Now comes the more difficult of the choices - getting the video resolution you want. You can do this in the xorg.conf file only but you can also install the 2D or 3D drivers from openchrome if you want to. 

Using the xorg.conf file only
This option is the easiest to get working, and allows normal video playback, etc.
- 
- open a terminal window via "Applications/Accessories/Terminal"
-
- type "sudo gedit /etc/X11/xorg.conf" and press enter
-
- press the fine button for the editor, enter "Generic Monitor" in the search for string and click the "find" button. Position your mouse to the end of the line and click, then press the return key to start a new line. Paste in the following These ranges are not accurate for the LCD panel, but since I cannot get a response from Gateway for the valid ones, you have to put these 2 lines in anyway.
-
HorizSync 30-96
VertRefresh 30-160

-
- press the "find" button for the editor, enter "Default Screen" in the search for string and click the "find" button. Now scroll down just a few lines. You will see lines something like this: Modes "800x600" with maybe some text after the "800x600". What you want to do is completely replace each of these lines (there will be several following) with the following: Modes "1024x768" "800x600" 
-
- click save and exit the editor
-
- log out and wait for the log on screen to appear. Instead of logging on, hold down the crtl alt and backspace keys and then let go. This will reboot the windows manager so the changes will take effect. When the log on screen comes up again just log on and you should be at 1024x768 resolution. I have not gotten any replies from Gateway regarding the valid sync and refresh rates for each resolution. So what that means is that for now you won't be able to successfully change resolution from the default 1024x768.
-
-
Using the openchrome drivers
Be advised that there are a couple of things you need to know regarding the driver:

- I have not been able to run Beryl or Compiz Fusion with it, so if you want desktop effects when you get done you are on your own!

- there is a known bug in the driver that is introduced starting with the 2D driver. I believe it is in one of the packages that is needed. This bug will prevent you from watching a video in such things as the players that show under "Applications/Sound and Video". Someplace along the line it messes up and to actually see the video you have to open 2 of the players and it will play in the 2nd as long as you are trying to play it in the first. This applies to DVD's as well! I have to thank Ubuntu user "tarek" for pointing out the 2 players thing or I would never have video! I have found no work around for this other than going back to the default "VESA" video driver. I believe this has something to do with the OpenChrome driver not supporting the "panel" option yet (and probably won't).

Okay, so you really want 2D and 3D drivers loaded?? I direct you to the following......follow it very carefully, and expect an abort as noted in the 3D section. Follow the link it gives, then go back and finish up. Here's a link to read first:

[http://wiki.openchrome.org/tikiwiki/...isplay+drivers](http://wiki.openchrome.org/tikiwiki/...isplay+drivers)

Still want the drivers? Follow this link:



[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)



Dave :)

---

### Post by websquad on 2009-04-15
> **Junkieman said:**
> Junkieman provided the following:   
```

    SubSection "Display"
        Modes        "1024x768"
    EndSubSection

```

Guys, I'm a total newbe, and am having the same problem with a HP laptop: max display is 800x600, and I need 1024x768.  So, coming from a windows background and knowing nothing about command line Linux, I used the file manager (?) to find the config file for the display, double-clicked it and it opened in gEdit (?) and I saw, alas, that there was no Display Subsection.  So I added the above.  But then it would not let me save it.  When I installed 8.10 a few hours ago it just asked for a userid and password, which I provided.  Now I need something call "root" (?).  ***How do I get there so I can made the change? *** And remember, I know nothing about the command line interface ... thanks !!

***But then maybe I'm too stupid to have a Ubuntu system ... should I go back to Win/XP?***

---

### Post by anewguy on 2009-04-15
You have to have root priviledges in order to update that file.

Do the following:

click on Applications, then Accessories, then over and down to Terminal

log in using your normal user name and password

type:

sudo cd /etc/X11 <enter> (use your normal password when it asks for one)

sudo cp xorg.conf xorg.conf_good <enter>

gksu gedit xorg.conf <enter>


This will open the editor so you can make the changes.  When finished, click save and close the editor, then type

exit <enter>

and you be back to the desktop.

Dave :)

---

### Post by hemicro on 2009-04-25
Going in the direction of "amylase" above, I was able to get my system working and have numerous screen resolutions available now. I have Ubuntu 9.04 installed on my computer and couldn't get any more than 800x600 resolution. Below is my xorg.conf file. I am using a 19" Hyundai LCD monitor. It now works like its supposed to finally. I have been working with this for 3 days!!!!

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Hyundai"
	Option	"DPMS"
	HorizSync 31-80
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"LCD"
	Monitor		"Hyundai"
	Device		"VIAInt"
	DefaultDepth	24
	#	SubSection "Display"
	#	Depth 8
	#	Modes "1280x1024" "1024x768"
	#	Virtual  1024 768
	#	ViewPort 0 0
	#	EndSubSection
#	SubSection "Display"
#		Depth 16
#		Modes "1280x1024" "1024x768"
#		ViewPort 0 0
#		Virtual	800 600
#	EndSubSection
	SubSection "Display"
		ViewPort 0 0
		Depth 24
		Modes "1024x768" "1280x1024"
#		Virtual	1024 768
	EndSubSection
EndSection

Section "Device"
	Identifier	"VIAInt"
	Driver "openchrome"
	BusID 	"PCI:1:0:0"
	Option 	"ActiveDevice" "LCD"
	# Option "LCDDualEdge" "true"
EndSection

---

### Post by hemicro on 2009-04-25
Going in the direction of "amylase", I was able to get my system working and have numerous screen resolutions available now. I have Ubuntu 9.04 installed on my computer and couldn't get any more than 800x600 resolution. Below is my xorg.conf file. I am using a 19" Hyundai LCD monitor. It now works like its supposed to finally. I have been working with this for 3 days!!!!

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
Identifier "Hyundai"
Option "DPMS"
HorizSync 31-80
VertRefresh 56-75
EndSection

Section "Screen"
Identifier "LCD"
Monitor "Hyundai"
Device "VIAInt"
DefaultDepth 24
# SubSection "Display"
# Depth 8
# Modes "1280x1024" "1024x768"
# Virtual 1024 768
# ViewPort 0 0
# EndSubSection
# SubSection "Display"
# Depth 16
# Modes "1280x1024" "1024x768"
# ViewPort 0 0
# Virtual 800 600
# EndSubSection
SubSection "Display"
ViewPort 0 0
Depth 24
Modes "1024x768" "1280x1024"
# Virtual 1024 768
EndSubSection
EndSection

Section "Device"
Identifier "VIAInt"
Driver "openchrome"
BusID "PCI:1:0:0"
Option "ActiveDevice" "LCD"
# Option "LCDDualEdge" "true"
EndSection

---

### Post by Agent.Logic_ on 2009-04-26
> **amylase said:**
> **I am unable to change visual effects to normal or extra and therefore cannot run the cube.**


Visual effects is not supported by the OpenChrome driver, unfortunately. :( For 3D acceleration, you'll need to get VIA's propreitary drivers for your card from [VIA Arena](http://www.viaarena.com/default.aspx?PageID=2). Unfortunately, following their installation directions isn't all that simple, and I haven't gotten the driver for my card to work properly yet. Gives me a "device cannot be found" error when X Server starts up. From what I hear, the drivers are designed for older kernel versions. So for now, I'm sticking to the openchrome driver for now, which works like a charm for all of my laptop needs (except the desktop pimping part :().

---

