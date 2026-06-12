---
title: "same old graphics problems"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by Knacker on 2009-05-29
Hi, 
I just installed jaunty on my desktop and my resolution is stuck at 1024x768. i have a intel gm3100 graphics card, samsung T220 monitor that should be displaying at 1680 x 1050. I seem to be able to enable desktop effects (wobble windows and etc.), but I don't know how to get resolution right. The tool Display preferences tool only lists resolutions up to 1280x1024 and none of available resolutions is widescreen. I initially thought that it was a problem with driver and so followed guide to revert to intrepid drivers. This made no difference, so I undid all i changed and now am left back where i started. Would be really grateful for some help. Here are what i think are some relevant bits of information:

> 
$ sudo lshw -C display

  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: 82G33/G31 Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0

*-display:1 UNCLAIMED
       description: Display controller
       product: 82G33/G31 Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0 

and xorg.conf:

> 
...

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection 


Please help! And thanks in advance!

---

### Post by Hospadar on 2009-05-29
just a guess, but you probably don't want to use fbdev.  It tends to monkey around with video stuff, and if you're having problems, I'd try canning it.

That might not be the problem at all, but if you havn't tried it, maybe give it a shot.

---

### Post by kestrel1 on 2009-05-29
Looks like your monitor has not been recognised. What type of monitor do you have?

---

### Post by Knacker on 2009-05-29
> **Hospadar said:**
> just a guess, but you probably don't want to use fbdev.  It tends to monkey around with video stuff, and if you're having problems, I'd try canning it.

That might not be the problem at all, but if you havn't tried it, maybe give it a shot.

I'm sorry, I don't know what fbdev is. I don't know how to "can it" - does this mean removing it with apt-get or disabling it somewhere? 


> **kestrel1 said:**
> Looks like your monitor has not been recognised. What type of monitor do you have?

I'm using a Samsung Syncmaster T220. Resolution should be 1680x1050. 
[http://www.samsung.com/us/consumer/detail/detail.do?group=computersperipherals&type=monitors&subtype=lcd&model_cd=LS22TWHSUV/ZA](http://www.samsung.com/us/consumer/detail/detail.do?group=computersperipherals&type=monitors&subtype=lcd&model_cd=LS22TWHSUV/ZA)

My desktop is built on shuttle SG31G2 barebones kit (with integrated Intel GMA 3100 video).

Any other thoughts?

---

### Post by Knacker on 2009-05-29
Something else: I checked and the display configuration tool shows the monitor as "Epson" (in error red) and the visual rendering of the screen layout (the place you would usually see the little graphical representation of your monitor set up...of, for instance, a dual-monitor set up), has a picture of a little 4:3 screen and it says "[E]rror Scree[n]" on it (letters at beginning and end are cut off).

I think diagnosis of jaunty not recognizing my monitor is the right one. How do I correct this?

---

### Post by Knacker on 2009-05-29
i'm an idiot. i figured it out. SO sorry to waste your time...i forgot i had a projector in the other room hooked up to this machine. (embarrassed face).

---

### Post by kestrel1 on 2009-05-30
> **Knacker said:**
> i'm an idiot. i figured it out. SO sorry to waste your time...i forgot i had a projector in the other room hooked up to this machine. (embarrassed face).

No need to feel embarrassed, we all make mistakes :-)

---

### Post by SunnyRabbiera on 2009-05-30
> **Knacker said:**
> i'm an idiot. i figured it out. SO sorry to waste your time...

Hey thats why were here, to help :D

---

