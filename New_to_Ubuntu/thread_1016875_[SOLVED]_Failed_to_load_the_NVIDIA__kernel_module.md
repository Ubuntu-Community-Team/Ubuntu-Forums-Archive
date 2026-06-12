---
title: "[SOLVED] Failed to load the NVIDIA  kernel module"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by cwmoser on 2008-12-20
I cannot install the nvidia restricted drivers on my new AMD PC.

Running Ubuntu 8.04

when I install the nvidia drivers, it changes my xorg.conf file putting in "nvidia" for the Device Driver.  I have to change it to "nv" to get my system back.  What I would like to do is get this so I can have dual monitors.

Any help is appreciated.

Thanks

Carl


Here is my /etc/X11/xorg.conf file after I changed "nvidia" to "nv".
Cannot get dual monitors to work -- need to figure out how to make the nvidia drivers work.


Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nv"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "twinview"
    Option         "TripleBuffer" "true"
    Option         "AllowGLXWithComposite" "True"
    Option         "RenderAccel" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "AccelMethod" "exa"
    Option         "MigrationHeuristic" "greedy"
    Option         "ExaNoComposite" "true"
    Option         "DynamicTwinView" "false"
    Option         "NoLogo" "True"
    
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by cwmoser on 2008-12-20
No matter how I try to enable the restricted nvidia drivers, what happens is that Ubuntu boots to a blank screen.  What I have to do is go to the Recovery Console and edit /etc/X11/xorg.conf file and change the Device "nvidia" back to the default "nv".  

This is strange.  I did not have this problem with my old PC - and Intel P4 with 2GB RAM.  My new PC is an AMD 64 X2 6000+ with 4GB Ram.  I've heard that 4GB RAM causes problems.  

Any ideas?

Carl

---

### Post by StevenHarper on 2008-12-20
First Question : Are you up to date -> have you got all the packages (System Update)

Second: is it possible to try a 8.10 Live CD

Third: which nvidia card do you have

Forth : which Driver version is mentioned in the restricted panel.

Ta

---

### Post by cwmoser on 2008-12-20
I've got all the updates installed.  I tried Ubuntu 8.10 but went back to 8.04.  My old PC (Intel P4, 2GB RAM) has Ubuntu 8.04 with nVidia AGP card and it ran great.  I've tried 2 different nVidia cards.  The one I am currently using is NX7300LE TD128EH.  

Here is my /etc/X11/xorg.conf file:

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"	"CoreKeyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nv"
	Option		"NoLogo"	"True"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	Option		"twinview"
	Option		"TripleBuffer"	"true"
	Option		"AllowGLXWithComposite"	"True"
	Option		"RenderAccel"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"AccelMethod"	"exa"
	Option		"MigrationHeuristic"	"greedy"
	Option		"ExaNoComposite"	"true"
	Option		"DynamicTwinView"	"false"
	Option		"NoLogo"	"True"
	SubSection "Display"
		
		Depth	16
		Modes		"1680x1050"	"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1680x1050"	"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection


If I change Driver  "nv"  to Driver   "nvidia" then when I reboot, it starts the boot normally but by the time the GUI starts up its a blank screen.  I have to reboot to the Recovery console and change it back to "nv" in order to get my desktop back.

I wonder if it has something to do with being an AMD X2 64 chip and 4GB RAM?

Carl

---

### Post by StevenHarper on 2008-12-20
Ah that's a 7300, could you tell me which restricted driver is being suggested in the restricted driver panel (does it say (latest cards) at the end)

Steve

---

### Post by StevenHarper on 2008-12-20
BTW : if you get stuck at a blank screen (login screen)

You can use CTRL+ALT+F2 or any F key (F7 is the gnome one F8 is the bootup) to swap to another text based login (F7 gets you back to the gnome one)

You can then edit the xorg.conf there and use 

```
sudo /etc/init.d/gdm restart
```

to restart X and gnome and try any changes

for anyone else try it now (don't do it on matrox cards they dont support it)

So hit CTRL+ALT+F2, login : try stuff then just hit CRTL+ALT+F7 to get back to this screen - fun.

Also if you EVER completely stuck and need to reset the machine  DONT just hit the power. Instead use the low level kernel reset that makes the disks close nicely


*****DONT DO THIS NOW UNLESS YOU REALLY WANT TO REBOOT WITHOUT WARNING****

Hold down CTRL+ALT+PRINTSCR 

while holding hit

reisub

The machine will reboot : I use this to remember it

Raising 
Elephants
IS
Utterly
Boring



Steve

---

### Post by cwmoser on 2008-12-20
Say what?  Never heard of that reboot technique.  Have to try it.

My PC locks up with the blank screen.  Ctrl Alt F2 will not work.  I'm thinking it has halted or crashed.

System -> Administration -> Hardware Drivers shows:

NVIDIA accelerated graphics driver (latest cards)
Enabled is unchecked - but if I check it and reboot, I get that blank screen.
Status is "In use:



Carl

---

### Post by StevenHarper on 2008-12-20
Hmm : have you tried a complete removal of the driver (using synaptic) 

I have a machine running 8.04 on a old nvidia card here.

---

### Post by cwmoser on 2008-12-20
> **StevenHarper said:**
> Hmm : have you tried a complete removal of the driver (using synaptic) 

I have a machine running 8.04 on a old nvidia card here.


I've removed every nvidia driver and reinstalled - still no joy.

I wonder if it has something to do with the AMD 64 X2 and 4GB?  My system locks up and will not respond.  When I had the blank screen, I tried to ssh into it with my old PC but it would not give me a login.  Seems like it just locked up.

Carl

---

### Post by alienexplorers on 2008-12-20
Have you tried using envyng to load and setup your driver.  Open terminal and load:
> sudo apt-get install envyng-core envyng-qt
Envyng will be loaded into Applications>System Tools.  Run it and select the driver recomended by envyng.

---

### Post by cwmoser on 2008-12-20
Hey that envyng package now allows for the "nvidia" to work.

Looks like I am one step further along.

Now I am trying to get the second monitor to work.  
Any ideas?  I do have "twinview" in xorg.conf but my second monitor is not working.

Carl

---

### Post by cwmoser on 2008-12-21
SOLVED.

OK, here is the keys to success with this issue.

1- Forget about the Nvidia drivers in Synaptics - they don't work.

2- Need to go to Nvidia Website and download the latest drivers:
[http://www.nvidia.com/object/linux_display_ia32_177.82.html](http://www.nvidia.com/object/linux_display_ia32_177.82.html)

3- Install the drivers:
sudo sh ./NVIDIA-Linux-x86-177.82-pkg1.run

4- Clear out your /etc/X11/xorg.conf file:
sudo nvidia-xconfig

5- run the nVidia configuration program:
sudo nvidia-settings

6- If you are trying to get dual monitors to work, make note that not all dual head video cards will accept VGA cables -- e.g. some cards will not work with the DVI to VGA adapter - mine was that way and fortunately my monitor supplied both VGA and DVI cables.

7- Wait until you do all of the above before you enable the Compiz stuff:
i.e. System -> Appearance -> Visual Effects -> Extra


One other tool that was suggested in this thread (EnvyNG) was helpful.
All the posts here helped me solve why I could not get the nvidia drivers to work.  

Thanks to everyone who helped me.

Carl

---

