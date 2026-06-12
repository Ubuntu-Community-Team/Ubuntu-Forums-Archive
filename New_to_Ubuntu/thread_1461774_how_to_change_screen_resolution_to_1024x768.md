---
title: "how to change screen resolution to 1024x768"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by purdurabo on 2010-04-24
OK guys i figured it out!! after three days and destroying my system twice, i finally changed the resolution of my monitor to 1024x768. i have an HP monitor and just so happens HP doesnt support linux, so i havent been able to find a software driver for it to run in ubuntu. that means that ubuntu can't detect what the settings of the monitor are, so it reverts to 'low graphics mode". which means that you cant set the resolution higher that 800x600.(to put it nicely that SUCK!!!) after hours looking through google results i found the answer. 

[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

the problem is, the code provided in this how-to will set the resolution to 1024x768_70.00mhz, and my monitor runs at 60.00mhz. so the link above will show you how to do it but you may have to change part of it to get it to work for you.

this is what i did:
first open the configuration file with:
```
gksudo gedit /etc/gdm/Init/Default
```then look for the line
                ```
PATH=/usr/bin:$PATH
                OLD_IFS=$IFS
```it should be near the top. position the curser just below these lines and past the code:
```
xrandr --newmode "1024x768_60.00"   60.00  1024 1072 1176 1328  768 771 775 798 -hsync +vsync


xrandr --addmode VGA1 1024x768_60.00
```(the 60.00 part outside the "" is the part i had to change to make mine work)
make sure that the code is two different lines and that they are all the way on the left margin.save and close the file. now restart your computer. login and go to system>preferences>display. now 1024x768 should be one of the options you can chose.

i know alot of people have this problem so i hope that this helps. good luck

---

### Post by nhasian on 2010-04-24
what is the make/model of your monitor?  1024x768@60hz seems pretty slow for a CRT.  Is it an LCD?

---

### Post by Drate on 2010-04-24
Not sure about his model, but I learned back in the "early days" of Ubuntu that my CRT's ran at 60Hz.

Also particualrly useful for puppy.

I was usually using an HP monitor when I could, but the same held true for several generic ones as well.

---

### Post by nhasian on 2010-04-24
> **Drate said:**
> Not sure about his model, but I learned back in the "early days" of Ubuntu that my CRT's ran at 60Hz.

sure maybe 1600x1200@60hz but 1024x768 should be faster.  depending on the model it may do 75 or 100hz at that resolution.  the faster the better.  at 60hz i can see it flickering and it makes my eyes water.

---

### Post by purdurabo on 2010-04-26
it is an HP vs15c and trust me it runs at 60mhz. if i try to input more than 60mhz a little box comes up on the screen telling me that the input signal is out of range, and for me to change the settings so 1024x768 60mhz. i know i wish it was faster too. i plan on getting a new as soon as i can. but i dont see any flicker at all.

---

