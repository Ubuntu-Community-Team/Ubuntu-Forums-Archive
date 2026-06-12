---
title: "A Few Problems That Needs To Be Solved"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by BJones007 on 2010-10-22
I tried logging in using the alt + ctrl + f4 method and after putting in my login info I got this message.

>  Linux bjones-laptop 2.6.35-22 generic #34-Ubuntu SMP Sun Oct 10 09:24:00 UTC 2010 i686 GNU/Linux Ubuntu 10.10  

and my qstn is why "686" and not '386" ?

Next thing is I tried running this command ```
 sudo gnome-session 
``` and I got this error message >  ** (gnome-session: 1357): WARNING **: Cannot open display  

I don't understand why this happens cos before when I was using Ubuntu 10.04 it worked perfectly fine. Can someone give me some insight on this please? I'm desperate! I had to resort back to WINXP -_-

---

### Post by ArgusVision on 2010-10-22
686 is referring to the processor architecture. Right this moment I cant remember if that indicates dual-core or hyperthreading... Still a 32 bit architecture.

Not sure about the gnome-display issue. You could try the older **startx** command, but that's kinda' reaching...

---

### Post by JustinR on 2010-10-22
> **BJones007 said:**
> I tried logging in using the alt + ctrl + f4 method and after putting in my login info I got this message.

 

and my qstn is why "686" and not '386" ?

Next thing is I tried running this command ```
 sudo gnome-session 
``` and I got this error message  

I don't understand why this happens cos before when I was using Ubuntu 10.04 it worked perfectly fine. Can someone give me some insight on this please? I'm desperate! I had to resort back to WINXP -_-

Hi, just for information CTRL + ALT +F4 isn't the only terminal - you can do CTRL + ALT + F[1-6].

The i686 label means you have at least a Dual Core CPU in your computer.

That gnome-session command most likely didn't work the way you put it - even in 10.04, try this:
*Don't use 'sudo' or 'su'*
```

export DISPLAY=:0.0
gnome-session

```

Then go back to the GUI through CTRL + ALT + F7 pr F8.

---

### Post by BJones007 on 2010-10-22
> **ArgusVision said:**
> 686 is referring to the processor architecture. Right this moment I cant remember if that indicates dual-core or hyperthreading... Still a 32 bit architecture.

Not sure about the gnome-display issue. You could try the older **startx** command, but that's kinda' reaching...
Um...I'm lost >.< what's the older startx command?

---

### Post by JustinR on 2010-10-22
> **BJones007 said:**
> Um...I'm lost >.< what's the older startx command?

Both commands ('gnome-session' & 'startx') do mostly the same thing.

'startx' starts the X-Server (everything GUI) and 'gnome-session' brings up the GNOME Desktop Environment.

Both commands work fine - although it seems to be more common to use 'startx'.

---

### Post by BJones007 on 2010-10-22
> **JustinR said:**
> Hi, just for information CTRL + ALT +F4 isn't the only terminal - you can do CTRL + ALT + F[1-6].

The i686 label means you have at least a Dual Core CPU in your computer.

That gnome-session command most likely didn't work the way you put it - even in 10.04, try this:
*Don't use 'sudo' or 'su'*
```

export DISPLAY=:0.0
gnome-session

```

Then go back to the GUI through CTRL + ALT + F7 pr F8.
Thanks I'm a try that, gonna have to reboot cos I'm on Windows

---

### Post by BJones007 on 2010-10-22
> **JustinR said:**
> Both commands ('gnome-session' & 'startx') do mostly the same thing.

'startx' starts the X-Server (everything GUI) and 'gnome-session' brings up the GNOME Desktop Environment.

Both commands work fine - although it seems to be more common to use 'startx'.
Oh I see, ok thanks for the insight. Will keep you posted if the prolem persists.

---

### Post by BJones007 on 2010-10-24
> **JustinR said:**
> Both commands ('gnome-session' & 'startx') do mostly the same thing.

'startx' starts the X-Server (everything GUI) and 'gnome-session' brings up the GNOME Desktop Environment.

Both commands work fine - although it seems to be more common to use 'startx'.
I tried that but it gave me the same error message >  ** (gnome-session: 1357): WARNING **: Cannot open display 
 
 
could it be that xorg is not installed?

---

### Post by cariboo on 2010-10-24
How did you install Maverick, was it an upgrade, or a fresh install? If it was an upgrade, you will more than likely have to remove /etc/X11/xorg.conf and the restricted driver from the previous version. 

There seems to be a bug in the installer, where it doesn't detect the restricted graphics driver from a  previous version. Graphics drivers for the the previous version don't work with the new version of Xorg.

---

### Post by BJones007 on 2010-10-25
> **cariboo907 said:**
> How did you install Maverick, was it an upgrade, or a fresh install? If it was an upgrade, you will more than likely have to remove /etc/X11/xorg.conf and the restricted driver from the previous version. 

There seems to be a bug in the installer, where it doesn't detect the restricted graphics driver from a  previous version. Graphics drivers for the the previous version don't work with the new version of Xorg.
It was an upgrade, but how do I go by removing "/etc/X11/xorg.conf" ? The splash screen doesn't go away and I'm not sure how to do that from the command line.

---

### Post by JustinR on 2010-10-25
> **BJones007 said:**
> It was an upgrade, but how do I go by removing "/etc/X11/xorg.conf" ? The splash screen doesn't go away and I'm not sure how to do that from the command line.

Hi, does the GRUB screen pop up when you boot up? If so, go to step two.

1. Press and ***hold*** 'Shift' when you start the computer and the GRUB boot menu should pop up - select the second option with the arrow keys and press 'Enter'.

2. When you get to the big blue screen, scroll down to the menu option called 'Root'. Press enter. then type the command:
```

rm /etc/X11/xorg.conf

```

Then depending your graphics card type this in:

nVidia Graphics cards:
```

sudo purge nvidia-current nvidia-settings nvidia-common

```

If you have another card just tell us!

3. Once that has finished type:
```

shutdown -r now

```

Your computer should boot up fine now - if this was a graphics card problem.

---

### Post by BJones007 on 2010-10-25
> **JustinR said:**
> Hi, does the GRUB screen pop up when you boot up? If so, go to step two.

1. Press and ***hold*** 'Shift' when you start the computer and the GRUB boot menu should pop up - select the second option with the arrow keys and press 'Enter'.

2. When you get to the big blue screen, scroll down to the menu option called 'Root'. Press enter. then type the command:
```

rm /etc/X11/xorg.conf

```

Then depending your graphics card type this in:

nVidia Graphics cards:
```

sudo purge nvidia-current nvidia-settings nvidia-common

```

If you have another card just tell us!

3. Once that has finished type:
```

shutdown -r now

```

Your computer should boot up fine now - if this was a graphics card problem.
I know this may sound dumb, but how do I know the type of graphics card I have?

---

### Post by JustinR on 2010-10-25
> **BJones007 said:**
> I know this may sound dumb, but how do I know the type of graphics card I have?

```

sudo lshw -c video

```

Copy & paste what ever the 'Vendor:' & 'Product' is.

---

### Post by ArgusVision on 2010-10-25
sudo lshw -c video

lshw = list hardware  -c video = class video

---

### Post by BJones007 on 2010-10-25
Ok thanks guys (: will keep you updated

---

### Post by BJones007 on 2010-10-27
Guys I don't think I have an Nvidia graphics card =(

---

### Post by GabrielYYZ on 2010-10-27
> **BJones007 said:**
> Guys I don't think I have an Nvidia graphics card =(

copy whatever you get when you use this :

```
lshw -c video
```

and paste it here.

---

### Post by BJones007 on 2010-10-27
Here's what I got when i typed ```
 lshw -c video 
``` 

>  PCI (sys) 

and then 

> 

 * - display: 0
description: VGA compatible controller
product: Mobile 954GME Express Integrated Graphics Controller
Vendor: Intel Corporation
Physical ID: 2
Bus Info: pci@0000:00:02.0
Version: 03
Width: 32 bits
Clock: 33 MHz
Capabilities: msi pm vga_controller bus_master cap_list rom
Configuration: driver=i915 latency=0
resources: irq:16 memory:56280000 ioport:50f0 (size=8 ) memory:40000000-4fffffff memory:5630000000-563fffffff 

 * - display: 1 Unclaimed
description: VGA compatible controller
product: Mobile 954GME Express Integrated Graphics Controller
Vendor: Intel Corporation
Physical ID: 2.1
Bus Info: pci@0000:00:02.1
Version: 03
Width: 32 bits
Clock: 33 MHz
Capabilities: pm bus_master cap_list
Configuration: latency=0
resources: memory:5630000000-563fffffff




---

### Post by 3rdalbum on 2010-10-27
I believe the correct way to start X is through starting the gdm service:

```
sudo service gdm start
```

Anything else might not work.

Also you can check whether X is installed, just by typing 'X' and hitting Enter. If it says "Command not found", then you don't have X installed.

---

### Post by BJones007 on 2010-10-27
> **3rdalbum said:**
> I believe the correct way to start X is through starting the gdm service:

```
sudo service gdm start
```

Anything else might not work.

Also you can check whether X is installed, just by typing 'X' and hitting Enter. If it says "Command not found", then you don't have X installed.
Ok, so to install X would it be ```
 sudo apt-get install xorg 
``` ?????

---

### Post by ArgusVision on 2010-10-27
I know this may sound like a wuss suggestion, but by this point I would seriously consider a re-install... It would be really nice to find the answer to this conundrum, but I imagine you would like a working PC as well. Since this problem seems to have occurred as the result of an upgrade I don't think a fresh install will run into the same problem. You might be best just backing up your files and starting with a clean slate. (You don't happen to have your /home in a separate partition do you? That would be preferable.)

To the rest of the Ubuntu community, I realize re-installation is something of a non-answer, and doesn't particularly benefit the community or humanity at large. But as a tech that has had to deal with deadlines and turnover, time is not a commodity without value.

---

### Post by BJones007 on 2010-10-28
> **ArgusVision said:**
> I know this may sound like a wuss suggestion, but by this point I would seriously consider a re-install... It would be really nice to find the answer to this conundrum, but I imagine you would like a working PC as well. Since this problem seems to have occurred as the result of an upgrade I don't think a fresh install will run into the same problem. You might be best just backing up your files and starting with a clean slate. (You don't happen to have your /home in a separate partition do you? That would be preferable.)

To the rest of the Ubuntu community, I realize re-installation is something of a non-answer, and doesn't particularly benefit the community or humanity at large. But as a tech that has had to deal with deadlines and turnover, time is not a commodity without value.
There is no way for me to back up my files. (Or there is a way but I dunno how), so doing a fresh install would remove everything and I don't think I can afford that.

---

