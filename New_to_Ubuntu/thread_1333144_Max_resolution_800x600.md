---
title: "Max resolution 800x600?"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by JumpJump123 on 2009-11-21
I just installed Ubuntu, having wanted to be rid of XP for too long. First problem - the only two resolution's available are 640x860 and 800x600. 

My monitor is a crappy generic 17inch flat-screen thing, no brand no nothing. Graphics card is Intel Extreme Graphics.

I'm pretty clueless as regards to Terminal commands, etc; was looking around old threads for help but couldn't follow a lot of what was said. Am hoping this won't be too much of a hassle, just a driver issue or whatever, because it's very annoying.

Internet is also crawling, where it was lightning fast on XP...but that's another issue.

Any help appreciated.

---

### Post by prshah on 2009-11-21
> **JumpJump123 said:**
> First problem - the only two resolution's available are 640x860 and 800x600. 

Graphics card is Intel Extreme Graphics.

Internet is also crawling, where it was lightning fast on XP...but that's another issue.


Please see [this post]("http://ubuntuforums.org/showpost.php?p=7656979&postcount=2") for how to set a custom resolution with Intel Graphics.

And please see [[SOLVED] Firefox/Epiphany/Lynx not loading certain websites]("http://ubuntuforums.org/showthread.php?t=718709") for a possible solution to slow Internet. It helps if you read the entire thread, but if you are impatient, you can just jump to the 2nd page, where the solution is detailed.

Please post back if you need more help or more detailed instructions with any of these "solutions". Please note that these address only particular issues, which may or may not be the actual problem you are facing.

---

### Post by JumpJump123 on 2009-11-21
Edit

---

### Post by JumpJump123 on 2009-11-21
UPDATE: Okay, I edited the xorg.conf with what I think are my monitor's native settings (as I said, I don't have any documentation for the generic monitor I have). And nothing happened. No other resolution options in Display. Anything I'm missing?

---

### Post by Sir Jasper on 2009-11-21
Hi,

If you open a terminal and type or copy and paste the code below

xrandr

then press Return do you see various screen sizes as output?

My regards

---

### Post by JumpJump123 on 2009-11-21
It gave me this:

Screen 0: minimum 320 x 200, current 800 x 600, maximum 2048 x 2048
VGA1 connected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        60.3* 
   640x480        59.9

---

### Post by Sir Jasper on 2009-11-21
Hi again,

Sorry. Since only two resolution are shewn as available the method I was thinking of will not work.

My regards

---

### Post by prshah on 2009-11-21
> **JumpJump123 said:**
> UPDATE: Okay, I edited the xorg.conf with what I think are my monitor's native settings (as I said, I don't have any documentation for the generic monitor I have). And nothing happened. No other resolution options in Display. Anything I'm missing?

You have to restart the X server (or the computer) for the changes to take effect; restarting the computer would be easiest, but if you would prefer to restart the X server:

a) Press Ctrl_Alt_F1 to switch to a virtual terminal.
b) Login
c) Give the command```
sudo service gdm restart
```
d) Your screen might flicker, please wait a few seconds
e) If the GUI doesn't show up after a few (10~15) seconds, please press Ctrl_Alt_F7 to switch to the GUI from the virtual terminal.

If it doesn't work, please post your /etc/X11/xorg.conf file and your /var/log/Xorg.0.log file.

Please post back with the results.

---

### Post by JumpJump123 on 2009-11-22
Well, that was a nightmare...

I restarted, and the computer went to the X server, but the screen was flashing rapidly and I couldn't type properly - I would have to keep punching in a key to get it to react, the whole thing was stuttered. When I hit Num-Lock it flashed on and off rapidly and wouldn't stop.

I had to reinstall Ubuntu.

I tried it again (stupidly, I know - assuming the problem had been something else), and the same thing happened again.

Ubuntu reinstall number 3.

I'm hoping this can be resolved, it's becoming a bit of a headache. I don't have Windows anymore (didn't dual-boot) so I really need a way around this.

---

### Post by arnab_das on 2009-11-22
is your graphics card an nvidia?

if so here's something to help u out:

[http://thoughtsndreams.wordpress.com/2009/10/23/installing-nvidia-drivers-in-ubuntu/](http://thoughtsndreams.wordpress.com/2009/10/23/installing-nvidia-drivers-in-ubuntu/)

---

### Post by JumpJump123 on 2009-11-22
No, it's an old Intel Extreme Graphics card. This thing is ancient.

---

### Post by JumpJump123 on 2009-11-22
Don't know how relevent/helpful this is, but this is my monitor:

[http://www0.uk.shopping.com/xPO-Emprex-LM1704-Black-Wite](http://www0.uk.shopping.com/xPO-Emprex-LM1704-Black-Wite)

---

### Post by wojox on 2009-11-22
So what does

```
lspci | grep VGA
```

Tell us?

---

### Post by JumpJump123 on 2009-11-22
Hey. It shows this:

milk@milk-desktop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

---

### Post by realzippy on 2009-11-22
I think the xrandr suggestion is the way to go...which resolution do you want?? 1024x768?  1280x1024 ?refresh rate?

---

### Post by JumpJump123 on 2009-11-22
Afaik 1280x1024 is my monitor's native res so that would probably be ideal, with 60hz refresh. What do I do?

---

### Post by realzippy on 2009-11-22
type in terminal

**cvt 1280 1024 60**

and post output (Modeline)

---

### Post by JumpJump123 on 2009-11-22
```
milk@milk-desktop:~$ cvt 1280 1024 60
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
```

---

### Post by realzippy on 2009-11-22
add this new mode
terminal:

[B]xrandr --newmode "1280x1024_60.00" 109.00 1280 1368 1496 1712 1024 1027 1034 1063 -hsync +vsync
[/B]

then link it to your monitor
terminal:

**xrandr --addmode VGA1 1280x1024_60.00**

and switch to it
terminal:

**xrandr --output VGA1 --mode 1280x1024_60.00**

---

### Post by JumpJump123 on 2009-11-22
Hey, thanks! That worked, only:

The 1280x1024 res looks odd, just as a res in general. I used 1024x768 afair in Windows, so I tried that...
But 1024x768 is distorted, it looks terrible.

Why is this exactly? Am I forcing these resolutions essentially?

Thanks a lot, either way. If I could get the 1024x769 as smooth as Windows it would be perfect

---

### Post by realzippy on 2009-11-22
So you understood how xrandr works.

You could generate more modelines to test,especially I would try different refresh rates,e.g:

cvt 1024 768 [COLOR="SeaGreen"]75[/COLOR]    (do not go higher than 75 until you know your monitor can handle)

I am not sure if the settings persist after restart,could you try?
Maybe you had to copy modeline in xorg.conf...

BTW,beeing on Karmic(??),do you have a xorg.conf?  (Usually in /etc/X11/)

If so,please post it.

P.S.

You also could try cvt without any given refresh rate,e.g. [COLOR="SeaGreen"]cvt 1024 768[/COLOR],then it is set to "auto"....


BTW,after addmoding the modelines they should also appear in your display GUI ...

---

### Post by JumpJump123 on 2009-11-22
So I tried this and that, and 1024x768 with 80hz seems a bit better.  But videos (flv's) don't seem too great, artifacts and distortion. Would this be to do with the refresh? I'll keep playing around and see if I find anything better.

I don't have a xorg.conf there, that I can see (in etc/X11/)...

---

### Post by realzippy on 2009-11-22
Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Modeline    "1024x768_[COLOR="SeaGreen"]??[/COLOR]"   [COLOR="SeaGreen"]PASTE HERE YOUR CURRENT MODELINE[/COLOR]-hsync +vsync
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

You could try to make a xorg.conf.Take the above,its working on Intel.Insert your modeline.


to make/edit xorg.conf:

**gksudo gedit /etc/X11/xorg.conf**

I would test modelines from:

cvt 1024 768

cvt 1024 768 70

cvt 1024 768 72

cvt 1024 768 85



If X does not start after this,press alt+ctrl+F1 to get to shell,log in,delete it:

**sudo rm /etc/X11/xorg.conf**

restart (or alt+ctrl+F7)

---

### Post by JumpJump123 on 2009-11-22
Hey.

I've tried a lot of different combos but nothing is really ideal. GIFs and videos and smaller images are always distorted (even in 800x600) and look terrible. Would this be related to the monitor or the graphics card? Is it running at 32 bit now?

Sorry, still confused. I'm a graphic designer by trade so I need good quality images. Would buying a new (more compatible) monitor solve this problem?

I want to try edit the xorg.conf like you suggest but last time I tried that (see the beginning of this thread - what was first suggested) the system reloaded in that xserver mode, the screen and keyboard blinking rapidly and I couldn't even enter a password. Had to reinstall Ubuntu.

---

### Post by JumpJump123 on 2009-11-22
Here's an example of what images look like, generally (text and fonts don't seem as bad):

[IMG]http://img.photobucket.com/albums/v97/MrMilk/Screenshot.jpg[/IMG]

---

### Post by JumpJump123 on 2009-11-22
Here's some details of the Graphics:

id:display
                description: VGA compatible controller              product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device              vendor: Intel Corporation              physical id: 2
              bus info: pci@0000:00:02.0
              version: 01              width: 32 bits              clock: 33MHz              capabilities: pm bus_master cap_list rom               configuration: driver=i915 latency=0              resources: irq:16 memory:d8000000-dfffffff(prefetchable) memory:d0000000-d007ffff

---

### Post by JumpJump123 on 2009-11-22
THIS IS SO FRUSTRATING.

1280x1024 is the right res but the fonts, etc just look horrible, like there's no anti-alias or anything.

Images still distorted.

I think this is more graphics related than monitor related, but I really haven't much clue.

ANYBODY who can help at all, I should be doing commissioned design work right now but it's pointless until l resolve this.

---

### Post by prshah on 2009-11-22
> **JumpJump123 said:**
> 
1280x1024 is the right res but the fonts, etc just look horrible, like there's no anti-alias or anything.

Have you used the monitor's auto-adjust feature? All LCD monitors have a "table" which remembers the best settings for each resolution; however, the first time the resolution is used, you need to run auto-adjust; subsequently, the settings are remembered and loaded each time a particular resolution/color depth combination is used.

Please check and post back.

---

### Post by JumpJump123 on 2009-11-22
Yeah I've done that. Nothing changes, it looks the same. The most distracting thing is the terrible quality of certain images (most GIFs, etc). Do you reckon this is monitor related or Graphics card related?

---

### Post by realzippy on 2009-11-23
You could try this:

gksudo gedit /etc/X11/xorg.conf

and insert this line: DefaultDepth 24:
if not better,then also try to set Option "UseFBDev" "false"



Section "Device"
Identifier "Configured Video Device"
Option "UseFBDev" "true"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
Modeline "1024x768_??" PASTE HERE YOUR CURRENT MODELINE-hsync +vsync
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
[COLOR="PaleGreen"]DefaultDepth 24[/COLOR]
Device "Configured Video Device"
EndSection

---

