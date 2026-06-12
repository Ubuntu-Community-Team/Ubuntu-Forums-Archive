---
title: "windows device manager equivalent?"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by nerfball on 2009-04-28
just installed 9.04 on a Dell M1530, install went fine, but I'm wondering how I can confirm what device drivers need further attention. Is there an Ubuntu equivalent to the Windows device manager?

I know for instance, that the webcam isn't working properly, as well as the HDTV tuner card I have on the laptop, and I want to know what else may be disabled or not working (or even compatible).

thanks for helping a newby.

---

### Post by theozzlives on 2009-04-28
Deinvice Manager in Add/Remove

---

### Post by northern lights on 2009-04-28
> **theozzlives said:**
> Deinvice Manager in Add/Remove

If you go with this tool, make sure to select the KDE/Hal manager if you're running Kubuntu or the Gnome version if you're running Ubuntu.

Plus, while you had been asking for a GUI, nothing is as informative as running```
lshw
```Run```
sudo lshw -html > ~/hardware.html

```to get an html file with all your hardware info put into your home folder.

---

### Post by clive littlewood on 2009-04-28
Hi

Go to synaptic package manager and enter in the search

gnome-device-manager check the box for installation then apply.

When installed you will find it as device manager in Apps > system tools


Hope this helps

Clive

---

### Post by nerfball on 2009-04-28
> **northern lights said:**
> If you go with this tool, make sure to select the KDE/Hal manager if you're running Kubuntu or the Gnome version if you're running Ubuntu.

Plus, while you had been asking for a GUI, nothing is as informative as running```
lshw
```Run```
sudo lshw -html > ~/hardware.html

```to get an html file with all your hardware info put into your home folder.

thanks!

I did produce the hardware.html document, but can you tell me what the different highlighting colours mean? some device are listed against a yellow background, or white, and the ethernet adapter is in pink.

also, after installing the device manager applet, some devices are listed with (?) next to them. does that mean there is some issue with proper identification or driver installation?

---

### Post by northern lights on 2009-04-28
yellow/orange: CLAIMED

grey/white: UNCLAIMED

red: DISABLED

[LIST]
[*] a node is marked as CLAIMED if a driver (usually a kernel module or a driver within the monolithic kernel) has been loaded for it
[*] a node is marked as UNCLAIMED if no specific support for it has been loaded (or lshw has been unable to identify the driver)
[*] a node is marked as ENABLED if a driver has been loaded for it and is fully functional
[*] a node is marked as DISABLED if the node has been disabled by a configuration, some hardware failure, etc.[/LIST]

---

### Post by nerfball on 2009-04-28
> **northern lights said:**
> yellow/orange: CLAIMED

grey/white: UNCLAIMED

red: DISABLED

[LIST]
[*] a node is marked as CLAIMED if a driver (usually a kernel module or a driver within the monolithic kernel) has been loaded for it
[*] a node is marked as UNCLAIMED if no specific support for it has been loaded (or lshw has been unable to identify the driver)
[*] a node is marked as ENABLED if a driver has been loaded for it and is fully functional
[*] a node is marked as DISABLED if the node has been disabled by a configuration, some hardware failure, etc.[/LIST]
awesome, thanks again.

so I see an entry in white (unclaimed)

> id:	
multimedia
description: 	Multimedia controller
product: 	Philips Semiconductors
vendor: 	Philips Semiconductors
physical id: 	
0
bus info: 	
pci@0000:0c:00.0
version: 	03
width: 	64 bits
clock: 	33MHz
capabilities: 	msi pciexpress pm bus_master cap_list
configuration:	
latency	=	0

I know the machine should have a **SIGMATEL STAC 92XX C-Major HD Audio** but I'm only seeing the **82801H (ICH8 Family) HD Audio Controller** as active. can anyone help me out getting the sound card to detect?

---

### Post by northern lights on 2009-04-28
> **nerfball said:**
> I know the machine should have a **SIGMATEL STAC 92XX C-Major HD Audio** but I'm only seeing the **82801H (ICH8 Family) HD Audio Controller** as active. can anyone help me out getting the sound card to detect?
That's probably the same device, anyhow, please post the output of```
sudo lshw -C display
```and```
cat /proc/asound/cards
```

---

### Post by nerfball on 2009-04-28
> **northern lights said:**
> That's probably the same device, anyhow, please post the output of```
sudo lshw -C display
```and```
cat /proc/asound/cards
```
> *-display               
       description: VGA compatible controller
       product: GeForce 8600M GT
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia


> 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf6ffc000 irq 21


here you go, thanks.

---

### Post by northern lights on 2009-04-28
Crap.

Brainfart. I need the *multimedia* class, i.e.```
sudo lshw -C multimedia
```

Sorry mate.

---

### Post by nerfball on 2009-04-28
> **northern lights said:**
> Crap.

Brainfart. I need the *multimedia* class, i.e.```
sudo lshw -C multimedia
```

Sorry mate.
> *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
  
*-multimedia UNCLAIMED
       description: Multimedia controller
       product: Philips Semiconductors
       vendor: Philips Semiconductors
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: msi pciexpress pm bus_master cap_list
       configuration: latency=0


no worries... any help you can offer is appreciated!

---

### Post by nerfball on 2009-04-29
bumppity bump? - thanks.

---

