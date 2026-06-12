---
title: "linuxwacom on Fujitsu T4410"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by ecksiota on 2010-01-02
Hi,

I recently got a Fujitsu T4410 with dual digitizer and am glad to report that most of the hardware works out of the box. The multitouch capable dual digitizer unfortunately does not work completely and I would like some help on that.

The hardware in question is a Wacom serial tabletpc device. Configuring the serial port by:
```

setserial /dev/ttyS0 port 0x0220 irq 4 autoconfig
```

activates the port for communication.  Furthermore,

```
xxd /dev/ttyS0
```

reports activity on both the pen events AND touching with fingers. I went ahead with linuxwacom-0.8.5-9, as the linuxwacom website says that's the minimum required to enable touch.  Using the attached xorg.conf, I can get the "stylus" and "eraser" inputs to work, but not the "touch". Xorg.0.log shows an error like:

> PreInit returned NULL for "touch"

Also, strangely, having the pen in proximity to the screen while X is starting makes the pen input go awry. So does touching the screen while X is starting. 

I am out of ideas to try. Please let me know if you experience the same or have a resolution.

Thanks.

---

### Post by Favux on 2010-01-03
Hi ecksiota,

Nice job to get stylus and eraser.  There are a few things we could do with the xorg.conf.  But if you are in Karmic the preferred method is a .fdi (device information file) and HAL/DeviceKit.

So what we need is to determine the plug and play (PnP) for your digitizer.  Try:
```
grep -i name /proc/bus/input/devices
```
and:
```
lshal>ecksiota_lshal.txt
```

And post the outputs.  The Xorg.0.log doesn't show touch as you know but it does show 2 keyboards, which is probably a big fat clue.

---

### Post by ecksiota on 2010-01-03
Thanks Favux, here is the info you requested.

```
$ grep -i name /proc/bus/input/devices
N: Name="Power Button"
N: Name="Lid Switch"
N: Name="Power Button"
N: Name="Macintosh mouse button emulation"
N: Name="AT Translated Set 2 keyboard"
N: Name="Video Bus"
N: Name="Fujitsu FUJ02B1"
N: Name="Fujitsu FUJ02E3"
N: Name="fsc tablet buttons"
N: Name="fsc tablet switch"
N: Name="CNF8248"
N: Name="HDA Digital PCBeep"
N: Name="ImPS/2 Generic Wheel Mouse"

```

The output of lshal is also attached. I know I should be looking into understanding udev and hal but it will take time for me to get used to them. The fjbtndrv drivers from khnz ppa work for me out-of-the-box for the tablet buttons, in case anyone wants to know. It will be fabulous if a hal fdi file is all that is needed. Thanks again Favux.

---

### Post by Favux on 2010-01-03
Hi ecksiota,

Unfortunately I do not see it in your lshal.  I don't believe any of the PnP identifiers is your tablet.  Ping's guess at the LWP is that it would be 'FUJ02e9'.

He also recommended updating the '8250_pnp.ko' (serial plug and play kernel driver/module) so that it would be identified.  However as near as I can figure out the last time there was a 8250_pnp.ko was Hardy.  I think it has been placed into the kernel.  Either by Ubuntu or the upstream kernel dev.s.  So it looks like to get a wacom.fdi working for you you'll need a kernel update that recognizes your tablet.

So that leaves us the xorg.conf.  To get touch working we have to hope the most recent wacom.rules symlink table that goes in udev has your tablet.  It would be in /src/utils in the 0.8.5-9 tar.  If not stylus and eraser are the best you will be able to do for now.

Stylus or eraser would be:
```
	Option		"Device"	"/dev/input/wacom"
```
and touch:
```
	Option		"Device"	"/dev/input/wacom-touch"
```

But first let's clean up your current xorg.conf a little.  How did you get it?  Was there an xorg.conf when you started?  Did you generate it or build it by hand?  Oh, and you are in Karmic correct?

---

### Post by ecksiota on 2010-01-03
I thoroughly read the linuxwacom detailed howto before attempting to configure the device myself; the howto is very clear despite the plethora of devices and configuration possibilities out there. In the process I verified (by downloading the kernel sources) that 8250_pnp.c exists, but does not have the {"WACFXXX", 0}, line.

```
$ locate 8250_pnp
/usr/src/linux-source-2.6.31/drivers/serial/8250_pnp.c
$ grep WAC `locate 8250_pnp.c`
	{	"WACF004",		0	},
	{	"WACF005",		0	},
	{       "WACF006",              0       },
	{       "WACF007",              0       },
	{       "WACF008",              0       },
	{       "WACF009",              0       },
	{       "WACF00A",              0       },
	{       "WACF00B",              0       },
	{       "WACF00C",              0       },
```

Would recompiling the kernel be a solution? The wacom.rules in 0.8.5-9.tar is identical to the one installed on my system.

About the xorg.conf, I built it starting from the default (printed by X in Xorg.0.log) and then adding to it bits from the linuxwacom detailed howto. I installed the new xorg.conf you attached and, not surprisingly, the results are identical.

You may find some significance in this piece of information, though I have no idea how to use it.

```

$ xsetwacom list
stylus
eraser
imps/2 generic wheel mouse
power button
fujitsu fuj02b1
at translated set 2 keyboard
fsc tablet buttons
cnf8248
power button
video bus
fujitsu fuj02e3
macintosh mouse button emulation
stylus     stylus
eraser     eraser
CNF8248     stylus

```

This CNF8248 device on the last line is what I recently noticed. Is that of any significance? Why is it showing up as a stylus? 

I'm on Ubuntu Karmic. What would be the next step for me to do?

---

### Post by Favux on 2010-01-03
Hi ecksiota,

> **ecksiota said:**
> I thoroughly read the linuxwacom detailed howto before attempting to configure the device myself; the howto is very clear despite the plethora of devices and configuration possibilities out there. In the process I verified (by downloading the kernel sources) that 8250_pnp.c exists, but does not have the {"WACFXXX", 0}, line.

```
$ locate 8250_pnp
/usr/src/linux-source-2.6.31/drivers/serial/8250_pnp.c
$ grep WAC `locate 8250_pnp.c`
	{	"WACF004",		0	},
	{	"WACF005",		0	},
	{       "WACF006",              0       },
	{       "WACF007",              0       },
	{       "WACF008",              0       },
	{       "WACF009",              0       },
	{       "WACF00A",              0       },
	{       "WACF00B",              0       },
	{       "WACF00C",              0       },
```
Good find.  I also noticed in the kernel team's compile list a 8250_pnp.h.
> **ecksiota said:**
> Would recompiling the kernel be a solution? The wacom.rules in 0.8.5-9.tar is identical to the one installed on my system.
It would be if there was an updated 8250_pnp.c (the 8250_pnp.h is probably ok).  But I can't find any upstream commit of a diff to 8250_pnp.c.  Maybe you will have better luck.  Or if you knew what the PnP identifier was you could manually enter it into the 8250_pnp.c and compile the kernel.  But the identifier would probably be in an upstream commit too.
> **ecksiota said:**
> About the xorg.conf, I built it starting from the default (printed by X in Xorg.0.log) and then adding to it bits from the linuxwacom detailed howto. I installed the new xorg.conf you attached and, not surprisingly, the results are identical.
Correct, that was expected.  I want to clear the "clutter" out first so if there are problems we know what changes are responsible.
> **ecksiota said:**
> You may find some significance in this piece of information, though I have no idea how to use it.
```

$ xsetwacom list
stylus
eraser
imps/2 generic wheel mouse
power button
fujitsu fuj02b1
at translated set 2 keyboard
fsc tablet buttons
cnf8248
power button
video bus
fujitsu fuj02e3
macintosh mouse button emulation
stylus     stylus
eraser     eraser
CNF8248     stylus

```
This does not look right at all.  What you should be seeing with "xsetwacom list" is:
```
stylus     stylus
eraser     eraser
touch     touch
```
> **ecksiota said:**
> This CNF8248 device on the last line is what I recently noticed. Is that of any significance? Why is it showing up as a stylus?
I don't think so.  I tracked them all down.  I don't believe any are your digitzer.
> **ecksiota said:**
> I'm on Ubuntu Karmic. What would be the next step for me to do?
I think our only current option is an xorg.conf.  I don't know if we can get touch with it.  But who knows?  :)

---

### Post by Favux on 2010-01-03
Here's the next version of the xorg.conf.  I changed your video sections and the line in "ServerLayout".  Be prepared for X breakage this time and ready to restore your previous working xorg.conf from the command line.

If this one works then the next step is to remove the video sections altogether.  In Karmic with Intel video you probably didn't have an xorg.conf at all would be my guess.  So then delete:
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
I think this will work, but I am not sure.

If that works we will be down to the minimal necessary xorg.conf for your tablet.

---

### Post by ecksiota on 2010-01-04
You were right. Your xorg.conf worked. Attached is the Xorg.log. Also xsetwacom displays the same output.

```

$ xsetwacom list
stylus
eraser
fsc tablet buttons
fujitsu fuj02b1
power button
power button
fujitsu fuj02e3
at translated set 2 keyboard
cnf8248
video bus
imps/2 generic wheel mouse
macintosh mouse button emulation
stylus     stylus
eraser     eraser
CNF8248     stylus

```

About recompiling the kernel with modified 8250_pnp.c, is there an easy way for me to find the PnP identifier? From either a linux log or even through booting into Win XP? I am willing to experiment if it is safe.

I will delete the Device, Monitor and Screen sections (and also from the serverlayout) and post the next log now.

---

### Post by Favux on 2010-01-04
Hi ecksiota,

I sure wouldn't compile the kernel unless I knew the 8250_pnp.c had the identifier for your tablet.  Then you'd already know it or could look through the 8250_pnp.c.  Just like in lshal it will most likely begin with FUJ as in the 'FUJ02e9' Ping suggested.

---

### Post by ecksiota on 2010-01-04
Same output on removing the Device, Screen and Monitor sections. I realized I did not have to further modify the SeverLayout from the previous xorg.conf. Also I added a "Option BaudRate 38400" to the stylus and eraser to check if they respond any faster on writing. Does not really help, 9600 is a fast enough rate. So I will revert it back.

I guess to obtain identical functionality, I can also delete the touch InputDevice section. But apart from that, is there anything else I should try? Thanks Favux for taking the time to help me out. From one of your previous post it seemed like touch may not work for now. That's a relief in at least one sense: I am not completely stupid. :)

---

### Post by Favux on 2010-01-04
Hi ecksiota,

> That's a relief in at least one sense: I am not completely stupid.
Of course you aren't, this is a hard problem.

I don't think there is anyway to get touch right now.  I think the linuxwacom code has to be able to identify your tablet for touch to work.  There's several places where it wants to define the ToolType for your tablet and it can't do that since it can't identify it.  We need to know the PnP identifier to do much of anything I think.

Actually it is an accomplishment to have stylus and eraser working.  They do work, correct?

Just to be sure this is the xorg.conf you are currently using, correct?  I just commented out touch because I'm an optimist.  :)

---

### Post by ecksiota on 2010-01-04
Yes, this is the xorg.conf I am currently using. And yes, fortunately the stylus and cursor are both working. Making the touch work is probably just a matter of time for the t4410 to be popularly used.

I hope someone like you gets your hands on a t4410 and figures out the PnP id. Just out of curiosity though, how does one figure this out? I'd be happy to help in any way I can.

---

### Post by Favux on 2010-01-05
Hi ecksiota,

Out of curiosity how did you determine this was the port you needed?:
```
setserial /dev/ttyS0 port 0x0220 irq 4 autoconfig
```

Olaf (another Fujitsu T4410 owner) points out that the lack of PnP identifier could be a BIOS issue, maybe with the DSDT.  Have you checked that you have the latest bios?

---

### Post by ecksiota on 2010-01-06
I wished I knew better. I just copied the setserial line reported by many linux-on-fujitsu users. (A google search on fujitsu wacom setserial finds many webpages mentioning the setserial command to be configured exactly as I quoted.) You are right, it's already a miracle that the stylus works.

I checked for any bios update from fujitsu and I found none. Hence I assumed I had the latest bios.

---

### Post by Favux on 2010-01-06
Hi ecksiota,

Usually you use:
```
dmesg | grep ttyS
```
and with luck it returns the port and irq, etc.

Ok, just so you are aware it's possible it may also be a bios issue.  So keep a look out for updates.  And you'll want to install a new bios in Windows not linux.

By the way Olaf got his stylus working with your serial.conf line and the xorg.conf we came up with.  Thought you'd like to know.

---

### Post by cooltech786 on 2010-03-27
Hello,

Just recently got a T4410.  I've been an Ubuntu fan for a long time now - so I'm currently dual booting Lucid and Win7.

The pen worked out of the box for me, but the touch didn't.  Just wondering if anybody has made any progress on that.

Thanks
-cooltech786

---

### Post by ecksiota on 2010-04-07
Hi cooltech786,

The touch magically started working for me over the weekend. I updated to the latest Karmic kernel:

$ uname -a
Linux localhost 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux

downloaded the latest linuxwacom version 0.8.5-12 source from:

[http://linuxwacom.sourceforge.net/](http://linuxwacom.sourceforge.net/)

compiled and installed it, and rebooted. Magically, the touchscreen started to respond to my fingers. I haven't had time to figure out exactly what changed, but may be Favux may be able to tell.

---

### Post by Favux on 2010-04-27
Hi ecksiota,

> The touch magically started working for me over the weekend. I updated to the latest Karmic kernel:

$ uname -a
Linux localhost 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux

downloaded the latest linuxwacom version 0.8.5-12 source from:

[http://linuxwacom.sourceforge.net/](http://linuxwacom.sourceforge.net/)

compiled and installed it, and rebooted. Magically, the touchscreen started to respond to my fingers.
Outstanding!  How well does it work?

Hopefully it means Ping and co. at LWP have finished adding the Fujitsu identifiers to the code and also submitted them to the kernel.  So maybe the nagging paid off.

---

### Post by Favux on 2010-04-28
Hi everyone,

As further confirmation of the Fuji id's being added see:  [http://sourceforge.net/mailarchive/forum.php?thread_name=20100428111840.GA18502%40barra&forum_name=linuxwacom-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=20100428111840.GA18502%40barra&forum_name=linuxwacom-devel)

So if you have a Fujitsu and are in Lucid you want to change the 10-wacom.conf at "/usr/lib/X11/xorg.conf.d/" from:
```
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection
```
to
```
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class identifiers"
	MatchProduct "WACf|FUJ02e5|FUJ02e7"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection
```
And keep an eye out for new Fujitsu identifiers.  I think a "FUJ02e9" may be out.

---

### Post by sigbjornt on 2010-05-04
After doing the change, my pen stopped working. 
It started to work once more after I changed the line 
```
MatchProduct "WACf|FUJ02e5|FUJ02e7"
```
to
```

MatchProduct "WACf|FUJ02e5|FUJ02e7|Serial Wacom Tablet"

```

Is this the correct way to do it, or am I going to get in trouble later for doing this?

---

### Post by Favux on 2010-05-04
Hi sigbjornt,

No that's fine.  What that is probably saying is is the Fujitsu idenifiers aren't in fact in the code.  And sure enough I looked at the kernel driver/module source code in linuxwacom 0.8.6-1's wacom_wac.c and no Fujitsu identifiers.  What appears to be happening is starting around the 0.10.5 version, the wcmUSB.c source code was rewritten in xf86-input-wacom so it no longer rejects non-wacom tablet signals coming from the kernel, as long as the format is proper.  The question I have is the Fujitsu still being picked up by the wacom.ko somehow and data passed the xf86-input-wacom X driver, or is it some other kernel driver?
 
You could further look at what Match Product lines are available on your system by doing:
```
udevadm info --export-db > $HOME/udev.txt
```
But clearly you have a line with "Serial Wacom Tablet" in it.

---

### Post by sigbjornt on 2010-05-05
Are the string in the "MatchProduct" line case sensitive? I noticed that ```
udevadm info --export-db > $HOME/udev.txt
``` 
gives the following lines matching FUJ2E3 (notice the capital E)
```



P: /devices/LNXSYSTM:00/LNXSYBUS:00/FUJ02E3:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/FUJ02E3:00
E: DRIVER=Fujitsu laptop FUJ02E3 ACPI hotkeys driver
E: MODALIAS=acpi:FUJ02E3:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/LNXSYBUS:00/FUJ02E3:00/input/input7
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/FUJ02E3:00/input/input7
E: PRODUCT=19/0/6/0
E: NAME="Fujitsu FUJ02E3"
E: PHYS="FUJ02E3/video/input0"
E: EV==3
E: KEY==1000000000c00 300000 0 0
E: MODALIAS=input:b0019v0000p0006e0000-e0,1,k94,95,CA,CB,F0,ramlsfw
E: SUBSYSTEM=input

P: /devices/LNXSYSTM:00/LNXSYBUS:00/FUJ02E3:00/input/input7/event7
N: input/event7
S: char/13:71
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/FUJ02E3:00/input/input7/event7
E: MAJOR=13
E: MINOR=71
E: DEVNAME=/dev/input/event7
E: SUBSYSTEM=input
E: ID_INPUT=1
E: ID_INPUT_KEY=1
E: XKBMODEL=pc105
E: XKBLAYOUT=no
E: DEVLINKS=/dev/char/13:71
E: XKBOPTIONS=lv3:ralt_switch,compose:lwin
E: DMI_VENDOR=FUJITSU SIEMENS


```
And same for FUJ02E7
```

P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:43/FUJ02E7:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:43/FUJ02E7:00
E: MODALIAS=acpi:FUJ02E7:ACPI\WACF004:
E: SUBSYSTEM=acpi

```

---

### Post by Favux on 2010-05-05
Hi sigbjornt,

I don't know if they are case sensitive, but it looks probable.  Because FUJ02E7 sure looks like your Wacom digitizer.  Look at this line:
```
MODALIAS=acpi:FUJ02E7:ACPI\WACF004:

```
WACF004 is a Wacom digitizer identifier.  I bet if you follow the FUJ02E7 tree from the farthest branch towards the trunk you'll spot "Serial Wacom Tablet"

So test it and then we can notify the LWP that they need to specify both cases.

---

### Post by sigbjornt on 2010-05-11
> **Favux said:**
> 
I bet if you follow the FUJ02E7 tree from the farthest branch towards the trunk you'll spot "Serial Wacom Tablet"

So test it and then we can notify the LWP that they need to specify both cases.

Hi Favux.
Could you point me to a tutorial or how-to? I understand the task but I do not know how to do it. (luckily this is the "[Absolute  Beginner Talk]("http://art.ubuntuforums.org/forumdisplay.php?f=326")" section)

btw: Sorry for the late follow up

---

### Post by Favux on 2010-05-11
Hi sigbjornt,

Just right click on the output and compress it using Create Archives.  Then attach it to your next post using Manage Attachments below.  I'll take a look at it.

---

### Post by sigbjornt on 2010-05-12
Thank you Favux. I really appreciate your help.

Is this correct?

---

### Post by Favux on 2010-05-12
Hi sigbjornt,

OK, I think we've made some progress.  This section:
```
P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:43/FUJ02E7:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:43/FUJ02E7:00
E: MODALIAS=acpi:FUJ02E7:ACPI\WACF004:
E: SUBSYSTEM=acpi
```
Definitely has your serial PnP Identifier and it is FUJ02E7.  Then there must be a udev rule that picks up tablet input somewhere and gives us these three sections:
```
P: /devices/pnp0/00:04
E: UDEV_LOG=3
E: DEVPATH=/devices/pnp0/00:04
E: SUBSYSTEM=pnp
E: NAME=Serial Wacom Tablet
E: ID_INPUT=1
E: ID_INPUT_TABLET=1

P: /devices/pnp0/00:0c
E: UDEV_LOG=3
E: DEVPATH=/devices/pnp0/00:0c
E: DRIVER=serial
E: SUBSYSTEM=pnp
E: NAME=Serial Wacom Tablet
E: ID_INPUT=1
E: ID_INPUT_TABLET=1

P: /devices/pnp0/00:0c/tty/ttyS0
N: ttyS0
S: char/4:64
E: UDEV_LOG=3
E: DEVPATH=/devices/pnp0/00:0c/tty/ttyS0
E: MAJOR=4
E: MINOR=64
E: DEVNAME=/dev/ttyS0
E: SUBSYSTEM=tty
E: ID_INPUT=1
E: ID_INPUT_TABLET=1
E: DEVLINKS=/dev/char/4:64
```
And there's your 'Serial Wacom Tablet'.  So I went to the [xf86-input-wacom git repository]("http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=shortlog") (the X driver for Lucid's Xserver 1.7) and sure enough found a commit for your identifier only two weeks ago.  And that was after 0.10.6 came out!
> 13 days ago     Peter Hutterer     conf: add WACf, FUJ02e5 and FUJ02e7 to serial identifers.
Since the first section indicates that your serial identifier has been added to the kernel's PnP driver for serial stuff it looks like all you need to do is clone the current git repository.  This is described in Appendix 5 in the [linuxwacom HOW TO.]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  Read the Lucid section near the top first.

---

### Post by cooltech786 on 2010-06-16
Hey guys,
Haven't checked in on this for a while.

It seems that you said that the new linuxwacom kernel got touch working.  I'm a complete newbie to linux, just understanding some of the most basic things.  Can't figure out how to compile and install this new kernel.  Any advice?

Thanks!!!

---

### Post by Favux on 2010-06-16
Hi cooltech786,

You don't need a new kernel.  You compile a new X driver and may be modifiy the wacom.conf.  Follow the link in post #27 and read through the HOW TO a few times starting with Lucid near the top and then Appendix 5 and Section 2 c.  See if it starts to make sense.

---

### Post by jjulia on 2010-08-22
Hi

Sorry for my English.

I have a FUJITSU T4410 with wacom FUJ02E7 serial device.

I believe that there is a bug on xf86-input-wacom-0.10.8 and the device is not properly detected.

If you execute "xinput -llist" there is not "Serial Wacom Tablet touch", only "Serial Wacom Tablet eraser" and "Serial Wacom Tablet stylus".

I have added one line on wcmISDV4.c and touch works now and I can see a new device on "xinput --list" output.

The change is:

root@fujitsu:/usr/local/src/xf86-input-wacom-0.10.8/src# diff wcmISDV4.c wcmISDV4.c.orig 
876d875
<     SETBIT(common->wcmKeys, BTN_TOOL_DOUBLETAP);


Now you must see "Serial Wacom Tablet stylus: serial tablet id 0xE3." on Xorg.0.log and touch should be working.

I also have added the following file:
root@fujitsu:/usr/local/src/xf86-input-wacom-0.10.8/src# cd
root@fujitsu:~# cat /etc/X11/Xsession.d/99-wacom 
/usr/bin/xsetwacom --set 16 "gesture" on
/usr/bin/xsetwacom --set 16 "TapTime" 250

Now, stylus, eraser and touch is working on my FUJITSU T4410 on Ubuntu Lucid with linux-maverick 2.6.35 kernel, but i think that this also works with Ubuntu Lucid "standard" kernel.

---

### Post by Favux on 2010-08-22
Hi jjulia,

Welcome to Ubuntu forums!

Nice work!!!

I urge you to submit properly formatted git patchs to linuxwacom-dev:  [https://lists.sourceforge.net/lists/listinfo/linuxwacom-devel](https://lists.sourceforge.net/lists/listinfo/linuxwacom-devel)  That way they'll learn there is a problem and be able to review your fixes and hopefully include them.

---

### Post by Favux on 2010-08-29
Hi jjulia,

Thank you very much for submitting your patches to linuxwacom-devel.  I really appreciate it.

They will want a properly formatted git patch before they will accept them.  The most important thing about a git patch is it will have a "signed by" with your name.

To do this see these links:

[http://wiki.x.org/wiki/Development/Documentation/SubmittingPatches](http://wiki.x.org/wiki/Development/Documentation/SubmittingPatches)

[http://sysmonblog.co.uk/misc/git_by_example/](http://sysmonblog.co.uk/misc/git_by_example/)

[http://linux.yyz.us/git-howto.html](http://linux.yyz.us/git-howto.html)

Please ask if you have any questions.

---

### Post by jjulia on 2010-09-01
Hi Favux,

I am not a developer but I am helping wacom-devel developers to test the patch that they are doing. I hope that they include this patch on next release of xf86-linux-wacom.

Now, I can do the following with unbuntu 10.04: pen, touch and gestures on Google Earth, Gimp, jarnal, xournal, firefox, etc.

I also installed fjbtndrv-2.1.3

I am happy with this :-)

Cheers.

---

### Post by Favux on 2010-09-01
Hi jjulia,

Very nice work!  Sounds like you have your Fujitsu T4410 pretty much working in Lucid.

---

### Post by askvictor on 2010-10-19
Thanks jjulia; with these instructions I've finally got touch working on my T4410!

Looking into the code, it appears that the the wacom driver is looking for a particular ID code in /sys/class/tty/ttyS0/device/id - and in wcmISDV4.c it only checks if that ID starts with "WACf" - if not, it assumes a default ID of 0. However, in the Fujitsu case, the ID starts with "FUJ", so the code doesn't pick it up, and the DOUBLETAP bit doesn't get set (this occurs on the following line in the if statement). Your patch, while it works in this particular case, might break other things.

Cheers,

vik

---

### Post by askvictor on 2010-10-19
In fact, I've found a thread on linuxwacom-devel that includes a patch:
[http://www.mail-archive.com/linuxwacom-devel@lists.sourceforge.net/msg00762.html](http://www.mail-archive.com/linuxwacom-devel@lists.sourceforge.net/msg00762.html)

---

### Post by askvictor on 2010-10-21
Looking further, this has been fixed in the trunk of linuxwacom as of September 2010. But I'm not certain how to build the trunk into a .deb (and the version in 11.04 doesn't include these latest updates). Might set up a ppa one of these days if I find out how.

---

