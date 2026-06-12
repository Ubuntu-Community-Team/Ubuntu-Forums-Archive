---
title: "screen resolution"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by Kwibus on 2009-09-15
[SIZE=2]Hi

I'm a new ubuntu (9.04) user and i seem to have a problem all new uses have: screen resolution.
The highest resolution my laptop can manage is 800 X 600 with a refrsh rate of 61 Hz.
I allready read some posts and to get a solution fast this is what my video card seems to be:

[/SIZE][SIZE=2]id:[/SIZE][SIZE=2][COLOR=gray]display[/COLOR][/SIZE]
                   [SIZE=2]description: [/SIZE][SIZE=2]VGA compatible controller[/SIZE]                 [SIZE=2]product: [/SIZE][SIZE=2]771/671 PCIE VGA Display Adapter[/SIZE]                 [SIZE=2]vendor: [/SIZE][SIZE=2]Silicon Integrated Systems [SiS][/SIZE]                 [SIZE=2]physical id: [/SIZE][SIZE=2]0[/SIZE]
                 [SIZE=2]bus info: [/SIZE][SIZE=2]pci@0000:01:00.0[/SIZE]
                 [SIZE=2]version: [/SIZE][SIZE=2]10[/SIZE]                 [SIZE=2]width: [/SIZE][SIZE=2]32 bits[/SIZE]                 [SIZE=2]clock: [/SIZE][SIZE=2]66MHz[/SIZE]                 [SIZE=2]capabilities: [/SIZE][SIZE=2]pm agp agp-3.0 cap_list[/SIZE]                 [SIZE=2]configuration:[/SIZE][SIZE=2] latency[/SIZE][SIZE=2]=[/SIZE][SIZE=2]0[/SIZE][SIZE=2] 
I hope this s (for now) enough info to get some answers.

Thanks
[/SIZE]

---

### Post by Drone4four on 2009-09-15
Kwibus: what show us the output for: ```
xrandr
```

---

### Post by durand on 2009-09-15
I don't know much about SiS graphics cards but you should try to install a graphics driver. If you go to System > Administration > Hardware Drivers, it might be there. Otherwise you could go here and install it: [http://www.winischhofer.net/mymain/welcome](http://www.winischhofer.net/mymain/welcome)

---

### Post by atmiller65 on 2009-09-15
I have a similar problem. Tried the xrandr command but it has no effect

---

### Post by durand on 2009-09-15
xrandr doesn't solve the problem, it helps us to diagnose it. Copy and pase the output of xrandr into this thread.

---

### Post by atmiller65 on 2009-09-15
OK, xrandr gives the following:
Screen 0: minimum 320 x 200, current 640 x 480, maximum 1360 x 480
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 640x480+0+0 (normal left inverted right x axis y axis) 222mm x 125mm
   640x480        59.9*

---

### Post by durand on 2009-09-15
Did you try installing a graphics driver like I suggested here? [http://ubuntuforums.org/showthread.php?p=7954602#post7954396](http://ubuntuforums.org/showthread.php?p=7954602#post7954396)

It looks like your max resolution is not very big at all.

---

### Post by bigboy7foru on 2009-09-15
well i havent been able to get it to work on the new 9.04 version
 
so im moving back to the 8.10 version till all these bugs are worked out

---

### Post by durand on 2009-09-15
That sounds fair enough but the bugs will probably not be fixed unless you report them: [https://bugs.launchpad.net/](https://bugs.launchpad.net/)

---

### Post by bigboy7foru on 2009-09-15
the bug has been reported and is on ubuntu's web page
 
so all we can do is wait

---

### Post by atmiller65 on 2009-09-15
Not yet. The guys at Zareason who sold me the netbook are lookin ginto it. If I find a fix I'll post it here.

---

### Post by bigboy7foru on 2009-09-16
really on Ubuntu's download page the bug is listed there 
 
Or atleast i thought i saw it lol

---

### Post by Kwibus on 2009-09-16
hi,

x ranr gives me this:

Screen 0: minimum 640 x 480, current 800 x 600, maximum 1280 x 800
default connected 800x600+0+0 0mm x 0mm
   1280x800       60.0  
   1024x768       60.0  
   800x600        60.0* 
   640x480        60.0 

(wich looks strange to me because it seems that there are higher resolutions i should be able to get. if i go to system > preferences > screen I can only choose 800 X600)

---

### Post by durand on 2009-09-16
bigboy7foru said that it worked with 8.10. Maybe you could try a live cd to check that it does?

---

