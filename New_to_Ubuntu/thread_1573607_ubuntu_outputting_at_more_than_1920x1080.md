---
title: "ubuntu outputting at more than 1920x1080"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by Mr.Transistor on 2010-09-13
i decided to move my server over to my 65" dlp. and i have done this before with the exact same machine running different variations of windows OS's(<<=eeew =]) with no trouble but no matter what version of ubuntu i use i get this same issue. the drivers for my video card are set to output 1920x1080 but what is apearing on the screen is a larger resolution because all of the edges of the OS are pusshed outside of what the display is capable(1080p max). i have been told that the xorg.conf needs a line added to let the OS know exactly what res to run but i am unsure what that line is. this seems to be a common problem that alot of users have but every fix i can find does not solve my problem... any ideas?

---

### Post by CharlesA on 2010-09-13
Sounds like something to do with overscan, but I have no idea if that's actually the case or how to fix it. :(

---

### Post by antmenj on 2010-09-13
I have found this feature (see attached) helpful with similar issues.  This is NOT shown in the menu by default in my version so you have to enable it as shown via system--> preferences --> main menu before using it.  On my version it then shows up under applications --> other.....

---

### Post by Mr.Transistor on 2010-10-03
no this menu item does not have anything to do with it... ya from what i read everywhere it is "over scan" most solutions are in the settings of the display itself. not mine. like i said. when i ran win xp and win server it displayed perfectly... anyone else have an idea? i am told i should edit modline but i don't know what to add to the script. i tryed one attempt at that so far and it crashed the kernal and would allow me to restart it...

---

### Post by jtarin on 2010-10-03
[Maybe here]("http://ubuntuforums.org/showthread.php?t=595105")

---

### Post by Mr.Transistor on 2010-10-06
how does the modeline have to look in the zorg.conf? nobdy gives a clear example of the suntax and where to put it within the script they just say get your x, y, and refresh rate and put it in the file... but clearly you don't just throw it in there anywhere.


xorg.conf* lol

---

### Post by jtarin on 2010-10-06
I have had problems with modelines that contain the decimal point in the label, and I always cut out the ".00" part.

If your xorg.conf file has a "ModeLines" section, then insert the modeline there. Notice the "UseModes" command in the "Monitor" section. Alternately, your xorg.conf file might have xorg calculate the modelines on the fly and not need a modelines section. In that case, add the modeline to the "Monitor" section.

First Method:
```
Section "Monitor"
  DisplaySize  332 207
  HorizSync    32-48
  Identifier   "Monitor[0]"
  ModelName    "ZV5000"
  Option       "DPMS"
  VendorName   "HP"
  VertRefresh  40-70
  UseModes     "Modes[0]"
EndSection


Section "Modes"
  Identifier   "Modes[0]"
  # 1280x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 80.14 MHz
  Modeline "1280x768_60"  80.14  1280 1344 1480 1680  768 769 772 795  -HSync +Vsync
  Modeline 	"1280x800" 80.58 1280 1344 1480 1680 800 801 804 827
  Modeline 	"1280x800" 67.25 1280 1328 1360 1440 800 803 809 822 +HSync -Vsync
  Modeline 	"1280x768" 80.14 1280 1344 1480 1680 768 769 772 795
...
```
Second Method:
```

Section "Monitor"
  DisplaySize  332 207
  HorizSync    32-48
  Identifier   "Monitor[0]"
  ModelName    "ZV5000"
  Option       "DPMS"
  VendorName   "HP"
  VertRefresh  40-70
  # 1280x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 80.14 MHz
  Modeline "1280x768_60"  80.14  1280 1344 1480 1680  768 769 772 795  -HSync +Vsync
EndSection
```
It would be a good idea to backup your xorg.conf file before editing it:

```
sudo cp xorg.conf xorg.conf.backup
```

---

### Post by ahorriblemess on 2010-10-11
I had the same problem. It turned out my TV wasn't set correctly. 

After hours of trying all kinds of things, I found this post: [http://ohioloco.ubuntuforums.org/showpost.php?p=7801095&postcount=6](http://ohioloco.ubuntuforums.org/showpost.php?p=7801095&postcount=6)

On my Sony Bravia TV the setting is: Screen>Auto Wide and Display Area. When I set "Auto Wide" to "off" it allowed me to edit "Display Area" which I set to "Full Pixel." It's default setting was "Normal."

Worth looking into...

---

### Post by Mr.Transistor on 2010-11-06
> **ahorriblemess said:**
> I had the same problem. It turned out my TV wasn't set correctly. 

After hours of trying all kinds of things, I found this post: [http://ohioloco.ubuntuforums.org/showpost.php?p=7801095&postcount=6](http://ohioloco.ubuntuforums.org/showpost.php?p=7801095&postcount=6)

On my Sony Bravia TV the setting is: Screen>Auto Wide and Display Area. When I set "Auto Wide" to "off" it allowed me to edit "Display Area" which I set to "Full Pixel." It's default setting was "Normal."

Worth looking into...

well i have infact checked all of these possibilities (A+ Cert troubleshooting lol). my tv is definitely not the issue. i have ran many oporating systems in 1920x1080 just fine and automatic on the same machine. also other machines run just fine but not in ubuntu.


this is what i get when i use the instruction gtf 1920 1080 60:
```
# 1920x1080 @ 60 Hz (GTF) sync: 67.08;
pclk: 172.80 Mhz ModeLine "1920x1080 60.00" 172.80 1920 2040 2248 2576 1080 1081 1084 1118 -HSync +Vsync
```

This is what my xorg.conf looks like:
```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
    SubSection "Display"
        Depth    24
        Modes    "1920x1080_60.00"
    EndSubSection
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

```
sooooo..... what can i do to get what i want? i have been hiding this machine in the closet instead of solving the problem. help please.

---

### Post by Mr.Transistor on 2010-11-07
Bump

---

### Post by P4man on 2010-11-07
Is this an ATI card? And are you using restricted or open drivers?
If you are using restricted try this:

```
aticonfig --tv-overscan=off
```

And/or in catalyst control center under adjustments select "use display for scaling". In htdv you can also click ADD and create a custom mode (again still using catalyst. No clue using the open drivers).

---

### Post by Mr.Transistor on 2010-11-07
> **P4man said:**
> Is this an ATI card? And are you using restricted or open drivers?
If you are using restricted try this:

```
aticonfig --tv-overscan=off
```

And/or in catalyst control center under adjustments select "use display for scaling". In htdv you can also click ADD and create a custom mode (again still using catalyst. No clue using the open drivers).

i am pretty confident that it is Nvidia it's running on there drivers...

---

### Post by Mr.Transistor on 2010-11-09
> **P4man said:**
> Is this an ATI card? And are you using restricted or open drivers?
If you are using restricted try this:

```
aticonfig --tv-overscan=off
```

And/or in catalyst control center under adjustments select "use display for scaling". In htdv you can also click ADD and create a custom mode (again still using catalyst. No clue using the open drivers).

is there a command like this for nvidia?

---

### Post by sandyd on 2010-11-09
> **Mr.Transistor said:**
> is there a command like this for nvidia?

```

sudo nvidia-xconfig --tv-over-scan=0.0
```
or
```

sudo nvidia-xconfig --tv-over-scan=1.0
```

---

### Post by fooman on 2010-11-09
does this have to be command line?  or can you use the nvidia-settings GUI? ... if you can use the gui, run:

```
nvidia-settings
```

look in the left column,  under GPU-0 you should see your monitor/tv listed....click on it and on the right there should be a slider for "overscan compensation"

---

### Post by Mr.Transistor on 2010-11-12
well i have tryed 
```
nvidia-xconfig --tv-over-scan=0.0

```
&
```
nvidia-xconfig --tv-over-scan=1.0

```
no success... did nothing.. so that rules out over scan as the culprit...
and again there is no settings for this in my tv either. what else could it be. i do have it running over a DVI to HDMI cable but i doubt that would be a problem. because i am not worried about interlaced or progressive. i just want the ressolution and i should still be able to have my 1920x1080 even if it is interlaced.

---

### Post by Mr.Transistor on 2010-11-14
what other settings could be the culprit?

---

### Post by Mr.Transistor on 2011-01-10
so i have been walking in circles with this problem for a long time now.. it wouldn't have anything to do with the fact that i am going from DVI to HDMI right? i used the same machine and cable to run and display windows and it displayed flawlessly...

---

### Post by achron on 2011-02-07
> **Mr.Transistor said:**
> so i have been walking in circles with this problem for a long time now.. it wouldn't have anything to do with the fact that i am going from DVI to HDMI right? i used the same machine and cable to run and display windows and it displayed flawlessly...

Just bumped into this issue myself at home after upgrading to a Samsung P2770FH 27" monitor. I was using a DVI to HDMI cable and Win 7 worked fine (yes, I know, but there are some apps/devices that just don't work under Ubuntu...). When I booted to 10.10, top and bottom of the screen wasn't visible, but it was there (could access menus, etc).

On the off-chance, I swapped from DVI->HDMI cable to DVI->DVI cable that came with the monitor, and voila, case solved (at least for me). No editing anything, just a cable swap.

---

### Post by buzzlight2nd on 2011-02-11
I'm a nube...
How do I set my display settings to something LESS than 1920x1080?
I cannot read the fine print without putting my nose to the screen. 
Also, some of the display is off the no man's land on the left of the screen where I cannot see it. 
 
Thanks In Advaance
P.S. I cannot find out how to post a NEW THREAD!? So please excuse me for posting this thread here.

---

