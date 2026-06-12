---
title: "Resolution stuck at 800x600"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by Code9 on 2010-01-23
I just installed the latest release of Ubuntu and after spending a couple hours getting the wireless to work I have a new problem. The resolution will not go past 800x600. I have searched extensively for a solution but have yet to find one.

---

### Post by nick_goodfate on 2010-01-23
Have you installed the driver of your video card ?

---

### Post by Code9 on 2010-01-23
I think so. I checked in synaptic and it says I have a display driver for my series of card.

---

### Post by natex on 2010-01-23
Hi Code9. Let me point you to [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution).

Basically, you have three options to set/change your display resolution.

1. Goto **System>Preferences>Display. **You will have the option to change the resolution here. If the resolution choices seem limited, that's because Ubuntu did not correctly detect the possible resolutions of your monitor/video card. You will have to try 2. or 3.

2. Edit /etc/X/xorg.conf. This is not the preferred way anymore, but sometimes needed.

3. Use **xrandr**. This is the preferred (modern) way.  The link I pointed to above will walk you through the process. 

Please let us know if you still have problems.

nate

---

### Post by Code9 on 2010-01-23
I tried the methods listed above and the resolution wont change. the xrandr commands are throwing up errors when i try to add a new mode

```
X Error of failed request: BadName (named color or font does not exist)
Major opcode of failed request: 149 (RANDR)
Major opcode of failed request: 16 (RRCreateMode)
Serial number of failed request: 18
Current serial number in output stream: 18


```

---

### Post by natex on 2010-01-23
Which commands are you using?

Also, what hardware do you have?

---

### Post by Code9 on 2010-01-23
I was using 

```
 xrandr --newmode <Mode``Line>
```

with the information I got using the cvt command 
so it looked like

```
 xrandr --newmode "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync
```

---

### Post by natex on 2010-01-23
What is your video card? Also, Please post the output of **xrandr -q**.

---

### Post by Code9 on 2010-01-23
Here is the result of lspci

```
Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
```

and the result of xandr -q




```
Screen 0: minimum 320 x 200, current 800 x 600, maximum 2048 x 2048
VGA1 connected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        60.3* 
   640x480        59.9  
  1024x768_60.00 (0xfa)   63.5MHz
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   47.8KHz
        v: height  768 start  771 end  775 total  798           clock   59.9Hz
```

Thanks for doing all this

---

### Post by natex on 2010-01-23
Ok thanks for posting that. Try this:
**xrandr --output VGA1 --mode 1024x768_60.00**

---

### Post by Code9 on 2010-01-23
error

```
xrandr: cannot find mode 1024x768_60.00
```

---

### Post by marin123 on 2010-01-23
if that doesnt work check your xorg.conf file to see if you are using correct driver... if you dont know what to search paste it here...

---

### Post by natex on 2010-01-23
xrandr --addmode VGA1 1024x768_60.00

---

### Post by Code9 on 2010-01-23
I thought that 9.10 got rid of that as mine is blank.

I pasted 

```
sudo gedit /etc/X11/xorg.conf
```

and it showed that mine was blank. I did not add anything to it nor delete anything

---

### Post by marin123 on 2010-01-23
i didnt even have an xorg.conf file, and then i messed with video drivers and somewhere in the process i got my xorg :D

you can put this inside xorg.conf:

```
Section "Device"
	Identifier	"Default Device"
	Driver	"ati"
EndSection
```

and change driver name to one you are using.. intel or whatever...

---

### Post by NCLI on 2010-01-23
Before we go as far as bringing back xorg.conf from the grave, have you tried opening "System->Hardware Drivers"?

---

### Post by Code9 on 2010-01-23
Yeah, i have tried system drivers. The only one that shows up is my wireless card, which i have installed. 

I'll try the xorg you posted though. (never mind on the xorg, didn't change anything)

---

### Post by Code9 on 2010-01-23
Bump

---

