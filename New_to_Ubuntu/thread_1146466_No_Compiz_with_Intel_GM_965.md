---
title: "No Compiz with Intel GM 965?"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-05-02
Hey, I've upgraded to Jaunty and now compiz won't enable.

I also **just now** discovered that i don't actually have an nVidia card. I thought I did, but I also didn't know that intel made graphics cards :rolleyes:

So my question is, I saw xserver-xorg-intel in the upgrade manager last night as i was updating. I know that the intel driver is now installed.

Will having multiple graphics drivers cause compiz not to work?

Should I go into synaptic and uninstall any "nVidia" video drivers I see?

And how do I initially configure an intel card?
ATI has 
```
aticonfig --initial
```

What command do I use to initialize the intel driver?

Thanks for any help in advance :)

---

### Post by skymera on 2009-05-02
There are problems with Intel on 9.04
This was in the release notes :)

[http://www.ubuntu.com/getubuntu/releasenotes/904#Other%20known%20issues](http://www.ubuntu.com/getubuntu/releasenotes/904#Other%20known%20issues)

You also don't configure Intel cards :)

---

### Post by gooligan on 2009-05-02
I have Intel 945GM Chipset on my Dell E1705 and I have compiz enabled
I edited the Device section of /etc/X11/xorg.conf to look like this after reading the release recommendations:

```

Section "Device"
	Identifier	"Configured Video Device"
        Driver 		"intel"
        Option 		"AccelMethod" "EXA"
        Option 		"MigrationHeuristic" "greedy"
EndSection

```

---

### Post by asuastrophysics on 2009-05-02
Thanks, I tried changing my xorg.conf to the same specs, X starts just fine :P

But desktop effects still can't be enabled. Here is the output of compiz:
```
girdy@girdy-laptop:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: Segmentation fault
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Software Rasterizer: Segmentation fault
Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Segmentation fault
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
/usr/bin/compiz.real (core) - Fatal: glXCreateContext failed
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

---

### Post by Delirium_Trigger on 2009-05-02
> **asuastrophysics said:**
> Thanks, I tried changing my xorg.conf to the same specs, X starts just fine :P

But desktop effects still can't be enabled. Here is the output of compiz

I'm having the same problem you are.
I tried the xorg.conf and got no results.

---

### Post by asuastrophysics on 2009-05-02
> **gooligan said:**
> I have Intel 945GM Chipset on my Dell E1705 and I have compiz enabled
I edited the Device section of /etc/X11/xorg.conf to look like this after reading the release recommendations:

```

Section "Device"
	Identifier	"Configured Video Device"
        Driver 		"intel"
        Option 		"AccelMethod" "EXA"
        Option 		"MigrationHeuristic" "greedy"
EndSection

```

gooligan, is this all you edited in Xorg? did you add a line anywhere enabling GLX?

---

### Post by gooligan on 2009-05-02
Here is my entire xorg.conf (without the comments)

```

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
        Option          "AccelMethod" "EXA"
        Option          "MigrationHeuristic" "greedy"
EndSection

```

---

### Post by gooligan on 2009-05-02
I enabled compiz through the Gnome menu
System->Preferences->Appearance
Then select the "Visual Effects" tab and the "Extra" option
That will enable compiz

By the way, I am running Jaunty 9.04

---

### Post by asuastrophysics on 2009-05-03
> **gooligan said:**
> I enabled compiz through the Gnome menu
System->Preferences->Appearance
Then select the "Visual Effects" tab and the "Extra" option
That will enable compiz

By the way, I am running Jaunty 9.04

weird...I do the same thing and get "Desktop Effects could not be enabled", 
So I think it's not working because compiz won't start. 

And I'm left with metacity, which is really slow

This is the output of my Xorg.conf file:
```
Section "Device"
	Identifier	"Configured Video Device"
        Driver 		"intel"
        Option 		"AccelMethod" "EXA"
        Option 		"MigrationHeuristic" "greedy"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerFlags"
    Option    "IgnoreABI"    "True"
EndSection
```

seems like I'm running the intel driver. 
...any ideas why compiz still won't start?

---

### Post by gooligan on 2009-05-04
Sorry I don't have any solution for you, although you might want to check out this post.
[http://ubuntuforums.org/showthread.php?p=7209877](http://ubuntuforums.org/showthread.php?p=7209877)

---

### Post by asuastrophysics on 2009-05-07
> **skymera said:**
> There are problems with Intel on 9.04
This was in the release notes :)

[http://www.ubuntu.com/getubuntu/releasenotes/904#Other%20known%20issues](http://www.ubuntu.com/getubuntu/releasenotes/904#Other%20known%20issues)

You also don't configure Intel cards :)
This link doesn't say anything about compiz not loading. I've followed all of its suggestions and steps, including downgrading to an earlier driver version, and compiz still won't start. 

is there a workaround for this or should i just scrap 9.04 altogether?

sorry compiz has never worked for me ever since upgrading to 9.04 and i'm beginning to think that there never will be an update to fix it

this is the output of compiz:
> $ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: Segmentation fault
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault
not present. 
aborting and using fallback: /usr/bin/metacity 


can somebody please help me with this? ubuntu looks so **ugly** without compiz.
also other things that no longer work in 9.04:
- fullscreen mode for movies and youtube
**if fullscreen is selected in firefox, firefox simply crashes

how do i fix this?
what workarounds are available?
/usr/bin/compiz shows the i965 driver as **not** being blacklisted. skip-checking compiz also fails.

anyone? please?

---

### Post by pyjamashark on 2009-05-15
So here is the solution to getting Compiz working.
However, getting compiz to work is a separate issue to the reduced graphics performance.

[http://www.rudkin.me.uk/2009/04/22/how-to-get-your-intel-gm965gl960-working-with-compiz-on-ubuntu-jaunty-jackalope/](http://www.rudkin.me.uk/2009/04/22/how-to-get-your-intel-gm965gl960-working-with-compiz-on-ubuntu-jaunty-jackalope/)

Enjoy

---

### Post by ndmaque on 2009-05-15
Intel 965 on a lenovo thinkpad T61, Ubunto 9.04 

A good thread so i add my humble experience to the SEO.

I am a newbie to linux so excuse my basic info.

I had problems. Compiz manager installed ok after removing Intel 965 from blacklist in the config etc all was well but after messing with settings it went wrong, apps snapped to the top and the desktop toolbar and the app toolbar went under the desktop toolbar so you couldn't see it in GUI.

I disabled all effects in compiz manager but it was still wonky, couldnt switch desktops, and minimize app lost my mouse and keyboard.

The solution for me was to go back into system >> preference >> appearance >> visual effects and select extra which kept reverting to none.

Whatever you do when you have multiple screens compiz doesn't work as far as i know. boot without an external screen on a lenovo T61 and compiz is fine.

---

### Post by asuastrophysics on 2009-05-17
Thread -> Solved

I did a complete reinstallation of ubuntu 9.04, and commented out the blacklist in compiz. Solved all my problems. 

back to wobbly windows & cool effects :cool:

---

