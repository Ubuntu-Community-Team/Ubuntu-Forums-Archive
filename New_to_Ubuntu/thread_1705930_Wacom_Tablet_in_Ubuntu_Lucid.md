---
title: "Wacom Tablet in Ubuntu Lucid"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by tinyyuki on 2011-03-13
Hello, everyone.

I'm generally not a very good computer person, but my dad is a computer genius, and he can't even figure out why my tablet isn't working. I have a Bamboo Wacom Pen and I'm running Ubuntu Studio Lucid 10.04.

Here's my build environment:

```
BUILD ENVIRONMENT:
       architecture - i486-linux-gnu
       linux kernel - yes 
      kernel source - no 
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - no
           dlloader - yes
               XLib - yes /usr/lib
         xf86config - no
                TCL - yes /usr/include/tcl8.4
                 TK - yes /usr/include/tcl8.4
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - no
            wacdump - no 
             xidump - no 
        libwacomcfg - no
         libwacomxi - no
          xsetwacom - no
          wacomxrrd - no
              hid.o - no 
       wacom_drv.so - no /usr/lib/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks - hal IsXExtensionPointer key-events dixScreenOrigins
----------------------------------------
You can build the kernel driver from this package by
./configure --enable-wacom


NOTE: the X driver in this package only supports Xorg servers older than 1.7.
          You are running a newer version. 
Please build the X driver from xf86-input-wacom.
The kernel driver provided in this package is independent of 
the X server version

```

I've tried many a different code and I've looked online for anything to get the tablet to work, and it isn't. I'm trying to get the linux wacom 0.8.8-11 package to run. I've tried earlier packages, and it's still not working.The wacom.ko is not in the src folder for 2.6.30, and I've no idea where it is, actually. My computer does detect my tablet, but for anything I do, it will not detect the pen, and in Gimp it doesn't even show that there's a tablet. It's rather frustrating, and I'm seriously considering going back to windows, it's that frustrating. Any help is greatly appreciated.

Thanks in advance.

Yuki

---

### Post by Favux on 2011-03-13
Hi Yuki,

Welcome to Ubuntu forums!

The line:
```
wacom.o - no

```
Is telling you it won't build the wacom.ko.  Object v.s. kernel object.  Better if it said ko I know.

So what kernel does Studio have?
```
uname -r
```
And what flags are you using on the configure line?

---

### Post by tinyyuki on 2011-03-13
Okay, the kernel is 2.6.32-21-generic.

And what do you mean "flags?" I'm really hopeless at this... I'm so sorry. >.<

---

### Post by tinyyuki on 2011-03-13
maybe you mean ```
l/configure --enable-wacom
```

I'm not really sure... >.<

Here's what I've been using:

```
sudo apt-get install build-essential
sudo apt-get install libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev

cd ./Desktop
tarxvfj linuxwacom-0.8.8-11.tar.bz2
cd ./linuxwacom-0.8.8-11
./configure --enable-wacom

```

then this tutorial i found says to go into "cd ./src/2.6.30" then it says to 

```
sudo cp wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet
```

which doesn't seem to really work since.. there... isn't.. a kernel... o.o

---

### Post by Favux on 2011-03-13
For:
```
./configure --prefix=/usr

```
the flag is --prefix=/usr.  On some 64-bit installs you may need another flag.  See Troubleshooting near the bottom of the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

---

### Post by tinyyuki on 2011-03-13
Alright, my evdev_drv.so is in the  /usr/lib/xorg/modules/input, so I put in ```
./configure --enable-wacom --prefix=/usr --libdir=/usr/lib64
```

and I'm getting```
  BUILD ENVIRONMENT:
       architecture - i486-linux-gnu
       linux kernel - yes 
      kernel source - no 
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - no
           dlloader - yes
               XLib - yes /usr/lib
         xf86config - no
                TCL - yes /usr/include/tcl8.4
                 TK - yes /usr/include/tcl8.4
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - no
            wacdump - no 
             xidump - no 
        libwacomcfg - no
         libwacomxi - no
          xsetwacom - no
          wacomxrrd - no
              hid.o - no 
       wacom_drv.so - no /usr/lib/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks - hal IsXExtensionPointer key-events dixScreenOrigins
----------------------------------------
You can build the kernel driver from this package by
./configure --enable-wacom


NOTE: the X driver in this package only supports Xorg servers older than 1.7.
          You are running a newer version. 
Please build the X driver from xf86-input-wacom.
The kernel driver provided in this package is independent of 
the X server version

```

I feel like I'm doing something wrong.

---

### Post by Favux on 2011-03-13
If evdev_drv.so is in lib and not lib64 you don't need the --libdir=/usr/lib64 flag.

Until it says:
```
wacom.o - yes

```
under Build Options, something is wrong.  Are you getting errors in the configure output?  Usually it lists them before Build Environment.  For example the dependency/library line you are using doesn't seem complete for linuxwacom.  It should be:
```
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev tk8.4-dev tcl8.4-dev libncurses5-dev

```
You need build-essential &  libxrandr-dev too for example.

---

### Post by tinyyuki on 2011-03-13
This is the section before the Build

```
configure: creating ./config.status
config.status: creating Makefile
config.status: creating mkxincludes
config.status: creating src/Makefile
config.status: creating src/util/Makefile
config.status: creating src/xdrv/Makefile
config.status: creating src/2.6.16/Makefile
config.status: creating src/2.6.18/Makefile
config.status: creating src/2.6.24/Makefile
config.status: creating src/2.6.30/Makefile
config.status: creating src/wacomxi/Makefile
config.status: creating src/wacomxi/wacomcpl
config.status: creating src/include/xdrv-config.h
config.status: src/include/xdrv-config.h is unchanged
config.status: creating src/include/kernel-config.h
config.status: src/include/kernel-config.h is unchanged
config.status: creating src/include/util-config.h
config.status: src/include/util-config.h is unchanged
config.status: executing depfiles commands

```

---

### Post by tinyyuki on 2011-03-13
Oh gosh, really?

My update manager updated the generic kernel, and now wacom.o = yes.

However, it does detect my tablet, but the pen will only move if I have it pressed down, like I'm clicking. Any thoughts?

---

### Post by Favux on 2011-03-13
Hmmm.  Anyway...

Let's make sure your stylus is on the wacom driver.  Enter in a terminal:
```
xinput list
```
and find the stylus "device name".  Using the "device name" in quotes:
```
xinput list-props "device name"
```
A short cut would be to enter:
```
xsetwacom list
```
and see if the stylus is in the output.

---

### Post by tinyyuki on 2011-03-13
Alright here's what I got:

```
Device 'Wacom Bamboo 4x5 Pen':
	Device Enabled (146):	1
	Device Accel Profile (267):	0
	Device Accel Constant Deceleration (268):	1.000000
	Device Accel Adaptive Deceleration (270):	1.000000
	Device Accel Velocity Scaling (271):	10.000000
	Evdev Reopen Attempts (262):	10
	Evdev Axis Inversion (272):	0, 0
	Evdev Axis Calibration (273):	<no items>
	Evdev Axes Swap (274):	0
	Axis Labels (275):	"Abs X" (264), "Abs Y" (265), "Abs Pressure" (266), "None" (0)
	Button Labels (276):	"Button Unknown" (263), "Button Unknown" (263), "Button Unknown" (263), "Button Wheel Up" (150), "Button Wheel Down" (151), "Button Horiz Wheel Left" (152), "Button Horiz Wheel Right" (153)
	Evdev Middle Button Emulation (277):	2
	Evdev Middle Button Timeout (278):	50
	Evdev Wheel Emulation (279):	0
	Evdev Wheel Emulation Axes (280):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (281):	10
	Evdev Wheel Emulation Timeout (282):	200
	Evdev Wheel Emulation Button (283):	4
	Evdev Drag Lock Buttons (284):	0

```

---

### Post by Favux on 2011-03-13
Alright, it looks like you're in the final stretch!

As you can see your stylus is on the evdev X driver, not the Wacom driver.  It appears for some reason a recent Lucid update knocked the 10-wacom.conf in /usr/lib/X11/xorg.conf.d out.  Check there and see if you have one.  If you do post the contents.  If not create a 10-wacom.conf file by entering:
```
gksudo gedit /usr/lib/X11/xorg.conf.d/10-wacom.conf
```
in a terminal.  Then Copy and Paste the entire contents of the sample wacom.conf in part *III. Configure the Wacom Bamboo P&T tablet* under *a) Configuring through 10-wacom.conf (Lucid) or 50-wacom.conf (Maverick)*.  Save, Close, then reboot.

That should match to your tablet and place it on the Wacom X driver xf86-input-wacom.

---

### Post by tinyyuki on 2011-03-13
Oh my gosh, thank you so much!!! I works perfect, if not better than my laptop when I used it on that!!! You're amazing hahah! Thank you so much for putting up with my not computer-like mind... >.<

---

### Post by Favux on 2011-03-13
You're welcome.  Plus you've learned a lot now.

Remember when the kernel is updated it will seem to break the tablet.  That's because the updated kernel will have a new modules directory and that directory will have the default (non-working) wacom.ko (usb kernel driver/module) in it.  All you need to do is repeat part I., i.e. recompile a new wacom.ko against that kernel and copy (cp) it into place and reboot.  Then it will work again.  Kernel updates don't happen very often and you'll find you can do the compile again in a couple of minutes.  When Natty comes out in less than two months you shouldn't have to do anything.  It should work out of the box.

---

