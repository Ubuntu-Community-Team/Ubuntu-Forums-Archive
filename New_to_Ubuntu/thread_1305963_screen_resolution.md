---
title: "screen resolution"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by shuggeee on 2009-10-30
I am new to Ubuntu and, in fact, Linux. I wanted to have a look at it before making any committment so I tried running Ububntu 9:10 from the CD I made from the download. I am unable to get a screen resolution higher than 800x600. Is there any way to change this. 

If anyone can tell me how to fix this in plain language I would be grateful. I am not a techie, and the long lists of numbers I've seen in other posts on this forum don't mean anything to me.

Thanks
shuggeee

---

### Post by PorkyPie on 2009-10-30
Hi shuggeee, welcome to Ubuntu Forums :)

You will have to go to System (at the top of your screen) -> Preferences -> Screen Resolution.

---

### Post by scrimple101 on 2009-10-30
> **PorkyPie said:**
> Hi shuggeee, welcome to Ubuntu Forums :)

You will have to go to System (at the top of your screen) -> Preferences -> Screen Resolution.

Unfortunately, i have the same problem and this solution doesn't work for me. I take it you mean system/preferences/display? Still the highest resolution is 640 * 480. I've downloaded the Nvidia driver and Nvidia X Server Settings and can't change anything.

---

### Post by shuggeee on 2009-10-30
Thanks for the rresponse. I tried the display settings as well. I also downloaded a recommended driver. Sadly it didn't work.

---

### Post by mushypeas on 2009-10-30
I had the same problem (see earlier post). Igf you have an SIS graphics card, it isn't compatible with Linux in th eusual way. There are workarounds (do a google search) but - as a raw beginner - they're too much for me so I am going to wait until I get a new computer before I make the move to Linux

---

### Post by kimharding on 2009-10-30
> **shuggeee said:**
> I am new to Ubuntu and, in fact, Linux. I wanted to have a look at it before making any committment so I tried running Ububntu 9:10 from the CD I made from the download. I am unable to get a screen resolution higher than 800x600. Is there any way to change this. 

If anyone can tell me how to fix this in plain language I would be grateful. I am not a techie, and the long lists of numbers I've seen in other posts on this forum don't mean anything to me.

Thanks
shuggeee

> **PorkyPie said:**
> Hi shuggeee, welcome to Ubuntu Forums :)

You will have to go to System (at the top of your screen) -> Preferences -> Screen Resolution.

This is the same problem as 9.04 Jaunty [COLOR=black]Jackalope[/COLOR][COLOR=black], you can not [/COLOR]change the screen resolution as PorkyPie suggests because the graphic card is not recognised (in my case CyberBlade XP Ai1), this bug was widely reported in JJ and should have been fixed for KK. :mad: ](*,)

The best fix I can suggest is, having installed to a hard drive, Open a terminal (the easiest way is to use Alt+F2), then paste in the command:

      > gksudo gedit /etc/X11/xorg.conf 

  This takes you into a text editor with root permissions (so take care), then paste in the following code:

 > Section "Device"
  Identifier "Trident Microsystems CyberBlade XPAi1"
  Driver "trident"
   BusID "PCI:1:0:0"
EndSection

 Section "Monitor"
  Identifier "Configured Monitor"
  Option "DPMS" "true"
  HorizSync 30.0-60.0
  VertRefresh 50.0-70.0
EndSection

 Section "Screen"
  Identifier "Default Screen"
  Monitor "Configured Monitor"
  Device "Configured Video Device"
  DefaultDepth 24
  SubSection "Display"
  Depth 24
  Modes "1024x768" "800x600"
EndSubSection

 EndSection

If anyone knows of a better way, please say so. ;)

---

### Post by shuggeee on 2009-10-30
My graphics card is NVIDIA GeForce 6150LE Does that suggest anything to anyone?

I'm reluctant to install Ubuntu before getting this sorted out as I don't want to go through all the hassle of reinstalling Windows and having to download all the updates. My computer is several years old and there are a lot of them, It takes ages.

I don't know if this is relevant but Ubuntu doesn't seem to recognise my monitor either

---

### Post by kimharding on 2009-10-30
> **shuggeee said:**
> My graphics card is NVIDIA GeForce 6150LE Does that suggest anything to anyone?

I'm reluctant to install Ubuntu before getting this sorted out as I don't want to go through all the hassle of reinstalling Windows and having to download all the updates. My computer is several years old and there are a lot of them, It takes ages.

I don't know if this is relevant but Ubuntu doesn't seem to recognise my monitor either

I think you may need to down load drivers for your card from 

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

but I am not certain...

---

### Post by shuggeee on 2009-10-30
Thanks for the link.

I have another question now, however. If I download the Linux driver, will that interfere with Windows. 

I don't want to muck up my Windows installation until I Have the Ubuntu resolution problem sorted out.

I realise these questions might sound stupid to you techies but I have little knowledge of how these things work and Its all a bit confusing for me.

Thanks for all the help so far and in, hopeful, anticipation of more to come

---

### Post by Turtle.net on 2009-10-30
No it will not.
It is not usually recommended to install drivers directly from the internet, but rather use synaptic to install a compatible driver.
Without the nvidia (proprietary) driver you should be able to boot since the installation will automatically choose the vesa driver.
The only difference : you'll not get 3D accelleration.
To do so, I suggest you to install, then boot and go to System->Administration->Hardware Drivers
This application should tell you something like "NVidia video card was detected we sugest you to use this driver" you click on the driver proposed and that should work.

It seems nonetheless that there are some issues between NVidia and Karmic release.
Maybe wait for a couple of days before installing Ubuntu Karmic Koala, this issue should be solved pretty soon anyway (and it seems to touch upgrades and not fresh installs).

Good luck :)

---

### Post by shuggeee on 2009-10-30
Thanks for the information. I think I'll take your advice and hang on for a while until it gets sorted out. I'm sure we've got our best people working on it!

---

### Post by Turtle.net on 2009-10-30
Btw, I suggest you to install Ubuntu in dual boot, that will not break anything on your windows session and partitions (that's the beauty of it) and you should play a little bit with it.
About the problem I refered about earlier look [here]("http://ubuntuforums.org/showpost.php?p=8198932&postcount=10") for hints ;)

I'm sure you'll find more minor issues. That's totally normal, as for everything else, there's a learning curve.

So go ahead play with your install :)

---

### Post by kimharding on 2009-11-01
> **shuggeee said:**
> My graphics card is NVIDIA GeForce 6150LE Does that suggest anything to anyone?

I'm reluctant to install Ubuntu before getting this sorted out as I don't want to go through all the hassle of reinstalling Windows and having to download all the updates. My computer is several years old and there are a lot of them, It takes ages.

I don't know if this is relevant but Ubuntu doesn't seem to recognise my monitor either


You might find [this tutorial]("http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html#more-2454") useful or maybe not, but it is worth a look.

---

### Post by Wim Sturkenboom on 2009-11-01
> **shuggeee said:**
> I don't know if this is relevant but Ubuntu doesn't seem to recognise my monitor eitherYes, that's the whole point. X will play it safe and only configure 640x480.

---

### Post by sharaq on 2010-01-02
I think this will help you...

[http://ubuntuforums.org/showthread.php?t=1364460](http://ubuntuforums.org/showthread.php?t=1364460)

---

