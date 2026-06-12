---
title: "setting undetected screen resolution ubuntu 10.04"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by seamustry on 2010-05-06
hi, when i try to set undetected screen resolution, i get following error: cannot find output "LVDS".

i'm typing in following code:

```
xrandr --output LVDS --mode 1024x768
```

i was following the guide here: [https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions)


here is the output when i type in the command "xrandr"
```
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0 
```


any ideas?? thanks.

---

### Post by James1293 on 2010-05-26
Try this (the $ just means terminal; don't type it):

```
$ cvt 1024 768
```
You will see some output, which will look something like this:
```
800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
  Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
```
 Copy *everything* after "Modeline" on your output.

 [COLOR="DarkRed"]THEN CHANGE THE SCREEN REFRESH RATE (thanks Moozillaaa for fix):

Do NOT copy the screen refresh rate info into the '--newmode' command. Delete it, and the underscore as well.
i. e.:
"800x600_60.00" 38.25 800 832 912 1024 600 603 607 624 -hsync +vsync
to
"800x600" 38.25 800 832 912 1024 600 603 607 624 -hsync +vsync
[/COLOR]
 Paste it in like below (with the words "xrandr --newmode" before it):
```
$ xrandr --newmode "800x600"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
```
Next command: instead of "800x600" at the end, put whatever was in the output that you copied.
(NOTE: the user tucm posted below that you may have to change the word "default" to "VGA1" in the next two commands.)
```
$ xrandr --addmode default 800x600
```
Finally, (changing the "800x600" again)
```
$ xrandr --output default --mode 800x600
```

That should do it. If you want it to stay for the next boot (you probably do...), type this...
```

$ cd ~
$ gedit .xprofile

```
In the window that pops up, paste all the lines that you just ran (except the cvt) (Remember the NOTE: the user tucm posted below that you may have to change the word "default" to "VGA1"):
```

xrandr --newmode "800x600"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
xrandr --addmode default 800x600
xrandr --output default --mode 800x600
```
Save the document.

If you need any help, reply, by all means!
James

---

### Post by Moozillaaa on 2010-10-20
> **James1293 said:**
> Try this (the $ just means terminal; don't type it):

```
$ cvt 1024 768
```You will see some output, which will look something like this:
```
800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
  Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
```[SIZE=2][COLOR=Red] **Copy *everything* after "Modeline" on your output. Paste it in like below (with the words "xrandr --newmode" before it):**[/COLOR][/SIZE]
```
$ xrandr --newmode "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
```Next command: instead of "800x600_60.00" at the end, put whatever was in the output that you copied.
```
$ xrandr --addmode default 800x600_60.00
```Finally, (changing the "800x600_60.00" again)
```
$ xrandr --output default --mode 800x600_60.00
```That should do it. If you want it to stay for the next boot (you probably do...), type this...
```

$ cd ~
$ gedit .xprofile

```In the window that pops up, paste all the lines that you just ran (except the cvt):
```

xrandr --newmode "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
xrandr --addmode default 800x600_60.00
xrandr --output default --mode 1024x768_60.00
```Save the document.

If you need any help, reply, by all means!
James

P.S.: I can help you more if you tell me the output of the "$ cvt 1024 768" command. You may be able to get it, though.
[B][COLOR=Red]
Do NOT copy the screen refresh rate info into the '--newmode' command.[/COLOR][/B] [B][COLOR=Red]Delete it, and the underscore as well.
[COLOR=Black]
i. e.:
[/COLOR][/COLOR]"800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync[/B]
[B][COLOR=Red][COLOR=Black]to
[/COLOR][/COLOR]"800x600"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync[/B]

The Wiki page information is incorrect.
[B][COLOR=Red][COLOR=Black]
[/COLOR][/COLOR][/B]

---

### Post by tucm on 2010-12-13
Hi,

I successfully changed my display resolution to 1280x1024 in ubuntu 10.04, follow the guide by **James1293**, but there were some tweaks:

Every time I enter the command:
```

$ xrandr --addmode default 1280x1024_60.00
```The system will reply:

```
xrandr: cannot find output "default"
```Finally I had to replace "default" with "VGA1" in the following commands:

```
$ xrandr --addmode default 1280x1024_60.00
$ xrandr --output default --mode 1280x1024_60.00
```And it works.

Sorry for my bad English,
I hope this might be useful for someone.

---

### Post by Z1-900 on 2011-07-02
Big thank you to James1293 and tucm!!

Ubuntu only gave me a refresh rate of 60hz with my crt monitor which normally uses 85hz the resolution was already set right just the refresh rate was too low. I've been trying to read articles for days to figure out how to change this I always ran into a problem following all the other articles [U]but your explanation of how to change it was easy to follow no problems encountered and actually worked.

[/U]So again thank you very,very much :D

---

### Post by James1293 on 2011-07-05
Hey Z1-900,
Great. I wish it worked for me. XD

---

### Post by SheaMan on 2011-11-20
Followed all the steps ( I included the refresh rate output from the cvt command )
and I get, 
```

xrandr: screen cannot be larger than 840x624 (desired size 1680x1050) :confused:

```
840x624!? You have got to be kidding me!?

---

### Post by fdrake on 2011-11-20
> **SheaMan said:**
> Followed all the steps ( I included the refresh rate output from the cvt command )
and I get, 
```

xrandr: screen cannot be larger than 840x624 (desired size 1680x1050) :confused:

```
840x624!? You have got to be kidding me!?

whats your xorg.conf?
```
less /usr/share/xresprobe/xorg.conf
```

---

### Post by SheaMan on 2011-11-29
urr.. there is more to the less man than I thought.. :neat:

I ran the command at the /$ and the ~$ and received the same,

[quote=error 10.04]
/usr/share/xresprobe/xorg.conf: No such file or directory

[/quote]

I have a Xorg.0.log - but tis loooong.

---

