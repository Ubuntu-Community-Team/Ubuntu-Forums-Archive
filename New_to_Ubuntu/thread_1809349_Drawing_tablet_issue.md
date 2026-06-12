---
title: "Drawing tablet issue"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by wishingstar on 2011-07-21
I have been using kde for the last couple of releases (kubuntu 10.10 and 11.04) and this issue exists in both.

I am trying out drawing on the computer using drawing tablets (needs getting used to because of the different fluidity). I've been using gimp on gnome, but when I switched to KDE I fell in love with krita.

My issue is that there is always a delay when I draw quickly with fluid motions, the software (gimp or krita) would not register half the strokes, I would have to go over the areas again which makes the drawing lose part of its fluidity. I was wondering if there is a way around this issue, as I really don't want to have to boot into MS every time I want to draw something. MS does not have this issue even though it runs on the same hardware and, from what I hear, is more resource hungry.

I also have a couple more questions about using drawing in linux:

1- Does krita have pressure sensitivity? How do I set it up? Does that gimp have that?

2- Would drawing be fluid if I try to use MS within virtualbox?

My Specs:
AMD Athlon X2 Dual Core - 32-bit Kubuntu 11.04 
356MB VGA ATI X1200
4GB RAM
Drawing tablet: Genius G-Pen 560

Thanks for the help...
-Wishing Star

---

### Post by Favux on 2011-07-21
Well gimp should have pressure sensitivity.  If you don't have it have you checked your setup in extended devices?

Maybe you need to adjust your configuration in the .conf file or maybe you have the wrong driver?

What is the output in a terminal of *xinput list*?

---

### Post by wishingstar on 2011-07-22
Thank you for responding Favux.

I do not have a configuration file or driver for it, I only used it as plug and play...perhaps that's the real cause of the problem. Do you know how I can configure it?

As for the command output, I don't have access to my machine right now, I'll post it once I get back home this evening.

Thanks again for the help.

-Wishing Star

---

### Post by Favux on 2011-07-22
> I do not have a configuration file or driver for it, I only used it as plug and play...perhaps that's the real cause of the problem. Do you know how I can configure it?
It depends on the actual maker of the tablet as to which X driver and the corresponding .conf file in xorg.conf.d is used.  A lot of tablets are rebranded so we need to know the OEM.  That's what *xinput list* will tell us.  What happens to an unclaimed tablet is evdev picks it up.  Evdev is the fall back X driver but it often doesn't work as well as the correct driver would even though it provides some function.

---

### Post by mastablasta on 2011-07-22
> **wishingstar said:**
>  
I do not have a configuration file or driver for it, I only used it as plug and play...perhaps that's the real cause of the problem. Do you know how I can configure it?
 
 
if you just plug and play you are using a driver the one that is provided by linux kernel.
 
drivers are programmes that help interact any device with motherboard and other devices. so you have drivers for keyboard, mouse, monitor (graphics), sound, CD drive etc... :-)
 
if it's opensource driver then usually there is a way to configure it, however since i have no experience with drwaing tablets i don't know where to look for config file or programme.
 
you could start of by posting your model as found by linux.
 
if oyu plug it in via USb then this command should show it in terminal:
 
lsusb

---

### Post by wishingstar on 2011-07-23
sorry for being late getting back to you, here are the outputs of the commands:

1- xinput list
```
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                id=11   [slave  pointer  (2)]
&#9116;   &#8627;  USB OPTICAL MOUSE                        id=9    [slave  pointer  (2)]
&#9116;   &#8627; Aiptek                                    id=12   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Power Button                              id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=10   [slave  keyboard (3)]

```

2-lsusb:
```
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0458:5003 KYE Systems Corp. (Mouse Systems) G-pen 560 Tablet
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 15d9:0a4c Trust International B.V. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 001 Device 002: ID 0480:a001 Toshiba America Info. Systems, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I think the pad is Aiptek from the first command and Bus 003 from the second command.

---

### Post by Favux on 2011-07-24
Yep, I agree its an Aiptek.  So check in Synaptic Package Manager that the Aiptek X driver is installed.  I think Ubuntu calls it something like xorg-xserver-input-aiptek.  If not install it.

The package didn't use to come with an aiptek.conf to match the tablet to the driver.  I think I may have read something about that being fixed but I don't know if the package has been updated to include it yet.  So after you install it and reboot check in /usr/share/X11/xorg.conf.d for an aiptek.conf.  It will have some number in front of it.  If not we can manually add one.  I'll have to dig up one that I have somewhere.

---

### Post by wishingstar on 2011-07-25
I just installed the aiptek driver and rebooted, there is no configuration file in that location named aiptek. The ones I currently have there are: synaptics, wacom, evdev and vmmouse.

Is it possible to control this lag/delay through a configuration script that is placed in this folder?
Thanks

---

### Post by Favux on 2011-07-25
Hi wishingstar,

I'm pretty sure the lag is from your Aiptek tablet being on the evdev X driver.  You could check by entering in a terminal:
```
xinput list-props "Aiptek"
```
This is because you don't have an aiptek.conf to match the tablet to the aiptek X driver.

So we will create one with the following contents:
```
Section "InputClass"
        Identifier "Aiptek class"
        MatchProduct "Aiptek|AIPTEK|aiptek"
        MatchDevicePath "/dev/input/event*"
        Driver "aiptek"
        Option "USB" "on"
        Option "Type" "stylus"
        Option "Mode" "absolute"
        Option "zMin" "0"
        Option "zMax" "511"
EndSection
```
Does your tablet have 512 levels of pressure?  Use the following command to create the file and then copy and paste the above contents into it:
```
gksudo gedit /usr/share/X11/xorg.conf.d/50-aiptek.conf
```
Then reboot.

---

### Post by wishingstar on 2011-07-26
Thanks Favux for the config script. I have two questions:

1- Within the script I can't find anything pertaining to delay, is that automatically configured when I use this config file?

2- Do I keep the evdev config file? or should I delete it for this to work?

Thanks

---

### Post by Favux on 2011-07-26
It should be automatically configured by the aiptek.conf.  I think the lag is because the evdev drive doesn't work right for your tablet.

You want to keep the evdev.conf.  That is also for mice, etc.

Because the aiptek.conf runs after the evdev.conf it should control your tablet.  Whatever runs last controls.

---

### Post by wishingstar on 2011-07-26
Thanks for the quick reply.

So as long as i give the config file i create a higher number than the evdev.conf, i'm set right?
I'll try that as soon as I'm off work today, and i'll let you know how it turns out :)

Thanks

---

### Post by wishingstar on 2011-07-26
> **Favux said:**
> You could check by entering in a terminal:
```
xinput list-props "Aiptek"
```


Here's the output:
```
Device 'Aiptek':
        Device Enabled (139):   1
        Coordinate Transformation Matrix (141): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (257):     0
        Device Accel Constant Deceleration (258):       1.000000
        Device Accel Adaptive Deceleration (259):       1.000000
        Device Accel Velocity Scaling (260):    10.000000
        Evdev Axis Inversion (261):     0, 0
        Evdev Axis Calibration (262):   <no items>
        Evdev Axes Swap (263):  0
        Axis Labels (264):      "Abs X" (614), "Abs Y" (615), "Abs Wheel" (616), "Abs Pressure" (617), "Abs Tilt X" (618), "Abs Tilt Y" (619), "Abs Misc" (620)
        Button Labels (265):    "Button Left" (142), "Button Middle" (143), "Button Right" (144), "Button Wheel Up" (145), "Button Wheel Down" (146), "Button Horiz Wheel Left" (147), "Button Horiz Wheel Right" (148)
        Evdev Middle Button Emulation (266):    0
        Evdev Middle Button Timeout (267):      50
        Evdev Wheel Emulation (268):    0
        Evdev Wheel Emulation Axes (269):       0, 0, 4, 5
        Evdev Wheel Emulation Inertia (270):    10
        Evdev Wheel Emulation Timeout (271):    200
        Evdev Wheel Emulation Button (272):     4
        Evdev Drag Lock Buttons (273):  0

```

I created the file with the contents you gave me, but with no change on delays after reboot! The list props command gives the following output now:

```
Device 'Aiptek':
        Device Enabled (139):   1
        Coordinate Transformation Matrix (141): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (257):     0
        Device Accel Constant Deceleration (258):       1.000000
        Device Accel Adaptive Deceleration (259):       1.000000
        Device Accel Velocity Scaling (260):    10.000000

```

Any thoughts?

---

### Post by Favux on 2011-07-26
Well you've gone from the evdev driver to now what appears to be the Aiptek driver so that's good.

Have you checked in Gimp if you now have pressure after configuring the extended input devices?  Does the lag still persist after things are configured?

Could you describe the lag a bit more?  We can try to adjust some of the Accel parameters.

---

### Post by wishingstar on 2011-07-27
I mainly use krita and not gimp. but when I installed/configured gimp to use extended devices (aiptek), I have a much worse lag now. Here's what happens now:

In GIMP: VERY slow performance. I draw a line, have to actually increase the pressure before I can get anything to show on screen. when it does, it's like a slow motion movie while it is drawing that single line. If there is more than one line drawn quickly after one another, only the first one is actually shown on screen. I did not play with the Accel parameters because I wouldn't know if I was making things better or worse.

In Krita: Still slow response to quick strokes, some are drawn (usually after some delay) while others are completely ignored. if I draw slow, i get better performance but with no pressure sensitivity. (no pressure sensitivity in krita whether i draw fast or slow)

---

### Post by Favux on 2011-07-27
Well in Gimp there has been a long standing GTK bug where the CPU usage goes through the roof causing a lag.  I thought that only affected Wacom tablets.  With a Wacom you would change your RawSample rate which cuts down the CPU load.  You could monitor your CPU usage and see if it is going up when the lag appears.  The Gimp dev.s have been slowly addressing it because apparently the gnome folks weren't too interested in fixing it.

I also vaguely recall seeing something about a long standing QT bug in Krita that caused no pressure.  But I thought that had been recently fixed.  Don't remember anything about a lag.

Again, how many pressure levels is your tablet suppose to have?

I've only used the Accel parameters to slow down an over accelerated input tool.  Let's see if we can go the other way with it and increase speed.  If it is a CPU utilization bug not sure whether this will cut down the incoming data points that need processing, which is what you would need.  Let's try a 20% decrease from the defaults and see what happens:
```
xinput set-prop "Aiptek" --type=float "Device Accel Constant Deceleration" 0.800000
xinput set-prop "Aiptek" --type=float "Device Accel Adaptive Deceleration" 0.800000
xinput set-prop "Aiptek" --type=float "Device Accel Velocity Scaling" 8.000000
```
Just run the commands in a terminal and they should apply right away.  Run them with Gimp or Krita closed.  The "Device Accel Constant Deceleration" is probably the most important one.

---

### Post by wishingstar on 2011-07-28
Thanks for the suggestions.
 
> **Favux said:**
> Again, how many pressure levels is your tablet suppose to have?

My tablet should have 512 pressure levels, that works perfectly in xp/win7 but not in linux.

The commands do not work for some reason, after running the first one in a terminal, here's what I get:
```
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  141 (XInputExtension)
  Minor opcode of failed request:  57 ()
  Value in failed request:  0x101
  Serial number of failed request:  18
  Current serial number in output stream:  19

```Which you said is the most important one.

As for CPU load in GIMP, it starts at 4% and goes up to about 8 or 9% when I'm doing quick strokes, misses most of them and comes back down to 4%.

---

### Post by wishingstar on 2011-07-29
Bump...

---

### Post by wishingstar on 2011-08-02
Any ideas?

---

### Post by Favux on 2011-08-02
> Any ideas? 
Nope.

I installed Kubuntu 11.04 and Gimp and Krita.  There is a huge lag in Gimp that I could probably address with adjusting RawSample.  With Krita my Wacom Bamboo doesn't even show up.  I can draw with the mouse but not the tablet.  I guess the older version had an extended input device thing like Gimp and Inkscape but this version is just suppose to recognize the tablet?

So anyway I get the impression there are some problems in Kubuntu so I did a quick google and got this:  [http://www.valdyas.org/fading/index.cgi/2011/05/04](http://www.valdyas.org/fading/index.cgi/2011/05/04)  Needless to say I'm pretty sure the distro that patches QT for multitouch they are complaining about is almost certainly Ubunutu/Kubuntu.  So oops.

We need to search launchpad but already came up with this one:  [https://bugs.launchpad.net/ubuntu/+source/koffice2/+bug/762938](https://bugs.launchpad.net/ubuntu/+source/koffice2/+bug/762938)  Notice the guy at the end isn't getting his Wacom tablet to do anything in Oneiric either.  Ouch.

---

### Post by Favux on 2011-08-02
Pencil, Inkscape, and MyPaint seem fine for what it is worth.

---

### Post by EkuquoL on 2011-08-02
You could see if INKscape would recognize the drawing pad... It is a graphic program.

You could... attempt to not use your mouse and see if the tablet would be recognized as a mouse.
Try using netbook mouse drivers for that ;)

Here is some sites that you could look for applications / drivers at -- Try using the manufacturer's name.
Freedesktop.org < A part of the X.org foundation
gnu.org < Part of the gnome foundation
gnome.org < Gnome

---

### Post by wishingstar on 2011-08-04
I just tried Pencil and MyPaint. Pencil works fine, there's a little lag in MyPaint but I guess that could be attributed to a VM using up lots of RAM. (I usually test with VM's off, but I couldn't this time).
I guess we'll just have to hope Qt gets patched to remove this delay in Krita.

---

### Post by Atomicity on 2011-08-04
I think the delay is an issue with the programs. I have the same problem (half of my strokes aren't showing up) only in GIMP and I'm using an Intuos4 with correct drivers. I thought the issue was caused by a possible conflict with the mouse so I tried unplugging it, but the problem persisted.

---

### Post by Favux on 2011-08-04
Hi Atomicity,

The lag in Gimp used to be due to a gtk bug causing excessive CPU demand.  I'm not so sure that's what's going on in Natty.  If you're in Natty using Unity try switching to Classic mode first (option at the bottom of the log in screen).

Almost by definition if adjusting RawSample up from the default 4 fixes it then its the gtk bug.  So try increasing RawSample.  Check *man xsetwacom* in a terminal for a little more background.
```
xsetwacom set "device name" RawSample 6
```
Then try maybe 8 and 10 etc.  Goes to 20 but you'll probably have other problems if you go much over 10.  Where you get the stylus "device name" from *xinput list*.

---

### Post by Atomicity on 2011-08-04
Nope, doesn't seem to change a thing. It's not a conventional slowdown lag thought, the cursor just remains stuck at the end of the first stroke and refuses to follow my pen to the other stroke. Thanks for the quick reply though.

---

### Post by Favux on 2011-08-04
Hi Atomicity,

It looks like the same issue they're talking about on this thread:  [http://ubuntuforums.org/showthread.php?t=1755492](http://ubuntuforums.org/showthread.php?t=1755492)

At least one person said going to Classic fixed it for them.

---

### Post by wishingstar on 2011-08-09
Hi,

I just found this thread on ubuntuforums:

[http://ubuntuforums.org/showthread.php?t=1653450](http://ubuntuforums.org/showthread.php?t=1653450)

They managed to make their tablet work with PS CS5 and Virtualbox. The only thing required, according to the guys who tried it, is to configure the tablet correctly under ubuntu (in terms of absolute x and y coordinates and pressure levels).

Does anyone know the correct configuration settings that I need to input to make my tablet work? Here are the settings:

Screen Resolution: 1280x800
Tablet: Aiptek with 1024 pressure levels (I got a new one after I spilled coffee on the old one :oops: )
I think I need to use the same driver that Favux indicated for me, all I need is to figure out the changes I have to make to the contents of the file.

Help is appreciated :)

---

### Post by Favux on 2011-08-09
Hi wishingstar,

For 1024 pressure levels you just change the aiptek.conf, from post #9, zMax from 511 to 1023:
```
Section "InputClass"
        Identifier "Aiptek class"
        MatchProduct "Aiptek|AIPTEK|aiptek"
        MatchDevicePath "/dev/input/event*"
        Driver "aiptek"
        Option "USB" "on"
        Option "Type" "stylus"
        Option "Mode" "absolute"
        Option "zMin" "0"
        Option "zMax" "1023"
EndSection
```
Since 0 is counted 1024 pressure levels is 0 to 1023.

By the way you can also create a pressure threshold by changing the zMin from say "0" to "3" if it is too sensitive at 0.

Let's see if we can find the coordinates.  They might be in Xorg.0.log in /var/log.  If *xinput list* still returns Aiptek for the tablet stylus let's first see if we can find them in list-props:
```
xinput list-props "Aiptek"
```
Getting the coordinates either way depends on if the driver is notifying the system about them.

---

### Post by wishingstar on 2011-08-11
Hello Favux,

Sorry for not getting back to you sooner, but I had a major system crash  and had to format my computer and reinstall everything. Now that I have  everything set up. I just ran the commands you suggested. After setting up the new aiptek.conf file with 0-1023 pressure levels, I restarted my computer and ran:

```
xinput list-props "Aiptek"
```

which returned:

```
Device 'Aiptek':
        Device Enabled (139):   1
        Coordinate Transformation Matrix (141): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (257):     0
        Device Accel Constant Deceleration (258):       1.000000
        Device Accel Adaptive Deceleration (259):       1.000000
        Device Accel Velocity Scaling (260):    10.000000
```

This obviously does not contain the coordinates needed. Pressure is working great with Zmin set to 0 (it's not too sensitive), but then again, I still haven't used any pressure-sensitive applications.

The Xorg.0.log file is HUGE! I tried a simple search for aiptek, I got the following lines:

```
22.620] (II) config/udev: Adding input device Aiptek (/dev/input/mouse2)
[    22.620] (II) No input driver/identifier specified (ignoring)
[    22.624] (II) config/udev: Adding input device Aiptek (/dev/input/event8)
[    22.624] (**) Aiptek: Applying InputClass "evdev pointer catchall"
[    22.625] (**) Aiptek: Applying InputClass "evdev keyboard catchall"
[    22.625] (**) Aiptek: Applying InputClass "evdev tablet catchall"
[    22.625] (**) Aiptek: Applying InputClass "Aiptek class"
[    22.625] (II) LoadModule: "aiptek"
[    22.625] (II) Loading /usr/lib/xorg/modules/input/aiptek_drv.so
[    22.672] (II) Module aiptek: vendor="X.Org Foundation"
[    22.672]     compiled for 1.9.99.902, module version = 1.3.99
[    22.672]     Module class: X.Org XInput Driver
[    22.672]     ABI class: X.Org XInput driver, version 12.3
[    22.673] (II) Using input driver 'aiptek' for 'Aiptek'
[    22.673] (II) Loading /usr/lib/xorg/modules/input/aiptek_drv.so
[    22.673] (**) Aiptek: always reports core events
[    22.673] (II) xf86AiptekInit(): begins
[    22.673] (**) xf86AiptekConfig: device not shared btw Aiptek and Power Button
[    22.673] (**) xf86AiptekConfig: device not shared btw Aiptek and Video Bus
[    22.673] (**) xf86AiptekConfig: device not shared btw Aiptek and Power Button
[    22.673] (**) xf86AiptekConfig: device not shared btw Aiptek and  USB OPTICAL MOUSE
[    22.673] (**) xf86AiptekConfig: device not shared btw Aiptek and AT Translated Set 2 keyboard
[    22.673] (**) xf86AiptekConfig: device not shared btw Aiptek and SynPS/2 Synaptics TouchPad
[    22.673] (**) xf86AiptekConfig: device not shared btw Aiptek and Aiptek
[    22.673] (**) Aiptek: always reports core events
[    22.673] (**) Option "Device" "/dev/input/event8"
[    22.688] (--) HID Device name: "Aiptek"
[    22.688] (--) HID Driver Version: 1.0.1
[    22.688] (--) HID Driver knows it has 1 devices configured
[    22.688] (--) HID Driver is using 21 as the fd
[    22.688] (EE) From ioctl() xCapacity=11999
[    22.688] (EE) From ioctl() yCapacity=8999
[    22.712] (**) Aiptek device is /dev/input/event8
[    22.712] (**) Aiptek is in absolute mode
[    22.712] (**) Option "USB" "on"
[    22.712] (**) Aiptek: reading USB link
[    22.712] (**) Option "ZMax" "1023"
[    22.712] (**) Aiptek: ZMax/MaxZ = 1023
[    22.712] (**) Option "ZMin" "0"
[    22.712] (**) Aiptek: ZMin/MinZ = 0
[    22.712] (**) Option "BaudRate" "9600"
[    22.712] (**) Aiptek: BaudRate 9600
[    22.712] (**) Aiptek: xf86AiptekInit() finished
[    22.712] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.0/input/input8/event8"
[    22.712] (II) XINPUT: Adding extended input device "Aiptek" (type: Stylus)
[    22.712] (**) xTop invalid; adjusted to 0
[    22.712] (**) yTop invalid; adjusted to 0
[    22.712] (**) xBottom invalid; adjusted to 11999
[    22.712] (**) yBottom invalid; adjusted to 8999
[    22.712] (**) ScreenNo invalid; adjusted to 0
[    22.712] (**) Aiptek: (accel) keeping acceleration scheme 1
[    22.712] (**) Aiptek: (accel) acceleration profile 0
[    22.712] (**) Aiptek: (accel) acceleration factor: 2.000
[    22.712] (**) Aiptek: (accel) acceleration threshold: 4
[    22.724] (--) HID Device name: "Aiptek"
[    22.724] (--) HID Driver Version: 1.0.1
[    22.724] (--) HID Driver knows it has 1 devices configured
[    22.724] (--) HID Driver is using 21 as the fd
[    22.724] (EE) From ioctl() xCapacity=11999
[    22.724] (EE) From ioctl() yCapacity=8999
[    22.724] (EE) Able to open aiptek device
```

Are the X and Y coordinates 11999 and 8999? (from the last three lines). I'm not sure how to read this log file ](*,)

Thank you for all the great ideas and advice, I really feel we're getting close to a solution. BTW the new tablet has the same lag in krita, but GIMP works much better: there's still a lag, but it's less noticeable than before, and pressure works, so that's a definite improvement. I just need to get the tablet to work with Virtualbox, and then I'm a happy camper :D

---

### Post by Favux on 2011-08-11
> BTW the new tablet has the same lag in krita, but GIMP works much better: there's still a lag, but it's less noticeable than before, and pressure works, so that's a definite improvement.
Good, progress!
> Are the X and Y coordinates 11999 and 8999?
That sure seems to be what it is telling us with:
```
[    22.688] (EE) From ioctl() xCapacity=11999
[    22.688] (EE) From ioctl() yCapacity=8999

[    22.712] (**) xTop invalid; adjusted to 0
[    22.712] (**) yTop invalid; adjusted to 0
[    22.712] (**) xBottom invalid; adjusted to 11999
[    22.712] (**) yBottom invalid; adjusted to 8999
```
It's not telling us what syntax to use for coordinates, but I'll take a guess:
```
Section "InputClass"
        Identifier "Aiptek class"
        MatchProduct "Aiptek|AIPTEK|aiptek"
        MatchDevicePath "/dev/input/event*"
        Driver "aiptek"
        Option "USB" "on"
        Option "Type" "stylus"
        Option "Mode" "absolute"
        Option "zMin" "0"
        Option "zMax" "1023"
        Option "TopX"    "0"
        Option "TopY"    "0"
        Option "BottomX" "11999"
        Option "BottomY" "8999"
EndSection
```
If that syntax works, in Natty xinput_calibrator is in the Universe repository as xinput-calibrator.  You should be able to use it to refine your coordinates if needed.

---

### Post by wishingstar on 2011-08-11
Thanks for the quick response!

I just edited the aiptek.conf file to reflect your changes. However, when I plugged in the tablet to try and test it, my session immediately gave an error (the terminal-like screen disappeared quickly but the last line seemed to have something to do with ALSA) and my session simply restarted, no crash messages, no "pick-up from where you left off". I had to restart all my open programs one by one and I lost all my unsaved work. 

After that I plugged it in again, did a small test using GIMP (same performance as before, so they seem to be the right coordinates), but when I disconnected the tablet I got the same error screen and a resetting of my session.

Any ideas?

---

### Post by Favux on 2011-08-11
Not really.  Assuming they're the right coordinates as Gimp seems to indicate maybe I have the syntax wrong?  You can check the coordinates with xinput-calibrator.

In /var/log does Xorg.0.log or Xorg.0.log.old have anything on the crash?  That would be a big help.  ALSA is the Advanced Linux Sound Architecture.  So that doesn't sound very related or helpful.

And you were able to hotplug without the coordinates?

---

### Post by wishingstar on 2011-08-12
Hello,

As I'm currently working on a project and can't afford to have my session reset without warning, I'm hesitant to plug the tablet in again and do more testing.

As for being able to use the tablet without entering the 8999 and 11999 coordinates, the answer is yes, no difference in performance between before and after we added those coordinates to the configuration file.

I did some digging in the two logs you mentioned. The latest had nothing but the second had the following - possible relevant - lines:

```
[    22.712] (II) XINPUT: Adding extended input device "Aiptek" (type: Stylus)
[    22.712] (**) xTop invalid; adjusted to 0
[    22.712] (**) yTop invalid; adjusted to 0
[    22.712] (**) xBottom invalid; adjusted to 11999
[    22.712] (**) yBottom invalid; adjusted to 8999
[    22.712] (**) ScreenNo invalid; adjusted to 0
[    22.712] (**) Aiptek: (accel) keeping acceleration scheme 1
[    22.712] (**) Aiptek: (accel) acceleration profile 0
[    22.712] (**) Aiptek: (accel) acceleration factor: 2.000
[    22.712] (**) Aiptek: (accel) acceleration threshold: 4
[    22.724] (--) HID Device name: "Aiptek"
[    22.724] (--) HID Driver Version: 1.0.1
[    22.724] (--) HID Driver knows it has 1 devices configured
[    22.724] (--) HID Driver is using 21 as the fd
[    22.724] (EE) From ioctl() xCapacity=11999
[    22.724] (EE) From ioctl() yCapacity=8999
[    22.724] (EE) Able to open aiptek device
[   230.036] (II) RADEON(0): EDID vendor "LPL", prod id 56320
[   230.036] (II) RADEON(0): Printing DDC gathered Modelines:
[   230.036] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[   251.980] (II) RADEON(0): EDID vendor "LPL", prod id 56320
[   251.980] (II) RADEON(0): Printing DDC gathered Modelines:
[   251.980] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[   283.900] (II) XKB: reuse xkmfile /var/lib/xkb/server-9A8405F3FE0A780485714A4B6DD41909C2CF9F83.xkm
[  3519.652] (II) XKB: reuse xkmfile /var/lib/xkb/server-9A8405F3FE0A780485714A4B6DD41909C2CF9F83.xkm
[  5881.368] (EE) Error reading Aiptek tablet: No such device
[  5881.371] (II) config/udev: removing device Aiptek
[  5881.385] 
Backtrace:
[  5881.385] 0: /usr/bin/X (xorg_backtrace+0x3b) [0x80eab8b]
[  5881.386] 1: /usr/bin/X (0x8048000+0x5fb38) [0x80a7b38]
[  5881.386] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb784a40c]
[  5881.386] 3: /usr/bin/X (xf86RemoveEnabledDevice+0x34) [0x80b3844]
[  5881.386] 4: /usr/lib/xorg/modules/input/aiptek_drv.so (0xb6b02000+0x1df5) [0xb6b03df5]
[  5881.386] 5: /usr/lib/xorg/modules/input/aiptek_drv.so (0xb6b02000+0x21a3) [0xb6b041a3]
[  5881.387] 6: /usr/bin/X (DeleteInputDeviceRequest+0x6b) [0x80c498b]
[  5881.387] 7: /usr/bin/X (0x8048000+0x8417f) [0x80cc17f]
[  5881.387] 8: /usr/bin/X (0x8048000+0x84239) [0x80cc239]
[  5881.388] 9: /usr/bin/X (0x8048000+0x84435) [0x80cc435]
[  5881.388] 10: /usr/bin/X (0x8048000+0x84ff2) [0x80ccff2]
[  5881.388] 11: /usr/bin/X (WakeupHandler+0x52) [0x8074602]
[  5881.388] 12: /usr/bin/X (WaitForSomething+0x1ba) [0x80a1faa]
[  5881.388] 13: /usr/bin/X (0x8048000+0x27f1e) [0x806ff1e]
[  5881.388] 14: /usr/bin/X (0x8048000+0x1a81c) [0x806281c]
[  5881.388] 15: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xe7) [0xb7559e37]
[  5881.389] 16: /usr/bin/X (0x8048000+0x1a411) [0x8062411]
[  5881.389] Segmentation fault at address 0x9643d4c
[  5881.389] 
Caught signal 11 (Segmentation fault). Server aborting
[  5881.389] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[  5881.389] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  5881.389] 
[  5881.424] (II) Power Button: Close
[  5881.425] (II) UnloadModule: "evdev"
[  5881.425] (II) Unloading evdev
[  5881.444] (II) Video Bus: Close
[  5881.445] (II) UnloadModule: "evdev"
[  5881.445] (II) Unloading evdev
[  5881.446] (II) Power Button: Close
[  5881.446] (II) UnloadModule: "evdev"
[  5881.446] (II) Unloading evdev
[  5881.449] (II)  USB OPTICAL MOUSE: Close
[  5881.449] (II) UnloadModule: "evdev"
[  5881.449] (II) Unloading evdev
[  5881.456] (II) AT Translated Set 2 keyboard: Close
[  5881.456] (II) UnloadModule: "evdev"
[  5881.456] (II) Unloading evdev
[  5881.462] (II) UnloadModule: "synaptics"
[  5881.462] (II) Unloading synaptics
[  5881.463] (II) AIGLX: Suspending AIGLX clients for VT switch
[  5881.477]  ddxSigGiveUp: Closing log

```

Hope this helps you pinpoint the issue with the random sudden crashes.

Thanks for the help.

---

### Post by Favux on 2011-08-12
Thanks for including the backtrace that helps.  Looks like it is the Aiptek driver causing the problems.

Your first Xorg.0.log showed the Aiptek driver grumbling about the coordinates being invalid and having to fix them.  Does it still do it with you supplying the coordinates?

It looks like usually the "signal 11 (Segmentation fault)" is from video drivers:  [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/740785](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/740785)  I'm not clear if it is because the drivers don't handle things correctly or the maybe the X server made an API change that folks aren't aware of yet.  If that's the problem once the "documentation' of the change spreads they'll get fixed.

I don't know why adding coordinates breaks things but it seems like if you do that you won't be able to hotplug.  Of course, again, we could be doing something wrong with the way we're adding the coordinates.  I'm just not sure what.

The Aiptek site doesn't seem real active:  [http://aiptektablet.sourceforge.net/](http://aiptektablet.sourceforge.net/)  and  [http://sourceforge.net/projects/aiptektablet/](http://sourceforge.net/projects/aiptektablet/)  But you could try asking questions there.

---

### Post by Favux on 2011-08-12
Hmmm.  Maybe it's the Aiptek usb driver/module in the kernel, aiptek.ko.

There was a recent fix to the kernel's linux-input list because the Pen was defined twice so they removed the second definition:  [https://patchwork.kernel.org/patch/962722/](https://patchwork.kernel.org/patch/962722/)  Not sure but maybe.

---

### Post by wishingstar on 2011-08-12
The Aiptek driver no longer seems to be complaining about the coordinates, it just accepts the ones in the config file. Also, if i remember correctly, there was at least one instance of this crash BEFORE I entered the coordinates into the config file! And it also seems to happen (the crash that is) as soon as I UNPLUG the tablet (I just tried again, and the crash happened when I removed the USB connector)

Also, if things seem to be set up correctly, is it possible for me to start working on connecting the tablet through Virtualbox? I can leave the tablet connected full time (for now) until I find a solution.

---

### Post by Favux on 2011-08-12
> if i remember correctly, there was at least one instance of this crash BEFORE I entered the coordinates into the config file! And it also seems to happen (the crash that is) as soon as I UNPLUG the tablet (I just tried again, and the crash happened when I removed the USB connector)

Ah!  That sounds like the Aiptek driver doesn't handle a termination (usb disconnect) correctly.  That is worth a bug report on the Aiptek site.
> The Aiptek driver no longer seems to be complaining about the coordinates, it just accepts the ones in the config file.
Alright, it sounds like we have the coordinates and syntax correct!  :)
> is it possible for me to start working on connecting the tablet through Virtualbox?
I don't see why not.

---

### Post by wishingstar on 2011-08-12
I will post a bug report to the Aiptek website. Thanks for all the help Favux. I'm marking this thread as solved for now, let's hope the Aiptek driver devs fix the termination problem soon :)

Thanks again.

---

### Post by wishingstar on 2011-09-10
Hi All, I know i marked this as solved about a month ago, but now it's doubly solved. I managed to avert X crashing every time I unplug the tablet by following the instructions on this page:

[http://cocoknight.com/g-pen-560-on-jaunty/](http://cocoknight.com/g-pen-560-on-jaunty/)

Basically, all I had to do is create the file /lib/udev/rules.d/69-xserver-xorg-input-aiptek.rules

and put the following inside:
```
ACTION!="add|change", GOTO="xorg_aiptek_end"
KERNEL!="event[0-9]*", GOTO="xorg_aiptek_end"
ATTRS{idVendor}=="08ca", ENV{x11_driver}="aiptek", SYMLINK+="input/aiptektablet"
LABEL="xorg_aiptek_end"
```

Then restart, X no longer crashes when the tablet is unplugged. And when I disabled mouse pointer integration and absolute pointing device in virtualbox, I was able to fully use the tablet inside VM's.

Good luck to all :)

Edit: it does still crash occasionally, but at least it's not EVERY TIME like before

---

