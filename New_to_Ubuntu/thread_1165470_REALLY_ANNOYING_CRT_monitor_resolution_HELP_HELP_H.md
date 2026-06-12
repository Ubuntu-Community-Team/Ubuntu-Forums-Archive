---
title: "REALLY ANNOYING CRT monitor resolution HELP HELP HELP"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by aziznjm on 2009-05-20
i am using ubuntu along with vista ultimate for some time now.i wish to switch os permanently.but the following problem is really bugging me.

ubuntu wont let me set maximum resolution.

my pc config is
win vista ultimate sp1
asus p5k-vm motherboard [intel g33 chipset onboard graphics]
AOC CRT monitor support upto 1280x1024@60 
[i am using 1280x1024@60 screen resolution in vista with maximum visual effect enabled]

i installed ubuntu 9.04 32bit.
everything is fine except i cannot set my monitor at 1280x1024@60.
it is default at 1152x864@60[but in vista refresh rate is 70].
the only other higher resolution showing in 
system>preference>screen resolution is 1360x768.

can somebody help?

---

### Post by bacardiandwatermelon on 2009-05-20
Sounds like you are going to have to manually add it to your xorg.conf file..
```
sudo gedit /etc/X11/xorg.conf
```And under screen add the resolution..

I think you can also run and add the res by running..
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by kerry_s on 2009-05-20
press **alt+f2**
type> **gksudo gedit /etc/X11/xorg.conf**

in the monitor section for 60 refresh:

```

Section "Monitor"
	Identifier	"Configured Monitor"
        HorizSync   	30-85
        VertRefresh 	50-60.1
EndSection

```

in the screen section for size:

```

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Modes	"1280x1024"
	EndSubSection
EndSection

```

this is what mine looks like(see pic), i like to run mine at a smaller resolution than the stock 1600x1280@75, my eyes are not that good. ;) i have mine set to 1024x768@60

---

### Post by aziznjm on 2009-05-21
**sorry for late reply.**timezone differance.
i tried your[kerry_s] solution but it didn't work.
the only change is in "display properties window" maximum res shown is 1152x864@60 and 1360x768 no longer there.no option for 1280x1024.
what do i do?
help

---

### Post by jcollins63 on 2009-05-22
THAT code worked for me!  thanks a lot!

---

### Post by xtremo on 2009-05-23
Worked for me as well Kerry.....many thanks!

---

### Post by cj13579 on 2009-05-23
I have been battling with this for an age! Many thanks kerry_s!

---

