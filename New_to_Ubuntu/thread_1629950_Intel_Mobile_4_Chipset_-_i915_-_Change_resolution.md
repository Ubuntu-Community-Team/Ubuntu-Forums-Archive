---
title: "Intel Mobile 4 Chipset - i915 - Change resolution"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by Dark7man on 2010-11-24
Hey Everyone!
Been running Ubuntu just over 2 weeks now, and after sorting out a few other issues I've got round to looking at my resolution issue.  

I ran a few commands in terminal to get the tech info on my hardware, here's the output

Command: lshw -v
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, fast devsel, latency 0, IRQ 47
	Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 7110 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, fast devsel, latency 0
	Memory at d5400000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>
```

My current resolution is 1366x768 (16:9) 60hz - the highest it will let me select in "System>Prefernces>Monitors"
doesn't show my colour depth etc though.

I was hoping for something a bit higher, just for when I'm viewing on my laptop screen, so my panel isn't so squashed.

Anybody got this same graphics driver?  Can You get a higher resolution or should I try maybe a different application for configuring my monitors?  I'm a noob, and any advice would be greatly appreciated! :)

---

### Post by Dark7man on 2010-11-24
...bump

---

### Post by Dark7man on 2010-11-24
...bump again just as board is getting busy :)

---

### Post by mr_luksom on 2010-11-25
So, is your question 'Can I get a higher resolution'? I have the 915GMA chipsets as well, works great with 1440x900.

You may need to set to modes manually with xrandr if this is what you are after.

---

### Post by Dark7man on 2010-11-25
Thanks dude - thats all I needed to know :)  Looking into configuring xrandr now! Thanks again for the info!
:D

---

### Post by mr_luksom on 2010-11-25
You'll need to get the modeline for your display. Use 'gtf'.


```
gtf 1440 900 59.9 
```

Then use xrandr to first create a new mode, add it to your display, and then set the mode.

---

### Post by sandyd on 2010-11-25
adding a modeline is best thing to do.

Press CTRL+ALT+F1
login
Run this

```

sudo killall gdm
sudo killall kdm
sudo X -configure
sudo gdm

```
login (again)

post output of
```

gedit /etc/X11/xorg.conf
```

Ill make the mods for you. (Adding a 'Mode "1440x900"' should be sufficient in the current version of xorg)

---

### Post by Dark7man on 2010-11-25
Will I need to have just my laptop screen on when running these commands?  Just I got my laptop plugged in via HDMI to my hdtv and doing a few things that a big screen is better for... or will it matter?

Might sound a silly question... just thought I'd ask as I'm in the middle of some work and wanting to know if I can do it now without disconnecting from my tv etc or will I do it later when I finish :)

Sorry if it seems a silly question...I'm a noob :)

---

### Post by Dark7man on 2010-11-28
> **sandyd said:**
> adding a modeline is best thing to do.

Press CTRL+ALT+F1
login
Run this

```

sudo killall gdm
sudo killall kdm
sudo X -configure
sudo gdm

```
login (again)

post output of
```

gedit /etc/X11/xorg.conf
```

Ill make the mods for you. (Adding a 'Mode "1440x900"' should be sufficient in the current version of xorg)

I have tried the above commands, but when I get as far as "sudo killall gdm" + "sudo killall kdm" I get the msg "no processes found" or whatever it said along those lines!

I ran through the advice found here...."Adding Undetected Resolutions
[https://wiki.ubuntu.com/X/Config/Resolution#Adding undetected resolutions]("https://wiki.ubuntu.com/X/Config/Resolution#Adding undetected resolutions")

```
Adding undetected resolutions
Due to buggy hardware or drivers, your monitor's correct resolutions may not always be detected. For example, the EDID data block queried from your monitor may be incorrect.

If the mode already exists, but just isn't associated for the particular output, you can add it like this:


  $ xrandr --addmode S-video 800x600
If the mode doesn't yet exist, you'll need to create it first by specifying a modeline:


  $ xrandr --newmode <Mode``Line>
You may create a modeline using the gtf or cvt utility. For example, if you want to add a mode with resolution 800x600, you can enter the following command: (The output is shown following.)


  $ cvt 800 600
  # 800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
  Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
Then copy the information after the word "Modeline" into the xrandr command:


  $ xrandr --newmode "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
After the mode is entered, it needs to be added to the output using the --addmode command as explained above.
```

Changing the desired resolution to 1440x900... but ran into a few issues also, I'll re-run this tomorrow and paste the errors it gives but just thought I'd throw it out there for now and see if it rings any bells with anyone!

More info tomorrow...

---

