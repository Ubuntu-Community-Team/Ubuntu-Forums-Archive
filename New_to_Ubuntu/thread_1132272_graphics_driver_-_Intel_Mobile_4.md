---
title: "graphics driver - Intel Mobile 4"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by dairysound on 2009-04-21
[FONT="Arial"]Hi there

I'm trying to get Compiz to run as I only have the basic video set up at the moment and can't change screen resolution (everything is HUGE!) plus some Visual Effects would be nice - I'm a sucker for that kind of thing, no dice though. I ran Compiz Check and get this:


Gathering information about your system... 
Distribution: Ubuntu 8.04 
Desktop environment: GNOME 
Graphics chip: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) 
Driver in use: vesa 
Rendering method: AIGLX 
Checking if it's possible to run Compiz on your system... [SKIP] 
Checking for hardware/setup problems... [SKIP] 
At least one check had to be skipped: 
Error: vesa driver in use 
Would you like to know more? (Y/n) y 
The vesa driver is not capable of running Compiz, you need to install 
the proper driver for your graphics card. 

I've had a look around - am I right thinking the drivers for this graphics card aren't available yet?

If not is there another solution? I a newbie but willing to try!

Many thanks

Dan[/FONT]

---

### Post by benerivo on 2009-04-21
I think i have the same graphics chip as you do, but i haven't had any problems with compiz. Ubuntu should use the intel driver automatically rather than giving you the 'fallback' vesa driver. What is your setup, and can you load the live cd (either 8.10 or 9.04 beta) and see if desktop effects are working from there?

Do you already have an /etc/X11/xorg.conf file? If so, then do```
gksudo gedit /etc/X11/xorg.conf
```Look for the 'Device' section in this file and make sure it has the intel driver somewhere in it```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
EndSection

```

Before doing any of this, you'll want to make a backup of any existing xorg.conf, so that you can replace it if the new version doesn't work at all.

---

### Post by dairysound on 2009-04-22
Hi

Thanks for getting back.

I'm dual booting with Vista on an Acer 5735. Live cd on 8.10 doesn't activate desktop effects.

Output from gksudo gedit /etc/X11/xorg.conf gives me:

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Could it be the dual boot?

Thanks again!

---

### Post by orlox on 2009-04-22
you should change vesa with intel. vesa is just a graphic driver compatible with many cards, but it has no hardware acceleration.

---

### Post by steve101101 on 2009-04-22
> **dairysound said:**
> Hi

Thanks for getting back.

I'm dual booting with Vista on an Acer 5735. Live cd on 8.10 doesn't activate desktop effects.

Output from gksudo gedit /etc/X11/xorg.conf gives me:

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Could it be the dual boot?

Thanks again!

ubuntu should have no ill verse affects from dual booting since it can use its own partitions.

---

### Post by dairysound on 2009-04-23
Thanks.

Can anyone point me towards the drivers and give me a quick rundown of how to install them please? Or how to point Ubuntu to them, they don't show up in the Drivers box - none do!

---

### Post by dairysound on 2009-04-24
Hi

Just realised benerivo meant I had to edit the device driver *myself* - duh, said I was new - anyway, done that and now I have Visual Effects and screen resolution is much better.

Case closed.

Thanks guys.

---

