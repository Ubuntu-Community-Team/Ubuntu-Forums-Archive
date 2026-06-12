---
title: "Playing Video on TV"
date: 2010-03-06
forum: New to Ubuntu
---

### Post by Rosc0PColtrane on 2010-03-06
Hi, 

A quick question if I may: I've installed Ubuntu a few months ago, on my laptop and love it. I used to use my laptop to connect to my tv (CRT) to watch video. Specifically video I have filmed. We've been blessed with a new arrival and I'd like to watch the videos of both my first and second child. 

It used to be a case of pressing the 'fn' and F4 key a couple times. This meant both my laptop monitor and tv displayed the image. Specifically on my TV, just the video.

It's all connected via S-Video.

Now, my fn and F4 key trick no longer works. I've scoured the net for the answer and have had no luck. Is there a straightforward way of achieving this??

Thanks in advance.

---

### Post by Rosc0PColtrane on 2010-03-07
bump!

---

### Post by Rosc0PColtrane on 2010-03-07
I posted this question on another part of the forum, but got no reply, so have assumed it's fairly simple stuff and beneath the super-eggs of that section.

Here's the link: [http://ubuntuforums.org/showthread.php?p=8931273#post8931273](http://ubuntuforums.org/showthread.php?p=8931273#post8931273)

Anyway. How do I get my laptop to play video on TV via S-Video? Is there a simple thing I'm missing in ubuntu itself, or do I need to install something??


Thanks!

---

### Post by fatality_uk on 2010-03-07
Can you provide some futher details. What brand/model of laptop do you have? Which version of Ubuntu are you using?

---

### Post by cariboo on 2010-03-07
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by lavinog on 2010-03-07
Because this is community support, sometimes a response might take a while.

To answer your question, it really would help if you gave some details about your laptop.  Different brand video cards have different solutions.
If you have an ATI or Nvidia card, you might need to activate the proprietary driver (located in System>admin>hardware drivers.)
Only recent ATI cards are supported by the proprietary driver. (less than 3 years old)

---

### Post by merlinof2 on 2010-03-07
I have a similar problem...  I have Ubuntu (now 9.10) dual booting with XP on a Sony Vaio and it's worked great for a couple of years.  I could use the system fine, and if I wanted to, I could hook up my 32" Vizio via a VGA cable, then using SYSTEM > PREFERENCES > DISPLAY, I could toggle video to the 32" display using the same 1366x768 resolution... it was great.  Suddenly, about 2 months ago, trying to toggle to the 32" would cause a hard lockup requiring a power off to recover.  What I should mention, is that if I power up the system with the auxilary VGA connected to the Vizio, it will display exactly what the Sony is showing on the screen, right up to login screen.  Then the Vizio goes black and won't come back.  I don't know if it was one of the updates that took out the video toggle or what...  but I surely would like the feature back.
Thanks in advance for any assistance.

---

### Post by Rosc0PColtrane on 2010-03-08
Sorry about the poor Netiquette!!! My laptop is a Compaq Pressario V2000 and I'm running Ubuntu 9.10

Looks like the SYSTEM ADMIN DISPLAY may provide me an avenue to explore when I next get chance!

---

### Post by HarrisonNapper on 2010-03-08
Yeah, there are a few possibilities here:

1. Your video driver does not support multiple monitors
2. Your video card is incapable of drawing the display for your TV
3. You can reboot and be off to watching videos of your kids

Plug in the TV, reboot the computer, and let us know how it goes.

---

### Post by lavinog on 2010-03-08
found this:
[http://wiki.x.org/wiki/radeonTV](http://wiki.x.org/wiki/radeonTV)

> 
Enabling TV-Out Dynamically

TV-out may be enabled by using a recent driver and xrandr utility:

   1. xrandr --addmode S-video 800x600
   2. xrandr --output S-video --mode 800x600
   3. xrandr --output S-video --set tv_standard ntsc 


I have a v5000 with the same card,  I will see if I can get this to work.

Update: No luck getting it to work.

---

### Post by Rosc0PColtrane on 2010-03-09
Thanks for the ideas. It worked fine when I had XP installed. I'll be sure to try these things when I next get opportunity to have a pop at it.

---

### Post by anthonyrossbach on 2010-03-09
If you open the Display settings and you click show displays in panel it will be in your notification area, then you can click it and click configure display settings and if you do this when your TV is plugged in you will get a black screen for a second then you will see the display manager and 2 screens, 1 for your laptop and one for your TV and you can make them 1 screen or a extended desktop.

I do this myself and it takes me like 3 seconds to start watching a movie on my tv and still be able to use my computer!

---

### Post by lavinog on 2010-03-09
> **anthonyrossbach said:**
> If you open the Display settings and you click show displays in panel it will be in your notification area, then you can click it and click configure display settings and if you do this when your TV is plugged in you will get a black screen for a second then you will see the display manager and 2 screens, 1 for your laptop and one for your TV and you can make them 1 screen or a extended desktop.

I do this myself and it takes me like 3 seconds to start watching a movie on my tv and still be able to use my computer!

Did not work for me.
What card do you have?
The radeon 200 seem to have some unique issues:
per man radeon:
> 
TV-out support (only on R/RV/RS1xx, R/RV/RS2xx,  R/RV/RS3xx.  Experi&#8208;
         mental support on R/RV5xx, R/RV6xx, and R/RV7xx through the ATOMTvOut

Notice the RS400/480 (radeon 200) is not listed.

---

### Post by lavinog on 2010-03-09
I got it working by following this page:
[http://wiki.archlinux.org/index.php/ATI#TV_out](http://wiki.archlinux.org/index.php/ATI#TV_out)
```

xrandr --output S-video --set load_detection 1
xrandr --output S-video --set tv_standard ntsc
xrandr --addmode S-video 800x600
xrandr --output S-video --same-as VGA-0
xrandr --output S-video --mode 800x600

```
And I got my video on my tv.

Hope this helps

Also, When I opened the display properties, the tv-out was disabled...so it looks like the command line is the only way at the moment.

If it doesn't work for you, try using my /etc/X11/xorg.conf:
```

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

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"radeon"
	option		"ClockGating"	"on"
#	Option          "DynamicPM"  	"on"
#	Option		"R4xxATOM"	"on"

	Option		"TVStandard"	"ntsc"
	Option 		"AccelDFS" 	"on"

	Option		"TVDACLoadDetect"	"on"
 	Option 		"ForceTVOut" 	"off"
	Option 		"ATOMTvOut" 	"on"



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
Only use it if it doesn't work for you, I am experimenting with some of the settings in it, and some are experimental.

---

### Post by Rosc0PColtrane on 2010-03-13
I followed the above xrandr commands. The screen flashed and then returned. Opened the display settings and for a second there was an 'unknown monitor', which is now gone and I don't know how to get it back. Couldn't get it on my TV though..

What's the next bit you've described there?? xorg.conf??

I also do not have a TV out option on DISPLAY??

---

### Post by lavinog on 2010-03-13
> **Rosc0PColtrane said:**
> I followed the above xrandr commands. The screen flashed and then returned. Opened the display settings and for a second there was an 'unknown monitor', which is now gone and I don't know how to get it back. Couldn't get it on my TV though..

the display properties undoes the commands to enable it.  You cannot open the display properties when trying to get it to work.

> 
What's the next bit you've described there?? xorg.conf??

I also do not have a TV out option on DISPLAY??

xorg.conf is located in /etc/X11.
it is a configuration file that tells the xserver what drivers to use for your hardware, and allows tweaking of those drivers.  By default it should be blank or non-existant.  The xserver does its best to auto-configure the options, but sometimes the default settings are set in a "safe-mode" because the driver is still unstable with some devices.
Currently it is a trial and error issue.

I will be installing Lucid alpha on my laptop this week.
I will be sure to check to see if there are any improvements in the tv-out function.

---

### Post by Rosc0PColtrane on 2010-03-14
> **lavinog said:**
> the display properties undoes the commands to enable it.  You cannot open the display properties when trying to get it to work.



xorg.conf is located in /etc/X11.
it is a configuration file that tells the xserver what drivers to use for your hardware, and allows tweaking of those drivers.  By default it should be blank or non-existant.  The xserver does its best to auto-configure the options, but sometimes the default settings are set in a "safe-mode" because the driver is still unstable with some devices.
Currently it is a trial and error issue.

I will be installing Lucid alpha on my laptop this week.
I will be sure to check to see if there are any improvements in the tv-out function.

I'm toying with the idea of a windows emulator and using the original video card drivers?? It had a decent monitors controller.

---

### Post by lavinog on 2010-03-15
> **Rosc0PColtrane said:**
> I'm toying with the idea of a windows emulator and using the original video card drivers?? It had a decent monitors controller.

When you say windows emulator are you referring to Wine?
or are you referring to a running windows in a virtual machine?

Both methods use ubuntu with your current video drivers, so it wont work.

---

