---
title: "What video driver should I use?"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by Ghost Hacks on 2010-01-22
Hey guys I'm back with the same problem, well I guess not problem since Ubuntu is kinda working fine at the moment.  I want to use 2D and 3D effects with my ATI Radeon HD 2400 but I can't because both the ATI driver from AMD and the Restricted Driver in Ubuntu, when installed cause my monitor to report no signal, I can hear the OS in the background perfectly but I can't see anything because my refresh rate or screen resolution be to high.  Does anyone know another driver I could use?  Or way to avoid this and still use the card?  I have a 17" CRT Monitor btw capable of up to 1280X1024.

Edit:  Should I try Envy?

---

### Post by adam814 on 2010-01-22
If your card is an r500 series (as opposed to r600 series) you should have 3D effects with the "radeon" driver that ships with X.  If it's an r600 there's 2D acceleration, but no 3D yet with it.

If you decide to give it a try just make sure you uninstall fglrx completely and de-activate it in the Restricted Drivers Manager and change any references to fglrx in your xorg.conf to radeon.

If you really require 3D with an r600 series card about your only option as far as Ubuntu goes is to run Hardy or Intrepid.  Even though ATI claims to support Ubuntu with their proprietary drivers the real focus is on having them working for RHEL and SLED environments.  Both of those use ancient versions of X and until those are updated (whenever RHEL 6 releases that is) I doubt we'll see a version of fglrx that works with xorg 1.6+.

---

### Post by Ghost Hacks on 2010-01-22
Thanks for the reply but I can't use my restricted driver either.  I'm using what ever driver works with Live CD (my Ubuntu is installed) but I haven't enabled the restricted driver due to the problem with no being able to see my display.

---

### Post by cariboo on 2010-01-22
You can also add the Horizontal and Vertical refresh rates to /etc/X11/xorg.conf, to get you monitor to work properly. You have to get the rates from your crt's manufacturers web site. This is what mine looks like:

```
Section "Monitor"
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-1"
    HorizSync       28.0 - 95.0
    VertRefresh     50.0 - 120.0
    Option         "DPMS"
EndSection
```

My monitor, isn't detected properly, as I am running through a D-Link DKVM-4 kvm. With a direct connection to the computer it shows as a KDS VS-190.

---

### Post by halitech on 2010-01-22
I agree with Cariboo907. I have an HD4350 and when using the ATI drivers, it tries to pump the resolution up to 1600x1200 but my lcd only supports 1400x1050 but as soon as I enter the Horizontal and vertical refresh rates I can get the screen to work.

---

### Post by Ghost Hacks on 2010-01-22
So if I add that config and install either the restricted driver or the ATI driver from AMD I will be able to see my display?  I have a KDSusa 17" CRT Monitor but I can't find the info anywhere on the net.  Also how would I add that info into the config?

I think this is my display, [http://www.kdsusa.com/XF7b.asp](http://www.kdsusa.com/XF7b.asp)

Section "Monitor"
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-1"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

I use a standard VGA connector is there anything else I need to configure?

I can't find that file on my system, maybe because I'm not using the restricted driver, should I create it, and is there anything else I need to add to it?

---

### Post by davec64 on 2010-01-22
Just a thought, in addition to what's been recommended so far above, you could also add a custom modeline to your Xorg.conf for your monitor.

Sometimes the automatic tools don't generate the correct setting for a monitor in relation to the graphics card, and the modeline efffectively is a manual override.

Google for "xorg modeline calculator" or something along those lines and that should provide you with plenty of additional information.

Best of luck! :)

---

### Post by halitech on 2010-01-22
the /etc/X11/xorg.conf file is not created during installation anymore. What I had to do is this:

1. Write down on paper how you want the xorg file to look
2. Enable the Restricted driver
3. Reboot
4. wait for the Signal Out of range message (if you get it) or the blank screen
5. Press CTRL + ALT + F1 and log into the terminal session
6. run sudo nano /etc/X11/xorg.conf
7. add the info that you wrote down on paper
8. Reboot

---

### Post by Ghost Hacks on 2010-01-22
Alright I don't much about terminal what do I need to do to configure it?  Like are there commands I need to know?

---

### Post by halitech on 2010-01-22
Basically just follow the steps I wrote out in my previous post, it has all the commands right there for you.

---

### Post by Ghost Hacks on 2010-01-22
How would I got about typing in the info?

{type} sudo nano /etc/X11/xorg.conf {enter}
{type} Section "Monitor" {enter}
{type} # HorizSync source: xconfig, VertRefresh source: xconfig {enter}
{type} Identifier     "Monitor0" {enter}

OR do I use the website that davec suggested?  The site says Warning 
[COLOR=red]Dot clock above maximum of 100MHz!
                     Interlace is recommended. 

[COLOR=Black][FONT=Arial]Sorry I'm a noob here's what the config the site gave me for 1280x1024 which my monitor supports but according to the config I should use 1024x768, should I use 1024x768 and then try 1280x1024 after just so I know it will work?

[/FONT][/COLOR][/COLOR]Modeline "1280x960@60"     105.68  1280 1312 1712 1744    960  979  989 1009

I also just noticed it says 1280x960?  My monitor supports 1280x1024?

Edit:  I tried the config again with just adding Max Res and got this: Modeline "1280x1024@54"    100.00  1280 1312 1688 1720   1024 1045 1054 1076

---

### Post by halitech on 2010-01-22
you would type that info into the terminal window that you logged into after rebooting.

If your monitor supports 1280x1024 then you would use that info, not 1280x960

---

### Post by Ghost Hacks on 2010-01-22
Thank you I'm sorry I had to bug you with noobness XD  Will do now.

---

### Post by Ghost Hacks on 2010-01-22
It didn't work, the first time I typed /etc/x11/xorg.conf which was a typo on my part with x11 not being X11.

The second time I got it right and it displayed a file with some display info in it, but nothing about screen resolution or anything at the top of the file I put in, Modeline "1280x1024@54" 100.00 1280 1312 1688 1720 1024 1045 1054 1076 and pressed Ctrl-Alt-Del and restarted but no luck still no display.

---

### Post by halitech on 2010-01-22
did you add this info as well?

```
Section "Monitor"
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-1"
    HorizSync       28.0 - 95.0
    VertRefresh     50.0 - 120.0
    Option         "DPMS"
EndSection
```

---

### Post by Ghost Hacks on 2010-01-22
No I will it add it, where in the file should I put it?

---

### Post by halitech on 2010-01-22
mine is at the bottom but I have an ATI card

---

### Post by Ghost Hacks on 2010-01-22
I have ATI also, should I add 30 and 70 for my HorizSync and 50 - 160 for my Vert since that's what the KDS site says my monitor is capable of?  Also should I leave Option as it is, I use a CRT with VGA connection.

Edit: I added the data to the file for Monitor but I found that the file isn't being saved.  After I add the info I have been pressing Ctrl-Alt-Del to restart, how do I save the file?

---

### Post by Ghost Hacks on 2010-01-22
OK I figured out how to save the file, and now I'm in ubuntu but I'm running in Safe Graphics mode because it was saying there was an error in the file.

```

Section "Monitor0"
        # HorizSync Source: xconfig, VertRefresh Source: xconfig
        Identifier  "Monitor0"
        VendorName  "Unknown"
        ModelName   "CRT-1"
        HorizSync    30.0 - 70.0
        VertRefresh  50.0 - 160.0
        Option      "DPMS"
EndSection

```

That's exactly what I added copy and pasted out of the file.

---

### Post by Ghost Hacks on 2010-01-22
Alright I noticed the typo and fixed it and restarted, still no display.

I tried adding the ModeLine "1280x1024@54" 100.00 1280 1312 1688 1720 1024 1045 1054 1076 to the config and restarted, still no luck.

I'm gonna try adding the modeline for 1024x768 but if it doesn't work then I don't know what else to do.  I guess I will remove the graphic driver and consider Ubuntu a loss =(

I tried it AND 2 other modelines calculated by another modeline calc and nothing seems to be working.  I tried to uninstall the driver but now that isn't working either I still have to run in Safe Graphics mode, wth?

---

### Post by halitech on 2010-01-23
Did you install either the Proprietary driver from Hardware Drivers or from the ati website?

your xorg.conf file should look like this
```
daryl@debian:~$ cat /etc/X11/xorg.conf
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Modes	"1280x1024" "1440x1050"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

daryl@debian:~$ 

```

---

