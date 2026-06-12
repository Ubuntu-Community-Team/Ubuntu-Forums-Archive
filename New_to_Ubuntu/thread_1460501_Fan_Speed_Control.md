---
title: "Fan Speed Control"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by tharman on 2010-04-22
I'm still fairly new to Ubuntu. I've dabbled with it for personal and work use. Recently I decided to install it on my desktop and get rid of Vista. 

When I was using Windows I had a fan control utility that allowed me to set the speed of my fan to work with my CPU so that when the load on it was low the fan was quieter. Now that I can't use this utility my fan is constantly running at top speed.

I was wondering how I could go about getting this to work. I've tried some stuff using lm-sensors but I always seem to get stuck somewhere. This is the output I get from sensors:

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +51.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +49.0°C  (high = +80.0°C, crit = +100.0°C)  

It looks a lot different from the output in this tutorial I was looking at here: [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

I've also tried looking here: [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)
but I'm not sure how to check if powersaved is in the autostart process. (Also cat /proc/acpi/thermal_zone/*/trip_points gives me a "No such file or directory" error.) 

I guess I was just hoping there was a utility I could use to do this easily or someone could point me where to go to try setting my fan to run comparative to my CPU. 

Any help is appreciated. :)

---

### Post by tharman on 2010-04-22
I figured out that I could turn the fan speed down by choosing a silent profile in my BOIS but I'm worried this might cause my CPU to overheat as the fan doesn't seem to speed up when I put more load on the CPU. Is it possible I'm not able to control the fan speed except through the BIOS?

---

### Post by appier on 2010-04-22
Can you give us a little more information about your computer and its configuration?  I have had this same trouble as you, but it was a number of years ago on an HP a305w--the fan sounded like it was getting ready to take off at any time.  In the case of that computer, the problem apparently was with the BIOS, and I relegated it as my computer in my classroom at school and Windows XP.  Having said that, Ubuntu has been running on a number of different donated machines at school, and none of them have the fan problem.

---

### Post by tharman on 2010-04-22
Basically its an ASUS P5QL Pro motherboard with a 3GHz Intel CPU. 2x2GB of RAM and 2TB of HDD storage.

Here's some more detailed info from lshw.

*-cpu  product: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz


*-display UNCLAIMED
                description: VGA compatible controller
                product: RV770 [Radeon HD 4850]


Not overly sure how to get more info.

EDIT: I've been a Windows user forever so getting hardware specs without device manager is new to me :P . I threw away most of my computer part packaging cause its a little old now.

---

### Post by appier on 2010-04-22
OK, this is a bit more modern than the equipment I am used to.  However, there should be someone here that can help you.  Have you checked the hardware compatibility lists?

---

### Post by tharman on 2010-04-22
Says it works fine according to [https://wiki.ubuntu.com/Asus_P5QL_Pro](https://wiki.ubuntu.com/Asus_P5QL_Pro)

I'm sure its a configurable setting somewhere, I'm just not experienced enough to know where to find or configure it. Everything else seems to be working fine (except the sound in my Fusion Genesis emulator :P )

---

### Post by 2hot6ft2 on 2010-04-22
First those 2 links in the first post are from 2004.
I wouldn't suggest following them, a lot has changed.

Mine doesn't have the fan speed control since it's controlled by the BIOS but I looked thru Synaptic and found Digitools for the ASUS. It's included below.
Here's a short version of installing them and it's current:
Just open a Terminal (Applications -> Accessories -> Terminal) and type (or copy and paste):

```
sudo apt-get install lm-sensors sensors-applet hddtemp digitools
```

Next, run sensors-detect. Answer y to each one until finished.
```
sudo sensors-detect
```

Now you can also run
```
sudo hddtemp /dev/sda
```
Where sda is your hard drive.
and it will show the temperature of your hard drive if it can.

All temps. are in Celsius by default, but you can change it to F or Kelvin if you want.

adding hdd temp to sensors-applet
> **dcstar said:**
> ```
gksudo gedit /etc/default/hddtemp
```

Make RUN_DAEMON="true"
Save and close
Finally, restart to load all the sensors.
Once back at the desktop, right-click on the top panel and choose "Add to Panel.
Select "Hardware Sensors Monitor" and click the "Add" button, then "Close".

Right-click on all the sensors applet that appears on the top panel and choose "Preferences".
Click the "Sensors" tab. There you can select/de-select all the relevant sensors and adjust their low and high values as well as set alarms if desired.

Digitools info from synaptic
```

**A set of tools to control ASUS Digimatrix embedded hardware**

This package is a combination of the previous programs asusfan and setpanel.
Included in this package are the following tools:
[B]  digifan:   allows fan speed control
             (formerly asusfan)
[/B]
  digipanel: allows control of the LED display, and volume knob controls
             the soundcard master mixer channel
             (formerly part of setpanel)

  digiradio: allows control of the in-built radio
             (formerly part of setpanel)

  digiwake:  allows for Wake-On-CIR (wake on remote) with existing
             versions of LIRC that support the digimatrix. This program
             just needs to be run after lircd, and the digimatrix will
             power on when pressing the music/(on/off) button on the
             remote control.

```

Sorry I don't know how to setup digitools but **if** there's no menu item for them you can always try.
```
man digitools
**man digifan**
man digipanel
man digiradio
man digiwake
```
To read the manuals for them. Use "q" that's the letter "Q" to exit the manual and be back in the terminal.

---

### Post by 3rdalbum on 2010-04-23
The Silent profile is perfectly safe to use on your system, the Asus motherboards are very good at controlling fan speed.

---

### Post by tharman on 2010-04-23
Well I suppose I will just go with the Silent Mode form my BIOS. 

On a sidenote though when I type:
```
sudo apt-get install lm-sensors sensors-applet hddtemp digitools
```

I get:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lm-sensors is already the newest version.
E: Couldn't find package digitools

```

Thanks for all the help though. I'm really starting to enjoy my Ubuntu experience.

:D

---

### Post by 3rdalbum on 2010-04-23
Even better yet, you could install one of the quieter aftermarket CPU coolers; I use Noctua's coolers. With the Noctua models you can actually turn off fan control and still barely be able to hear the fan, plus you can overclock.

They're not the absolute easiest things to install (unless your case has a cutout on the right-hand side, you need to take the motherboard out!) but the instructions provided are clear and supported with illustrations.

No I don't work for Noctua, I just like that my computer is both silent AND fast :-)

---

### Post by csaket on 2010-04-23
It could also be the video drivers.
I have issues with my ATI 3650 if I use the open source drivers and if I use the proprietary fglrx then the fans throttle down under low usage.

---

### Post by 2hot6ft2 on 2010-04-23
> **tharman said:**
> 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lm-sensors is already the newest version.
**E: Couldn't find package digitools**

```

Thanks for all the help though. I'm really starting to enjoy my Ubuntu experience.

:D
That's probably because I use UUE (Ubuntu Ultimate Edition) so I have things that others don't. I tried.

---

### Post by no2498 on 2010-04-23
open a terminal type top or htop or you can run both
it tells you how to install

after installed type top or htop
see what is running to make the fan run fast

do this before you change any fan speeds 
the system should run the fan not you

look for the problem not a quick fix

---

