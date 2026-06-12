---
title: "Configured Dual Monitors Compiz stopped working"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by Balkoth25 on 2009-03-01
Hi, 

I just installed Ubuntu 8.10 amd64 a couple of days ago.  I have two monitors set up and initially my system only recognized one of the monitors.  I started playing around and installed and enabled compiz just fine.  I had all the nice bells and whistles working too.  I then tackled the issue of my system not recognizing my two monitors.  I have a ATI Radeon HD 2600XT video card.  I installed the proprietary drivers and used aticonfig to configure my monitors.  Once I configured my system for dual monitors using aticonfig, my auto detect on the resolutions stopped working correctly and I had to edit my xorg.conf file to include a modeline in my monitor section to force the correct resolution settings.  That worked fine.  I then noticed that in the change desktop background property when you right click on the desktop on the Visual Effects tab the option None was selected.  I did have Extra selected before I configured dual monitors.  When I tried to change my visual effects to normal or extra, my desktop freezes up and I need to restart X (I think that is what it is called).  I have searched the forums and googled my issue and couldn't find a resolution.  Compiz is running, I tried installing the Compiz Fusion icon and everything looks fine there.  I did check to see if my video card could handle compiz and everything checked out a ok there.  Any help would be greatly appreciated thank you.  Also here is my xorg.conf file:

```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "Default Screen" 0 0
	Screen         "aticonfig-Screen[0]-1" RightOf "Default Screen"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
        Modeline     "1440x900_60.00" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-1"
	Option	     "VendorName" "ATI Proprietary Driver"
	Option	     "ModelName" "Generic Autodetecting Monitor"
	Option	     "DPMS" "true"
        Modeline     "1440x900_60.00" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal"
	Option	    "OverlayOnCRTC2" "1"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-1"
	Device     "aticonfig-Device[0]-1"
	Monitor    "aticonfig-Monitor[0]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1440x900" "1280x1024" "1024x768"
	EndSubSection
EndSection

```

Thanks again in advance.

-Balkoth25

---

### Post by Bölvaður on 2009-03-01
Are you able to set the ati config to let you have 1 big screen stretched on 2 monitors?

Compiz doesn't support multiply outputs anymore I think so lettting compiz only see 1 is the best way to go.

---

### Post by Balkoth25 on 2009-03-01
I am not to sure how to do that.  I am willing to try that out though.  I don't think I can do this through aticonfig, does anyone know how to do this or can someone point me in a direction so I can do more research?  Thanks.

---

### Post by Bölvaður on 2009-03-02
it has been 2 years since I used ati (and having 2 monitors) so can you send a screenshot of the config manager they provide.

Im very sure you should have more than just 1 option how to control the displays. Try find clone/..../...  where ... are the dual monitor options I dunno what is called.

---

### Post by Balkoth25 on 2009-03-02
This drove me nuts until I figured it out.  You were correct and Compiz doesn't support multiple outputs.  Well, it does, but only in certain scenarios.  So I did some more research and ended up going the Big Desktop route.  I had a hard time configuring this as well so I read up on the xorg.conf file, ATI, and the aticonfig.  I then manually edited my xorg.conf file until it worked correctly for me.  Trial and error worked for me in the end.  I spent a lot of time restarting X and manually shutting down my computer to reboot it in recovery mode, but I eventually got it.  Here is my ending result:

```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
       #Modeline    "1440x900_60.00" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
EndSection

Section "Device"
	Identifier  "Configured Video Device"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal"
        #Option      "Mode2" "1440x900,1440x900"
	Option	    "PairModes" "1440x900+1440x900,0x0+0x0"
	Option	    "EnableMonitor" "auto,auto"
	Option	    "ForceMonitors" "auto,auto"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	SubSection "Display"
		Modes    "1440x900"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"

               #Virtual 1440 900
		Viewport   0 0
		Depth     24
		Modes    "1440x900"
	EndSubSection
EndSection

```

I did have a lot more junk in there, but I cleaned it up a lot.  The more junk in a file, the harder it is to read.  Thank you for help.  I greatly appreciate it.  One last question though, how do I mark this as solved or close this thread?  Thanks.

-Balkoth25

---

### Post by Bölvaður on 2009-03-03
> **Balkoth25 said:**
> One last question though, how do I mark this as solved or close this thread?

I guess they have disabled it at the same time they disabled the "thank system".
Im glad you found out how to fix the problem.

For people that might read this but do not have ati but nividia I have found:
With nvidia you get a program "nividia-settings" where you have to click configuration and pick an option (example: clone if you are connecting it to your tv)

---

