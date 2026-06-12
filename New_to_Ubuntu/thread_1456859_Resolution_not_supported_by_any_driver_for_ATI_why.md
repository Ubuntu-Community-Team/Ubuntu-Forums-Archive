---
title: "Resolution not supported by any driver for ATI why?"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by marcoftheknight on 2010-04-17
EUREKA SO SIMPLE it hurts!

SO today playing around with the button on my monitor I managed to initiate the auto reconfigure for sizing the auto button on your monitor and low and behold WHAT! everything is clear my font is perfect my screen is perfect.(This is after a new reinstall of ubuntu LOL and downloading all the packages that you have to get to get it back to where it was. But it's ok I am almost an expert now at setting everything I need up. Key word ALMOST!)

What lesson did I learn play with the Hardware first then check the software omg I can beleive it anyone suffering out there who is being misled that the ATI drivers aren't good dont fear at all in fact they work perfect just adjust the settings on your monitor and voila perfect picture.

This is the site that made me do it :
[http://www.life123.com/technology/computer-hardware/monitors/monitor-display-problems.shtml](http://www.life123.com/technology/computer-hardware/monitors/monitor-display-problems.shtml)

I am so happy :) 
So anyone setting up a ATI heres the rundown>>go to amd >>[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English) this is what I used for the amd64 system>> download pdf and follow install instructuion for your system make sure to follow the instructions to uninstall fglrx before you install this and restart before you install the new driver.>> once installed by doing the terminal codes your driver should be working and the WATERMARK SHOULD BE GONE>>NOw heres the important part your monitor is blurry and your getting a headache and you think it's the driver so you try every resolution and try editing every Xorg file on the planet WAIT!!!!!!!!!!! check your monitors menu and play with the setting. Damn if only I had played around more with the stupid button I would of avoided 10-12hrs of frustration then again Im starting to get the hang of linux. Hopefully this might save someone else 10-12hrs of frustration.

Thanks everyone for you help and input was good linux practice

Thanks for reading

---

### Post by overdrank on 2010-04-17
Hi and welcome, moved to Absolute Beginner Talk

---

### Post by quadproc on 2010-04-17
> **marcoftheknight said:**
> 
Other annoying problems that occured was the watermark on the lower Right corner which I got rid of but since I recently tried a different installation methods of the driver it came back and now I have to repeat the solution I found thank goodness I have a record of the solution.I have found the Hardware Drivers utility does not necessarily correctly report the status of the system that it is running on, so I suggest looking into the xorg.conf file to see what X windows really thinks about your driver, your hardware characteristics, etc.>   The other question is when I type in the terminal there is tons of weird spaceing between the text. Help please !Could you be more detailed in describing the problem?
> What's really weird that without anydrivers or the first time boot up the resolution works and everything is clearUnder these conditions you are not running fglrx; I would suspect that your xorg.conf file has "ati" in the driver at these times.

Which of the ATI driver versions did you install?  Did you get it directly from the ATI site?

quadproc

---

### Post by halitech on 2010-04-17
> **quadproc said:**
> I have found the Hardware Drivers utility does not necessarily correctly report the status of the system that it is running on, so I suggest looking into the xorg.conf file to see what X windows really thinks about your driver, your hardware characteristics, etc.Could you be more detailed in describing the problem?
Under these conditions you are not running fglrx; I would suspect that your xorg.conf file has "ati" in the driver at these times.

Which of the ATI driver versions did you install?  Did you get it directly from the ATI site?

quadproc

I would be surprised that on initial install that the OP even has an /etc/X11/xorg.conf file

OP - open the terminal and run
```
cat /etc/X11/xorg.conf
```
and post the results back here

---

### Post by sandyd on 2010-04-17
alright. stay w/ fglrx
```

gksudo gedit /etc/X11/xorg.conf

```in the "screen" section, add
```

SubSection "Display"
                Depth           24
                Modes           "1366x768"[FONT=monospace]
[/FONT]EndSubSection


```The mode changes your resolution and the depth is the monitor depth. be sure to set them properly

---

### Post by marshmallow1304 on 2010-04-18
> **carlee said:**
> ```

gksudo gedit /etc/apt.sources.list

```


I'm sure you mean

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by mcduck on 2010-04-18
Quite many displays with the native resolution of 1366x768 actually prefer input resolution of 1360x768. This is especially common with HD-Ready televisions, but might apply to some monitors as well. So if you can't get the 1366x768 resolution to work then you should try with 1360x768 instead.

---

### Post by halitech on 2010-04-18
You may also want to find out the info for the HorizSync and VertRefresh and add them to the monitor section.

Here is a sample file to compare to
> Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device
	Driver		[color="red"]"trident"[/color]
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Option		"DPMS" "true"
[color="red"]HorizSync	30.0-60.0
	VertRefresh	50.0-70.0[/color]
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection	"Display"
			Depth		24
			Modes		[color="red"]"1024x768" "800x600"[/color]
	EndSubSection

EndSection

Obviously you would want to put the correct info in for your monitor where its highlighted in red.

---

### Post by marcoftheknight on 2010-04-18
Yes I downloaded the driver and bult the package according to unofficial ATI wiki driver installation method for binary install and built the package in the terminal.

THe problem I think consist of a few things as if the screen or mainly the fonts are being stretched and colored incorrectly and the refresh rate doesn't seem to be nearly fast enough orbeing done correctly. Whne using compiz and moving windows around seems a little choppy and not seemless.

Anyways im working on the different solutions that have been presented give me a few days to try them.

Thanks everyone

---

### Post by marcoftheknight on 2010-04-18
Eureka see above for the ridiculous solution

---

### Post by quadproc on 2010-04-18
> **marcoftheknight said:**
> I have virtual not MODE?I do not understand this statement.

You are running the fglrx driver according to the xorg.conf file:
> 
    Driver    "fglrx"
But the next contradicts that:
> aticonfig
aticonfig: No supported adapters detectedCould you check the xorg.conf file to be sure that its ownership and permissions are OK?  The owner and group should be root and the permissions should be rw, r, r.  I think that your system is unable to access the file and is falling back by assuming that you don't have an xorg.conf.  Looking in the xorg.0.log might shed some light.

quadproc

---

### Post by sandyd on 2010-04-18
> **marshmallow1304 said:**
> I'm sure you mean

```
gksudo gedit /etc/X11/xorg.conf
```
I guess I wasnt paying enough attention :D

---

