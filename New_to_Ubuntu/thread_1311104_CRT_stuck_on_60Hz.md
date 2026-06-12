---
title: "CRT stuck on 60Hz"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by LanceyD on 2009-11-02
Don't have any option to change resoluion or refresh rate, stuck on 1024*768 60Hz, it's hurting my eyes :p

Spec: 
Ubuntu 9.04 (although currently downloading 9.10)
NVidia Geforce 7900 GTO 256Mb with latest reccomended package (180 i think) 

I installed two packages to try and get the 3D to work in Chess, now it just opens and closes straight away.  3D works fine on sceensavers though.  

I don't know if the 2 problems are linked.  When chess is opened the Graphics card fans kicks in as it used to in windows when opening a game.

---

### Post by LanceyD on 2009-11-02
Just upgraded to the lastest package and now when i try and boot on the first option, the screen flashes on startup.  Black screen with version and system start up, eventually asking to log in but in text and still flashing, impossible to enter any data.

option3 boots up but i have crazy horizontal green lines scrolling across the top, wish i'de stayed with 9.04 now, only upgraded to see if i can ge 85hz refresh and 60hz was killing my eyes :(

---

### Post by scratman on 2009-11-02
You wouldn't have a NVidia graphics card would you?  I had a similar problem, which I resolved by booting up using a previous Kernel, and then selecting the 2nd most recent NVidia drivers, 173 in my case.

---

### Post by Frantic_Earthling on 2009-11-02
I stuck with the current kernel. but rolled back my nVidia driver to 173.
Problem solved (so far...)

---

### Post by LanceyD on 2009-11-02
yes NVidia GeForce 7900 GT

What's with all these problems with NVidia, when i was searching for the 60hz problem it seems this has been ongoing for years :???:

---

### Post by LanceyD on 2009-11-02
I get 1 minute of use and then crash, blank screen and have to reboot then the same.

how do i roll back divers?

---

### Post by LewRockwell on 2009-11-02
> **LanceyD said:**
> I get 1 minute of use and then crash, blank screen and have to reboot then the same.

just do this:

[http://ubuntuforums.org/showthread.php?t=1308317](http://ubuntuforums.org/showthread.php?t=1308317)

.

---

### Post by Frantic_Earthling on 2009-11-02
> **LanceyD said:**
> I get 1 minute of use and then crash, blank screen and have to reboot then the same.

how do i roll back divers?

All you need to do is to go to:

System -> Admin -> Hardware Drivers

You should find that 185 is "recommended" and probably already installed.
Just activate 173. That will take care of the uninstallation of 185 and of the install of 173.

Hope this does it for you.

---

### Post by LanceyD on 2009-11-02
> **Frantic_Earthling said:**
> All you need to do is to go to:

System -> Admin -> Hardware Drivers

You should find that 185 is "recommended" and probably already installed.
Just activate 173. That will take care of the uninstallation of 185 and of the install of 173.

Hope this does it for you.

Thanks for the reply.  While i was waiting, i removed the nvidia driver and reinstalled the 185 and it now boots to latest kernal, albeit with a few heart wrenching flashing screens on the way.  seems ok so far though :D

When i asked the question before, the hardware drivers section was blank, that's why i asked :???:

---

### Post by LanceyD on 2009-11-02
Now running Ubuntu 9.10 and latest 185 nVidia package, still only have 60hz, my eyes are watering :(

---

### Post by LanceyD on 2009-11-02
Come on chaps, someone must be able to help, i'm going blind here :p

---

### Post by LanceyD on 2009-11-02
maybe i've worded my previous thread wrong, or maybe there is no solution.  But i'm going to try a new thread to find a solution because my eyes are more important than Ubuntu

[http://ubuntuforums.org/showthread.php?p=8225668#post8225668](http://ubuntuforums.org/showthread.php?p=8225668#post8225668)

I'm running nVidia package 185
Ubuntu 9.10

Geforce 7900 GTO
Belinea 19" CRT 
Dual 3.2Ghz
2mb RAM

i cannot change the refresh rate at all, it is on 60hz and that's it, i was previously running on 85hz with XP.  What can i do :(

This really really should be just a point and click "forced" app, it's one thing Windows had right, change it and if it works then great if not it flicks back, it's not as if i'm using some back and beyond graphics card or monitor either.

Thanks :D

---

### Post by LanceyD on 2009-11-02
**How to change to 85hz refresh rate**             
                                                                maybe i've worded my previous thread wrong, or maybe there is no solution. But i'm going to try a new thread to find a solution because my eyes are more important than Ubuntu

[http://ubuntuforums.org/showthread.p...68#post8225668]("http://ubuntuforums.org/showthread.php?p=8225668#post8225668")

I'm running nVidia package 185
Ubuntu 9.10

Geforce 7900 GTO
Belinea 19" CRT 
Dual 3.2Ghz
2gb RAM

i cannot change the refresh rate at all, it is on 60hz and that's it, i was previously running on 85hz with XP.  What can i do :sad:

This really really should be just a point and click "forced" app, it's one thing Windows had right, change it and if it works then great if not it flicks back, it's not as if i'm using some back and beyond graphics card or monitor either.

---

### Post by NickJones on 2009-11-02
Try going to: System, Preferences, Displays, 
Click on refresh rate, if your drivers support it, you should be able to change it from 60Hz. Why do you want to change it anyway?

---

### Post by LanceyD on 2009-11-02
60hz is the only option available.  

My eyes water on 60hz, on XP i've always had it on 85hz.  Its a CRT by the way.

---

### Post by Vaphell on 2009-11-02
because 60Hz on a CRT monitor is BAD - flickering is clearly visible and your eyes really suffer

---

### Post by Cypher on 2009-11-02
If you have the restricted Nvidia drivers, when you go to System->Preferences->Displays, it should prompt you about starting the "vendor tool" and in there as long as your monitor is detecetd properly it should allow you to change the resolution.

@NickJones, the OP says that he has a CRT and not an LCD. LCD's are run at 60 hz by default, but CRTs have been run at at least 75 hz to avoid CRAZY flicker.

Regards

---

### Post by jimmy the saint on 2009-11-02
try opening a terminal and running

```
nvidia-settings
```

That will give you nvidia's direct settings manager.

---

### Post by LanceyD on 2009-11-02
> **Cypher said:**
> If you have the restricted Nvidia drivers, when you go to System->Preferences->Displays, it should prompt you about starting the "vendor tool" and in there as long as your monitor is detecetd properly it should allow you to change the resolution.

@NickJones, the OP says that he has a CRT and not an LCD. LCD's are run at 60 hz by default, but CRTs have been run at at least 75 hz to avoid CRAZY flicker.

Regards

Hi, yes i run the vendor tool.  Monitor is not detected. Why can i not force it like in Windows?

---

### Post by LanceyD on 2009-11-03
please please please can someone help :(

---

### Post by LanceyD on 2009-11-03
18 hours and i've had the windows equivalent help of "right click on desktop" :D and a bit of blind leading the blind, then had my threads merged which has helped nothing as now my title is not attracting anyone in.

Nobody willing to take on the challenge and give me some real help before i go blind?  

I have been searching to forums and lots of people have had similar problems but i cannot find any solutions.  Why not just force the refresh, why can this not be done?

---

### Post by realzippy on 2009-11-03
Please post your xorg.conf file.Its in /etc/X11:

To open it:

gedit /etc/X11/xorg.conf

If you do not have one (or its empty) run in terminal:

[B]sudo nvidia-xconfig
[/B]

to create a new one...

Which resolution do  you want to achieve?

---

### Post by P4man on 2009-11-03
+1 What real zippy asked

Also do you have a precise monitor model or its technical specs? Particularly horizontal and vertical refresh rates, so we can enter those in your xorg.conf, since it seems nvidia drivers arent recognising your monitor and defaulting to a safe 60Hz.

if you dont have those, what resolution and refresh rate can you set in windows?

---

### Post by LanceyD on 2009-11-03
CRT is a Belinea 19" model: 10 60 20
Max resolution of 1600 x 1200 75hz
Max syn rate (V x H) 150Hz x 95kHz 

> 
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

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection


ideally would like 1024*768 at 85hz, thats how it was running in XP

---

### Post by realzippy on 2009-11-03
Please make your xorg.conf screen section look like:


Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
[COLOR="SeaGreen"]Option         "metamodes" "1024x768_75 +0+0; nvidia-auto-select +0+0"[/COLOR]
EndSection


and restart X (log out/in)

 edit: This tries to set refresh to 75 HZ.If it works,you can test 85 Hz.


Before please backup your old xorg by typing in terminal:

[B]sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
[/B]

In case of harm you can restore it by:

sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf

---

### Post by P4man on 2009-11-03
150Hz vertical? Wow.

Anyway open the file with root permissions:

sudo gedit /etc/X11/xorg.conf

add the red section:

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
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
Identifier "Configured Monitor"
[COLOR="Red"]    HorizSync       30.0 - 95.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"[/COLOR]
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
EndSection

Section "Module"
Load "glx"
EndSection

Section "Device"
Identifier "Configured Video Device"
Driver "nvidia"
Option "NoLogo" "True"
EndSection 
```

Save. restart X
```
sudo /etc/init.d/gdm restart
```
(or reboot)

If this messed things up and you dont get a GUI you can get back to a terminal with control alt F1 then type

```
sudo nano /etc/X11/xorg.conf
```

to edit the file again (control +x to quit and save changes)

edit: zippy beat me to it. If his solution doesnt work you can try adding my red part :D

---

### Post by realzippy on 2009-11-03
Yeah.do what P4man says,do not feel confused.
The green line (I gave you) should force nvidia to use 1024x768@75.

The Red section (P4man) should tell nvidia-settings your monitor range abilities to choose from in the GUI.Can paste both,will not harm.

---

### Post by LanceyD on 2009-11-03
realzippy & p4man, i used both your solutions, and now i can feel the relief in my eyes :D
it switched to 75hz and then from the drop down i chose 85hz, all working brilliantly.  It is such a good monitor that i didn't really want to change it.

many thanks, now i can enjoy Ubuntu!

---

### Post by P4man on 2009-11-03
Good :)
Now you can start playing with it and run in to the next problem :p

I do agree with you though, nvidia should allow a manual "force" option to set resolution and refresh rates. its all nice and well if it all works automatically, but if it doesnt (and clearly that happens) there ought to be a simpler way than manually editing xorg.conf.

---

### Post by realzippy on 2009-11-03
One more thing:

To save chosen refreshrate after reboot you have to open nvidia-settings by

**gksudo nvidia-settings**

set resolution (85),and hit the 
"save to X configuration file" button or settings will be lost after reboot...

have fun !

---

### Post by LanceyD on 2009-11-03
Thanks.  Ive got modes that didn't work in Windows now.  I'm now running 1280x1024 at **85hz**, the monitor OSD also confirms this :D

---

### Post by Viva on 2009-11-03
> **realzippy said:**
> Please make your xorg.conf screen section look like:


Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
[COLOR="SeaGreen"]Option         "metamodes" "1024x768_75 +0+0; nvidia-auto-select +0+0"[/COLOR]
EndSection


and restart X (log out/in)

 edit: This tries to set refresh to 75 HZ.If it works,you can test 85 Hz.


Before please backup your old xorg by typing in terminal:

[B]sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
[/B]

In case of harm you can restore it by:

sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf

I did this, but I still can't set the refresh rate to higher than 60. Windows XP allows me to choose up to 75.

---

### Post by realzippy on 2009-11-03
> **Viva said:**
> I did this, but I still can't set the refresh rate to higher than 60. Windows XP allows me to choose up to 75.



So post your xorg.conf please and your monitor model if not listed in screen section..

---

### Post by Viva on 2009-11-03
> **realzippy said:**
> So post your xorg.conf please and your monitor model if not listed in screen section..

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@crested)  Sun Feb  1 20:25:37 UTC 2009


Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
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

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 61.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Default Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 SE/7200 GS"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Default Device"
    Monitor        "Monitor0"
EndSection

Section "Screen"

# Removed Option "metamodes" "1280x720_75 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1280x720_75 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

I've edited it as you pointed out in the other post. This flicker gave me a head ache:(

---

### Post by realzippy on 2009-11-03
*I've edited it as you pointed out in the other post. This flicker gave me a head ache:*

That was for the threadstarter's monitor:

CRT is a Belinea 19" model: 10 60 20
Max resolution of 1600 x 1200 75hz
Max syn rate (V x H) 150Hz x 95kHz 

**Do not** insert those given modeline to other monitors please... 

Did you create a complete **new** xorg?Seems kinda strange for me because there are doubled (outcommended) entries...  ?

Your monitor also will not work higher than 75 Hz:

HorizSync       30.0 - 61.0
    VertRefresh     56.0 - [COLOR="Red"]75.0[/COLOR]
EndSection

I would edit it;set to 85.0 will not do harm.

---

### Post by Viva on 2009-11-03
The commented entries are caused by nvidia-settings. I only need to set the refresh rate to 75 Hz. Another question, is it horizontal or vertical refresh rate you can set in the nvidia-settings?

---

### Post by realzippy on 2009-11-03
> **Viva said:**
> The commented entries are caused by nvidia-settings. I only need to set the refresh rate to 75 Hz. Another question, is it horizontal or vertical refresh rate you can set in the nvidia-settings?

I was confused about e.g.:

# Removed Option "metamodes" "1280x720_75 +0+0"

BTW,is it your monitor's native resolution?Why not 1024*768  or 1280*1024?

I suggest you try again:

**sudo rm /etc/X11/xorg.conf**
**sudo nvidia-xconfig**
  *restart Xserver (log out,in)*
**gksudo nvidia-settings**
  [I]this time,as mentioned,depending to monitor's native resolution make
  your settings[/I]
Hit apply and hit "save to X configuration file".

---

### Post by Viva on 2009-11-03
It is my monitor's native resolution. I was just going through the manual and it looks like 60hz is the maximum refresh rate too, but it flickers at that rate on both windows and ubuntu. Windows allows me to force a 75hz refresh rate where I don't see the flicker.

---

### Post by realzippy on 2009-11-03
No idea.

Option "UseEDIDFreqs" "FALSE"

inserted in monitor or screen section (forgot,google for it!) or paste twice,allows refreshrates higher than the monitor's EDID's data.

HorizSync       30.0 - 121.0
VertRefresh     48.0 - 160.0

would do no harm until you set refreshrates higher than 75 Hz in nvidia-settings but should enable more options in choosing refreshrate.

---

### Post by P4man on 2009-11-03
I wouldnt push my luck. If nividia driver decides to enable the highest possible refresh rate your monitor may not like 150Hz if its designed for 60. Play it safe(r):

> **realzippy said:**
> No idea.

Option "UseEDIDFreqs" "FALSE"

HorizSync       30.0 - 121.0
VertRefresh     48.0 - [COLOR="DarkRed"]75.0[/COLOR]


that will limit the vertical refresh rate to 75Hz no matter what resolution you chose.

---

### Post by realzippy on 2009-11-03
Gave warning:
"until you set refreshrates higher than 75 Hz in nvidia-settings"

I suggested to do so because I am not shure if "VertRefresh 48.0 - 75.0"
in monitor section means to have 75 Hz as  option in nvidia-settings.
Had to edit modelines manually once and think I had to set max vert refresh in xorg higher to do so in nvidia-settings.Somebody knows.

---

### Post by P4man on 2009-11-03
Make it 76 then, but not 150 :)

---

### Post by LanceyD on 2009-11-03
I think my super duper CRT is confusing matters now :D

---

### Post by realzippy on 2009-11-03
> **P4man said:**
> Make it 76 then, but not 150 :)

you are right;)

---

### Post by Viva on 2009-11-04
Still no luck:(

Here is my latest xorg.conf
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@crested)  Sun Feb  1 20:25:37 UTC 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    Option         "UseEDIDFreqs" "FALSE"
    HorizSync       30.0 - 61.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 SE/7200 GS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1280x720_75 +0+0; 1280x720 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by Viva on 2009-11-04
It allows me to choose 75Hz on lower resolutions.

---

### Post by P4man on 2009-11-04
Hmm.. Im not sure what vertical refresh rate  a horizontal synch of 61.0 KHz allows at 1280x1024, I tried finding a calculator but couldnt find any. I thought it would be plenty for 1280x1024 @ 75Hz per perhaps its not.

you could try increasing the setting for horizontal synch from 61 to say 70. You'd basically be "overclocking" your monitor, proceed at your own risk.

---

### Post by LanceyD on 2009-11-04
> **P4man said:**
> Hmm.. Im not sure what vertical refresh rate  a horizontal synch of 61.0 KHz allows at 1280x1024, I tried finding a calculator but couldnt find any. I thought it would be plenty for 1280x1024 @ 75Hz per perhaps its not.

you could try increasing the setting for horizontal synch from 61 to say 70. You'd basically be "overclocking" your monitor, proceed at your own risk.

Mine requires a horizontal sync of 80kHz for 1280x1024 @ 75Hz and 91kHz @ 85 Hz

But viva is trying 1280x**720, **this is not a mode my monitor supports.

---

### Post by realzippy on 2009-11-04
> **P4man said:**
> Hmm.. Im not sure what vertical refresh rate  a horizontal synch of 61.0 KHz allows at 1280x1024, I tried finding a calculator but couldnt find any. I thought it would be plenty for 1280x1024 @ 75Hz per perhaps its not.

you could try increasing the setting for horizontal synch from 61 to say 70. You'd basically be "overclocking" your monitor, proceed at your own risk.

A calculator:

[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

You tested:
Option "UseEDIDFreqs" "FALSE"    ?
More:
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by P4man on 2009-11-04
I just found cvt does it as well.. well obviously.
1280x720 60 Hz would only require  44.77 kHz hsync ? Or am I misreading this:
```

cvt 1280 720 60
# 1280x720 59.86 Hz (CVT 0.92M9) hsync: 44.77 kHz; pclk: 74.50 MHz
Modeline "1280x720_70.00"   88.25  1280 1352 1480 1680  720 723 728 752 -hsync +vsync

```

and should pclk value be used? I got no clue lol

---

### Post by Viva on 2009-11-04
I think it is my power supply that is causing the problem. I don't see any flickering when I run my computer on UPS. Thanks for your time everybody.

---

