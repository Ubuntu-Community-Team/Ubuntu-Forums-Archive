---
title: "Monitor with Useless Resolution"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by BrightSky on 2010-05-15
I have this week started a determined effort to use Linux.  It has taken me a little while to download and create a boot CD (after not using NERO).  I now have it installed but with only 800 by 600 screen resolution which as far as I am concerned is a waste of time.  I have struggled for about 4 hours now trying to found how to get a driver for my screen following a number of help routes.  I can't solve it without help and at the moment this is as far as my linux experience will go

I have a flat screen which is best 1280 by 1060 60hz.  The graphics card is an ATI 3D rage LT Pro which I believe conforms to the 9200 series.  I can find a driver on the ATI site but where do I download it to.  There appears to be an install screen for available drivers! The detect monitor option doesn't work.  Some of the help files talk about modifying a file called xorg.conf whilst in other places it is advised to throw it away with verion 10.04.  At the moment, Bill Gates doesn't seem all bad.  Can someone help me.

---

### Post by TeoBigusGeekus on 2010-05-15
Can you enable desktop effects?
Right click on Desktop, select Change Background and go to Visual Effects.
Select Extra and Ubuntu will try to find the best available driver for your system.

---

### Post by Morten ML on 2010-05-15
Pretty newbie myself but ill give it a shot:

First make sure the graphics card is what you say:
```
lspci
```
in concole/terminal

and see what it says about your graphics card.

Secondly - i am not sure it is a good idea to use a "third party" driver - i think some driver from ubuntu repo should be able to make this work. but as said I am a newbie myself.

And welcome to ubuntu :)

EDIT: First do what TeoBigusGeekus says ;)

---

### Post by BrightSky on 2010-05-15
Thanks but I've already done that on gone through the next stages on that help route

---

### Post by BrightSky on 2010-05-15
I have tried your recommendation.  After a while with the screen greyed I receive the reply, Desktop effects could not be enabled.

---

### Post by halitech on 2010-05-15
the ATI 3D rage LT Pro does not conform to the Radeon 9200 series. It has long been in the Legacy category and there are no drivers other then what Ubuntu has by default. You could try creating an xorg.conf file and editing it by hand to see if it helps.

```
sudo touch /etc/X11/xorg.conf
```
```
gksudo gedit /etc/X11/xorg.conf
```
paste this info in

> 
Section "Monitor"
	Identifier	"Configured Monitor"
	Option		"DPMS" "true"
	HorizSync	30.0-60.0
	VertRefresh	50.0-70.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection	"Display"
			Depth		24
			Modes		"1024x768" "800x600"
	EndSubSection

EndSection


reboot and hopefully you will have 1024x768

---

### Post by BrightSky on 2010-05-15
Yes, that does work.  A number of other lower resolutions have also appeared.  Under Windows XP I run @ 1280 x 1060.  What do I have to change to get that option.  Thanks so far and also in anticipation.

---

### Post by halitech on 2010-05-15
in the line where it says "1024x768" "800x600" add the resolutions you want to be able to use. Make sure you put "" around them or they won't work.

---

### Post by cascade9 on 2010-05-15
> **halitech said:**
> the ATI 3D rage LT Pro does not conform to the Radeon 9200 series. It has long been in the Legacy category and there are no drivers other then what Ubuntu has by default.

Yes, its a 1997 card with no hardware T&L (transform and lighting). Pretty old, very 'legacy' these days. 

> **BrightSky said:**
> Yes, that does work.  A number of other lower resolutions have also appeared.  Under Windows XP I run @ 1280 x 1060.  What do I have to change to get that option.  Thanks so far and also in anticipation.

I think you mean 1280 x 1024. I havent ever seen a monitor that does 1280 x1060. 

You should be able to just add the resolution you want in the 'mode' line, like this-

Modes "1280x1024"        "1024x768" "800x600"

---

### Post by Silent Warrior on 2010-05-15
Brings back memories... I think the Rage LT Pro was what was in my first computer - new in '98, now retired. And then I got a Voodoo 2 with 12 Mb VRAM to show that sucker who's boss! :) I-War and Wing Commander: Prophecy were suddenly that much more fun... But I digress - I need to keep this topic around for reference for adding some resolution to my other computer.

---

### Post by BrightSky on 2010-05-15
I have now tried add "1280x1024" and it doesn't work.  I have removed the "800x600" in case it would only accept two items but to no avail.  Do I have to give up?

---

### Post by BoneKracker on 2010-05-15
There is a tool you can use to compute custom modelines.  Using this, you can set your screen's pixel resolution to anything the hardware will support.

Note: Doing this is dangerous if you don't know what you're doing.  You can destroy your monitor.

You probably already have the tool: /usr/bin/gtf

You can read the extensive documentation (ha ha) here:
```
man gtf
```

As an example (this is an example, use the correct numbers that your monitor will support, or you may damage your hardware):

```
~ $ gtf 1280 1060 60

  # 1280x1060 @ 60.00 Hz (GTF) hsync: 65.82 kHz; pclk: 112.68 MHz
  Modeline "1280x1060_60.00"  112.68  1280 1360 1496 1712  1060 1061 1064 1097  -HSync +Vsync
```

You would then cut and paste that into the "Monitor" or "Modes" section of your  xorg.conf file (don't do it; use your own numbers).

You should first research the specifications for your monitor.  Make sure you are using a vertical refresh rate that is within the range the hardware supports.  You will probably get the best results with a resolution that the monitor was engineered to use.  Read the monitor's documentation.

You should also understand the capabilities of your graphics card and use a resolution that is within its capabilities.

I have used this before successfully to use a non-standard resolution on a monitor.  However, you have been warned that you need to understand what you're doing or you may damage your hardware.

---

