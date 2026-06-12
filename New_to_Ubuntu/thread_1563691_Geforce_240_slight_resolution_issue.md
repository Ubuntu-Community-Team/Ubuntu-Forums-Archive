---
title: "Geforce 240 slight resolution issue"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by cchaos on 2010-08-29
More or less a little "niggle" I currently have with my monitor (Iiyama ProLite E430T (TFT)) which is it likes to use a 1024x768 resolution, rather than a 1280x1024.

I dont fully know if my Nvidia card will take 1280x1024 but my monitor certainly does.

My monitor is mentioned here: [http://ubuntuforums.org/showthread.php?t=1113062](http://ubuntuforums.org/showthread.php?t=1113062) and needless to say I have now upgraded my whole pc since making that thread, and my current graphics card is a PNY GeForce 240 1024Mb (though ubuntu 9.10 is detectiong it as a 230)

Previously, I was only getting a 800X600 resolution, but I managed to fix that by changing the values of the resolution in monitors.xml (which made the change complete) and Xorg.conf.

Mistakenly, I have tried sorting out this problem elsewhere. The person helping me wanted to be a little parrot, trying to give the same fix for anything connected to the monitor (ie edit xorg.conf, which I have done until Im blue in the face and without success)

To help you guys out as to what has been tried, am I allowed to place a link to that thread? If not then I will give it out in code boxes and the results

---

### Post by realzippy on 2010-08-29
Open a terminal:
```
sudo nvidia-bug-report.sh

```
creates a Nvidia/X log file in your home directory,can you post this ? 

It contains useful informations,xorg.conf included...

---

### Post by cchaos on 2010-08-29
> **realzippy said:**
> Open a terminal:
```
sudo nvidia-bug-report.sh

```
creates a Nvidia/X log file in your home directory,can you post this ? 

It contains useful informations,xorg.conf included...
Terminal said:

```
nvidia-bug-report.sh will now collect information about your
system and create the file 'nvidia-bug-report.log.gz' in the current
directory.  It may take several seconds to run.  In some
cases, it may hang trying to capture data generated dynamically
by the Linux kernel and/or the NVIDIA kernel module.  While
the bug report log file will be incomplete if this happens, it
may still contain enough data to diagnose your problem.

Please include the 'nvidia-bug-report.log.gz' log file when reporting
your bug via the nV News NVIDIA Linux forum (see www.nvnews.net)
or by sending email to 'linux-bugs@nvidia.com'.

Running nvidia-bug-report.sh... complete.
```
File created: attached.

Thanks for any help :)

---

### Post by realzippy on 2010-08-29
The driver cannot get the monitor's data (EDID).

[I](WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-1
(WW) NVIDIA(0): Unable to get display device CRT-1's EDID; [/I]

You are using the 185.xx driver on Ubuntu 9.10?

---

### Post by cchaos on 2010-08-29
> **realzippy said:**
> The driver cannot get the monitor's data (EDID).

[I](WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-1
(WW) NVIDIA(0): Unable to get display device CRT-1's EDID; [/I]

You are using the 185.xx driver on Ubuntu 9.10?
Yes. Ive included a screenshot.

So, how can I fix that then, or is it a case of "live with it"?

---

### Post by realzippy on 2010-08-29
Click on CRT1

Is there an option "Acquire EDID" on the right?

---

### Post by cchaos on 2010-08-29
No, there isnt.

---

### Post by realzippy on 2010-08-29
2 questions:

Ever tried newer driver?
Think I remember some fixed bugs according to EDID misreads with newer chips.

Is the file monitors.xml still existing?

---

### Post by cchaos on 2010-08-29
> **realzippy said:**
> 2 questions:

Ever tried newer driver?
Think I remember some fixed bugs according to EDID misreads with newer chips.

Is the file monitors.xml still existing?
If you mean [http://www.nvidia.co.uk/object/linux-display-ia32-256.44-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-256.44-driver-uk.html) I havent as it wants me to login in root to install it (which is not a solution as rot is disabled under 9.10 as far as Im aware)

Monitors.xml:

```
<monitors version="1">
&#8722;
<configuration>
<clone>no</clone>
<output name="VGA1">
      </output>
<output name="DVI0">
      </output>
&#8722;
<output name="VGA0">
<vendor>???</vendor>
<product>0x0000</product>
<serial>0x00000000</serial>
<width>1152</width>
<height>864</height>
<rate>60</rate>
<x>0</x>
<y>0</y>
<rotation>normal</rotation>
<reflect_x>no</reflect_x>
<reflect_y>no</reflect_y>
<primary>no</primary>
</output>
<output name="DVI1">
      </output>
</configuration>
</monitors>
```
But that is not what I set it at. I know I tried uninstallling and reinstalling the driver hoping to fix it, but to no avail

---

### Post by realzippy on 2010-08-29
Yes I mean this driver.No need to install it manually.Which driver is offered
in Systam/Administration/Hardware Drivers ?

*monitors.xml* is created when running System/Preferences/Monitors and "disturbs" *nvidia-settings*.Delete this file (or rename it if you want to keep it).
Then log out/in to restart X.

---

### Post by cchaos on 2010-08-29
Its just offering me the 185* one. Not the 256* driver.

ok, will delete that file then and hope for the best

---

### Post by realzippy on 2010-08-29
Deleting monitors.xml might but won't do it alone...
Generally 2 ideas to solve your problem:
1.Use newest driver by adding xswat ppa to your sources;might also help with
  recognizing your geforce 240 correctly;might solve EDID issue (that's your problem!)

2.Reconfigurating your xorg.conf (which is pretty vanilla and not made by nvidia    xconfig) and trying to configurate the monitor section.

Maybe both has to be made;which pill first?

---

### Post by cchaos on 2010-08-29
Just a sudden thought: will an install of 10.04 fix this do you think? or will it make it worse?

---

### Post by realzippy on 2010-08-29
> **cchaos said:**
> Just a sudden thought: will an install of 10.04 fix this do you think? or will it make it worse?

Can make new problems (which can be fixed also,,,)
:)


Edit:
The 2 solutions would take 4 minutes (if they work),a fresh install at least 20 ....

---

### Post by cchaos on 2010-08-29
> **realzippy said:**
> Deleting monitors.xml might but won' do it alone...
Generally 2 ideas to solve your problem:
1.Use newest driver by adding xswat ppa to your sources;might also help with
  recognizing your geforce 240 correctly;might solve EDID issue (that's your problem!)

2.Reconfigurating your xorg.conf (which is pretty vanilla and not made by nvidia    xconfig) and trying to configurate the monitor section.

Maybe both has to be made;which pill first?

I would go with the first pill; xorg.conf editing just doesnt get me anyway as described in this post: [http://www.linuxforums.org/forum/ubuntu-help/168488-resolution-problem-ubuntu-9-10-a-2.html#post800451](http://www.linuxforums.org/forum/ubuntu-help/168488-resolution-problem-ubuntu-9-10-a-2.html#post800451) and I ended up going back to my first topic here.

Though having said that, Im not 100% convinced that will work as well: I think that the monitor (and/or the VGA cable) I have is either kak or simply too old.

Anyway, I assume you want me to go to software sources, but what do I do after that?

---

### Post by cchaos on 2010-08-29
> **realzippy said:**
> Can make new problems (which can be fixed also,,,)
:)


Edit:
The 2 solutions would take 4 minutes (if they work),a fresh install at least 20 ....
Try longer than that: I would have to reinstall windows XP and 7, then install 10.04, then fix any issues with that. However, if its worth it....

---

### Post by realzippy on 2010-08-29
The xorg.conf file from the link you posted cannot work;it calls the "nv" driver;
the one suggested from the other thread has a wrong modeline...or do I understand wrong?
You want 1280x1024 ?
Anyway ,add vdpau ppa (xswat only has the driver for 10.04):

Delete *monitors.xml*,restart X/reboot

```
sudo add-apt-repository ppa:nvidia-vdpau/ppa
```

```
sudo apt-get update
```

the 256.driver (or "current") should appear in *Hardware Drivers*
Install it and reboot.

---

### Post by cchaos on 2010-08-29
> **realzippy said:**
> The xorg.conf file from the link you posted cannot work;it calls the "nv" driver;
the one suggested from the other thread has a wrong modeline...or do I understand wrong?
You want 1280x1024 ?
Anyway ,add vdpau ppa (xswat only has the driver for 10.04):

Delete *monitors.xml*,restart X/reboot

```
sudo add-apt-repository ppa:nvidia-vdpau/ppa
```

```
sudo apt-get update
```

the 256.driver (or "current") should appear in *Hardware Drivers*
Install it and reboot.
Nope that didnt fix it.

However since I know now what driver Im looking for, I have found it in the Package Manager

Uninstall the old one and then install the newer one via package manager?

---

### Post by realzippy on 2010-08-29
The 2 commands should have made the driver appear,not fixing anything.
Yes,uninstall the old one (reboot)and then install the newer one via package manager(reboot).

---

### Post by cchaos on 2010-08-29
> **realzippy said:**
> The 2 commands should have made the driver appear,not fixing anything.
Yes,uninstall the old one (reboot)and then install the newer one via package manager(reboot).
Right actually theres a couple: which ones do I need?

PS: sorry for the resolution I decided to remove everything nvidia

---

### Post by realzippy on 2010-08-29
Install the three 256.44 files.

---

### Post by cchaos on 2010-08-29
Right as soon as thats done I will give it a reboot or try to configure it?

---

### Post by realzippy on 2010-08-29
Reboot.The kernel module for this driver has to be loaded.

---

### Post by cchaos on 2010-08-29
Hasnt sorted it :(


In low resolution mode (800x600). Something about nv driver not available. Nvidia settings complaining that x-server isnt started and wants me to run as root.

Time to edit xorg.conf manually? Just reading the readme about the driver installed. Says it should be "nvidia" rather than "nv" or anything else

---

### Post by realzippy on 2010-08-29
[I]Something about nv driver not available?
Nvidia settings complaining that x-server isnt started [/I]

Can you specify?

---

### Post by realzippy on 2010-08-29
Run:
```
sudo nvidia-xconfig
```

errors?

---

### Post by cchaos on 2010-08-29
> **realzippy said:**
> [I]Something about nv driver not available?
Nvidia settings complaining that x-server isnt started [/I]

Can you specify?
Photos:

Seriously thinking that the only fix now is a clean install, and see what I have under Ubuntu 10.04

---

### Post by cchaos on 2010-08-29
> **realzippy said:**
> Run:
```
sudo nvidia-xconfig
```

errors?
```
Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```
However that has changed the xorg.conf file. Reboot?

---

### Post by realzippy on 2010-08-29
*New X configuration file written to '/etc/X11/xorg.conf'*

Restart X after this to load new file,and post the new xorg.conf please...

---

### Post by cchaos on 2010-08-29
Reboot has made it worse. Wonder if thats down to my "friend" monitors.xml?

---

### Post by cchaos on 2010-08-29
> **realzippy said:**
> *New X configuration file written to '/etc/X11/xorg.conf'*

Restart X after this to load new file,and post the new xorg.conf please...
Xorg.conf:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 256.44  (buildmeister@builder97.nvidia.com)  Thu Jul 29 02:00:07 PDT 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```
And monitors.xml doesnt exist

---

### Post by realzippy on 2010-08-29
xorg.conf seems to be fine.
And nvidia does not run?
What does nvidia-settings show?

---

### Post by cchaos on 2010-08-29
> **realzippy said:**
> Xorg.conf seems to be fine.
And nvidia does not run?
What does nvidia-settings show?
Nvidia seems to be running now but its at (very) low resolutions.Im tempted just to "tweak" the horizontal sync up to an old value just to see if that will get a higher resolution. But sudo nvidia-settings is showing that it still cant detect the monitor - which brings us full circle back to the error of earlier?

---

### Post by cchaos on 2010-08-29
Just found out that the Frequency supported on the monitor is:

Horizontal: 24 - 80khz
Vertical: 55 - 75hz

---

### Post by realzippy on 2010-08-29
HorizSync 28.0 - 83.0
VertRefresh 56.0 - 75.0

are the xorg.conf values for an  22"TFT here..btw.

Have you tested those?

---

### Post by cchaos on 2010-08-29
Worth a try at editing the xorg.conf to that then?

Here is the link I found: [http://www.aurora.se/iiyama/iiyama-prolite-e430.htm](http://www.aurora.se/iiyama/iiyama-prolite-e430.htm) except mine is a e430t (not sure what the difference is but I know that mine doesnt have a DVi in)

No not yet, but I will now take that as you want me to

---

### Post by realzippy on 2010-08-29
[I]Worth a try at editing the xorg.conf to that then?
[/I]
Yes,not a try,you have to.If higher resolutions than 1280x1024 (your Iljama's native) appear,don't try to use them to prevent damage..

---

### Post by cchaos on 2010-08-29
> **realzippy said:**
> [I]Worth a try at editing the xorg.conf to that then?
[/I]
Yes,not a try,you have to.If higher resolutions than 1280x1024 (your Iljama's native) appear,don't try to use them to prevent damage..
Dont know why I just didnt find that out in the first place :lol: When it rebooted I could tell it was in a better resolution. Now Im able to set it at 1280X1024. And indeed you are correct: there are other resolutions available.

Xorg.conf now reads:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 256.44  (buildmeister@builder97.nvidia.com)  Thu Jul 29 02:00:07 PDT 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       24.0 - 80.0
    VertRefresh     55.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

Many thanks for your help. Now Im sure its a small job just to set 1280x1024 as the "mode"

---

### Post by realzippy on 2010-08-29
"*Save to x configuration file*" in nvidia-settings.Then it should persist reboot.If so,you can set thread as "solved" ...

---

### Post by cchaos on 2010-08-29
> **realzippy said:**
> "*Save to x configuration file*" in nvidia-settings.Then it should persist reboot.If so,you can set thread as "solved" ...
Done that, all working. Thankyou :)

---

