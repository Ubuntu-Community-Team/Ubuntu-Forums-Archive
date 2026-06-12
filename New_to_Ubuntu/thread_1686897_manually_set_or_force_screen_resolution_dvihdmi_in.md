---
title: "manually set or force screen resolution dvi/hdmi intel"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by debray6379 on 2011-02-13
I would like to if it is possible to manually change/configure my display resolution?.
I have an Acer Aspire L320 with Intel Corporation 82946GZ/GL Integrated Graphics Controller (rev 02) running Ubuntu maverick 10.10. It is connected to my 32"(81cm) TV through it's DVI via a HDMI adapter & cable
I have typed in lspci into terminal
```
roo79@acer1:~$ lspci 
00:00.0 Host bridge: Intel Corporation 82946GZ/PL/GL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82946GZ/GL Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
03:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
04:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```

the highest resolution I can currently set is 1280x720(16:9)
my TV is 1366x768(16:9).

How can/do I set 1366x768(16:9) resolution please?

---

### Post by mr_luksom on 2011-02-13
Yep, you can. First you need the modeling of the resolution you want.

```

gtf horizontal vertical refreshrate

```

Then copy the numbers you'll use them to create the mode:
```

xrandr- -newmode "name" (paste numbers here, they should end in something like hsync Vsync - no parentheses )

```

Now you need to find your output name. Type 'xrandr' by itself, and it will give you the name and some available resolutions. It is usually VGA1 or similar.

Then assign your mode to your output screen so it can be set:
```

xrandr- -output "outputname" --addmode "name"

```

Then you can set the mode for the new resolution!
```

xrandr --output "outputname" --mode "name"

```

---

### Post by debray6379 on 2011-02-13
```
roo79@acer1:~$ gtf horizontal vertical refreshrate

  # 0x0 @ 0.00 Hz (GTF) hsync: -nan kHz; pclk: -nan MHz
  Modeline "0x0_0.00"  -nan  0 -2147483648 -2147483648 -2147483648  0 1 4 1  -HSync +Vsync
```

do I add all of that or just from "0x0_0.00"? sorry I'm a dummy :D

---

### Post by debray6379 on 2011-02-13
I forgot to say thank you

---

### Post by debray6379 on 2011-02-14
```
roo79@acer1:~$ xrandr- -newmode "name" 0 -2147483648 -2147483648 -2147483648  0 1 4 1  -HSync +Vsync
No command 'xrandr-' found, did you mean:
 Command 'xrandr' from package 'x11-xserver-utils' (main)
xrandr-: command not found
```

this is what I get from step two
can I get some help please? I changed xrandr- to just xrandr but it still did not work??? I need some help!

---

### Post by debray6379 on 2011-02-19
anyone??? please help???

---

### Post by mr_luksom on 2011-02-19
Okay, let's go back to post #3, and work our way through it.

After the gtf command, substitute "horizontal", "vertical" and "refreshrate" with the details of the video mode you are after. You mentioned 1366x786. I don't know what refresh rate your tv is (depends on where you live), but you should probably pick 50Hz in the US, 60Hz in Europe/Australia. See if you can. Google to find out what your tv supports before doing executing the command - the wrong refresh rate can damage some tvs.

Let's say you live where I live (60Hz), and you want 1366x768:

gtf 1366 768 60

After checking your tv's refresh rate, post the output of the gtf command with your refresh rate, and I'll step you through the rest.

I promise I will get back to you sooner next time!

---

### Post by debray6379 on 2011-02-20
gtf 1366 768 60

  # 1368x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 85.86 MHz
  Modeline "1368x768_60.00"  85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync

and yes I'm in Australia and as far as I can tell/ find out the tv refresh rate is 60Hz

---

### Post by debray6379 on 2011-02-20
[QUOTE=] I promise I will get back to you sooner next time![/QUOTE]

It's ok mate I just thought there might have been someone else out there that would help and not just place the burden all on you. I am very thankful for you time!. take your time I'm sure you have better things to do than to spend all day on a forum for noobs lol!

---

### Post by mr_luksom on 2011-02-20
Great. Now from the info you have posted, we have the modeline:

  *85.86 1368 1440 1584 1800 768 769 772 795 -HSync +Vsync*

Note that although you asked for 1366x768, your onboard video does not support it, the closest is 1368x768. It shouldn't even be noticeable.

So we can create the mode "1368x768@60":
```

xrandr --newmode "1368x768@60" 85.86 1368 1440 1584 1800 768 769 772 795 -HSync +Vsync

```

Can you then post the output of just xrandr by itself? Then we can assign it to your monitor (Need to know the name of the monitor to do this). 

```

xrandr

```

---

### Post by debray6379 on 2011-02-21
[QUOTE=]
Can you then post the output of just xrandr by itself? Then we can assign it to your monitor (Need to know the name of the monitor to do this). 
```

xrandr

```[/QUOTE]

```
roo79@acer1:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 720, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
DVI1 connected 1280x720+0+0 (normal left inverted right x axis y axis) 708mm x 398mm
   1280x720       60.0*+   50.0  
   1024x768       60.0  
   800x600        60.3  
   720x576        50.0  
   720x480        60.0     59.9
```

here is the output of xrandr :)

---

### Post by mr_luksom on 2011-02-21
Okay. So lets add the mode we just created to the display DVI1.

```

xrandr --addmode DVI1 "1368x768@60"

```

And then you should finally be able to change the mode:

```

xrandr --output DVI1 --mode "1368x768@60"

```

That should change your resolution.

---

### Post by debray6379 on 2011-02-22
thank you so much it worked perfectly my screen looks so much better!!! you are a saint!

---

### Post by debray6379 on 2011-02-25
after setting this up it works but I'm having to reset it everytime I login? it says it cannot apply saved settings?

---

### Post by Commandrkeen on 2011-03-15
Thanks Mr_Luksom that helped me too, but I am also having the issue of having to reset each time.  It didn't save the configuration.  I'm going to man xrandr to see what I can come up with but if you have the answer that'd be great too.  Thanks :)

---

### Post by Commandrkeen on 2011-03-15
You're off the hook Mr_Luksom.  I found the answer here:

Go to step #6 [http://ubuntuforums.org/showthread.php?p=8595940](http://ubuntuforums.org/showthread.php?p=8595940) :D

---

### Post by spegru on 2011-05-19
Hi there I've been trying to follow this without success so far. Using another PC I've established that my TV/Monitor likes 1360x768 60Hz

When I type:  

gtf 1360 768 60  

I get
# 1360x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 84.72 MHz
  Modeline "1360x768_60.00"  84.72  1360 1424 1568 1776  768 769 772 795  -HSync +Vsync

but when I type    

xrandr --newmode "1360x768_60.00"  84.72  1360 1424 1568 1776  768 769 772 795  -HSync +Vsync

and then

 xrandr --addmode LVDS1 "1360x768_60.00"  

I get

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  25
  Current serial number in output stream:  26

What am I doing wrong?

---

### Post by spegru on 2011-05-23
bump

---

### Post by spegru on 2011-05-25
bump

---

### Post by Grenage on 2011-05-25
This would really be better off in a thread of its own, but please post the results of these three commands; the last may have no output.

```
xrandr -q
lspci | grep VGA
cat /etc/X11/xorg.conf
```

---

### Post by spegru on 2011-05-25
The output of xrandr -q  is:

Screen 0: minimum 320 x 200, current 1280 x 720, maximum 4096 x 4096
LVDS1 connected 1280x720+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x720       60.0*+
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)

The output of lspci | grep VGA  is:

00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)


I have already trying to follow the method earlier in this thread. Seems I need to add another mode to get the TV's preferred 1360x768 60Hz instead of 1280 x 720 but I get that error I mentioned on the previous page of this thread.....

---

### Post by spegru on 2011-05-29
bump

---

### Post by spegru on 2011-05-30
bump

---

### Post by spegru on 2011-06-02
Hi there I've been trying to follow this without success so far. Using another PC I've established that my TV/Monitor likes 1360x768 60Hz

When I type:

gtf 1360 768 60

I get
# 1360x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 84.72 MHz
Modeline "1360x768_60.00" 84.72 1360 1424 1568 1776 768 769 772 795 -HSync +Vsync

but when I type

xrandr --newmode "1360x768_60.00" 84.72 1360 1424 1568 1776 768 769 772 795 -HSync +Vsync

and then

xrandr --addmode LVDS1 "1360x768_60.00"

I get

X Error of failed request: BadMatch (invalid parameter attributes)
Major opcode of failed request: 150 (RANDR)
Minor opcode of failed request: 18 (RRAddOutputMode)
Serial number of failed request: 25
Current serial number in output stream: 26

What am I doing wrong?

---

### Post by spegru on 2011-09-05
Still havn't got this working right but do have some info.
When consulting monitor settings it always shows the HDMI connection as 'laptop'. No problem with the name but it does tend to show that HDMI support is immature.
Tried both a TV with HDMI and also a normal PC monitor using an adapting DV-HDMI cable and the result seem to be the same - a restricted set of not very good resolutions to choose from.
Also tried multiple monitors, one of when had to be HDMI as that and VGA is all I've got - resulted in utter garbage on moth screens

So basically it looks like we need better HDMI support

In the mean time I'm left with fluffy fonts on my TV/monitor...

---

